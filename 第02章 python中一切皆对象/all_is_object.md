## 一切皆对象

### 一、理解一切皆对象

1. Python 的动态性，变量使用无需声明，一切变量都是对象（object 是所有类的基类，所有对象都是 type 的实例，也都是 object 的实例，包括它们自己），Python 面向对象更为彻底。
2. 函数和类都是对象，是 Python 的一等公民
   - 赋值给一个变量
   - 可以添加到集合对象中
   - 可以作为参数传递给函数
   - 可以作为函数的返回值

3. 元类、猴子补丁都是一切皆对象的体现

### 二、type、object、class

![1554802963919](C:\Users\SXN\AppData\Roaming\Typora\typora-user-images\1554802963919.png)

`type` 的作用：

- 生成一个类 `type(name:str, bases:tuple, dict) -> class/type`
- 返回一个对象的类型 `type(object)`

```python
type(1)     # <class 'int'>
type(int)   # <class 'type'>
type(str)   # <class 'type'>

class Student:
    pass
type(Student())   # <class '__main__.Student'>
type(Student)     # <class 'type'>

type(object)      # <class 'type'>
```

`type -> class -> obj`

- **`type` 是一个类，同时也是一个对象；`object` 是最顶层类，同时也是一个对象**
- **所有的类都是 `object` 的子类**

- **所有的对象都是 `type` 的实例（包括 `object`）**
- **结合 2、3 两点，所有的对象也都是 `object` 的实例**
- **以上几点就是 Python 一切皆对象的根本**

```python
type.__bases__       # (object,)
object.__bases__     # ()

# object 是最顶层类，所有类都是 object 的子类
issubclass(type, object)    # True
issubclass(object, type)    # False

# 所有对象都是 type 的实例
isinstance(type, type)      # True
isinstance(object, type)    # True

# 所有对象也都是 object 的实例
isinstance(type, object)    # True
isinstance(object, object)  # True
```

### 三、内置类型

> 对象的三个特征
>
> - 身份：即对象在内存中的地址  `id(obj)`
> - 类型：和静态语言有所不同
> - 值

内置类型：

- `None` （全局只有一个）

- 数值类型
  - `int`
  - `float`
  - `complex`
  - `bool`

- 迭代类型
- 序列类型
  - `list`
  - `bytes`、`bytearray`、`memoryview`
  - `range`
  - `tuple`
  - `str`
  - `array`
- 映射类型  `dict`
- 集合类型 
  - `set`
  - `frozenset`
- 上下文管理类型  `with`
- 其他
  - 模块类型
  - `class` 和实例
  - 函数类型
  - 方法类型
  - 代码类型
  - `object` 对象
  - `type` 类型
  - `ellipsis` 类型
  - `NotImplemented` 类型

