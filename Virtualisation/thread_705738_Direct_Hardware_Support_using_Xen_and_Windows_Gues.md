---
title: "Direct Hardware Support using Xen and Windows Guest?"
date: 2008-02-23
forum: Virtualisation
---

### Post by T313C0mun1s7 on 2008-02-23
I have been away from the forums for quite some time as I have been forced into the Windows world for a while. I really want to come back to using Ubuntu as my primary OS, but there are some major roadblocks. Well until now hopefully. I may have found a solution, but I need the assistance of the community before I make the leap. I Just need more information and maybe some testing if possible. Thank you all in advance. Also, sorry in advance for the LONG post.

Here is the scoop. There are just some things that can not be done in a virtual machine because of the hardware emulation. For example, ripping and then burning CD and DVD blackups is problematic because you have no direct access to your burner. Also, you may have paid a pretty penny for that fancy video card, but in the virtual environment all you get is a cheap VESA knockoff. Lets face it, this can be a big deal since Windows has such a large user base there are programs that still have no true Linux alternative. Plus I am an IT outsource professional, so I get doubly stuck to the Windows world for client support.

For example. I have yet to find Linux software that will truly do what BlindRead/BlindWrite in paranoid mode does, and without direct access to the hardware I can not do it in a VM.

So I was reading that Xen basically allows direct hardware access rather than virtualized emulation of generic hardware. I also read that if you have a processor that supports it (I do, I checked) Xen 3 and up will allow for the running of unmodified OSes in the hypervisor (Windows XP Pro for example).

So the holy grail here would be being able to run Windows XP Pro SP2 (or SP3) as a guest OS on Ubuntu, and still have direct hardware access thus allowing me to still have full use of my video card, DVD burner, and hardware dongles (tied to software licensing) without any issues. Performance is still an issue of course. I run a lot of software that can be resource intensive such as the Adobe CS3 Master Collection and the software involved there, and Video encoding software. I am also fairly active with VoIP and sometimes need to trascode audio codecs in real time with various Windows virtual PBX software (although I prefer Asterisk).

So is this really now possible?? I mean can I install say a second Gig of RAM in my computer, build the latest Xen from source, and run Windows XP Pro while having direct hardware access? Has anyone here tried this? Any help is well appreciated. This is my primary workstation, I really want to make the leap and come back to Ubuntu (I was much happier), but I can not afford extensive downtime. Thank you all for any assistance, suggestions, or resources you can provide.

---

### Post by Sugi on 2008-02-23
This may not helpful, but I would like to comment on behalf of your thread.  I have not (or I may have) heard of Xen and it's virtualization of direct hardware.  I will have to give it a try.  I will report back in on that.  If it works flawless, or at least good, that would be exciting.

The issus thats keeping me from fully converting over to Linux and I say Linux, not Ubuntu.  Don't get me wrong, I love Ubuntu and have been for the last year and half if not longer, but thats the point of Linux.  Chooses. :)  I would to test Linux distros on my extra desktops.  Anyways, back to the point.  

Games.  That's what fully keeping me from converting over, and once again, don't  get me wrong.  I have been using Linux straight for the last 5 months.  No Windows until a week ago when my friend turned me on to Crysis.  Wow, that game is amazing and now, I want to reroll back to Oblivion, but I am having a hell of a time installing and tweaking Oblivion on Linux.  I must have lost about about 20 FPS in Oblivion if not more not even including any mods :( :(.  I have been able to play some games, Warhammer 40,000 Dawn of War Dark Crusade, Warcraft 3 Frozen Throne, Starcraft (i kinda like RTS a lot :)), Diablo 2, Lineage 2 (everyone should play this game), and soon to be Sonic.

Anyways, back to the point again, drop another Gig stick into your PC.  I have two Gigs of DDR2 and I can run Adobe Photoshop, Illustrator, and InDesign CS3 with no problem with VirtualBox.   I can run two of those applications at once.  Sometimes, it gets a little slow.  Though, I don't get the same performance that I would get in a native installation of XP, but for a graphic designer it woulds in a pitch and then some.

Quick Specs:
Core Duo 2.0 GHZ
2 Gigs DDR2


Sugi

---

### Post by T313C0mun1s7 on 2008-02-24
> **Sugi said:**
> 
Anyways, back to the point again, drop another Gig stick into your PC.  I have two Gigs of DDR2 and I can run Adobe Photoshop, Illustrator, and InDesign CS3 with no problem with VirtualBox.   I can run two of those applications at once.  Sometimes, it gets a little slow.  Though, I don't get the same performance that I would get in a native installation of XP, but for a graphic designer it woulds in a pitch and then some.

Quick Specs:
Core Duo 2.0 GHZ
2 Gigs DDR2


Sugi

Yea, Linux is a little more memory hungry than Windows is (excepting Vista of course), and I noticed before that I was always wishing for more RAM when I had an guest VM running. It would not be  a single stick though, more like two more 512Mb sticks. I am using dual-channel (dual-channel-enabled memory controllers utilize two 64-bit data channels, resulting in a total bandwidth of 128-bits) and I have four slots with only two occupied.

I have used a few different VM solutions under windows, but I only ever used VMWare Server under Linux. I have no experience with Xen outside of all that I have read - thus the point of this thread. If I was to use VMWare again I would dedicate a Gig of RAM to the Guest in the VM, and leave a Gig for the host OS. If I understand how the Xen hypervisor works correctly though, I don't need to do that using Xen. It should just dynamically use the memory available as needed. I still want the extra overhead however.

---

### Post by NullHead on 2008-02-24
I'm very interested in this subject too. I'll be keeping up with this thread for info on this subject. 

I'm in the same place as Sugi is. I love to play games and currently dual-boot because of 'em ... I'm a gamer first and a geek second. 

+1 for good idea! :D

---

### Post by Sugi on 2008-02-24
I quickly scan the Xen website.  It appears to be only a trial, but there is a free version.  Thoguh, I didn't check what's the difference between the paid vs the free version.  I wonder if anyone here has tired the paid version.

T313C0mun1s7,  I am currently thinking about making a new rig with linux in mind.  I am thinking about dropping a few gigs of ram in for visualization and gaming as well.  I have not used VMware for a long time now.  Isn't the VMserver the paid edition?

NullHead, I think it's the opposite for me.  Linux then Games, or Games during linux :)  but like I have stated before.  I have to switch over to Windows to play the games at their native speed.  Lineage 2 runs like crap for me now within linux. :(  Pretty sad, it should to be prefect with some FPS drops.

Sugi

---

### Post by T313C0mun1s7 on 2008-02-24
VMWare Server - Free
VMWare ESX Server - Not free

Xen - acquired by Citrix, but I think still open source, thus can be built from source[LIST]
[*]                                 Citrix XenServer Express Edition[LIST]
[*]Free
[*]Limited to Dual Socket, 4 Gig RAM, and 4 VMs
[*]Upgradable by simple add of adding license key[/LIST] 
[*]                                 Citrix XenServer Standard Edition[LIST]
[*]As above but Native 64 bit
[*]Multi-server management
[*]Fully Supported
[*]32 Sockets, 128 Gig RAM
[*]Unrestricted number of VMs[/LIST] 
[*]                                 Citrix XenServer Enterprise Edition[LIST]
[*]As Standard Edition plus Live Migration with Resource Pools
[*]CPU, Disk and Network Resource Controls for QoS[/LIST] [/LIST]I don't know my Xen history or version numbering, but I kind of get the impression it was the Citrix acquision and their Windows Terminal target market that pushed the ability takes full advantage of Intel VT and AMD V enabled x86-64 processors (on chip virtualization extensions) to allow for the running of Windows guests. Prior to this you could only run Linux/Unix like guests because you had to use a modified kernel. Thus proprietary OSes that you could not modify the kernel on would not run.

I can not make the leap unless I know this works as I hope. I have not been able to run anything other than Windows in my office for over a year now and thus have not been very active here. If either of you are active forum members, or know anyone that can help, please, PLEASE point them to this thread. I would love to start getting some good hard info on the viability of this, any possible roadblocks, and if it is not too much to ask - some real world testing. Thank you again.

---

### Post by fjgaude on 2008-02-24
The VMware Server is free... I've only used the one from their website, vmware.com, because of the apparent issues that so many have had with the .deb version in the Ubuntu repositories.

I'm a graphic designer using vmware server to handle WinXP and three or four Windows programs that I simply can't seem to let go of. See my signature.

I use only 2G of RAM but my main box is fast: allocating 512MB to the guest:

With CPU at 3.81 MHz (9 x 423), memory at 846 MHz (2.0 x 423), temp=28C, fan=1427 RPM, VCore=1.33
/dev/md32:
 Timing cached reads:   18154 MB in  2.00 seconds = 9090.26 MB/sec
 Timing buffered disk reads:  616 MB in  3.01 seconds = 204.93 MB/sec

As you can see. Now, the vm guest side seems just as quick as the host side, Ubuntu 7.10, 64-bit. I can use a quad core Intel 45nm chip but nothing I have uses more than two cores presently. All scanners, printers, USB devices work under the vm quest. VMware is mature without any bugs that I've run across. And it's free but not open source. So be it.

It seems Ubuntu is going the KVM route and dropping Xen. I watch as Hardy comes out. I test the Alpha 5 release... not finished but getting there.

---

### Post by T313C0mun1s7 on 2008-02-24
> **fjgaude said:**
> 
It seems Ubuntu is going the KVM route and dropping Xen. I watch as Hardy comes out. I test the Alpha 5 release... not finished but getting there.

Yes, and here in lies the problem (from the stickied getting started with virtualization thread)

> Each virtual machine has private virtualized hardware: a network card, disk, graphics adapter, etc.As I stated in my original post, it is not good enough to run Windows on virtualized hardware, I need Windows on MY HARDWARE. So I can give the guest OS direct access to my DVD burner, video card, hardware dongles, etc.

Dual boot is not an option either, because I need to switch back and forth too much. If I was just booting to play a game sure, but I am not. I need to have my machine up and running and move back and forth between my daily task software such and e-mail, and the Windows only stuff, where I use Photoshop CS3 and Dreamweaver CS3. Sorry but bluefish, N|vu, and GIMP just don't cut it and I don't want to take the time to learn a bunch of new software so I can continue to do my work. I also have a Windows only remote support client the I use to assist my clients, and many, many other ties to Windows administration, networking, multimedia, web design, and VoIP softwares.

Can Xen do this, or should I just forget the whole thing and just keep using XP Pro until I eventually am forced into upgrading to the [FONT=Arial Narrow][COLOR=DarkRed]*[CENSORED BY      vBulletin]*[/COLOR][/FONT] of all OSes Vista Ultimate? I already make fair use of cross platform software. I use Firefox, Thunderbird, and use Thunderbird as my IMAP client for Gmail. I use Video LAN for my media player, etc. It all seems to run as well or better to me on a Linux desktop. I also have come to the personal conclusion that Suse made desktop Linux viable, and Ubuntu made it truly usable. This only holds true if you are not already tied to Windows, and as an IT person that does ALL of the technology work for many small to medium businesses I am locked in.

So Xen running Windows XP with direct hardware access - is this something than can be done, and work the way I am hoping, or do I just resolve myself to live in a Window always looking out?

---

### Post by fjgaude on 2008-02-24
I do believe I understand your feelings... I run InDesign CS and it runs good in vmware server, as do the other Windows apps in my signature.

Access to hardware other than through the vm seems to be an issue. When I think of it, the ability to virtualize, or whatever word we use, hardware is the thing that has made VMware a huge company.

My video card is a nvidia 7600 GS and it seems to be snappy under vmware. I really feel blessed to be able to do it all the way I do.

What's wrong with using Ubuntu software for burning DVDs and the like? The new burner in Hardy seems to be all the rage at the moment. I don't use it as Hardy is not released yet.

I would suggest trying a vm with WinXP and seeing just how all your apps run. Photoshop has no trouble.

Let us know what you come up with, eh?

---

### Post by T313C0mun1s7 on 2008-02-24
> **fjgaude said:**
> I do believe I understand your feelings... I run InDesign CS and it runs good in vmware server, as do the other Windows apps in my signature.

Access to hardware other than through the vm seems to be an issue. When I think of it, the ability to virtualize, or whatever word we use, hardware is the thing that has made VMware a huge company.

My video card is a nvidia 7600 GS and it seems to be snappy under vmware. I really feel blessed to be able to do it all the way I do.

What's wrong with using Ubuntu software for burning DVDs and the like? The new burner in Hardy seems to be all the rage at the moment. I don't use it as Hardy is not released yet.

I would suggest trying a vm with WinXP and seeing just how all your apps run. Photoshop has no trouble.

Let us know what you come up with, eh?

I have done this, it is exactly why I had to switch back to running native Windows.

I don't know if you no what a dongle is. It is a hardware device that some software tie the license to. No dongle, no program. Also there is no Linux alternative to BlindRead/BlindWrite in paranoid mode, as I stated earlier. There is also no true Linux alternative to DVDFab Platinum, or ProCoder3. Heavy 3D rendering apps such as Maya, are not going to work. VoIP also becomes an issue because unless you have a separate DSP processor (and even if I did I would not have access to in in a virtual machine) the Digital Signal Processing is very processor intensive and will take a hit in a VM that will cause audio drops, jitter, and echo.

No, unfortunately the ONLY option would be one that does NOT virtualize the hardware environment and instead uses some form of paravirtualization. The downside here is the guest OS must support all the same hardware that the host OS is running. Great, as this is exactly the case for most of us. Most of us are running Ubuntu on the same hardware we would run Windows on. Thats what makes what I am looking for such a Holy Grail so to speak. It is not enough to just run *MOST* Windows programs well, as I have already stated I have specific applications that require DIRECT hardware access.

Also I have tried WINE, as it runs windows apps natively, but that induces it's own set of issues which I don't wish to get into as some of them are quite technical. Suffice it to say the Windows application support is not very broad, especially when getting into vertical market software, and there are many non-solvable issues in the tradeoffs between WINE native dlls and Windows native dlls.

---

### Post by T313C0mun1s7 on 2008-02-24
I have posted a link to this thread on the [EMAIL="xen-users@lists.xensource.com"]xen-users@lists.xensource.com[/EMAIL] mailing list, and received a reply. I believe it answered my questions.

Here is the reply I received:
[quote="jim burns"]
I'm afraid you're a little ahead of the curve. Running Windows means full virtualization, which means performance loss. While the situation is getting better with hard disk/block file drivers and net drivers (see PV drivers for HVM from James Harper, Halsign, and proprietary approachs to PV drivers from various distros), the console is what really still suffers.

While direct hardware access is possible with pciback (hiding the pci device from the dom0 and passing it to a guest) in *theory*, in practice, read this list (xen-users) for awhile. People are getting it to work for some cards, and not others. Even if you can get a video card to pass through to your guest, that means you need a 2nd video card for your dom0 (or at least it makes setting things up a lot easier). And that's the situation for paravirtual (PV) guests. Support for passthrough for HVM is brand new and still being worked out in xen 3.2.x. Additionally (I believe) it requires Vt-d support to remap dma requests. Your processor may support intel vmx/Amd svm to get full virtuallization to work, but Vt-d is brand new. Even if you do have that hardware, better get your hacking shoes on![/quote]

My Reply:
[quote="T313C0mun1st on xen-users list"]
[quote="jim burns"]I'm afraid you're a little ahead of the curve.[/quote]...> Support for passthrough for HVM is brand new and still being worked out in xen 3.2.x. Additionally (I believe) it requires Vt-d support to remap dma requests. Your processor may support intel vmx/Amd svm to get full virtuallization to work, but Vt-d is brand new. Even if you do have that hardware, better get your hacking shoes on!
This is exactly the information I was looking for. Based on your response I guess that my answer would be "not yet" so to speak. I will hold off on trying this just yet, but I will watch Xen closely and wait with baited breath for the day this might become possible. I have my doubts if it will come to fruition though. Now that Cirtix is involved, my goal is quite a way off from the Citrix push. Their website seems very geared towards server consolidation and thin client services; as would be expected, that is were the money is going to be.

I don't know how much the open source end of things are steered by the commercial side, but the situation I describe really would be the Holy Grail. I see it as a way to prove this platform for VM as the undisputed champion, and a way to rise above VMWare. If that were to happen the commercial values would certainly follow.

I will stay registered to the list for a while, as I imagine that I can learn quite a lot here - even if I am not ready to jump into the product quite yet.

Thank you Jim. As stated earlier I will report this back to the other forum.[/quote]

---

### Post by fjgaude on 2008-02-25
Good things come to those who are patient. Thanks for sharing your discoveries with us.

---

### Post by Ares Drake on 2008-04-22
Hey there.

I can imagine how you feel T313C0mun1s7. Currently I am trying to accomplish the same as you want: A Xen3.2 host (=Dom0) with hardware passthrough to guests (=DomUs). I want to use a SCSI Controller for my Scanner in Win and a SATA controller in Solaris. The use of my second graphics card and a TV Card in a DomU would be a plus. However it is as you say: brand new uncharted territory. What I found out till now:

[LIST]
[*]Graphic
[INDENT]Passthrough of graphics card is a little more difficult as those directly access the main memory. I have seen a report suggesting it works between paravirtualised guests. As of now, Windows cannot be paravirtualised. But graphiccard passthrough can be made to work with linux paravirtual guests. For me this would be enough though it probably doesn't help you. Reason it only works in "virtualisation-aware" aka paravirtual guests is that those see all the real main memory and know what their share is - Windows guests see only their share. So the memory access of the graphics card would screw up as memory adressing would missmatch.[/INDENT]
[*]Windows
[INDENT]With Xen3.2 it should be possible to passthrough the SCSI Card and the USB controller to Win. So your (USB?) dongles should work. For good Windows Performance in Xen you need to install special drivers in Windows however - much like the vmware tools in Vmware. I have not found working drivers for ubuntu's xen yet  - though in the mailinglist answer you postet was a hint - I'll check it out. Plus, with 3.2 the package xen-ioemu-3.2 is missing - i don't know perhaps it is obsolete now with 3.2? However all tutorials on how to install Windows on Xen depend on that one. So the install doesn't work right now - or rather I don't know how to install windows in xen3.2.[/INDENT]
[/LIST]

Documentation is *VERY* sparse atm. I'd really like to get this to work. Though because of other projects my time is rather limited for the next 4 weeks. In case some of you are interested as well (and own IntelVT / AMD Parcifica enabled machines) we might just go ahead and collect and share our findings, problems and solutions here. If enough people are interested and participating (and it seems so) and everyone just helps a little bit, it might work  out perfectly. So please don't be afraid to "put on the hacking shoe", together it is probably doable. Just post your findings here so that others can carry on where you run into a roadblock...

It would be more than great to get it to work!

---

### Post by T313C0mun1s7 on 2008-04-22
Most legacy hardware dongles are plugged into the parallel port. For a while developers thought this was the most effective way to thwart software piracy.

One of my personal biggest concerns is the ability to use windows software that has no Linux counterpart such as Blindwrite, and some DVD ripping and Disk burning stuff. WAY BACK IN THE DAY printers were individually controlled by the software that printed to them, and it did not take long for people to figure out that moving that driver out of each individual software program and into the OS was the way to go (remember DOS printing), unfortunately optical disk burning still holds the drivers for every drive it needs to access in the userspace software, not the OS. This means userspace software needs direct access to the drives to burn CDs and DVDs, not a generic emulated drive. There are no other programs I have found that does the same thing that Exact Auto Copy in paranoid mode does, or Blindwrite, or DVDFab Platinum - they just don't exist in Linux.

---

### Post by Ares Drake on 2008-04-22
In theory you should be able to passthrough anything you can see by lspci. In a terminal just run sth like "lspci -vv > ~/lspci.txt" and have a look at that file in your home dir. So while you probably won't see your CD-ROM / Burner in there, you can passthrough the IDE / SATA Controller. I don't know if it works for single ports or just the whole bunch, so you might need a second controller - however some boards come with a second raid controller or sth.
Then you would not see the CDROM in linux but would have native and complete control in your virtual Windows.

Im trying to setup the GUI virt-manager as an easy way to manage the virtual machines. Once I got it running, I can test the above and will post results.
I seem to be stuck at this error message: [https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/198957](https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/198957)
though I got the libvirt-bin installed. No clue whats missing...

---

### Post by yanndinendal on 2008-05-14
> **Ares Drake said:**
> Plus, with 3.2 the package xen-ioemu-3.2 is missing - i don't know perhaps it is obsolete now with 3.2? However all tutorials on how to install Windows on Xen depend on that one. So the install doesn't work right now - or rather I don't know how to install windows in xen3.2.
Hi, I was looking for xen-ioemu-3.2 too, as xen-ioemu-3.1 is conflicting with every other xen 3.2 package, and I found nothing about it but your post... 
Anyway, I've now found the answer here :
[quote=Chuck Short, in changelogs]xen-3.2 (3.2.0-0ubuntu1) hardy; urgency=low

  * Initial release based on 3.2.0 rc4.
  * Updated build-depends.
  * Added pciutils-dev to build-depends.
  * **Dropped xen-ioemu now in xen-utils.**
  * Dropped xen-docs.
  * Dropped security fixes since it is now apart of upstream.
  * Moved from dpatch in-favour of quilt.

 -- Chuck Short <zulcss@ubuntu.com>  Fri, 11 Jan 2008 14:28:08 -0500[/quote]
So it should work... but now I have another problem : I can't create any domain. I have the same problem on a Debian etch with xen 3.0...

```
root@MVDS1:~# xm create /etc/xen/VDS01.hvm
Using config file "/etc/xen/VDS01.hvm".
VNC= 1
Unexpected error: <type 'exceptions.OSError'>

Please report to xen-devel@lists.xensource.com
Traceback (most recent call last):
  File "/usr/sbin/xm", line 10, in <module>
    main.main(sys.argv)
  File "/usr/lib/python2.5/site-packages/xen/xm/main.py", line 2535, in main
    _, rc = _run_cmd(cmd, cmd_name, args)
  File "/usr/lib/python2.5/site-packages/xen/xm/main.py", line 2559, in _run_cmd
    return True, cmd(args)
  File "<string>", line 1, in <lambda>
  File "/usr/lib/python2.5/site-packages/xen/xm/main.py", line 1309, in xm_importcommand
    cmd.main([command] + args)
  File "/usr/lib/python2.5/site-packages/xen/xm/create.py", line 1190, in main
    dom = make_domain(opts, config)
  File "/usr/lib/python2.5/site-packages/xen/xm/create.py", line 1053, in make_domain
    os.kill(vncpid, signal.SIGKILL)
OSError: [Errno 3] No such process
```

---

### Post by lex1 on 2008-05-14
not the answer your looking for but if you go to howtoforge.com
you will see howto of xen on hardy if this is not specific to you you can ask a question in the forum


lex1

---

### Post by hdtvrocks on 2008-05-15
Hi guys,

Picked up an Asus P5E-VM DO Q35 board with VT-d to give Xen a go. My goal is to run an XP domU and give direct access to my DVB PCI cards to the XP guest. Don't need actual video playback, it's just recording and streaming to media clients. Anyhow, I noticed in my mobo manual that "Virtual Appliance" is supposed to be an option to turn enable or disable, but my bios doesn't give me that option and only gives me the Version. 

Been following the Xen 3.2.0 on Hardy 8.0.4 How-To and managed to get a Xen SDL window to show, but it keeps failing with the error:

Error: Device 768 (vbd) could not be connected. losetup /dev/loop11 /xen/images/WinXP.img failed

I can't seem to get past this, let alone try VT-d.

UPDATE: According to the guys on #xen 2.6.24 isn't well supported and was forward patched for Xen. It is possible HVM support for Windows is broken for 2.6.24. I'm going to have to revert to 2.6.18 and will likely try a different distribution.

---

### Post by hdtvrocks on 2008-05-16
Just to let people know, I struggled with getting OpenSUSE 10.3 installed on my multi-HD system, finally got it running. Creating a Windows HVM DomU is GUI driven are simple as pie. BUT Xen only officially supports 2.6.18 and the OpenSUSE binaries are Xen 3.1.0. So while I had a stable Windows XP DomU, there's no VT-d support. Wasted another day, and now I'm onto CentOS 5.1 2.6.18 with the mercurial repo of Xen.

---

### Post by yanndinendal on 2008-06-18
> **yanndinendal said:**
> ```
root@MVDS1:~# xm create /etc/xen/VDS01.hvm
Using config file "/etc/xen/VDS01.hvm".
VNC= 1
Unexpected error: <type 'exceptions.OSError'>

Please report to xen-devel@lists.xensource.com
Traceback (most recent call last):
  File "/usr/sbin/xm", line 10, in <module>
    main.main(sys.argv)
  File "/usr/lib/python2.5/site-packages/xen/xm/main.py", line 2535, in main
    _, rc = _run_cmd(cmd, cmd_name, args)
  File "/usr/lib/python2.5/site-packages/xen/xm/main.py", line 2559, in _run_cmd
    return True, cmd(args)
  File "<string>", line 1, in <lambda>
  File "/usr/lib/python2.5/site-packages/xen/xm/main.py", line 1309, in xm_importcommand
    cmd.main([command] + args)
  File "/usr/lib/python2.5/site-packages/xen/xm/create.py", line 1190, in main
    dom = make_domain(opts, config)
  File "/usr/lib/python2.5/site-packages/xen/xm/create.py", line 1053, in make_domain
    os.kill(vncpid, signal.SIGKILL)
OSError: [Errno 3] No such process
```Ha :/ my mistake ! In fact, this error appears when the disk image hasn't been created before creating the DomU... So this was my fault, but the error message isn't explicit at all! 
Hope it will help somebody. :)

---

