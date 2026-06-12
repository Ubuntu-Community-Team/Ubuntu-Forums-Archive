---
title: "Ubuntu 14.04 LTS Final Beta Release &amp; Adobe Flash Player?"
date: 2014-04-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Christopher on 2014-04-09
I have both Firefox & Chromium web browsers installed, is there a way to get adobe flash player working on one of these 2 web browsers? Any help would be much appreciated. Thanks in advance.


[http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html]("http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html")  Does this work?

[http://www.enqlu.com/2014/02/how-to-install-adobe-flash-on-ubuntu-or.html]("http://www.enqlu.com/2014/02/how-to-install-adobe-flash-on-ubuntu-or.html")   Or this?

---

### Post by craig10x on 2014-04-10
Easiest way is to install Google Chrome from their website....that way, you will get the pepperflash plug in built right into the browser instead of having to add it on...
Only thing is if it's a recent 14.04 install, you may find the ubuntu software center is unable to install it (it's a current bug) so if you also install gdebi, then you can save the deb from the google site,
and then right click it and select gdebi and it will install smoothly and easily...

Chromium requires that manual install (if you can get it to work...perhaps someone else here can guide you on it) and you can't install it for Firefox...Firefox doesn't have a current flash plug in, uses the rather
outdated one that the ubuntu restricted extras installs (not ubuntu's fault....adobe no longer makes newer flash for linux other then their agreement to provide the latest versions to Chrome web browser through it's pepperflash plug in)...

---

### Post by Christopher on 2014-04-10
> **craig10x said:**
> Easiest way is to install Google Chrome from their website....that way, you will get the pepperflash plug in built right into the browser instead of having to add it on...
Only thing is if it's a recent 14.04 install, you may find the ubuntu software center is unable to install it (it's a current bug) so if you also install gdebi, then you can save the deb from the google site,
and then right click it and select gdebi and it will install smoothly and easily...

I installed Chromium from the "Ubuntu Software Center" darn lol.

---

### Post by monkeybrain20122 on 2014-04-10
Other than flash you need other media-codecs too. To get everything at once install ubuntu-restricted-extras from the package manager (Ubuntu Software Centre, synaptic or muon depending on your DE) or in the terminal
```
sudo apt-get install ubuntu-restricted-extras
```
This will install flash along with other codecs.

---

### Post by Christopher on 2014-04-10
> **monkeybrain20122 said:**
> Other than flash you need other media-codecs too. To get everything at once install ubuntu-restricted-extras from the package manager (Ubuntu Software Centre, synaptic or muon depending on your DE) or in the terminal
```
sudo apt-get install ubuntu-restricted-extras
```
This will install flash along with other codecs.

Will this install the "Pepper Flash Player" for Chromium?

---

### Post by cariboo on 2014-04-10
> **Christopher said:**
> Will this install the "Pepper Flash Player" for Chromium?

There is a pepperflashplugin-nonfree package in the repositories, I'm using it with zero problems on my Trusty Ubuntu Gnome install.

---

### Post by monkeybrain20122 on 2014-04-10
No. Pepperflash is separate. But IMO you may as well use Chrome if you want pepper flash.

Also a bit of extra info, some sites such as vimeo use html5 but you need h264 support and the package that provides it for Firefox is removed from 14.04 . Supposedly Firefox will support the replacement sometimes later but some geniuses in Ubuntu's team somehow think that it is a good idea to remove packages when the replacements are not in place so no html5 on Firefox for Ubuntu's next LTS for at least a couple of months. Fortunately there is a ppa to add the missing piece

```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

P.S. Firefox's flash (system flash) may be 'outdated', but works 99% of the time. I have not found any advantage of pepper flash really,--except maybe for a handful of websites that require it.

---

### Post by Christopher on 2014-04-10
Thank you everyone.

---

### Post by Christopher on 2014-04-10
> **monkeybrain20122 said:**
> Other than flash you need other media-codecs too. To get everything at once install ubuntu-restricted-extras from the package manager (Ubuntu Software Centre, synaptic or muon depending on your DE) or in the terminal
```
sudo apt-get install ubuntu-restricted-extras
```
This will install flash along with other codecs.

Ok this worked, so far so good! SWEET TY! :mrgreen:

---

### Post by mörgæs on 2014-04-10
Please mark the thread 'solved'.

---

### Post by craig10x on 2014-04-10
Only thing is i think i read that Chromium will shortly not support that old flash that ubuntu restricted extras installs...while it was still work on firefox, i think within the next few months, it's going to be removed from access on Chromium Browser, so that means you would still need to somehow get that pepperflash package in the ubuntu repos to work on your chromium...

A much simpler suggestion: switch to Google Chrome...pepperflash is already built in to it...also it has an nifty pdf reader built in and it also adds a ppa so you get new versions of Chrome through the software updater as soon as they are released...Lot of advantages there...anyway, that's what i would do (i love and use Chrome as my main browser) :D

---

