---
title: "Suspicious automatic downloading of unwanted suspicious file"
date: 2017-03-13
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2017-03-13
Hi all,
every time I visit this Croatian web page (local news)
[http://www.regionalexpress.hr/](http://www.regionalexpress.hr/)
I see an unwanted suspicious file downloaded inside Download directory: 

*File name: 6FHNuv_zl6I*
*Shockwave Flash datoteka (application/vnd.adobe.flash.movie)*
*5,5 kB (5522 bytes)*

Problem exist only with Google Chrome (Firefox everything ok).
What's happening?

---

### Post by jeremy31 on 2017-03-13
It is supposed to be a youtube video, chrome downloads it but firefox will actually display a youtube video with a link about the player being deprecated, the link is [https://developers.google.com/youtube/flash_api_reference](https://developers.google.com/youtube/flash_api_reference)

---

### Post by aljosa2 on 2017-03-13
Thank you very much for your reply jeremy31.
The question is: how can my browser dowload a file without tell me anything, without ask me anything and especially without my permission?

---

### Post by QIII on 2017-03-13
Hello!

Do hou have any script blockers running in your browser?  If not, a script could initiate a download without your consent.

---

### Post by &amp;KyT$0P# on 2017-03-13
I have seen similar on machines where I don't have Flash.  It happens to me when opening a web page that embeds a Flash object as a [FONT=Courier New]<iframe>[/FONT], instead of a [FONT=Courier New]<object>[/FONT] or [FONT=Courier New]<embed>[/FONT].

* And sure enough -
```
<iframe src="http://www.youtube.com/v/6FHNuv_zl6I" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="" style="" frameborder="0"></iframe>
```

---

### Post by aljosa2 on 2017-03-13
> **QIII said:**
> Hello!

Do hou have any script blockers running in your browser?  If not, a script could initiate a download without your consent.
Hi, I have no script blockers. The only active Chrome extension is "History Limiter Custom 1.1.1".

---

### Post by jeremy31 on 2017-03-13
I wonder if there is something in Chrome that trusts content from youtube as I have flash and autodownload disabled.  The first hit from a google search for the file name is a video on youtube and the second hit is this thread

---

### Post by &amp;KyT$0P# on 2017-03-13
Did you see my post above?  I should have said, that code is from the site linked in the OP.  And I too get the download attempt on that site.

jeremy31, I reckon you have Flash disabled in Chrome but enabled in Firefox.

---

### Post by aljosa2 on 2017-03-14
My Internet speed - unfortunately - is not so high. The reason why I prefer Chrome over Firefox is that during the past years Chrome is much faster than Firefox in all of my computers. **This experience completely and totally breaks the logic why cca. 5 years ago I switched from Windows to Linux.**

---

### Post by vasa1 on 2017-03-14
> **halogen2 said:**
> Did you see my post above?  I should have said, that code is from the site linked in the OP.  And I too get the download attempt on that site.

jeremy31, I reckon you have Flash disabled in Chrome but enabled in Firefox.

With Chrome incognito (no extensions), I get the unsolicited download.

I tried with Firefox 52 (private browsing): uBlock origin turned off. I don't have the conventional flash-plugin and haven't done anything to make Firefox see Chrome's Flash (which I understand is possible).

I get this window:

---

### Post by aljosa2 on 2017-03-17
Just received Chrome update - problem solved :)

---

