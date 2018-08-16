## 安装

```python
$ pipenv install requests-html
```
只支持python3.6及以上

## 使用方法
构造一个访问[python.org](https://python.org/)的GET请求，使用[Requests](https://docs.python-requests.org/):
```python
>>> from requests_html import HTMLSession
>>> session = HTMLSession()

>>> r = session.get('https://python.org/')
```
获取本页面所有的链接并返回一个列表, 保留了url在页面中原本的形式（已经自动去掉了html标签）:
```python
>>> r.html.links
['//docs.python.org/3/tutorial/', '/about/apps/', 'https://github.com/python/pythondotorg/issues', '/accounts/login/', '/dev/peps/', '/about/legal/', '//docs.python.org/3/tutorial/introduction.html#lists', '/download/alternatives', 'http://feedproxy.google.com/~r/PythonInsider/~3/kihd2DW98YY/python-370a4-is-available-for-testing.html', '/download/other/', '/downloads/windows/', 'https://mail.python.org/mailman/listinfo/python-dev', '/doc/av', 'https://devguide.python.org/', '/about/success/#engineering', 'https://wiki.python.org/moin/PythonEventsCalendar#Submitting_an_Event', 'https://www.openstack.org', '/about/gettingstarted/', 'http://feedproxy.google.com/~r/PythonInsider/~3/AMoBel8b8Mc/python-3.html', '/success-stories/industrial-light-magic-runs-python/', 'http://docs.python.org/3/tutorial/introduction.html#using-python-as-a-calculator', '/', 'http://pyfound.blogspot.com/', '/events/python-events/past/', '/downloads/release/python-2714/', 'https://wiki.python.org/moin/PythonBooks', 'http://plus.google.com/+Python', 'https://wiki.python.org/moin/', 'https://status.python.org/', '/community/workshops/', '/community/lists/', 'http://buildbot.net/', '/community/awards', 'http://twitter.com/ThePSF', 'https://docs.python.org/3/license.html', '/psf/donations/', 'http://wiki.python.org/moin/Languages', '/dev/', '/events/python-user-group/', 'https://wiki.qt.io/PySide', '/community/sigs/', 'https://wiki.gnome.org/Projects/PyGObject', 'http://www.ansible.com', 'http://www.saltstack.com', 'http://planetpython.org/', '/events/python-events', '/about/help/', '/events/python-user-group/past/', '/about/success/', '/psf-landing/', '/about/apps', '/about/', 'http://www.wxpython.org/', '/events/python-user-group/665/', 'https://www.python.org/psf/codeofconduct/', '/dev/peps/peps.rss', '/downloads/source/', '/psf/sponsorship/sponsors/', 'http://bottlepy.org', 'http://roundup.sourceforge.net/', 'http://pandas.pydata.org/', 'http://brochure.getpython.info/', 'https://bugs.python.org/', '/community/merchandise/', 'http://tornadoweb.org', '/events/python-user-group/650/', 'http://flask.pocoo.org/', '/downloads/release/python-364/', '/events/python-user-group/660/', '/events/python-user-group/638/', '/psf/', '/doc/', 'http://blog.python.org', '/events/python-events/604/', '/about/success/#government', 'http://python.org/dev/peps/', 'https://docs.python.org', 'http://feedproxy.google.com/~r/PythonInsider/~3/zVC80sq9s00/python-364-is-now-available.html', '/users/membership/', '/about/success/#arts', 'https://wiki.python.org/moin/Python2orPython3', '/downloads/', '/jobs/', 'http://trac.edgewall.org/', 'http://feedproxy.google.com/~r/PythonInsider/~3/wh73_1A-N7Q/python-355rc1-and-python-348rc1-are-now.html', '/privacy/', 'https://pypi.python.org/', 'http://www.riverbankcomputing.co.uk/software/pyqt/intro', 'http://www.scipy.org', '/community/forums/', '/about/success/#scientific', '/about/success/#software-development', '/shell/', '/accounts/signup/', 'http://www.facebook.com/pythonlang?fref=ts', '/community/', 'https://kivy.org/', '/about/quotes/', 'http://www.web2py.com/', '/community/logos/', '/community/diversity/', '/events/calendars/', 'https://wiki.python.org/moin/BeginnersGuide', '/success-stories/', '/doc/essays/', '/dev/core-mentorship/', 'http://ipython.org', '/events/', '//docs.python.org/3/tutorial/controlflow.html', '/about/success/#education', '/blogs/', '/community/irc/', 'http://pycon.blogspot.com/', '//jobs.python.org', 'http://www.pylonsproject.org/', 'http://www.djangoproject.com/', '/downloads/mac-osx/', '/about/success/#business', 'http://feedproxy.google.com/~r/PythonInsider/~3/x_c9D0S-4C4/python-370b1-is-now-available-for.html', 'http://wiki.python.org/moin/TkInter', 'https://docs.python.org/faq/', '//docs.python.org/3/tutorial/controlflow.html#defining-functions']
```
获取本页面所有的链接并返回一个列表, 自动将url转换为[绝对路径](https://www.navegabem.com/absolute-or-relative-links.html)形式（已经自动去掉了html标签）:
```python
>>> r.html.absolute_links
['https://github.com/python/pythondotorg/issues', 'https://docs.python.org/3/tutorial/', 'https://www.python.org/about/success/', 'http://feedproxy.google.com/~r/PythonInsider/~3/kihd2DW98YY/python-370a4-is-available-for-testing.html', 'https://www.python.org/dev/peps/', 'https://mail.python.org/mailman/listinfo/python-dev', 'https://www.python.org/doc/', 'https://www.python.org/', 'https://www.python.org/about/', 'https://www.python.org/events/python-events/past/', 'https://devguide.python.org/', 'https://wiki.python.org/moin/PythonEventsCalendar#Submitting_an_Event', 'https://www.openstack.org', 'http://feedproxy.google.com/~r/PythonInsider/~3/AMoBel8b8Mc/python-3.html', 'https://docs.python.org/3/tutorial/introduction.html#lists', 'http://docs.python.org/3/tutorial/introduction.html#using-python-as-a-calculator', 'http://pyfound.blogspot.com/', 'https://wiki.python.org/moin/PythonBooks', 'http://plus.google.com/+Python', 'https://wiki.python.org/moin/', 'https://www.python.org/events/python-events', 'https://status.python.org/', 'https://www.python.org/about/apps', 'https://www.python.org/downloads/release/python-2714/', 'https://www.python.org/psf/donations/', 'http://buildbot.net/', 'http://twitter.com/ThePSF', 'https://docs.python.org/3/license.html', 'http://wiki.python.org/moin/Languages', 'https://docs.python.org/faq/', 'https://jobs.python.org', 'https://www.python.org/about/success/#software-development', 'https://www.python.org/about/success/#education', 'https://www.python.org/community/logos/', 'https://www.python.org/doc/av', 'https://wiki.qt.io/PySide', 'https://www.python.org/events/python-user-group/660/', 'https://wiki.gnome.org/Projects/PyGObject', 'http://www.ansible.com', 'http://www.saltstack.com', 'https://www.python.org/dev/peps/peps.rss', 'http://planetpython.org/', 'https://www.python.org/events/python-user-group/past/', 'https://docs.python.org/3/tutorial/controlflow.html#defining-functions', 'https://www.python.org/community/diversity/', 'https://docs.python.org/3/tutorial/controlflow.html', 'https://www.python.org/community/awards', 'https://www.python.org/events/python-user-group/638/', 'https://www.python.org/about/legal/', 'https://www.python.org/dev/', 'https://www.python.org/download/alternatives', 'https://www.python.org/downloads/', 'https://www.python.org/community/lists/', 'http://www.wxpython.org/', 'https://www.python.org/about/success/#government', 'https://www.python.org/psf/', 'https://www.python.org/psf/codeofconduct/', 'http://bottlepy.org', 'http://roundup.sourceforge.net/', 'http://pandas.pydata.org/', 'http://brochure.getpython.info/', 'https://www.python.org/downloads/source/', 'https://bugs.python.org/', 'https://www.python.org/downloads/mac-osx/', 'https://www.python.org/about/help/', 'http://tornadoweb.org', 'http://flask.pocoo.org/', 'https://www.python.org/users/membership/', 'http://blog.python.org', 'https://www.python.org/privacy/', 'https://www.python.org/about/gettingstarted/', 'http://python.org/dev/peps/', 'https://www.python.org/about/apps/', 'https://docs.python.org', 'https://www.python.org/success-stories/', 'https://www.python.org/community/forums/', 'http://feedproxy.google.com/~r/PythonInsider/~3/zVC80sq9s00/python-364-is-now-available.html', 'https://www.python.org/community/merchandise/', 'https://www.python.org/about/success/#arts', 'https://wiki.python.org/moin/Python2orPython3', 'http://trac.edgewall.org/', 'http://feedproxy.google.com/~r/PythonInsider/~3/wh73_1A-N7Q/python-355rc1-and-python-348rc1-are-now.html', 'https://pypi.python.org/', 'https://www.python.org/events/python-user-group/650/', 'http://www.riverbankcomputing.co.uk/software/pyqt/intro', 'https://www.python.org/about/quotes/', 'https://www.python.org/downloads/windows/', 'https://www.python.org/events/calendars/', 'http://www.scipy.org', 'https://www.python.org/community/workshops/', 'https://www.python.org/blogs/', 'https://www.python.org/accounts/signup/', 'https://www.python.org/events/', 'https://kivy.org/', 'http://www.facebook.com/pythonlang?fref=ts', 'http://www.web2py.com/', 'https://www.python.org/psf/sponsorship/sponsors/', 'https://www.python.org/community/', 'https://www.python.org/download/other/', 'https://www.python.org/psf-landing/', 'https://www.python.org/events/python-user-group/665/', 'https://wiki.python.org/moin/BeginnersGuide', 'https://www.python.org/accounts/login/', 'https://www.python.org/downloads/release/python-364/', 'https://www.python.org/dev/core-mentorship/', 'https://www.python.org/about/success/#business', 'https://www.python.org/community/sigs/', 'https://www.python.org/events/python-user-group/', 'http://ipython.org', 'https://www.python.org/shell/', 'https://www.python.org/community/irc/', 'https://www.python.org/about/success/#engineering', 'http://www.pylonsproject.org/', 'http://pycon.blogspot.com/', 'https://www.python.org/about/success/#scientific', 'https://www.python.org/doc/essays/', 'http://www.djangoproject.com/', 'https://www.python.org/success-stories/industrial-light-magic-runs-python/', 'http://feedproxy.google.com/~r/PythonInsider/~3/x_c9D0S-4C4/python-370b1-is-now-available-for.html', 'http://wiki.python.org/moin/TkInter', 'https://www.python.org/jobs/', 'https://www.python.org/events/python-events/604/']
```
通过css选择器选取一个**Element对象**([了解更多](https://www.w3schools.com/cssref/css_selectors.asp)):
```python
>>> about = r.html.find('#about', first=True)
```
获取一个**Element对象**内的文本内容
```python
>>> print(about.text)
About
Applications
Quotes
Getting Started
Help
Python Brochure
```
获取一个**Element对象**的所有attributes([了解更多](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes)):
```
>>> about.attrs
{'id': 'about', 'class': ('tier-1', 'element-1'), 'aria-haspopup': 'true'}
```
渲染出一个**Element对象**的HTML内容:
```python
>>> about.html
'<li aria-haspopup="true" class="tier-1 element-1 " id="about">\n<a class="" href="/about/" title="">About</a>\n<ul aria-hidden="true" class="subnav menu" role="menu">\n<li class="tier-2 element-1" role="treeitem"><a href="/about/apps/" title="">Applications</a></li>\n<li class="tier-2 element-2" role="treeitem"><a href="/about/quotes/" title="">Quotes</a></li>\n<li class="tier-2 element-3" role="treeitem"><a href="/about/gettingstarted/" title="">Getting Started</a></li>\n<li class="tier-2 element-4" role="treeitem"><a href="/about/help/" title="">Help</a></li>\n<li class="tier-2 element-5" role="treeitem"><a href="http://brochure.getpython.info/" title="">Python Brochure</a></li>\n</ul>\n</li>'
```
获取**Element对象**内的特定子**Element对象**，返回列表:
```youtrack
>>> about.find('a')
[<Element 'a' href='/about/' title='' class=''>, <Element 'a' href='/about/apps/' title=''>, <Element 'a' href='/about/quotes/' title=''>, <Element 'a' href='/about/gettingstarted/' title=''>, <Element 'a' href='/about/help/' title=''>, <Element 'a' href='http://brochure.getpython.info/' title=''>]
```
查找一个**Element对象**内的绝对路径链接
```youtrack
>>> about.absolute_links
{'http://brochure.getpython.info/', 'https://www.python.org/about/gettingstarted/', 'https://www.python.org/about/', 'https://www.python.org/about/quotes/', 'https://www.python.org/about/help/', 'https://www.python.org/about/apps/'}
```
在获取的页面中查找文本
```youtrack
>>> r.html.search('Python is a {} language')[0]
programming
```
更加复杂的css选择器示例（从Chrome dev tools复制）
```youtrack
>>> r = session.get('https://github.com/')
>>> sel = 'body > div.application-main > div.jumbotron.jumbotron-codelines > div > div > div.col-md-7.text-center.text-md-left > p'

>>> print(r.html.find(sel, first=True).text)
GitHub is a development platform inspired by the way you work. From open source to business, you can host and review code, manage projects, and build software alongside millions of other developers.
```
同时也支持XPath（[了解更多](https://msdn.microsoft.com/en-us/library/ms256086(v=vs.110).aspx)）
```youtrack
>>> r.html.xpath('a')
[<Element 'a' class='btn' href='https://help.github.com/articles/supported-browsers'>]
```
你也可以获取到只包含某些文本的**Element对象**
```youtrack
>>> r = session.get('http://python-requests.org/')
>>> r.html.find('a', containing='kenneth')
[<Element 'a' href='http://kennethreitz.com/pages/open-projects.html'>, <Element 'a' href='http://kennethreitz.org/'>, <Element 'a' href='https://twitter.com/kennethreitz' class=('twitter-follow-button',) data-show-count='false'>, <Element 'a' class=('reference', 'internal') href='dev/contributing/#kenneth-reitz-s-code-style'>]
```


## 支持JavaScript
让我们获取一些通过JavaScript渲染的文本吧：
```youtrack
>>> r = session.get('http://python-requests.org/')

>>> r.html.render()

>>> r.html.search('Python 2 will retire in only {months} months!')['months']
'<time>25</time>'
```
注意，当你第一次调用`render()`方法时，代码将会自动下载Chromium，并保存在你的家目录下（如：~/.pyppeteer/）。它只会下载这一次。

## 分页
支持智能分页（持续改进中）
```youtrack
>>> r = session.get('https://reddit.com')
>>> for html in r.html:
...     print(html)
<HTML url='https://www.reddit.com/'>
<HTML url='https://www.reddit.com/?count=25&after=t3_81puu5'>
<HTML url='https://www.reddit.com/?count=50&after=t3_81nevg'>
<HTML url='https://www.reddit.com/?count=75&after=t3_81lqtp'>
<HTML url='https://www.reddit.com/?count=100&after=t3_81k1c8'>
<HTML url='https://www.reddit.com/?count=125&after=t3_81p438'>
<HTML url='https://www.reddit.com/?count=150&after=t3_81nrcd'>
…
```
你也可以很方便地请求下一个URL：
```youtrack
>>> r = session.get('https://reddit.com')
>>> r.html.next()
'https://www.reddit.com/?count=25&after=t3_81pm82'
```
不使用Requests库
你不需要Requests库也可以使用requests-html
```youtrack
>>> from requests_html import HTML
>>> doc = """<a href='https://httpbin.org'>"""

>>> html = HTML(html=doc)
>>> html.links
{'https://httpbin.org'}
```
你不需要Requests库也可以渲染JavaScript页面
```youtrack
# ^^ 接上边代码继续 ^^
>>> script = """
        () => {
            return {
                width: document.documentElement.clientWidth,
                height: document.documentElement.clientHeight,
                deviceScaleFactor: window.devicePixelRatio,
            }
        }
    """
>>> val = html.render(script=script, reload=False)

>>> print(val)
{'width': 800, 'height': 600, 'deviceScaleFactor': 1}

>>> print(html.html)
<html><head></head><body><a href="https://httpbin.org"></a></body></html>
```

## API 文档

这些类是`requests-html`主要的接口：
### ****HTML类****
class **requests_html.HTML**(\*,* session: Union[_ForwardRef('HTTPSession'),_ForwardRef('AsyncHTMLSession')] = None, url: str ='https://example.org/',html: Union[str, bytes], default_encoding: str = 'utf-8'*) → None &ensp;&ensp;[[源码](http://html.python-requests.org/_modules/requests_html.html#HTML)]
 
 用来解析HTML文档。
 ****参数说明****：
- **url** - HTML对应的URL，`absolute_links`函数会调用该参数
- **html** - 解析成字符串或字节（可选参数）
- **default_encoding** - 指定字符编码

#### ****absolute_links****

&ensp;&ensp;&ensp; 页面上所有可被获取到的超链接，都会被转成绝对路径形式。

#### ****base_url****

&ensp;&ensp;&ensp; 页面的基准URL，支持`<base>`标签（[了解更多](http://www.w3school.com.cn/tags/tag_base.asp)）。

#### ****encoding****

&ensp;&ensp;&ensp; 用于编码从HTML和html响应头中提取的内容

#### ****find****

****find****(selector: str = '\*', \*, containing: Union[str, typing.List[str]] = None, clean: bool = False, first: bool = False,_encoding: str = None) → Union[typing.List[_ForwardRef('Element')], _ForwardRef('Element')]

接收一个css选择器参数，返回一个**Element对象**或**Element对象**组成的列表。

****参数说明****：

- **selector** - css选择器
- **clean** - 对找到的`<script>`和`<style>`是否进行处理
- **containing** - 如果指定，则只会返回包含指定文本的**Element对象**
- **first** - 是否只返回第一个结果
- **_encoding** - 编码格式

CSS选择器示例：

- a
- a.someClass
- a#someID
- a[target=_blank]

查看CSS选择器的[更多](http://www.w3school.com.cn/cssref/css_selectors.asp)详细内容

如果`first`参数被置为`True`， 则只返回找到的第一个**Element对象**

#### ****full_text****

&ensp;&ensp;&ensp; 返回**Element对象**或HTML中的所有文本（包括链接）

#### ****html****

&ensp;&ensp;&ensp; 返回Unicode行式的HTML内容([了解更多](http://www.diveintopython3.net/strings.html))

#### ****links****

&ensp;&ensp;&ensp; 返回页面所有链接，并保留链接的原本形式

#### ****lxml****

&ensp;&ensp;&ensp; 返回[lxml](https://lxml.de/)行式的HTML内容

#### ****pq****

&ensp;&ensp;&ensp; 返回[PyQuery ](https://pythonhosted.org/pyquery/)行式的HTML内容

#### ****raw_html****

&ensp;&ensp;&ensp; 返回字节行式的HTML内容（[了解更多](http://www.diveintopython3.net/strings.html)）

#### ****render****

****render****(retries: int = 8, script: str = None, wait: float = 0.2, scrolldown=False, sleep: int = 0, 
reload: bool = True, timeout: Union[float, int] = 8.0, keep_page: bool = False)

&ensp;&ensp;&ensp;执行JavaScript，在Chromium里重新加载响应，并用最新获取到的HTML替换掉原来的HTML。

****参数说明****：

- **retries** - 在Chromium里加载页面的重试次数
- **script** - 执行页面上的JavaScript（可选参数）
- **wait** - 页面加载前的等待时间，防止超时（单位：秒，可选参数）
- **scrolldown** - 接收整数参数n。如果提供参数n，表示向后翻n页
- **sleep** - 接收整数参数n。如果提供参数n，则在`render`初始化后，程序会暂停n秒
- **reload** - 如果为False，则不会重新从浏览器加载内容，而是读取内存里的内容
- **keep_page** - 如果为True，将会允许你通过`r.html.page`与浏览器页面交互

如果`scrolldown`和`sleep`都指定，那么程序会在暂停相应时间后，再往后翻页面（如：`scrolldown=10, sleep=1`）

如果仅指定了`sleep`，程序会暂停相应时间，再返回数据

如果指定`script`，他将会在运行时执行提供的JavaScript。如：
```youtrack
script = """
    () => {
        return {
            width: document.documentElement.clientWidth,
            height: document.documentElement.clientHeight,
            deviceScaleFactor: window.devicePixelRatio,
        }
    }
"""
```
返回一段JavaScript的返回值：
```youtrack
>>> r.html.render(script=script)
{'width': 800, 'height': 600, 'deviceScaleFactor': 1}
```
&ensp;&ensp;&ensp; ****警告****：如果你使用`keep_page`, 你最好关闭已经使用过的页面，如果打开过多页面会造成浏览器崩溃。

&ensp;&ensp;&ensp; ****警告****：如果你第一次运行这个方法，它将会下载Chromium保存在你的家目录下。

#### ****search****

****search****(*template: str*)  → parse.Result 

&ensp;&ensp;&ensp; 根据传入的模板参数，查找**Element对象**

****参数说明****：

- **template** - 模板参数

#### ****search_all****

****search_all****(*template: str*)  → Union[typing.List[_ForwardRef('Result')], _ForwardRef('Result')] 

&ensp;&ensp;&ensp; 根据传入的模板参数，查找所有的**Element对象**

****参数说明****：

- **template** - 模板参数

#### ****xpath****

****xpath****(selector: str, *, clean: bool = False, first: bool = False, _encoding: str = None) → Union[typing.List[str], typing.List[_ForwardRef('Element')], str, _ForwardRef('Element')]

&ensp;&ensp;&ensp; 传入一个XPath选择器参数，返回所有的**Element对象**

****参数说明****：

- **selector** - xpath选择器
- **clean** - 对找到的`<script>`和`<style>`是否进行处理
- **first** - 是否只返回第一个结果
- **_encoding** - 编码格式

如果指定了一个子选择器（如：`//a/@href`），将返回一个简单的结果列表

查看更多细节[Xpath示例](http://www.w3school.com.cn/xpath/)

如果`first`参数被置为`True`， 则只返回找到的第一个**Element对象**

### ****Element类****
class **requests_html.Element**(\*, element, url: str, default_encoding: str = None) → None &ensp;&ensp;[源码](http://html.python-requests.org/_modules/requests_html.html#Element)
 
 HTML的一个element对象。
 
 ****参数说明****：
- **element** - 根据该参数进行解析
- **url** - HTML对应的URL，`absolute_links`函数会调用该参数
- **default_encoding** - 指定字符编码

#### ****absolute_links****

&ensp;&ensp;&ensp; 返回一个字典，该字典包括**Element对象**的所有html属性。

#### ****attrs****

&ensp;&ensp;&ensp; 页面上所有可被获取到的超链接，都会被转成绝对路径形式。

#### ****base_url****

&ensp;&ensp;&ensp; 页面的基准URL，支持`<base>`标签（[了解更多](http://www.w3school.com.cn/tags/tag_base.asp)）。

#### ****encoding****

&ensp;&ensp;&ensp; 用于编码从HTML和html响应头中提取的内容

#### ****find****

****find****(selector: str = '\*', \*, containing: Union[str, typing.List[str]] = None, clean: bool = False, first: bool = False,_encoding: str = None) → Union[typing.List[_ForwardRef('Element')], _ForwardRef('Element')]

接收一个css选择器参数，返回一个**Element对象**或**Element对象**组成的列表。

****参数说明****：

- **selector** - css选择器
- **clean** - 对找到的`<script>`和`<style>`是否进行处理
- **containing** - 如果指定，则只会返回包含指定文本的**Element对象**
- **first** - 是否只返回第一个结果
- **_encoding** - 编码格式

CSS选择器示例：

- a
- a.someClass
- a#someID
- a[target=_blank]

查看CSS选择器的[更多](http://www.w3school.com.cn/cssref/css_selectors.asp)详细内容

如果`first`参数被置为`True`， 则只返回找到的第一个**Element对象**

#### ****full_text****

&ensp;&ensp;&ensp; 返回**Element对象**或HTML中的所有文本（包括链接）

#### ****html****

&ensp;&ensp;&ensp; 返回Unicode行式的HTML内容([了解更多](http://www.diveintopython3.net/strings.html))

#### ****links****

&ensp;&ensp;&ensp; 返回页面所有链接，并保留链接的原本形式

#### ****lxml****

&ensp;&ensp;&ensp; 返回[lxml](https://lxml.de/)行式的HTML内容

#### ****pq****

&ensp;&ensp;&ensp; 返回[PyQuery ](https://pythonhosted.org/pyquery/)行式的HTML内容

#### ****raw_html****

&ensp;&ensp;&ensp; 返回字节行式的HTML内容（[了解更多](http://www.diveintopython3.net/strings.html)）

#### ****search****

****search****(*template: str*)  → parse.Result 

&ensp;&ensp;&ensp; 根据传入的模板参数，查找**Element对象**

****参数说明****：

- **template** - 模板参数

#### ****search_all****

****search_all****(*template: str*)  → Union[typing.List[_ForwardRef('Result')], _ForwardRef('Result')] 

&ensp;&ensp;&ensp; 根据传入的模板参数，查找所有的**Element对象**

****参数说明****：

- **template** - 模板参数

#### ****text****

&ensp;&ensp;&ensp; 返回**Element对象**或**HTML对象**的文本内容（不包含html标签）

#### ****xpath****

****xpath****(selector: str, *, clean: bool = False, first: bool = False, _encoding: str = None) → Union[typing.List[str], typing.List[_ForwardRef('Element')], str, _ForwardRef('Element')]

&ensp;&ensp;&ensp; 传入一个XPath选择器参数，返回所有的**Element对象**

****参数说明****：

- **selector** - xpath选择器
- **clean** - 对找到的`<script>`和`<style>`是否进行处理
- **first** - 是否只返回第一个结果
- **_encoding** - 编码格式

如果指定了一个子选择器（如：`//a/@href`），将返回一个简单的结果列表

查看更多细节[Xpath示例](http://www.w3school.com.cn/xpath/)

如果`first`参数被置为`True`， 则只返回找到的第一个**Element对象**

## 比较实用的方法

### ****user_agent****

****requests_html.user_agent****(style=None) → str &ensp;&ensp; [源码](http://html.python-requests.org/_modules/requests_html.html#user_agent)

返回一个指定风格的合法的用户代理，默认是Chrome风格的用户代理

## HTML Sessions

这些sessions用于构造http请求。

class ****requests_html.HTMLSession****(mock_browser=True) &ensp;&ensp; [源码](http://html.python-requests.org/_modules/requests_html.html#HTMLSession)

它是一个可被销毁的session，可用于cookie持久化和连接池，以及其他地方。

### ****close()****

&ensp;&ensp;&ensp; 关闭一个已经被创建的浏览器

### ****delete(url, \*\*kwargs)****

&ensp;&ensp;&ensp; 发送一个DELETE请求，返回一个`Response`对象

&ensp;&ensp;&ensp; ****参数说明****：

- **url** - 新的`请求对象`的URL

- **\*\*kwargs** - `request`携带的参数（可选）

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `requests.Response`

### ****get_adapter(url)****

&ensp;&ensp;&ensp; 返回指定url的一个合适的连接适配器

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp;  `requests.adapters.BaseAdapter`

### ****get_redirect_target(resp)****

&ensp;&ensp;&ensp; 接收一个响应，返回重定向后的URL或none

### ****head(url, \*\*kwargs)****

&ensp;&ensp;&ensp; 发送一个HEAD请求，返回一个`Response`对象

&ensp;&ensp;&ensp; ****参数说明****：

- **url** - 新的`请求对象`的URL

- **\*\*kwargs** - `request`携带的参数（可选）

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `requests.Response`

### ****merge_environment_settings(url, proxies, stream, verify, cert)****

&ensp;&ensp;&ensp; 检查环境变量并与其他设置合并

&ensp;&ensp;&ensp; ****返回类型****：字典

### ****mount(prefix, adapter)****

&ensp;&ensp;&ensp; 在前缀上注册连接适配器

&ensp;&ensp;&ensp; 适配器根据前缀长度降序排序

### ****options(url, \*\*kwargs)****

&ensp;&ensp;&ensp; 发送一个OPTIONS请求，返回一个`Response`对象

&ensp;&ensp;&ensp; ****参数说明****：

- **url** - 新的`请求对象`的URL

- **\*\*kwargs** - `request`携带的参数（可选）

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `requests.Response`

### ****patch(url, data=None, \*\*kwargs)****

&ensp;&ensp;&ensp; 发送一个PATCH请求，返回一个`Response`对象

&ensp;&ensp;&ensp; ****参数说明****：

- **url** - 新的`请求对象`的URL

- **data** - 它被包含在`请求对象`中，它可以是字典、字节、文件（可选参数）

- **\*\*kwargs** - `request`携带的参数（可选）

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `requests.Response`

### ****post(url, data=None, json=None, \*\*kwargs)****

&ensp;&ensp;&ensp; 发送一个POST请求，返回一个`Response`对象

&ensp;&ensp;&ensp; ****参数说明****：

- **url** - 新的`请求对象`的URL

- **data** - 它被包含在`请求对象`中，它可以是字典、字节、文件（可选参数）

- **json** - 它被包含在`请求对象`中，它是json（可选参数）

- **\*\*kwargs** - `request`携带的参数（可选）

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `requests.Response`

### ****prepare_request(request)****

&ensp;&ensp;&ensp; 构造一个`预请求`对象（PreparedRequest）。这个预请求对象的设置来自于已经设置好session的`请求实例`。

&ensp;&ensp;&ensp; ****参数说明****：

- **request** - 已经设置好session的`请求实例`

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `requests.PreparedRequest`

### ****put(url, data=None, \*\*kwargs)****

&ensp;&ensp;&ensp; 发送一个PUT请求，返回一个`Response`对象

&ensp;&ensp;&ensp; ****参数说明****：

- **url** - 新的`请求对象`的URL

- **data** - 它被包含在`请求对象`中，它可以是字典、字节、文件（可选参数）

- **\*\*kwargs** - `request`携带的参数（可选）

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `requests.Response`

### ****rebuild_auth(prepared_request, response)****

&ensp;&ensp;&ensp; 当被重定向的时候，我们可能要从`请求对象`中去掉认证信息，避免认证信息泄露。
本方法会自动去掉认证信息，并且重新申请授权，来避免认证信息泄露。

### ****rebuild_method(prepared_request, response)****

&ensp;&ensp;&ensp; 当被重定向的时候，我们可能要修改请求的方法，用来请求某个特殊的页面，或者适应某个
特殊的浏览器习惯。

### ****rebuild_proxies(prepared_request, response)****

&ensp;&ensp;&ensp; 本方法会根据环境变量重新设置代理的配置。如果我们被重定向到一个不需要代理的URL，
我们将去掉代理的配置，否则，我们将给该URL添加缺失的代理配置（防止由于之前重定向去掉了代理而造成的请求错误）。

必要时，本方法可以替换`Proxy-Authorization`头。
&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `字典`

### ****request(\*args, \*\*kwargs)****

request(*args, **kwargs) → requests_html.HTMLResponse

&ensp;&ensp;&ensp; 使用欺骗性地`User–Agent`头，构造一个HTTP请求。返回`HTTPResponse类`对象<HTTPResponse>。

### ****resolve_redirects****

resolve_redirects(resp, req, stream=False, timeout=None, verify=True, cert=None, proxies=None, yield_requests=False, **adapter_kwargs)

&ensp;&ensp;&ensp; 接收一个响应对象，返回响应对象或请求对象的生成器。

### ****send(request, \*\*kwargs)****

&ensp;&ensp;&ensp; 发送`预请求对象`。必要时，本方法可以替换`Proxy-Authorization`头。

&ensp;&ensp;&ensp; ****返回类型****：

&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; `	requests.Response`



















