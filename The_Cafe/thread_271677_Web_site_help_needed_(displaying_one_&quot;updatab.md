---
title: "Web site help needed (displaying one &quot;updatable&quot; frame accross pages)"
date: 2006-10-05
forum: The Cafe
---

### Post by towsonu2003 on 2006-10-05
Hi,

I am extremely new to web page writing. I basically got a web page template from "Open Source Web Design" and playing around that. 

The design I have has a news coloumn displayed in every page of the web site. To add news, you have to change the <news> section of each and every page... 

Is there a way to tell the browser to display a web page as a frame inside all the web pages I've got? For example, instead of
```

<h1>Latest news</h1>

<p><strong>Feb 15, 2007: </strong>

Oppsie</p>
<p><strong>Dec 29, 2006: </strong>

Duh!</p>

<p><strong>Oct 05, 2006: </strong>

Ha Ha!</p>

```
in each page, display this:
```

<command>get this frame from /link/</command>

```

So in order to change the news section in each web page I have, I have to change only one document, the /link/

I appreciate any help you can give,

thanks :)

Ps. the design is using css. but just like with html, I am clueless about css as well..

---

### Post by argie on 2006-10-05
I'm not sure, but you could put the HTMl in another file and use:

```
<iframe src="/path/to/otherfile.html" />
```

or using php use the include("thefile.html") statement.

---

### Post by maniacmusician on 2006-10-05
you could also make a div section, put it wherever you need to, and use an include command. 

```

<div style="float: left">
     <!--#include virtual="path to file"-->
</div>

```
but all files that use the include command must end in ".shtml" or it wont work.

edit: the float left is to put it on the left side, because i'm assuming thats where you want it. it could really be anywhere.
Also, you wont be able to see the effects of it until after you put it on the  internet. so the shtml include doesnt work while its still on your computer.

---

### Post by towsonu2003 on 2006-10-05
> **argie said:**
> I'm not sure, but you could put the HTMl in another file and use:

```
<iframe src="/path/to/otherfile.html" />
```

or using php use the include("thefile.html") statement.

I'll try to go with the iframe reccomendation, it seems more "easy" to me :) thanks so much for both replies

Though I'm having problems validating it as xhtml1.1... keeps saying [there is no attribute "src"] etc and [element "iframe" undefined]. this is bc I'm clueless :) I'll do research and check out valid templates that use frames + css / xhtml :)

edit: oh well, xhtml1.1 I'm using doesn't accept iframes, and when I change it to xhtml1.0 frameset, then the rest of the document gets flamed by w3c validator... I'll try the php method :)

---

