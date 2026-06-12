---
title: "adobe flash player  fail/ 14.04/15.04"
date: 2015-02-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-02-04
All of a sudden adobe flash player will fail. Someone directed me to a site with a video. It said I needed to isntall adobe flash player.  (already installed) There was a notification at the adobe site that it will not support Linux OSes past the current version of 11.2  I uninstalled / reinstalled/completely removed .. etc .. and it still will not play these videos.

Try to play a news story from:

[www.ctv.ca](www.ctv.ca)

---

### Post by QIII on 2015-02-04
Interesting.  I'm getting the fail there in both 14.04 and 15.04 as well.

---

### Post by VinDSL on 2015-02-04
Only error I get is 'can't view in my geo region' or whatevs -- no flash player failure notifications...

---

### Post by VinDSL on 2015-02-04
Er...

I just started thinking -- I don't even think I have flash installed :D

```

Chromium	40.0.2214.93 (Built on Ubuntu 14.10, running on Ubuntu 15.04)
OS	        Linux
Flash plugin	15.0.0.189 /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so
```

I'm running Pepperflash.

---

### Post by grahammechanical on 2015-02-04
I have had flash player crash. That is with certain newspaper web sites that have lots of flashy advertising and lots of elements on the page. Chromium did not crash even though there is a message asking if I wanted to relaunch or leave closed. I do also have pepper flash installed.

I got Adobe flash player when I installed restricted extras. I installed restricted extras to get the audio and video codecs. I was testing Unity8 session and downloading mp3 audio files and mp4 video files and they were not playing. So, I needed restricted extras.

There was an old lady who swallowed a fly. :) 

Regards.

---

### Post by zika on 2015-02-04
> **grahammechanical said:**
> There was an old lady who swallowed a fly. :) She's dead, of course... ;)

---

### Post by slickymaster on 2015-02-04
Getting the same with today's Vivid image.

```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
3.18.0-12-generic

~$ apt-cache policy firefox
firefox:
  Installed: 34.0+build2-0ubuntu2
  Candidate: 34.0+build2-0ubuntu2
  Version table:
 *** 34.0+build2-0ubuntu2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ vivid/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by zika on 2015-02-04
Did You see this: [http://malwaretips.com/blogs/warning-your-flash-player-may-be-out-of-date-virus/](http://malwaretips.com/blogs/warning-your-flash-player-may-be-out-of-date-virus/)
these days?
I'm not (to be precise, very rarely) using AF so...

---

### Post by buzzingrobot on 2015-02-04
The  CTV site doesn't break here, but it does tell me I need to upgrade Flash.

As we know, the Flash version Adobe maintains for Linux has only seen security patches for some time, so it's possible, maybe likely, that Flash-for-Windows has seen new features that are incompatible with the Linux version.  I don't pay enough attention to it to know if that's the case.

We know, though, that the version numbers are different.  So, this might be just a case of the CTV site builder hard coding a check for Flash version the site was coded to support.

[There's at least one CTV clip that appears identical -- same open still shot -- to a clip at BBC News, and that plays fine here.]

---

### Post by ventrical on 2015-02-04
Thanks all.

btw I'm using firefox.

---

### Post by ventrical on 2015-02-04
> **zika said:**
> Did You see this: [http://malwaretips.com/blogs/warning-your-flash-player-may-be-out-of-date-virus/](http://malwaretips.com/blogs/warning-your-flash-player-may-be-out-of-date-virus/)
these days?
I'm not (to be precise, very rarely) using AF so...

I am getting the below .. so I am not sure..

---

### Post by SeijiSensei on 2015-02-04
There have been two updated releases for Flash in the past couple of weeks.  Installing the latest eliminated all "player is outdated" messages on the sites I've visited. Run "sudo apt-get install adobe-flashplugin".

---

### Post by buzzingrobot on 2015-02-04
> **ventrical said:**
> I am getting the below .. so I am not sure..

That's what I see at the CTV site on Firefox.

440 is the latest version and it's in the repos, so any correctly updated system should have it.

---

### Post by buzzingrobot on 2015-02-04
OK, the CTV clips play here with Opera using pepper Flash.

---

### Post by VinDSL on 2015-02-04
> **ventrical said:**
> I am getting the below .. so I am not sure..

Oh, cool, screenie time... :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-4-feb-2015-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-feb-2015-1.png")[/INDENT]


I'm pretty sure it's working here.

---

