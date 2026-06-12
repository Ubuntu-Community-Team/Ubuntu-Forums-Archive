---
title: "Anyone gotten user scripts to work in Chromium?"
date: 2009-09-26
forum: The Cafe
---

### Post by SomeGuyDude on 2009-09-26
Just curious. I'm on the latest snapshot and trying to get a few of my favorite scripts rolling, no luck so far.

---

### Post by kerry_s on 2009-09-27
did you do the enable thing "-enable-greasemonkey" i think it is?
sorry, i only added the "adsweep" on mine & it was just click on the adsweep.crx. [http://www.adsweep.org/](http://www.adsweep.org/)

but i have a question, do you get like a pause when the page is loading, where it's like unresponsive?
i only been using chrome a day, so just wondering if thats normal or perhaps cause i'm using a crappy 450mhz 256mb ram laptop. :lolflag:

---

### Post by renkinjutsu on 2009-09-27
user scripts work for me..

the parameters i open chromium with:
```
chromium-browser --enable-plugins --enable-extentions --enable-user-scripts
```

---

### Post by HappinessNow on 2009-09-27
> **renkinjutsu said:**
> user scripts work for me..

the parameters i open chromium with:
```
chromium-browser --enable-plugins --enable-extentions --enable-user-scripts
```Maybe a screenshot step-by-step How-to would be more helpful for some people?

---

### Post by renkinjutsu on 2009-09-27
Here's a good step-by-step...
I found out about user scripts in chromium only after seeing this

[http://penguininside.blogspot.com/2009/09/best-way-to-create-perfect-chromium.html]("http://penguininside.blogspot.com/2009/09/best-way-to-create-perfect-chromium.html")

---

### Post by kerry_s on 2009-09-27
> **renkinjutsu said:**
> Here's a good step-by-step...
I found out about user scripts in chromium only after seeing this

[http://penguininside.blogspot.com/2009/09/best-way-to-create-perfect-chromium.html]("http://penguininside.blogspot.com/2009/09/best-way-to-create-perfect-chromium.html")

i thought you was suppose to put the settings in /etc/chromium-browser/default like it says here->
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

> * To pass flags to Chromium, please don't tweak the launcher, but edit /etc/chromium-browser/default instead

---

### Post by SomeGuyDude on 2009-09-27
Hm.

I've tried a few scripts from UserScripts.org with the "--enable-user-scripts" flag and it doesn't seem to work. Maybe I'm just trying the wrong scripts, I dunno.

---

### Post by b2bwild on 2009-10-03
> **renkinjutsu said:**
> Here's a good step-by-step...
I found out about user scripts in chromium only after seeing this

[http://penguininside.blogspot.com/2009/09/best-way-to-create-perfect-chromium.html]("http://penguininside.blogspot.com/2009/09/best-way-to-create-perfect-chromium.html")

:P, Actually I'm the author of this guide.

You should know that you need userscripts which are specifically made for Chromium, the scripts you get on userscript.org, are mostly for Firefox and rarely for Opera and Safari (on Mac).

There are not so many scripts for Chromium, 
There is Greasemetal [http://greasemetal.31tools.com/](http://greasemetal.31tools.com/) (Chromee Version of Greasemonkey)

unfortunately its 'Windows' only.

---

