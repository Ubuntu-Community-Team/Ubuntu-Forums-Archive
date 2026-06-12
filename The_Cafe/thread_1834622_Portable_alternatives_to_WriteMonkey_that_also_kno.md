---
title: "Portable alternatives to WriteMonkey that also know Markdown"
date: 2011-08-27
forum: The Cafe
---

### Post by siddartha on 2011-08-27
I recently discovered Writemonkey and find it irezistible. Only that it depends on the ugly dot net.

I need something small (thus fast) that can do full screen editing and, most important, can export to HTML from the Markdown source. Sure, once you install perl you can make a script do that, but that's about the same as the issue with dot net. I want it as independent as possible so it can be moved across systems both old and new. Is there such an editor?

---

### Post by jerrrys on 2011-08-28
from what i see, writemonky is just a full screen text editor.  which linux has a few.  are there any special features that you are looking for?

[http://www.google.com/search?client=ubuntu&channel=fs&q=Writemonkey+linux&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Writemonkey+linux&ie=utf-8&oe=utf-8)

---

### Post by jerrrys on 2011-08-28
i like simple, heres my favorite

[ATTACH]200977[/ATTACH]

there are many more in the software center

---

### Post by keithpeter on 2011-08-28
Hello siddartha

I'm using markdown and a simple (and simplistic, I'm no expert) bash script to convert from markdown files to complete web pages with header and footer. Works ok for me.

Gedit has the capacity to work with shell commands and show the output in the editor. SO I'm thinking that you edit your markdown in Gedit then run a command that opens another tab with the HTML code in it. I'll have a play tomorrow as I'd like that as well...

```
#!/bin/bash
# usage: ./dopage.sh markdown-file-no-extension
TEXTFILE=${1}
# the first line of that file is always the title of the page, so goes in the title header
TITLE=`head -1 $TEXTFILE`
# write out the header part of the web page
echo "<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Transitional//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd\"> 
<html xmlns=\"http://www.w3.org/1999/xhtml\"> 
<head> 
<meta http-equiv=\"Content-Type\" content=\"text/html; charset=ISO-8859-1\" /> 
<title> 
$TITLE 
</title>
<link rel=\"stylesheet\" href=\"../style.css\" type=\"text/css\" media=\"screen\" /> 
</head> 
<body>
<p>[ <a href=\"../index.html\">home</a> ]</p> " | tee $TEXTFILE.html
# call markdown (on my system its on the bash path) on the text of the file
markdown $TEXTFILE | tee --append $TEXTFILE.html
# now add the footer
DATETEXT=$(date '+%a %b %d %Y')
echo "<hr /><p><small>Last updated: $DATETEXT</small></p>
</body>
</html>" | tee --append $TEXTFILE.html
chmod 777  $TEXTFILE.html
exit 0
```

---

### Post by siddartha on 2011-08-29
> **jerrrys said:**
> from what i see, writemonky is just a full screen text editor.  which linux has a few.  are there any special features that you are looking for?

Yes. I wrote: > can export to HTML from the Markdown source> **keithpeter said:**
> I'm using markdown and a simple (and simplistic, I'm no expert) bash script to convert from markdown files to complete web pages with header and footer. Works ok for me.

Sure, but once I put it on a stick and jump to another computer I might have quite a bit of a surprise if there's Windows and not Linux.

For me Writemonkey is perfect. Err, almost perfect. Only that it depends on dot net which makes it less portable. Markdown in itself also needs something installed which complicates the whole thing.

Let me rephrase: something that can build on multiple systems, can do full screen and once I write the text with Markdown to be able to push into the clipboard the text adorned with HTML tags instead of the Markdown.

---

### Post by potrick on 2011-08-29
I'm a big fan of WriteRoom, myself. 

[http://gottcode.org/focuswriter/](http://gottcode.org/focuswriter/)

Not sure if there's a portable version.

---

### Post by siddartha on 2011-08-29
Oh, FocusWriter is wonderful! I know it and have used it. It is highly customisable and really portable. Only that it does not do Markdown out of the box. That's why I have moved to WriteMonkey by the way.

---

### Post by juancarlospaco on 2011-08-29
Markup.py from Python does that...

---

### Post by juancarlospaco on 2011-08-29
> **keithpeter said:**
> 
```

chmod 777  $TEXTFILE.html

```

chmod 777  $TEXTFILE.html is not good,
 it also uses Windows charset, and HTML4 header.

---

