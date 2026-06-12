---
title: "New to Linux - Ubuntu is a Wonderful Thing"
date: 2016-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by atrab101 on 2016-04-10
Not sure if this is where I should post this, But I just had to say something about my experience!

I am new to Linux and recently built a dual boot desktop system with Ubuntu 14.04.4 and Windows XP.  I had about 14 years of history on that XP system which finally failed, so needed to retain access to that data and many associated programs.  I just have to say how thankful I am to the Ubuntu developers...not one problem!  I downloaded the ISO image and burned the DVD, then began the installation.  Frankly, I expected to likely have some problems with something so new to me, but the installation was flawless.  All necessary drivers loaded without incident, and I was using Ubuntu in just a few minutes.  The system was up and running well without any proprietary software.  AMAZING!  My AMD Radeon video card was fully supported with hardware acceleration, with the drivers furnished in Ubuntu.  The only drivers I had to manually install were for my Epson printer and scanner.  Linux drivers were available and they are just as full-featured as my XP drivers and work flawlessly.   

 

 I have UEFI BIOS, and there were no problems with that.  I have separate hard drives for XP and Ubuntu, and had disconnected my XP drive during the Ubuntu installation just in case there might be a problem that could affect my XP drive.  After the successful Ubuntu installation I reconnected the XP drive, and after another boot cycle found that Ubuntu then automatically installed GRUB 2.0 on its own for OS selection at boot.  It is not possible that this could have been a better experience.  After nearly 2 months I have had no issues or problems with the system.  No system hangs or BSODS.  Any new installation of any Windows version I have had in the past was definitely not this trouble-free.  There is an incredibly large number of programs available.  All the ones I have installed thus far are free, including two marvelous astronomy programs that are every bit as good as the astronomy program I have for XP (that was not free).  I have really only begun to explore what's available. Kudos, much kudos and more kudos to the developers and the community that supports them!  
 

 I did do some research in advance to pick system components that would likely work well with both XP 32 bit and Ubuntu 64 bit systems.  The XP side of things for me did limit the selection to motherboards and video cards that are backward compatible.  I would like to give the list of the most critical compatible components that I used, in case there are other persons out there that seek to preserve their many years of XP or other Windows version history, while also installing a great new OS that will serve them well for the future (no more Windows versions!).  Of course this list is also fine for a new Ubuntu system without a dual boot configuration with XP (from what I have read, there is a very wide range of Linux-compatible components, indeed).  I think it would be unusual to encounter a component that was not compatible.
 

 For my dual boot XP/Ubuntu system:
 Motherboard – ASUS M5A97 R2.0
 Processor – AMD FX-4300
 Video – VisionTek Radeon 4650 PCIe

 Also used WD Black 1 TB Disk Drive, Vantec PCIe 800/400 Firewire, 8GB Kingston Hyper-X memory and LG Super-Multi DVD writer - no problems.

---

### Post by grahammechanical on 2016-04-11
> I did do some research in advance

That is one reason for you good experience. That and the good efforts of the developers of Ubuntu and other components of the Ubuntu distribution.

> Ubuntu then automatically installed GRUB 2.0 on its own for OS selection at boot.

There must have been an update either to the Linux kernel or to Grub forcing a rebuild of the Grub configuration files. You could have brought this about yourself. After re-installing the XP drive you can then open a terminal and run

```
sudo update-grub
```

You will then get a Grub boot menu showing Windows XP as a boot option. Something to keep in mind for the future, perhaps. I am also guessing that you installed Ubuntu in BIOS mode & not EFI mode. Otherwise things would not have been so simple when re-connecting the XP drive as XP would not have been installed in EFI mode. So, if you want Windows 10 in a separate drive you may need to do some more research as Windows 10 will need to be installed in EFI mode.

Regards

---

### Post by atrab101 on 2016-04-12
"There must have been an update either to the Linux kernel or to Grub forcing a rebuild of the Grub configuration files." 

                        That makes perfect sense.  I did do a number of updates that I had deferred when initially installing Ubuntu.  It's good to understand how that happened, and thanks for the info on the command to use if I ever want to rebuild GRUB on purpose!  I have much to learn about Ubuntu and am looking forward to that.
  
"I am also guessing that you installed Ubuntu in BIOS mode & not EFI mode." 

                        A bit puzzling.  My advance research did show that there could be problems with the UEFI BIOS, but I decided to just try the installation and see how it would go.  I had first built the system.  Then I  installed my XP backup image using Acronis Universal Restore, which allowed me to restore my XP partition (first created on the ancient system built in 2002 that failed) to completely new and different hardware.  I just had to have drivers for the new hardware available on a thumb drive and point to that device, as Acronis does not install the original drivers in the image when tn the Universal Restore mode.  I did set the disk drives to IDE Mode in the UEFI.  Otherwise, I would have had to “start over” and reinstall the OS and all my programs in XP.  I don't think SATA had been invented when I built that system!  My new SATA drives test pretty fast, although I understand that I don't get NCQ which some comments from my research said would not be much benefit on a home desktop system.  I used the system for a few days, with UEFI and very stable.  Then I disconnected the XP drive, made no UEFI changes and proceeded with the Ubuntu installation.  After reconnecting the XP drive, it now all works great whether booting Ubuntu or XP, with the UEFI, and with no problems encountered so far.  I have liked the look and features of UEFI.  Maybe I am a bit lucky or perhaps it's due to the particular UEFI version that ASUS selected for my motherboard.  Any further thoughts on what happened here?
  Best regards and thanks for responding to my first post ever on any forum!

---

### Post by ventrical on 2016-04-14
Great to have you aboard. ;)

I have helped a lot of people recover  files from obsoleted Windows XP installs using  Ubuntu. It is really an amazingly efficient program. I like how you re-installed the XP image to the new system. Awesome.

regards..

---

### Post by atrab101 on 2016-04-15
It is great to be aboard.  Thanks.  I really was glad that a way was found to continue with a viable XP drive on the new system, so I could continue to use programs that I previously purchased.  That was a fair investment over time.  Smooth sailing ahead with Ubuntu.  The latest positive experience was a new web cam purchased to conference with my far-flung family.  Works perfectly, no proprietary driver required.  I have been imaging my Ubuntu drive, in case I do something stupid and blow up my partition.  I know I will experiment with new things.  Did a trial restore and worked perfectly.  No need to purchase any software for that task, as had been my windows experience.  :)

Regards

---

### Post by atrab101 on 2016-04-20
I decided to check out the UEFI BIOS issue as relates to my newly built system.  Comments I received and further research led me to the following observations and conclusions:
 
 1) The only interface that I have seen on my system is the UEFI with graphics and mouse control, with all of its features as described in the ASUS motherboard manual.  I like the interface very much.  It has lots of selections for configuring and tuning the system, over-clocking (although I don't do that), etc.
 
 2) My boot menu page in advanced mode has three BIOS settings: a) BIOS for older OS only, b) *both* UEFI and BIOS for older OS and c) UEFI only.  The first time I looked at mine it was already set to the “both” mode.  I presume they do it that way to allow the system to detect a disk with either MBR or GPT and make the appropriate selection.  It is possible that this mode was determined when I selected IDE mode for my hard drives elsewhere in the configuration options, in order to allow my new SATA drive to work with my WinXP image without having to reinstall Windows XP.  I had always had IDE drives in WinXP, right up to the point of my recent system failure.
 
 3) In my case I restored a WinXP disk image with MBR, so it follows that this drive must be booting with the older standard BIOS.  I understand that Win XP (always MBR) cannot work with UEFI.
 
 4) I think it certain that my Ubuntu installation is also the older standard BIOS.  The Ubuntu drive is MBR, although I don't recall making any choice in this regard vs. GPT when I installed Ubuntu 14.04 LTS (but perhaps I did). So I think this may be the the default for Ubuntu also.  If that is true, that is good.  It saved a novice like me from getting into trouble.  So again many thanks to the Ubuntu developers!
 
 I conclude from all this that the UEFI graphics goodies, mouse use and enhanced options that I see are not dependent on being in any specific BIOS mode.  I had originally thought that if you were in a legacy mode with the BIOS, then you would only get the older BIOS standard text based interface.  In my case, I had absolutely not a single problem with setting up my dual boot system, and I am extremely pleased with the way my system works.  I have written this post to insure that my comments on my success when combined with erroneous comments on UEFI didn't mislead anyone.  I think I really have *no experience* with UEFI installation!  I have benefited from the work of others in setting up defaults that worked well for me.  I guess I always have been one to start with defaults and play with options later.  This system meets all my needs now, so I doubt I will need to make significant changes.  If I do, I will be sure to have a recent disk image at the ready!

Regards

---

### Post by Bucky Ball on 2016-04-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Thanks for sharing your experience. It may be of more benefit to others here. 

Enjoy the ride. :)

---

### Post by coldraven on 2016-04-20
Nice story, you really did your homework ! Anyway welcome to the forum, there is lots of good advice here. My last Windows was XP, I moved to Linux rather than use Vista. I kept XP in a virtual machine for a few  years but don't seem to need it any more.

---

### Post by atrab101 on 2016-04-20
I am enjoying the ride a lot!  You get a feeling of freedom that was not there with Windows.   :D

 I have looked many threads on several forums and am extremely impressed with the the support that is available.  Some issues are easily solved and some are complex, but answers do come after enough dialogue to pinpoint issues.   I have also learned some things that will be helpful in the future, such as the best time to upgrade from 14.04 to 16.04.  It's fine to wait awhile.  It seemed with Windows that Microsoft always encouraged you to upgrade fast, even when it was not a good idea.  So far I have experienced great stability and performance with Ubuntu,  installed hardware and all the applications I have tried.  I know I will be able to get answers whenever I need them in the future.  I like the fact that there is sometimes good feedback directly from the terminal to assist you.  I love the ability to cut and paste commands into the terminal (not so in my WinXP).  That really helps at times.

Regards

---

### Post by mastablasta on 2016-04-21
> **atrab101 said:**
>  I love the ability to cut and paste commands into the terminal (not so in my WinXP). 

windows have this option as well. just saying... and not that you need CLI in windows much (unless you're an admin).

edit: I forgot to add that this chip Video &#8211; VisionTek Radeon 4650 PCIe will no longer be supported with AMD drivers from 16.04 onward. you will still have opensource drivers which are 20-30% worse. it is still not known what will happen with older LTS point releases when kernel and such get's updated. but we hope for the best. :)

---

### Post by atrab101 on 2016-04-21
```
windows have this option as well.
```

                        Did not realize that Windows XP had that.  You're right, I never had much need for the CLI.
  
```
VisionTek Radeon 4650 PCIe will no longer be supported with AMD drivers from 16.04 onward.
```

                        Thanks for the info on the Radeon HD4650 PCIe.  I have seen a few posts on the proprietary AMD drivers (or lack thereof) regarding 16.04.  Wasn't sure if it applied to my card and had not investigated yet.  So far I have just used the open-source driver (Gallium 0.4 on AMD RV730) installed by Ubuntu14.04.  It works well for me.  I don't really use games, but it is plenty fast for any video I have come across in my use.  I really like Xscreensaver, and it is plenty fast for anything in there.  I like my system so much that I have planned for a future upgrade already by purchasing a Visiontek Radeon HD 7750 PCIe.  I presume that the same issue will apply to that card.  From what I have read, I think the open-source driver will also be compatible with that card.  Of course I also hope a proprietary AMD driver is available in the future with Ubuntu, in case I do need it for better performance.   It does appear that the 7750 is about as fast a card that I will be able to get and still be compatible with my WinXP drive.  I hope to keep this newly built dual boot system for a long time ...at least 10 years?(made 14 years with the last one), so this advance sparing should avoid some of the scrounging around looking for compatible parts as I did in the past.  I also bought a faster spare processor for the same reason. :)

Regards

---

### Post by mastablasta on 2016-04-22
if you don't game open soruce driver is quite good. actually it is also good for some games, just not as good as it should/could be. and it affects more things on laptops where energy and fan can be an issue. 

I think 6xxx and 7xxx series are going out of support.

I recently bought NVidia GT 730 to replace Radeon 3650 which had a VRAM failure. anyway the GT 730 supports pcie 2.0 and works nicely on Windows XP. the stronger GT740 has PCIe 3.0 support, but also works on XP. I am not sure regarding 750 and higher as they are mostly outside of my price range. the important thing to note here is that they do not use all the features as directx is limited to 9.0c in windows XP. however all directx features under xp work well. they should perform well under Linux as they have closed source drivers available.

One more thing regarding opensource drivers - they do have most features available. some might need to be enabled with extra parameters. you can check what is enabled and what does not work here: [http://www.x.org/wiki/RadeonFeature/](http://www.x.org/wiki/RadeonFeature/)


I wish I could have gone with AMD, but the R series has bad backwards OS and hardware compatibility and I was out of money to replace the whole thing (motherboard, CPU, ram...).

---

### Post by atrab101 on 2016-04-22
```
I think 6xxx and 7xxx series are going out of support.
```
You are right about the 6xxx and 7xxx.  I did find something about that on the AMD web site.  This from AMD on Nov 23, 2015:  

 “ [COLOR=#000000][FONT=inherit][SIZE=2]AMD Radeon™ HD 8000 Series (HD 8400 and below), Radeon™ HD 7000 Series (HD 7600 and below), Radeon™ HD 6000 Series, and Radeon™ HD 5000 Series Graphics products have been moved to a legacy support model and no additional driver releases are planned. This change enables us to dedicate valuable engineering resources to developing new features and enhancements for graphics products based on the [/SIZE][/FONT][/COLOR][[COLOR=#000000][FONT=arial]GCN Architecture[/FONT][/COLOR]]("https://community.amd.com/external-link.jspa?url=http%3A%2F%2Fwww.amd.com%2Fen-us%2Finnovations%2Fsoftware-technologies%2Fgcn")[COLOR=#000000][FONT=inherit][SIZE=2].”[/SIZE][/FONT][/COLOR]
 
 [COLOR=#000000][FONT=inherit][SIZE=2]It looks like my [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]VisionTek [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]HD7750 I bought for a future upgrade is not [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]going out of support[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2], as it has the G[FONT=inherit]CN[/FONT] architecture.  I [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]am sure[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2] that future [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]AMD [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]support for this card will [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]not [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]include WinXP.  [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]Visiontek provided a WinXP driver, so I should be OK there.  For Ubuntu I hope I will also be OK, as AMD should be including support with the new Linux driver that they are supposed to be working on.  In any event, as long as an opensource driver is available in the future, my needs should be met.  I think (hope) that will be the case.[/SIZE][/FONT][/COLOR]

```
One more thing regarding opensource drivers - they do have most features available.
``` [URL="http://www.x.org/wiki/RadeonFeature/"]
[/URL][COLOR=#000000][FONT=inherit][SIZE=2]T[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]hanks for the link info on the features available on the opensource drivers.  I will be studying that a bit...a lot of good information!  It looks like the 7750 is Cape Verde and GCN 1.0.  [/SIZE][/FONT][/COLOR] 
 
 [COLOR=#000000][FONT=inherit][SIZE=2]By the way I also have a Radeon HD3650  [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]Mine is an AGP version[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2].  It gave me many years of service in my WinXP computer that recently failed.  [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=inherit][SIZE=2]That was a rock solid card.  It was EOL for me when I finally moved past AGP with my new dual boot system! :( :)[/SIZE][/FONT][/COLOR]

Regards

---

### Post by coldraven on 2016-04-26
> such as the best time to upgrade from 14.04 to 16.04.  It's fine to wait awhile.  I
Yes, I'm using 15.10 but I will wait a month before I install 16.04. That way any unexpected problems will have been solved.
P.S. You are using the CODE # tag for quotes, the  Quotes tag looks like a tiny speech bubble. (the far right one in the quick reply bar)

---

### Post by atrab101 on 2016-04-26
>  the  Quotes tag looks like a tiny speech bubble. (the far right one in the quick reply bar) 

Thanks for the info.  I wondered how to do that.  And how do you incorporate the line above in the box with red quote mark in front, statement Originally Posted by.... and link to original post?  I am a real novice to forums (as well as Linux)!  I may wait quite a while to upgrade to 16.04.  I saw someone say to wait for the first point release.  Is that best?

Regards

---

### Post by Bucky Ball on 2016-04-26
[quote=atrab101] starts the quote ...

Copy weblink, highlight text, click HTML tag icon, paste weblink, 'ok' ...

But this is drifting and off-topic. If you want any more advice with this, please post a new thread as this is a non-support thread in a non-support forum area. Thanks.

---

### Post by atrab101 on 2016-04-27
> ...please post a new thread as this is a non-support thread in a non-support forum area. 

Will look further at FAQs and post a new thread if necessary (thanks for pointing me that direction).  

Getting back to general philosophy for upgrading, my 14.04 is working great, so I am inclined to perhaps wait quite awhile.  I have generally done upgrades in the past rather than clean installs, as I don't like starting over.  Is it necessary to upgrade in sequence to the next LTS release, or could you wait and upgrade from 14.04 to 18.04 when that is released?  Or would skipping a release kill the upgrade option?  If 14.04 continues to meet all my needs with great stability, I might consider waiting that long.  It's been almost three months since I installed 14.04, and I am amazed with the user interface, functionality and stability.  Not a single issue so far.  No screen freeze, BSOD or unexpected reboot issues at all. :)  I never had a Windows version without some type of issue early on, although I always had good stability after some tweaking.

Regards

---

### Post by coldraven on 2016-05-01
> I have generally done upgrades in the past rather than clean installs, as I don't like starting over
I'm the opposite, I like a clean install. I don't have many extra programs installed so it's not a hassle.

If 14.04 is working for you then just carry on using it
For possible future use you might like to research the following technique and, as always, do a backup of your important stuff.
If you have your /home folder on a separate partition you can do an install and select "Do not format this partition" and "Use this partition as /home". So the new system is installed at root (/) and your home stays unchanged. You would have to re-install any programs but their settings should all be in your home folder.

> could you wait and upgrade from 14.04 to 18.04 when that is released?
I don't know, but most likely you would have to go via 16.04, a double upgrade would be a tedious experience.

---

### Post by Bucky Ball on 2016-05-01
> **coldraven said:**
> I don't know, but most likely you would have to go via 16.04, a double upgrade would be a tedious experience.

Probably this. It has never been possible to upgrade an LTS by leapfrogging the next LTS to the one after that. Don't see that changing.

---

### Post by deadflowr on 2016-05-01
> **mastablasta said:**
> 
edit: I forgot to add that this chip Video – VisionTek Radeon 4650 PCIe will no longer be supported with AMD drivers from 16.04 onward. you will still have opensource drivers which are 20-30% worse. it is still not known what will happen with older LTS point releases when kernel and such get's updated. but we hope for the best. :)

Actually, Didn't that card lose support four years ago?

I think it's the 5000's and up that lost support with 16.04.

---

### Post by atrab101 on 2016-05-01
> I think it's the 5000's and up that lost support with 16.04.

I believe that is correct.  I am told by 14.04 that no proprietary drivers are available with the Radeon HD 4650 currently installed in my system.  The 4650 meets my current needs as is, but I do like to do upgrades occasionally.  I will probably install a Radeon HD 7750 by the end of the year.  Time will tell if there will be a proprietary driver available.  From what I have read I think (hope) the open source driver in both 14.04 and 16.04 will support the 7750.  That should really be enough for me, in any event.  I am held back in the graphics card arena by the need to maintain hardware compatibility with the Windows XP side of my dual boot system.  It must be an enormous task for software developers to keep track of hardware variations and determine what they can continue to support with any software release.  What a challenge!  I think they do a commendable job.

Regards

---

