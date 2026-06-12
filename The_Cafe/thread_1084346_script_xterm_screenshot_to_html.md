---
title: "script: xterm screenshot to html"
date: 2009-03-01
forum: The Cafe
---

### Post by eexpress on 2009-03-01
if anyone like this? 
effect picture:
[http://forum.ubuntu.org.cn/download/file.php?id=57406&mode=view/ansi2html.png](http://forum.ubuntu.org.cn/download/file.php?id=57406&mode=view/ansi2html.png)

```

&#9742; grep -i "^xterm.*print" .Xdefaults 
XTerm*VT100.Translations: #override Ctrl <KeyPress> P: print() \n
xterm*printerCommand: xterm2html.bash
xterm*printAttributes: 2
xterm*printerExtent: true

&#9742; dog xterm2html.bash 
cat > ~/xterm-screenshot.copy
cat ~/xterm-screenshot.copy|ansi2html.bash > ~/xterm-screenshot.html
```

ansi2html.bash
[HTML]
#!/bin/bash

# Convert ANSI (terminal) colour codes to HTML
# Last Modify: eexpress @ 2009-02-27
# Author:
#    http://www.pixelbeat.org/docs/terminal_colours/

echo -n "
<head>
<style type=\"text/css\">
/* linux console palette */
.f0 { color: #000000; }
.f1 { color: #FF0000; }
.f2 { color: #00AA00; }
.f3 { color: #E5E414; }
.f4 { color: #5B5BFC; }
.f5 { color: #FF00FF; }
.f6 { color: #01FEFD; }
.f7 { color: #AAAAAA; }
.bf0 { color: #555555; }
.bf1 { color: #FF5555; }
.bf2 { color: #55FF55; }
.bf3 { color: #FFFF55; }
.bf4 { color: #5555FF; }
.bf5 { color: #FF55FF; }
.bf6 { color: #55FFFF; }
.bf7 { color: #FFFFFF; }
.b0 { background-color: #000000; }
.b1 { background-color: #AA0000; }
.b2 { background-color: #00AA00; }
.b3 { background-color: #CDCD00; }
.b4 { background-color: #0000AA; }
.b5 { background-color: #AA00AA; }
.b6 { background-color: #00AAAA; }
.b7 { background-color: #E5E5E5; }
.bold { font-weight:bold; }
.normal { font-weight:normal; color: #AAAAAA; background-color: #000000; }
.reverse { background-color: #2A2A2A; }
.underline { text-decoration: underline; }
.line-through { text-decoration: line-through; }
.blink { text-decoration: blink; }
</style>
<title>xterm ansi color screenshot -> html</title>
</head>
<html>
<body bgcolor=\"#000000\" text=\"#ffffff\">
<pre>
"
#<meta content="charset=UTF-8">
#<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
#<meta http-equiv="content-type" content="text/html; charset=UTF-8">
p='&#8599;[^&#8598;]*\<'
e='\>[^&#8598;]*'
echo '<span>'
sed 's/\xef\xbf\xbf//g'|\
sed 's#\&#\&amp;#g; s#>#\&gt;#g; s#<#\&lt;#g'|\
#sed 's#\"#\&quot;#g; s#\ +#\&nbsp;#g'|\
sed 's#\x1b\#[0-9]##g'|\
#sed 's#\x1b\[0m##g'|\
sed 's#\x1b\[\([0-9;]*\)m#&#8599;\1&#8598;#g'|\
sed "s#${p}1${e}#& bold#g"|\
sed "s#${p}4${e}#& underline#g"|\
sed "s#${p}5${e}#& blink#g"|\
sed "s#${p}7${e}#& reverse#g"|\
sed "s#${p}9${e}#& line-through#g"|\
sed "s#${p}3\([0-7]\)${e}#& f\1#g"|\
sed "s#${p}4\([0-7]\)${e}#& b\1#g"|\
#sed "s#&#8599;0&#8598;##g"|\
sed "s#&#8599;[0-9;\ ]\+#</span><span class=\"#g"|\
sed "s#&#8598;#\">#g"|\
#sed "s#^#</span><span class=\"normal\">#g"|\
tr -d "\r"|\
cat
echo '</span>'

echo "</pre>
</body>
</html>
"

[/HTML]

---

### Post by pixelbeat on 2009-03-02
Thanks for the update. The changes look interesting and I'll try to integrate them back into my script. Please keep me updated on any enhancements (email = [email]P@draigBrady.com[/email]).

BTW I don't usually enable the bold attribute as it's generally used to get a bright color on a terminal rather than making the text bold.

---

### Post by eexpress on 2009-03-04
pixelbeat,  your original idea of using class is so nice.  :P 

i like accuratlly playback the result include "blod".  lol

---

