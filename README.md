# swift-code-guide
swift编码规范

* 代码基本样式规范
	* 每行字符数长度
		* 为了代码的可读性，每行代码的长度尽量控制代码长度在80字符以内
		* 如果代码需要换行，每行的开头不允许为特殊字符，比如：“＋，－，／”等
	* 字符编码
		*	代码书写中只允许使用UTF－8编码规则字符
	* 独立语句书写规则
		* 除非特殊情况，否则每条语句结束可以不用写';'
		* 不能在同一行中定义多条独立语句
	* 代码块语句中的左大括号尽量保持在语句第一行的末尾
* 注释使用规范
	* “块注释”的使用'/* */'
		* 主要用于文件的注释或者类注释，通过简单文字解释文件或者类的主要作用，同时注意每行注释的长度
		* 不要嵌套使用“块注释”
	* "行注释"的使用'//'
		* 可以用于方法或者函数的注释，简单描述方法的作用
	* 	注意注释的简洁性一句准确性，在代码重构过程中要及时更新注释同时删除不必要的注释
	* 	注释规范示例：
	```swift
	//简单行注释,主要用于函数或方法功能的简单描述
	/*文件，结构体或者类功能描述。注意描述分行*/
	/*swift能够进行注释嵌套，但是为了简洁性
	/*程序中不允许进行注释嵌套*/
	*/
	```
* 命名规范
	* 变量和常量命名规范
		* 使用小驼峰命名，假如名字中间特殊字符则特殊字符全部大写。如果只有一个单词则采用小写
       * 在定义常量和变量的时候需要标注类型
	   * 常量在声明的时候就必须完成赋值
	* 方法函数集合命名规范
		* 采用小驼峰命名，第一个单词小写其余大写
	* 函数方法参数命名规范
		* 全部采用小写
	* 类结构体命名规范	
		* 采用大驼峰命名，类名每个单词都大写 
	* 命名规范示例：
		```swift
		  //变量和常量命名规则
	      let MaxCount: Int = 1000
		  var currentNum: Int = 100
		  var rootURL:String = "http://www.zhuozhuo.io.com"
		  //类和结构体命名规则
		  class SomeClass{
		  }
		  struct SomeStructrue{
		  }
		  //函数方法命名规则
		  func globalFunction(){
		  }
		  class SomeClass{
				  func localFunction(){
				  }
		  }
		  //集合命名规则
		  var someList = ["value1","value2"]
		  var someMap = ["key1":"value1","key2":"value2"]
	    ``` 
* 类结构体使用规范
	* 类的属性除了可选类型都应该赋默认值
	* 使用“＝＝＝”判断类的变量或者常量是否相等
* 集合使用规范
	* 使用显示类型和空集合进行集合定义，类型在赋值操作符左边，空实例在赋值操作符右边
	* 在声明集合的时候明确集合类型，尽量不用类型推导
	* 遍历集合的时候尽量使用for-in语法
	* 使用isEmpty判断集合个数是否为0
	* 集合使用规范示例：
	  ``` swift
		  // 空集合的定义
			var x: [String: Int] = [:]
			var y: [Double] = []
			var z: Set<String> = []
			var mySet: MyOptionSet = []
		 // 声明时确定类型
		    var shoppingList: [String] = ["Eggs", "Milk"]
		    var favoriteGenres: Set<String> = ["Rock", "Classical", "Hip hop"]
	  ```
* 方法函数使用规范
	* 函数方法定义中第一个大括号的做括号必须在函数定义末尾
	* 如果使用外部参数要么全部都使用要么全部都不使用，不允许部分使用部分不使用
	* 在定义外部参数时，不能使用相同的外部参数
	* 如果存在默认参数则默认参数定义在普通参数后面
	* 参数顺序规则：普通参数，默认参数，可变参数
	* 在函数返回值为空的时候使用->void代替->()
	* 函数方法使用示例：
	    ``` swift
		// 全部使用外部参数名
		 func functionDemo1(firstParam a:Int, secondParam b:Int) {
			 // function body
		 }
		 //全部不使用外部参数名
		 func functionDemo2(firstParam:Int, secondParam:Int) {
			 // function body
		 }
		 //函数参数顺序规则
		 func functionDemo3(normalParam:Int , defaultParam:Int = 12,variadicParam:Int...){
		 //function body
		 }
		```
* 闭包使用规范
	* 在闭包方法行数少于5行的时候，尽量通过闭包表达式减少代码量
	* 闭包中不允许使用参数名称缩写和运算符函数闭包，这样会增加代码的可读性
	* 尾随闭包：尾随闭包是一个书写在函数括号之后的闭包表达式，函数支持将其作为最后一个参数调用
	* 尾部闭包参数时函数式就用圆括号，是程序式就用花括号
	* 闭包使用示例：
	``` swift
	//闭包表达式
	func backwards(s1: String, s2: String) -> Bool {
	    return s1 > s2
	}
	var reversed = myArray.sort(backwards) 
	var reversed = myArray.sort({s1,s2 in return s1> s2 })
	//不允许使用参数缩写和运算符闭包
	var reversed = myArray.sort({$0 > $1}) //不好
	var reversed ＝ myArray.sort(>) //不好 
	//尾部闭包
	func functionWithTask(close:()->Void){
		//函数主体
	}
	//不使用尾随闭包进行调用
	functionWithTask({
		//闭包主体
	})
	//使用尾随闭包进行调用
	functionWithTask(){
		//闭包主体
	}
	```
* if switch判断语句使用规范
	* if判断语句判断条件只能为bool类型
	* 使用可选链式调用访问进行不确定性判断
	* switch中case后面规定不用break
	* switch中不允许使用空语句，完成没有意义
	* switch中最好不要使用贯穿，如果需要可以通过在case中添加多个匹配条件 
* 属性使用规范
	* 只读属性一律省略get关键字和大括号
	* setter属性一律使用便捷声明
	* 属性示例：
	``` swift
	//只读属性示例
	struct StructDemo{
		var point:Int = 0
		var center:Int{
				return point
		}
	}
	//setter便捷声明
	struct StructDemo{
		var point:Int = 0
		var center:Int{
			get {
				return point
			}
			set {
				point = newValue+2
			}
		}
	}
	```
* self使用规范
	* 当变压器可以自动推断成员类型时可以省略self，但是在方法调用会反射到一个实例时必须使用self
*构造和析构使用规范
	* 在类类型中，定义类的时候必须添加一个析构方法进行释放处理，如果没有需要释放的资源可以写个空的方法。保证定义的一致性。
* 变量使用规范
	* 除可选类型的变量外，其它变量在声明的时候默认提供一个初始值
	* 在定义可选类型变量的时候尽量使用？，防止使用！但而没有正确初始化的错误
	* 在可选链中使用？而不用！
	* 尽量避免使用多层可选链式调用
	* 规范示例：
	```swift
	  //?使用
	  var name: String? = "pengyuan"
	  if name != nil{
		  println(name!) //解包
	  }else{
		  println(nil)
	  }
	  //通过可选链式调用访问属性
	  if let count = py.residence?.number {
		    print(" \(count) ")
	   } else {
		    print("Unable to retrieve the number.")
		}
		//通过可选链式调用访问属性
		 if  py.residence?.number() != nil {
		    print("Enable to get the number ")
	     } else {
		    print("Unable to get the number.")
		 }
		 //通过可选链式调用访问下标
		 if let name = py.residence?[0].name {
		    print(" \(name).")
		  } else {
		    print("Unable to get the name.")
		  }
		  //多层调用(一般情况下尽量不用)
		  if let name = john.residence?.address?.name {
		    print(" \(name).")
		  } else {
		    print("Unable to get name)
		  }		  
    ```
 * 类型转换使用规范
	 * 其它类型向String转换的时候使用\()方式
	 * 在类型转换中尽量使用as?，如果需要使用as!则应该在使用前通过is进行判断
	 * AnyObject和Any的使用中，所有的类类型使用AnyObject，其它类型使用Any
	 * 类型转换使用示例：
	 ``` swift
	 age：String ＝ \(12)
	 for item in list{
	    if let movie = item as? Movie {
        //
     } else if item is Song {
        let song = item as! Song
	 }
	 let someObjects: [AnyObject] = [object1,object2]
	 var things:[Any] = []	 
	 things.append(0)
	 things.append(42)
	 things.append(3.14159)
	 things.append("hello")
	 ```
*  扩展使用规范
	*  不允许在类型扩展中添加构造器，不方便类型的管理
	*  扩展最好单纯的用于添加扩展方法，而不添加其它额外信息
