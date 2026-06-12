---
title: "Final Flash (Adobe) plugin is here..."
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-03-28
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
**11.2.202.228**

---

### Post by pqwoerituytrueiwoq on 2012-03-28
Nvidia users will experience a color issues (a red and blue inversion) on youtube with flash 11.2
see bug [3109467]("https://bugbase.adobe.com/index.cfm?event=bug&id=3109467")

---

### Post by ajgreeny on 2012-03-28
I realise this is a ubuntu +1 thread, but I can not get this version of flash to work at all on my 10.04 system with an ATI 9200SE video card.  I have tried flash-aid using both the beta version and the repository version, but neither do anything at all, and the beta version seems to be no longer available through flash-aid (is it the same as the repos version?).  Luckily I have a backup of the libflashplayer.so file that I know does work (11.1r102) so was able to restore that.

See [http://ubuntuforums.org/showthread.php?p=11800683#post11800683](http://ubuntuforums.org/showthread.php?p=11800683#post11800683)

What's going on; anybody know?

---

### Post by Harry33 on 2012-03-28
> **pqwoerituytrueiwoq said:**
> Nvidia users will experience a color issues (a red and blue inversion) on youtube with flash 11.2
see bug [3109467]("https://bugbase.adobe.com/index.cfm?event=bug&id=3109467")

I have NVidia 285GTX with nvidia proprietary drivers 295.33.
However, I cannot reproduce that bug with the new 11.2.202.228 Adobe Flash Plugin.

---

### Post by zuti on 2012-03-28
> **Harry33 said:**
> I have NVidia 285GTX with nvidia proprietary drivers 295.33.
However, I cannot reproduce that bug with the new 11.2.202.228 Adobe Flash Plugin.

295.33 and GTX 560, and the bug is definitely there. Even better is the fact that the built-in flash plugin in chrome dev still runs at 2x speed. No youtube for me then (except with all hardware acceleration disabled) :(

---

### Post by VinDSL on 2012-03-28
Thanks, zika!

Working great on my install:
[LIST]
[*]Linux 3.3 / Ubu 12.04 b1
[*]GeForce 7600 GT AGP
[*]nVidia 295.33 drivers
[/LIST]

Speaking of which, I just posted some pics of my vid card on AnandTech:

[INDENT][http://forums.anandtech.com/showthread.php?t=2235595](http://forums.anandtech.com/showthread.php?t=2235595)[/INDENT]

... if you want to see the inside of my Ubu Box.  :D

---

### Post by Sworddragon on 2012-03-28
On my system this version uses Stage Video by default. It decreases the cpu usage of my system from ~130% to ~13% if the video supports it. This sounds good but this feature is running very unstable. For example I'm seeing the video through the letters of the context menu and even some applications like htop. The most videos are even freezing for a few seconds and I got already ~10 crashes in 5 minutes. Interestingly setting EnableLinuxHWVideoDecode=0 in /etc/adobe/mms.cfg does not disable it. It seems I have to uninstall libvdpau1 to disable this. I'm using a GeForce 8600 GT with nvidia-current 295.20-0ubuntu1. Has somebody else this problem too?

Edit: It seems it is now deactivated somehow but I will test it after sleeping again. But I can confirm this color problem.

---

### Post by Nick Payne on 2012-03-28
> **Harry33 said:**
> I have NVidia 285GTX with nvidia proprietary drivers 295.33.
However, I cannot reproduce that bug with the new 11.2.202.228 Adobe Flash Plugin.

Neither can I (GTS250 with 295.33 driver and Flash 11.2.202).

---

### Post by xyzzyman on 2012-03-29
Happens here with 9600M GS 512MB and 295.33. Just wound up rolling back to 11.1.

---

### Post by VMC on 2012-03-29
I don't have that issue. Using nvidia 295.20 and flash 11.2

The odd thing is I'm using chrome 17.0.963.83, and I can't get the apparently already installed flash to work, so I install 11.2 to the Mozilla folder. It works perfectly that way.

---

### Post by the ruler on 2012-03-29
I installed this plugin in Ubuntu 12.04 64bit but Flash crashes sometimes when I hit Esc in fullscreen mode in Firefox. How do I solve this?

---

### Post by paul_in_london on 2012-03-29
> **zika said:**
> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
**11.2.202.228**

Thanks for the heads-up zika. I've been slow off the mark with this one. I checked the adobe labs page earlier this morning funnily enough, so the fact that 11.2 has now been released would explain why I didn't see anything new about flash there! :lolflag: 

Will try it out later.

---

### Post by Sworddragon on 2012-03-29
I have tested this again and Stage Video is not enabled by default (at least not fully) but it has on an disabled state some bad behaviours which it only had in earlier versions with Stage Video enabled.

This means with EnableLinuxHWVideoDecode=0 I'm getting the bugs as it would be enabled but without the performance advantages. Enabling it gives me the performance advantages and solves the color problem. But there are still some other problems to solve.

---

### Post by Johnny3 on 2012-03-29
> **VinDSL said:**
> Thanks, zika!

Working great on my install:
[LIST]
[*]Linux 3.3 / Ubu 12.04 b1
[*]GeForce 7600 GT AGP
[*]nVidia 295.33 drivers
[/LIST]

Speaking of which, I just posted some pics of my vid card on AnandTech:

[INDENT][http://forums.anandtech.com/showthread.php?t=2235595](http://forums.anandtech.com/showthread.php?t=2235595)[/INDENT]

... if you want to see the inside of my Ubu Box.  :D

Nice PC. This old man is a fan nut. Just spent $60.00 on 4 120 fans.
Thanks and God Bless Johnny3 65+++

---

### Post by Derek Karpinski on 2012-03-30
Is there a repository of older versions of 64 bit flash?  Or has someone saved the older versions somewhere?
 
I have vdpau installed and am running an nVidia G210.  The newest version of flash (and the last few for that matter) don't work with HW acceleration.  This new version turns people into smurfs.
 
I was almost certain there was a beta version of flash that worked well with vdpau and HW acceleration turned on.  I should've saved it, but......
 
Any help?

---

### Post by zika on 2012-03-30
> **Derek Karpinski said:**
> Is there a repository of older versions of 64 bit flash?  Or has someone saved the older versions somewhere?
 
I have vdpau installed and am running an nVidia G210.  The newest version of flash (and the last few for that matter) don't work with HW acceleration.  This new version turns people into smurfs.
 
I was almost certain there was a beta version of flash that worked well with vdpau and HW acceleration turned on.  I should've saved it, but......
 
Any help?I do have them (I think) all... ;)
Look (also) here: [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

---

### Post by xyzzyman on 2012-03-30
64bit [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260791](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260791)

32bit [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260792](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260792)

I used synaptic to lock it to that version for now. Strangely enough on my fresh install of 12.04 I don't have to rollback. Just on my old 12.04 install and my daily 11.10 (My new 12.04 install is now my daily though. Close enough for me. lol)

---

### Post by pqwoerituytrueiwoq on 2012-03-30
> **Harry33 said:**
> I have NVidia 285GTX with nvidia proprietary drivers 295.33.
However, I cannot reproduce that bug with the new 11.2.202.228 Adobe Flash Plugin.
are you using flash or html5?
right click and go to setting if hardware acceleration is enabled (defailt) the colors are inverted unless you enable hardware decode in [FONT=Courier New]/etc/adobe/mmc.cfg[/FONT] in which case flash is insanely unstable on a nvidia chip

---

### Post by pt123 on 2012-03-31
> **zuti said:**
> 295.33 and GTX 560, and the bug is definitely there. :(

GT210 & 295 and I am experiencing the problems

---

### Post by pt123 on 2012-03-31
> **xyzzyman said:**
> 64bit [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260791](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260791)

32bit [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260792](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260792)



When I tried to install this it caused problems, saying it was conflicting with the Firefox package, software centre keeps on trying to repair.

---

### Post by pqwoerituytrueiwoq on 2012-03-31
> **pt123 said:**
> When I tried to install this it caused problems, saying it was conflicting with the Firefox package, software centre keeps on trying to repair.
try purging flash
sudo apt-get purge adobe-flashplugin

old copies of flash should be available via linux mint's repositories in the mint-flash plugin package it does not update like the adobe-flashplugin packages does

---

### Post by dcstar on 2012-04-01
> **zika said:**
> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
**11.2.202.228**

This version of Flash is evil, I just had to manually roll back:

[http://ubuntuforums.org/showthread.php?t=1950501](http://ubuntuforums.org/showthread.php?t=1950501)

---

### Post by pt123 on 2012-04-04
> **pqwoerituytrueiwoq said:**
> try purging flash
sudo apt-get purge adobe-flashplugin

I tried that I am still getting this message
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 firefox : Breaks: adobe-flashplugin (<= 11.1.102.63-0precise1) but 11.1.102.55-0lucid1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

After googling found a presice version of the deb
here,
[https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0precise1](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0precise1)
 it installed fine and Flash is not showing blue tint

---

### Post by zika on 2012-04-05
> **pt123 said:**
> I tried that I am still getting this message
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 firefox : Breaks: adobe-flashplugin (<= 11.1.102.63-0precise1) but 11.1.102.55-0[COLOR=Red]lucid1[/COLOR] is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

After googling found a presice version of the deb
here,
[https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0precise1](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0precise1)
 it installed fine and Flash is not showing blue tintlucid1?
Update: Just noticed second part of Your message... ;)

---

### Post by Harry33 on 2012-04-05
> **zika said:**
> lucid1?
Update: Just noticed second part of Your message... ;)

There could be something wrong with the sources.list (not all Precise repos) if the system finds a lucid version.

---

### Post by JMB74 on 2012-04-05
11.2 keeps crashing for me.

Rolled back to v11.1.102.63 and all my problems are fixed, so not going to try with 11.2 again until they release a bugfix version.

---

### Post by lovinglinux on 2012-04-05
> **JMB74 said:**
> 11.2 keeps crashing for me.

Rolled back to v11.1.102.63 and all my problems are fixed, so not going to try with 11.2 again until they release a bugfix version.

Unless the problem can be fixed on the nVidia side, I doubt it will be fixed, since Adobe stopped supporting Flash on Linux.

---

### Post by JMB74 on 2012-04-05
I thought they were still going to release bugfix versions of the 11.2 version for a few years yet? Instead it was was linux support in terms of no new versions beyond 11.2 that was being withdrawn.

---

### Post by chrisccoulson on 2012-04-05
> **JMB74 said:**
> I thought they were still going to release bugfix versions of the 11.2 version for a few years yet? Instead it was was linux support in terms of no new versions beyond 11.2 that was being withdrawn.

There have been several bugs opened in Adobe's bug tracker for regressions in 11.2, and they've all been closed as wontfix with a comment that they no longer support Linux

---

### Post by JMB74 on 2012-04-05
Just worked that out looking at the announcement again.

[http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

[COLOR=Red]*"Adobe will continue to provide _**security**_ updates to non-Pepper  distributions of Flash Player 11.2 on Linux for five years from its  release"*[/COLOR]

Security fixes = yes.

Non security bugs/regression = no

Oh well.....

---

### Post by lovinglinux on 2012-04-05
> **JMB74 said:**
> I thought they were still going to release bugfix versions of the 11.2 version for a few years yet? Instead it was was linux support in terms of no new versions beyond 11.2 that was being withdrawn.

They will provide security patches for 5 years, not general bug fixes. The problem with hardware acceleration is coming from a few versions back. It is just becoming evident now. They won't fix it. 

> **chrisccoulson said:**
> There have been several bugs opened in Adobe's bug tracker for regressions in 11.2, and they've all been closed as wontfix with a comment that they no longer support Linux

I wonder if nVidia could do something to mitigate this situation?

---

### Post by lovinglinux on 2012-04-05
> **JMB74 said:**
> Just worked that out looking at the announcement again.

[http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

[COLOR=Red]*"Adobe will continue to provide _**security**_ updates to non-Pepper  distributions of Flash Player 11.2 on Linux for five years from its  release"*[/COLOR]

Security fixes = yes.

Non security bugs/regression = no

Oh well.....

The scenario isn't good. Mozilla and Opera won't implement Pepper, because they believe will be bad for the web. 

[http://www.theregister.co.uk/2011/09/12/google_native_client_from_all_sides/page3.html](http://www.theregister.co.uk/2011/09/12/google_native_client_from_all_sides/page3.html)

So, if we want to continue using flash, we will have to use Chrome at some point, unless another browser implements Pepper or if Gnash gets a boost.

---

### Post by chrisccoulson on 2012-04-05
> **lovinglinux said:**
> The scenario isn't good. Mozilla and Opera won't implement Pepper, because they believe will be bad for the web. 

[http://www.theregister.co.uk/2011/09/12/google_native_client_from_all_sides/page3.html](http://www.theregister.co.uk/2011/09/12/google_native_client_from_all_sides/page3.html)

So, if we want to continue using flash, we will have to use Chrome at some point, unless another browser implements Pepper or if Gnash gets a boost.

It doesn't really matter whether other vendors implement Pepper or not, as Adobe have said that Flash will not be available as a separate download but will only be distributed with Chrome.

---

### Post by lovinglinux on 2012-04-05
> **chrisccoulson said:**
> It doesn't really matter whether other vendors implement Pepper or not, as Adobe have said that Flash will not be available as a separate download but will only be distributed with Chrome.

They said Google would take over the development and provide support through Pepper API. It is not clear if Google will be able or want to release it to other browser vendors. At least that is what I understood.

---

### Post by santosh83 on 2012-04-05
> **lovinglinux said:**
> They said Google would take over the development and provide support through Pepper API. It is not clear if Google will be able or want to release it to other browser vendors. At least that is what I understood.

Since Adobe has always made freely available their binary only Flash plugin, I'd expect Google to more or less continue it, under approximately the same licensing terms. 

If that turns out to be the case then I presume that any browser which implements Google's Pepper API would be able to use the version of Flash Google would distribute. If Mozilla and Opera don't do so, then it's only their smaller Linux user-base that'd be affected, since their Windows users can use the Adobe's version which will continue to be available.

Chrome itself would work equally well on all platforms, since it'd have access to both Adobe's Windows plugin and it's own bundled version.

I'd guess that Mozilla would've much less incentive to implement Pepper API than H.264 support.

---

### Post by Sworddragon on 2012-04-05
> **JMB74 said:**
> I thought they were still going to release bugfix versions of the 11.2 version for a few years yet? Instead it was was linux support in terms of no new versions beyond 11.2 that was being withdrawn.

If you look to the current tickets on the adobe site you will see that they try to inofficially stop the support now. They are saying on 11.2 tickets that 11.3+ isn't supported by linux anymore. This is totally besides the point.

Let's hope that some sort of HTML5 + JavaScript will evolve in the near future to support videos and games with a good performance.

---

### Post by pt123 on 2012-04-05
This is a security issue if many people aren't going to upgrade because they don't want to see their videos in blue.

---

### Post by bwallum on 2012-04-06
..are we saying that we cannot get flash content to work using Precise 1386 and Firefox?

---

### Post by bwallum on 2012-04-06
...and why can I get flash working fine in Precise AMD64 with nVidia and not get it working in Precise i386?

---

### Post by ryley on 2012-04-06
Just tried out the new "Pepper" flash player with chrome-unstable. Finally got accelerated rendering on my netbook (N450)! Too bad it can't use my crystalhd decoder card like the latest Netscape based flash player... Does anyone know if the new flash player has an equivaent of the old /etc/adobe/mms.cfg?

---

### Post by bwallum on 2012-04-06
I have now got flash working in Firefox on Precisei386 running an nVidia graphics card - an old one - GeForce 6200/AGP/SSE/3DNOW! - with the current nVidia driver

This is how I did it which has been gleamed from a number of thread links above, this is just a summary. Basically you use an older version of the flashplugin.

Close Firefox

Delete all versions of flash from your system with:```
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper
```then go to [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html ]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html")

Scroll down the page and choose 
(Released 3/05/2012) [[IMG]http://helpx.adobe.com/content/dam/kb/en/142/tn_14266/images/download.gif[/IMG]Flash Player 11.1.102.63]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip") (174 MB)

When you have downloaded it extract the libflashplayer.so file for your system. 

Note: To find out if you are 32 or 64bit click on the top right system button, choose System Settings >Details>Overview 

Now open a terminal and enter the command```
sudo nautilus
```you will open nautilus as root. Navigate to /usr/lib/mozilla/plugins and delete any existing libflashplayer.so file, then drag your new libflashplayer.so file to this folder. Right click on the folder and ensure the Execute check box is ticked to allow the file to run as a programme. Set owner and group as root.

Exit all windows including the the terminal. Now restart Firefox and watch flash content.

---

