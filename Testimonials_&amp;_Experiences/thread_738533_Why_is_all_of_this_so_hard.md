---
title: "Why is all of this so hard?"
date: 2008-03-28
forum: Testimonials &amp; Experiences
---

### Post by mj52730 on 2008-03-28
Hi all. I hate to come off like a downer on Ubuntu, but it is frustrating the heck out of me. I recently installed 7.10 on my brand new Toshiba laptop as a 2nd os, partitioned the hard drive & installed it. That is the last easy thing I have been able to do. I cannot figure out an easy way to install wifi drivers, I can't play mpgs or mp3s ect. I am very new to this & I know I'll get heckled in here by some of the same pretentious "Linux is the 2nd coming of Christ"  posters that I've seen on other boards, but I need to know basically, why installing this software & drivers for this OS has to be so stinkin'  HARD?? Why can't a person just download a file & install it? Why all of the Terminal & command line B.S.? Microsoft is more popular because frankly it's about 1000 times easier to use. I know they also have about a million times more development money too, but c'mon.  I have tried other linux distros & livecd's  and found (& have heard)  that Ubuntu is the easiest to use, but it is still WAY too difficult to install software & drivers & codecs. Maybe I am too much of a noob to figure out the easy way to do things with this OS, but I was looking for an alternative to crappy MS Windows & I just can't seem to figure this stuff out. In my opinion, Linux OS's will never be viable competition to Microsoft or Apple until someone simplifies how to use it. Or maybe they don't want to be....?

---

### Post by ad_267 on 2008-03-28
Linux is not Microsoft, things work differently. Personally I find synaptic package manager a far easier way of installing software. You will get it eventually, but it does take a short while to get used to the differences. I recommend sticking with it though, it's definitely worth it.

For mp3s and things like flash you need the package ubuntu-restricted-extras and may have to enable the universe and multiverse repositories in synaptic. These codecs cannot be included in the ubuntu installation for legal reasons. Have a look here for more info: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As for the command line stuff, most things in Ubuntu don't require the command line at all, but a lot of people find it easier and faster so a lot of help given in the forums asks people to use the command line and type in one line, rather than a lengthy explanation of click here then here then here etc.

I don't have any experience with wifi but someone else might help you if you start a post with a more relevant title like "cannot find wifi drivers"

---

### Post by saj0577 on 2008-03-28
Some of your points are correct, and others are purely opinion. As for the installing of drivers, this is all getting easier with each update and release, we need people like you to report your problems so we can try to fix them because you cant fix a problem you dont know exsists.

So if you want to tell us which software and drivers are not working we will be happy to help.

Saj

---

### Post by spydon on 2008-03-28
> Microsoft is more popular because frankly it's about 1000 times easier to use.
Yes, but ony if you have used it your whole life...

What brand is your wifi card? Is it a broadcom maybe?

---

### Post by Talon2 on 2008-03-28
It is just a matter of you getting used to it.

Give yourself a month or two.

The best way to get used to Ubuntu is to ask specific questions about specific things you want to do.

Tell us what your most important issue is right now.  Be specific.

:)

---

### Post by mj52730 on 2008-03-28
Oh please, don't misunderstand, I thing this Ubuntu is Really cool, & you're right, if a persons been using MS their entire life, is does seem easier. I was just ranting, been a long day messin with this. Actually my wifi is a built-in Realtek rt8187b. I also have no idea what you are talking about when you say

*For mp3s and things like flash you need the package ubuntu-restricted-extras and may have to enable the universe and multiverse repositories in synaptic.*

I'm just trying to learn something new, that's all.

---

### Post by bhold on 2008-03-28
Mint is an ubuntu-based distribution with most necessary media codecs pre-installed so mint might be a good distribution for you to try. I'm running it now on one of my 3 linux partitions and yes, more stuff did work right out of the box with mint. Ubuntu does not pre-install some codecs, I think due to free software licensing issues but am not 100% sure why.

[http://www.linuxmint.com/index.php](http://www.linuxmint.com/index.php)

Good luck

---

### Post by ad_267 on 2008-03-28
Ok to install the package ubuntu-restricted extras:

Click on System  - Administration - Synaptic Package Manager

Click on Settings - Repositories

Tick next to the universe, restricted and multiverse options (these might already be enabled, I'm not sure)

Close that window then click on Reload in synaptic

Click on search and search for ubuntu-restricted-extras

click the box next to ubuntu-restricted-extras

And click apply

---

### Post by ad_267 on 2008-03-28
The upcoming Hardy Heron release due on April 24 is supposed to have a lot better support for wireless, you could try using the beta release and see if your wireless works in that.

---

### Post by kwacka on 2008-03-28
First Linux isn't Windows, if you want windows stick with it. The analogy I've read is comparing a car and a motorcycle - if you want to take the family out use a car; if you want to get from a-b without getting held up in traffic, use a bike.

There's problems with Vista because of the lack of drivers; its the manufacturers fault apparently, but its linux fault if drivers aren't available in linux?

I have to disagree with your comments about the ease of Windows. If you take a standard computer, and install to a clean harddrive, Ubuntu is far easier to install. Inside 45 minutes you can be safely checking emails, websites, printing letters you have typed, using a DTP program and designing flashy buttons for a web page. Installing Windows you won't even have reached your second reboot by then (and you have to add everything else).

I can tell from your tone that you are more used to the Windows forum; they tend to be a lot friendlier here, although nobody owes you anything. If you want to get stroppy over something not working, get on the phone to whoever sold you the item - its their fault that drivers aren't available.

Q1. What wireless card can't you get working? This seems to be the main problem area for many people - lets hope the manufacturers get their act together soon and provide drivers.

Q2. have you installed codecs for MP3, etc? 

Q3. Did you read the sticky at the head of the forum? Which parts are you having problems with?

Have you seen the "idiot's guide" at [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

For your wireless card see: [http://ubuntuforums.org/showpost.php?p=3397386&postcount=13](http://ubuntuforums.org/showpost.php?p=3397386&postcount=13)

---

### Post by mj52730 on 2008-03-28
Thanks ad_267, those instructions worked GREAT! Any suggestions on my wireless card? BTW, did someone move my thread?

---

### Post by unknown03 on 2008-03-28
I'm pretty sure that if Ubuntu was to include those "restricted" drivers then they would be the defendant in a copywrite violation.. Therefore, YOU must install them (assuming you have internet)

It took me a while to figure out how the hell to get my wireless card to work in Gutsy and Hardy.. but this post help me out alot
[http://ubuntuforums.org/showthread.php?t=714304&highlight=WMP54GS]("http://ubuntuforums.org/showthread.php?t=714304&highlight=WMP54GS")

in a nutshell, if your card is based on Bcm43xx chipset, then download the bcm43xx-fwcutter_20060108-6build1_i386.deb (or *amd64.deb) and install it.. and download (wl_apsta-3.130.20.0.o) to your desktop..

Then go to the restricted drivers and enable it, when prompted for the firmware, click browse and point it in the right direction of (wl_apsta-3.130.20.0.o)

Thats how I got it working..

if you have any problems then do a search for your wireless card on the forums, usually youll find an answer 8 times outta 10

---

### Post by abyssius on 2008-03-28
As a recent convert from the Windows world to Linux / Ubuntu I can sympathize with much of what you say. However, I would respectfully take issue with some of your comments. First, I'd like to address your comment "...pretentious "Linux is the 2nd coming of Christ" posters that I've seen on other boards...". One of the most striking things I found upon joining the Ubuntu Forum is the exemplary politeness and patience I've experienced within the support sections of this forum. It seems that you are channeling your experiences with "chat" type forums, which naturally attract characters who enjoy expressing their combative natures online. It simply isn't fair to paint the support forums with that brush without adequate research on your part. I'm confident that if you give this forum a chance, you'll agree with me.

One of the hardest things I found in my migration from Windows was learning the different ways that things are accomplished in Linux. Windows may seem 1000 times easier to use - because that's what you're used to. You've been through the Windows learning curve - and now you feel comfortable enough to accomplish an advanced task like partitioning a hard-drive. You're also aware that there is such a thing as a wifi driver. These are signs that you're way more aware than the vast majority of Windows users already. This also tells me that you're quite capable of learning the Linux techniques required to get your computer working, once you decide to be patient about it. I can also say from personal experience that if you decided to migrate to Macintosh without prior experience, you'd run into hurdles that would make you equally frustrated.

Having said all this, the problems you are experiencing are not unique, nor are they impossible to overcome. My advice as a fellow newbie, is don't think of Linux operations as "stinking hard". They really are not. They are simply different.

If you want to get your wifi working, simply identify what type of hardware you have, and someone will gladly help you through the process. Most of the time all you will have to do is as you put it, "download a file and install it".  You'll probably have to use command line techniques. But, you'll find clear instructions on this forum, and if you don't like typing, you'll simply cut and paste those commands to accomplish what you want to do.

I've been using Ubuntu since January, and now when I load Windows it seems, bulky, awkward and scattered. With Ubuntu, no more VIRUS worries; no more resource-stealing anti-virus/spyware overhead - no more Microsoft intrusion  (dictating to me how I should use my computer or what I can or cannot run on it). I feel liberated. To be honest, every day is a new learning experience but I've never felt as intimate with my computer as I do now. The net result has been mostly positive. I can promise you that the frustrations you feel now will quickly go away, and you'll learn to appreciate this tightly integrated and streamlined operating system. 

BTW, I don't completely agree that Windows "sucks". Windows is probably the most powerful platform in terms of capabilities right now - simply due to the proliferance of available software and compatible hardware. (BTW, I tried running some Windows software using WINE and wasn't sucessful in getting it working as yet).

Final points. If you buy a computer with 100% compatible hardware- and Linux factory-preinstalled, I think you might reconsider the viability of Linux vs. Windows or Apple. Sears and Walmart are selling very reasonable Linux machines right now. The people who buy them are hardly experts, and they're having no problems surfing the Internet and sending emails, capturing photos, etc.  - essentially what 90% of new computer users do. To them, Linux is a turn-key experience. You'll get there also. Give it a chance.

---

### Post by wolfen69 on 2008-03-28
> **bhold said:**
> Mint is an ubuntu-based distribution with most necessary media codecs pre-installed so mint might be a good distribution for you to try. I'm running it now on one of my 3 linux partitions and yes, more stuff did work right out of the box with mint. Ubuntu does not pre-install some codecs, I think due to free software licensing issues but am not 100% sure why.

[http://www.linuxmint.com/index.php](http://www.linuxmint.com/index.php)

Good luck

try LinuxMint. everything works out of the box.(all codecs,flash,java,etc.) it's the easiest distro in my opinion. since it is based on ubuntu, most of what you learn about ubuntu can be applied to Mint.

---

### Post by kool_kat_os on 2008-03-28
> **abyssius said:**
> As a recent convert from the Windows world to Linux / Ubuntu I can sympathize with much of what you say. However, I would respectfully take issue with some of your comments. First, I'd like to address your comment "...pretentious "Linux is the 2nd coming of Christ" posters that I've seen on other boards...". One of the most striking things I found upon joining the Ubuntu Forum is the exemplary politeness and patience I've experienced within the support sections of this forum. It seems that you are channeling your experiences with "chat" type forums, which naturally attract characters who enjoy expressing their combative natures online. It simply isn't fair to paint the support forums with that brush without adequate research on your part. I'm confident that if you give this forum a chance, you'll agree with me.

One of the hardest things I found in my migration from Windows was learning the different ways that things are accomplished in Linux. Windows may seem 1000 times easier to use - because that's what you're used to. You've been through the Windows learning curve - and now you feel comfortable enough to accomplish an advanced task like partitioning a hard-drive. You're also aware that there is such a thing as a wifi driver. These are signs that you're way more aware than the vast majority of Windows users already. This also tells me that you're quite capable of learning the Linux techniques required to get your computer working, once you decide to be patient about it. I can also say from personal experience that if you decided to migrate to Macintosh without prior experience, you'd run into hurdles that would make you equally frustrated.

Having said all this, the problems you are experiencing are not unique, nor are they impossible to overcome. My advice as a fellow newbie, is don't think of Linux operations as "stinking hard". They really are not. They are simply different.

If you want to get your wifi working, simply identify what type of hardware you have, and someone will gladly help you through the process. Most of the time all you will have to do is as you put it, "download a file and install it".  You'll probably have to use command line techniques. But, you'll find clear instructions on this forum, and if you don't like typing, you'll simply cut and paste those commands to accomplish what you want to do.

I've been using Ubuntu since January, and now when I load Windows it seems, bulky, awkward and scattered. With Ubuntu, no more VIRUS worries; no more resource-stealing anti-virus/spyware overhead - no more Microsoft intrusion  (dictating to me how I should use my computer or what I can or cannot run on it). I feel liberated. To be honest, every day is a new learning experience but I've never felt as intimate with my computer as I do now. The net result has been mostly positive. I can promise you that the frustrations you feel now will quickly go away, and you'll learn to appreciate this tightly integrated and streamlined operating system. 

BTW, I don't completely agree that Windows "sucks". Windows is probably the most powerful platform in terms of capabilities right now - simply due to the proliferance of available software and compatible hardware. (BTW, I tried running some Windows software using WINE and wasn't sucessful in getting it working as yet).

Final points. If you buy a computer with 100% compatible hardware- and Linux factory-preinstalled, I think you might reconsider the viability of Linux vs. Windows or Apple. Sears and Walmart are selling very reasonable Linux machines right now. The people who buy them are hardly experts, and they're having no problems surfing the Internet and sending emails, capturing photos, etc.  - essentially what 90% of new computer users do. To them, Linux is a turn-key experience. You'll get there also. Give it a chance.

You type alot....(i mean ALOT :)

---

### Post by abyssius on 2008-03-28
Ha Ha Ha. You're right. I do it for a living, so it seems natural to me. Maybe, that's why I like Linux.  Having to type those weird commands restricts my "flying" fingers big time! :lolflag:

---

### Post by wolfen69 on 2008-03-28
> ...and so castles made of sand fall in the sea - eventually... Jimi Hendrix
nice sig btw. Hendrix and Beatles are 2 of my favs.

---

### Post by DMK62 on 2008-03-28
mj52730 

Most of us get frustrated at times and in a way it can be  part of learning something new. Especially when that something new doesn't want to work at all. Add to that having to try and figure something out that uses terms and language you have never heard of just makes it more difficult. Stick with it and you will be surprised how fast what irritated you now will  be second nature to you down the road.

Linux Mint Main Edition ( Gnome ) is what I would recommend as far as multimedia capability out of the box. It's based off of Ubuntu 7.10 and for the most part it is the same. There are some different tools and programs installed by default however you will have a fully functioning system sooner. It's a good distro to start with for linux. Once you feel comfortable with linux and its way of doing things then you can always try other distros.

If in the future you give other distros like slackware, debian, arch etc you will find out just how much effort the Ubuntu devs put into making things easier for the end user.

Feel free to ask as many questions as you need.

Dale

---

### Post by ElKeBusK on 2008-03-29
Hard?
NO!!!!
Just different :) and from my point of view... better :)

My first experience with Linux was years ago, when KDE and Gnome were just betas and the unique windows like front-end was X11. You cna bet that that was really hard for someone used to windows, but I always liked type commands (my first OS in a PC was a DR-DOS 5.0) so after read a lot Linux manual pages I managed to run the X11 in my debian machine :)
For reasons that are pointless explain here I left Linux aside for several years (about 10?) and I came back to Linux when my sister dropped and Ubuntu Feisty live CD on my desk a few days ago. At first I thought "OMG, again all that man pages and read a lot to learn how to do anything in a Linux machine. NO WAY!" but the CD seemed say: "Try me!". So I did it... and I get shocked when I saw myself right into Gnome desktop and not having to configure ANYTHING since EVERYTHING was recognized from start, even the hardware that is not supported like my onboard soundcard C-Media CM6501 that is fully working with generic alsa drivers for usb sound devices. You cannot say that of any windows version, if a hardware is not supported you won't find a generic driver that will make it work.

True that you've got to learn new ways of do things and sometimes you will ask yourself: "why this is not like in windows", well the answer is simple: because is not windows :)

About your codecs problem, I've installed VCL Media Player athrough synaptic and I can play mp3 divx, xvid, wma, mpeg, ogg..., no problems with multimedia stuff so far :)

---

