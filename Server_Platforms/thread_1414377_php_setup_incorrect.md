---
title: "php setup incorrect?"
date: 2010-02-23
forum: Server Platforms
---

### Post by edothas on 2010-02-23
I recently set up apache/mysql/php server on karmic and all seems to be running well, until I try to display an image with html in a php page. Firefox tells me the linked file (a png) is text format. Oddly enough, the same page works perfectly in a pure HTML page. Where do I start sorting this out?

---

### Post by tlsarles on 2010-02-23
does phpinfo(); work?

---

### Post by edothas on 2010-02-24
yes it does

---

### Post by mcarrara on 2010-02-24
I am not sure I understand the issue.  Say you have a page with a picture in an <img> tag.  If the extension is html it works been if you change the extension to php it does not?

Mark

---

### Post by edothas on 2010-02-25
It does work if the extension is html. If I change the extension to php, I can only see what's in the <img> tag if the image is in the same directory as the php file.

---

### Post by AlexDudko on 2010-02-25
Can you show the code and the markup of the page?

---

### Post by edothas on 2010-02-25
sure - this works in php:

<html>
<head></head>
<body>
<p>Aquarium Pages</p>
<p>
links to:<br />
	<a href=""><img src='Burn.png' alt="icon" width="45" height="45" /></a><br />
	<a href="">my aquarium</a><br />
</p>
</body>
</html>


and if i change the src= to /Burn.png or /png/Burn.png to doesn't.

---

### Post by AlexDudko on 2010-02-25
It's not a php problem since it doesn't generate the code.
Simply use a standard way of html coding:
```
<img src="Burn.png" alt="icon" width="45" height="45" />
```
And try also to keep from using uppercase characters - some severs don't "like" it.

---

### Post by tlsarles on 2010-02-25
> **edothas said:**
> sure - this works in php:
and if i change the src= to /Burn.png or /png/Burn.png to doesn't.

I think the problem is the leading /. If you start the path with a /, it starts from the filesystem root, which is probably not what you want. try 'png/Burn.png' not '/png/Burn.png'

---

### Post by edothas on 2010-02-26
That's got me sorted out. Thanks!

---

