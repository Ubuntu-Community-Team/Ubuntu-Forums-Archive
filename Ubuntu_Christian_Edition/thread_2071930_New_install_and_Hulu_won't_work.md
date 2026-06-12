---
title: "New install and Hulu won't work"
date: 2012-10-16
forum: Ubuntu Christian Edition
---

### Post by bigv316 on 2012-10-16
Hi everyone, I am setting up Ubuntu CE as a media center for my home entertainment system and since I have young children I wanted something safe. So far it seems to work well except for Hulu and Hulu desktop. I did a fresh install of Ubuntu CE and those are the only things that don't work. Any ideas?

---

### Post by stlsaint on 2012-10-17
> **bigv316 said:**
> Hi everyone, I am setting up Ubuntu CE as a media center for my home entertainment system and since I have young children I wanted something safe. So far it seems to work well except for Hulu and Hulu desktop. I did a fresh install of Ubuntu CE and those are the only things that don't work. Any ideas?

hello bigv316,

Thank you for the post. I need some more info from you in regards to "how" hulu is not working. What function's are not working with the desktop application and are you using the hulu website also and it is not working?

---

### Post by Limestone Cowboy on 2012-10-31
I will weigh-in here since its been a couple of weeks without a reply from the previous poster.  

I too have v12.1 newly installed and cannot view hulu videos.  I cannot view cnn dot com videos either, but I can play you tube vid's and MPEG4's.

I suspect the prev. poster meant that nothing happens when you click a video link.  The video page begins to load, but that's as far as it gets.  No video, no errors, no nothing.

I have adequate processing power and a AGP v3800 video card.  I understand that Ubunto locates and loads drivers for you, so that shouldn't be a problem (right?)  I've looked into Flash issues without success (lots of discussion and work-arounds that are no longer available from user linux lover).

sorry to ramble, but I'm at the end of my wits here with this issue.

I have a laptop with v11.4 loaded and videos (all videos) play just fine.  I've tried to load v11.4 onto this system, but I can't get it to boot from a memory stick and NONE of the bootable disc(s) I've burned will boot in this machine either.  

I've tried LOTS of scripts from this forum, but none seem to solve the video problem.  

Unbelievable frustration.

Any help

P.S.  I don't just scrap the whole thing and use the laptop because it is under processed and slow as a crab - also causing grave aggravation

---

### Post by xinawesome on 2013-03-18
Hi, everyone. I'm having trouble with hulu and quakelive.com also. Both websites don't load. I'm running Ubuntu CE parallel with windows 7 in which both sites works fine. I checked the errors when loading the page:
For hulu:

```
Uncaught SyntaxError: Unexpected identifier [application-8ba7e7deaa90296ca3b707f21a5e086a.js:4842]("http://static.huluim.com/huluguru/i18n/en-us/application-8ba7e7deaa90296ca3b707f21a5e086a.js")
Failed to load resource: the server responded with a status of 403 (Request blocked by Privoxy) [http://www.google-analytics.com/ga.js](http://www.google-analytics.com/ga.js)
Uncaught TypeError: Cannot call method 'getInstance' of undefined [application_framework-7cb3494d27d3d5ce33e8305700abfc2e.js:300]("http://static.huluim.com/huluguru/application_framework-7cb3494d27d3d5ce33e8305700abfc2e.js")
XMLHttpRequest cannot load [http://t2.hulu.com/v3/sitetracking/error?datatype=jsloaderror&computerguid=96603B59B50B4891E421D9E503A15BC8&isbingcrawler=false&os=Linux+X11%3B+Linux+x86_64&client=Chrome+21&frameworkloaded=true&applicationloaded=false&templatesloaded=false&playerloaded=true](http://t2.hulu.com/v3/sitetracking/error?datatype=jsloaderror&computerguid=96603B59B50B4891E421D9E503A15BC8&isbingcrawler=false&os=Linux+X11%3B+Linux+x86_64&client=Chrome+21&frameworkloaded=true&applicationloaded=false&templatesloaded=false&playerloaded=true). Origin [http://www.hulu.com]("http://www.hulu.com/") is not allowed by Access-Control-Allow-Origin.

```
For quakelive:
```

Uncaught SyntaxError: Unexpected token + [compiled_v2013022600.0.js:709]("http://cdn.quakelive.com/web/2013022600/compiled_v2013022600.0.js")

Uncaught ReferenceError: jQuery is not defined [script_v2013022600.0.js:17]("http://cdn.quakelive.com/web/2013022600/css/valances/20130122-premium-content/script_v2013022600.0.js")


Uncaught ReferenceError: $ is not defined [http://www.quakelive.com/:145]("http://www.quakelive.com/")


GET [http://www.google-analytics.com/ga.js](http://www.google-analytics.com/ga.js) 403 (Request blocked by Privoxy) [http://www.quakelive.com/:32]("http://www.quakelive.com/")


GET [http://edge.quantserve.com/quant.js](http://edge.quantserve.com/quant.js) 403 (Request blocked by Privoxy) [http://www.quakelive.com/:176]("http://www.quakelive.com/")


GET [http://bin.clearspring.com/at/v/1/button1.6.swf](http://bin.clearspring.com/at/v/1/button1.6.swf) 404 (No such domain) [addthis_widget_v2013022600.0.js:2]("http://cdn.quakelive.com/web/2013022600/js/addthis_widget_v2013022600.0.js")


```

anyone  knows how to fix this? Thank you so much everybody. I also tried reinstalled Ubuntu and that didn't work. I suspect the Dansguardian is blocking it, but I have no idea how to fix it.

---

### Post by stlsaint on 2013-03-19
Have you tried adding hulu and quake sites to your whitelist? This should not be necessary as i am able to reach both sites out the box but we can try. Have you changed anything with DG or privoxy before noticing the issues?

---

### Post by xinawesome on 2013-03-30
> **stlsaint said:**
> Have you tried adding hulu and quake sites to your whitelist? This should not be necessary as i am able to reach both sites out the box but we can try. Have you changed anything with DG or privoxy before noticing the issues?

I reinstalled Ubuntu CE still has the same problem. Also Dansguardian doesn't seem to block google image unsafe searches.

---

### Post by davidkennedy85 on 2013-04-02
xinawesome, if you want to filter Google Image Search or force safe mode, then you have to make Google Search use http as opposed to https: [http://ubuntuforums.org/showthread.php?t=2131780](http://ubuntuforums.org/showthread.php?t=2131780)

Alternatively, you could block Google altogether.

---

### Post by xinawesome on 2013-04-12
Hi, installed the Ubuntu again and Hulu works fine until I updated some files. The game still doesn't work though. I've have no problem with other linux distros like Mint. But I really like ubuntu. I hope there is a solution to this,

---

