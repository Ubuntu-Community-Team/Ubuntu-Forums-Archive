---
title: "pc emulators"
date: 2008-01-06
forum: Virtualisation
---

### Post by Pevichaey5 on 2008-01-06
hi 

is there any other free pc emulators for linux around other than bochs, as it doesn't seem to be working for me.

i have tried vmware for linux, but i can't seem to get that working either

i jus need to be able to run 'Visual Studio 2005' on my computer and i won't dual boot, as when i do to get certain programs, i forget about Linux :(

any help

cheers

---

### Post by phillips321 on 2008-01-06
vmware?
qemu?

What i have done is set up a server that hosts all my other operating systems on.

Linux HTTP, Linux SMTP and Server03. VMware is run ontop of an ubuntu server build with a very light gui.

What you could possibly do is install VMware server, create a winblowz virtual machine, then whenever u need to do some windows work just simply rdp into the winblowz box.

In this screen shot you can see i have VNC'd into the Host operating system, you can see that im running two machines (LinuxHTTPVM and WindowsServerVM).
[[IMG]http://www.forumpix.co.uk/thumbs/1199671759.jpg[/IMG]](http://www.forumpix.co.uk/i.php?I=1199671759)

To access the WindowsServerVM box i either do it like this or a much much faster way is to rdp directly into it. As seen in the next screenshot
[[IMG]http://www.forumpix.co.uk/thumbs/1199671820.jpg[/IMG]](http://www.forumpix.co.uk/i.php?I=1199671820)

You can get VMware server for free from [http://download3.vmware.com/software/vmserver/VMware-server-1.0.4-56528.tar.gz]("http://download3.vmware.com/software/vmserver/VMware-server-1.0.4-56528.tar.gz")

Any problems just ask...

---

### Post by gilf on 2008-01-06
I just installed VMWare player, copied my existing windows installation to an image file using partimage. I installed that in a virtual machine using partimage. I then added VMWare tools. It runs perfectly -- seemingly as fast as it did natively.

I also had the same windows system running as a dual boot, and also had Wine set up to run certain programs.

My conclusion is that for 90% of what I do, Ubuntu covers it, for the rest VMware has it all over dual booting and Wine for most windows tasks EXCEPT certain windows games. VMware ran all kinds of small oddball windows programs I've collected (Auction Sentry, Tileprint, Motocalc, etc) without having to re-register with new numbers. It also ran all of the Windows oddball 3D CADs I have (Turbocad, DesignCad, etc) these absolutely wouldn't run in Wine.

I will; say the VMWare install had me scratching my head a few times, and there were some late nights spent -- mainly in porting over my existing windows installation. But I finally did it, and it truly is a fine emulator. The speed is outstanding, and I also like the separation from my Ubuntu system -- so if it does any windows nasties, it won't hurt the Ubuntu side of things. Also extremely easy to back up, since you just copy one file and you're done.

---

### Post by AlexThomson_NZ on 2008-01-06
VMWare is definitely the way to go, and is pretty easy to install if you follow the guides on this forum (ie. just use the repositories, don't try to compile it yourself).

I think Wine now almost fully supports Studio now too doesn't it?

---

### Post by kelbizzle on 2008-01-06
Virtualbox works great.

---

### Post by ryanVickers on 2008-01-06
Vmware is complete garbage - its so slow just moving a window gets like 1 - 5 fps, and even the mouse is slow... even with all the fancy stuff your supposed to do, i don't remember I try not to :D

**problems:**
 -incredibly slow
 -feature lacking
 -complicated
 -after a while, would just randomly stop working... it just wouldn't open any more!
**up sides:**
 -possibly 1% more stable...

I too would highly recommend VirtualBox - some say its unstable, but only very slightly, ... I would say maybe 99% stability!! (which is better than real windows... ;))

**problems:**
 -possibly 1% less stable...
[B]up sides:
[/B] -although a bit picky at first, always works once you have it running (very easy!!)
 -very fast (runs 3D just as good as real windows)
 -tons of features!

---

### Post by phillips321 on 2008-01-06
ryanVickers - how were you accessing the virtualmachine on vmware? using the vmware console?

make sure to access the virtual machine you either use vnc or rdp. allways worked fine for me. (see my first post in this thread)

i might have to try virtualbox tho, sounds intresting if it supports full 3d? that mean i wont have to dual boot to play CSS and C&C3?

---

### Post by ryanVickers on 2008-01-06
I just ran "VMware" that ***it ***put in the menu... one would expect that to work! :???::mad:

As for the 3D in virtualBox, It won't do all the games, but some older ones yes (MM2 for one ;)), and I do 3D rendering in bryce 5 and its just as good, like 90% or better!!

---

### Post by Mike'sHardLinux on 2008-01-06
I've been using VMware server, player and workstation for a while and haven't ever had any of those problems. The only "fancy" stuff I ever had to do was install the VMware tools into the guest and then things run smoothly.

One thing I really like about VMware server is you can host the guest OSes on a server and access them remotely. And for me, while doing this, the OS is surprisingly responsive (on a dual P3-866 server and 100Mb network). I don't know if VirtualBox does this.

---

### Post by ryanVickers on 2008-01-06
> **Mike'sHardLinux said:**
> I've been using VMware server, player and workstation for a while and haven't ever had any of those problems. The only "fancy" stuff I ever had to do was install the VMware tools into the guest and then things run smoothly.

One thing I really like about VMware server is you can host the guest OSes on a server and access them remotely. And for me, while doing this, the OS is surprisingly responsive (on a dual P3-866 server and 100Mb network). I don't know if VirtualBox does this.

I guess I should have been more clear; it's good for stuff like that... network features etc. but nothing really in the settings (in Player at least) beyond enabling/disabling cdrom's, etc....

---

### Post by gilf on 2008-01-07
Inspired by your problems getting VMWare Player to work here, I decided to document my own install, completed a couple days ago,

 I just posted a rough HOW-TO on moving a whole existing Win98 dual boot partition ino a virtual machine for player

[http://ubuntuforums.org/showthread.php?t=660511](http://ubuntuforums.org/showthread.php?t=660511)

Using Vmware Tools provides near native speed for normal (non gamer) purposes.-- Note that the original poster asked about a development suite, not animations.  

( For gaming,dual boot, or run Wine if the game runs in it)

Yes it does do 3D rendering fine, if your software does the work, rather than depending on special internal functions of a cutting edge graphics card. 

Remember the virtual graphics card is SVGA (with VMWare tools). Most normal graphic intensive programs will work fine with this type of virtual graphics card. Older programs expect it and were designed to work with it. Specialized latest version cutting edge games probably won't.

3d doesn't work? Wrong. Mine works great! 3D CAD rendering is absolutely normal, and speedy with several programs I tried, including 2 current 3D CADs for Windows.

As proof, here's a screenshot of a 3D CAD design I'm working on in VMWare Player. It rendered just as fast as it did natively -- under 1 second from clicking on the drawing file. In fact, I think it ran faster because Ubuntu meshes better with my physical graphics card than Win98SE did natively. The CAD program is DesignCAD 3DMax.

By the way,any jaggies and dithering in the attached image are due to the.reduced size png screenshot, The original screen is hi-res perfect.

ps. if your VMWare player is running slowly, check your memory allocation in your VMX file -- some sample files have this *set as low as 64 megabytes*. Naturally you want to run your virtual machine with* at least as much memory as you ran native Windows, if you're trying to compare speeds. *

Note also that your Ubuntu host system needs enough memory to run the VMPlayer, plus whatever you are running in Ubuntu concurrently. Therefore, for a meaningful comparison, you should add physical memory, or you're comparing apples and oranges.

 If you're used to a 500 meg RAM system in Windows, then you may want to consider1Gig of physical memory for a Ubuntu/Vmware combo.I **did not** find this necessary with Win98 (compact and relatively efficient), and running on a 2.4 Gig Pentium 4 single proc, I use only 500 megs total divided in half for the VMPlayer. 3D CAD is the most intensive thing I need on the Windows side, and it runs fine with this setup.

---

### Post by kavoura on 2008-01-08
I just installed VirtualBox and am installing Windows 98. The only downside is that Ubuntu has mounted the CD drive from the device /dev/scd1 and VirtualBox requires the CD to be the device /dev/cdrom. So I had to copy the Windows 98 CD to an ISO file before I could use it to install Windows 98.
Also you need to add your username to the vboxusers group. I used
```
sudo kuser
```
and then found the group vboxusers and added my username to it.
Then
```
sudo /etc/init.d/vboxdrv start
```
then run virtualbox from the menu and start adding virtual systems.

---

### Post by kavoura on 2008-01-08
It seems rather slow at times, maybe because I only have a 32-bit single core CPU.
The fullscreen mode does not make it go proper full screen, it has a large black border around everything.
To get in and out of fullscreen mode, press RightCTRL-F.

---

### Post by kavoura on 2008-01-11
My experience firstly was with Windows 98, as per previous message, and that did not work well at all, mostly because it would not load any drivers for making the screen resolution higher, nor did I get any sound.

But when running Linux distros as virtual systems, the virtual system runs just as well as a real system. Sound works well and the video is perfect. I was able to run live CDs from ISO files, and install to a virtual system. 

This is a great way to try out a new linux distro, especially if still in beta, without messing up hard drives, grub or lilo menus.

VirtualBox has been pretty good for me so far.

---

### Post by bhavi on 2008-01-11
Is there a processor emulator in open source?

---

### Post by gilf on 2008-01-11
This isn't a processor emulator per se, but a virtual machine -- a layer for running a guest OS.

If that's not what you meant I apologize.

If it is, then:

VMWare Server is Open Source
VMWare Tools are Open Source

VMware Player, I believe is not Open Source.

---

### Post by bharadwaj on 2008-01-12
> **ryanVickers said:**
> Vmware is complete garbage - its so slow just moving a window gets like 1 - 5 fps, and even the mouse is slow... even with all the fancy stuff your supposed to do, i don't remember I try not to :D

**problems:**
 -incredibly slow
 -feature lacking
 -complicated
 -after a while, would just randomly stop working... it just wouldn't open any more!
**up sides:**
 -possibly 1% more stable...

I too would highly recommend VirtualBox - some say its unstable, but only very slightly, ... I would say maybe 99% stability!! (which is better than real windows... ;))

**problems:**
 -possibly 1% less stable...
[B]up sides:
[/B] -although a bit picky at first, always works once you have it running (very easy!!)
 -very fast (runs 3D just as good as real windows)
 -tons of features!
VMware runs just better than VBox I completely disagree with you i have vbox which just fails to start. From where in the world would i expect it to run my Windows?

---

