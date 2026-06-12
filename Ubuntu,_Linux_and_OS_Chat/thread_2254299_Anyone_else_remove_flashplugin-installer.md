---
title: "Anyone else remove flashplugin-installer?"
date: 2014-11-26
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-11-26
My video viewing is quite limited, nearly all YouTube. I've removed flashplugin-installer. For the few videos that don't play, I use mpv (from the software center) or Google Chrome.

---

### Post by pqwoerituytrueiwoq on 2014-11-26
me, but i installed adobeflash-plugin
```
~$ apt-cache policy adobe-flashplugin flashplugin-installer pepperflashplugin-nonfree 
adobe-flashplugin:
  Installed: 11.2.202.418-0trusty1
  Candidate: 11.2.202.418-0trusty1
  Version table:
 *** 11.2.202.418-0trusty1 0
        500 http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages
        100 /var/lib/dpkg/status
flashplugin-installer:
  Installed: (none)
  Candidate: 11.2.202.418ubuntu0.14.04.1
  Version table:
     11.2.202.418ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
        500 http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ trusty/main amd64 Packages
     11.2.202.350ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
pepperflashplugin-nonfree:
  Installed: 1.3ubuntu1
  Candidate: 1.3ubuntu1
  Version table:
 *** 1.3ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
        100 /var/lib/dpkg/status
```
i just pause all DRM-free flash based video and run it in smplayer
i have YouTube set for html5 as the preferred player cause there flash one uses some drm so i can't find the video and run it via smplayer like every other site i use
and my firefox developer edition has much better ghtml5 video acceleration

---

### Post by Tar_Ni on 2014-11-26
Since I use Firefox as my one and only browser, I keep the 11.2 Flash plugin activated. I do a little more than watch Youtube video as far as video streaming goes and some websites requires it. I wish HTML5 was standard across the web so that I could get rid of it though..

But the most popular video hosting websites like Youtube, Dailymotion and Vimeo all have HTML5 players so if these are the only websites with media contents that you visit, then you are fine.

I might soon try the Fresh Player plugin (a wrapper for the pepperflash plugin) when it's fully tested and proved because more and more sites are saying that my Flash 11.2 is not good enough and need upgrading..

Some developpers are also working full-time on Shumway, an open-source HTML5 plugin which will allow Firefox's user to play pretty much all of the media content online and cut the tie with proprietary Adobe once and for all..

---

### Post by coldcritter64 on 2014-11-26
I removed the Debian equivalent here (flashplugin-nonfree) as I never could get it to work properly in Firefox Nightly.

Instead I use the pepperflashplugin-nonfree package and chromium (no google-chrome is installed).
Then in firefox I use the extension "Open in Chrome" and set it up to access Chromium in the settings.
With firefox as my main use browser, 1 click (left click for single tab, middle click for all tabs) of the chrome icon on the firefox toolbar and the relevant tab/s are opened in Chromium for viewing any flash vids.

Edit: seems by doing that the flash version being reported here is [COLOR=#000000][FONT=Bitstream Vera Sans]"Version:[/FONT][/COLOR][COLOR=#000000][FONT=Bitstream Vera Sans]15.0.0.223" in [noparse]about:plugins.[/noparse][/FONT][/COLOR]

---

### Post by help_me2 on 2014-11-27
I use Chrome, therefore I don't have to worry about flash. Google takes care of it for me with updates. The days of trying to get flash to work good in linux are over for me. It just works now, and good.

---

### Post by philinux on 2014-11-27
Move to Ubuntu, Linux and OS Chat

---

