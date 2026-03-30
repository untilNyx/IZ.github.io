# TECH-IZ.github.io
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Python解难初赛练习应用</title>
    <!-- Tailwind CSS v3 -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome -->
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#3b82f6',
                        secondary: '#64748b',
                        accent: '#06b6d4',
                        success: '#10b981',
                        warning: '#f59e0b',
                        danger: '#ef4444',
                        light: '#f8fafc',
                        dark: '#1e293b'
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .text-shadow {
                text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
            }
            .card-hover {
                @apply transition-all duration-300 hover:shadow-lg hover:-translate-y-1;
            }
        }
    </style>
</head>
<body class="bg-gray-50 min-h-screen">
    <!-- 导航栏 -->
    <nav class="bg-white shadow-md">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <i class="fa fa-python text-primary text-3xl"></i>
                <h1 class="text-xl font-bold text-gray-800">Python解难初赛练习</h1>
            </div>
            <div class="hidden md:flex space-x-6">
                <a href="index.html" class="text-primary font-medium">首页</a>
                <a href="records.html" class="text-gray-600 hover:text-primary transition-colors">答题记录</a>
                <a href="knowledge.html" class="text-gray-600 hover:text-primary transition-colors">知识点速查</a>
            </div>
            <button id="mobile-menu-button" class="md:hidden text-gray-600 focus:outline-none">
                <i class="fa fa-bars text-xl"></i>
            </button>
        </div>
        <!-- 移动端菜单 -->
        <div id="mobile-menu" class="hidden md:hidden bg-white shadow-lg absolute w-full z-10">
            <div class="container mx-auto px-4 py-2 flex flex-col space-y-3">
                <a href="index.html" class="text-primary font-medium py-2 border-b border-gray-100">首页</a>
                <a href="records.html" class="text-gray-600 hover:text-primary transition-colors py-2 border-b border-gray-100">答题记录</a>
                <a href="knowledge.html" class="text-gray-600 hover:text-primary transition-colors py-2">知识点速查</a>
            </div>
        </div>
    </nav>

    <!-- 主要内容 -->
    <main class="container mx-auto px-4 py-8">
        <!-- 欢迎区域 -->
        <section class="text-center mb-12">
            <h2 class="text-4xl font-bold text-gray-800 mb-4 text-shadow">欢迎使用 Python 解难初赛练习应用</h2>
            <p class="text-lg text-gray-600 max-w-3xl mx-auto">
                本应用提供Python解难初赛相关的练习题，帮助你巩固Python知识点，提高编程能力。
                支持单选题和填充题，覆盖从基础语法到高级应用的多个知识点。
            </p>
        </section>

        <!-- 开始练习区域 -->
        <section class="bg-white rounded-lg shadow-md p-6 mb-12">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 text-center">开始练习</h3>
            
            <form id="quiz-form" class="max-w-2xl mx-auto">
                <div class="mb-6">
                    <label for="question-count" class="block text-gray-700 font-medium mb-2">题目数量</label>
                    <select id="question-count" class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary">
                        <option value="10">10题</option>
                        <option value="20" selected>20题</option>
                        <option value="30">30题</option>
                        <option value="50">50题</option>
                    </select>
                </div>
                
                <div class="mb-6">
                    <label for="difficulty" class="block text-gray-700 font-medium mb-2">难易程度</label>
                    <select id="difficulty" class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary">
                        <option value="all">全部难度</option>
                        <option value="1">难度 1 - 入门级</option>
                        <option value="2">难度 2 - 基础级</option>
                        <option value="3">难度 3 - 中级</option>
                        <option value="4">难度 4 - 进阶级</option>
                        <option value="5">难度 5 - 高级</option>
                        <option value="1-2">难度 1-2 - 入门到基础</option>
                        <option value="2-3">难度 2-3 - 基础到中级</option>
                        <option value="3-4">难度 3-4 - 中级到进阶</option>
                        <option value="4-5">难度 4-5 - 进阶到高级</option>
                    </select>
                </div>
                
                <div class="mb-6">
                    <label class="block text-gray-700 font-medium mb-2">知识点范围</label>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                        <div class="flex items-center">
                            <input type="checkbox" id="category-basic" name="categories" value="basic" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-basic" class="text-gray-700">基本语法</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-control" name="categories" value="control" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-control" class="text-gray-700">流程控制</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-data" name="categories" value="data_structure" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-data" class="text-gray-700">序列与数据结构</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-file" name="categories" value="file" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-file" class="text-gray-700">文件读写</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-oop" name="categories" value="oop" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-oop" class="text-gray-700">面向对象编程</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-builtin" name="categories" value="builtin" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-builtin" class="text-gray-700">内置程序库</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-third" name="categories" value="third_party" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-third" class="text-gray-700">数据处理库</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-crawler" name="categories" value="web_crawler" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-crawler" class="text-gray-700">网络爬虫</label>
                        </div>
                        <div class="flex items-center">
                            <input type="checkbox" id="category-practice" name="categories" value="practice" class="mr-2 h-4 w-4 text-primary focus:ring-primary" checked>
                            <label for="category-practice" class="text-gray-700">实践应用</label>
                        </div>
                    </div>
                </div>
                
                <div class="mb-6">
                    <label for="time-limit" class="block text-gray-700 font-medium mb-2">时间限制（分钟）</label>
                    <select id="time-limit" class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary">
                        <option value="0">无限制</option>
                        <option value="15">15分钟</option>
                        <option value="30" selected>30分钟</option>
                        <option value="60">60分钟</option>
                    </select>
                </div>
                
                <div class="text-center">
                    <button type="submit" class="bg-primary hover:bg-blue-600 text-white font-medium py-3 px-8 rounded-md transition-colors shadow-md hover:shadow-lg">
                        开始练习
                    </button>
                </div>
            </form>
        </section>

        <!-- 知识点范围介绍 -->
        <section class="mb-12">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 text-center">考核知识点范围</h3>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- 基本语法 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-blue-100 p-3 rounded-full mr-4">
                            <i class="fa fa-code text-primary text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">基本语法</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• 变量与数据类型</li>
                        <li>• 变量命名规则</li>
                        <li>• 函数定义与调用</li>
                        <li>• 注释</li>
                        <li>• 运算符</li>
                        <li>• Lambda表达式</li>
                        <li>• 列表推导式</li>
                    </ul>
                </div>
                
                <!-- 流程控制 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-green-100 p-3 rounded-full mr-4">
                            <i class="fa fa-sitemap text-green-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">流程控制</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• 条件语句</li>
                        <li>• 循环语句</li>
                        <li>• 循环控制</li>
                        <li>• 异常处理</li>
                        <li>• 推导式</li>
                        <li>• range()函数</li>
                    </ul>
                </div>
                
                <!-- 序列与数据结构 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-purple-100 p-3 rounded-full mr-4">
                            <i class="fa fa-list text-purple-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">序列与数据结构</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• 列表(list)</li>
                        <li>• 元组(tuple)</li>
                        <li>• 字符串(str)</li>
                        <li>• 字典(dict)</li>
                        <li>• 集合(set)</li>
                        <li>• 切片操作</li>
                    </ul>
                </div>
                
                <!-- 文件读写 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-yellow-100 p-3 rounded-full mr-4">
                            <i class="fa fa-file-text text-yellow-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">文件读写</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• 文件打开与关闭</li>
                        <li>• 文件打开模式</li>
                        <li>• 文件读取方法</li>
                        <li>• 文件写入方法</li>
                        <li>• CSV文件处理</li>
                    </ul>
                </div>
                
                <!-- 面向对象编程 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-red-100 p-3 rounded-full mr-4">
                            <i class="fa fa-object-group text-red-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">面向对象编程</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• 类的定义</li>
                        <li>• 构造方法</li>
                        <li>• 实例方法</li>
                        <li>• 类方法与静态方法</li>
                        <li>• 继承</li>
                        <li>• 迭代器与生成器</li>
                    </ul>
                </div>
                
                <!-- 内置程序库 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-indigo-100 p-3 rounded-full mr-4">
                            <i class="fa fa-cubes text-indigo-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">内置程序库</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• datetime模块</li>
                        <li>• json模块</li>
                        <li>• csv模块</li>
                        <li>• os模块</li>
                        <li>• random模块</li>
                        <li>• math模块</li>
                    </ul>
                </div>
                
                <!-- 数据处理库 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-teal-100 p-3 rounded-full mr-4">
                            <i class="fa fa-database text-teal-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">数据处理库</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• NumPy基础</li>
                        <li>• Pandas基础</li>
                        <li>• Matplotlib基础</li>
                        <li>• 数组操作</li>
                        <li>• 数据筛选</li>
                    </ul>
                </div>
                
                <!-- 网络爬虫 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-orange-100 p-3 rounded-full mr-4">
                            <i class="fa fa-globe text-orange-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">网络爬虫</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• Requests库</li>
                        <li>• Beautiful Soup基础</li>
                        <li>• XPath选择器</li>
                        <li>• CSS选择器</li>
                        <li>• Selenium基础</li>
                    </ul>
                </div>
                
                <!-- 实践应用 -->
                <div class="bg-white rounded-lg shadow-md p-6 card-hover">
                    <div class="flex items-center mb-4">
                        <div class="bg-pink-100 p-3 rounded-full mr-4">
                            <i class="fa fa-wrench text-pink-600 text-xl"></i>
                        </div>
                        <h4 class="text-xl font-semibold text-gray-800">实践应用</h4>
                    </div>
                    <ul class="text-gray-600 space-y-2">
                        <li>• 字符串拼接与分割</li>
                        <li>• 字符串大小写转换</li>
                        <li>• 字符串查找与统计</li>
                        <li>• 字符串判断方法</li>
                        <li>• map()函数应用</li>
                    </ul>
                </div>
            </div>
        </section>
        
        <!-- 难度说明 -->
        <section class="mb-12">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 text-center">难度等级说明</h3>
            
            <div class="bg-white rounded-lg shadow-md p-6">
                <div class="grid grid-cols-1 md:grid-cols-5 gap-4">
                    <div class="text-center p-4 rounded-lg bg-green-50">
                        <div class="text-2xl font-bold text-green-600 mb-2">难度 1</div>
                        <div class="text-gray-600">入门级</div>
                        <div class="text-sm text-gray-500 mt-2">基础概念认知</div>
                    </div>
                    <div class="text-center p-4 rounded-lg bg-lime-50">
                        <div class="text-2xl font-bold text-lime-600 mb-2">难度 2</div>
                        <div class="text-gray-600">基础级</div>
                        <div class="text-sm text-gray-500 mt-2">基本语法应用</div>
                    </div>
                    <div class="text-center p-4 rounded-lg bg-yellow-50">
                        <div class="text-2xl font-bold text-yellow-600 mb-2">难度 3</div>
                        <div class="text-gray-600">中级</div>
                        <div class="text-sm text-gray-500 mt-2">综合知识运用</div>
                    </div>
                    <div class="text-center p-4 rounded-lg bg-orange-50">
                        <div class="text-2xl font-bold text-orange-600 mb-2">难度 4</div>
                        <div class="text-gray-600">进阶级</div>
                        <div class="text-sm text-gray-500 mt-2">高级特性掌握</div>
                    </div>
                    <div class="text-center p-4 rounded-lg bg-red-50">
                        <div class="text-2xl font-bold text-red-600 mb-2">难度 5</div>
                        <div class="text-gray-600">高级</div>
                        <div class="text-sm text-gray-500 mt-2">深入理解应用</div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- 页脚 -->
    <footer class="bg-gray-800 text-white py-8">
        <div class="container mx-auto px-4">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="mb-4 md:mb-0">
                    <div class="flex items-center space-x-2">
                        <i class="fa fa-python text-primary text-2xl"></i>
                        <span class="text-lg font-semibold">Python解难初赛练习应用</span>
                    </div>
                    <p class="text-gray-400 mt-2">帮助你巩固Python知识点，提高编程能力</p>
                </div>
                <div class="flex space-x-6">
                    <a href="index.html" class="text-gray-300 hover:text-white transition-colors">首页</a>
                    <a href="records.html" class="text-gray-300 hover:text-white transition-colors">答题记录</a>
                    <a href="knowledge.html" class="text-gray-300 hover:text-white transition-colors">知识点速查</a>
                </div>
            </div>
            <div class="mt-6 pt-6 border-t border-gray-700 text-center text-gray-400">
                <p>&copy; 2023 Python解难初赛练习应用. 保留所有权利.</p>
            </div>
        </div>
    </footer>

    <script>
        // 移动端菜单切换
        document.getElementById('mobile-menu-button').addEventListener('click', function() {
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenu.classList.toggle('hidden');
        });

        // 表单提交处理
        document.getElementById('quiz-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // 获取选中的知识点分类
            const selectedCategories = Array.from(document.querySelectorAll('input[name="categories"]:checked'))
                .map(checkbox => checkbox.value);
            
            // 验证是否至少选择了一个知识点分类
            if (selectedCategories.length === 0) {
                alert('请至少选择一个知识点分类');
                return;
            }
            
            // 获取题目数量、难度和时间限制
            const questionCount = parseInt(document.getElementById('question-count').value);
            const difficulty = document.getElementById('difficulty').value;
            const timeLimit = parseInt(document.getElementById('time-limit').value);
            
            // 将配置保存到sessionStorage
            const quizConfig = {
                categories: selectedCategories,
                questionCount: questionCount,
                difficulty: difficulty,
                timeLimit: timeLimit
            };
            
            sessionStorage.setItem('quizConfig', JSON.stringify(quizConfig));
            
            // 跳转到答题页面
            window.location.href = 'quiz.html';
        });
    </script>
</body>
</html>
