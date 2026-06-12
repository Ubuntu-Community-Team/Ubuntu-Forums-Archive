---
title: "[SOLVED] Virtual Machine Question"
date: 2008-10-09
forum: Virtualisation
---

### Post by crazyness003 on 2008-10-09
Hello. I was contemplating on using a VM. But here are the questions i have:

1. Is there a list of available (preferably FOSS) software VM's for *ubuntu
2. How does it work (i've used VM in 'doze and OSX, so is it similar?)
3. Can i use an already existing partition (highly unlikely, but still awesome if you can use an already bootable partition to upen in a VM) or do i need to set up a Virtual HDD
4. What about speed and compatability?

just some general questions one might have about Virtual Machines.
I've used
(win) MS Virtual Machine 2007 (garbage)
(win) VMware [something] (okay)
(mac) VMware fusion (didnt test a lot to give a judgment)
(mac) Parallels Desktop (awesome-ish)

I've seen something called VirtualBox in the repos, but i wanna get all the facts before i dive into this. So, if anyone has some wise wisdome for me, and anyone else who was curious, hit me.

Obviously, im gonna use it to install XP. Stupid Live Messenger, all my family uses it, even tho i constantly tell them to use something else. I need the Video Chat, i know about amsn etc, but no video with them. Also, wine is a little sketchy when i make flash movies using Flash 8 pro. wine works, but not good enough.

Thanks in advance

EDIT: I also wanted to test arch and puppy before i install them

---

### Post by wd5gnr on 2008-10-09
VirtualBox works well. The set up is a little involved, but not terrible. It is best to set up a virtual partition but you can run an existing drive. However, it is kind of wonky. Partly because XP discovers new hardware (set up a "virtual" profile) and may need to reauthorize windows. Partly because you almost certainly have ACPI and ioAPIC set up on Windows and the ioAPIC especially makes VirtualBox very slow. I actually went in and rekerneled mine so it was just a plain jane setup so I could turn ioAPIC off -- it was painfully slow.

Speed is good, integration is good (but the floating windows don't work well on dual monitor). The display does not do 3d accel so forget games or anything else like that. If you have two monitors it will sit on one or the other and you can move it, but you can't really get two monitors going in any meaningful way. There is some way you can do multiple monitors through RDP but it doesn't look practical to me.

---

### Post by lazyart on 2008-10-09
VirtualBox OSE is open source.  I believe Xen is open as well...

---

### Post by run1206 on 2008-10-09
i'm using virtualBox OSE on Intrepid, here's a screenshot. I'm running off my current Windows partition on the same HDD. (so now i can view/run programs without dual booting).
I use the ACPI feature from the settings in virtualbox. the ioACPI feature was too slow for me.  I ramped up the RAM to about 300MB (cuz i use MS Visual Studio C# and MatLab while in Windows)

had some trouble in the beginning, but make sure the module vboxdrv runs when booting, and make sure you update your kernals and linux-headers-generic before installing

just as wd5gnr says, i also had to reactivate windows (while in virtual mode) and setup a Vbox profile in the hardware manager tab in System within the Control Panel.

---

### Post by WWSmith36 on 2008-10-09
I think VirtualBox is the best VM out there.  It is more robust the VMWare I think.  I would not recommend the the OSE version.  The OSE version in the repos do not have USB support.  Your jump drive and other USB devices will not be seen by VBoxOSE.  There is USB support in the closed source version

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Hope this helps

---

### Post by run1206 on 2008-10-09
> **WWSmith36 said:**
> I think VirtualBox is the best VM out there.  It is more robust the VMWare I think.  I would not recommend the the OSE version.  The OSE version in the repos do not have USB support.  Your jump drive and other USB devices will not be seen by VBoxOSE.  There is USB support in the closed source version

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Hope this helps

VirtualBox OSE supports my USB mouse in windows :?
their was a hack to input so it could support USB in the open source version, i don't remember where it was (definitely within these forums somewhere)

are you running Hardy or Intrepid?

---

### Post by crazyness003 on 2008-10-09
Coolz. So VirtualBox OSE would be my best bet, and you say ther's a way to boot my existing partition? *shwiggy!* Thats roxor. I dont care how hard  it is, i just dont wanna mess up that partition,since its a pain in the [bleep] to clean and reinstall 'doze. 
I might return and get some help for that, but my questions were answered and thanks to all who participated.

I dont feel like getting closed source, its too microsofty and steve jobs lame (and that is some serisous lamness)...kinda like my video drivers...rats

anyway, thanks  =P~

>  I actually went in and rekerneled mine so it was just a plain jane setup so I could turn ioAPIC off -- it was painfully slow.
What exactly did you rekernel, because that would be a little too over my head.  :?:

Also, im on a laptop (hp tx1000), so dual monitors are not optional. As for ram...i got 2 gigs, and ubuntu only uses about 1gig at any given time, so dedicating about 700mb to XP will give me satisfactory results...i think. Any other pointers i should be aware of would be appreciated.

- I gnu baby, gnu :-({|=

---

### Post by crazyness003 on 2008-10-09
> **run1206 said:**
> ...

I wanted to ask you about your screenshot, whats the icon you got in your awn bar, its the ie icon, almost upside down with a smiley-like smile under it?

just curious

---

### Post by run1206 on 2008-10-10
> **crazyness003 said:**
> I wanted to ask you about your screenshot, whats the icon you got in your awn bar, its the ie icon, almost upside down with a smiley-like smile under it?

just curious

ies4linux: it a program to run Internet Explorer 6 within Linux.
link: [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

i think they're trying to get IE7 in ies4linux as well, not sure.

so i switched over to VirtualBox PUEL just a few minutes ago, but now i can't see my USB devices (jumpdrive). keep getting a memory error when accessing the settings and for within settings i can't see the device. :(

edit: SUCCESS!!! i searched virtualbox.org and found out the we have the solution in our Ubuntu Help pages:
[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

```

USB

To get USB support, you need the PUEL version. Via the GUI, there is an option to enable USB.

Furthermore, your user must be able to access /proc/bus/usb/*

Since Gutsy, /proc/bus/usb is not mounted by default. You need to edit /etc/init.d/mountdevsubfs.sh and uncomment the following lines:

        #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

In order to give users in the vboxusers group write permissions to the devices in /proc/bus/usb, you'll need to edit some rules in /etc/udev/rules.d.

Under gutsy, edit /etc/udev/rules.d/40-permissions.rules to say the following:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

Under hardy, edit /etc/udev/rules.d/40-basic-permissions.rules to say the following:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

Then, restart the udev service:

sudo /etc/init.d/udev restart

Now, if you haven't done it already, make sure your user is part of the group vboxusers using the following command:

sudo adduser $USER vboxusers

http://www.virtualbox.org/ticket/747
```

you have to make a group and gave them access to reading and writing to the devices in /proc/bus/usb

even though it says Gutsy and Hardy, i'm now running my Kingston USB Drive from within Windows while on Intrepid!
(screenshot-2)

crazyness, i agree with WWSmith36, the PUEL version of Virtualbox is better, just make sure to "filter" your USB devices that you want in the setting tab.

---

### Post by wd5gnr on 2008-10-10
A few more links:

[http://forums.virtualbox.org/viewtopic.php?t=333&postdays=0&postorder=asc&start=0](http://forums.virtualbox.org/viewtopic.php?t=333&postdays=0&postorder=asc&start=0)

[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)
(plus links at the bottom of that article)

---

### Post by crazyness003 on 2008-10-12
Hey, thanks a lot guys or girls. I've thought about it and decided im gonna wait it out till 8.10 is released. Im running a beta right now and some things are a little off (some errors here and there and some services crashing, they're already reported bugs i think). I wonder if theres a better partition scheme i could use in order to save my settings and programs after each clean install of the buntu OS (thats a different story for a different day). 
But I do thank you for the insight, im sure someone else whi has a question about this will find it very helpful aswell. 

I was also wondering (since theres a download for Windows too) Could I load my Linux partition in windows (i dont know why, but if its doable...why not)? Just a curious statement.

But the concensus remains: **VirtualBox PUEL** (and not  VirtualBox OSE) is recommended for what I have in mind. And i have to download from their site, not the repos. Isin't that version closed source? Will I be flamed for using it? Who will save all the kittens? 

Since OSE is FOSS, hasent anyone generated a free fix for USB, SATA and all the other features that PUEL enables? I know its asking much, but free is better than closed, but sometimes closed is easier, i guess.

Again, thanks

---

