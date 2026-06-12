---
title: "Why is it?"
date: 2007-11-05
forum: Testimonials &amp; Experiences
---

### Post by patrickalexson on 2007-11-05
Alright, first off, im used to Windows (a downside to jumping into linux) but heck, most people are too.

First off, I know what im doing, somewhat. Ran into a problem with the graphics not working correctly so I went in to the configuration and changed a bunch of crap and what not. Well unfortuantly still doesnt work, but I cannot give Ubuntu a low rating for that. Im not dumb enough to think that it should be 100% worry free, compatible with my hardware.

The few things I dont like about Ubuntu are this, and yes while it sounds stupid, this really applies probably to everyone.

First off, Macromedia flash doesnt work with my system, not sure why but I have tried alternatives and they DO NOT work, or the ones that do are so glitchy, its not even worth trying. If I can get the ACTUAL macromedia flash for firefox installed, I will be happy.

Second, I never have gotten used to the Terminal Commands. They make sense, yes, but what the heck is this? If I wanted to look like im hacking the CIA every three seconds, I would just use command prompt for the rest of my life. I wish there was an install feature, like the .exe automated install. Also, side note here, why is it that when I install something, I cant just have a freaking shortcut in the main menu or app menu? Why must I be forced to use the Terminal to start it?

---

### Post by Rudi Völler on 2007-11-05
Hi, 

Im not sure what problems you are having with Adobe Flash player, but it is available for Linux and works with Mozilla, Firefox and Seamonkey. See:[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200701/011707FlashPlayerLinux.html]("http://www.adobe.com/aboutadobe/pressroom/pressreleases/200701/011707FlashPlayerLinux.html") and it works perfectly in my Firefox browser. 
For automated install features you use Adept or Synaptic package managers (GUI applications that manage installation / update / removal of your software). 
And applications that I install (running Kubuntu 7.10) appear in my application menu so I dont have to open a terminal to start programs. 

Anyway, good luck with exploring Ubuntu!

---

### Post by patrickalexson on 2007-11-05
Well I was reading somewhere, cant find the link anymore, that Macromedia flash will NOT work with AMD cpus for some odd reason. First, not sure why, but Firefox doesnt even allow me to use the "add on" plugin whatever feature for Mac Flash so...mabey im doing something wrong but I would assume that Firefox works relatively the same way with Windows as it does in Linux, as far as addon/ plugins go for flash.

I go directly to the Mac flash distro site and download the archive file, when I try to install it, this was in 7.04, it tells me that I have the wrong architecture...which is strange but yeah I guess I probably am doing something wrong. Any suggestions?

---

### Post by mdsmedia on 2007-11-05
> **patrickalexson said:**
> Alright, first off, im used to Windows (a downside to jumping into linux) but heck, most people are too.

First off, I know what im doing, somewhat. Ran into a problem with the graphics not working correctly so I went in to the configuration and changed a bunch of crap and what not. Well unfortuantly still doesnt work, but I cannot give Ubuntu a low rating for that. Im not dumb enough to think that it should be 100% worry free, compatible with my hardware.

The few things I dont like about Ubuntu are this, and yes while it sounds stupid, this really applies probably to everyone.

First off, Macromedia flash doesnt work with my system, not sure why but I have tried alternatives and they DO NOT work, or the ones that do are so glitchy, its not even worth trying. If I can get the ACTUAL macromedia flash for firefox installed, I will be happy.

Second, I never have gotten used to the Terminal Commands. They make sense, yes, but what the heck is this? If I wanted to look like im hacking the CIA every three seconds, I would just use command prompt for the rest of my life. I wish there was an install feature, like the .exe automated install. Also, side note here, why is it that when I install something, I cant just have a freaking shortcut in the main menu or app menu? Why must I be forced to use the Terminal to start it?I don't have a problem with Flash in Firefox. I can't remember if it was a plugin, but it's available and works without problem.

Installation is easy using Synaptic or Add/Remove Programs or with apt-get and apptitude or adept in command line. Generally you can find a .deb package to install by double clicking like .exe.

---

### Post by wolfen69 on 2007-11-05
did you install the 32 or 64 bit version of ubuntu? secondly, flash works perfect with AMD cpu's. try this: go to system>administration>software sources, and make sure everything is checked off. next, go to applications>add/remove. from pull down menu, select all available applications. search for "ubuntu restricted extras". install, and you are done. you will have flash/java/and some codecs. have fun.

---

### Post by Rudi Völler on 2007-11-05
First of all, as a general suggestion, I would not go to some website and download a program (the Windows way of doing things) since it is most likely already in the repositories and you can then use Synaptic or Adept to download and install them. Use the Package managers for this stuff. 
Your troubles with Firefox sound strange but have you tried the installation of the Flash player with these instructions: [https://help.ubuntu.com/community/MultimediaApplications]("https://help.ubuntu.com/community/MultimediaApplications") (see chapter 4). 
Hope this helps...

---

### Post by mivo on 2007-11-05
Flash works in Firefox in 64-bit Ubuntu, too (7.10). You just click on "missing plugins" and you are offered the GNU open source version and the Adobe version. Choose one, download, and you are set. No different than in Windows.

If you are new to Ubuntu and Linux in general, I suggest to make use of the software selection in Applications -> Add/Remove...  This gives you access to neatly organized programs that will be downloaded and installed on demand. All of them add their icon to the program files menu. There are thousands more packages, but start small. :) You can also check out [http://www.getdeb.net](http://www.getdeb.net) if you cannot find something in Synaptic.

Video cards can be tricky. Make sure to install the restricted driver for your video card. This will address many issues already (it is like downloading the driver from the maker's web site).

The terminal ... hey, some of us grew up with command lines when we started out. :) I missed it in the fifteen years I used Windows, because it is such a flexible tool! You can get real personal with your computer this way! Many things you can do without it and if you use your computer the way you use it in Windows, you will almost never need it unless you need to fix something. I always have a terminal window open, but really, I think it is optional for the most part.

Welcome to Linux!

---

### Post by gjn on 2007-11-05
Here is the simplest procedure I could find for installing the Adobe Flash Player v9 on Ubuntu Gutsy (7.10) 64 bit edition. This is not applicable to Feisty (7.04) 64 bit. 

I have tested this procedure using a Live CD to ensure no prior configuration would cause steps to be missed. It does not involve user explicit downloading of tar files nor does it involve using a terminal window.

[LIST]
Add additional software package repositories.
Click on System->Administration->Software Sources. In the dialog's first tab (Ubuntu Software) check all sources downloadable from the Internet. 
[/LIST]
[LIST]
Open the Firefox browser. I used the [www.youtube.com](www.youtube.com) site to initiate and test the installation. Click on any video and notice the message claiming you may not have the Flash reader installed. Do not click on any links in the YouTube site. They will lead you to the Adobe site.
[/LIST]
[LIST]
Click on the "Install missing plugins" button on the right of the information bar. A dialog will come up. You will be given a choice between the Adobe player (selected by default) and a GNU open source player.
[/LIST]
[LIST]
Once the installation completes, the FireFox window will refresh and the YouTube video will play.
[/LIST]
The Adobe flash plugin is included in the Ubuntu distribution as a package (flashplugin-nonfree 9.0.48.0.2) in a repository  (multiverse) that is not enabled by default.

In another test, I did download the tar file from the Adobe site and tried to install it. I did get an error claiming that the x86_64 architecture was not supported.

As a rule of thumb, I always look first in the Synaptic Package Manager for the appropriate package. I have tried that as well and it works fine.

---

