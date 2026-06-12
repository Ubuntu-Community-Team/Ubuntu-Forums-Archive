---
title: "pandora and chromium"
date: 2016-02-27
forum: The Cafe
---

### Post by rosswmcgee on 2016-02-27
Pandora kept giving me a message saying I need to upgrade Adobe flash and would not open. I am using ubuntu 12.04.4 lts. I tried a few thing all failed. So I downloaded Chrome and installed it. Now Pandora works fine. I like Chrome better than Chromium. I use Chrome on my smartphone too. Pandora worked fine in Firefox and these are the two browsers I generally use. If I get a website that tells me to discontinue using adblock then I use midori which they seem not to have caught up with yet.

---

### Post by grahammechanical on 2016-02-27
I do not know what Pandora is. But I think that Adobe stopped updating its Linux version of Flash some years ago and Google has somehow obtained permission to integrate Flash into Chrome and also to take responsibility for keeping the Linux version up to date.

There is a procedure to obtain the Chrome version of Flash by using the Ubuntu Software Centre. We down load a Flash plugin installer. The installer downloads Chrome and extracts the Flash components and then uninstalls Chrome leaving the Flash components behind for Firefox or Chromium to use.

It seems that Pandora is taking advantage of Chrome's integration of Flash.

Regards.

---

### Post by Frogs Hair on 2016-02-27
Pepperflash-nonfree is the package graham is referring to. I have tried it in Opera which is Chromium based and it doesn't work. The Pithos Pandora client from the software center works fine with no additional flash player . If you interact on the social end of Pandora you may have to install Chrome if Pepper doesn't work.

---

### Post by rosswmcgee on 2016-02-27
Correction I am using ubuntu 14.04.4.

Chrome works with  Pandora.  Chromium quit working with Pandora.

---

### Post by vasa1 on 2016-02-27
> **grahammechanical said:**
> I do not know what Pandora is. ...
[https://en.wikipedia.org/wiki/Pandora_Radio](https://en.wikipedia.org/wiki/Pandora_Radio) is what OP refers to, I'm guessing.

And:```
07:38 AM ~ $ apt-cache search pandora
libpiano-dev - library to interface with Pandora radio -- development
libpiano0 - library to interface with Pandora radio -- runtime files
pandora - GIMP Plugin For Creating Panoramas
pandora-build - autotools made better, faster stronger
pandorafms-agent - Pandora FMS - The Flexible Monitoring System (agent)
pianobar - console based player for Pandora radio
pithos - Pandora Radio client for the GNOME desktop
unity-webapps-pandora - Unity Webapp for pandora
unity-webapps-pandora-com - Unity Webapp for pandora-com
07:39 AM ~ $ 
```

---

### Post by ajgreeny on 2016-02-27
If you install the two packages adobe-flashplugin, and also freshplayerplugin from the webupd8 repository (I will have to let you search for that as I have not figured out how to copy a URL using android which is what I am.using at the moment) you will see that you get the most recent version of flash, 20.0.0.296 or similar in chromium.and firefox.

If you any other flash packages installed remove them as they only confuse the system and mean you may still be using older versions of flash in one or other, or both browsers.

---

### Post by rosswmcgee on 2016-02-28
I like Chrome better now that I have i and zero problems.

---

### Post by Dragonbite on 2016-02-29
Pandora in the browser is a resource hog.

Install [Pithos]("http://pithos.github.io/"), an application that plays Pandora and, unlike the web version, shows you the next 3 songs that are going to be played! 

Installation is as easy as ```
sudo add-apt-repository ppa:pithos/ppa
sudo apt-get update
sudo apt-get install pithos
```

I install that on all of my Linuxes... I wish it was available for Windows even!

---

### Post by yoshii on 2016-02-29
I still use FireFox.  I was able to use some kind of linux flash substitute (i forget what it was called).  There's a way to get a file and put it into a specific directory.  Apparently it gets installed into the wrong directory and some people say to create a symbolic link to the file.  I didn't know how to create a symbolic link so instead I just copied the file into the place where FireFox needs it and now FireFox plays flash OK for me.  Sorry that this is so vague.  I don't remember the details.  But I don't like Chrome so I wasn't going to install Chrome and it turns out you don't have to.  All you need is that particular flash file in one or two places (or symbolically linked, if you know how to do that).  

As for Pandora, Pithos is great!!!!!! it's in the Software Center.

---

### Post by user1397 on 2016-03-01
I just use spotify, like it much better than pandora.  Mostly use it on my android phone, but sometimes use it through a browser, in which case it also needs flash (which sucks), but it works fine on Chrome.  Not sure about other browsers.

---

### Post by Dragonbite on 2016-03-01
In Ubuntu, I haven't had any issues with running Flash.  In other distributions it is not so, but Ubuntu has been as easy to use as the proprietary systems when it comes to flash and codecs.

---

### Post by rosswmcgee on 2016-03-04
Added pithos via synaptic , fixed problem went back to chromium and removed chrome, pleas and thank you.

---

### Post by Frogs Hair on 2016-03-05
I have Pandora working with Opera using the adobe-flashplugin from the 15.10 repository. This is not the flashplugin-intaller. I’ve been a regular Pithos user, but it's nice to have the site working in Opera.  

> Adobe® Flash® Player is a cross-platform, browser-based application runtime
that provides uncompromised viewing of expressive applications, content, and
videos across browsers and operating systems.

This package provides plugins compatible with both Chromium and Mozilla based
web browsers

---

