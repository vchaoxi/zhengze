# 表示边界

|字符|功能|
| - | - |
|^|匹配字符串开头|
|$|匹配字符串结尾|
|\b|匹配一个单词的边界|
|\B|匹配非单词边界|

## 示例1：$

需求：匹配163.com的邮箱地址

```python

#coding=utf-8

import re

# 正确的地址
ret = re.match("[\w]{4,20}@163\.com", "xiaoWang@163.com")
ret.group()

# 不正确的地址
ret = re.match("[\w]{4,20}@163\.com", "xiaoWang@163.comheihei")
ret.group()

# 通过$来确定末尾
ret = re.match("[\w]{4,20}@163\.com$", "xiaoWang@163.comheihei")
ret.group()

```

运行结果：

![](/assets/Snip20160906_142.png)

## 示例2: \b

```python

>>> re.match(r".*\bver\b", "ho ver abc").group()
'ho ver'

>>> re.match(r".*\bver\b", "ho verabc").group()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'

>>> re.match(r".*\bver\b", "hover abc").group()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'
>>>

```

## 示例3：\B

```python

>>> re.match(r".*\Bver\B", "hoverabc").group()
'hover'

>>> re.match(r".*\Bver\B", "ho verabc").group()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'

>>> re.match(r".*\Bver\B", "hover abc").group()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'

>>> re.match(r".*\Bver\B", "ho ver abc").group()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'

```