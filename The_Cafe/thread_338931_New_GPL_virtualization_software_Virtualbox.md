---
title: "New GPL virtualization software: Virtualbox"
date: 2007-01-15
forum: The Cafe
---

### Post by imagine on 2007-01-15
Hi,

InnoTek rereleased his virtualization software Virtualbox under the GPL today ([press statement](http://www.virtualbox.org/wiki/News)). Before, the application was not available to to endusers.
Virtualbox supports Linux and Windows both as client and host systems. OpenBSD and OS/2 are also supported as clients. It works and looks similar to VMware and although it's not quite as powerful as VMware Workstation yet, it still looks promising.

There are also Ubuntu Dapper and Edgy packages available on their website (at least as long as the site doesn't get /.ed): [http://www.virtualbox.org](http://www.virtualbox.org)

Edit: Sorry, the DEB-packages are only available for the commercial edition, so the GPLed version has to be built from source.

---

### Post by zugu on 2007-01-15
Moderator, please delete.

---

### Post by Aetherius on 2007-01-15
cheers for this, I'm gonna give it a spin when I get home


aeth

---

### Post by darkninja on 2007-01-15
Nice find!

This program looks very well done!

---

### Post by neoflight on 2007-01-15
does anyone has a test report on this one yet? i am eager to try it out....
just found out about virtualbox from slashdot....

---

### Post by TheRingmaster on 2007-01-15
> **zugu said:**
> Moderator, please delete.


he is not selling anything. he is just telling us about this new software.

---

### Post by jpeddicord on 2007-01-15
FYI: You can download the DEB packages and use them without restriction, they seem to work fine here.

And a word of warning for GNOME users: It uses Qt.

---

### Post by lyceum on 2007-01-15
> **jacobmp92 said:**
> FYI: You can download the DEB packages and use them without restriction, they seem to work fine here.

And a word of warning for GNOME users: It uses Qt.

I am not sure what that means, should I use KDE if I want to check this out?

---

### Post by maddog39 on 2007-01-15
It wont make any difference if its made for Qt, since all KDE/Qt apps still run natively in GNOME.  I'm curious if this will emulate an x86 processor, because I'm on PowerPC.

---

### Post by maniacmusician on 2007-01-15
I can't get it to open my virtual machines that already exist...I thought the standard for Virtual machines was the vmx extension? and that disks were vmdk? 

When I try to add a hard drive, it insists that the extension should be .vdi or something. 

I'm sure it's good software, but I don't want to set up my various VM's over again.

If someone knows how to do this, post it please.

---

### Post by gapplewagen on 2007-01-15
I was able to get the .deb to install but when trying to run a VM I'm getting:

 Error inserting vboxdrv (/lib/modules/2.6.17-10-386/misc/vboxdrv.ko): Invalid module format
 

Not sure why just yet.  /usr/src/linux is pointed to /usr/src/linux-headers-2.6.17-10-386 and uname -a says:

2.6.17-10-386


Anyone had similar problems?

---

### Post by maniacmusician on 2007-01-15
I tried creating a VM and I get

> 

VirtualBox kernel driver not accessible, permission problem.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

### Post by kevinf311 on 2007-01-15
I got a similar vboxdrv error when installing, but the program started up. I went through the "New" wizard, but it never prompted me to install the OS. When I clicked on the session, it yelled at me for not having a kernel to start. ](*,) 

I'll keep messing around with it to see if I can get it to work.

---

### Post by maniacmusician on 2007-01-15
I was trying to install from an iso. It never even got to the booting from CD part, that message comes up as soon as I start the VM. Same thing as you I think. I'd love to get this working too....

hmm it's talking about a file in /home/vbox/... but nothing like that exists on my computer. it shouldnt in the VM either, since its empty. where is it trying to look?

---

### Post by gapplewagen on 2007-01-15
Mine is similar but does not complain about permissions, but that the driver isn't installed.  I can't seem to get it to load the module.  The documentation has a section on support for external Kernel modules but the steps they provide aren't working for me.  Fails on the first step (make defconfig)... says there is no arch/i386/defconfig.

Error from virtualbox when starting:

VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by maniacmusician on 2007-01-15
w00t, I got it.

After you add your user to the vboxusers group,

> usermod -G vboxusers -a <userid/username>

You've got to log out and then log in again. It should now work.

---

### Post by gapplewagen on 2007-01-15
I was able to fix mine too.  Here was the issue (or what I think it was):

When I originally installed the .deb my /usr/src/linux was pointed to /usr/src/linux-headers-2.6.17-10-generic.  So when I ran the deb it said:

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log

That's fine and all but my uname -a output said I was running 2.6.17-10-386.  So I changed the symlink for /usr/src/linux to point to /usr/src/linux-headers-2.6.17-10-386 and retried the whole install.  After multiple "apt-get remove virtualbox" and "dpkg --purge virtualbox" I was still getting the same error.  The problem was that the apt-get remove and dpkg --purge was not removing the module that it built from the 2.6.17-10-generic headers.  so I did this:

sudo rm -f /lib/modules/2.6.17-10-386/misc/vboxdrv.ko

Then I did the apt-get remove and dpkg --purge on the virtualbox package once more, installed the .deb again with the proper symlink to my current kernel and it worked.  

Hope this helps.

---

### Post by maniacmusician on 2007-01-15
I like this software way better than vmware. and its open source! 

I just wish there was a way to use existing .vmx machines! I have a bunch of them that I use regularly and I can't just reinstall all of them and lose the data...

---

### Post by musther on 2007-01-15
I changed my 'linux' symlink and got a kernal module, but now I have the permissions issue:

```

VirtualBox kernel driver not accessible, permission problem.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

The thing is '/home/vbox/vbox/src/VBox/VMM/VM.cpp' doesn't exist, I've done a search and can't even find VM.cpp.  The other odd thing is that virtualbox works fine when I run it as root.  Anyone know what the permission issue is?

---

### Post by gapplewagen on 2007-01-15
> **musther said:**
> I changed my 'linux' symlink and got a kernal module, but now I have the permissions issue:

The thing is '/home/vbox/vbox/src/VBox/VMM/VM.cpp' doesn't exist, I've done a search and can't even find VM.cpp.  The other odd thing is that virtualbox works fine when I run it as root.  Anyone know what the permission issue is?

As maniacmusician said, the permission issue is fixed by:

```

usermod -G vboxusers -a <userid/username>

```

---

### Post by maniacmusician on 2007-01-15
You've also got to log out and back in. Or just Ctrl + Backspace to restart all of X and give your system a nice flush.

---

### Post by gapplewagen on 2007-01-15
> **maniacmusician said:**
> I like this software way better than vmware. and its open source! 

I just wish there was a way to use existing .vmx machines! I have a bunch of them that I use regularly and I can't just reinstall all of them and lose the data...

I agree... it is so much easier and streamlined than vmware.

---

### Post by maniacmusician on 2007-01-15
It has a better full screen function. VMWare fullscreen would f*ck my resolution up something bad, and I'd have to restart X. with this, I can have it fullscreening on one side of the cube.

gapplewagen, have you installed the "Guest Additions"? They include mouse integration, and higher resolutions. kickass. Fullscreen is a blast now.

I have to recreate all my VMs though! [cries]

---

### Post by gapplewagen on 2007-01-15
> **maniacmusician said:**
> It has a better full screen function. VMWare fullscreen would f*ck my resolution up something bad, and I'd have to restart X. with this, I can have it fullscreening on one side of the cube.

gapplewagen, have you installed the "Guest Additions"? They include mouse integration, and higher resolutions. kickass. Fullscreen is a blast now.

I have to recreate all my VMs though! [cries]

I haven't messed with full screen just yet.  I only got as far as installing XP and checking to make sure networking works fine via wifi on the laptop.  Everything runs great so far.  I'm going to play with it more tomorrow.

---

### Post by musther on 2007-01-15
I've tried that too, I'm user 'musther' so I issued (as root)

```
usermod -G vboxusers -a musther
```

Didn't change anything.

---

### Post by maniacmusician on 2007-01-15
hello good sir, are you running 6.06? I've been having a discussion with someone in #vbox@freenode and he's having the same problem. I think he fixed it with 

> chmod 666 /dev/vboxdrv

apparently dapper presents some very weird permissions issues.

---

### Post by gapplewagen on 2007-01-15
> **maniacmusician said:**
> gapplewagen, have you installed the "Guest Additions"? They include mouse integration, and higher resolutions. kickass. Fullscreen is a blast now.

Ok so I couldn't wait until tomorrow and gave it a shot tonight.  This is great.  The mouse integration is 200% better than having to hit the right control key every time I want my mouse back.  I'm very impressed so far.

---

### Post by maniacmusician on 2007-01-16
hehe :) It's owning VMWare. 

Can't wait to get my Core 2 Duo + Feisty Fawn = true hardware virtualization!

wait, Feisty is using the new kernel with the virtualization features right?

---

### Post by musther on 2007-01-16
Ah ha, that worked, but I'm running 6.10, a clean install, not an upgrade.  Hmm.

---

### Post by maniacmusician on 2007-01-16
well thats weird. OF course that would work because that allows pretty much everyone to use that driver I think. But you being a user of vboxusers shouldve been enough. A bug I suppose.

---

### Post by kverde on 2007-01-16
This is nice...  any tips on getting the host's CDROM drive to show up?  The pull-down box is empty even though I have a mounted CDROM in PC.

---

### Post by maniacmusician on 2007-01-16
> **kverde said:**
> This is nice...  any tips on getting the host's CDROM drive to show up?  The pull-down box is empty even though I have a mounted CDROM in PC.
For some reason, the drive doesn't show up if mounted. unmount the CD from your system and try again.

Sheesh I'm getting to be an expert with this thing. That's what I get for spending the whole night in the #vbox channel at freenode. Saw plenty of tech support transactions.

---

### Post by Onyros on 2007-01-16
I like it... I like it a lot. Performance on my laptop is (already!) way better than VMWare's. It still has a few bugs, but I've had a great and fluid experience up until now.

In order to use the CDROM, I had to use an ISO file first, and only after did it recognize the drive. I've had no luck with USB drives, though. I can't connect my pendrive in Virtualbox, which makes for quick & dirty file transfers on the go to be a little harder right now.

Anyone had luck with those?

---

### Post by maniacmusician on 2007-01-16
> **Onyros said:**
> I like it... I like it a lot. Performance on my laptop is (already!) way better than VMWare's. It still has a few bugs, but I've had a great and fluid experience up until now.

In order to use the CDROM, I had to use an ISO file first, and only after did it recognize the drive. I've had no luck with USB drives, though. I can't connect my pendrive in Virtualbox, which makes for quick & dirty file transfers on the go to be a little harder right now.

Anyone had luck with those?
I think USB support is in the works? I dunno.

You should really get on their irc channel and ask there. #vbox@freenode.net

I dont see an option for USB drives either.

---

### Post by Onyros on 2007-01-16
It has one, but you have to configure the specifics of each one you insert and want available.

I found a better solution, one that was quite problematic with VMWare... I set up a share on the host which is available on the guest, and it works like a charm.

I typed the following at the terminal

```
VBoxManage sharedfolder add "VM Name" -name "sharename" -hostpath "home/xxxx/folder"
```

which determines the folder on the host you want accessible on the guest.

And then, as I had installed Windows Professional (I need QuarkXpress, InDesign and other Windows programs available quickly), I just enabled the shared folder with a simple

```
net use x: \\vboxsvr\sharename
```

where x: is the drive letter you want your shared folder to be accessed through.

In Linux, it should be something like

```
mount -t vboxsf [-o OPTIONS] sharename mountpoint
```

This is a serious contender to VMWare, really. I'm utterly surprised with the performance. I tried Super PI on the guest, again with Windows XP Professional, and got a very respectable 40 seconds on the 1M test. Taking into account that my laptop has a 760 Pentium M inside (2.0GHz, 2MB cache L2), with 1024MB of DDR2 RAM... that's an incredible result, because running Windows natively the result is around 38 seconds. That's a 2 second degradation in performance... and I have 256MB available to my guest OS. W-O-W.

I'm speechless, really.

---

### Post by maniacmusician on 2007-01-16
cool. If you have time, you should write a more detailed how-to on how to set up that usb drive (that would for for any kind of storage device, really), and send the link my way. I'd love to use include it as part of a guide eventually.

unfortunately, it's not giving me much performance...I don't know why. It seems even slower than vmware for me. I must be doing something wrong.

---

### Post by Onyros on 2007-01-16
Strange... probably something to do with your setup? I currently have a mem usage of 557M on my host system, which accounts for 55% of available memory (1024MB of DDR2 RAM), so I imagine anything less than 1GB of RAM may be problematic.

BTW, how did you setup the virtual drive (fixed-size >>>>> dynamically expanding file, in terms of I/O access). It has influence on performance, just like it has on VMWare. Also, until you install the Virtualbox Guest Additions performance may also be quite shaky.

---

### Post by maniacmusician on 2007-01-16
I have Guest Additions installed.

I used a dynamically expanding file. But changing this now would be a pain, I'd have to install again...(that's all three derivates of ubuntu on one installation). Does it make that big of a difference? Because I was pretty slow.

I have 1.5 GBs of RAM, but this computer is really bad at caching and retrieving from cache, so my RAM is slow sometimes.

to the guest system, I assigned 432MB of memory and 14MB of video memory.

its a mystery to me.

---

### Post by zugu on 2007-01-16
> **TheRingmaster said:**
> he is not selling anything. he is just telling us about this new software.

Sorry, I was referring to my post, not to this thread.

I'll give Virtualbox a try, we need a good open source alternative to VMWare. I know there's Xen and others, but it seems to me that Virtualbox is more VMWare-like that the other alternatives.

Cheers.

---

### Post by Onyros on 2007-01-16
maniac, I tested a config with a dynamically sized file... the degradation in performance was incredible. It probably is the bottleneck in your Virtualbox usage. ;)

Xen is a great product as well, but Virtualbox is virtualization for the masses; and whereas Xen needs a processor with VT capabilities built-in to run Windows, both Virtualbox and VMWare don't.

I remain impressed with Virtualbox. I'm gonna give it a test drive on a Pentium III 800 MHz with 512MB of RAM :P

Pray for it, hehe

---

### Post by ago on 2007-01-16
How does it compare to QEMU with kqemu module?

---

### Post by gapplewagen on 2007-01-16
I have mine set up to run Win XP on a dynamic file with 192MB RAM and 8MB video and it actually runs fine.  I accepted the full defaults from the XP suggestions just to see how it would act.  It's not blazingly fast but it's usable for what I need Windows for (Quickbooks and only Quickbooks).  I'm thinking about bumping up the RAM a bit though.  This actually may make me buy more RAM for my laptop.  I'm so sick of dual booting just to track the books and this is so much easier than vmware.

---

### Post by maniacmusician on 2007-01-16
haven't tried qemu personally but I'm hearing that it kills qemu and vmware both in terms of performance; as long as you use a fixed size file. I'm going to try running it on this junker at school....P4 2.04 GHz with a 512kb cache with 256MB of RAM. bring it on!

---

### Post by maniacmusician on 2007-01-16
> **gapplewagen said:**
> I have mine set up to run Win XP on a dynamic file with 192MB RAM and 8MB video and it actually runs fine.  I accepted the full defaults from the XP suggestions just to see how it would act.  It's not blazingly fast but it's usable for what I need Windows for (Quickbooks and only Quickbooks).  I'm thinking about bumping up the RAM a bit though.  This actually may make me buy more RAM for my laptop.  I'm so sick of dual booting just to track the books and this is so much easier than vmware.
hey try using a fixed size file; you may get the blazing fast you're looking for. and if you up it to 256 you'll probably be satisfied.

---

### Post by Enverex on 2007-01-16
Unless it has passthrough support for devices other than USB and/or supports 3D accelleration properly then it's not really any different than VMWare or QEmu. We need things with benefits, not more of the same :(

---

### Post by ago on 2007-01-16
By the way 2.6.20 (which will be in Feisty) will support kernel level virtualization, which uses both full virtualization (requiring new processors) and paravirtualization (should be in latest patches). kvm runs a modified version of qemu for the userspace tools but I bet that virtualbox can be modified to fully use kvm. This should further improve performance, particularly with new processors.

---

### Post by Onyros on 2007-01-16
> **maniacmusician said:**
> haven't tried qemu personally but I'm hearing that it kills qemu and vmware both in terms of performance; as long as you use a fixed size file. I'm going to try running it on this junker at school....P4 2.04 GHz with a 512kb cache with 256MB of RAM. bring it on!It does more than just kill VMWare and qemu in terms of sheer speed... it obliterates them.

qemu I've always found too slow to be usable; I used VMWare up until now, but guess what... It's now replaced, deleted, gone.

BTW, it's not more of the same... It's faster AND open source. So, taking into account the community WILL start looking at it with interest, you can always expect it to become even better than it already is. And, at least for me, it already surpasses VMWare by far. In the end, performance does it.

It's not just a matter of it being open source now, and all: I'm not that kind of user, I use whatever I find better suits my needs, regardless of licensing (e.g., Opera vs Firefox, I love the first and don't even use the latter, prefer Epiphany & dillo as alternative browsers).

---

### Post by Enverex on 2007-01-16
QEmu is open source but I don't see packs of developers jumping on it to make it amazing, as you said it was too sow to be usable...

---

### Post by ago on 2007-01-16
QEmu is acceptable in my experience when kqumu module is used. Unfortunately this module is not open source. Now it is less relevant, since virtualbox offers a full FOSS solution, but also because kvm+qemu module has performances very close to qemu+kqemu. I was just curious to know how virtualbox compares to kqemu, since I am not on a Linux machine and cannot try that.

> QEmu is open source but I don't see packs of developers jumping on it to make it amazing
They are. But because of kvm, which in turns uses quemu in userland. The kvm devs in the kml seem really productive recently and I would expect KVM to progress extremely rapidly (supposedly it is already very good but I have not tried it yet). The only question is whether Virtualbox will be adapted to use kvm or not.

See this article [http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html](http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html)

---

### Post by EdThaSlayer on 2007-01-16
Is it easier to use than VMware? I hope it is...
Nice find by the way! :)

---

### Post by maniacmusician on 2007-01-16
it is definitely easier than vmware.

It's unfair to say that it's more of the same; it's a brand new project, and it already has most of the features that are in VMware. It will continue to grow fast (because it started out great) and I think it will be THE virtualization software of choice, because it's just simpler to use and more efficient than anything else. Try it out at least. To give it a fair shot, try it on the Feisty kernel when it's comeplete. If you happen to get full virtualization, you'll be blown away, period.

I don't work for them or anything;  I'm just saying, this is one of the best apps I've seen in a while.

---

### Post by -Rick- on 2007-01-16
Looks nice and all, but guest OS support doesn't seem to coop with Qemu or VMWare. I've tried Knoppix, OpenBSD 3.9 and Syllable 0.6.2 and only Knoppix would boot.

I'll stay with vmplayer for a little longer :)

---

### Post by rdd on 2007-01-16
Comparing Qemu and VirtualBox: Qemu with KQemu is WAY slower. Tried it ony my girlfriends computer. She had a qemu machine for a program she needs for her studies and it was barely usable. Now I moved it to VirtualBox and its a blast. 

A lot quicker and really easy to set up.

I am very impressed. An interesting question though is, whether there will be a fork of VirtualBox starting out on the pure GPL part of it.

---

### Post by janmartin on 2007-01-16
Hi all,

I had the same problem that the **VBoxLinuxAdditions.iso** did not show up in the guest. All I got was an empty CDRom drive.
Anyway I uploaded the file from my host to webspace, then downloaded from the guest again. Not nice, but worked.
I then mounted the file and run **sudo sh ./VBoxLinuxAdditions.run  all** which leads to this output:

```
jan@jan-virtual:~/a$ sudo sh ./VBoxLinuxAdditions.run  all
Verifying archive integrity... All good.
Uncompressing VirtualBox 1.3.2 Guest Additions for Linux installation.....................................................................................................
VirtualBox 1.3.2 Guest Additions installation
Checking the setup of your guest system...
Please install GNU make on your guest system.
Please install the header files for your current kernel.
Please install the GNU compiler on your guest system.
Problems were found which would prevent the Guest Additions from installing.
Please correct these problems and try again.
```

The guest is Ubuntu Dapper Drake 6.06, What packages do I need to install now?

Anyone have a few 
**sudo apt-get install ...... **
lines for me?

Thanks.

---

### Post by ago on 2007-01-16
> **rdd said:**
> Qemu with KQemu is WAY slower.

THAT is what I wanted to hear. OK I am sold :D

---

### Post by thewump on 2007-01-16
Wow!

I love this.. the only question now is.. Why do I need it ;-)

Incredible how only a month into using Linux, I don't need anything else!

Good job on the support side Maniac.. that chmod 666 is exactly what I needed.

Best

Keith

---

### Post by BathroomNinja on 2007-01-16
In reply to janmartin
try:
```
sudo apt-get install gcc make autoconf automake1.9 libtool linux-headers-`uname -r`
```

---

### Post by janmartin on 2007-01-16
@BathroomNinja
seems to work:

```
jan@jan-virtual:~/a$ sudo sh ./VBoxLinuxAdditions.run  all Verifying archive integrity... All good.
Uncompressing VirtualBox 1.3.2 Guest Additions for Linux installation.....................................................................................................
VirtualBox 1.3.2 Guest Additions installation
Checking the setup of your guest system...
Building the VirtualBox Guest Additions kernel module...
Building the shared folder support kernel module...
Installing the VirtualBox Guest Additions...
Successfully installed the VirtualBox Guest Additions.
You must restart your guest system in order to complete the installation.
jan@jan-virtual:~/a$

```

---

### Post by janmartin on 2007-01-16
Me again, 
Actually it did not work. 
On restart Xorg crashed:

[B]...
dlopen: /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.4' not found
(required by /usr/lib/xorg/modules/input/vboxmouse-drv.so)
...[/B]

How to install the missing file?

Thanks.

---

### Post by ago on 2007-01-17
It is very good indeed. I am impressed. Does anyone know if it is possible to pack the drive images? I need to a way to edit the contents quickly and test the results within the VM. File system can be ext2/3.

---

### Post by thetictacaddict on 2007-01-17
Wow!  :)   This is a big difference from Qemu.  Changing the device permissions fixed the problem I encountered, but just adding myself to the group did not.  I am super impressed with VirtualBox. I saw some headlines like "Virtual Box Goes Open Source" and almost didn't read any, but I'm glad I checked this out.  I have some windows software for a German class right now and this is just what I needed.

---

### Post by kverde on 2007-01-17
Am I the only one having a hard time going in and out of mouse/keyboard control?  I try pressing CTRL+R, but it doesn't seem to release the mouse.

---

### Post by maniacmusician on 2007-01-17
it's not CTRL + R, it's the CTRL key on the right hand side. I changed mine to SUPER_L because thats easier to reach

---

### Post by marcoski on 2007-01-18
Hi,

I've a problem on Virtualbox's installation.
I use kubuntu dapper. And the dpkg -i errors message on the .deb Virtualbox file is the following:
[PHP]
Starting VirtualBox kernel moduleFATAL: Module vboxdrv not found.
(modprobe vboxdrv failed)...fail!
invoke-rc.d: initscript virtualbox, action "start" failed.
dpkg: error processing virtualbox (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox
[/PHP]

I think that the criticfal problem is loading kernel module. I try to look for it in /lib/`unme -r`/misc/ and in fact i can found a file named vboxdrv.ko. But modprobe doesn't want to load the module. 

Anyone can help me?

Tks

---

### Post by fosk on 2007-01-18
Hello,
I have installed VirtualBox and created a new VM. While trying to install Win XP on it, i got to press F8 to accept the license, but it seems this key does not get recognize :(
I have not found any other problem using the keyboard and mouse inside the VM. I can write and it works ok... Av Pag too... Just the "F8" key gives me problems.
Dont know how to solve that!
Any ideas anyone?
Thank you very much!!

---

### Post by fosk on 2007-01-18
Forget my previous post, i found out what was happenning :)
I just had the F8 key configured in gnome to be used by another app, and this was what interfer with VirtualBox keyboard i guess.
I am installing win xp righ now :)

---

### Post by fractal99 on 2007-01-19
marcoski,
I had this problem. I got it working in the end via this rather convoluted method:
I installed the package (with errors)
Then I downloaded the .run install option and followed the instructions for installing that, up to and including the compiling bit. However I then stopped (ie. i didn't attempt to make the device node)
I then used apt-get to install a program (didn't matter which), eg. sudo apt-get install ksirc
This would install ksirc, but then it would continue to install virtualbox, during which it succeeded in starting the vbox kernel module.
I then renamed the install directory (that was set up when using the .run install)
Then did the following
sudo apt-get remove --purge virtualbox
sudo dpkg -i VirtualBox_1.3.2_Ubuntu_Dapper_x86.deb
It installed fine this time, and is currently installing WinXP
Hope that helps!

---

### Post by depele on 2007-01-19
I am trying to! 
Lets hope on some nice working system, I hope I can put vb.net 2005 on it so I can program in vb.net (school)

thanks a lot! 

grtz

---

### Post by Enverex on 2007-01-19
> **marcoski said:**
> Hi,

I've a problem on Virtualbox's installation.
I use kubuntu dapper. And the dpkg -i errors message on the .deb Virtualbox file is the following:
[PHP]
Starting VirtualBox kernel moduleFATAL: Module vboxdrv not found.
(modprobe vboxdrv failed)...fail!
invoke-rc.d: initscript virtualbox, action "start" failed.
dpkg: error processing virtualbox (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox
[/PHP]

I think that the criticfal problem is loading kernel module. I try to look for it in /lib/`unme -r`/misc/ and in fact i can found a file named vboxdrv.ko. But modprobe doesn't want to load the module. 

Anyone can help me?

Tks

I had this issue too, you need to add "nmi_watchdog=0" to the end of your kernel boot line.

---

### Post by in_flu_ence on 2007-01-19
I have pretty good success with VBox. installed my XP and it does run very smoothly.
Got my USB keyboard set and cdrom working.

Yah I did some tweak as mentioned by previous post to get it properly installed. but it does worth a try. I think it functions better than vmware in terms of desktop use. Good for gamers i guess.

---

### Post by miack on 2007-01-19
Im new to linux and ubuntu so don't shout at me hehe 

I installed virtualbox but could not get it to work and tried the chmod and usermod commands but couldn't seem to get the commands to work silly me didn't realize I had to be root :P anyways its a cracking program and I'd suggest everyone try it.

---

### Post by timbobsteve on 2007-01-20
Hey everyone,

I am trying to get networking for VirtualBox working. I can get NAT, but the Host Adapter network option doesn't work for me. I get the following error when I try to start a machine with Host-Adapter sharing enabled:

```

Failed to initialize Host Interface Networking.
At '/home/vbox/vbox/src/VBox/Main/ConsoleImpl.cpp' (5018) in static int Console::configConstructor(VM*, void*).
VBox status code: -3100 VERR_HOSTIF_INIT_FAILED
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

Has anyone got host-shared networking under virtualbox working or getting the same error?

Any help is greatly appreciated.

-Timbobsteve

---

### Post by dimeotane on 2007-01-20
anyone figured out how do get it to open the host cd/dvd drive?

I was having the same problem that someone earlier wrote:
"  The pull-down box is empty even though I have a mounted CDROM in PC."

the solution is to unmount / eject the CD first.  Then the device will show up in your Virtualbox drop down menu.

---

### Post by The Noble on 2007-01-20
Sadly, this does not work for me on feisty. Even after reading this entire thread and  googleing for answers, I came up empty handed. When I use the deb to install VirtualBox, it comes up with this:
```

brian@btubb2:/stuff/media/Debs$ sudo dpkg -i VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb
Selecting previously deselected package virtualbox.
(Reading database ... 145853 files and directories currently installed.)
Unpacking virtualbox (from VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
Setting up virtualbox (1.3.2-20070114_Ubuntu_edgy) ...
-e 
Creating group 'vboxusers'. VM users must be member of that group!

Starting VirtualBox kernel moduleFATAL: Error inserting vboxdrv (/lib/modules/2.6.20-5-generic/misc/vboxdrv.ko): Invalid argument
(modprobe vboxdrv failed)...fail!
invoke-rc.d: initscript virtualbox, action "start" failed.
dpkg: error processing virtualbox (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox

```

It doesn't work even if I try to force the install either. From looking at the error message, It looks like it can't install the vboxdrv module. Anyone have any clue what to do? I am not exactly the most experienced when it comes to tinkering with the main kernel, but I am willing to try right now.

EDIT: I forgot to mention that VB actually runs, but it comes up with this error message when attempting to start a virtual machine:
```

VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
...{more stuff}

```

---

### Post by nfear24 on 2007-01-22
I have VirtualBox installed on Ubuntu Edgy 6.10 and it runs my windows XP great on my laptop 1280x800.  My question Im wondering is my mouse sometimes just randomly jumps around when in windows virtualbox.  Is anyone else experiencing this.  Gets rather annoying when it jumps to the edge of the screen when Im like in the middle or somethingl

---

### Post by Enverex on 2007-01-23
Works for me on Feisty. To get the module to load you have to disable to nmi_watchdog and to get past that second error you have to be in the vbox users group.

---

### Post by nfear24 on 2007-01-23
> **gapplewagen said:**
> I was able to fix mine too.  Here was the issue (or what I think it was):

When I originally installed the .deb my /usr/src/linux was pointed to /usr/src/linux-headers-2.6.17-10-generic.  So when I ran the deb it said:

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log

That's fine and all but my uname -a output said I was running 2.6.17-10-386.  So I changed the symlink for /usr/src/linux to point to /usr/src/linux-headers-2.6.17-10-386 and retried the whole install.  After multiple "apt-get remove virtualbox" and "dpkg --purge virtualbox" I was still getting the same error.  The problem was that the apt-get remove and dpkg --purge was not removing the module that it built from the 2.6.17-10-generic headers.  so I did this:

sudo rm -f /lib/modules/2.6.17-10-386/misc/vboxdrv.ko

Then I did the apt-get remove and dpkg --purge on the virtualbox package once more, installed the .deb again with the proper symlink to my current kernel and it worked.  

Hope this helps.

uname -a gives me 2.6.17-10-server

How do I change the symlink from /usr/src/linux to linux-headers-2.6.17-10-server

do I just sudo ln -s /usr/src/linux-headers-2.6.17-10-server
from /usr/src/linux

Thanks

---

### Post by nfear24 on 2007-01-23
I have it working now.  The make command wasnt installed on my ubuntu server.

Nick

---

### Post by MadmanTM on 2007-01-23
looking good :)

---

### Post by nfear24 on 2007-01-23
Windows XP installs great and runs fine, but when trying to install windows2000 it crashes during the install after the network setup.  Anyone else install win2000?

Nick

---

### Post by in_flu_ence on 2007-01-23
Latest update: It runs fine for both on my laptop and desktop but apparently, i can't get it to run it widescreen (laptop).

---

### Post by nfear24 on 2007-01-23
Has anyone successfully setup there virtual machine to use host interface networking instead of the default virtual Box setting NAT.  Because you can get outbound fine.  But Im testing this out running it on a server and need the machine setup that way.  So Im working on getting the host interface networking for the virtual machine instead of the NAT.

---

### Post by igeterrors on 2007-01-23
I have a suggestion that may help some who are having trouble installing VirtualBox in Dapper:  Check to see whether you are running the 386 version of the kernel or the 686 version, and if appropriate for your hardware, upgrade to 686.  Evidently for compatibility reasons, the default Dapper install is the 386, but my laptop has a Celeron M 370, so I should've been using the 686 version all along.  

When I tried to install VirtualBox I saw every error message that is mentioned in this thread and I dealt with them one by one in various ways.  The [**VirtualBox FAQ**]("http://www.virtualbox.org/wiki/User_FAQ") had an interesting item that seemed helpful:> 
If the installation of the VirtualBox_*.deb package was not successful because the compilation of the kernel module fails, it might not be possible to remove the package nor to install other packages as the pre-remove (prerm) script of the package (which is executed prior to package removing or upgrading) aborts with an error "(Kernel module not found)...fail!". In that case do the following:

    * Edit /etc/init.d/virtualbox and change line 129 from 'exit 1' to 'exit 0'
    * Reinstall the virtualbox package by 'dpkg -i <the VirtualBox package for your distribution>'. An installation failure of this package is expected.
    * Edit /var/lib/dpkg/info/virtualbox.postinst and change line 39 from 'exit 1' to 'exit 0'
    * Execute 'dpkg --configure --pending'
    * The package should now be installed successfully. However, the kernel module is still not compiled. Before you will be able to execute VirtualBox you have to create a kernel module for your current kernel, as described in the User ManualSo I get it installed, and I can create a virtual drive and a virtual machine, but when I go to start it, I get:```
VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
```And I remember what the FAQ said about having to create a kernel module for your current kernel, so after downloading the manual from [**here**]("http://www.virtualbox.org/wiki/Downloads"), I read:> To be able to install this kernel module, you will have to prepare your system for building external kernel modules. Unfortunately, this process varies greatly from system to system, so we can only describe what to do for a few common cases.
&#8226;  If you have already built your own kernel, /usr/src/linux points to your kernel sources, and you have not removed the files created during the build process, then your system will already be correctly set up and installation as described below should proceed properly.
&#8226;  Some Linux distributions can be set up simply by installing a package:
   &#8226;   the linux-headers package in newer Debian and Ubuntu releasesSo I open up Synaptic and search for linux-headers and this is where it gets interesting because what I see is that there is a kernel-headers package for 386 and one for 686 which says it is for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.  I look down at the little sticker on my laptop that says "Celeron" and so I grab the 686 package.  Install.  No joy.  Still getting the "VirtualBox kernel driver not installed" error. 

That's when it hits me to open up my menu.lst file and there it is:  Ubuntu, kernel 2.6.15-27-386.  So now I'm thinking maybe that's been the problem all along.  After more searching of the forums I find out how to upgrade the kernel, and it turns out it's pretty easy.  Just do:
```
sudo apt-get install linux-686
``` which isn't going to take your old version out of grub, so if there's a problem you can always boot back into it.

So, I install new kernel, reboot, open up VirtualBox and BAM!  It works! I was a little worried that my wireless wouldn't work because that was a pain to get set up when I first installed Dapper, but it worked without a hitch!  Hopefully this is of some help to others like me who are (as I was) at their wits end trying to install VirtualBox.

---

### Post by The Noble on 2007-01-23
Hey thanks! It sadly did not work for me, as I still cannot run a virtual machine. No worries, though, as that is what is to be expected as I am on Feisty. Maybe the generic kernel is where the problems are... Anyways, the installer stopped complaining about any kernel problems after editing the two 'exit 1' lines, but I still get the error when trying to start them. Even though it did not help me, it sounds like it may help others. Anyways, does anyone else using the generic kernel succesfully with VirtualBox (2.6.20-5 generic with headers)?

---

### Post by miack on 2007-01-23
> **nfear24 said:**
> Has anyone successfully setup there virtual machine to use host interface networking instead of the default virtual Box setting NAT.  Because you can get outbound fine.  But Im testing this out running it on a server and need the machine setup that way.  So Im working on getting the host interface networking for the virtual machine instead of the NAT.

Isn't there an option to change it to "host interface" I'm sure there is.

edit: yep its there dunno if it works or not I'd say so.

---

### Post by nfear24 on 2007-01-23
> **miack said:**
> Isn't there an option to change it to "host interface" I'm sure there is.

edit: yep its there dunno if it works or not I'd say so.

Ya there is an option but its not as simple as just chaning that in virtual box.  Things have to be setup in linux to work with it.  Not sure how to set it up.  Also is anyone running virtualbox with beryl.  I notice if I have beryl running and Im inside my virtual windows xp, the mouse tends to be jumpy and jump around but everyting else runs fine.   Now if beryl isnt running I dont have the problem with the mouse jumping around.  Sucks because I like to have beryl running so I can have my windows xp running full screen on one side of the cube.

---

### Post by 3rdalbum on 2007-01-24
> **nfear24 said:**
> Windows XP installs great and runs fine, but when trying to install windows2000 it crashes during the install after the network setup.  Anyone else install win2000?

Nick

I think that's probably due to the Win2k installer's driver bug. Quoted from TFM for Virtualbox (page 59):

> 
9.1.2. Windows 2000 installation failures
        When installing Windows 2000 guests, you might run into one of the following issues:
        •   Installation reboots, usually during component registration.
        •   Installation fills the whole hard disk with empty log files.
        •   Installation complains about a failure installing msgina.dll.
        These problems are all caused by a bug in the hard disk driver of Windows 2000. After issuing a hard disk request, there is a race condition in the Windows driver code which leads to corruption if the operation completes too fast, i.e. the hardware interrupt from the IDE controller arrives too soon.

With physical hardware, there is a guaranteed delay in most systems so the problem is usually hidden there (however it should be possible to reproduce it on physical hardware as well). In a virtual environment, it is possible for the operation to be done immediately (especially on very fast systems with multiple CPUs) and the interrupt is signalled sooner than on a physical system. The solution is to introduce an artificial delay before delivering such interrupts. This delay can be configured for a VM using the following command:

VBoxManage setextradata <vmname> "VBoxInternal/Devices/piix3ide/0/Config/IRQDelay" 1

This sets the delay to one millisecond. In case this doesn't help, increase it to a value between 1 and 5 milliseconds. Please note that this slows down disk performance. After installation, you should be able to remove the key (or set it to 0).


---

### Post by v.ipe.r on 2007-01-24
> **nfear24 said:**
> Ya there is an option but its not as simple as just chaning that in virtual box.  Things have to be setup in linux to work with it.  Not sure how to set it up.  Also is anyone running virtualbox with beryl.  I notice if I have beryl running and Im inside my virtual windows xp, the mouse tends to be jumpy and jump around but everyting else runs fine.   Now if beryl isnt running I dont have the problem with the mouse jumping around.  Sucks because I like to have beryl running so I can have my windows xp running full screen on one side of the cube.

I have the same problem configuring host networking, how does one do that?](*,)  Do we have to configure some kind of virtual nic in the host? The manual states that alternatively in Linux, they can be configured by VB, but how? I have VB running fine in Edgy, the only problem i had (apart the networking configuration) was after having installed Edgy server, it wont get past grub, other from that is working fine.

---

### Post by nfear24 on 2007-01-24
I got this link off the IRC chats.  check it out.  Im testing it out now and I think I have it working.

[https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")

Its at the bottom of the page!

---

### Post by v.ipe.r on 2007-01-24
> **nfear24 said:**
> I got this link of the IRC chats.  check it out.  Im testin git out now and I think I have it working.

[https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")

Its at the bottom of the page!

Awesome!!!!! :D Going to try it as soon as i get home! By by Vmware!!!

Tanks a lot for the find, nfear24!

---

### Post by v.ipe.r on 2007-01-24
Well, after trying that i ended up without networking, i must be doing something wrong.:-k 
Did any body else tried it?

---

### Post by G_Willakuh on 2007-01-25
I would like to offer some assistance if I can

The link here contains the best info for configuring your TAPx and ETHx devices and adding them both to a bridge BRx: [https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")

Once those steps have been followed, there are additional steps required, such as configuring the routing between host and guest (VirtualBox).

In your guest box, bring up the ETHx device with an IP - just set a static like 192.168.0.1 for simplicity.

eg. if the guest ethernet interface is eth0:
> sudo ifconfig eth0 192.168.0.1 up

Then, still on the guest box, add a route to the host ip. (By 'host ip', I mean the bridge interface ip on the host).

eg. if the host ip (bridge interface ip) is 10.1.1.1:
>  sudo route add -host 10.1.1.1 dev eth0

Have a squiz at the routing table and see how it looks:
> route -n

So, now you have the guest routing configured. Good. Onto the host routing...

On the host box, add a route to the guest. This time, we are going to use the bridge interface in the route, rather than the ethernet interface as per on the guest box.

eg. if the guest ethernet interface ip is 192.168.0.1, and the host bridge interface is br0:
> sudo route add -host 192.168.0.1 dev br0

Try pinging each way

#host: sudo ping 192.168.0.1
#guest: sudo ping 10.1.1.1

This site has excellent info on user-mode-linux and configuring the different interfaces & routes: [http://user-mode-linux.sourceforge.net/networking.html]("http://user-mode-linux.sourceforge.net/networking.html")

I hope this is useful - please post your results

---

### Post by v.ipe.r on 2007-01-25
Tanks G_Willakuh, I'm going to try that later when i get home still, what worries me, is that after fallowing the steps in here [https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03](https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03), i ended up without networking.:confused: 
Any way, tomorrow i will report back in!

---

### Post by nfear24 on 2007-01-25
> **G_Willakuh said:**
> I would like to offer some assistance if I can

The link here contains the best info for configuring your TAPx and ETHx devices and adding them both to a bridge BRx: [https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")

Once those steps have been followed, there are additional steps required, such as configuring the routing between host and guest (VirtualBox).

In your guest box, bring up the ETHx device with an IP - just set a static like 192.168.0.1 for simplicity.

eg. if the guest ethernet interface is eth0:


Then, still on the guest box, add a route to the host ip. (By 'host ip', I mean the bridge interface ip on the host).

eg. if the host ip (bridge interface ip) is 10.1.1.1:


Have a squiz at the routing table and see how it looks:


So, now you have the guest routing configured. Good. Onto the host routing...

On the host box, add a route to the guest. This time, we are going to use the bridge interface in the route, rather than the ethernet interface as per on the guest box.

eg. if the guest ethernet interface ip is 192.168.0.1, and the host bridge interface is br0:


Try pinging each way

#host: sudo ping 192.168.0.1
#guest: sudo ping 10.1.1.1

This site has excellent info on user-mode-linux and configuring the different interfaces & routes: [http://user-mode-linux.sourceforge.net/networking.html]("http://user-mode-linux.sourceforge.net/networking.html")

I hope this is useful - please post your results

by chance do you have a howto if the guest is a windows xp machine to setup the routing?

---

### Post by v.ipe.r on 2007-01-25
No go!](*,) 

After fallowing this:

```
Networking

To start, NAT is by far the easiest way to get your guests connected to the interweb, but you may want to use the guests as servers, for this you need Host Networking. You will need to install bridge-utils and uml-utilities so that you can make a tap device and add it to a bridge.

sudo apt-get install bridge-utils uml-utilities 

Now make a bridge, and put your current interface into it:

sudo tunctl -t tap1 -u fred #where fred is the user you will be running vbox as 
sudo chmod 666 /dev/net/tun

Make a new bridge called br0:

sudo brctl addbr br0 

Put your current interface (in this case eth0) into promiscuous mode, then add it to the bridge and give the bridge a dhcp address.

sudo ifconfig eth0 0.0.0.0 promisc 
sudo brctl addif br0 eth0
dhclient br0

Add the new tap1 device to the bridge

sudo brctl addif br0 tap1 

You should now be able to use host networking in vbox, just change "attached to" to "host interface" and add the interface name of tap1 in your networking settings. Read the manual as well, there are some other nifty ways to do this
```

I still end up without networking in my host system!:(

---

### Post by nfear24 on 2007-01-25
> **v.ipe.r said:**
> No go!](*,) 

After fallowing this:

```
Networking

To start, NAT is by far the easiest way to get your guests connected to the interweb, but you may want to use the guests as servers, for this you need Host Networking. You will need to install bridge-utils and uml-utilities so that you can make a tap device and add it to a bridge.

sudo apt-get install bridge-utils uml-utilities 

Now make a bridge, and put your current interface into it:

sudo tunctl -t tap1 -u fred #where fred is the user you will be running vbox as 
sudo chmod 666 /dev/net/tun

Make a new bridge called br0:

sudo brctl addbr br0 

Put your current interface (in this case eth0) into promiscuous mode, then add it to the bridge and give the bridge a dhcp address.

sudo ifconfig eth0 0.0.0.0 promisc 
sudo brctl addif br0 eth0
dhclient br0

Add the new tap1 device to the bridge

sudo brctl addif br0 tap1 

You should now be able to use host networking in vbox, just change "attached to" to "host interface" and add the interface name of tap1 in your networking settings. Read the manual as well, there are some other nifty ways to do this
```

I still end up without networking in my host system!:(

Did you by chance double check to make sure you entered everyting correctly.  I still have networking on my host after following that guide.   If you can later post your results from a ifconfig.

---

### Post by nfear24 on 2007-01-25
Im not getting this to work right. 

Here is what my host machine routing table looks like:
> amach@virtualbox:~$ route -n
Kernel IP routing table
Destination                  Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.168.101           0.0.0.0         255.255.255.255 UH    0      0        0 br0
192.168.168.102           0.0.0.0         255.255.255.255 UH    0      0        0 br0
192.168.168.0                0.0.0.0         255.255.255.0   U     0      0        0 br0
0.0.0.0                       192.168.168.1   0.0.0.0         UG    0      0        0 br0


now my guest machine I have it setup like this.
ip:  192.168.168.102
mask: 255.255.255.0
gw: 192.168.168.1

How can I get it so I can see this guest machine on the network.  Here is what my routing table looks like on the guest machine:


> 
Destination                  Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.168.22         0.0.0.0         255.255.255.255 UH    0      0        0 eth0
192.168.168.0                          0.0.0.0         255.255.255.0 UH    0      0        0 eth0
0.0.0.0                                192.168.168.1         0.0.0.0   U     0      0        0 eth0

---

### Post by v.ipe.r on 2007-01-25
> **nfear24 said:**
> Did you by chance double check to make sure you entered everyting correctly.  I still have networking on my host after following that guide.   If you can later post your results from a ifconfig.

Ok, I'm going to confirm if every thing is wright, just one question, what ip should i put here?

```
sudo ifconfig eth0 0.0.0.0 promisc
```

---

### Post by nfear24 on 2007-01-25
> **v.ipe.r said:**
> Ok, I'm going to confirm if every thing is wright, just one question, what ip should i put here?
sudo ifconfig eth0 0.0.0.0 promisc 
```
sudo ifconfig eth0 0.0.0.0 promisc
```

[COLOR="Navy"]sudo ifconfig eth0 0.0.0.0 promisc[/COLOR] is exactly what you put there.   You leave the ip 0.0.0.0 because its being put into promiscuous mode.

Nick

---

### Post by Moulton on 2007-01-25
To get the kernel module to load, I found I had to issue the 'depmod' command (as root) first.  Perhaps a reboot would have also worked.

I also had trouble with the group permission issue on /dev/vboxdrv.  Adding myself to the entry in /etc/group didn't seem to work (even with logging out and back in again).  I finally adopted MusicManiac's solution of changing the permissions on /dev/vboxdrv to 666.

The default Host Key is documented as 'Control_R', which I found confusing.  It's not Ctrl+R, but the right control key, which has to be pressed and released.

Like MusicManiac, I was interested in whether VirtualBox could import or mount .vmdk files from VMware.  It's pretty clear that no such feature yet exists.

There are two semi-interesting possibilities (neither of which I have tried)... 

A .vmdk file on Windows can be attached as a drive letter using some free third-party tools.  Then, any VFAT or NTFS partitions can be mounted in Windows and (presumably) shared using the native SMB file sharing feature of Windows.  

A more interesting possibility is to exploit the iSCSI feature of the proprietary version of VirtualBox.  The license says that the proprietary version can be used free of charge for personal or educational use.  It occurs to me that one might be able to build a small iSCSI server in VMware and export a .vmdk drive as a generic block device which could then be attached as an iSCSI drive in VirtualBox.  If this can be made to work, then one might be able to use existing .vmdk drives that way.

---

### Post by DrainBead on 2007-01-25
> **Moulton said:**
> To get the kernel module to load, I found I had to issue the 'depmod' command (as root) first.  Perhaps a reboot would have also worked.

I also had trouble with the group permission issue on /dev/vboxdrv.  Adding myself to the entry in /etc/group didn't seem to work (even with logging out and back in again).  I finally adopted MusicManiac's solution of changing the permissions on /dev/vboxdrv to 666.

The default Host Key is documented as 'Control_R', which I found confusing.  It's not Ctrl+R, but the right control key, which has to be pressed and released.

Like MusicManiac, I was interested in whether VirtualBox could import or mount .vmdk files from VMware.  It's pretty clear that no such feature yet exists.

There are two semi-interesting possibilities (neither of which I have tried)... 

A .vmdk file on Windows can be attached as a drive letter using some free third-party tools.  Then, any VFAT or NTFS partitions can be mounted in Windows and (presumably) shared using the native SMB file sharing feature of Windows.  

A more interesting possibility is to exploit the iSCSI feature of the proprietary version of VirtualBox.  The license says that the proprietary version can be used free of charge for personal or educational use.  It occurs to me that one might be able to build a small iSCSI server in VMware and export a .vmdk drive as a generic block device which could then be attached as an iSCSI drive in VirtualBox.  If this can be made to work, then one might be able to use existing .vmdk drives that way.

1. .vmdk is a proprietary format.
2. Says on their homepage that this is NOT FLOSS in the versions that do allow file sharing, and that is pretty much something you'd need sooner or later so the PUEL is the only valid licence for this, besides, download the sourcecode, the released source is void of any commentary rendering it useless to anyone else than the people at Innotek. this isn't true FLOSS more than Intel's graphics drivers are FLOSS. Only the people involved can understand the codebase.

3. But it is a whole wagonload faster than VMWare, mostly because it uses a lot of cache.

So the more the merrier, of course, if you were to run Vista which is extremely efficient in that department, VMWare or Virtualbox would not matter as long as you assign enough memory.

---

### Post by ago on 2007-01-26
If I try to install from feisty herd 2 iso, the screen gets unusable when I get to the partiotion section in the installation wizard and I cannot proceed. Using server/alternate ISO works fine. Does anybody else have the same problem?

EDIT: solved updating Ubiquity before running the installer

---

### Post by nfear24 on 2007-01-26
> **v.ipe.r said:**
> Ok, I'm going to confirm if every thing is wright, just one question, what ip should i put here?

```
sudo ifconfig eth0 0.0.0.0 promisc
```

v.ipe.r check out this post on the ubuntu forums.  It solves eveything.

[http://ubuntuforums.org/showthread.php?p=2066565#post2066565](http://ubuntuforums.org/showthread.php?p=2066565#post2066565)

_________
Nick

---

### Post by happybill on 2007-01-26
I started a thread called Installing Virtualization Software.  At first it was about vmware and virtualbox, but I became more attracted to virtualbox because vmware proved to be difficult to install (understanding what to do was the difficult part), and virtualbox, with its self-contained auto unpacker installer, looked a lot easier  Wrong!

Then I found this thread and read all the entries with great interest.  Following the approach of igetorrors to install linux 686 and the related linux-headers, and working through the instructions in the virtualbox.org FAQs, I eventually had a virtualbox installation - or so I thought.

All is not well.  I've made one virtual machine, but cannot start it.  An error message complains that the VirtualBox Kernel driver is not installed.  I tried to set the permissions for /dev/vboxdrv to 666 as some people appear to done, but there is no such file or folder on my PC.

Any advice would be most welcome.. Is a guide to installing VirtualBox in a clean, updated, installation of Dapper Drake too much to hope for?

---

### Post by nfear24 on 2007-01-26
> **happybill said:**
> I started a thread called Installing Virtualization Software.  At first it was about vmware and virtualbox, but I became more attracted to virtualbox because vmware proved to be difficult to install (understanding what to do was the difficult part), and virtualbox, with its self-contained auto unpacker installer, looked a lot easier  Wrong!

Then I found this thread and read all the entries with great interest.  Following the approach of igetorrors to install linux 686 and the related linux-headers, and working through the instructions in the virtualbox.org FAQs, I eventually had a virtualbox installation - or so I thought.

All is not well.  I've made one virtual machine, but cannot start it.  An error message complains that the VirtualBox Kernel driver is not installed.  I tried to set the permissions for /dev/vboxdrv to 666 as some people appear to done, but there is no such file or folder on my PC.

Any advice would be most welcome.. Is a guide to installing VirtualBox in a clean, updated, installation of Dapper Drake too much to hope for?

check your virtualbox install log.   you might be missing a few things when its trying to build it.  It will show you there.

---

### Post by Moulton on 2007-01-26
As I understand it, the .vmdk format is a published architecture, which means that third-party tools can create and parse working .vmdk drive image files, including translations into other drive image formats.  There are such tools for converting to the Virtual PC .vhd format, for example.

Eventually, I suppose, the developers will provide ways to directly attach drive images in foreign formats, just as file systems are increasingly easy to mount on non-native operating systems.

Since VirtualBox, is Open Source, I expect that means the .vdi disk image format is a published architecture.

In the meantime, existing .vmdk drives can be exported using conventional network file sharing protocols, so it might suffice just to build a small /boot drive in VirtualBox and snarf an existing Linux file system via a network mount.

I took a look at openfiler.  There is a pre-packaged VMware appliance for it, and it's easy enough to attach a .vmdk file to it.  But openfiler might be a tad too massive if all you want to do is export a file system residing on .vmdk.  I still don't know if exporting a .vmdk drive as an iSCSI block device would make it directly bootable within VirtualBox.  In theory this should be doable, but reducing theory to practice is another story.

---

### Post by Moulton on 2007-01-26
> I tried to set the permissions for /dev/vboxdrv to 666 as some people appear to done, but there is no such file or folder on my PC.

I had this same problem.  For me, the fix was to run
```
sudo depmod
``` before executing /etc/init.d/virtualbox.  

The depmod command rebuilds the module dependencies.  Without that step, the attempt to load the kernel driver fails.

Once the kernel driver for vboxdrv is successfully loaded, there will magically appear the /dev/vboxdrv entry.  Change the permissions on it to 666 before starting up your Virtualbox session.  For some reason, the group permissions aren't being recognized, even when you are added to the vboxusers group.

There was always a rarely used 'newgrp' command in Unix to choose which of your group IDs would dominate.  I found that the 'newgrp' command failed for me, presumably because groups now have password authorization.  It may be necessary to take additional measures to fully authorize group read/write permissions.

---

### Post by Moulton on 2007-01-26
Upthread ManiacMusician lamented the inability to boot Virtual Box from an existing VMware .vmdk disk image.

I found a way to do this using the iSCSI feature of VirtualBox.  

As proof of concept, I did this using some ready-made tools on Windows.  I had previously installed the suite of third-party [VMware tools from RDPsoftware]("http://petruska.stardock.net/software/VMware.html"), including VDKwin.  I used VDKwin to attach a bootable .vmdk disk image as if it were a physical disk in Windows.  Note that I did not mount any of the partitions as drive letters in Windows.

Then, using [iSCSI Cake]("http://www.iscsicake.com") on Windows , I exported that attached disk image as an iSCSI target to my adjacent Linux computer where I had VirtualBox installed.  The VirtualBox console interface doesn't provide a convenient way to attach the IDE drive to an iSCSI target, so I had to issue this command at the Unix shell ...
```
VBoxManage addiscsidisk -server kayak -target "Marble Drop" -username Dell
```
The target and username correspond to the names that I had chosen in iSCSI Cake when I exported the .vmdk disk image as an iSCSI target.

Now, back in the VirtualBox console, the newly defined iSCSI target shows up in my list of registered drives, and I can select it as my first IDE drive.

I start my virtual machine, and miracle of miracles, it accesses the remote drive over my LAN, booting up at the sluggish speed one would expect for booting from a network drive.

Since the virtual hardware has changed, I have to deal with loading different drivers, and perhaps revectoring the location of the root partition, say from sda3 to hda3.  Booting into a Windows .vmdk, there is lots of 'Found New Hardware' to cycle through.

But it works.

At home, I'm running a 10-Mbps Ethernet, which is really too slow for iSCSI.  But if VirtualBox is running on the same host as the iSCSI server, the localhost loopback interface would presumably run at reasonable speeds.  

I don't know of any easy way to mount a .vmdk image as an attached drive in Linux that could be similarly exported as an iSCSI target, short of running an iSCSI server inside of a VMware appliance.   I did look into the OpenFiler VMware appliance, but it's way too hefty a package for the task at hand.

---

### Post by Fingerz91 on 2007-01-26
Hey All,

I dual boot between Windows XP and Ubuntu, and would like to be rid of XP for good, except for VirtualBox installation...

I followed the guide located here [http://www.ubuntuforums.org/showthread.php?t=340113](http://www.ubuntuforums.org/showthread.php?t=340113)

and tried to install XP, with no luck

I cant seem to get the program to look on the disk, it opens, and says no boot media found!

Any ideas?

---

### Post by Moulton on 2007-01-26
Regarding group permissions, I see that adding oneself to the vboxusers group requires matching entries in both /etc/group and /etc/gshadow.  The latter is the group password file.  

If one is properly represented in both /etc/group and /etc/gshadow, then write permission succeeds to /dev/vboxdrv with the default 660 permissions.

---

### Post by Moulton on 2007-01-26
> **Fingerz91 said:**
> I can't seem to get the program to look on the disk, it opens, and says no boot media found!

Any ideas?
If you create a new VM with an empty drive, you have to make sure your physical CD-ROM (or an equivalent ISO image) is attached and activated as a bootable device, with a bootable installation disk of Windows, just as if you were installing Windows on a brand new machine with a brand new empty hard drive.

Note that Windows XP will probably consider this installation to be unrelated to the existing one on your host computer, and will likely demand a new license key.  If it comes to that, you will probably have to call the 800 number and beg them to let you reinstall your original licensed copy in the virtual machine on the same physical host.

---

### Post by chocolatemintmocha on 2007-01-27
> **Moulton said:**
> I had this same problem.  For me, the fix was to run
```
sudo depmod
``` before executing /etc/init.d/virtualbox.  

The depmod command rebuilds the module dependencies.  Without that step, the attempt to load the kernel driver fails.

Once the kernel driver for vboxdrv is successfully loaded, there will magically appear the /dev/vboxdrv entry.  Change the permissions on it to 666 before starting up your Virtualbox session. 

Hello, I had the same problem, so I tried sudo depmod, but I still can't find /dep/vboxdrv or /etc/init.d/virtualbox. I compiled and installed from source. I did find a folder named vboxdrv in the out/linux.x86/release/obj/src/VBox/HostDrivers/vboxdrv directory. Any suggestions?

---

### Post by Moulton on 2007-01-27
> **chocolatemintmocha said:**
> Hello, I had the same problem, so I tried sudo depmod, but I still can't find /dev/vboxdrv or /etc/init.d/virtualbox. I compiled and installed from source. I did find a folder named vboxdrv in the out/linux.x86/release/obj/src/VBox/HostDrivers/vboxdrv directory. Any suggestions?
Can you confirm that all the components (especially including the kernel modules) were successfully compiled without errors?  You would have gotten lots of compile-time errors if you were missing critical resources such as the kernel headers.

Then, after a successful compile, what did the installation phase report?  In a generic source package, the installer has to figure out which of several styles of startup script is appropriate for your distribution.  Sometimes you have to take extra steps to ensure that startup scripts are of the correct style, and in the correct location for your brand of Unix.

---

### Post by Moulton on 2007-01-27
By the way, if you have one of the standard versions of Ubuntu, you should download the .deb package for your version, rather than a generic source package.

For example, I downloaded VirtualBox_1.3.2_Ubuntu_Dapper_x86.deb from the [VirtualBox Download Page]("http://www.virtualbox.org/wiki/Downloads"), and the installation went fine.

---

### Post by happybill on 2007-01-27
Thanks for the suggestions.
1.  There is no file called virtualbox install.log on my PC, but I found  '/.VirtualBox/VBoxSVC.log.0' (and .log.1 and .log.2) They showed that there were errors on Qt3.  My Qt is version 3.3.3.6, whereas the Virtualbox manual specifies 3.3.5 or greater.  I used Synaptic to install a couple of Qt4 files that looked right.

2. Next I ran the command 'sudo depmod' and then worked through the commands provided in the FAQs.  The first edit revealed that line 129 was already exit 0, the re-installation worked as expected and terminated in an error.  When I came to  edit '/var/lib/dpkg/info/virtualbox.postinst'. my system became unstable and applications closed unexpectedly so I could not finish.  To write this. I'm back in XP - sorry about that.

---

### Post by chocolatemintmocha on 2007-01-27
> **Moulton said:**
> Can you confirm that all the components (especially including the kernel modules) were successfully compiled without errors?  You would have gotten lots of compile-time errors if you were missing critical resources such as the kernel headers.

Then, after a successful compile, what did the installation phase report?  In a generic source package, the installer has to figure out which of several styles of startup script is appropriate for your distribution.  Sometimes you have to take extra steps to ensure that startup scripts are of the correct style, and in the correct location for your brand of Unix.

When I attempted to sudo make install the driver I got messages like this one: 
WARNING:  out/linux.x86/release/bin/src/vboxdrv.o - Section mismatch: reference to .init.text: from .smp_locks after '' (at offset 0x38)

Also, when i run virtualbox I get this: Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Informational: VirtualBox object created (rc=00000000).

I also checked to see if I had linux-headers installed in synaptic, which I think I do.

---

### Post by graabein on 2007-01-27
Can I run a virtual image of Windows XP and play for example World Of Warcraft through it? 

How does virtualization and 3D graphics work together?

---

### Post by Fingerz91 on 2007-01-27
> **Moulton said:**
> If you create a new VM with an empty drive, you have to make sure your physical CD-ROM (or an equivalent ISO image) is attached and activated as a bootable device, with a bootable installation disk of Windows, just as if you were installing Windows on a brand new machine with a brand new empty hard drive.

Note that Windows XP will probably consider this installation to be unrelated to the existing one on your host computer, and will likely demand a new license key.  If it comes to that, you will probably have to call the 800 number and beg them to let you reinstall your original licensed copy in the virtual machine on the same physical host.

Got it running nice and smooth:D 

However, has anyone gotten devices like printers to work?

I have posted a separate thread reguarding this, if anyone has a guide, or howto....

---

### Post by domino on 2007-01-28
Has anyone had any success with vb running under beryl/xgl? The app and vm runs fine, but I can not resize the vm. Much like the problem with earlier version of Parallels application under Beryl/XGL.

---

### Post by black_magician on 2007-01-28
I had the same problem with permissions as some other people on this thread.  I restarted as the FAQ suggests, and it fixed the whole thing.  It's kinda nice having the option to run Windows if I want,  and so far no other problems.  (although I kinda feel like I'm jumping back in time when I look at XP)

---

### Post by maniacmusician on 2007-01-28
> **graabein said:**
> Can I run a virtual image of Windows XP and play for example World Of Warcraft through it? 

How does virtualization and 3D graphics work together?
Only if your processor supports hardware virtualization will you get it to run fast enough to do that. Some P4's support it (I think, dont remember) and the core 2 duo line supports it. You could probably google it and find others that do

---

### Post by Moulton on 2007-01-28
> **chocolatemintmocha said:**
> When I attempted to sudo make install the driver I got messages like this one...

If you are running a standard installation of Dapper or Edgy, you should abandon the attempt to install from a generic source version of VirtualBox and go with the prebuilt .deb package for your version of Ubuntu.

For example, I downloaded VirtualBox_1.3.2_Ubuntu_Dapper_x86.deb from the [VirtualBox Download Page]("http://www.virtualbox.org/wiki/Downloads"), and avoided the grief of compiling everything from source.

---

### Post by Karl S. on 2007-01-28
I've managed to install VirtualBox just fine. I'm running Windows XP Home version in it, and I've managed to install the three apps I need in Windows (Word, Endnote, and MyBase), all of which run just fine. 

The problem? The files I need are on hda6. I *could* upload everything I need and download it into the Windows virtual machine whenever I need it, and then upload it back when I'm done, but that would be a pain, particularly with the enormous MyBase file. So, how can I access my Ubuntu partitions--or, really, just the hda6 partition--from w/in my Virtual Machine? 

This answer [**here**]("http://www.ubuntuforums.org/showpost.php?p=2020413&postcount=35") seems to offer some kind of solution, but it's way over my head. I need an answer suitable for a total beginner. 

If It's of any significance, I've successfully pinged my host ip from within my virtual machine. I tried this since I guessed the solution would be to get the Virtual Machine to recognize hda6 as being on a network somewhere....

Second question: I'm going to call Microsoft in the next few days to ask if I can activate my copy of Windows XP *again,* since I'm basically installing it twice on the same machine. Has anyone else managed to get Microsoft to allow this yet?

---

### Post by happybill on 2007-01-29
Congrats to black_magician.  I'd be very grateful for answers to the following questions.
1.  Did you start with the standard Dapper Drake 6.06 and accept only the updates suggested by the program, or are you using something later?
2.  What did you do to meet the requirement for Qt?
3.  Is your linux kernel 2.6.15-27, or something else?
4.  Did you upgrade the linux kernel to -686?
5.  Did you do anything else apart from following the FAQ advice in the third bullet point under Linux hosts?

---

### Post by chocolatemintmocha on 2007-01-29
I've found a simple solution to install the Vbox OSE on my box. I origionally compiled vbox from source, but everytime i would try to load a virtualmachine I would get a kernel not installed error. I really only wanted to use the GPL version of the software, and my understanding is, is that the binary versions of the program are not completely GPL. So what I did was I installed the .deb package of vbox, which installed the correct kernel modules for vbox. Then I uninstalled the non-free .deb package leaving behind the installed vbox kernels. Then I compiled the GPL source code again. Made sure I was in the virtualbox group. And voila, it worked like a charm!

---

### Post by Karl S. on 2007-01-29
RE: my comments above (#123)

Problem one: figured it out by reading the manual, which is pretty much the same information as post #35 by Onyros.

Problem two: Microsoft cheerfully gave me an activation ID for the Virtual Install of my copy of Windows XP.

---

### Post by Fingerz91 on 2007-01-29
Just an update...

I got my printer and external HD working like a charm in my virtual XP

[http://www.ubuntuforums.org/showthread.php?p=2081241#post2081241](http://www.ubuntuforums.org/showthread.php?p=2081241#post2081241)

If anyone needs, there's my thread that explains everything...

---

### Post by kuukie on 2007-02-01
Would somebody care to enlighten me on what **can't** run inside it? Graphic-intensive games, obviously, but apart from that ... ?

VirtualBox could be quite a milestone for the Linux desktop, if it would be added to Feisty.

Ubuntu already is *the* most popular distribution out there. At least with non-technical Linux users. Now the average joe doesn't really care about the OS, but he loves his applications. The FOSS alternatives (Firefox, OpenOffice, Thunderbird, ...) are already used widely and many people can be brought to switch to them, because browsing, office work and reading mail are pretty straight-forward things. 

But although there's a vast amount of FOSS alts for many other, smaller applications, there's an even bigger amount of applications that are, believe it or not, Windows-only. And many of these can be even more critical to a user than above mentioned popular apps. Then of course there's the biggest problem of them all: stubborn users that just won't let go of Photoshop in lieu of the GIMP, for example. No matter how hard you try, there will *always* be people out there that argue about PS vs GIMP. I think that energy is wasted ... just let them use PS, it's not 'critical' like, say, the browser.

VirtualBox (being a VMware equivalent) will take care of all of this moaning about applications and even more importantly hopefully 'persuade' developers to stop trying to clone $obscure-application and get down to improving the kernel and/or hardware drivers.

Again, whoever is 'responsible' (;-)) for integrating stuff into Feisty, please consider VirtualBox  ... wait, is this the place to request that kind of thing at all? Would an entry in the Ubuntu Wiki be a good idea?

---

### Post by Brunellus on 2007-02-01
> **kuukie said:**
> Would somebody care to enlighten me on what **can't** run inside it? Graphic-intensive games, obviously, but apart from that ... ?

VirtualBox could be quite a milestone for the Linux desktop, if it would be added to Feisty.

Ubuntu already is *the* most popular distribution out there. At least with non-technical Linux users. Now the average joe doesn't really care about the OS, but he loves his applications. The FOSS alternatives (Firefox, OpenOffice, Thunderbird, ...) are already used widely and many people can be brought to switch to them, because browsing, office work and reading mail are pretty straight-forward things. 

But although there's a vast amount of FOSS alts for many other, smaller applications, there's an even bigger amount of applications that are, believe it or not, Windows-only. And many of these can be even more critical to a user than above mentioned popular apps. Then of course there's the biggest problem of them all: stubborn users that just won't let go of Photoshop in lieu of the GIMP, for example. No matter how hard you try, there will *always* be people out there that argue about PS vs GIMP. I think that energy is wasted ... just let them use PS, it's not 'critical' like, say, the browser.

VirtualBox (being a VMware equivalent) will take care of all of this moaning about applications and even more importantly hopefully 'persuade' developers to stop trying to clone $obscure-application and get down to improving the kernel and/or hardware drivers.

Again, whoever is 'responsible' (;-)) for integrating stuff into Feisty, please consider VirtualBox  ... wait, is this the place to request that kind of thing at all? Would an entry in the Ubuntu Wiki be a good idea?
a feature request in launchpad is the way to do it.

---

### Post by Enverex on 2007-02-01
> **kuukie said:**
> Would somebody care to enlighten me on what **can't** run inside it? Graphic-intensive games, obviously, but apart from that ... ?

VirtualBox could be quite a milestone for the Linux desktop, if it would be added to Feisty.

Ubuntu already is *the* most popular distribution out there. At least with non-technical Linux users. Now the average joe doesn't really care about the OS, but he loves his applications. The FOSS alternatives (Firefox, OpenOffice, Thunderbird, ...) are already used widely and many people can be brought to switch to them, because browsing, office work and reading mail are pretty straight-forward things. 

But although there's a vast amount of FOSS alts for many other, smaller applications, there's an even bigger amount of applications that are, believe it or not, Windows-only. And many of these can be even more critical to a user than above mentioned popular apps. Then of course there's the biggest problem of them all: stubborn users that just won't let go of Photoshop in lieu of the GIMP, for example. No matter how hard you try, there will *always* be people out there that argue about PS vs GIMP. I think that energy is wasted ... just let them use PS, it's not 'critical' like, say, the browser.

VirtualBox (being a VMware equivalent) will take care of all of this moaning about applications and even more importantly hopefully 'persuade' developers to stop trying to clone $obscure-application and get down to improving the kernel and/or hardware drivers.

Again, whoever is 'responsible' (;-)) for integrating stuff into Feisty, please consider VirtualBox  ... wait, is this the place to request that kind of thing at all? Would an entry in the Ubuntu Wiki be a good idea?

You can't directly interface to hardware other than USB devices but any other programs should be fine.

---

### Post by kuukie on 2007-02-01
Whoops, please forgive my ignorance, it's already in [Launchpad]("https://blueprints.launchpad.net/ubuntu/+spec/virtualbox") *and* the [Wiki]("https://wiki.ubuntu.com/SimpleVirtualization"). Sorry, but I had only searched for 'virtualbox' instead of 'virtualization'.

Still thinking about VirtualBox, another comes to mind: the PITA that is dual-booting will hopefully begone. Of course dual-booting is easy with Ubuntu, but I think everybody's screwed up GRUB or LILO sometime or other while using Linux and seeing your virtual machine crash isn't quite as horrifying as not being able to boot & troubleshoot at all :)

---

### Post by Moulton on 2007-02-01
One thing about virtualization vs multi-booting is that you need considerably more RAM to do virtualization, since each instance of a running VM takes a sizeable chunk of real memory for itself.

---

### Post by David Floyd on 2007-02-02
If running Windows XP in VirtualBox, is Anti Virus software needed?

Personally I think it would need it in the Virtual XP to protect that system, but if not, any attack on that system I presume wouldn't get through to Dapper.

Is my thinking correct?

Thanks
David

---

### Post by Drakkor on 2007-02-02
Ok, I may be dense,but I've been to most of the links to forums,google, and the rest, but I still haven't seen a step by step guide to running VirtualBox.  I have installed the .deb version and that went fine, I can open the program, but it escapes me how to actually load or install , say XP onto it. 
I have a dual boot XP/Edgy machine and have the XP CD.  Could someone clue me in ?? 
Thanks ! :) 
Edit: After I go through the instructions, this is what I get !

---

### Post by steve.horsley on 2007-02-02
Add yourself to the vboxusers group, then log out and in again. You may even need to reboot (I did). 

Once the VM is running, mount the cd-rom while it is still empty. Then insert the Windows install disk and reset the VM. Install windows as normal.

---

### Post by Drakkor on 2007-02-02
Thanks,Steve, but I am beginning to think this is just too hard for me !  :(  vs. just dual booting
Did what you said , i think,but just got a box that said "unable to read boot whatever"
What do you mean by "install disk and reset the VM. Install windows as normal.?? Where's the "reset the VM" button ??

---

### Post by steve.horsley on 2007-02-03
So you got the VM going. Good.

Did you give it a hard disk image to use? If not, use File->Virtual Disk Manager and create a virtual disk image for the VM to use. A couple of Gig should do, and I don't recommend  using a dynamically expanding image - they're too slow. Once you have created a disk image (of an empty hard disk), configure the VM to use it.

Start the VM and it will say boot failed because no bootable devices were found. This is correct - the hard disk image doesn't have an operating system on it yet.

In the VM window (You may need to hit right-Ctrl to get the mouse back), pull down Devices->Mount CD/DVD and choose "host drive /dev/cdrom". Now the VM will see the windows installer CD when you insert it. 

Insert the windows installer CD. Ubuntu also pops up a nautilus window on the CD but you can just close that. The point is that now when you use the VM menu VM->Reset, it will boot from the CD rom and start the windows installer. You probably know what to do from there - Yes, Yes, Yes, license key etc...

---

### Post by brainformat on 2007-02-03
hi i really need some help!
i have installed it on my 6.10, ad myself in usergroup etc...
i'm trying to make xp guest.
it shows me this:

[[img]http://img2.freeimagehosting.net/uploads/th.33a6099d16.png[/img]](http://img2.freeimagehosting.net/image.php?33a6099d16.png)

after i click ok, it turns down...

---

### Post by Drakkor on 2007-02-03
Hmm. Steve, in your screenshot 2, there seems to be no choose "host drive /dev/cdrom" , as I don't seem to have that option !  I only have CD/DVD-ROM Image. Here's where I am now.

---

### Post by Drakkor on 2007-02-03
Wow,figured it out, on the main page, I mounted the CD/DVD-ROM , and presto,lol , I was able to
install XP and get it working !! :)  My question now is that I guess you can only work on one OS at 
a time, because I have no mouse cursor outside of the XP window, and what's with these host
keys, they don't seem to work for me, and finally how'd you get those screenshots ?,lol !

---

### Post by Rich78 on 2007-02-03
> **brainformat said:**
> hi i really need some help!
i have installed it on my 6.10, ad myself in usergroup etc...
i'm trying to make xp guest.
it shows me this:

[[img]http://img2.freeimagehosting.net/uploads/th.33a6099d16.png[/img]](http://img2.freeimagehosting.net/image.php?33a6099d16.png)

after i click ok, it turns down...

I get the same on my Edgy machine.

I've also found I cannot remove VirtualBox either to try to reinstall it.

If it do a sudo apt-get remove I get the following: E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

If I re-run the .deb file I get:

The package might be corrupted or you are not allowed to open the file.

I've changed permissions etc to no avail.  I also downloaded the package again incase it was corrupt but get the same message.

If anyone could help I'd appreciate it.

---

### Post by Karl S. on 2007-02-03
> **Drakkor said:**
> Wow,figured it out, on the main page, I mounted the CD/DVD-ROM , and presto,lol , I was able to
install XP and get it working !! :)  My question now is that I guess you can only work on one OS at 
a time, because I have no mouse cursor outside of the XP window, and what's with these host
keys, they don't seem to work for me, and finally how'd you get those screenshots ?,lol !

Control-R = the right control key. Press that and it should release your cursor to let you work outside your Virtual Machine window. Double click in the VM window to have it recapture your cursor. Alternately, you could install the Guest Additions (which you can do from a menu once you start your Windows VM), as this allows you free motion with your cursor without having to worry about releasing it.

---

### Post by Drakkor on 2007-02-03
Yeah, Karl the thing was I actually never knew there was a right control button,lol,  :)  Just like
when you drive down the same street for 10 years and never notice one of the places there,lol :-D
Got it goin' on,lol.   What does the F12 button do ???

---

### Post by Medieval_Creations on 2007-02-05
> **Rich78 said:**
> I get the same on my Edgy machine.
If it do a sudo apt-get remove I get the following: E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.


I'm running it on Edgy and I haven't had very many problems.  I got that error before to.  Have you added your user ID to the vboxuser group?  Also make sure that the vboxsvr module is loaded "lsmod -l".

I would try that first.  It resolved that error for me.

---

### Post by Medieval_Creations on 2007-02-05
Ok, I only have two things that I haven't been able to get working properly.

1.) I've gotten USB to work, but i have to use the CLI and do "sudo VirtualBox &".  Then I have read/write on the USB drive.  If I just launch VBox normally I get an error that I need to change the permissions on the usb module.  I don't know how to do that.

2.) No sound from VBox.  I choose the OSS driver for my WinXP in VBox, but it I get no sound and it shows no Sound HW installed in WinXP.  I only have 2 options when setting up the sound for that image Null & OSS.  Not sure what I need to change to get that working.

Anyone have any thoughts?

Aside from these 2 glitches everything else runs great.  I'm really impressed with VBox.
=D>

---

### Post by Drakkor on 2007-02-05
I'm using the OSS sound in Edgy, with XP loaded, and get good sound.

---

### Post by Medieval_Creations on 2007-02-05
I'm using a SB Audioligy 2, I'm not sure if that has something to do with it or not.  I also had Amarok running.  I see no sound as a minor, but it would be nice if I could make sure it works.

---

### Post by StuntMonkeh on 2007-02-05
Thats it!!! I have had enough.... but I won't let this beat me.  I am trying to install the guest additions to an ubuntu virtual machine.  I have NEVER used linux before and im not likely to if I can't install these damn guest additions.  Can someone walk me through it PLEASE!!!  There is nothing in the cd drive when I mount the iso and I have even tried downloading the iso file to the desktop but it always comes up 'command not found'.

---

### Post by Medieval_Creations on 2007-02-05
I run Ubuntu as the Host & XP as the guest, so I haven't had this problem. 

But here is how you would mount an iso in linux.

From the command line (A.K.A. "Terminal") in linux.  the command to mount an iso is:
```
sudo mount -o loop [image name] /media/cdrom
```

once the image is mounted you should be able to navigate to the cdrom and run the command:
```
sh ./VBoxLinuxAdditions.run all
```

I hope this helps.

From VirtualBox PDF:
> 
4.3.1. Installing the Linux Guest Additions
        The VirtualBox Guest Additions for Linux are provided on the same ISO CD-ROM as the Additions
        for Windows described above. They also come with an installation program guiding you through the
        setup process, although, due to the significant differences between Linux distributions, installation
        may be slightly more complex.
        Installation involves the following steps:
        1.    Before installing the Guest Additions, you will have to prepare your guest system for building
              external kernel modules. This is exactly the same process as described in Section 2.2.2,
              &#8220;Support for external kernel modules&#8221;, except that this step must now be performed in your
              Linux guest instead of on a Linux host system, as described there.
        2.    Mount the VBoxGuestAdditions.iso file as your Linux guest's virtual CD-ROM drive, ex-
              actly the same way as described for a Windows guest in Section 4.2.1.1, &#8220;Mounting the Addi-
              tions ISO file&#8221;.
        3.   Change to the directory where your CD-ROM drive is mounted1 and execute as root: sh ./VBoxLinuxAdditions.run all



---

### Post by StuntMonkeh on 2007-02-06
Feel a complete idiot!  I still fall at the first hurdle.  I opened up terminal and typed in the first command it tells me 'no such file or directory'.  The .iso is sitting on the desktop at the moment..... What does the bit in front of the cursor mean, is that just logon details with the @ in?

---

### Post by Medieval_Creations on 2007-02-06
> What does the bit in front of the cursor mean, is that just logon details with the @ in?

As far as I know ( which doesn't mean it's at all correct :D ), it basically just mars the the command prompt.  Similar to c:\ in old schools dos.  After installing you can change how that looks and what is displayed as well.

---

### Post by Brunellus on 2007-02-06
user@hostname$

means

'user' is on computer 'hostname' as a nonpriveleged user '$'

it's trivially easy to telnet/ssh to different machines, all in the same shell, so the prompt reminds you who you are and where you are, if not necessarily what you're doing.

whoa.  zen.

---

### Post by mtalexan on 2007-02-06
> **The Noble said:**
> Sadly, this does not work for me on feisty. Even after reading this entire thread and  googleing for answers, I came up empty handed. When I use the deb to install VirtualBox, it comes up with this:
```

brian@btubb2:/stuff/media/Debs$ sudo dpkg -i VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb
Selecting previously deselected package virtualbox.
(Reading database ... 145853 files and directories currently installed.)
Unpacking virtualbox (from VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
Setting up virtualbox (1.3.2-20070114_Ubuntu_edgy) ...
-e 
Creating group 'vboxusers'. VM users must be member of that group!

Starting VirtualBox kernel moduleFATAL: Error inserting vboxdrv (/lib/modules/2.6.20-5-generic/misc/vboxdrv.ko): Invalid argument
(modprobe vboxdrv failed)...fail!
invoke-rc.d: initscript virtualbox, action "start" failed.
dpkg: error processing virtualbox (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox

```

It doesn't work even if I try to force the install either. From looking at the error message, It looks like it can't install the vboxdrv module. Anyone have any clue what to do? I am not exactly the most experienced when it comes to tinkering with the main kernel, but I am willing to try right now.

EDIT: I forgot to mention that VB actually runs, but it comes up with this error message when attempting to start a virtual machine:
```

VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
...{more stuff}

```

I had the same problem when I was installing it on Dapper.  In addition whenever I installed anything else I got an error message saying virtualbox installer returned an exit code 1.  Since then I've upgraded to Edgy (I'm a little behind) and tried the Edgy version of virtualbox.  Unfortunately I think some things got crossed and now apt-get crashes as a command and using the GUIs (Synaptic and Update Manager).  Both tell me 
```

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

```

Can someone suggest something?  I also didn't upgrade my kernel sources so I've still got the old Dapper 2.6.15 kernel headers that I think might be causing some problems with the Edgy version of the install, but I can't get the 2.6.17 ones (Edgy) while I don't have access to the apt-get command.

As a side note, the documentation for VirtualBox says there are problems interacting with the linux kernel 2.6.17 which incidentally is the one Edgy is built on.  The fix suggested by VirtualBox is to use kernel 2.6.15, or if necessary to use kernel >=2.6.17, use 2.6.19.  My understanding is that they basically say to use Dapper, instead of Edgy, or Feisty when it comes out if you want VirtualBox to work.

---

### Post by Medieval_Creations on 2007-02-06
Have you tried loading the module manually?

```
sudo modprobe vboxdvr
```

If that does work to load the module you can load it at start-up by editing you /etc/modules file.

```
sude pico /etc/modules
```

just add vboxdvr to the end of the list.

---

### Post by mtalexan on 2007-02-06
> **Medieval_Creations said:**
> Have you tried loading the module manually?

```
sudo modprobe vboxdvr
```

If that does work to load the module you can load it at start-up by editing you /etc/modules file.

```
sude pico /etc/modules
```

just add vboxdvr to the end of the list.

That didn't change anything.  There isn't a module running named vboxdvr either before or after I added vboxdvr to /etc/modules.  Is there a way to track down where the script that keeps interrupting apt-get is and stop it?

EDIT: I also discovered that GDebi now denies me access to the VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb file I initially used to install the package in the first place.  It gives me the error:
```

The package might be corrupted or you are not allowed to open the file.  Check the permissions of the file.

```

When I first installed the package it asked me for the root password to install the packages necessary and now it won't even give me that.  I've tried redownloading the package in case it had been corrupted with no changes.

---

### Post by Medieval_Creations on 2007-02-06
OH, I just realized that the deb is from Edgy and you are running Feisty.  Feisty is running a 2.6.20 kernel the modules wouldn't be compatible.  They have to be compiled by the same kernel version in order to work.  The Edgy deb file most likely isn't going to work.  Chances are the only way you'll be able to get VBox working is to download the source from their site and compile the whole thing, *(unless you can find a deb file for Feisty).*

---

### Post by mtalexan on 2007-02-06
> **Medieval_Creations said:**
> OH, I just realized that the deb is from Edgy and you are running Feisty.  Feisty is running a 2.6.20 kernel the modules wouldn't be compatible.  They have to be compiled by the same kernel version in order to work.  The Edgy deb file most likely isn't going to work.  Chances are the only way you'll be able to get VBox working is to download the source from their site and compile the whole thing, *(unless you can find a deb file for Feisty).*

I am using Edgy.  I simply commented that the documentation warns against using 2.6.17.  I am still using it though.

EDIT:
I keep trying to get rid of VirtualBox in the hopes it might allow my system to do anything.  With that in mind my latest attempt was:
```

mike@mike-laptop:/$ sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 165762 files and directories currently installed.)
Removing virtualbox ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing virtualbox (--remove):
 subprocess pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox
mike@mike-laptop:/$ 

```

This was a result of my previous attempts:
```

mike@mike-laptop:/$ sudo apt-get remove virtualbox
Reading package lists... Done
Building dependency tree... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
mike@mike-laptop:/$ sudo dpkg --remove virtualbox
dpkg: error processing virtualbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox
mike@mike-laptop:/$ 

```

I discovered I can't remove the package until I reinstall it, and I can't reinstall it because the package itself isn't installed correctly.  One big thing I noticed was the line:
```

(Kernel module not found)...fail!

```

I get the same thing when I try to run bash on a file, but I just assumed I wasn't using it correctly.  Any thoughts?

---

### Post by Medieval_Creations on 2007-02-07
EDIT:
Here is a link to a thread where they were able to force the .deb to uninstall.

[http://www.ubuntuforums.org/showthread.php?t=350447](http://www.ubuntuforums.org/showthread.php?t=350447)

When I got that error I just recompiled the kernel ***(not install it, just recompiled)***.

---

### Post by ago on 2007-02-08
I am not able to boot the Feisty 2.6.20-6-generic kernel. It crashes the kernel, the error is:

> BUG: unable to handle kernel paging request at virtual address 08048110

Is anybody else experiencing this? Is there a solution? Kernel 2.6.20-5, works but I need to make the new kernel working.

---

### Post by mtalexan on 2007-02-09
> **Medieval_Creations said:**
> Here is a link to a thread where they were able to force the module to uninstall.

[http://www.ubuntuforums.org/showthread.php?t=350447](http://www.ubuntuforums.org/showthread.php?t=350447)

When I got that error I just recompiled the kernel ***(not install it, just recompiled)***.

If you're referring to the VirtualBox kernel, I don't have the slightest idea how since the directions on their website include references to folders that only exist if you download it from source instead of the package, something I've been unable to do.  If you're referring to my OS kernel, I'm pretty sure there's no need.

---

### Post by Medieval_Creations on 2007-02-09
That was a typo on my part.  module is wrong.  I meant to say force the uninstall of the .deb.

When I installed the deb the error I got from the log file was that it was unable to create the vbox module because a module file in the /usr/src/linux folder didn't exist.  I've had a similar error a while ago when trying to compile & install QEMU/KQEMU.  It looks for a module information file (I can't remember the name at the moment), so it can create it's own module.

I just did the same thing I did for QEMU to fix it.  I downloaded the OS kernel source and compiled it.  That created the file that was missing and the deb file then installed properly.

---

### Post by ramjet_1953 on 2007-02-10
I've been using VirtualBox almost from it's release and have had no problems with running it. I have installed XP Pro as a guest OS and it runs every Windows app that I have thrown at it. I have it running full-screen (1280 X 800) on my Acer TravelMate 4101.

Initial start-up is slower than native, but that is understandable, as it needs to set-up the virtual machine first. But after the OS is running, apps seem to run just as well as under a native XP install.

Regards,
Roger :cool:

---

### Post by farbird on 2007-02-12
i have some games which says this upon running..

"DirectX Error: Can not setup display mode"


i am running ubuntu 6.10 with virtualbox guest os [winxp]

It runs fine on my dualboot system of course.

if anyone wanna help me test it.. 
pls email me for the file..

my msn identity is farbird

---

### Post by Medieval_Creations on 2007-02-12
I got everything working in VBox now.  USB, Sound, & even setup a network drive in my Guest OS (XP) to one of my Storage partitions in Ubuntu.  So far every app I've installed works great.

I haven't tried games yet.  That's next.  :D

---

### Post by Enverex on 2007-02-12
> **farbird said:**
> i have some games which says this upon running..

"DirectX Error: Can not setup display mode"


i am running ubuntu 6.10 with virtualbox guest os [winxp]

It runs fine on my dualboot system of course.

if anyone wanna help me test it.. 
pls email me for the file..

my msn identity is farbird


As pointed out before, 3D games dont work in VirtualBox at the moment (or any other VM properly).

---

### Post by shrek on 2007-02-12
OK so I have noticed that some folks have been having issues getting the VirtualBox guest additions to install in a Ubuntu 6.10 guest environment. I am also having this issue and am still not sure how to fix the problem, can anyone offer some suggestions. 

I have a great XP VirtualBox guest environment on my XP host (Work laptop) my Ubuntu Desktop 6.10 guest also works great except for the fact that I can’t get the guest additions installed. I updated the kernel modules as per the VirtualBox documentation but when I mount the ISO and browse the drive the CD is empty. Thanks in advance.

---

### Post by Medieval_Creations on 2007-02-13
I'm running a Linux host, so I'm not sure of the differences, but when I installed the Guest Additions in my XP Guest all I did was go up to the VBox menu and selected Install VirtualBox Guest Additions. *(I'm at work, and can't remember the specifics. Sorry)* It ran like any other installation in XP, then after a reboot of the guest it worked perfectly.  I didn't have to mount anything.

---

### Post by shrek on 2007-02-13
Thanks for the reply. I finally figured it out after surfing around the postings for VirtualBox and Ubuntu., so now I will unashamedly display my ignorance as a Linux newbie and pass it on. 

1.	From the Ubuntu menu open System, Administration, Synaptic Packager Manager
2.	From the left pane select ‘Development’
3.	On the top right, select linux-headers-386 and click the Apply button
4.	You should be told that the package is dependant on linux-headers-2.6.17.11-386 and that this package will also be added.
5.	Restart the Ubuntu guest machine.
6.	Mount the VBoxGuestAdditions.iso from the VirtualBox Devices menu on the Ubuntu guest VirtualBox Window. 
7.	From Terminal in the Ubuntu guest enter:
             sudo mount /media/cdrom0
             cd /media/cdrom0
             sh ./VBoxLinuxAdditions.run all
	     umount /media/cdrom0
8.	Restart the Ubuntu guest machine (Not sure if this restart is required but since we    are on a Windows host a restart seem natural about now. LOL)

Thank to everyone who participates in these forums, it really makes figuring things out  lot easier when there is a community around you.

---

### Post by gapplewagen on 2007-02-13
Be careful when doing kernel upgrades.  VirtualBox will stop working after upgrading.  When I originally installed VB I was running 2.6.17-10 and recently upgraded to 2.6.17-11.  VirtualBox uses a module when starting /etc/init.d/virtualbox.  That module is in /lib/modules/<CURRENT KERNEL VERSION>/misc.  After the upgrade the startup script can't find the module (obviously).  I was able to copy and then relink /usr/src/linux and it fixed the issues:

* Make sure VirtualBox is closed
```

sudo rm /usr/src/linux
sudo ln -s /usr/src/linux-headers-2.6.17-11 /usr/src/linux
sudo cp -R /lib/modules/2.6.17-10-386 /lib/modules/2.6.17-11-386
sudo depmod -a
sudo /etc/init.d/virtualbox restart

```

Fire it up and give it a shot.  Keep in mind that your /lib/modules and /usr/src version/arch could differ from mine.  I'm doubting that this will work for a "real" kernel upgrade (ie 2.6.17 to 2.6.18).  If this is the case I would assume you would have to completely remove virtualbox (and purge) and reinstall it so it can recreate the kernel module with the new kernel headers.

---

### Post by Pom2122 on 2007-02-14
> If this is the case I would assume you would have to completely remove virtualbox (and purge) and reinstall it so it can recreate the kernel module with the new kernel headers.


I'm pretty sure that you could just run (as root) 
```
#/var/lib/dpkg/info/virtualbox.postinst
```
to have it create a new kernel module. You might have to run depmod afterwards.
:)

---

### Post by gapplewagen on 2007-02-14
> **Pom2122 said:**
> I'm pretty sure that you could just run (as root) 
```
#/var/lib/dpkg/info/virtualbox.postinst
```
to have it create a new kernel module. You might have to run depmod afterwards.
:)


Ahhh very good thanks for the info... your way is much easier  :)

---

### Post by caled on 2007-02-15
Yup, that way worked for me too. 
Cheers mate

---

### Post by robenroute on 2007-02-22
The new 1.3.6 version is out! At last, people with a 2.6.17 kernel (and before) can use ALSA audio settings without the dreaded reboot on every attempt to start the VM.

InnoTek, thank you!

---

### Post by robenroute on 2007-02-22
I'm running this on an "ancient" P4M 1.8MHz with 512MB internal, and I must say..... I'm impressed, officially! Tried qemu (with the special module to speed things up) and a few others, but this stuff goes like a ton of bricks down a mineshaft! I'm pleeeeeeased..:):):)

---

### Post by Karl S. on 2007-02-23
Since this is sort of a general thread for VirtualBox, I thought I'd ask these (probably very stupid) questions:

Do I need to keep my Windows XP.iso after I've installed the Windows Virtual Machine? In other words, does the Virtual Machine need that .iso to run?

The other (probably stupid) questions: I can access my ntfs partition through the VM. I set up access to it as a network drive today, but I had been accessing it through Samba. The network drive option (set up through net use f: \\vboxsvr\files) is faster than the Samba way, *but* for some reason it won't let me save MS Word files directly from Word into the partition. I have to same them to the Windows desktop and then copy then over. This is a problem, since my VM is purposefully as small I could make it (3GB) because I didn't plan on storing anything in it, which means there's *barely* room for me to store any file on it, even temporarily. So, there's Samba, which isn't buggy, except it doesn't work when I don't have an internet connection. So, since this is a VBox thread, if these questions are appropriate here, can anyone help me with the: 1).iso q? 2) the Network drive irritation?; 3) the Samba internet thing? Just pointing me to the appropriate thread would be fine.

---

### Post by maniacmusician on 2007-02-23
I don't know about your second and third questions, but the answer to the first is no, you don't have to keep your .iso. You can back it up onto a CD/DVD or just delete it.

---

### Post by bash on 2007-02-24
Running Virtualbox on an P3 500 mhz with 393 mb ram and an old geforce 2 gts (bout 64 mb of video ram). And its running fast (well as fast as a 500 mhz runs). Im currently installing Win 200 in the backgroup, while im happily typing here in firefox. Installation so far runs quite fast. And I even got dynamic filesize set.

So im officially impressed with this program. :popcorn:

---

### Post by darthchaosofrspw on 2007-02-25
> **imagine said:**
> Hi,

InnoTek rereleased his virtualization software Virtualbox under the GPL today ([press statement](http://www.virtualbox.org/wiki/News)). Before, the application was not available to to endusers.
Virtualbox supports Linux and Windows both as client and host systems. OpenBSD and OS/2 are also supported as clients. It works and looks similar to VMware and although it's not quite as powerful as VMware Workstation yet, it still looks promising.

There are also Ubuntu Dapper and Edgy packages available on their website (at least as long as the site doesn't get /.ed): [http://www.virtualbox.org](http://www.virtualbox.org)

Edit: Sorry, the DEB-packages are only available for the commercial edition, so the GPLed version has to be built from source.

I installed it the other night on my desktop (2.1GHz with 768 MB RAM). It's nice...it runs Win2K faster than Win4Lin Pro. And for s**** and giggles, I tried installing Linspire 4.5.603 on there as well. And it ran really nice as well. I will probably keep Win2K on there so I can keep using Muvee AutoProducer on there (Muvee AP doesn't work on Wine or Crossover).

---

### Post by BlackMamba on 2007-02-26
Hi, I've installed Windows XP with VirtualBox in my Ubuntu Edgy installation but I can only access to drive C in VM! Is there a way to access all partition in my hard disks?
Thank you

---

### Post by Karl S. on 2007-02-26
*Is there a way to access all partition in my hard disks?*

Yes. I'm sure someone else who actually knows something about computers can give you a better answer than I'm about to give, but for the time being, go to #35 in [this thread]("http://www.ubuntuforums.org/showpost.php?p=2020413&postcount=35") (and if #35 doesn't quite make sense, check the VirtualBox manual, where the instructions, although identical, struck me as somewhat clearer) or, if you're having trouble with that, follow the Samba instructions [here.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

BTW, thanks maniacm. for the answer. The weird thing is that I can save to my net drive directly from MS Word so long as I save as rtf (in other words, saving directly as Word doesn't work). Looks like the problem is a Windows problem, so not suitable for this forum. Weird!

---

### Post by kuukie on 2007-02-26
*From [http://www.virtualbox.org/wiki/News](http://www.virtualbox.org/wiki/News)*

Feb 12, 2007. InnoTek today announced that it has released VirtualBox 1.3.4, an important update to its leading virtual machine product which is available both as Open Source and as a commercial application with professional support. Over 800 improvements have been integrated, largely based on feedback from the VirtualBox user community. At the same time, InnoTek also announces that **it has agreed with Ubuntu to integrate VirtualBox into the upcoming Ubuntu Linux 7.04 ("Feisty Fawn"),** making it even easier to enjoy professional virtualization in an user-friendly manner.

---

### Post by chalimac on 2007-02-26
Wow. This is big. I wonder if Virtual Box will take advantage of the xen virtualization in the kernel.

---

### Post by BlackMamba on 2007-02-26
> **Karl S. said:**
> *Is there a way to access all partition in my hard disks?*

Yes. I'm sure someone else who actually knows something about computers can give you a better answer than I'm about to give, but for the time being, go to #35 in [this thread]("http://www.ubuntuforums.org/showpost.php?p=2020413&postcount=35") (and if #35 doesn't quite make sense, check the VirtualBox manual, where the instructions, although identical, struck me as somewhat clearer) or, if you're having trouble with that, follow the Samba instructions [here.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

Thank you, it works! :)

---

### Post by maniacmusician on 2007-02-26
> **kuukie said:**
> *From [http://www.virtualbox.org/wiki/News](http://www.virtualbox.org/wiki/News)*

Feb 12, 2007. InnoTek today announced that it has released VirtualBox 1.3.4, an important update to its leading virtual machine product which is available both as Open Source and as a commercial application with professional support. Over 800 improvements have been integrated, largely based on feedback from the VirtualBox user community. At the same time, InnoTek also announces that **it has agreed with Ubuntu to integrate VirtualBox into the upcoming Ubuntu Linux 7.04 ("Feisty Fawn"),** making it even easier to enjoy professional virtualization in an user-friendly manner.
Damn...that's great...I wonder if it will be the OSE or the one with all the bells and whistles included...

---

### Post by PapaWiskas on 2007-02-26
> **maniacmusician said:**
> I have Guest Additions installed.


Where do you get the Guest Additions from.
I installed this on a XP box and made a Ubuntu .vdi, but cant get the darn window to be smaller than my original Desktop size.  Would like to be running in a 800x600 window if I want, and switch to full screen whenever I feel like.  But I cant find a Guest Addtions download on the page anywhere for windows or linux....?
Help.

---

### Post by maniacmusician on 2007-02-26
> **PapaWiskas said:**
> Where do you get the Guest Additions from.
I installed this on a XP box and made a Ubuntu .vdi, but cant get the darn window to be smaller than my original Desktop size.  Would like to be running in a 800x600 window if I want, and switch to full screen whenever I feel like.  But I cant find a Guest Addtions download on the page anywhere for windows or linux....?
Help.
It's in one of the context menus at the top of the window. Probably something like "VM". There's an option called "Install Guest Additions". You click on that, and it loads a .iso. You mount the .iso as a CD (Usually "sudo mount /dev/hdc" by default). Navigate to the CD drive (cd /media/cdrom) and run the Linux shell script as root ("sudo sh LinuxGuestAdditions.iso" <--or whatever the name of the shell script is) and it will install all the nice little things for you like good video drivers and complete mouse integration, etc.

---

### Post by PapaWiskas on 2007-02-26
Okay, can anyone help me with this error, I went through this entire thread, post by post... did not see anything about my error however.

This is on my linux box, I already got the windows version working on an xp box.

NEVERMIND....appeared to be permissions issue with files inside the .VirtualBox directory, changed those permissions and it came up.

---

### Post by BlackMamba on 2007-02-26
OK, shared folders with Guest Additions is very bugged! Every time I try to open an NTFS partition in my Windows XP client I go into a BSOD and VM reboot....
So my question is: how can I share files and folders between my host and my guest?

I tried with an FTP server on my host too, but there is no way to access in it from my guest... :(

---

### Post by PapaWiskas on 2007-02-26
I am really surprised at how well this works.  I tried VMWare before on this laptop and it ran like a tired horse.

This, wow, sound works, It flies and only uses about 40% of my CPU at the peak moments.
Just blows my mind.  I wish this would work for games, has anyone tried that yet?

---

### Post by maniacmusician on 2007-02-27
> **PapaWiskas said:**
> I am really surprised at how well this works.  I tried VMWare before on this laptop and it ran like a tired horse.

This, wow, sound works, It flies and only uses about 40% of my CPU at the peak moments.
Just blows my mind.  I wish this would work for games, has anyone tried that yet?
Yup :) the power of open source, my friend...

---

### Post by Medieval_Creations on 2007-02-27
Most of the older games will work, but 3D typically doesn't work.  I haven't tried any yet myself.

---

### Post by encho on 2007-02-28
Anyone experienced installation failure for XP as a guest OS? It comes to the second part of the installation (right after serial no and network settings, when copying the files) and suddenly window closes without any error notification (main VB window is still open with 'aborted' notice next to the vm name).

---

### Post by Quillz on 2007-02-28
I haven't been reading this entire thread, so this may have already been brought up... Is VirtualBox in the Ubuntu repos?

---

### Post by Medieval_Creations on 2007-02-28
Unfortunatley not in Edgy.  But it will be for Feisty.

---

### Post by spoot on 2007-02-28
> **Medieval_Creations said:**
> Unfortunatley not in Edgy.  But it will be for Feisty.
I do not see the package in any distribution yet.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=names&subword=1&version=all&release=all)

Also, the deadline for new packages was Feb 22 if I read this correct :)
[https://wiki.ubuntu.com/FeistyReleaseSchedule](https://wiki.ubuntu.com/FeistyReleaseSchedule)

EDIT: Oops, didn't read the entire thread yet, they are working to get it included in Feisty. Odd that there's not even a first version in the repo's then after all these deadlines.
[http://www.virtualbox.org/wiki/News](http://www.virtualbox.org/wiki/News)

---

### Post by BlackMamba on 2007-02-28
> **BlackMamba said:**
> OK, shared folders with Guest Additions is very bugged! Every time I try to open an NTFS partition in my Windows XP client I go into a BSOD and VM reboot....
So my question is: how can I share files and folders between my host and my guest?

I tried with an FTP server on my host too, but there is no way to access in it from my guest... :(
help me please :(

---

### Post by baobab68 on 2007-03-09
I wish I could help, I have the same problem and it's the only thing stopping me from using VirtualBox...

---

### Post by H.E. Pennypacker on 2007-03-17
After figuring a lot of stuff out myself in the installation part, I have been able to get VirtualBox running with Windows XP.  It may have been an unnecessary pain, but it's worth it.

---

### Post by mustang on 2007-03-17
> **encho said:**
> Anyone experienced installation failure for XP as a guest OS? It comes to the second part of the installation (right after serial no and network settings, when copying the files) and suddenly window closes without any error notification (main VB window is still open with 'aborted' notice next to the vm name).

I did not encounter this problem. I was using a XP SP2 integrated disc.

---

### Post by OffHand on 2007-03-18
fixed

---

### Post by daengbo on 2007-03-19
I would like to recommend that average Joes like me don't need the VM running in a window all the time sucking up processor cycles, but we want a fast start-up time. The solution is to run the guest OS without a GUI and connect via RDesktop.

Start your VM like this:
VBoxManage startvm "Windows XP" -type vdrp

-type vrdp tells the VM to start with no gui. Put it in your start-up scripts if you plan to use it often.

Then create a launcher to connect to your VM like this:
rdesktop -a 16 localhost

Just click the button and the connection is almost instant!

---

### Post by marsm on 2007-03-25
Awesome piece of software.

Just wanted to say that Rosetta Stone (probably the best language learning system around) runs smoothly inside of it even on my low-tech laptop which runs at 1.5GHz, 512MB RAM, Intel Graphics etc...

Oh and thanks for the tip daengbo :)

---

### Post by robtotheb on 2007-03-25
Amazing stuff - I FINALLY have a stable and fast Photoshop solution for Ubuntu!

Is there a way to just have photoshop load outside of the VirtualBox XP window?

---

### Post by TheRingmaster on 2007-03-25
> **robtotheb said:**
> Amazing stuff - I FINALLY have a stable and fast Photoshop solution for Ubuntu!

Is there a way to just have photoshop load outside of the VirtualBox XP window?
You could maybe run photoshop in wine.

---

### Post by maniacmusician on 2007-03-25
> **robtotheb said:**
> Amazing stuff - I FINALLY have a stable and fast Photoshop solution for Ubuntu!

Is there a way to just have photoshop load outside of the VirtualBox XP window?
not a reliable solution. The setup you have now is your best bet.

---

### Post by robtotheb on 2007-03-26
Any way to share apache localhost with a virtualbox xp?

---

### Post by stijngysemans on 2007-03-27
> **robtotheb said:**
> Any way to share apache localhost with a virtualbox xp?

I think you just hast to reffer to your host computer via it's Ip address!

---

### Post by maniacmusician on 2007-03-27
> **robtotheb said:**
> Any way to share apache localhost with a virtualbox xp?
Acessing apache localhost on the host from virtual XP?

For me, I use the address "10.0.2.2"

This is how I figured it out; open a command prompt in XP (Start > Run > type in "cmd" and hit enter). Run the "ipconfig" command. The Default Gateway is what you use to access the apache localhost from inside the Virtual XP. I've found this is really useful for testing websites and stuff :)

---

### Post by Sunnz on 2007-03-27
Just wondering how's the graphics in VBox?

VMware need to install vmtools for the guest OS... is there a similar thing on VirtualBox?

---

### Post by OffHand on 2007-03-27
> **Sunnz said:**
> Just wondering how's the graphics in VBox?

VMware need to install vmtools for the guest OS... is there a similar thing on VirtualBox?

Yeah

---

### Post by Onyros on 2007-03-27
> **daengbo said:**
> I would like to recommend that average Joes like me don't need the VM running in a window all the time sucking up processor cycles, but we want a fast start-up time. The solution is to run the guest OS without a GUI and connect via RDesktop.

Start your VM like this:
VBoxManage startvm "Windows XP" -type vdrp

-type vrdp tells the VM to start with no gui. Put it in your start-up scripts if you plan to use it often.

Then create a launcher to connect to your VM like this:
rdesktop -a 16 localhost

Just click the button and the connection is almost instant!
In newer versions it's just a little different.

To start the VM:

```
VBoxVRDP -startvm "VM Name"
```

and then connect to the VM with the same command posted by daengbo

```
rdesktop -a 16 localhost
```

---

### Post by steven8 on 2007-04-23
I just installed WinXP via VirtualBox.  it was the fastest, easiest windows installation I have ever done!  : - )

I wasn't going to, but a friend I program for wants to finish a program, I believe, and it's in VB.net.  Visual Studio just won't install via wine, so I decided virtualization is the way to go.

Well done by innotek!!

---

### Post by hanzomon4 on 2007-05-22
I just installed XP in virtualbox, I'm impressed! Sound works, unlike vmware products I've tried. 
However the ultimate irony was that Windows Media Player couldn't play dvds so I had to install VLC :lolflag:

I'm installing Nexenta(opensolaris) right now. I wanted to install pc-bsd but it failed due to some error. This affects all of the freebsd's, however this is apparently fixed in the svn open source version Virtualbox OSE

---

### Post by be4truth on 2007-05-22
I switched to VirtualBos after having problems with VMware. Not only is it free but it does work well. My Windows guest was up immediately. Good software. Fast and nicely designed.
Well done
:KS

---

