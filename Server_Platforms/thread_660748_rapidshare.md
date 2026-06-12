---
title: "rapidshare"
date: 2008-01-07
forum: Server Platforms
---

### Post by danharper on 2008-01-07
Is there a download manager I can use for rapidshare either with webmin or the command line?

Cheers Dan

---

### Post by (((X))) on 2008-01-07
not sure it will be useful to you..
w3m is command-line webbrowser, maybe it can  download files too,
[http://w3m.sourceforge.net/](http://w3m.sourceforge.net/) homepage
[http://abe.nwr.jp/w3m/w3m-js-en.html](http://abe.nwr.jp/w3m/w3m-js-en.html) for javascript.

---

### Post by ario on 2008-05-03
No!
D4x used to do just you want but it has bug now and project seems to be died for a log time:( flashget may runs under wine but all programs under wine sometimes run and sometimes not!
I don't know no other download manager for linux to do that.
I have a premium rapidshare account and it will finished few days and don't know how to use it:(

---

### Post by kurageart on 2008-05-05
rapget works perfectly under wine... try it, it works

---

### Post by coldstatue on 2008-05-31
As of yesterday, rapget no longer works. It will get the first file, and then return errors, even if you have direct downloads enabled in your rs account. When I figure out where the rapget log file goes, I'll post a copy. I've tried flashgot, orbit, and a few others since this started, and they all give me a bunch of 4k files (actual files should be about 95 MB.) 

Looks like new protection, which stinks. If anyone has tested a prog, even win, in the last 24 hours that works with a list of links (that don't have to be entered one at a time) and it can remember your uname and pass, PLEASE let us know!

---

### Post by coldstatue on 2008-05-31
BTW, could someone move this thread?

---

### Post by swmiller6 on 2008-06-03
wget for commandline...
Download Them All Firefox add-on works great if you enable direct download through our rapidshare premium account settings. You must also allow firefox to save the rapidshare login cookie for it to work correctly with a premium account. If you ever remove the cookie you will have to log back into rapidshare before you will be able to use DTA with your premium accout.
DTA uses the rapidshare cookie firefox saves to login to your rapidshare account.
swmiller6

---

### Post by coldstatue on 2008-06-03
I've tried wget, but I'm not smart enough to figure out downloading a bunch of links with that. Still reading, still getting 4.3 kb files.

The site I am using doesn't provide links - just text URls, so selecting them all and using the DTA context menu entry doesn't work - it down't recognize the text as addresses. 

I got the batch descriptor in DTA to work, (kind of) but it downloads the first file, while the others load 4.3 kb. Do I need a referrer URl? What do i use? I have the same issue no matter what method I use.

It is, however, renaming all my rars to .ra.html, so, it's just getting the page where you choose the dowload site or something. 

Thanks

There was definitely a change in RS. Working one day, not the next. Only 3 days into my membership.

---

### Post by coldstatue on 2008-06-03
Well, if I can't get this resolved soon, it will be my last month at rs, and I'll be sure to tell others on this board and elsewhere. 

I thought paying members were allowed to use dl managers.

I have followed all instructions that worked before the latest update. They are broken now.

---

### Post by djuniah on 2008-06-13
Easy solution to this one everyone.

This is actually cross platform and completely firefox based

First, install linkification.  This will turn all those text links into clickable (or DTA-able) links.
[https://addons.mozilla.org/en-US/firefox/addon/190](https://addons.mozilla.org/en-US/firefox/addon/190)

Then install DownThemAll
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

configure DTA to download links from rapidshare.com/*
then just right go to that page with RS links, after it finishes loading, linkification will work its magic, and you can right click on the page and "DTA one click"


NOTES:
I would suggest turning OFF the chunks (set them to 1) in the DTA menu.  RS counts each chunk as a full file and this will eat up your cap (i believe its up to 50GB in 5 days now)  
so lets say you are getting a 100MB file at 10 chunks.  To rapidshare that counts as 1GB worth of data.

also, theres some sort of I/O issue with firefox that forces it to use almost 100% of the CPU when you have more than one file DLing in DTA. This seems like a linux only issue and i have yet to find a fix for it.  It has to do with how firefox(not DTA) handles disk IO and wait times.

---

### Post by coldstatue on 2008-06-13
You rock, djuniah. I no longer need to boot into windows to download from rs (with the RS Manager.) Thank you. I'm not sure why I have to put the green check next to each file in the DTA manager before downloading, but that is a very minor issue.

I salute you

---

### Post by swmiller6 on 2008-07-03
DTA works with the flashgot plugin also, you do not need to check each file you can just flashgot selection and it will adda and start the files downloading in DTA. Just make sure you configure flashgot to use DTA as the download manager in the flashgot preferences section, also flashgot can be set to use wget as well.

---

### Post by Levander on 2008-07-06
> **djuniah said:**
> Easy solution to this one everyone.

This is actually cross platform and completely firefox based

First, install linkification.  This will turn all those text links into clickable (or DTA-able) links.
[https://addons.mozilla.org/en-US/firefox/addon/190](https://addons.mozilla.org/en-US/firefox/addon/190)

Then install DownThemAll
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

configure DTA to download links from rapidshare.com/*
then just right go to that page with RS links, after it finishes loading, linkification will work its magic, and you can right click on the page and "DTA one click"

How do I "configure DTA to download links from rapidshare.com/*"?  I just installed DTA and restarted firefox.  I see how to make some kind filter based on the filename extension.  But, I don't see how to do it based on the URL host name you are downloading from.

---

### Post by jonian_g on 2008-07-06
The best solution is to go and get jDownloader.

"JDownloader is open source, platform independent and written completely in Java. It simplifies downloading files from One-Click-Hosters like Rapidshare.com or Megaupload.com - not only for users with a premium account but also for users who don't pay. It offers downloading in multiple paralell streams, captcha recognition, automatical file extraction and much more. Of course, JDownloader is absolutely free of charge. Additionally, many "link encryption" sites are supported - so you just paste the "encrypted" links and JD does the rest. JDownloader can import CCF, RSDF and the new DLC files."

Works perfecly.

---

### Post by petrovicivan on 2008-07-07
you can use wget from Terminal. Just type
```
wget --user=your_rapidshare_user --password=your_rapidshare_password http://rapidshare.com/link1 http://rapidshare.com/link2...
```

or you can collect many URLs for download and put then all in the file and add option ```
-i inputfile.txt
```

next, you can do the download in the background, and then close Terminal, with option ```
-b
```

when you merge this three ways you will get my favorite way of RS download, which is like this

```
wget --user=my_user --password=my_pass -i input.txt -b
```

---

### Post by coolworm on 2008-07-14
[http://ubuntudoitall.blogspot.com/](http://ubuntudoitall.blogspot.com/)

D4x best download manager - with rapidshare fix!

---

### Post by Jimmy9pints on 2008-07-20
> **djuniah said:**
> Easy solution to this one everyone.

This is actually cross platform and completely firefox based

First, install linkification.  This will turn all those text links into clickable (or DTA-able) links.
[https://addons.mozilla.org/en-US/firefox/addon/190](https://addons.mozilla.org/en-US/firefox/addon/190)

Then install DownThemAll
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

configure DTA to download links from rapidshare.com/*
then just right go to that page with RS links, after it finishes loading, linkification will work its magic, and you can right click on the page and "DTA one click"


NOTES:
I would suggest turning OFF the chunks (set them to 1) in the DTA menu.  RS counts each chunk as a full file and this will eat up your cap (i believe its up to 50GB in 5 days now)  
so lets say you are getting a 100MB file at 10 chunks.  To rapidshare that counts as 1GB worth of data.

also, theres some sort of I/O issue with firefox that forces it to use almost 100% of the CPU when you have more than one file DLing in DTA. This seems like a linux only issue and i have yet to find a fix for it.  It has to do with how firefox(not DTA) handles disk IO and wait times.

This seemed to work VERY well at first (I was really pleased) but then after the first few downloads the rest came as html files! Very annoying. 

Has anyone any idea what I have done wrong?

J

---

