---
title: "Why doesn't Ubuntu automatically mount internal hard drives?"
date: 2007-01-08
forum: The Cafe
---

### Post by mr_helm on 2007-01-08
I studied computer science in college and almost ALL of the professors there constantly extolled the virtues of Linux as an os being that it is so stable, reliable, etc. (it helped that the code is open source and we could study the boot sequence).  We did a mass install party one night of Linux and I installed on an old p133 with a dual boot to mswincrud, however I never found the Linux partition to be useful for anything other than playing mahjongg as it didn't even recognize my nic and thus couldn't get online (an offline computer is a sad and useless thing).

Skip to 8 years later and I learn about Ubuntu and its fun little live cd feature and its "linux for humans" ideals and I downloaded and started playing with it.  It worked nicely although a little weirdly doing things like recognizing my scanner but not my printer, (even though they are one machine) and other odd things like that.  It also lets me get online (nice).

Ubuntu even notices when I insert a floppy or a usb flash drive etc. and gives me an icon on the desktop (eerily maclike!!), however i have one question.  Why, why, why, why, why am I still forced to commit what in mswincrud would be a registry hack just to get it to look at my computers hard drives?  The code that i have looked at in the help sections here seems to be the same for all computers, relatively straightforward and uniform.  In fact its the same code I studied 8+ years ago in class.  Why can't this be an automated process by now?

If anyone knows an answer to this question or feels the same reply and share the love.](*,)

---

### Post by abijah on 2007-01-08
Then "Why, why, why, why, why" **don't you write and contribute the code** to automate the said process?

---

### Post by IYY on 2007-01-08
> **abijah said:**
> Then "Why, why, why, why, why" **don't you write and contribute the code** to automate the said process?

This is not exactly the right way to word it, but if you are a computer science major, you should indeed consider helping to solve this problem.

But I agree, the problem is certainly there and I expect it should be solved soon enough.

---

### Post by mr_helm on 2007-01-08
> **abijah said:**
> Then "Why, why, why, why, why" **don't you write and contribute the code** to automate the said process?

Linux hackers/enthusiasts are renowned the world over for being an intolerant, unhelpful lot who can't stand anyone who doesn't know as much as they do about their precious little sideline Operating System, and you sir are no exception.  Thank you for keeping the traditions of your kind alive and well in this "For Humans" version of your project.[-(   Keep this type of thinking up and your OS will remain on the sidelines and mswincrud will continue to dominate and eventually **WIN ALL** (pun intended).

I don't write the code because I am NOT particularly a linux hacker/enthusiast or even a programmer anymore.  I was taught to expect an OS to perform the functions needed to make using a computer possible (the mac has an OS, mswincrud is really more of a file handling system than an OS, and Linux is SUPPOSED to be an OS).  The one main thing I learned as a CS major is that I hate programming and I stand in reverent awe of the people who like it and can do it well (this includes documenting your code so that others can read it and understand it later).  I wouldn't know where to find the controllers for such a thing, what language to write it in, how to compile it, test it, add it to the OS, I don't know any of these things.  I'm just trying to use my computer and i would like to get out from under the mswincrud thumb.

That said I guess maybe this thread should go into a suggestions thread or something, I'll let the moderators decide but if everything else can be auto-mounted on the fly why can't the hard drives be also.  When we installed 8+ years ago the floppies had to be mounted too and that has been overcome, it might be just a simple rewrite of the same code??

---

### Post by Tomosaur on 2007-01-08
Forgive me if I misunderstand you, but are you asking why Linux can't read/write your Windows partitions? If that's the case, then there's something wrong, because Ubuntu at least can automatically read Windows hard drives. Writing is (by default) either unstable or non-existent, and this is because the NTFS filesystem is closed-source. The code which allows you to write to NTFS is in development, and is actually very very good these days. It's not a linux problem though - it just takes time to reverse engineer stuff. Complaining about it in the Ubuntu forums will not get your voice heard - the Ubuntu developers do not read these forums (you'd need to look at Launchpad to get hold of them), and the NTFS read/writing project is not based here either, as it's a general Linux project and as such is not assosciated with any one distribution.

---

### Post by jem7v on 2007-01-08
Tomosaur, that's only with NTFS though. If you're running an older Win98 install and the hard drive is fat32, there should be no problems reading or writing it.  And there aren't.  But when you first install Ubuntu (or at least when I did), it doesn't have that second hard drive mounted up automatically.  You have to go and put in a few lines of code into your fstab, and it's always the same lines of code.  I do believe that That is what he is refering to.

It's not so much that it Can't read the partitions - it's that it Won't until you tell it to.

---

### Post by seuaniu on 2007-01-08
I'm with tomosaur. 

Assuming that you mean "why can't Ubuntu read my NTFS drives?", its not a matter of the operating system being lazy or stupid.  Its a matter of Microsoft having a closed source FS that is not easy to reverse-engineer.  In fact, its a mammoth undertaking.

There have been many projects to get NTFS working on linux over the years, and they've met with varying degrees of success.  Read-only access has been available for quite some time.  Write access is more difficult.  You don't want your drive head flipping bits on the platter unless the driver knows **exactly** whats going on under the hood of the filesystem.  Look at the number of filesystems that linux supports fully.  NTFS isn't on that list because MS doesn't want it there.  They could easily publish the specs to the filesystem, and we'd have working NTFS drivers within a couple of months.

Don't blame the linux/ubuntu/bsd/etc crowd.  They're doing the best job that they can.

---

### Post by Tomosaur on 2007-01-08
Ah, the auto-mounting is what he was talking about, I understand now.

Auto-mounting is switched off by default, if my memory serves me correctly. It can be switched on via the gnome config app, which ironically is not in the apps menu. I never had to edit fstab to get my stuff mounted, I just clicked the 'auto-mount' option. I switched it back off after a little while though.

Regardless, auto-mounting works, you just have to tell it that you want it to. Some people would complain if it was on by default, and others complain if it's off by default. Gotta pick one of them :P

---

### Post by mr_helm on 2007-01-08
Jem7v has me right.  

My computer has 2 hard drives both partitioned into 2 drives each.  HD1A for lack of a better name is mswincrud's proprietary idiocy but HD1B and HD2A are both fat32 and HD2B is where Ubuntu chose to lodge itself with whatever file system it uses.  

I have useful files of the other 2 hard drives  as I am sure other clueless newbies also have that being able to just read would be nice and writing to them even better.  I am not totally unwilling to "hack" Ubuntu's registry to get them visible, (as this OS is just an experimental plaything for me at this point and if i ruin it i don't care) it just seems like an awful lot to ask a nonprogrammer to go through.

---

### Post by mr_helm on 2007-01-08
> **Tomosaur said:**
> 

Auto-mounting is switched off by default, if my memory serves me correctly. It can be switched on via the gnome config app, which ironically is not in the apps menu. I never had to edit fstab to get my stuff mounted, I just clicked the 'auto-mount' option. I switched it back off after a little while though.

Regardless, auto-mounting works, you just have to tell it that you want it to. Some people would complain if it was on by default, and others complain if it's off by default. Gotta pick one of them :P

thank you Tomosaur  can you give more detail??  where is this gnome cinfig app?? At least you give me a place to look.:KS :KS

---

### Post by jem7v on 2007-01-08
Right-click on your app/places/system menu and choose Edit Menus.  Go down to the Applications -> System Tools area and enable "Configuration Editor," which will put it in your Applications menu.  I think Maybe the place to look (once you have the program open) would be under Desktop: GNOME: Volume Manager.  Automount is in there I think.

---

### Post by chesman on 2007-01-08
I think the place u wann edit is /etc/X11/fstab.conf???  im not totally sure.

But the fstab file is the one u add what partitions / HD's you want.

---

### Post by Efwis on 2007-01-08
take into consideration the following, some people are dual booting with dual disk setups using SATA and IDE drives on the same machine. next take into consideration that there are people that have Ubuntu (or Any version of Linux) on the same HDD as Windows. Now how is the fstab supposed to know exactly which way to go?

there is the strong possibility that fstab would try to set up the ntsf/fat32 mount as a partition mount when it is actually a separate hdd. or even vice versa. This is something that will probably be taken care of as AI advances, but until computers are AI enabled by default this will be a difficult situation to fix.

as I'm sure you recall from your CS classes, A computer can only do what the programmer tells it to do. In the case of fstab it is just a file that is designed to let the computer know what is available. but it can't read whether or not you, the user, wants to have read or read/write access to your windows drive.

Now on the flip side, what if we had that set up as default for all disks to be accessible when installed. You decide that you want Linux to be your only OS. now you start getting read errors because fstab is trying to find non-existant disks/partitions that have been preprogrammed to be mounted.

These are just my thoughts, but believe me I wish I was able to program something that would help that out. I just don't know where to begin on that effort.

---

### Post by MetalMusicAddict on 2007-01-08
Problem, mr_helm, is that you just ranted about your situation without asking a direct question. That is the sure-fire way _not_ to get help on _any_ forum. I would think an educated person would have displayed a little more tact that what you did in your first post.

And frankly you come across as very condescending towards linux *and* windows.

I think if you take some time to actually search, read and be polite as most users in this unmatched community are, you will get the hang of things.

Linux is not windows and it never should be.

---

### Post by Efwis on 2007-01-08
> **jem7v said:**
> Right-click on your app/places/system menu and choose Edit Menus.  Go down to the Applications -> System Tools area and enable "Configuration Editor," which will put it in your Applications menu.  I think Maybe the place to look (once you have the program open) would be under Desktop: GNOME: Volume Manager.  Automount is in there I think.

the problem with you directions is as follows, Linux can't mount anything that is not listed in /etc/fstab

the volumes that it mounts are all referred to it from fstab. Also those are checked by default on installation. you still have to put in fstab the volume info.

---

### Post by Tomosaur on 2007-01-08
Hit Alt-F2, and type 'gnome-settings' or 'gnome-config' or something like that. I'm on Windows atm so I can't give you the exact wording.

HINT:
Open up a terminal, type 'gnome' and hit the tab button twice. You should be presented with a list of all commands with 'gnome' in the title. The app you need is one of those. Everyone's talking about fstab - I think the option in here will tell fstab to add the missing partitions. I may be mistaken though, it was quite a while back when I did this.

You may need to launch the app using gksudo.

---

### Post by harmeet on 2007-01-08
I think Tomosour is refering to **gnome-control-center** which is also accessible from panel as **System -> Preferences**

There is a "*Removable Drives and Media*" were you can play with mounting settings for drives.

---

### Post by Efwis on 2007-01-08
> **harmeet said:**
> I think Tomosour is refering to **gnome-control-center** which is also accessible from panel as **System -> Preferences**

There is a "*Removable Drives and Media*" were you can play with mounting settings for drives.

removable media is just that, cd's, floppies, usb devices. not hardwired hdd's (aka internal HDD's)

---

### Post by hendoc on 2007-01-08
I don't find linux enthusiasts to be "unhelpful" or "intolerant."  I know I have asked some stupid questions in the past, but have recieved earnest help from many people at this forum in spite of my ignorance. Pehaps some place other than here would be better for venting your anger and frustration.

---

### Post by raul_ on 2007-01-08
I'd ask for a refund if i were him :rolleyes:

---

### Post by beercz on 2007-01-08
> **raul_ said:**
> I'd ask for a refund if i were him :rolleyes:
From whom?

---

### Post by ardvark71 on 2007-01-08
> **mr_helm said:**
> Linux hackers/enthusiasts are renowned the world over for being an intolerant, unhelpful lot who can't stand anyone who doesn't know as much as they do about their precious little sideline Operating System, and you sir are no exception.  Thank you for keeping the traditions of your kind alive and well in this "For Humans" version of your project.[-(   Keep this type of thinking up and your OS will remain on the sidelines and mswincrud will continue to dominate and eventually **WIN ALL** (pun intended).

Thank you! I couldn't have said it better myself! :-D Fortunately, the forums here are not quite as bad as elsewhere.

Best Regards...

---

### Post by tagra123 on 2007-01-08
> **mr_helm said:**
> Linux hackers/enthusiasts are renowned the world over for being an intolerant, unhelpful lot who can't stand anyone who doesn't know as much as they do about their precious little sideline Operating System, and you sir are no exception.  Thank you for keeping the traditions of your kind alive and well in this "For Humans" version of your project.[-(   Keep this type of thinking up and your OS will remain on the sidelines and mswincrud will continue to dominate and eventually **WIN ALL** (pun intended).


Don't let a few speak for all of us. Most of us here have had to learn new things too, and I for one am willing to help when I think I can be helpful. 

I like ubuntu better than windows, but am always willing to help--especially those that are new to the operating system..

---

### Post by jmartini on 2007-01-08
I think the thing that this thread demonstrates best is the importance of asking a clear question.

---

### Post by STREETURCHINE on 2007-01-08
these forums have been very helpfull to me ,
the sum of my knowledge can be summed up as 2 years ,mostly windows ,but ubuntu for about 5 months now and i have learned so much.

i have learnt to mount my hard drive (not real hard)
i can fix my xorg.conf(which i have broken many times)
and the command line stuff well it used to scare me getting more confident these days

so my opinion ubuntu hard !no way just time and patience that is all that is required.
and ask your questions in a civil tone and if any one can help they usually do

---

### Post by glabouni on 2007-01-08
> **mr_helm said:**
> Why can't this be an automated process by now?

If anyone knows an answer to this question or feels the same reply and share the love.](*,)

I don't know the answer, but I guess it is somewhat related to a computer not being sentient hence unable to guess where to mount these drives and what rights to apply to them. 
if ou had the choice between your partitions automounted somewhere you don't know with some rights that don't necesseraliy suit you, and your partitions not being mounted at all, what 'd you prefere ? in other words "if it ai'nt broke, don't fix it"

this could also very well be related to linux being a secured environment. keep in mind that unix and linux are designed from the ground up to be multi user.
you don't want your mom to have access to your pr0n collection do you ? ^^

---

### Post by david_kt on 2007-01-08
To read/mount windows partition is not a problem. The problem if to write to ntfs file system. I have been using ntfs 3g to write to ntfs harddisk without any problem.

Below link teach you how to install ntfs 3g, and also how to mount your windows partition:

[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

Regards,
DK

---

### Post by Efwis on 2007-01-08
ok, I found the section you need to be in.

go to system>administration>disks

if I am correct, I can't guarantee that I am since I used fstab to enable my windows HDD, that is the tool you want to use.

---

### Post by msak007 on 2007-01-08
Maybe I'm not understanding the problem here, is this an Ubuntu (Gnome) thing only? I run Kubuntu and with every install since Breezy, all 3 of my hard drives (and all 3  partitions on my primary - / and /home on Kubuntu, and Windows) are all automatically mounted. I never once touched my fstab after a format and reinstall, and my drives always show up. Is the problem with hard drives in the machine at the time of install, or newly added hard drives after doing a fresh install?

---

### Post by doobit on 2007-01-08
I run Xubuntu and mine are also automounted. I'm not sure what the problem is here. With my system I open the file manager and look at the "file system" and it's all there.

---

### Post by mr_helm on 2007-01-08
I would like to thank those who have tried to be helpful with my question.  I also would like to apologize to anyone I may have offended with my rants.  What set me off was that the first reply to my question was very typical of the way Linux Hackers/Enthusiasts reacted when I asked a question about my first install 8 years ago (they basically told me to go and write a driver for my nic if I wanted it to work).  Not friendly then and not friendly now.  However, since that first reply most of the other posts have been more helpful so again Thank You.

For those who say i didn't ask a Question I will clarify it:
[I]
If Ubuntu can automatically detect, mount, give proper permissions to, and put an icon on the desktop for a variety of storage media (it even knows that my sd card was made by kodak and made the icon look like my card), why can't it do the same for my hard drives internally? [/I] 

My answers as I understand them so far are that there are a variety of different configurations possible in partitions etc that the system can't know about in advance therefore the OS cannot assign things the proper permissions etc.  Plus it cant read ntfs at all.  

This may be the case if the OS is trying to do everything in advance, but why not treat the fat 32 hard drives as removable media and assign them on the fly after the OS has already loaded?  Isn't this what the individual users are being asked to do in editing the fstab file and then creating a mount point so an icon shows up?  Maybe this is an impossible task like asking mswincrud to access the partition where ubuntu installed, but i guess I just expected a good OS like Linux to be even better than the other OS.  I expected too much.  I want my money back;)   

The other answers where helpful and interesting but in the end fruitless as the automount checkbox was already checked when I found it and the fstab file will have to be edited as per all the other mounting instructions in this forum.  Thank you for your efforts.  :KS 

Again this I guess this was the wrong forum to ask this question in, but I didn't see one more appropriate, and as a totally clueless newbie I went to the absolute beginners forum because I am an absolute beginner.  I know a few things but I am new to this OS

I look forward to asking better, more appropriate questions in the future and receiving your help with a bit more grace.

---

### Post by MetalMusicAddict on 2007-01-08
I have noticed that the drives that are defined during boot havnt showed up on the desktop for some reason. Odd thing is is that they appear in **/mount/** ie: At install I defined my windows partition path as **/media/XPPRO**. It didnt appear on the desktop but its there and mounted if I navigate to **/mount/**.

As I really dont need to access it I just havnt bothered to explore the behavior.

Heres a example as to how I mount a NTFS storage drive of mine:
[SIZE="1"]```
/dev/hdb1       /media/Storage     ntfs    nls=utf8,umask=0222 0       0
```[/SIZE]

There are also ways to write to NTFS drives but I have yet to use them. The example above is read-only.

---

### Post by Dual Cortex on 2007-01-08
Hey! you might as well install "LinuxMint" ... it does what many distros and its developers fail to do for their users. In fact here's something that addresses that problem of not automatically mounting disks:
[http://lt.k1011.nutime.de/forum/viewtopic.php?t=530](http://lt.k1011.nutime.de/forum/viewtopic.php?t=530)

---

### Post by Efwis on 2007-01-08
> **msak007 said:**
> Maybe I'm not understanding the problem here, is this an Ubuntu (Gnome) thing only? I run Kubuntu and with every install since Breezy, all 3 of my hard drives (and all 3  partitions on my primary - / and /home on Kubuntu, and Windows) are all automatically mounted. I never once touched my fstab after a format and reinstall, and my drives always show up. Is the problem with hard drives in the machine at the time of install, or newly added hard drives after doing a fresh install?

with every install of Gnome I have not been able to have my Windows drive automounted. This must be a Gnome specific issue. When I used OpenSuse and Slackware my windows file was mountable at install, both of them I was using KDE desktop.

---

### Post by david_kt on 2007-01-08
May be you have not opened the link I give before. Below I attached the content as well.

[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

Mount your widows Partitions and make it read/writable in ubuntu
by Admin @ 11:10 am. Filed under Other Linux

Some of ubuntu users are running their ubuntu machine as dual boot with windows and if you want to access your windows partition data using this guide in a simple manner.

This tutorial will show you how to mount NTFS and FAT partitions in ubuntu

For mounting TFS we are going to use one small tool called NTFS-3G this is very powerfull and simple tool.

The NTFS-3G driver is an open source, freely available NTFS driver for Linux with read and write support. It provides safe and fast handling of the Windows XP, Windows Server 2003 and Windows 2000 file systems. Most POSIX file system operations are supported, with the notable exception of file ownership and access right changes.

You need to edit the sources.list file using the following command

sudo gedit /etc/apt/sources.list

and add the following repositories which is suitable for you

If you are running Ubuntu Dapper enter the following lines save and exit the file

deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all

If you are running Ubuntu Edgy enter the following lines save and exit the file

deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main

Now you need to import th GPG key for these repositories using the any one of the following command

wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -

wget [http://givre.cabspace.com/ubuntu/givre_key.asc](http://givre.cabspace.com/ubuntu/givre_key.asc) -O- | sudo apt-key add -

Now you need to update the source list using the following command

sudo apt-get update

Install ntfs-3g in Ubuntu

If you want to install ntfs-3g run the following command from your terminal

sudo apt-get install ntfs-3g

Configuring ntfs-3g

Now you need to use the following command to determine all the available partitions

sudo fdisk -l

Now you need to configure your NTFS partitions in /etc/fstab file before doing any changes in /etc/fstab file we will take a backup of this file using the following command (Highly Recommended)

sudo cp /etc/fstab /etc/fstab.bak

Now you need to create a directory where do you mount your windows partitions in this example i ma creating windows directory

sudo mkdir /media/windows

If you want to mount /dev/hda1 is your windows partition you need to enter the following line in /etc/fstab file

/dev/ /media/ ntfs-3g defaults,locale=en_US.utf8 0 0

You need to replace your partition and mount point with your details

Example

/dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

save and exit the file

If you want to mount as read only you need to enter the following line in /etc/fstabfile

/dev/hda3 /media/windows ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0

If You want to change your locale option you need to run the following command in a terminal to know which one is supported by your system.

locale -a

Now if you want these new chnages to take effect there are two options one is you can simply reboot your machine and the second one is without rebooting you need to run the following commands

To unmount

sudo umount -a

To Mount

sudo mount -a

If you want to know more available options for ntfs-3g check man page

If you want to mount and unmount Windows partitions (FAT) manually, and allow all users to read and write

Follow the same procedure to get the list of your windows partitions,create a directory where do you want to mount and you do the following command from your teminal replace /dev/hda3,/media/windows/ to your environment

sudo mount /dev/hda3 /media/windows/ -t vfat -o iocharset=utf8,umask=000

If you want to mount FAT partitions on boot-up to allow users to read and write use the following command in your /etc/fstab file you can see the above procedure how to take backup of fstab file before you do any changes

/dev/hda3    /media/windows vfat  iocharset=utf8,umask=000  0    0

---

### Post by abijah on 2007-01-09
I foolishly wrote that response, and I apologize to mr_helm and the forum.

First off, you said you were a Computer Scientist.  So maybe I jumped to the wrong conclusion by thinking that you were a developer.

I’m a programmer by profession and I personally hate dealing with an unfriendly OS (*nix), or the lame mediocre expensive one.  But I think if we as developers (especially schooled ones like yourself) don’t like something, we should first try to make it better instead of whining/complaining “why why …” about it.
  
I know what you mean about the proud hacker type, but I'm very far from being one.  
I would love to see the day when software is simple. A lot of developers expect novices to buy/use their stuff, yet get kicks from making it so cryptic.

This forum is very helpful and I think it’s providing a great service for Linux.  
In hindsight, my nonconstructive comment was uncalled for.  I might have taken too much caffeine. 

Sorry

---

### Post by Dual Cortex on 2007-01-09
> **david_kt said:**
> May be you have not opened the link I give before. Below I attached the content as well....

Actually, it seems you haven't understood the topic of the thread. This is pretty much another "Linux ready for the desktop" thread.

---

### Post by Crakie on 2007-01-09
> **mr_helm said:**
> I would like to thank those who have tried to be helpful with my question.  I also would like to apologize to anyone I may have offended with my rants.  What set me off was that the first reply to my question was very typical of the way Linux Hackers/Enthusiasts reacted when I asked a question about my first install 8 years ago (they basically told me to go and write a driver for my nic if I wanted it to work). 

All's well that ends well :) 

Linux's origins are geeky. It's rather amazing it has come this far as a desktop OS to begin with. Ubuntu made major contributions to that. Technical contributions to be sure, but perhaps more importantly, it has spawned a beginner friendly community willing to share the knowlegde they gained in the process of tuning their favorite distro to their needs. Because Ubuntu's origins are still showing, here and there, and sometimes needs some work that goes beyond a few clicks of a mouse ;)

Barging in and 'demanding' functionality is not in the spirit of Ubuntu - as you seem to realize now. Nor is posting cranky replies to genuine questions, though. Rather, the people around here generally are just doing what they can to take Ubuntu to the next level.

---

### Post by randiroo76073 on 2007-01-09
Well, as I understood the reason for not auto-mounting to be was for security reasons, if someone managed to gain access to your computer they would only be able to access the Ubuntu OS and not your other OS's or hard drives, therefore could only corrupt/change your OS[Ubuntu] that they managed to hack.  I could be wrong, but it makes sense to me.

---

### Post by 3rdalbum on 2007-01-09
Yes, I read somewhere on the Ubuntu wiki that the mounting was not automatically done for reasons pertaining to security.

There are a bunch of programs floating around which will detect all your hard drives and put them into the fstab. It's an easy procedure. Heck, I even wrote a program to do it :-)

I wanna know why Windows won't automatically mount an HFS-formatted flash drive or CD. The Mac OS has been around since longer than Windows, so why doesn't it do it?

---

### Post by randiroo76073 on 2007-01-10
Don't know about Mac, but windoz can't read linux partitions w/o third party tool

---

### Post by david_kt on 2007-01-10
> **Dual Cortex said:**
> Actually, it seems you haven't understood the topic of the thread. This is pretty much another "Linux ready for the desktop" thread.

At first I also thought this thread is "Linux ready for the desktop" thread, until I read his remark at posting #9:

**I am not totally unwilling to "hack" Ubuntu's registry to get them visible, (as this OS is just an experimental plaything for me at this point and if i ruin it i don't care)**

Then, second thought is this thread is not really "Linux ready for the desktop" thread. May be only mr_helm could answer it. Did I miss something?

Regards,
DK

---

### Post by glabouni on 2007-01-12
> **mr_helm said:**
> [I]
If Ubuntu can automatically detect, mount, give proper permissions to, and put an icon on the desktop for a variety of storage media (it even knows that my sd card was made by kodak and made the icon look like my card), why can't it do the same for my hard drives internally? [/I]

actually you assume ubuntu can't do this. IMHO though it does not do it out of the box for some (good) reason, I don't think ubuntu is unable to do this.
My guess is it is probably just a matter of tuning and tweaking to have this feature activated. I never really look in that matter as this is a feature I have no use for and genuinely don't wan't as I have several partitions I don't want to show up unless I choose so (data backup partition, other OS and rescue OS partition.). For this reason I can't help you there.

For my own use I'm trying to have an external hard drive installed ubuntu working as the live cd does. I mean detecting hardware during boot, and actually booting on almost any box I plug my external hard drive to, but that's a totally different matter.

-edit- having some difficulties with an eSATA drive not being detected, my search lead me to this [post]("http://ubuntuforums.org/showthread.php?t=241345"), and maybe what you want can be achieved through [udev]("http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html").

---

### Post by ragadanga63 on 2007-01-15
The point of Mr_helm is that why can't Ubuntu have a software that enables one to mount/unmount any drive at the click of the mouse.  For example, Linux Puppy has a software that shows all your drives but doesnt automatically mount/unmount them for you.  It does allow you to do that with the click of a mouse.  Plus it reads/writes to ntfs/fat32 file systems without tweaking.  

If a small distro like Puppy can have that feature, why can't Ubuntu?

---

### Post by steve.horsley on 2007-01-15
If you look carefully at the original question, it was asking why the live CD doesn't auto-mount all the windows partitions. I have to say, I like the way Knoppix does it, putting icons on the desktop that give you the **option** to mount the disk partitions, and think the lack of such a thing on the Ubuntu live CD is either lack of interest or time by the developers, or less likely, lack of CD space.

I seem to remember that installer configures an installed Ubuntu to mount all partitions it can understand, in /media, but I may be wrong on this. Fixing fstab is such a trivial thing that I really don't pay much attention to it. I do however think there should be a GUI for setting the fstab options, for beginners to use, and really don't see why the Ubuntu developers saw fit to remove the one that was in Dapper from Edgy even if it wasn't that brilliant. There's an excellent one called pysdm in the repos for Edgy but you have to undo the UUID stuff in fstab first.

---

### Post by Dual Cortex on 2007-01-16
Again, you guys should check out Linux Mint.

---

### Post by j002 on 2007-01-16
Windows (not sure about XP) is a *microcomputer* sytem, designed for single users.

HDs are not assigned dynamically, the OS uses the IRQ lines hardwired in the motherboard.  Its based on a system that did not have a program manager.

Unix is designed for multiple users.  This means there are different mount points for devices.  These mount points are "conceptual" not actual physical points like in microcomputers.

Differrent programs access different mount points. So if they were provided dynamically (like USB) some programs would not work properly if the access point was wrong.  This does not occur with microcomputers because the IRQ address is always the same.

---

### Post by aysiu on 2007-01-16
This is not a "Linux isn't ready for the desktop" thread, especially since Knoppix and Mepis (and who knows how many other Linux distros) can already do the task in question.

This is, however, also not a support thread, so I'm moving it to the Cafe and giving it a more accurately descriptive title.

---

### Post by Polygon on 2007-01-16
and linux can also read ntfs partitions out of the box, as i have a couple of em for windows and every time i reinstall edgy it sets em up just fine

but i do agree that ubuntu needs to have something like knoppix where all hard drive partitoons are mounted, and then a tool to let you configure where they get mounted, if they are read only or not, etc. It would be a project that would make a ton of people happy :D

---

### Post by ihatethedekoys on 2007-01-17
Um, Ubuntu automatically detected my hard drives, added them to the FSTAB and mounted them to /media and put a symlink on my desktop.

And I don't remember doing anything.

---

### Post by aysiu on 2007-01-17
> **ihatethedekoys said:**
> Um, Ubuntu automatically detected my hard drives, added them to the FSTAB and mounted them to /media and put a symlink on my desktop.

And I don't remember doing anything.
So you're saying you installed Ubuntu on one drive, physically added a new drive **after** installation and then Ubuntu automatically detected the new drive and added it to the /etc/fstab file?

---

### Post by macogw on 2007-01-17
Wait, what?  I know the live cd doesn't mount internal hard drives by default, but I've never turned it on and not had my hard drive be mounted.  How the heck could it boot from the hard drive if it wasn't mounted?  Are you still running it live?  If so, that's why.  If not, I can't fathom how it booted without mounting.

---

### Post by aysiu on 2007-01-17
I think the question is this:

Hard drive #1 is the one Ubuntu is installed on. Of course it's mounted because that's what gets booted.

After Ubuntu is already installed, hard drive #2 is inserted.

Hard drive #2, as far as I know, does **not** get detected and automatically added to the /etc/fstab or automatically mounted in /media. That's what I was trying to clarify with ihatethedekoys.

---

### Post by dca on 2007-01-17
Uh oh, aysiu...  This is starting to sound like a 'Linux not being ready for the desktop' thread...  
 
 
What Linux is ready for:
 
A friend of mine runs a small business.  He has older hardware that we're converting into servers.  One will be firewall/router, one NAS-type, etc, etc.  I have a slew of Linux distro CD(s).  I now have more than I did of AOL install CD(s) from the nineties.  The beautiful thing for me is any one of those will work great versus spending schmekels on an MS Server 2k or 2k3 license which ranges well above $1K USD per install...  I like that....
 
 
Just on that principle alone I would never down-play or why can't this distro do that and not that like this one can, etc, etc...

---

### Post by aysiu on 2007-01-17
> **dca said:**
> Uh oh, aysiu...  This is starting to sound like a 'Linux not being ready for the desktop' thread...   At most, it could be a "Ubuntu is not ready" thread, since this is a non-issue in Knoppix and Mepis.

---

### Post by Johnsie on 2007-01-17
I submitted a feature request regarding this topic.... The Ubuntu developers told me that  drives are now mounted by default, including ntfs.

---

### Post by dca on 2007-01-17
Okay, I guess I'll buy that.  It does kinda' sound like sour grapes, though.  I look at it this way as a Linux distro being a tool.  When Ubuntu came on to the seen, they broke ground.  Obviously many many people converted or found Linux for the first time to gain som much popularity so fast...  Here it is a couple years later, Ubuntu is #1 by a long shot...  Someone must be doing something right because I haven't heard too much about Ubuntu in the enterprise, only Ubuntu on the desktop...
 
Ah, it is what it is...  :D

---

### Post by vjones777 on 2007-01-28
> The Ubuntu developers told me that drives are now mounted by default, including ntfs.
Thank goodness for that. :D 
Also see ["Will Feisty Live CD (& Install) include Auto-Mounting Drives Like Knoppix Live CD?"]("http://www.ubuntuforums.org/showthread.php?t=339788")
I think OzzyFrank summed up the problem nicely - New users coming from Windoze will question why they have to switch to another disto (Knoppix) if Ubuntu is so great.
I certainly didn't want to have to explain to my 70 year old mother how to open a terminal, type in the command line and deal with inevitable typo's over the phone!

However, the implication from OzzyFranks thread is that we may have to wait until the next release to have the live CD do this (or use a development version for now). 

So in the meantime, for those having the same problem with the live CD, (if you'll excuse me repeating stuff) you'll have to:
Either:

```
Using Gnome goto:
System->Administration->Disks
select the required disk and partition
Under 'Access path' create a new directory e.g. /windows
then enable it and hit OK
```
OR
If you want to use the command line, refer to the section "To Mount a FAT32 partition (or NTFS, but with read-only privileges)" in [MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

That lets you read - to write to the partition with Nautilus it seems you have to have root permission.  Open a terminal and type
```
gksudo nautilus
```You will probably get a Gnome authentication warning message, if so if you just hit Enter it should bring up Nautilus anyway.   You can now write to that drive from Nautilus.

---

