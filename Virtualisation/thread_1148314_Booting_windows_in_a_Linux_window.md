---
title: "Booting windows in a Linux window"
date: 2009-05-04
forum: Virtualisation
---

### Post by Eld.Raven on 2009-05-04
I was wondering how I can boot Windows in Linux so I run both systems at the same time. I dont want to use VirtualBox because then I have to reinstall windows.

I have them in dualboot now. So I can choose between Linux or Windows at startup.

// Seb

---

### Post by Didius Falco on 2009-05-04
You can run some Windows apps by using Wine or another emulator, but to run full-blown windows in linux,virtualization is the only way.

---

### Post by Mark Phelps on 2009-05-04
> **Eld.Raven said:**
> I was wondering how I can boot Windows in Linux so I run both systems at the same time. I dont want to use VirtualBox because then I have to reinstall windows.

I have them in dualboot now. So I can choose between Linux or Windows at startup.

// Seb
You can install and run Wine -- but it's an emulation layer and only runs some MS Windows programs.

---

### Post by Mark Phelps on 2009-05-04
> **Eld.Raven said:**
> I was wondering how I can boot Windows in Linux so I run both systems at the same time. I dont want to use VirtualBox because then I have to reinstall windows.

I have them in dualboot now. So I can choose between Linux or Windows at startup.

// Seb
You can install and run Wine -- but it's an emulation layer and only runs some MS Windows programs.  You're not really "booting into Windows".

If you want to do it the other way, you can install Ubuntu inside MS Windows using Wubi.

---

### Post by Eld.Raven on 2009-05-04
No not wine....

Hmm thats to bad, I realy didnt want to reinstall windows >.< But I will giv it a try, I have a spare HD that I can use to try it out!

Is it possible to resize the partion that ubuntu uses. I need to give it a lot of more space I think (for general reasons).

---

### Post by Didius Falco on 2009-05-04
Sure, just put in your Live CD and use the partition manager in **System/Administration** to resize it.It shouldn't be mounted, by default, but if you see a key icon on the partition, unmount it before you resize it.

---

### Post by apienk01 on 2009-05-04
Also be aware that Windows installation will break GRUB bootloader. You will have to fix it afterwards.

---

### Post by phantom3113 on 2009-05-04
I would think that as there's PartImage to create a copy of a Ubuntu install, there should be a similar way to make a copy of a Windows install. If you can do that and burn it to a cd, you should be able to install Windows from exactly where it's currently at. (In a VBox, that is)

---

### Post by BLTicklemonster on 2009-05-04
[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

This might give you some ideas. Probably not for the faint of heart. I have always wanted to try this myself... I mean, if you already dual boot, why do a fresh install of windows?

---

### Post by DGortze380 on 2009-05-04
> **Eld.Raven said:**
> I was wondering how I can boot Windows in Linux so I run both systems at the same time. I dont want to use VirtualBox because then I have to reinstall windows.

I have them in dualboot now. So I can choose between Linux or Windows at startup.

// Seb

You can boot a raw disk in virtual box. (ie. boot a VM from an existing HDD partition). It's tricky but can be done.

---

### Post by Eld.Raven on 2009-05-04
Hmm so there is ways for me to keep my current windows installation in other words.
I will take a look on that link you recommended.

just a Q about that stuff that phantom wrote. Im not sure that it will work, I will explain.

> My computer setup looks like this (with the partions)
*** Windows partion**
- here I keep windows and nothing else, in other words, I install all games and programs in a other partion
*** Unsorted**
- Here I keep programs and downloaded stuff and things that I yet havent sorted.
*** Media**
- This is for all my movies and music and other stuff, like pictures and so on.
*** Games**
- as it says, all games here

then I have the Linux partions and swap.
* Linux ubuntu
* ext3 partion for future use of an other dist (if I would like to try something else)
* SwapSo in other words, if I made a cope of the windows-install it would probably loose all the directions for the programs and games, well this is just a thought. It could be that it keep the directions.

EDIT: Im very good at windows but totally new at Linux (more or less) So if its to tricky maybe I wont be able to pull it off =/

---

### Post by Mykle87 on 2009-05-04
I dual boot XP and Ubuntu on my laptop and I can virtualize the existing windows partition inside Ubuntu with Virtualbox. [I followed this thread.]("http://ubuntuforums.org/showthread.php?t=769883&highlight=virtualize+physical+windows") [Follow this guide for Vista/7.]("http://ubuntuforums.org/showthread.php?t=984437&highlight=virtualize+physical+windows") It is a little advanced but you follow step by step you can do it. Good luck.

---

### Post by Eld.Raven on 2009-05-04
Hehe Im just scared to **** everything up ^^

But I will try it out!

---

### Post by Mykle87 on 2009-05-04
I don't blame you. I was nervous working through the tutorial but I learned a lot after doing it. I had a fresh system so I didn't really have much to lose. Backup all your data just in case and post in that thread if you have any issues or concerns.

---

### Post by Eld.Raven on 2009-05-04
Hmm I dont have anything important on the Ubuntu-install (since its kinda fresh and the things I have done can I do again ^^) Its more the windows thingy Im afraid of loosing.

Some1 please define GRUB. I know that different dists are build upon different cores. But this maybe is something else.

---

### Post by Mykle87 on 2009-05-04
Maybe its time for a good format anyway :) Anytime you do something like this, it is highly recommended that you back up your system.

---

### Post by Didius Falco on 2009-05-04
> **phantom3113 said:**
> I would think that as there's PartImage to create a copy of a Ubuntu install, there should be a similar way to make a copy of a Windows install. If you can do that and burn it to a cd, you should be able to install Windows from exactly where it's currently at. (In a VBox, that is)

You can use Partimage to make an image of Windows as well.

---

### Post by Eld.Raven on 2009-05-04
> **Mykle87 said:**
> Maybe its time for a good format anyway :) Anytime you do something like this, it is highly recommended that you back up your system.

Brr I get the chills every time I think of formating my windows or reinstalling it...

---

### Post by DGortze380 on 2009-05-04
> **Eld.Raven said:**
> Hmm so there is ways for me to keep my current windows installation in other words.
I will take a look on that link you recommended.

just a Q about that stuff that phantom wrote. Im not sure that it will work, I will explain.

So in other words, if I made a cope of the windows-install it would probably loose all the directions for the programs and games, well this is just a thought. It could be that it keep the directions.

EDIT: Im very good at windows but totally new at Linux (more or less) So if its to tricky maybe I wont be able to pull it off =/

Don't expect to play those games in a VM is they require any significant 3D Graphics.. DirectX etc. is not supported.

---

### Post by Eld.Raven on 2009-05-04
> **Mykle87 said:**
> I dual boot XP and Ubuntu on my laptop and I can virtualize the existing windows partition inside Ubuntu with Virtualbox. [I followed this thread.]("http://ubuntuforums.org/showthread.php?t=769883&highlight=virtualize+physical+windows") [Follow this guide for Vista/7.]("http://ubuntuforums.org/showthread.php?t=984437&highlight=virtualize+physical+windows") It is a little advanced but you follow step by step you can do it. Good luck.

So I decided to try this out.. I will first just type down how I will do it (so I get it right with all the things)

```

1. 
cd ; mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub 

2.
- I open "menu.lst"
- Find and erase "# savedefault=false"

3. 
sudo usermod -G disk,vboxusers -a `whoami`

4.
I change:
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register
too (since Windows XP is installed on that partition):
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda1 -partitions 1 -relative -register

5. I just follow the rest of the tutorial word for word.
```I just wanted to check so I do the right stuff from the beginning. So if someone please could check this for me I would be happy ^^

@[DGortze380]("http://ubuntuforums.org/member.php?u=390930") No worries, I had no hopes of that =) If I want to play anything more advanced I could just switch! Thx anyway.

// Seb

---

### Post by Mykle87 on 2009-05-04
I think your step 4 should be this:
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk **[B][B]/dev/sda -partitions 1**[/B][/B] -relative -register
```

Note it should be **/dev/sda -partitions 1** instead of /dev/sda1 -partitions 2

---

### Post by Eld.Raven on 2009-05-04
Greate... then i change that =)

---

### Post by Eld.Raven on 2009-05-04
I get this error when I try this:

```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 1 -relative -register
``````
VirtualBox Command Line Management Interface Version 2.1.4_OSE
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error opening the raw disk '/dev/sda1': VERR_ACCESS_DENIED
The raw disk vmdk file was not created

```

---

### Post by anewguy on 2009-05-04
There is a section in the vbox help itself under advanced that tells how to actually set this up.  I did this myself a long time ago.  At that point in time you were left with more or less a run Windows in vbox or run Windows seperate type thing whereby you had to stick with one once you did it.  Otherwise Windows can get confused by the hardware (actual versus virtual) and can get quite nasty.  It eventually got to the point that if I tried to dual-boot it, then go to vbox, then come back and dual-boot it again that Windows wouldn't boot and just gave me the bsod.  I talked to Microsoft about it, without letting them know I was virtualizing it besides, and they told me the only way to recover was to completely wipe it clean and reinstall.  So, yes this can be done.  Yes it works.  Be aware though, that the smallest of errors can result in your Windows installation suddenly becoming non-bootable.

Dave :)

---

### Post by Eld.Raven on 2009-05-04
eeek!!!!

well I still havent solved my current problem ^^
But i will check in the "vbox help".

---

### Post by Mykle87 on 2009-05-04
If you put /dev/sda -partitions1 instead of /dev/sda1, that should fix it.

---

### Post by Eld.Raven on 2009-05-04
Now I am here:
```
Step 5: Run VirtualBox

Realize that you may have to reactivate your copy of XP
Create a machine that uses the created .vmdk (in the drop-down menu of the HD selection section
**Have this machine boot the CD-ROM first and mount the grub.iso file**
You may have to try between the two IDE controllers types (Settings/Advanced) to see which works for you
Enable the IO-ACPI option and run your VM!
```

how do I change so that I boot the CD-ROM first? do I do it from BIOS or is there a way to do it in Linux?

---

### Post by DGortze380 on 2009-05-04
> **eld.raven said:**
> now i am here:
```
step 5: Run virtualbox
[list]
[*]    realize that you may have to reactivate your copy of xp
[*]     create a machine that uses the created .vmdk (in the drop-down menu of the hd selection section)
[*]**have this machine boot the cd-rom first and mount the grub.iso file**
[*]     you may have to try between the two ide controllers types (settings/advanced) to see which works for you
[*]    enable the io-acpi option and run your vm!
[/list]

```

how do i change so that i boot the cd-rom first? Do i do it from bios or is there a way to do it in linux?

bios

---

### Post by TheNosh on 2009-05-04
if you really want to run both at the same time without virtualization i think it's doable, but only with windows as your base system. google andlinux, i'm pretty sure thats basically what it does

---

### Post by Eld.Raven on 2009-05-04
Hmm I allready had CD-ROM as top priority in the boot order. And I have also maunted grub.iso in VB

When I try to boot Windows I get this
```
Error 15: File not found

Press any key to continue...
```

---

### Post by Eld.Raven on 2009-05-04
Yeah I have tried andLinux but its not what Im after. Well, I cant say that I gave it a honest chance, since I never got it to work probably ^^

---

### Post by Insanity01 on 2009-05-04
Wine / Cedega could be of some use

---

### Post by Eld.Raven on 2009-05-04
Hmm I bet that there is sometime during the fifth step that I am doing wrong...

I open VB click new and make a new Virtual Machine, I use the fake/virtual HD that I have created.
Then cant I figure out if he means that I am going to mount the grub.iso in Ubuntu or in VB.

---

### Post by Mykle87 on 2009-05-04
You mount the grub.iso in VB

---

### Post by Eld.Raven on 2009-05-04
[I]**[Configure]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") /home/you/iso/boot/grub/menu.lst** to boot your target partition. Remove the "savedefault" option from your target entry if it exists. Then run the following to create the grub.iso file,

[/I]- How do configure it to boot my target partition? (where in the file can I find that?) and is the targeted partition sda1?

---

### Post by Insanity01 on 2009-05-04
you know maybe this can help, you probably ever installed a OS on a computer without OS
virtualbox is that PC without OS, just do as u'd do on other pc, virtualbox DOESN'T affect your real machine, it's just a virtualization level so u shouldn't be scared to try things out either ^.^

---

### Post by Mykle87 on 2009-05-04
> **Eld.Raven said:**
> [I]**[Configure]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") /home/you/iso/boot/grub/menu.lst** to boot your target partition. Remove the "savedefault" option from your target entry if it exists. Then run the following to create the grub.iso file,

[/I]- How do configure it to boot my target partition? (where in the file can I find that?) and is the targeted partition sda1?

Post the output of the file and I can help you configure it.

---

### Post by bodhi.zazen on 2009-05-04
Moved to Virtualization.

Yes you can do this (boot your windows partition) with VirtualBox, KVM, or VMWare.

Take care as this is in Beta and can cause breakage.

There are many how-to's for this, in fact the sticky at the top of this forum has the links :

[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

There is a reason it is a stick after all.

[http://ubuntuforums.org/showpost.php?p=6122463&postcount=6](http://ubuntuforums.org/showpost.php?p=6122463&postcount=6)

You can also migrate your windows installation to a virtual hard drive.

Virtualbox and vmware maintain how-to's for doing exactly this :

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

====

With windows, however, my advice is to do a fresh install, and then back up the new hard drive. Run in a snapshot and discard changes when done. You system will allways be fast, virus free, and defragmented.

---

### Post by Eld.Raven on 2009-05-05
Well anyway I solved it yesterday, I can now boot Windows! Its working but its not flawless! =/

I still cant runt the programs and games I have. When I start windows and check in "my computer" I cant find the other partitions =S

Well Thanks to all of those who have helped me =D

// Seb

---

### Post by DGortze380 on 2009-05-05
> **Eld.Raven said:**
> Well anyway I solved it yesterday, I can now boot Windows! Its working but its not flawless! =/

I still cant runt the programs and games I have. When I start windows and check in "my computer" I cant find the other partitions =S

Well Thanks to all of those who have helped me =D

// Seb

You're going to have to create raw images of those and include them in the vm as slave drives.

---

### Post by Eld.Raven on 2009-05-05
Do you know any guide for that?

---

### Post by DGortze380 on 2009-05-05
I've never done it, I imagine it would be the same as what you just did: [http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

create a .vdmk for the parition, then in the virtual box settings for your XP VM add teh .vdmk as a slave drive.

---

### Post by bodhi.zazen on 2009-05-05
You will not be able to run your games from windows with virtualilzation.

This is because virtualization does not use your actual hardware, in this case your videocard. The virtual emulated card does not support 3-d graphics required for most games.

In terms of sharing, no need to convert. Use samba ;)

---

### Post by Eld.Raven on 2009-05-05
well, lets say i want to use my programs then. Atm I cant use anything that I have on my actual install.

---

### Post by bodhi.zazen on 2009-05-05
> I cant use anything that I have on my actual install.

Can you describe your problem a bit better ?

If you can not "boot" windows in a Virtual Machine then you have a problem with your configuration, which may be complex as you are boot a physical partition.

Assuming windows boots, and you can log in, what application are you having a problem with ?

---

### Post by Eld.Raven on 2009-05-05
ok like this.

I can boot windows in Linux (with VB)
I can boot windows normal

But when I boot windows threw VB I cant use the programs that I have. I cant start any application at all, I mean except the ones that I have on my windows partition. But since I have a lot of stuff on other partitions that became a problem.

you get me now?

---

### Post by bodhi.zazen on 2009-05-05
> **Eld.Raven said:**
> ok like this.

I can boot windows in Linux (with VB)
I can boot windows normal

But when I boot windows threw VB I cant use the programs that I have. I cant start any application at all, I mean except the ones that I have on my windows partition. But since I have a lot of stuff on other partitions that became a problem.

you get me now?

No as you did not include sufficient information. I assume that Windows boots and you can run applications on your C:\ Drive, such as notebook.

I assume you have additional drives on Windows, such as D:\ I assume you can not run applications on D:/ as you have not added the drive to your windows VBox guest.

As DGortze380 said, add them, wither as a raw disk as an image.

> **DGortze380 said:**
> You're going to have to create raw images of those and include them in the vm as slave drives.

You have not indicated your actual partition scheme for windows or if you have added the disks to vbox.

---

### Post by Eld.Raven on 2009-05-06
Exactly and that is a thing I dont know how to do =)

You do get me. I posted this thred in "Absolute beginners talk" Since I havent run Linux for so long (max a week or so). So there is a lot of stuff that is new to me! =/

EDIT: does VB virtulize my current hardware or does it just pick some hardware at random, since the application for controlling my graphic-card wont work.

// Seb

---

### Post by DGortze380 on 2009-05-06
> **Eld.Raven said:**
> Exactly and that is a thing I dont know how to do =)

You do get me. I posted this thred in "Absolute beginners talk" Since I havent run Linux for so long (max a week or so). So there is a lot of stuff that is new to me! =/

EDIT: does VB virtulize my current hardware or does it just pick some hardware at random, since the application for controlling my graphic-card wont work.

// Seb

It runs on a hardware abstraction layer. Your hardware appears to the guest as devices 'simulated' by VirtualBox, VirtualBox forwards all hardware interactions to your real devices through your Host OS. You don't choose what hardware the Guest sees (unless VirtualBox allows it, like for your NIC). So no, your Guest does not have direct access to your Hosts Video Card which is why you don't have 3D and why your program for controlling the card doesn't work. As far as the Guest is concerned, the card doesn't exist.

---

### Post by Eld.Raven on 2009-05-06
Thanks for the answer!

So this means that I never will be able to boot "the real thing" in a Linux window, since some "things" always be lost during this attempt. Am I right?

Cuz I wanted to boot windows the way I see it when I am logged in to windows.

---

### Post by DGortze380 on 2009-05-06
> **Eld.Raven said:**
> Thanks for the answer!

So this means that I never will be able to boot "the real thing" in a Linux window, since some "things" always be lost during this attempt. Am I right?

Cuz I wanted to boot windows the way I see it when I am logged in to windows.

You can boot it 'the way you see it when you are logged in to windows'... but as I said pages back, don't expect 3D, etc. to work... It's still a Virtual Machine.

---

### Post by bodhi.zazen on 2009-05-06
> **Eld.Raven said:**
> Thanks for the answer!

So this means that I never will be able to boot "the real thing" in a Linux window, since some "things" always be lost during this attempt. Am I right?

Cuz I wanted to boot windows the way I see it when I am logged in to windows.

Define "Real". No virtualization does not directly use your hardware. It does run the actual windows binary.

I think your problem is not with your understanding of linux, but your understanding of Virtualization.

To be honest, I suggest you take a look at the virtualbox documentation. It is well written and after an hour or so you will have a much better understanding.

[http://download.virtualbox.org/virtualbox/2.2.2/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.2.2/UserManual.pdf)

With Virtualization, the hardware is emulated. Normally you install an operating system onto a virtual, or emulated hard drive.

Make a new guest, see where it asks you to make a hard drive ?

Now close down your windows guest. Go to the Setup and add a new hard drive. Either add in your additional partitions, as you did with C:\ or move your data to a new virtual hard drive.

---

### Post by Eld.Raven on 2009-05-06
> **bodhi.zazen said:**
> 
With Virtualization, the hardware is emulated. Normally you install an operating system onto a virtual, or emulated hard drive.

Make a new guest, see where it asks you to make a hard drive ?

Now close down your windows guest. Go to the Setup and add a new hard drive. Either add in your additional partitions, as you did with C:\ or move your data to a new virtual hard drive.

With normally, do you mean when I install Windows from scratch or when I install it in VB (or anything else?).

By "guest" I guess that you mean "Virtual machine" and it asks me to use WinHD.vmdk (and I guess that this is the virtual HD that I made through that guide?!)

Well anyway, Im thinking about running only Linux and move all my "data" from the NTFS-partitions to my Linux-partitions. Mostly cause this seems much easier, and run the programs/games trhough wine insted. Im starting to think that I took "water over my head". Im still very new to linux (and VB for that part too), and there are a lot of commands and other stuff that I maybe need to learn before I try any too complemated stuff.

But I will give that manual a try, eaven if I think that I will have a hard time to keep up with all the commands and code-parts that usually is taken for granted knowledge. (And that English aint my main-language makes things a little bit harder too).

But I   appreciate all the help I get!

// Seb

---

### Post by albinootje on 2009-05-06
> **Eld.Raven said:**
> With normally, do you mean when I install Windows from scratch
No
> or when I install it in VB (or anything else?).

Yes. Here VirtualBox was meant.
> 
By "guest" I guess that you mean "Virtual machine" and it asks me to use WinHD.vmdk (and I guess that this is the virtual HD that I made through that guide?!)

vmdk is the extension of a VMware style virtual disk.
VirtualBox should be able to work with that, but there were some reports of problems with that a while back. 
Make sure you make regular backups of your important data.
> 
Well anyway, Im thinking about running only Linux and move all my "data" from the NTFS-partitions to my Linux-partitions. Mostly cause this seems much easier, and run the programs/games trhough wine insted.
Please do some testing first, before you move to Linux only.
When you're a Linux beginner it makes more sense to keep the dual -boot for a while until you have learned to be comfortable enought in Linux.

---

### Post by Eld.Raven on 2009-05-06
> **albinootje said:**
> No
Please do some testing first, before you move to Linux only.
When you're a Linux beginner it makes more sense to keep the dual -boot for a while until you have learned to be comfortable enought in Linux.

Well the thing is that I probably will use Linux in a week more or two. And then will I go back to windows because Im to lazy to relearn my self into linux. But if I only have Linux then I cant get back to windows and I more or less get forced to use Linux. And its not like I have anything to loose, I can just leave all my files (soutch as music/movies/games and whatelse) on an other HD. And if I REALY think that Linux sucks then I just install windows again and reinstall the programs that I had. easy as that ;)

---

### Post by albinootje on 2009-05-06
> **Eld.Raven said:**
> But if I only have Linux then I cant get back to windows and I more or less get forced to use Linux. And its not like I have anything to loose, I can just leave all my files (soutch as music/movies/games and whatelse) on an other HD.

Okay, fine :)

But I also made this remark here because you and/or others mentioned Wine a few times.
Wine is an interesting project which has been around for more than 15 years now, but it cannot replace MS-Windows for a 100%. 
You better check the Wine application database, and the user reviews for specific software.
For certain MS-Windows software you're better of with running MS-Windows in VirtualBox in Ubuntu.

Please read this :
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

and check this for installing software from the repositories :
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

and check this for names of software choices in Linux :
[http://www.osalt.com/](http://www.osalt.com/)

and this for audio and video playback :
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Eld.Raven on 2009-05-06
Thanks I will give a look.

Hmm yeah how will I manage without CS or Team fortress =O. Maybe I should have MS in a dualboot for ONLY games.. And if there is other software that I would like to have... Hmm it seems like I need to sleep about this ^^ as it is now I am in Linux all the time except when I play games. And playing games is something that I should do less anyway =D

---

