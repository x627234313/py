# 1.3.1 环境
一个求值表达式的环境由一系列的框架组成。每个框架都包含绑定，这些绑定将一个名称与其相应的值相关联。

赋值和导入语句添加条目到当前环境的第一个框架中。 到目前为止，我们的环境只包含全局框架。

一个`def`语句也绑定一个名称到定义时创建的函数上。

注意函数的名称是可重复的，一次的框架中，一次作为函数本身的一部分。这种重复是故意的：许多不同的名称可能指向相同的函数，但是函数本身只有一个内部名称。
但是，在环境中查找名称的值只会检查名称绑定。 函数的内部名称在查找名称时不起作用。

__New environment Features__：Assignment and user-defined function definition.  
（assignment：分配 任务 作业）  
新环境特点：赋值和用户定义的函数定义。

# 1.3.2 调用用户定义的函数
求值一个调用表达式，其运算符命名用户定义的函数，Python解释器按照相似的过程对于使用内建运算符函数求值的表达式。也就是说，解释器对操作数表达式求值，然后将命名函数应用到结果参数。

应用用户定义函数的行为引入了第二个本地框架，这个框架只能被该函数访问。应用用户定义函数的一些理由：
1. 将参数绑定到新的本地框架中函数形参的名称上
2. 从该框架开始到全局框架结束，在这个环境中求函数体的值。

求值主体的环境由两个框架组成：首先是本地框架包含参数绑定，然后是全局框架包含其他所有内容。 函数应用程序的每个实例都有自己独立的本地框架。