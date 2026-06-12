---
title: "character encoding"
date: 2005-04-21
forum: The Cafe
---

### Post by primeirocrime on 2005-04-21
So...I want it easy once again. 

I really like having UTF-8 in my system, but now I designing web pages and everyone else here in Portugal uses windows 1252 or ISO 8859. I'm wondering if I can still maintain the UTF-8 but convert the characters like Çç ÀÁáà in their &Ccedil; &ccedil; or even the numeric form  &_#_199_;
is there any way to have the text beeing converted from one to another form? some command line utility, script, plugin to do this for me? I'm doing it by hand now but it's a pain in my eyes to handpic all the buggers we have in portuguese. 


thanks in advance.

---

### Post by nautilus on 2005-04-21
Well, with the correct header, their browser should have no trouble rendering a UTF8 document.

An example:

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
   "http://www.w3.org/TR/html4/loose.dtd">
<meta http-equiv="content-type" content="text/html; charset=UTF-8">

and/or, in your webserver, have it state that .html files are UTF8 encoded.

if none of this works for you, then yes, you can convert them :)

look up UNICODE CHART HTML on your search engine of choice

---

### Post by Alexander Kirillov on 2005-04-21
[QUOTE=primeirocrime]So...I want it easy once again. 

I really like having UTF-8 in my system, but now I designing web pages and everyone else here in Portugal uses windows 1252 or ISO 8859. I'm wondering if I can still maintain the UTF-8 but convert the characters like Çç ÀÁáà in their &Ccedil; &ccedil; or even the numeric form  &_#_199_;
is there any way to have the text beeing converted from one to another form? some command line utility, script, plugin to do this for me? I'm doing it by hand now but it's a pain in my eyes to handpic all the buggers we have in portuguese. 


thanks in advance.[/QUOTE]
You can use package "recode".  See manual here [http://www.delorie.com/gnu/docs/recode/recode_toc.html#SEC_Contents](http://www.delorie.com/gnu/docs/recode/recode_toc.html#SEC_Contents) (especially -d option). 

However, all browsers of the last 2 years should (including Netscape and IE) shoudl render documents in UTF8 encoding without any problems -- even on the system using a different encoding. Of course, document encoding should be in the header.

---

### Post by primeirocrime on 2005-04-22
Thank you both for your help. I tried with multiple browsers and the only ones like links or dillo and of course some IE from 1998 gave problems with my Çç áà characters. Since I define the encoding in the document the browser reads it proper. I do enjoy learning :) 

I'm still amazed with this ubuntu community :) 


I'll try "recode" anyway.

---

