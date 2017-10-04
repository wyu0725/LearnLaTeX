# LearnLaTeX
Sublime Text3 + TeXLive配置

2017年9月19日

21:49

1.  首先是安装Sublime Text 3，破解的话网上找一个，本来打算买一个的，但是80刀略贵，不过不激活个人用户也可以用，只是软件上显示一个未激活

2.  安装Package Control

    a.  CTRL+ \`调出安装控制台

    b.  输入如下内容回车，如有错误谷歌查之

> import urllib.request,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed\_packages\_path(); urllib.request.install\_opener( urllib.request.build\_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( '[*http://sublime.wbond.net/*](http://sublime.wbond.net/)' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

1.  按住Ctrl+Shift+P调出Package Control

    a.  如果调不出来，多半是因为新版本将Package Control屏蔽了

    b.  在Preferences -&gt; Settings中将如下代码中的Package Control去掉

> "ignored\_packages":
>
> \[
>
> "Package Control",
>
> "Vintage"
>
> \]

1.  在Package Control中输入install进入Package Control:Install Package

2.  安装LaTeXTools

3.  顺便安装如下两个包

    a.  ConvertToUTF8 : 可以将其他的编码格式的文件转换为 UTF8。

    b.  Markdown Preview： 可以使用 Sublime Text 将 Markdown 文件编译成 html 文件实现预览。

<!-- -->

1.  下载TeXLive,上[*科大镜像*](http://mirrors.ustc.edu.cn/CTAN/)者[*清华镜像*](https://mirrors.tuna.tsinghua.edu.cn/CTAN/)下载会快一点，安装过程大约1小时

2.  配置LaTeXTools

    a.  在Preferences -&gt; Package Settings -&gt; LaTeXTools中点击Reconfigure and migrate settings

    b.  然后Package Settings-&gt;LaTeXTools-&gt;Settings - User

    c.  找到Windows字段

    d.  填入如下设置

> "windows": {
>
> // Path used when invoking tex & friends; "" is fine for MiKTeX
>
> // For TeXlive 2011 (or other years) use
>
> // "texpath" : "C:\\\\texlive\\\\2011\\\\bin\\\\win32;\$PATH",
>
> "texpath" : "TeXLive安装路径",
>
> // TeX distro: "miktex" or "texlive"
>
> "distro" : "texlive",
>
> // Command to invoke Sumatra. If blank, "SumatraPDF.exe" is used (it has to be on your PATH)
>
> "sumatra": "",
>
> // Command to invoke Sublime Text. Used if the keep\_focus toggle is true.
>
> // If blank, "subl.exe" or "sublime\_text.exe" will be used.
>
> "sublime\_executable": "",
>
> // how long (in seconds) to wait after the jump\_to\_pdf command completes
>
> // before switching focus back to Sublime Text. This may need to be
>
> // adjusted depending on your machine and configuration.
>
> "keep\_focus\_delay": 0.5
>
> },

1.  其中sumatra设置留空是因为可以直接将其填入PATH中

2.  在[*SumatraPDF*](https://www.sumatrapdfreader.org/free-pdf-reader.html)下载合适版本的SumatraPDF版本

3.  然后在环境变量PATH中填入安装路径

<!-- -->

1.  在命令行中运行，其中Sublime Text 3的路径改成自己的安装路径，这样可以SumatraPDF反向检索Sublime

> sumatrapdf.exe -inverse-search "\\"C:\\Program Files\\Sublime Text 3\\sublime\_text.exe\\" \\"%f:%l\\""
>
>  
>
> **大功告成啦**
>
> 新建一个HelloWorld.tex写入如下内容
>
> % 使用 ctexart 文类，UTF-8 编码
>
> \\documentclass\[UTF8\]{ctexart}
>
> \\begin{document}
>
> Hello World!
>
>  
>
> 你好！
>
> \\end{document}
>
> 按Ctrl + B即可编译

另外在Preferences -&gt; Settings中可以修改字体等信息

"color\_scheme": "Packages/Color Scheme - Default/Monokai.tmTheme",

"font\_face": "InputSerif",

"font\_size": 9,

 