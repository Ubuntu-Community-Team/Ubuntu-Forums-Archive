---
title: "Flash crash with 720p fullscreen video (YouTube)"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 8Kuula on 2012-03-12
For some reason when watching flash videos from YouTube, 720p fullscreen videos play ~30sec and then video freezes, sound continues and after while flash crashes.
If I change video to 480p, 1080p or do not play 720p video in fullscreen, then all works fine.

[http://youtu.be/rJ0sSc18Wb0](http://youtu.be/rJ0sSc18Wb0) here is example where it hapends.

Have not noticed that this would hapend other sites than YouTube.

Shockwave Flash 11.1 r102 (last updated 12.03.2012)
Firefox 11.0
Ubuntu 12.04 64-bit Beta
nvidia driver version 295.20

---

### Post by Gavin77 on 2012-03-12
I tried that video link and it worked fine here using Firefox 12 (Aurora) and Intel graphics.

I ran it at 720p in fullscreen and it played perfectly.

---

### Post by Gregory Lee on 2012-03-12
> **8Kuula said:**
> ... video freezes, sound continues and after while flash crashes.

I tried your example with results sort of like yours.  I played the video at 480p fullscreen, and after a few minutes, the video froze while the sound continued.  If I had had the patience, eventually Flash might have crashed, but I switched to another workspace, did "top" in a terminal to find the process number of "plugin-container", which is running running Flash, and used the process number to kill it.  (This is old news, for me, since I've had many Flash crashes of this kind, on my old Fedora 6 system, as well as Ubuntu 12.04.)

Remembering, finally, that you wanted to know about a problem specific to 720p at full screen, I tried it again this way, and wouldn't you know!, this time it played through the whole 20:45 minutes without freezing or crashing.  (Nice video; boring audio narration.)

What does it mean?  I don't know, except Flash obviously doesn't work all that well.

I saw a new version of Flash being downloaded when I updated a few hours ago.

---

### Post by 8Kuula on 2012-03-13
More precise version, if it helps.
```
$ dpkg --list flashplugin-installer
||/ Name                Version             Description
+++-===================-===================-======================================================
ii  flashplugin-install 11.1.102.63ubuntu2  Adobe Flash Player plugin installer

```

---

### Post by lovinglinux on 2012-03-13
Do you have AdBlock or NoScript?

---

### Post by 8Kuula on 2012-03-14
Both installed.
Tested both disabled and enabled. Flash crash either way.

---

### Post by lovinglinux on 2012-03-14
Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by 8Kuula on 2012-03-14
Hmm, first time hear about that addon.
So installed it. Apears to be realy wierd addon. But anyways.
Wants me to run some script asking root password, so had to export that script :]

Looks of that script it wants to download 11.2 beta flash...
Mkay.
```
$ wget http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p5_install_lin_64_013112.tar.gz
--2012-03-14 23:27:30--  http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p5_install_lin_64_013112.tar.gz
Resolving download.macromedia.com (download.macromedia.com)... 2.19.3.191
Connecting to download.macromedia.com (download.macromedia.com)|2.19.3.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-03-14 23:27:30 ERROR 404: Not Found.
```
Bleh...

Oh well lets see tweaking part.
Tested GPU validation override option with flash that i have installed.
```
:/etc/adobe$ cat mms.cfg 
OverrideGPUValidation=true
```
No luck with that. Still crashes.

```
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg
```
Line in script do not appear to do anything. /etc/adobe/mms.cfg file remains same(??).

```
NPVIEWER=/usr/lib/nspluginwrapper/i386/linux/npviewer
if test -f "${NPVIEWER}";then
cat /usr/lib/nspluginwrapper/i386/linux/npviewer | sed '/export GDK_NATIVE_WINDOWS=1/d' | sudo tee /usr/lib/nspluginwrapper/i386/linux/npviewer
fi
```
/usr/lib/nspluginwrapper/i386/linux/npviewer file do not exists.

---

### Post by lovinglinux on 2012-03-14
> **8Kuula said:**
> Hmm, first time hear about that addon.
So installed it. Apears to be realy wierd addon. But anyways.
Wants me to run some script asking root password, so had to export that script :]

Looks of that script it wants to download 11.2 beta flash...
Mkay.
```
$ wget http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p5_install_lin_64_013112.tar.gz
--2012-03-14 23:27:30--  http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p5_install_lin_64_013112.tar.gz
Resolving download.macromedia.com (download.macromedia.com)... 2.19.3.191
Connecting to download.macromedia.com (download.macromedia.com)|2.19.3.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-03-14 23:27:30 ERROR 404: Not Found.
```
Bleh...

Oh well lets see tweaking part.
Tested GPU validation override option with flash that i have installed.
```
:/etc/adobe$ cat mms.cfg 
OverrideGPUValidation=true
```
No luck with that. Still crashes.

```
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg
```
Line in script do not appear to do anything. /etc/adobe/mms.cfg file remains same(??).

```
NPVIEWER=/usr/lib/nspluginwrapper/i386/linux/npviewer
if test -f "${NPVIEWER}";then
cat /usr/lib/nspluginwrapper/i386/linux/npviewer | sed '/export GDK_NATIVE_WINDOWS=1/d' | sudo tee /usr/lib/nspluginwrapper/i386/linux/npviewer
fi
```
/usr/lib/nspluginwrapper/i386/linux/npviewer file do not exists.

Adobe removed the file from the server, but I just updated to get the new flash version. First, click "Check Update" in Flash-Aid menu, then wait for the new version alert, then run the Wizard again.

You might want to try disabling GPU validation override in the Tweaking section. It might help, since I have received reports about instability issues with nVidia drivers. If that doesn't work, visit an YouTube video, right-click on it, select "Settings" then disable hardware acceleration.

---

### Post by 8Kuula on 2012-03-15
> **lovinglinux said:**
> Adobe removed the file from the server, but I just updated to get the new flash version. First, click "Check Update" in Flash-Aid menu, then wait for the new version alert, then run the Wizard again.

You might want to try disabling GPU validation override in the Tweaking section. It might help, since I have received reports about instability issues with nVidia drivers. If that doesn't work, visit an YouTube video, right-click on it, select "Settings" then disable hardware acceleration.

Managed to update flash to 11.2.202.221. Used url that flash-aid gave me, /etc/adobe/mms.cfg removed.
Fullscreen 720p video still freezes. Only does it somewhat faster and in 5min it have not closed fullscreen player window, so had to kill plugin-container myself.

I may have stumbled to other bug with flash. Both 11.2.202.221 and 11.1 r102.
Adobe Flash Video Settings, well it opens, can't interact with it after that :D
So can't disable hardware acceleration with that metod, it just sits there, can't even close it.
Is there other way to disable it?

---

### Post by sdowney717 on 2012-03-15
Worked here on an 8400 GS PCIE vid card and core2duo 8gb ram

perhaps your hardware has issues.

---

### Post by 8Kuula on 2012-03-15
I have GeForce GTX 285 card. Driver version 295.20.

---

### Post by lovinglinux on 2012-03-15
> **8Kuula said:**
> Managed to update flash to 11.2.202.221. Used url that flash-aid gave me, /etc/adobe/mms.cfg removed.
Fullscreen 720p video still freezes. Only does it somewhat faster and in 5min it have not closed fullscreen player window, so had to kill plugin-container myself.

I may have stumbled to other bug with flash. Both 11.2.202.221 and 11.1 r102.
Adobe Flash Video Settings, well it opens, can't interact with it after that :D
So can't disable hardware acceleration with that metod, it just sits there, can't even close it.
Is there other way to disable it?

Try the other installation options. You can install the 32bit with the wrapper and if you have thr partner repository enabled, Flash-Aid willa lso offer the 64bit stable plugin.

For the settings try [http://forums.adobe.com/message/3863047#3863047](http://forums.adobe.com/message/3863047#3863047)

---

### Post by 8Kuula on 2012-03-16
> **lovinglinux said:**
> Try the other installation options. You can install the 32bit with the wrapper and if you have thr partner repository enabled, Flash-Aid willa lso offer the 64bit stable plugin.

For the settings try [http://forums.adobe.com/message/3863047#3863047](http://forums.adobe.com/message/3863047#3863047)

Actualy Flash-Aid won't offer 64bit stable plugin, "Adobe Stable, from repositories (32bit)" and "Adobe Beta, from Adobe Labs" are only options in wizard.

Selecting "Adobe Stable, from repositories (32bit)" from wizard, script is
```
#!/bin/bash
echo "***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************"
sudo -k
echo '***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************'
sudo apt-get purge flashplugin.*installer
sudo apt-get purge flashplugin-downloader
echo '***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************'
sudo apt-get update
echo '***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************'
sudo apt-get install flashplugin-installer
echo '***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************'
sudo mkdir /etc/adobe
sudo touch /etc/adobe/mms.cfg
cat /etc/adobe/mms.cfg | sed '/OverrideGPUValidation=true/d' | sudo tee /etc/adobe/mms.cfg
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg
NPVIEWER=/usr/lib/nspluginwrapper/i386/linux/npviewer
if test -f "${NPVIEWER}";then
TWEAK=$(cat /usr/lib/nspluginwrapper/i386/linux/npviewer | grep 'GDK_NATIVE_WINDOWS=1')
if test -z "${TWEAK}";then
echo '#!/bin/sh' | sudo tee /usr/lib/nspluginwrapper/i386/linux/npviewer
echo 'TARGET_OS=linux' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
echo 'TARGET_ARCH=i386' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
echo 'case "$*" in' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
echo '*libflashplayer*)' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
echo '	export GDK_NATIVE_WINDOWS=1' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
echo '	;;' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
echo 'esac' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
echo '. /usr/lib/nspluginwrapper/noarch/npviewer' | sudo tee -a /usr/lib/nspluginwrapper/i386/linux/npviewer
fi
fi
echo -n "***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************" && read
```
Looking it for while and still can't get my head around why it first removes flashplugin-installer, updates repositories and then install flashplugin-installer back?
How that changes it to be 32bit version?

For settings, from that [http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html) page settings is disabled, it shows in menu but can't click it and it is gray.

---

### Post by lovinglinux on 2012-03-31
> **8Kuula said:**
> Actualy Flash-Aid won't offer 64bit stable plugin, "Adobe Stable, from repositories (32bit)" and "Adobe Beta, from Adobe Labs" are only options in wizard.

It only display the 64bit stable if you enable the Partner repository in Software Sources.


> **8Kuula said:**
> 
Looking it for while and still can't get my head around why it first removes flashplugin-installer, updates repositories and then install flashplugin-installer back?
How that changes it to be 32bit version?


Yes, it removes the plugin from various places than install again, to make sure there is no conflicting plugins.

It is 32bit with the 64bit wrapper.

> **8Kuula said:**
> For settings, from that [http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html) page settings is disabled, it shows in menu but can't click it and it is gray.

Try to delete the flash config file:

```
sudo rm -f /etc/adobe/mms.cfg
```

---

### Post by 8Kuula on 2012-03-31
Partner repositories enabled. Installs adobe-flashplugin, it is same version that flashplugin-installer package installs after all flashplugin-installer just downloads it from adobe and adobe-flashplugin package is "real deal" that do not download it.
Still crashes anyways.

> Yes, it removes the plugin from various places than install again, to make sure there is no conflicting plugins.

It is 32bit with the 64bit wrapper.
And yet it ain't, when flashplugin-installer package is first removed and then installed back, it won't magicaly change to 32bit with 64bit wrapper, whole /usr/bin/nspluginwrapper directory is not created.
```
$ apt-cache show flashplugin-installer
Package: flashplugin-installer
Priority: optional
Section: multiverse/web
Installed-Size: 142
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@knars.be>
Architecture: amd64
Source: flashplugin-nonfree
Version: 11.2.202.228ubuntu1
Replaces: flashplugin (<< 6), flashplugin-downloader (<< 11.1.102.55ubuntu3), flashplugin-nonfree (<< 11.0.1.152ubuntu1)
Provides: flashplugin-nonfree
Depends: debconf (>= 0.5) | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g, libnss3-1d, libnspr4-0d, libcurl3 | libcurl3-gnutls, libasound2
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, x-ttcidfont-conf, ttf-mscorefonts-installer, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-nonfree (<< 11.0.1.152ubuntu1), libflashsupport
Breaks: flashplugin-downloader (<< 11.1.102.55ubuntu3)
Filename: pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.228ubuntu1_amd64.deb
Size: 8750
MD5sum: 49e6c4be75866a8e373ade76ce1ebbe8
SHA1: 4c2cf8cbe0faf44ff03eb5e70b7c934e1534fd19
SHA256: eab5d3d2fd19daab19e36b2d2b0690a903e5086bb012c57df7d2c1549777786e
Description-en: Adobe Flash Player plugin installer
 **Downloads and Installs the Adobe Flash Player plugin**. The Adobe Flash Player
 plugin supports playing of media and other dynamic content online.
 .
 The Adobe Flash Player plugin will work with a range of web-browsers including,
 limited to:
  * Firefox
  * Chromium
  * SeaMonkey
  * Iceweasel
  * Iceape
  * Galeon
  * Epiphany
  * Konqueror
 .
 WARNING: Installing this Ubuntu package causes the Adobe Flash Player plugin to
 be downloaded from the Adobe web site. The distribution license of the
 Adobe Flash Player plugin is available at www.adobe.com. Installing this
 Ubuntu package implies that you have accepted the terms of that license.
Multi-Arch: foreign
Homepage: http://www.adobe.com/products/flashplayer.html
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player (http://www.adobe.com)
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Description-md5: a03e9ebc20ce82c05567d088e79bf750
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```
flashplugin-installer package just downloads and installs same data that adobe-flasplugin installs directly, in 64bit system it still is 64bit version without wrapper.

Anyways, after all this wiggling around, I have concluded that there is something wrong with Adobe flashplugin or nVidia driver. I am leaning more to direction of Adobe flashplugin, other resolutions and non fullscreen 720p works.

---

### Post by lovinglinux on 2012-03-31
Sorry, you are correct. They changed the behaviour of flashp&#314;ugin-installer recently, because it was the 32bit last time I released Flash-Aid. I just tested it and indeed is the 64bit without the wrapper now.

About the nVidia issues, there are many threads this week reporting various issues with Flash and nVidia.

---

### Post by lovinglinux on 2012-03-31
> **8Kuula said:**
> So can't disable hardware acceleration with that metod, it just sits there, can't even close it.
Is there other way to disable it?

Try this:

> **mc4man said:**
> I'd go with an older flash version but if you wish to disable hw acceleration in the flash settings you must do it in the player while it's  in fullscreen
(scrollbars make the settings box unclickable

---

### Post by mc4man on 2012-03-31
Just to add regarding the flash settings box - in unity-2d it is usable when the player is windowed, only 3d needs to be full-screened

---

### Post by 8Kuula on 2012-03-31
Aand v11.2.202.228 without hardware acceleration fullscreen 720p, crash and burns.

---

### Post by mc4man on 2012-03-31
> **8Kuula said:**
> Aand v11.2.202.228 without hardware acceleration fullscreen 720p, crash and burns.
Then just use an older version of flash if you're going to watch 720p in fullscreen
(or find some other means to view your video's

Edit: or use google-chrome/chromium

---

