---
title: "My Strategy With Ubuntu Going Forward"
date: 2020-06-10
forum: Ubuntu, Linux and OS Chat
---

### Post by atrab101 on 2020-06-10
I decided to write this after reading the "Any other OS" by jwn-2 closed thread.

I apologize if commenting on a closed thread violates protocols (kill if needed), but I do understand the OP's concern in that thread.  I developed a solution that works very well for me, and should give me many more years of stable computing, without having to ditch my history with computers and become a captive balloon to the winds of change.

Over 4 years ago in early 2016, I had a 14 year old Windows XP system that died.  What to do?  I decided to build a system with newer hardware, which were the last versions that still supported XP.  I restored my XP image with Acronis to the new hardware (Asus M5A97 Rev2, AMD FX8300, Radeon HD7750, 8MB 1866DDR3 HyperX).  It was important that I retain many legacy applications, as I was not interested in a lot of new Windows stuff, already being in retirement.  All worked great.  I also bought spare hardware, so I could support Windows XP as a frozen configuration for many years.

Realizing that XP would not be safe on the Internet going forward, I had planned to dual boot with Ubuntu after doing research on hardware compatibility.  I installed Ubuntu 14.04 and everything worked perfectly.  I later upgraded to Ubuntu 16.04, and that was completely problem free.  I had followed the advice of sticking with software in the Ubuntu repositories.  I have now had Ubuntu installed for over 4 years, use it every day, and have not had a single incident where I had to do a hard restart in all that time.  I upgraded to a SSD from HDD using a Clonezilla image about 2 years ago, which really made the system lightning fast.

I may delay upgrading to Ubuntu 18.04 and get Ubuntu Extended Maintenance Support for a while with 16.04.  I like Unity and my system does everything I need.  At some point I will try the upgrade after saving a Clonezilla 16.04 image, but I have read that there might be some issues that require tweaking, so if it ain't broke...

I am over 70, so I may be nearing EOL. :)  From what I have read, I am quite sure that 18.04 will support my current hardware, and probably 20.04 will also do so.  If I get to the point that to have a secure version of Ubuntu I must upgrade my hardware, I can get a new system for Internet use and just use this Desktop for Windows XP applications and no Internet.

I love Ubuntu.  It has been flawless for over 4 years so far.  The very best decision I ever made in my history with computers was building the system I am now using and installing Ubuntu as my primary OS, retaining XP for lots of legacy applications.  If I had gone the Windows 10 route, I might have had my daughter's experience.  A windows 10 mandatory update during the Spectre/Meltdown fiasco, turned her AMD system into a brick.  Impossible to boot and the disk could not be accessed by Windows 10 for any repair attempt.  I took her HDD home, installed it in my system and then did a disk repair with my vintage 2005 Norton Disk Doctor in XP.  After it fixed everything on a 200 page error report her data was saved and accessible!  Her data was then installed on a new system which she decided to buy.  She does backups now.

Thank you, Ubuntu! :D

---

### Post by mastablasta on 2020-06-10
if winxp applications are not heavy GPU applications (games...) you can run it in virtualbox. same goes with older linux version (if they would be needed). snap packages will also remove the need for that (eventually).

i am still on now 15 year old winXP machine, but me personally haven't booted windowsxp since january 2019. my kid played a few games on it, but after he bought his own PC and after i installed the games in Linux using Wine he uses linux exclusively. 

he likes to game (1 hour a day is the limit) on his new PC. and it's interesting to hear him comment about win 10 and the view. he wanted osme new games, but was upset as they work on his PC but would only work well in win10. i told him save up the money, buy windows 10 and you can play all games. he said "no, i don't like windows 10. they are slower (he saw them on my PC), they have long updates and they force updates that might not work on your PC. i will stay with Kubuntu, i am just upset they don't make more games for Linux."  he is 8 yo.

software and hardware (external devices) support for linux (overall) is not ideal, but it is better than it was. especially as more manufacturers turn to FOSS.

---

### Post by grahammechanical on 2020-06-10
Please keep in mind that Ubuntu is not only Ubuntu. There are official flavours built on Ubuntu that use less resources than Ubuntu does with Gnome shell as the desktop user interface. Investigate Lubuntu and Xubuntu. This forum has been recommending those flavours for Windows XP machines for many years. If I had not upgraded my machine from 1GB RAM to 4GB I think I would have had to switch to Lubuntu or Xubuntu.

Regards

---

### Post by mastablasta on 2020-06-11
while others are lighter they do not have long support options (3 years max.) compared to Ubuntu (5 years). though i am still not sure it would actually be a major security risk if you used Lubuntu after 4 years.

---

### Post by atrab101 on 2020-06-11
I see that my original post incorrectly said 8MB of 1866 HyperX RAM instead of 8GB.  In my purchase of spares for this system I have 16GB 1866DDR3 to use in future as needed, and I also have a more powerful XP compatible video card to upgrade with in the future.  My AMD FX-8300 processor really has no significant upgrade potential but is very much more than adequate for my needs.  I don't do games, but I do some video editing for which it performs well.

I don't know much about Virtual Box or WINE, but it seems that just having an image of my old XP system that I can boot whenever I want is probably best for me.  I do have Windows on a separate drive and GRUB for access.  I have thought that having separate drives for Ubuntu and Windows probably avoids potential problems.  Windows XP had some free built-in video editing tools that were stripped out of later versions, such as Windows Movie Maker.  It wouldn't do for current HD video, but my video library consists mostly of older VHS and Digital8 raw video that I have moved off tape to the PC with the Windows tools.  Now I am editing and organizing, so my children can have all these memories for the future.  I really wonder if Virtual Box or WINE would be effective for this kind of effort.  I also have some financial programs (such as Quicken) that have a lot of history and forecasts that are fairly complex.  Would these work?  I think the transfer of the data to new programs in Linux would be problematic, and that is another reason I wanted to keep my Windows XP around.

I am glad that Ubuntu has other flavours such as Lubuntu and Xubuntu.  This gives much more flexibility than the Windows world.  If I do get to the point where my system is strained, it is good to have options such as these.  I probably will continue use versions with the longest available support for now.  I have seen that the Gnome Shell in 18.04 and 20.04 seems to give some people problems as do SNAP packages, in terms of slowing their system down and storage space requirements.  There seems to be a lot of debate on these subjects!

I have been impressed with the available software in Ubuntu.  I use many of these programs and have found them to be free of problems.  Stellarium (astronomy) is a great one, as is Aeskulap Viewer (for medical studies such as MRI).  I couldn't find a free viewer for medical studies that was any good in Windows.

I really loved the comments from the 8 year old budding computer wizard.:D   I have several grandchildren, and I am amazed by the things they say sometimes.  We older folks often over-complicate things, rather than get to the heart of the matter quickly.

Regards

---

### Post by mastablasta on 2020-06-12
> **atrab101 said:**
> 
I don't know much about Virtual Box or WINE, but it seems that just having an image of my old XP system that I can boot whenever I want is probably best for me.  I do have Windows on a separate drive and GRUB for access.  I have thought that having separate drives for Ubuntu and Windows probably avoids potential problems.  Windows XP had some free built-in video editing tools that were stripped out of later versions, such as Windows Movie Maker.  It wouldn't do for current HD video, but my video library consists mostly of older VHS and Digital8 raw video that I have moved off tape to the PC with the Windows tools.  Now I am editing and organizing, so my children can have all these memories for the future.  I really wonder if Virtual Box or WINE would be effective for this kind of effort.  I also have some financial programs (such as Quicken) that have a lot of history and forecasts that are fairly complex.  Would these work?  I think the transfer of the data to new programs in Linux would be problematic, and that is another reason I wanted to keep my Windows XP around.


**wine**
i use Play on linux to install in Wine as it has a nice GUI and works quite well. it's a compatibility layer. it basically adds windows libraries so you can run windows applications in linux. not all work. 

Quicken seems to work on Wine. you can check which software works in the wine application database (gold and platinum rating work with little to no effort) : [https://appdb.winehq.org/objectManager.php?sClass=application&iId=107](https://appdb.winehq.org/objectManager.php?sClass=application&iId=107)

Quicken is used to file for taxes right? if you are using it to track personal finances, there are a few others that do that such as Skrooge, Kmymoney, (these two work best in KDE dekstop), Gnucash, HomeBank (these two work best in Gnome desktop). I am not sure how these ones can do taxes. i never explored that. we (as persons) don't file taxes here. we just get calculations from government, and then file any compliant to calculation via their website. a few years ago they started supporting linux, so i can file "complaint" from there. companies use acocuntants which have special software that also often works on linux.

**virtualbox** on the other hand virtualizes the whole computer. so you would create a virtual PC (assign GPU, CPU , RAM and disk to it) and then install full OS to it. it works very well for applications that are not GPU intensive, such as quicken. but does not work so good for video editing or gaming. though some GPUs can be used directly i believe. this is very old tutorial for installing ubuntu in virtualbox: [https://www.psychocats.net/ubuntu/virtualbox](https://www.psychocats.net/ubuntu/virtualbox)  
i still find it helpful. the idea is the same and windows installs in similar way.

as for video editing, linux has good native software. there is professional grade Blender, but it is a bit too complex for me. Professional software Davinci Resolve also works. 
but there are easier ones for us amateurs such as for example Openshot, Cinelerra, Kdenlive, Flowblade, VidCutter, Shotcut....

I tried a few and found Shotcut to be relatively easy to use just for some light video editing (cutting video, adding music), though some think it has too many features. i use Kubuntu and Kdenlive is also nice option for KDE desktop. but for Ubuntu maybe Openshot would be better choice or the simple Flowblade. all will work though, they just might add dependencies when instalinng them. not much of an issue if you have enough disk space.

For video transcoding (changing formats, compressing videos etc.) handbrake will do the job very well and is easy to use.

**backup, backup, backup**
finally don't forget about backup when you do the edits as well as later when you are done. digital formats need different versions of backup and on different places (hardware and if possible on different location). 

rdiff-backup is command line tool that will make version backups. there is also rsync.

if you want something with GUI there are a couple to choose (backintime, kabackup, dejadup, duplicati...). after checking a few i went with Areca.

if you just need versioning (for example so you can jump back to previous version of file after failed editing) then there are also file systems available that will make snapshots such as btrfs and zfs. just so many options in opensource world these days...


i can say with confidence that unless you need specific gaming software or other GPU intensive software you don't actually need Windows installed in dualboot mode. virtualbox (or similar virtualisation software like wmware...) will do the job, can make snapshots, and with good machine you won't have to wait long for OS in virtualbox to boot. you can alt+tab to windows and back to linux or if oyu have two monitors you can have windows on one, linux on the other. so there is no need to hold on to old hardware. well unless if it works well enough for you. it does for me, that's why i am also still on the windows XP box but use the linux disk only. it takes linux 45 secs to boot, widnows xp on same box takes about 10 mins.

---

### Post by atrab101 on 2020-06-14
> **mastablasta said:**
> **wine**

i can say with confidence that unless you need specific gaming software or other GPU intensive software you don't actually need Windows installed in dualboot mode. virtualbox (or similar virtualisation software like wmware...) will do the job, can make snapshots, and with good machine you won't have to wait long for OS in virtualbox to boot. you can alt+tab to windows and back to linux or if oyu have two monitors you can have windows on one, linux on the other. so there is no need to hold on to old hardware. well unless if it works well enough for you. it does for me, that's why i am also still on the windows XP box but use the linux disk only. it takes linux 45 secs to boot, widnows xp on same box takes about 10 mins.

Great news for Ubuntu users with legacy Windows applications they want to continue to use!  I spent a little time reading about both Wine and Virtual Box.  I note that the Synaptic Package Manager has both of these.  Is the best way to install to simply get them from there?  I presume that I would be assured that the version would be supported by Ubuntu 16.04.6 LTS which I am now using.  

I see that my Quicken 2006 Deluxe gets a gold grade with Wine.  So that looks pretty good.  I have other programs such as Qimage (photo editing) and Chessmaster 9000 (released for Windows 98/ME but compatible with XP) and also others that I like, which might not have wide enough use for evaluation with Wine, but I could give them a try.  

Virtual Box looks very interesting.  I see that I would need to install Windows XP to the Virtual Box.  It looks like I could not just use an image of my current XP system, but I would need to install from my original media.  In my case that started with Windows 3.1 on 3.5" Floppy, with upgrades through Windows XP Service Pack 1 DVD from 2002.  On-line updates (no longer available) took me to Service Pack 3.  Unless there is another way to install the final version of XP, this would be a non-starter I think.  So maybe for me it would be best to just experiment with Wine.

You mentioned tax software.  Boxed software for Windows XP in the U.S. has not been supported for several years.  I also could not find any that supported Linux.  What I have found is that a company called TaxAct supports Linux very well with their on-line version of tax software.  They don't show Linux support on their website, but when I contacted their technical support they said it should work.  I have been using in for several years with Ubuntu and Firefox and absolutely no problems.

Again I say thank you to the developers of Ubuntu and to all who provide such great support on Ubuntu forums.  My switch to Ubuntu over 4 years ago provided a path for me move forward after my XP system died.  I have found the experience to be user-friendly and I have learned a lot.  I also feel that I have much better control of my computer life than I did with Windows and far less annoying technical issues to resolve (none so far!).  For me, Ubuntu and all the applications I have installed in it have just worked.  I love that!

Regards

---

### Post by mastablasta on 2020-06-15
> **atrab101 said:**
> Great news for Ubuntu users with legacy Windows applications they want to continue to use!  I spent a little time reading about both Wine and Virtual Box.  I note that the Synaptic Package Manager has both of these.  Is the best way to install to simply get them from there?  I presume that I would be assured that the version would be supported by Ubuntu 16.04.6 LTS which I am now using.  

yes, installing from repositories works well. like i said i use play onlinux because it is easier to switch between older and newer wine versions. this can be done through command line as well, btu i just think that having a descent GUI sometimes reduces the time spent learning commands.

for very new software you will need to install some developer/beta version of wine. but older stuff usually works fine with what is in the repositories.

> 
Virtual Box looks very interesting.  I see that I would need to install Windows XP to the Virtual Box.  It looks like I could not just use an image of my current XP system, but I would need to install from my original media.  In my case that started with Windows 3.1 on 3.5" Floppy, with upgrades through Windows XP Service Pack 1 DVD from 2002.  On-line updates (no longer available) took me to Service Pack 3.  Unless there is another way to install the final version of XP, this would be a non-starter I think.  So maybe for me it would be best to just experiment with Wine.


yes you would need to install it. you would need to get an iso somehow. there are copies of the iso on internet. some are genuine, some have issues. anyway if you could get a genuine one then all you would need to do is activate it with your number. they don't really complicate with XP anymore. before you changed the hardware you might got a warning or something, but that is no longer the case. there are also so called black additions out there - user modified editions with all the extra stuff removed that people then use in virtualbox. again since they are modified they carry a certain security risk. 

by the way if you have upgrade CD/DVD it offers full install. because upgrade in windows means "overwrite all system files, leave the old files if they are different, leave certain settings". so the upgrade DVD/CD would have the whole OS on it.
it's the same process if you would install ubuntu to your current disk and then say do not format the drive. then all files get overwritten. any extra files are left there (as well as those in the home folder which hold many app settings).

service packs and updates can still be downloaded (manually).

---

