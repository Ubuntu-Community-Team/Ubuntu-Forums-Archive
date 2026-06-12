---
title: "Apt Proxy Support?"
date: 2015-05-04
forum: Ubuntuzilla
---

### Post by ejbiow on 2015-05-04
I have a very slow internet connection and a bandwidth cap and several Debian & Ubuntu installations so I have my machines set up to use an apt proxy, currently [approx]("http://en.wikipedia.org/wiki/Approx"), so I only have to download a new package once, and then it is available to all my machines from my local LAN server.  Unfortunately, for some reason this doesn't work with the standard ubuntuzilla repository, [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt)

Approx or apt-cacher(-ng) just aren't able to parse it, I believe because of some ['302 redirect' issue]("http://ubuntuforums.org/showthread.php?t=1417362").  But I read that there was an alternative repository that works with apt proxies, to wit: [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/)

So I set up approx to point to that repository & that worked for years, but it seems like that server has been down for the last week or three, and so now I will have to download the mozilla-build packages directly on each machine or manually fetch them to my server and install them with "dpkg -i", both a PITA.  

Is "switch.dl.sourcefore.net" a thing of the past or just experiencing a hickup?  Is there any prospect of getting the main repository to play nice with apt proxies?  (I tried recently, it still doesn't)  

FWIW: The configuration of my approx proxy:
```
#ubzilla               http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt # doesn't work
ubzilla        http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/

```

Thank you for what you do...

---

### Post by nanotube on 2015-05-04
Hi,

It appears that maybe sourceforge has discontinued the switch mirror. Here are a few more mirrors you can try:

jaist.dl.sourceforge.net
softlayer-ams.dl.sourceforge.net
ufpr.dl.sourceforge.net
hivelocity.dl.sourceforge.net
softlayer-dal.dl.sourceforge.net

In general, if you want to discover the mirror urls that sourceforge uses, you can try going to download any file, and click on "try another mirror" and select one you like. once it offers you the download, observe the url. E.g. try the link below for ubuntuzilla instructions. That's how I produced the list above :)
[https://sourceforge.net/projects/ubuntuzilla/files/latest/download?source=files](https://sourceforge.net/projects/ubuntuzilla/files/latest/download?source=files)

Give these a try, hope they work - let me know how it goes! 

Best,
nanotube

---

### Post by ejbiow on 2015-05-05
Thanks a ton, nanotube, the first one works great, I have the others in my config file commented out if jaist.dl goes away and a link to this thread.  

I use ubuntuzilla to give me seamonkey and to get me firefox and thunderbird on Debian (I realize that iceweasel and icedove are pretty much the same thing, but I don't care for their pale, washed out icons in my taskbar and unless I set up the mozilla.debian.net backport repository the versions of FF get dated awfully quickly on Debian stable.) 

I kicked you a (modest) lunch via your [email]ubuntuzilla@gmail.com[/email] account on PayPal, enjoy.

---

### Post by nanotube on 2015-05-05
Glad to help, and thank you for your support! :)

---

