---
title: "Ubuntu Customization Guide - Quick Start"
date: 2006-06-02
forum: Ubuntu Customization Guide
---

### Post by ubuntu_demon on 2006-06-02
[B]I'm posting this as a forum user and not as a staff member. This is all on your own risk.

Legal Notice :[/B] Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country.

This HOWTO focuses on the most common customizations suitable for average users.

FIRST STAGE : MAKING YOUR SOURCES.LIST READY
SECOND STAGE : MULTIMEDIA AND PROPRIETARY/RESTRICTED FORMATS
THIRD STAGE : OPTIONAL OPEN SOURCE SOFTWARE
FOURTH STAGE : OPTIONAL PROPRIETARY SOFTWARE
FIFTH STAGE : PERFORMANCE TWEAKS
SIXTH STAGE : PROPRIETARY BINARY VIDEODRIVERS
SEVENTH STAGE : REBOOT

There is a good reason why Ubuntu doesn't include better multimedia support on default. 

[I]Some file formats are proprietary, which means that they are owned by a company or other organisation. Sometimes, the owners of such formats charge licensing fees or impose legal restrictions on the use of their formats. This means that people may be unable to use or distribute these formats without first paying a fee or applying for a license.

A Free or open format is one which can be used by anyone, free of legal restrictions on how they use the format. Free formats are very popular - the World Wide Web is based on the open HTML standard. Ubuntu supports many free formats and the open-source community as a whole encorages their wider use. [/I]

[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

**FIRST STAGE : MAKING YOUR SOURCES.LIST READY**


Here's how to make your sources.list ready :

**my recommended Dapper sources.list** 
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

Don't forget to run (in the terminal) :
```

sudo aptitude update && sudo aptitude upgrade

```

**SECOND STAGE : MULTIMEDIA AND PROPRIETARY/RESTRICTED FORMATS**


Luckily for most people sound support is pretty good. If you don't hear the drums when you your computer shows the login screen then you are probably having some sound issue (please check the cables first). If your soundcard doesn't work at all then you have to fix that first. If you are new to Ubuntu and you know someone who's good with Linux then this is a good moment to ask for his/her help. This is the place to start : [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 

Okay you hear the drums when your computer shows the login screen. Let's continue and install some stuff.

[B]First you have to start a terminal from applications->accessoires->terminal

Then you type in these commands.[/B]

Installing a bunch of codecs from universe/multiverse : 
```

sudo aptitude install gstreamer0.10-plugins-ugly mpg321 vorbis-tools gstreamer0.10-ffmpeg gstreamer0.10-gl libxine-main1 libxine-extracodecs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll

```

To install w32codecs :
```

wget -c http://mikesplanet.net/dapper/w32codecs_20060611-0.1~dapper1_i386.deb
sudo dpkg -i w32codecs_20060611-0.1~dapper1_i386.deb

```
This is taken from a fellow mod's blog right here : [http://www.mikesplanet.net/?p=38](http://www.mikesplanet.net/?p=38)

It might create a false positive in your virus scanner. Don't worry it's not a virus.

This command installs a couple of good players. I always use totem-gstreamer instead of totem-xine. Because I want to be able to try the gstreamer framework for playback. If a video doesn't run in any of these you might as well give up :
```

sudo aptitude install totem-gstreamer vlc mplayer gxine

```
You don't have to install both xine-ui and gxine alhough they don't take up much space. They look different but they are using the same "engine".

To be able to play videos in firefox you have three choices. Depending on which websites you visit you will get better results with one or the other. Try **one at a time** and don't forget to restart firefox :
```

sudo aptitude install mozilla-plugin-vlc
sudo aptitude install mozilla-mplayer
sudo aptitude install totem-gstreamer-firefox-plugin

```

Problems with video in firefox ?

-Restart firefox and see whether that helps.
-Save your work and log out gnome (Ubuntu). Now you are back at the login screen. Log in again and see if the problem is solved :).
-If this is not about flash and you are still experiencing problems then try a different different "player" (mozilla-plugin-vlc,mozilla-mplayer,totem-gstreamer-firefox-plugin)
-Remember it's depending on the websites you visit which one (mozilla-plugin-vlc,mozilla-mplayer,totem-gstreamer-firefox-plugin) will give the best results.

To get flash :
```

sudo aptitude install flashplugin-nonfree
sudo update-flashplugin

```

Sound problems with flash ?
[http://ubuntuforums.org/showthread.php?p=1087994#post1087994](http://ubuntuforums.org/showthread.php?p=1087994#post1087994)
The "Flash Troubleshooting" section here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

To install java JRE from sun :
```

sudo aptitude install sun-java5-bin sun-java5-plugin  
sudo update-alternatives --config java

```
and choose the sun option 
(/usr/lib/jvm/java-1.5.0-sun/jre/bin/java)

Microsoft TrueType core fonts :
```

sudo aptitude install msttcorefonts

```

If you burn a lot of cd's/dvd's it's good to check whether DMA is on for your burner.
***Warning:** Enabling DMA can be dangerous in some cases. Usually issues are directly related to faulty hardware, poorly written drivers, or using settings that are unsupported by your system. USING HDPARM INCORRECTLY CAN CAUSE MAJOR DATA CORRUPTION AND/OR LOSS. Most systems newer than 4 years support DMA.*
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

I bet you didn't know that your dvd's are encrypted? You need to install this to be able to play them. (libdvdcss2 comes from cipherfunk)
```

sudo aptitude install libdvdread3 regionset
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

Jerky DVD playback ? First check whether DMA is on for your dvd-drive :
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

From [https://help.ubuntu.com/community/RestrictedFormats#dvd](https://help.ubuntu.com/community/RestrictedFormats#dvd) :
> If your DVD player regularly locks up when you try to play back a DVD, your DVD player probably does not match the DVD's Region Code. Region Codes are a form of vendor lock-in.

On delivery, most DVD drives have no region code set. The drive firmware allows you to change the region code, but on nearly all drives you are limited to five (5) changes.

To change the Region Code of your DVD player, insert a DVD from your region in the DVD player, and do the following:
```

regionset

```

For more information about proprietary/restricted formats look here :
[B]
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)[/B]

**THIRD STAGE : OPTIONAL OPEN SOURCE SOFTWARE**

F-sport is a personal photo management application.

If you want f-spot :
```

sudo aptitude install f-spot

```

If you want to show of a nice penguin game to your friends. It has two-player support.

If you want frozen-bubble :
```

sudo aptitude install frozen-bubble

```

Ubuntu comes with evolution which looks a bit like outlook but some (like me) prefer thunderbird.

If you want thunderbird  :
```

sudo aptitude install mozilla-thunderbird 

```

If you want GPG support for thunderbird :
```

sudo aptitude install mozilla-thunderbird-enigmail 

```

Liferea is a nice (gnome) program if you like to follow/read RSS feeds.

If you want liferea :
```

sudo aptitude install liferea

```

beep-media-player (bmp) - Versatile audio player that supports Winamp skins

If you want bmp :
```

sudo aptitude install beep-media-player

```

If you want wine :

[I]If you uncommented the wine repository of "my recommended Dapper sources.list" then you will get a newer version. Here's more information :
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
[/I]
```

sudo aptitude install wine

```


**FOURTH STAGE : OPTIONAL PROPRIETARY SOFTWARE**

If you want realplayer :
```

sudo aptitude install realplay

```

If you want opera :
```

sudo aptitude install opera

```

If you want skype :
```

sudo aptitude install skype

```


**FIFTH STAGE : PERFORMANCE TWEAKS**


IMHO picking the right kernel is something everyone should do. In some cases it even might solve some obscure problem you have. It's easy and safe to try. 

If you have an intel Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV you should probably install this kernel :
```

sudo aptitude install linux-686

```

If you have an amd duron/athlon you should probably install this kernel :
```

sudo aptitude install linux-k7

```

**If you are in doubt** whether you have installed the right kernel **then do a reboot** and find out. There will be multiple options in your grub menu ; the new kernel will be the default.

You can choose to continue with the fourth stage at this moment. The rest of the performance tweaks will be less important. It's fun to do if you like to tweak though.

I've collected a couple of optional performance tweaks which are quite safe and easy to do here :

Desktop performance tweaks
[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)

(note : I will improve the guide to make the performance tweaks more easy to understand)


**SIXTH STAGE : PROPRIETARY BINARY VIDEODRIVERS**


To find out which videocard you have :
```

lspci | grep VGA

```

**NVIDIA**

[B]
A note before we start :[/B]
**Instead** of installing linux-restricted-modules-`uname -r` you can also install linux-386, linux-686 or linux-k7. This will install the restricted modules as a dependency and it makes sure that they stay installed when upgrading your kernel. So no need to install *linux-restricted-modules-`uname -r`* if you have picked the right kernel in the previous (performance tweaks) stage. 

If you have a nvidia (Geforce 3 or newer) videocard then you should probably install this videodriver :
```

$sudo aptitude install nvidia-glx nvidia-kernel-common linux-restricted-modules-`uname -r`
sudo nvidia-xconfig

```

These are the video cards for which you have to try the legacy driver first (before trying the regular driver). You should try the regular nvidia driver if your driver is not on the following list.

From [http://www.ubuntuforums.org/showthread.php?t=233241](http://www.ubuntuforums.org/showthread.php?t=233241) :

> 
NVIDIA chip name 	Device PCI ID
RIVA TNT 	0x0020
RIVA TNT2/TNT2 Pro 	0x0028
RIVA TNT2 Ultra 	0x0029
Vanta/Vanta LT 	0x002C
RIVA TNT2 Model 64/Model 64 Pro 	0x002D
Aladdin TNT2 	0x00A0
GeForce 256 	0x0100
GeForce DDR 	0x0101
Quadro 	0x0103
GeForce2 GTS/GeForce2 Pro 	0x0150
GeForce2 Ti 	0x0151
GeForce2 Ultra 	0x0152
Quadro2 Pro 	0x0153
GeForce4 460 Go 0x0177


Here's how to install the legacy (propretiary) nvidia driver :
```

sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`
sudo nvidia-xconfig

```

If you have a (very) new nvidia videocard and you are experiencing problems with the nvidia-glx driver included in Dapper :
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

More information :
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

**Don't forget** to post the way you got your Nvidia videocard to work (if you installed a proprietary driver) :
[http://www.ubuntuforums.org/showthread.php?t=221313](http://www.ubuntuforums.org/showthread.php?t=221313)

If you have problems you can also look in that thread whether someone else has the same videocard. He or she might already have solved your problems.

**ATI**

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://ubuntuforums.org/showthread.php?p=423584](http://ubuntuforums.org/showthread.php?p=423584)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

**Don't forget** to post the way you got the ATI driver to work (if you installed a proprietary driver) :
[http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)

If you have problems you can also look in that thread whether someone else has the same videocard. He or she might already have solved your problems.

**general information**

Dealing with problems with the Xserver
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

Still having problems with your videocard ? Then create a new thread here :
[http://www.ubuntuforums.org/forumdisplay.php?f=138](http://www.ubuntuforums.org/forumdisplay.php?f=138)
Don't forget to include this information :
- what did you try to get it working ?
- the (compressed) file : /var/log/kern.log
- the (compressed) file : /var/log/Xorg.0.log
- The result of : 
```

lspci -n | grep 0300
lspci | grep VGA

```

HowTo: Dual Monitors (Xinerama/TwinView/MergedFB)
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

**SEVENTH STAGE : REBOOT**

**Don't forget to do a reboot** after you have installed a new kernel and/or new videodriver.

Here's more documentation :
[http://doc.gwos.org](http://doc.gwos.org)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

In the future some of this customizing will be more easy. See :

CommonCustomizations - feedback request
[http://www.ubuntuforums.org/showthread.php?t=206535](http://www.ubuntuforums.org/showthread.php?t=206535)

I attended most of the BOF's. I hope this speficiation will make Ubuntu Customization Guide useless.

**Ubuntu Customization Guide Quick Start (discussion)**
[http://www.ubuntuforums.org/showthread.php?t=236429](http://www.ubuntuforums.org/showthread.php?t=236429)

---

