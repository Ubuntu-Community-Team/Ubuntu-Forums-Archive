---
title: "Precise Advice"
date: 2011-11-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-12
Fortunately my Intel MoBo allows me to disable my SATA hdd and run my IDE hdd separately. After reading a lot of forums and listening to old timers I decided it would be wise to start  working Precise from a separate HDD, in anticipation that there will be breakage (oh joy) :) With this Intel board I can run my SATA installs without cracking open my tower..

regards

---

### Post by effenberg0x0 on 2011-11-12
You can totally disable one of the HDDs in the BIOS boot devices, activate another, etc. Or simply select the preferred boot device during boot (generally the BIOS asks for the F12 key to display the boot device selection). 

If you have a eSATA or USB3, you can use a external HDD with no loss in performance. Also a good option.

I hate dual booting and switching between PCs, so there's not too many options for me: Either I risk keeping precise as the primary OS or put it in a VM (and deal with poor hardware acceleration issues in VIrtualBox and VmWare). 

I'm not sure but I think I could get PCI passthrough and real video 3D accel using KVM/Qemu? Anyone using it?

---

### Post by ventrical on 2011-11-12
I am looking to get an AB switch box or KVM to hook up two PCs. This way , no dual booting. I want to run Precise repos on a high speed tower and then switch to  another tower for stable. This will make alpha/beta testing more interesting and less hassle.

Thanks for your suggestions.

---

### Post by effenberg0x0 on 2011-11-12
I have just installed OO 64Bits and PP64Bits to VMWare Player VMs and, despite the fact that theres no 3D Acceleration for Video, I can get an amazing performance running the Ubuntu 2D Session simultaneously in the two VMs under PP as the host native OS (Unity Session). I had set each VM to use up to 4GB and 4 CPU Cores but in fact each is using more or less 1GB and CPUs are not being used more than 25%. There's virtually no impact on the host.

I made a script to auto clone the PP VM easily, so I can always have a fresh PP install to boot and test stuff and simply discard afterwards.

For tests requiring 3D Acceleration, one can use VirtualBox. [s]It doesn't have an amazing performance, but does support the GL requirements of Unity.[/s] I have created two VMs (OO64 and PP64) on VirtualBox now and both are performing Unity Sessions perfectly. I'm amazed with the performance, it's the perfect testing environment.

There's recent news about VMWare, that it is soon gonna release a new Linux Guest Video Driver that is capable of both hardware acceleration and software rendering using Galium3D. So maybe it is a good choice to stick to VMWare.

For now, anyway, it's a no go for 3D on VMWare...
```

ahsl@ahsl-VM:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
ahsl@ahsl-VM:~$ 
```...and good support on VirtualBox:
```

ahsl@AHSL-VBOX-PP:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Humper
OpenGL renderer string: Chromium
OpenGL version string:  2.1 Chromium 1.9

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
ahsl@AHSL-VBOX-PP:~$ 

```

---

### Post by kansasnoob on 2011-11-12
> **ventrical said:**
> Fortunately my Intel MoBo allows me to disable my SATA hdd and run my IDE hdd separately. After reading a lot of forums and listening to old timers I decided it would be wise to start  working Precise from a separate HDD, in anticipation that there will be breakage (oh joy) :) With this Intel board I can run my SATA installs without cracking open my tower..

regards

Could you possibly have come up with a worse title for this thread :confused:

I guess it's good to draw traffic :(

---

### Post by ventrical on 2011-11-12
> **kansasnoob said:**
> Could you possibly have come up with a worse title for this thread :confused:

I guess it's good to draw traffic :(

  I'm just a beta tester. I'm just trying to keep the flow going. I'm trying to push my hardware to the limit. I am trying to prepare myself for 'breakage' to come.  It's just too easy to get complacent .

---

### Post by ventrical on 2011-11-12
@effenberg,

 I have an olde AMD 64 AthelonX2 on an Acer Extensa but it's running in 32 bit mode. If I install VirtualBox in 32bit mode can I load the 64bit Precise in the vBox?  

As for Unity 2D .. YEAH !!  I really like it. Actually I like the smooth scrolling. I am typing this message from a USB running Precise on a Dell Inspiron B130.

---

### Post by effenberg0x0 on 2011-11-12
> **ventrical said:**
> @effenberg,

 I have an olde AMD 64 AthelonX2 on an Acer Extensa but it's running in 32 bit mode. If I install VirtualBox in 32bit mode can I load the 64bit Precise in the vBox?  

I know running a 64bit Guest in a 32Bit Host OS created some problems in the past and that it became possible some time ago, but it creates a lot of overhead, because of memory addresses translation. 64->32 32->64, etc. You also won't have a speed gain from nested paging. And you need your cpu to support virtualization extensions (AMD-V, Intel VTx), otherwise it's a no go. Check with cat /proc/cpuinfo | grep --color svm[FONT=Verdana]. There's better info here: [http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)[/FONT]

So, if I could you some advice, I would tell you to install your Host in 64bits, that way you can test 32 and 64bits without having to go through any particular issue.

**EDIT:** Maybe you should test running Ubuntu 64-bit on it first via USB or CD to check how it performs.

> **ventrical said:**
> 
As for Unity 2D .. YEAH !!  I really like it. Actually I like the smooth scrolling. I am typing this message from a USB running Precise on a Dell Inspiron B130.
IMHO you lose so little in comparison to a "3D" session, I don't know why people bother so much. The performance is really light and fast, even in standard and low-end hardware. I tested it on a VM with a single 1GHz CPU and 1GB of RAM and it ran nicely.

I'm looking forward for better ways to emulate video hardware. Now, we can enable/disable 2D and 3D support (but support is limited, as well as performance) and the amount of video memory. It would be great for software testing and development if further options could also be customized (GPU Speed and Cores, etc).

---

### Post by jerrylamos on 2011-11-13
USB hard drive running Precise Pangolin here.  Insulates the hard drive from being screwed up by unstable development release code, to a degree.

Huge warning - when doing an "install" from CD Daily build or wherever, especially near Alpha time, "unstable development install ubiquity" can and will get any number of bugs.  Development has demonstrably little interest in Ubiquity and Grub. Severe bugs persist for weeks. Or months.

Install onto a USB hard drive has even killed Windoze on my main my hard drive.  Took eons and four DVD's to re-install.  How does that happen?  /dev/sdx gets mixed up.  

On my fast tower pc, the boot IDE hard drive is /dev/sda and the SATA is /dev/sdb for Lucid Lynx LTS, Meerkat, and Narwhal.

Oneiric Ocelot has decided that the boot IDE hard drive is /dev/sdb (!) and the secondary SATA is /dev/sda. (!)  Totally switched around.  Yes I entered a Launchpad bug, and no development is interested.

Caveat emptor.

Jerry

p.s. Why any windoze around?  My wife supports a couple websites with proprietary software Dreamweaver, not available on Linux.

---

### Post by ronacc on 2011-11-13
Jerry thats exactly why I tedt on a dedicated test box and don't let a developement version of any distro anywhere near anything I actually care about ( or the first install of a release version of anything).

---

### Post by ventrical on 2011-11-13
> **jerrylamos said:**
> USB hard drive running Precise Pangolin here.  Insulates the hard drive from being screwed up by unstable development release code, to a degree.

Huge warning - when doing an "install" from CD Daily build or wherever, especially near Alpha time, "unstable development install ubiquity" can and will get any number of bugs.  Development has demonstrably little interest in Ubiquity and Grub. Severe bugs persist for weeks. Or months.

Install onto a USB hard drive has even killed Windoze on my main my hard drive.  Took eons and four DVD's to re-install.  How does that happen?  /dev/sdx gets mixed up.  

On my fast tower pc, the boot IDE hard drive is /dev/sda and the SATA is /dev/sdb for Lucid Lynx LTS, Meerkat, and Narwhal.

Oneiric Ocelot has decided that the boot IDE hard drive is /dev/sdb (!) and the secondary SATA is /dev/sda. (!)  Totally switched around.  Yes I entered a Launchpad bug, and no development is interested.

Caveat emptor.

Jerry

p.s. Why any windoze around?  My wife supports a couple websites with proprietary software Dreamweaver, not available on Linux.

 Thanks Jerrylamos,

This is exactly what I'm talking about.  It's funny . Precise  is working so great right now that I tend to forget that it is not even in alpha stage yet. Thankfully Lucid will be LTS until Apr. 2013.

---

### Post by ventrical on 2011-11-13
> **effenberg0x0 said:**
> I know running a 64bit Guest in a 32Bit Host OS created some problems in the past and that it became possible some time ago, but it creates a lot of overhead, because of memory addresses translation. 64->32 32->64, etc. You also won't have a speed gain from nested paging. And you need your cpu to support virtualization extensions (AMD-V, Intel VTx), otherwise it's a no go. Check with cat /proc/cpuinfo | grep --color svm[FONT=Verdana]. There's better info here: [http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)[/FONT]

So, if I could you some advice, I would tell you to install your Host in 64bits, that way you can test 32 and 64bits without having to go through any particular issue.

**EDIT:** Maybe you should test running Ubuntu 64-bit on it first via USB or CD to check how it performs.


IMHO you lose so little in comparison to a "3D" session, I don't know why people bother so much. The performance is really light and fast, even in standard and low-end hardware. I tested it on a VM with a single 1GHz CPU and 1GB of RAM and it ran nicely.

I'm looking forward for better ways to emulate video hardware. Now, we can enable/disable 2D and 3D support (but support is limited, as well as performance) and the amount of video memory. It would be great for software testing and development if further options could also be customized (GPU Speed and Cores, etc).

 I will install  the 64bit version on a partition. I tired to run VBox (on Acer Extensa) lastnight but no luck. 

 Untiy2D. Yup .. I agree. If someone wants to do stable buisness then just forget about compiz dazzle.

  Thanks for the Precise advice !

---

### Post by ventrical on 2011-11-13
Well. i'm almost embarassed to say  that I should have tired 64bit earlier on this AMD processor. What a difference.

@Jerry

 On 2 of my PCs I have the option in BIOS to disable the SATA drive. That means simply that I can boot from an IDE drive when SATA is off and then when SATA is enabled the IDE is disabled, therefor any negative activity from GRUB during alpha/beta testing of Precise will not affect production hdds.

  On my 64bit system I used a USB drive and removed the SATA and I am about to check if that can be disabled in BIOS also.

---

### Post by ventrical on 2011-11-13
I installed the Precise ppas ..etc... sudo updated, sudo upgraded .. ran sudo grub-update .. one package reported a problem .. and then I did a reboot and the whole system has foobarred!!

  Thankfully it was on a USB-hdd drive.

[http://www.youtube.com/watch?v=NV3IFV0Vu7w](http://www.youtube.com/watch?v=NV3IFV0Vu7w)


 I am able to get grub bootloader in Plymouth and the Recovery option seems to work but I can't get the terminal when pressing Crtl/Alt/F2 or F1 ect..

  btw .. this is a 64 bit system.

 thoughts .. anyone .. :)

---

### Post by ronacc on 2011-11-13
is this after the boot starts? if so it looks like something went wrong in /boot/grub/grub.cfg  can you post that file ? Also a very handy thing to have is a cd with supergrub disk on it . That can recover installs that update- grub misses or even a completely screwed grub install .

---

### Post by ventrical on 2011-11-13
> **ronacc said:**
> is this after the boot starts? if so it looks like something went wrong in /boot/grub/grub.cfg  can you post that file ? Also a very handy thing to have is a cd with supergrub disk on it . That can recover installs that update- grub misses or even a completely screwed grub install .

  I got terminal and yes, that file is there but I have no network.  I think it was a *grub miss* as you say.

 Thanks for the reply.

  I cannot post the grub.cfg file because I do not have a desktop or network.

---

### Post by ventrical on 2011-11-13
I got the latest grub rescue disk. (super grub is outdated).

No go!

 Thanks anyways.

 Perhaps I'll try another fresh install.

---

### Post by ronacc on 2011-11-13
I should have specified super grub2 disk as it will handle grub 2 where the original super grub disk is grub 1 .

---

### Post by ventrical on 2011-11-13
> **ronacc said:**
> I should have specified super grub2 disk as it will handle grub 2 where the original super grub disk is grub 1 .

super grub2 is now rescutux.

at least that is where I was redirected to.

The  rescutux CD detects the Precise kernel correctly, it reports "Success" but no success. still same error.

---

### Post by ronacc on 2011-11-13
maybe the problem isn't grub then , take a look at your /etc/fstab and see if the entry for your sda makes sense . and BTW what are you installing , what specific .iso and date .

---

### Post by effenberg0x0 on 2011-11-13
I just saw the YouTube video you did. You get the the boot process stuck on that message when letting the machine boot normally, that is, without selecting any different option on grub, right?

You mention it is a USB HDD. Yet, the error message you get refer to /dev/sda1, which makes no sense. /dev/sda is probably your internal HDD and this USB HDD is probably /dev/sdb. 

I would boot into recovery and run fdisk -l to get an idea of how Linux is seeing your units. Then I'd backup /boot/grub/grub.cfg to /boot/grub/grub.cfg.backup and edit /boot/grub/grub.cfg with nano to set proper units identifiers. 

You probably will have to replace wrong stuff (like /dev/sda and /dev/sda1) for proper names (/dev/sdb and /dev/sdb1).

**EDIT:** Not sure, but first thing in recovery you might need to remount / as rw and set /boot/grub/grub.cfg rw for you to be able to save your changes to it. Just run mount when you login to make sure / is rw.

---

### Post by effenberg0x0 on 2011-11-13
Still thinking about it, I remembered it would be interesting to check what you have for 
cat /proc/cmdline. You'll get something like:

```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=5a949780-1e2d-4119-a00f-68d24618e28a ro quiet splash vt.handoff=7

```If you get a block id like UUID="5a949780-1e2d-4119-a00f-68d24618e28a", you can run
sudo blkid to get a list of which partition is labeled with each block id... you will get something like:

```
$ sudo blkid
[sudo] password for ahsl: 
/dev/sda1: UUID="5a949780-1e2d-4119-a00f-68d24618e28a" TYPE="ext4" 
/dev/sda2: UUID="f0e83c44-b038-4b3d-99a8-3d8edb7e294b" TYPE="swap" 
/dev/sdb1: UUID="c03a4fd5-c162-48ce-9d91-d549a8f02b64" TYPE="ext4" 
/dev/sdc1: UUID="5138-3664" TYPE="vfat" 

```I am convinced grub is looking in the wrong place for the wrong partition. In my example above, you can see that grub boot line is right, because it's pointing to /dev/sda1, which indeed is a partition to boot from. If your USB HDD is actually /dev/sda or /dev/sdb, which would depend on your BIOS settings (primary, secondary, etc - if and how it exports units when you boot from USB is unknown to me), grub config file has to match it exactly.

---

### Post by ventrical on 2011-11-14
> **ronacc said:**
> maybe the problem isn't grub then , take a look at your /etc/fstab and see if the entry for your sda makes sense . and BTW what are you installing , what specific .iso and date .


ubuntu-11.10-desktop-amd64.iso

---

### Post by ventrical on 2011-11-14
> **effenberg0x0 said:**
> I just saw the YouTube video you did. You get the the boot process stuck on that message when letting the machine boot normally, that is, without selecting any different option on grub, right?

You mention it is a USB HDD. Yet, the error message you get refer to /dev/sda1, which makes no sense. /dev/sda is probably your internal HDD and this USB HDD is probably /dev/sdb. 

I would boot into recovery and run fdisk -l to get an idea of how Linux is seeing your units. Then I'd backup /boot/grub/grub.cfg to /boot/grub/grub.cfg.backup and edit /boot/grub/grub.cfg with nano to set proper units identifiers. 

You probably will have to replace wrong stuff (like /dev/sda and /dev/sda1) for proper names (/dev/sdb and /dev/sdb1).

**EDIT:** Not sure, but first thing in recovery you might need to remount / as rw and set /boot/grub/grub.cfg rw for you to be able to save your changes to it. Just run mount when you login to make sure / is rw.


What I was trying to do was set up  Dumb Terminal on an old IDE drive using my USB to IDE&SATA converter cable. (works every time except this time). So, to protect my regular SATA HDD I removed it. So there is only the CD/DVD and the USB converter to 20GB Maxtor IDE.

Everything was working beautifully. I converted the ppas to Precise. All went well. Then:

sudo grub-update

 and that is what did it in.

  I'll try your advice/suggestions on this. I could easily do a fresh install ... but it is better to get skills at working  these problems manually. Perhaps it is  a Precise bug but I have no way of confirming this.

I'll get on this prob soon.

---

### Post by ventrical on 2011-11-14
> **effenberg0x0 said:**
> I just saw the YouTube video you did. You get the the boot process stuck on that message when letting the machine boot normally, that is, without selecting any different option on grub, right?



 After I added the Precise ppas and ran -sudo grub-update, it did not register the Precise kernel in the grub bootloader. Just the 3.0.0-12 kernel of Ocelot.

 So I have the Grub Bootloader presenting me with only the standard options of Recovery, 3.0.0-12 kernel, memtest and etc..

also ... when I am at #root terminal I have no network so I can't do any  apt-get install commands or update commands.

---

### Post by ventrical on 2011-11-14
> **sigirl said:**
> especially near Alpha time, "unstable development install ubiquity" can  and will get any number of bugs.  Development has demonstrably little  interest in Ubiquity and Grub. Severe bugs persist for weeks. Or months.


Hmmmm.. perhaps I am doing somthing wrong here then because what i am doing (or what I think that everyone else had been doing) is following the instructions  in the sticky about setting up Precise.So I am downloading Oneiric Ocelot and then editing the sources list so  I have the PP kernels and repos. as instructed here:

[http://ubuntuforums.org/showpost.php?p=11338561&postcount=1](http://ubuntuforums.org/showpost.php?p=11338561&postcount=1)

---

### Post by ventrical on 2011-11-14
> **effenberg0x0 said:**
> 

**EDIT:** Not sure, but first thing in recovery you might need to remount / as rw and set /boot/grub/grub.cfg rw for you to be able to save your changes to it. Just run mount when you login to make sure / is rw.

 I ran this, then it presented me with an Update Grub option. i did so and got the system  back !

I think I have some unmet depends also because  a warning tells me: error-broken count >0 so I'll try to run synaptic again.

Thanks all.

---

### Post by effenberg0x0 on 2011-11-14
> **ventrical said:**
> Hmmmm.. perhaps I am doing somthing wrong here then because what i am doing (or what I think that everyone else had been doing) is following the instructions  in the sticky about setting up Precise.So I am downloading Oneiric Ocelot and then editing the sources list so  I have the PP kernels and repos. as instructed here:

[http://ubuntuforums.org/showpost.php?p=11338561&postcount=1](http://ubuntuforums.org/showpost.php?p=11338561&postcount=1)

So am I, and that is irrelevant in your case. When it comes to APT, either you manage to get the packages you need or you don't, that's as far as it goes. You have a grub/partition problem.

What I want to understand is this: 
- Unless I turn off my HDD in BIOS or disconnect it, it always is /dev/sda, no matter what. Even if I boot from USB, my HDD (not used) is there as /dev/sda and the usb will be /dev/sdb. So I would say that if you have installed grub to the disk SDB and the system partition is SDB1, that would be the expected behavior and you should go check the grub.cfg in the USB-IDE HDD, which probably is looking elsewhere.

Now, is it possible that your BIOS understand that this USB-IDE converter is in fact an HDD, not a USB, throw it as a primary and and calls it SDA? I'm not sure how it works and would guess it's BIOS dependent. For example, in my BIOS, if I boot with a USB stick attached, I can set the BIOS to emulate that the stick is any of these options: ATAPI CD-ROM, IDE HDD, SATA HDD, USB Drive. I can have it as a primary HDD, a secondary cd-rom, whatever I want. But most BIOS don't have this explicit option. What do they do then? I don't know.  

Only way to know all this is to boot to recovery and call fdisk -l to see how things are being informed from BIOS to Linux, that is, which are units available and their names. 

Only by looking at this information, you'll really be able to make sure your grub.cfg is or is not correct and fix it to whatever the units are named. fdisk will show you the size of the units, as well as if they have boot partitions. It will be easy to identify which is which.

Example: Maybe the internal HDD grub was updated on update, not the one on the external HDD.

---

### Post by effenberg0x0 on 2011-11-14
> **ventrical said:**
> I ran this, then it presented me with an Update Grub option. i did so and got the system  back !

I think I have some unmet depends also because  a warning tells me: error-broken count >0 so I'll try to run synaptic again.

Thanks all.

Ah, cool, now we can see by the size od the disk that it is in fact running on the USB. Pay attention to future grub updates, to make sure that grub is updating the USB external HDD, not the internal one, and you'll be fine. 

How's the speed when running from a USB-IDE adapter?

---

### Post by ventrical on 2011-11-14
I tried to fix broken pkgs and got this:

---

### Post by ventrical on 2011-11-14
I tired to Unmark that pkg but it wants to take a bunch of stuff with it. I guess I need some precise advice :)

---

### Post by effenberg0x0 on 2011-11-14
> **ventrical said:**
> I tired to Unmark that pkg but it wants to take a bunch of stuff with it. I guess I need some precise advice :)

Me too, same package, same file. I simply removed it. You may want to be more careful than me and move it to your home directory as a backup, etc. I killed the thing.

sudo rm -rf  /usr/share/doc/name of that gz
sudo apt-get clean
sudo apt-get update 
sudo apt-get upgrade

---

### Post by effenberg0x0 on 2011-11-14
Another advice: If later today you start getting serious dependency errors related to libjack-jackd2-0, apt-get can't get past it. apt-get will remove pulseudio, mess your system because of this beast if you force it. You have to run aptitude update and it will offer possible solutions, as usual. I chose the second solution and it's solved.

---

### Post by ronacc on 2011-11-14
sorry it took me awhile to get back, I shudown and went to bed after my last post . I'm glad effenberg0x0 jumped in his knowledge of tech support far exceeds mine I'm just a hobbyist that don't even work in tech . Go with his advice . I'm glad you got your system back .

---

### Post by effenberg0x0 on 2011-11-14
> **ronacc said:**
> sorry it took me awhile to get back, I shudown and went to bed after my last post . I'm glad effenberg0x0 jumped in his knowledge of tech support far exceeds mine I'm just a hobbyist that don't even work in tech . Go with his advice . I'm glad you got your system back .

I've seen you helping so many people here, and always with coherent ideas. I wouldn't imagine that IT is not your field of work, to be honest :)

---

### Post by ventrical on 2011-11-14
> **ronacc said:**
> sorry it took me awhile to get back, I shudown and went to bed after my last post . I'm glad effenberg0x0 jumped in his knowledge of tech support far exceeds mine I'm just a hobbyist that don't even work in tech . Go with his advice . I'm glad you got your system back .

Thanks very much ronacc.  You gave good advice because now I know about the rescutux CD. It *did* recognize the PP install but probably somthing I did wrong.

Thanks again .. you are a great helper.

---

### Post by ventrical on 2011-11-14
> **effenberg0x0 said:**
> i've seen you helping so many people here, and always with coherent ideas. I wouldn't imagine that it is not your field of work, to be honest :)


++!

:)

---

### Post by ventrical on 2011-11-14
> **effenberg0x0 said:**
> Another advice: If later today you start getting serious dependency errors related to libjack-jackd2-0, apt-get can't get past it. apt-get will remove pulseudio, mess your system because of this beast if you force it. You have to run aptitude update and it will offer possible solutions, as usual. I chose the second solution and it's solved.

The update went real smooth. Thanks again!

I'll be keeping an eye on it.

---

### Post by philinux on 2011-11-14
> **effenberg0x0 said:**
> Another advice: If later today you start getting serious dependency errors related to libjack-jackd2-0, apt-get can't get past it. apt-get will remove pulseudio, mess your system because of this beast if you force it. You have to run aptitude update and it will offer possible solutions, as usual. I chose the second solution and it's solved.

I usually use aptitude update && aptitude safe-upgrade and full-upgrade when needed.

I saw your warning of possible errors. Anyway just chrooted in and updated, 109 updates too, without an error. :D

---

### Post by ronacc on 2011-11-14
keep in mind effenberg0x0 's advice about checking the blkid and making sure that update grub wrote the correct one for your boot device . I have more than once seen the installer get it wrong , also during install make sure you are installing to the device you think you are ,the partitioner ubiquity uses does not report drive letters the same as gparted  so if you have a multi drive box it can get confusing .

---

### Post by ventrical on 2011-11-14
> **ronacc said:**
> keep in mind effenberg0x0 's advice about checking the blkid and making sure that update grub wrote the correct one for your boot device . I have more than once seen the installer get it wrong , also during install make sure you are installing to the device you think you are ,the partitioner ubiquity uses does not report drive letters the same as gparted  so if you have a multi drive box it can get confusing .


  The reason I started this thread was that I was reading often enough about other old time members on the forums talking about 'breakage' during alpha/beta testing. With Oneiric I didn't seem to have many problems and made a smooth transition on systems with multiple installs. THIS 64bit system with Precise I wanted to be able to run with a USB drive. That means I removed the regular HDD so, when I update or anything to do with GRUB then it will not affect my stable installs because >I just remove the drive. It is really not that much extra work.

  As with most other testers here .. I m expecting breakage.. been there , done that!! so I just like to keep a few ticks in my vest pocket so to speak :)  I more or less like to run hardware to the limit but I think there is a lot of wise advice to have backups on hand just in case there is a really bad string during alpha or beta testing.

btw .. here is that grub.cgf file...

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.1.0-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
    linux    /boot/vmlinuz-3.1.0-2-generic root=UUID=ac701ee0-b3bf-4264-ab92-ecfa611c6bec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.1.0-2-generic
}
menuentry 'Ubuntu, with Linux 3.1.0-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
    echo    'Loading Linux 3.1.0-2-generic ...'
    linux    /boot/vmlinuz-3.1.0-2-generic root=UUID=ac701ee0-b3bf-4264-ab92-ecfa611c6bec ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.1.0-2-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ac701ee0-b3bf-4264-ab92-ecfa611c6bec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ac701ee0-b3bf-4264-ab92-ecfa611c6bec ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ac701ee0-b3bf-4264-ab92-ecfa611c6bec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```


thanks again for your suggestions.

---

### Post by ventrical on 2011-11-14
> **effenberg0x0 said:**
> Still thinking about it, I remembered it would be interesting to check what you have for 
cat /proc/cmdline. You'll get something like:

```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=5a949780-1e2d-4119-a00f-68d24618e28a ro quiet splash vt.handoff=7

```If you get a block id like UUID="5a949780-1e2d-4119-a00f-68d24618e28a", you can run
sudo blkid to get a list of which partition is labeled with each block id... you will get something like:

```
$ sudo blkid
[sudo] password for ahsl: 
/dev/sda1: UUID="5a949780-1e2d-4119-a00f-68d24618e28a" TYPE="ext4" 
/dev/sda2: UUID="f0e83c44-b038-4b3d-99a8-3d8edb7e294b" TYPE="swap" 
/dev/sdb1: UUID="c03a4fd5-c162-48ce-9d91-d549a8f02b64" TYPE="ext4" 
/dev/sdc1: UUID="5138-3664" TYPE="vfat" 

```I am convinced grub is looking in the wrong place for the wrong partition. In my example above, you can see that grub boot line is right, because it's pointing to /dev/sda1, which indeed is a partition to boot from. If your USB HDD is actually /dev/sda or /dev/sdb, which would depend on your BIOS settings (primary, secondary, etc - if and how it exports units when you boot from USB is unknown to me), grub config file has to match it exactly.
dale@dale-Extensa-4420:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.1.0-2-generic root=UUID=ac701ee0-b3bf-4264-ab92-ecfa611c6bec ro quiet splash vt.handoff=7
dale@dale-Extensa-4420:~$ sudo blkid
[sudo] password for dale: 
Sorry, try again.
[sudo] password for dale: 
/dev/sda1: UUID="ac701ee0-b3bf-4264-ab92-ecfa611c6bec" TYPE="ext4" 
/dev/sda5: UUID="e02b88c8-bc85-4986-82d1-027f527bbd33" TYPE="swap" 
dale@dale-Extensa-4420:~$

---

### Post by effenberg0x0 on 2011-11-14
> **philinux said:**
> I usually use aptitude update && aptitude safe-upgrade and full-upgrade when needed.

This is the safest way. When I was warned to rely more on aptitude than on apt-get in the past, I always thought that was some kind of silly myth. That was until aptitude mysteriously saved the day like 10 times, now I believe it completely :) 

> **philinux said:**
> 
I saw your warning of possible errors. Anyway just chrooted in and updated, 109 updates too, without an error. :D 

Generally when I finish a install from ISO, I just update & upgrade using the new sources, remove what I don't use (network-manager, some other stuff) and add a couple apps I use. There's something about this "basic" apps I add/remove that is consistently creating a crazy dependency situation. I had more than five times in the last week in real and virtual machines, but I can't identify what it is...  At some point, when I try to update & upgrade I get a "*E*: Internal Error, Could not *early remove* libjack-jackd2-0" and update becames impossible. Clearing the cache, etc won't fix it. Removing it removes things like pulseaudio, libc6, etc. It breaks the setup beautifully. A solution proposed by aptitude removes a bunch of packages and reinstall most of them and fixes it. I couldn't understand it yet.

---

### Post by seeker5528 on 2011-11-14
> **ventrical said:**
> super grub2 is now rescutux.

at least that is where I was redirected to.

The  rescutux CD detects the Precise kernel correctly, it reports "Success" but no success. still same error.

supergrub2 and rescatux, while related are two different things....

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Whichever I click on is the download I get.

If you followed a link on some other site, that other site may give preferential treatment to rescatux instead of sending you to the download you thought you should get.

Rescatux does seem to be where the bulk of the developers effort is going though, seeing how the supergrub2 disk seems not to have been updated since 2010-08-20. 

Later, Seeker

---

### Post by ventrical on 2011-11-15
> **seeker5528 said:**
> supergrub2 and rescatux, while related are two different things....

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Whichever I click on is the download I get.

If you followed a link on some other site, that other site may give preferential treatment to rescatux instead of sending you to the download you thought you should get.

Rescatux does seem to be where the bulk of the developers effort is going though, seeing how the supergrub2 disk seems not to have been updated since 2010-08-20. 

Later, Seeker

  Thanks for your reply seeker.  Yes, I had seen that and so I just naturally assumed that there may be breakage with supergrub2 or that it may not be compatible  with Precise/Oneiric, however , for the sake of interest and <precision>  :) I''ll take a look at supergrub2.

  Thanks very much for the link.

---

