---
title: "Confusion over where to start with developing apps"
date: 2013-07-10
forum: Ubuntu Application Development
---

### Post by astrolinux22 on 2013-07-10
Hi,

Please forgive what is probably a naive question bit I am new to app development and programming. Basically I am interested in writing applications for Ubuntu/Linux and my background is Python and Web (HTML/PHP/Javascript etc).

I have just written a Python program to change the desktop background by time of day and made an app indicator using GTK. However I know that Ubuntu is moving over to Qt/QML so I don't want to put a lot of effort into learning GTK if it is not going to stay around much longer. But I can't find much in the way of Qt integration with Python? For example how would I implement an app indicator in Python using Qt? 

Also my other question is if I write a python/qt app will that then run in Ubuntu Phone? Where will an app indicator sit on the phone interface? As I say I am new to this so sorry if it is a noob question. :-)

Thanks in advance.

Matt

---

### Post by huidagamal on 2013-07-13
> **astrolinux22 said:**
> Hi,

Please forgive what is probably a naive question bit I am new to app development and programming. Basically I am interested in writing applications for Ubuntu/Linux and my background is Python and Web (HTML/PHP/Javascript etc).[&#1605;&#1603;&#1575;&#1601;&#1581;&#1577; &#1575;&#1604;&#1581;&#1588;&#1585;&#1575;&#1578; &#1576;&#1575;&#1604;&#1585;&#1610;&#1575;&#1590;](http://www.nile7.com/content/%D8%A7%D9%81%D8%B6%D9%84-%D8%B4%D8%B1%D9%83%D8%A9-%D9%85%D9%83%D8%A7%D9%81%D8%AD%D8%A9-%D8%AD%D8%B4%D8%B1%D8%A7%D8%AA-%D8%A8%D8%A7%D9%84%D8%B1%D9%8A%D8%A7%D8%B6) [&#1603;&#1588;&#1601; &#1578;&#1587;&#1585;&#1576;&#1575;&#1578; &#1575;&#1604;&#1605;&#1610;&#1575;&#1607; &#1608; &#1575;&#1604;&#1594;&#1575;&#1586; &#1576;&#1575;&#1604;&#1585;&#1610;&#1575;&#1590;](http://www.nile7.com/content/%D9%82%D9%85%D8%A9-%D8%A7%D9%84%D8%A7%D9%86%D8%AC%D8%A7%D8%B2-%D9%84%D8%A7%D9%83%D8%AA%D8%B4%D8%A7%D9%81-%D8%AA%D8%B3%D8%B1%D8%A8-%D8%A7%D9%84%D9%85%D9%8A%D8%A7%D9%87-%D9%88%D8%A7%D9%84%D8%AA%D8%B1%D9%85%D9%8A%D9%85%D8%A7%D8%AA-%D8%A7%D9%84%D8%B9%D8%A7%D9%85%D8%A9-%D8%A8%D8%A7%D9%84%D8%B1%D9%8A%D8%A7%D8%B6) [&#1578;&#1606;&#1592;&#1610;&#1601; &#1602;&#1589;&#1608;&#1585; &#1576;&#1575;&#1604;&#1585;&#1610;&#1575;&#1590;](http://www.nile7.com/content/%D9%85%D8%A4%D8%B3%D8%B3%D8%A9-%D9%82%D9%85%D8%A9-%D8%A7%D9%84%D8%A7%D9%86%D8%AC%D8%A7%D8%B2-%D9%84%D9%84%D8%AA%D9%86%D8%B8%D9%8A%D9%81-%D8%A8%D8%A7%D9%84%D8%B1%D9%8A%D8%A7%D8%B6) [&#1593;&#1586;&#1604; &#1582;&#1586;&#1575;&#1606;&#1575;&#1578; &#1608;&#1575;&#1587;&#1591;&#1581; &#1576;&#1575;&#1604;&#1585;&#1610;&#1575;&#1590;](http://www.nile7.com/content/%D8%A7%D8%AC%D9%88%D8%AF-%D8%AE%D8%AF%D9%85%D8%A7%D8%AA-%D8%AA%D9%86%D8%B8%D9%8A%D9%81-%D9%88%D8%B9%D8%B2%D9%84-%D8%A7%D9%84%D8%AE%D8%B2%D8%A7%D9%86%D8%A7%D8%AA-%D8%A8%D8%A7%D9%84%D8%B1%D9%8A%D8%A7%D8%B6) [&#1588;&#1585;&#1603;&#1577; &#1606;&#1602;&#1604; &#1571;&#1579;&#1575;&#1579; &#1576;&#1575;&#1604;&#1585;&#1610;&#1575;&#1590;](http://www.nile7.com/content/%D8%B4%D8%B1%D9%83%D8%A9-%D8%A7%D9%84%D8%A7%D9%88%D9%84-%D9%84%D9%86%D9%82%D9%84-%D8%A7%D9%84%D8%A7%D8%AB%D8%A7%D8%AB-%D8%A8%D8%A7%D9%84%D8%B1%D9%8A%D8%A7%D8%B6)  [&#1588;&#1585;&#1603;&#1577; &#1578;&#1606;&#1592;&#1610;&#1601;]("https://www.facebook.com/alawelorg0558796867")[TABLE]
[TR]

[/TR]
[TR]

[/TR]
[TR]

[/TR]
[TR]

[/TR]
[TR]
[/TR]
[TR]
[TD="align: left"][/TD]
[/TR]
[/TABLE]

 I have just written a Python program to change the desktop background by time of day and made an app indicator using GTK. However I know that Ubuntu is moving over to Qt/QML so I don't want to put a lot of effort into learning GTK if it is not going to stay around much longer. But I can't find much in the way of Qt integration with Python? For example how would I implement an app indicator in Python using Qt? 

Also my other question is if I write a python/qt app will that then run in Ubuntu Phone? Where will an app indicator sit on the phone interface? As I say I am new to this so sorry if it is a noob question. :-)

Thanks in advance.

Matt[INDENT]                     Hi everyone.  In art school we used a language called processing to  do all kinds of neat things to images.  I have recently started playing  with Processing some more (processing.org) and have decided that I may  just want to include my sketches in an Ubuntu Touch app.  I don't have  any really specific questions for the community at this point, as I am  simply beginning my trial.  I do wonder if there are any other  programmers using Processing in these forums, and if anyone has already  (successfully) tried this?

So, for those unfamiliar with processing, you can export your sketch  (fancy name for a program in processing) to Javascript, which I believe I  can simply add into (import "processing.js" as Processing) This may be  totally wrong, and not work at all, I am not really sure, but it is  worth hacking around on for a bit (especially if it will work)                 
[/INDENT]

---

