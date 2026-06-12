---
title: "Ubuntu Customization Guide - Quick Start(discussion)"
date: 2006-06-02
forum: Ubuntu Customization Guide
---

### Post by raublekick on 2006-06-02
excellent, thank you very much! 

i'm so glad java is in the repos.

---

### Post by l33tDad on 2006-06-02
Great guide .. One question: how do I install Java 1.4.2_05 instead of 1.5*? If I can get a certain Java app to work on Ubuntu (won't work in Java 1.5*), I might be able to convince the powers that be at work to at least consider killing some windows boxes.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=l33tDad]Great guide .. One question: how do I install Java 1.4.2_05 instead of 1.5*? If I can get a certain Java app to work on Ubuntu (won't work in Java 1.5*), I might be able to convince the powers that be at work to at least consider killing some windows boxes.[/QUOTE]
look here : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by DarthGroznii on 2006-06-02
This has not worked for me in trying to install the Java plugin - here are the messages I get - 

> christian@stilgar:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  sun-java5-bin sun-java5-jre
Suggested packages:
  sun-java5-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed
  sun-java5-bin sun-java5-jre
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After unpacking 83.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 74018 files and directories currently installed.)
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please advise.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=DarthGroznii]This has not worked for me in trying to install the Java plugin - here are the messages I get - 

Please advise.[/QUOTE]

First try this :
$sudo apt-get update
$sudo apt-get dist-upgrade

If you run into crazy problems please start a new thread here :
[http://www.ubuntuforums.org/forumdisplay.php?f=140](http://www.ubuntuforums.org/forumdisplay.php?f=140)

Be elaborate and post your errors. Good luck!

(I might go to sleep soon so I hope someone can help you)

---

### Post by ubuntu_demon on 2006-07-02
In the future some if this is more easy. See :

CommonCustomizations - feedback request
[http://www.ubuntuforums.org/showthread.php?t=206535](http://www.ubuntuforums.org/showthread.php?t=206535)

---

### Post by Gr4v3 on 2006-07-02
thank you nice post it works great

---

### Post by ubuntu_demon on 2006-07-03
[QUOTE=Gr4v3]thank you nice post it works great[/QUOTE]
thnx!

---

### Post by ubuntu_demon on 2006-07-09
I posted on my blog about this new dapper-commercial repository :
[http://ubuntudemon.wordpress.com/2006/07/09/dapper-commercial-repository/](http://ubuntudemon.wordpress.com/2006/07/09/dapper-commercial-repository/)

---

### Post by RRS on 2006-07-13
Thanks, just followed your guide in a fresh Dapper install, worked great with no errors reported.

New commercial repository made getting Realplayer much easier then last time.

---

### Post by ubuntu_demon on 2006-07-14
> **RRS said:**
> Thanks, just followed your guide in a fresh Dapper install, worked great with no errors reported.


I'm glad to be of help. And thank you for the feedback.

> **RRS said:**
> 
New commercial repository made getting Realplayer much easier then last time.

Yeah it's great if you want realplayer (or opera).

---

### Post by manicka on 2006-07-14
Nice summary of some of the more common customisations offered at [ubunutguide.org]("http://ubuntuguide.org")

---

### Post by ubuntu_demon on 2006-07-14
> **manicka said:**
> Nice summary of some of the more common customisations offered at [ubunutguide.org]("http://ubuntuguide.org")
Thank you :)

---

### Post by ubuntu_demon on 2006-07-22
I posted about this thread to the digg and to my blog :
[http://digg.com/linux_unix/HOWTO_common_customizations_such_as_multimedia_in_Ubuntu_Dapper](http://digg.com/linux_unix/HOWTO_common_customizations_such_as_multimedia_in_Ubuntu_Dapper)
[http://ubuntudemon.wordpress.com/2006/07/22/howto-common-customizations-such-as-multimedia-in-ubuntu-dapper/](http://ubuntudemon.wordpress.com/2006/07/22/howto-common-customizations-such-as-multimedia-in-ubuntu-dapper/)

---

### Post by ubuntu_demon on 2006-08-07
This HOWTO focuses on the most common customizations suitable for average users.

I have a personal preference to use commands in the terminal because :
- the user sees and learns what is happening
- the user can easily choose not to do some parts

My guide now consists of five stages :

FIRST STAGE : making your sources.list ready
SECOND STAGE : installing the software and codecs
THIRD STAGE : proprietary binary videodrivers
FOURTH STAGE : performance tweaks
FIFTH STAGE : reboot

I blogged about this here :
[http://ubuntudemon.wordpress.com/2006/08/07/howto-common-customizations-such-as-multimedia-in-ubuntu-dapper-2/](http://ubuntudemon.wordpress.com/2006/08/07/howto-common-customizations-such-as-multimedia-in-ubuntu-dapper-2/)

---

### Post by MacMan on 2006-08-07
> **ubuntu_demon said:**
> The focus of this guide is on the most common customizations which are suitable for average users.

Ciao ubuntu_demon,

I got an error while following your guide:
```
$ sudo apt-get install vlc mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
```

Same thing with libxine-extracodecs.

*EDIT*: Never mind, I've found what was wrong: I didn't enable the **multiverse** repositories... Shame on me. :-(

Ciao.
-- 
Mac

---

### Post by SeaRox on 2006-08-09
Great thread!  I wish I would have read this one before I used EasyUbuntu and had to fix a few things.

---

### Post by ubuntu_demon on 2006-08-09
> **SeaRox said:**
> Great thread!  I wish I would have read this one before I used EasyUbuntu and had to fix a few things.
Thanks :).

---

### Post by eKlipSe on 2006-08-10
[COLOR="Blue"][B]Hi all, well i downloaded 'Easy Ubuntu', and i can see flash video on the web now. i can also play videos on Google and You Tube - however i dont get any sound with them ? On MySpace i can't get the videos to play there.

Can anyone help me out and tell me what else i need. i didnt install all the 'Easy Ubuntu' packets ... i just checked the ones i thought i would need for video playback on the internet. ThanX riK ... : )  i'm really new at this.
[/B][/COLOR]

---

### Post by ubuntu_demon on 2006-08-10
> **eKlipSe said:**
> [COLOR="Blue"][B]Hi all, well i downloaded 'Easy Ubuntu', and i can see flash video on the web now. i can also play videos on Google and You Tube - however i dont get any sound with them ? On MySpace i can't get the videos to play there.

Can anyone help me out and tell me what else i need. i didnt install all the 'Easy Ubuntu' packets ... i just checked the ones i thought i would need for video playback on the internet. ThanX riK ... : )  i'm really new at this.
[/B][/COLOR]
You should choose yourself whether you want to remove Easy Ubuntu  and follow my guide. phase 1 and phase 2 (are important for multimedia)

If you have followed my guide and you are still experiencing problems with sound in firefox first try to log out (gnome) and then log back in again. I will elaborate in my guide. Let me know if you have problems.

I have a **personal** preference to use commands in the terminal because :
- the user sees and learns what is happening
- the user can easily choose not to do some parts

You might also go to the Easy Ubuntu forum section to see whether they can help you.

Easy Ubuntu
[http://ubuntuforums.org/forumdisplay.php?f=86](http://ubuntuforums.org/forumdisplay.php?f=86)

---

### Post by SeaRox on 2006-08-12
Thanks.  It worked great for me.  It even fixed some problems that were created when I used EasyUbuntu.=D>

---

### Post by ubuntu_demon on 2006-08-13
> **SeaRox said:**
> Thanks.  It worked great for me.  It even fixed some problems that were created when I used EasyUbuntu.=D>
Great. I'm glad it helped you. Suggestions are welcome :).

---

### Post by dvader on 2006-08-13
ubuntu_demon


right kernel is something everyone should do, install linux-686


Before making  this modification , I would to know if it will cause any problems with my current system??


I have a 1.7 celleron CPU and have already installed the nVidia driver(NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)) and the xgl graphics display   and would not wish to mess it up


Any suggestions on how to proceed with the 686 kernek  

Dvader

---

### Post by ubuntu_demon on 2006-08-13
> **dvader said:**
> ubuntu_demon


right kernel is something everyone should do, install linux-686


Before making  this modification , I would to know if it will cause any problems with my current system??


I have a 1.7 celleron CPU and have already installed the nVidia driver(NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)) and the xgl graphics display   and would not wish to mess it up


Any suggestions on how to proceed with the 686 kernek  

Dvader
You can still boot the old (current) kernel in case of problems(it becomes a grub entry).

---

### Post by marcus12 on 2006-08-14
Thank you so much! I just started running ubuntu (with xfce since I am running it on older hardware), but I was really dreading having to find and install codecs since I wanted to be able to see my movies and music on this machine. This made it much easier, thanks again. :D

---

### Post by ubuntu_demon on 2006-08-14
> **marcus12 said:**
> Thank you so much! I just started running ubuntu (with xfce since I am running it on older hardware), but I was really dreading having to find and install codecs since I wanted to be able to see my movies and music on this machine. This made it much easier, thanks again. :D
your welcome :)

---

### Post by crag277 on 2006-08-16
I may be wrong, but if you install a new kernel, then install a new VGA driver, then reboot into the new kernel, won't it just use the regular VSEA driver?  Then you'd have to install proprietary drivers again in the new kernel.

So maybe one more reboot should be added to the guide.

Otherwise, excellent work!  This will save new users hours of scouring the forums for a specific solution.

---

### Post by ubuntu_demon on 2006-08-16
> **crag277 said:**
> I may be wrong, but if you install a new kernel, then install a new VGA driver, then reboot into the new kernel, won't it just use the regular VSEA driver?  Then you'd have to install proprietary drivers again in the new kernel.

So maybe one more reboot should be added to the guide.


AFAIK there is no problem. I have tried it. If someone experiences another result please let me know.

> **crag277 said:**
> 
Otherwise, excellent work!  This will save new users hours of scouring the forums for a specific solution.

thank you very much!

---

### Post by noumaan on 2006-08-17
> **ubuntu_demon said:**
> 
My guide now consists of five stages :

FIRST STAGE : making your sources.list ready
SECOND STAGE : installing the software and codecs

I would say that it is better to add a suggestion or a new step. 

Planning the customization. 

which could save a lot of time.

---

### Post by ubuntu_demon on 2006-08-17
> **noumaan said:**
> I would say that it is better to add a suggestion or a new step. 

Planning the customization. 

which could save a lot of time.
Thnx. I will add something like this.

---

### Post by K.Mandla on 2006-08-24
Fantastic work. I don't know how this escaped me for so long, but I can't wait to get home and try some of it out. Thanks!

---

### Post by ubuntu_demon on 2006-08-24
> **K.Mandla said:**
> Fantastic work. I don't know how this escaped me for so long, but I can't wait to get home and try some of it out. Thanks!
no problem :)

suggestions are very welcome

---

### Post by Eddieduce on 2006-08-30
Hey, Ub's, is it possible to use Wine to run webpages with Shockwave video as embeded web pages?  I'm trying to find a work around for having no Linux Ubuntu compatible ShockWave Player and for viewing/hearing video within a web page withough having to worry about the plugin. Please read NOTE.

NOTE: I am NOT looking for Flash, I already have it.

I have already checked with Adobe but there is still no version that will work with Ubuntu!*

It also seems that the request petition has not been making that big of an impact with Adobe since I have heard no news about a compatible version for Ubuntu even though there are several thousand people signed up.

*there is a X86 bit version but I doubt that can be tweaked.

--Ed

---

### Post by ubuntu_demon on 2006-08-31
> **Eddieduce said:**
> Hey, Ub's, is it possible to use Wine to run webpages with Shockwave video as embeded web pages?  I'm trying to find a work around for having no Linux Ubuntu compatible ShockWave Player and for viewing/hearing video within a web page withough having to worry about the plugin. Please read NOTE.

NOTE: I am NOT looking for Flash, I already have it.

I have already checked with Adobe but there is still no version that will work with Ubuntu!*

It also seems that the request petition has not been making that big of an impact with Adobe since I have heard no news about a compatible version for Ubuntu even though there are several thousand people signed up.

*there is a X86 bit version but I doubt that can be tweaked.

--Ed
You can use wine to install windows firefox. AFAIK you can install (almost?) every plugin/player for it. I haven't tried myself.

By the way x86 is what you should use for a desktop (instead of 64 bit) unless you are running on a ppc processor.

---

### Post by waydaws on 2006-09-04
This is a bit off-topic, but I'm curious about the use of aptitude instead of apt-get.  What are it's advantages?

---

### Post by 3rdalbum on 2006-09-05
It keeps track of dependancies pulled in by your programs. So when you install mozilla-thunderbird through aptitude, it keeps track of which dependancies it has pulled in. If you decide to use aptitude to uninstall mozilla-thunderbird, aptitude checks if its dependancies are in use by anything else, and if not it also removes them.

Apt-get doesn't do that stuff.

---

### Post by sakathor on 2006-09-19
thx for the guide, excellent work. Wish I'd found it earlier ;)

---

### Post by FyreBrand on 2006-09-19
Ubuntu Demon, it's a very nice guide.  I like that it's precise and thorough.

I would like to mention that Google offers a debian repository for Picasa.  I have tried F-Spot and digiKam, but like Picasa.  I thought I would share that repository for those who choose to use this application.  I don't know if it rates being in your guide, but it's nicer than installing locally.

```
# Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free
```

---

### Post by ubuntu_demon on 2006-09-22
> **FyreBrand said:**
> Ubuntu Demon, it's a very nice guide.  I like that it's precise and thorough.

I would like to mention that Google offers a debian repository for Picasa.  I have tried F-Spot and digiKam, but like Picasa.  I thought I would share that repository for those who choose to use this application.  I don't know if it rates being in your guide, but it's nicer than installing locally.

```
# Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free
```
thanks for the suggestion. I don't think I will include it (because f-spot is nice and improving) but maybe if multiple people request it.

keep the suggestions coming! :)

---

### Post by dolphinsonar on 2006-10-05
Is there a free software alternative to JAVA?  Sun makes OpenOffice, so they can't be all bad, but I am trying to be an Ubuntu fundamentalist here...

---

### Post by ubuntu_demon on 2006-10-07
> **dolphinsonar said:**
> Is there a free software alternative to JAVA?  Sun makes OpenOffice, so they can't be all bad, but I am trying to be an Ubuntu fundamentalist here...
GIJ
GNU Interpreter for Java
[http://en.wikipedia.org/wiki/GNU_Interpreter_for_Java](http://en.wikipedia.org/wiki/GNU_Interpreter_for_Java)

gij is Ubuntu's java default and it sits in the package 'gij'. Here's how to set what's used :
$sudo update-alternatives --config java

if you want to compile java :

GCJ
GNU Compiler for Java
[http://en.wikipedia.org/wiki/Gcj](http://en.wikipedia.org/wiki/Gcj)

---

### Post by jcrnan on 2006-10-08
I think the guide is very good. I always use it for quick reference for setting up pc's after a fresh ubuntu install. But do you plan on updating it for edgy?

---

### Post by ubuntu_demon on 2006-10-09
> **jcrnan said:**
> I think the guide is very good. I always use it for quick reference for setting up pc's after a fresh ubuntu install. But do you plan on updating it for edgy?
Yeah I plan on writing one for Edgy around Edgy's release.

---

### Post by FyreBrand on 2006-10-09
> **ubuntu_demon said:**
> Yeah I plan on writing one for Edgy around Edgy's release.
Thanks.  I use your list as well.  It's quite nice and I can just go down the list so I don't forget anything.  I guess I could copy it to a file and use the list that way but I like to check it in case there are any changes.

---

