---
title: "VMware vs VirtualBox vs QEMU?"
date: 2007-05-04
forum: Virtualisation
---

### Post by Sunnz on 2007-05-04
Just wondering how these compare?

Performance wise? When I tried VMware I always had to install VMtools on the guest OS, which is a bit of pain if they haven't got it working the the guest OS you want to install.

Features wise? Can it boot from an existing partition? Can it boot from bootcamp?

Any other difference between these?

---

### Post by Bloodfen Razormaw on 2007-05-04
VMware is far superior to the others from a technical perspective.  It has the best feature support and performance.  QEMU has the advantage of being free software.  Traditionally the kernel module required for QEMU to compete on performance was proprietary but it was recently freed.  VirtualBox doesn't have VMware's speed or features, and it isn't free either.

---

### Post by MRiGnS on 2007-05-04
> **Bloodfen Razormaw said:**
> VirtualBox doesn't have VMware's speed or features, and it isn't free either.

It's free and open source

---

### Post by Bloodfen Razormaw on 2007-05-04
> It's free and open source
The only version that was freed was crippleware.  Even the proprietary version can't match VMware's features, with what features it has removed it is very unimpressive.  It's practically trial software.

---

### Post by steven8 on 2007-05-04
> **Bloodfen Razormaw said:**
> The only version that was freed was crippleware.  Even the proprietary version can't match VMware's features, with what features it has removed it is very unimpressive.  It's practically trial software.

Wow, what features aren't there in VirtualBox.  It's the only one I've tried, and it works great for me.  I'm very happy with it.  I know the personal version is the free one.

---

### Post by MRiGnS on 2007-05-04
well the proprietary version is free to use for personal usage.

vmware has no open source version only the free vmwareplayer and server. these are crippled.

> **steven8 said:**
> Wow, what features aren't there in VirtualBox.  It's the only one I've tried, and it works great for me.  I'm very happy with it.  I know the personal version is the free one.

If you've installed it via the binary you got all features. the binaries are the proprietary version which is free to use.

the open source version lacks some features but has to be compiled of tarballs

```
Closed-source features ¶

The following list shows the enterprise features that are only present in the closed-source edition. Note that this list may change over time as some of these features will eventually be made available with the open-source version as well.

    * Remote Display Protocol (RDP) Server 

    This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

    * USB over RDP 

    This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

    * Shared Folders 

    With the use of Shared Folders, users can share directories on their host system with guest systems.

    * iSCSI initiator 

    VirtualBox contains a builtin iSCSI initiator making it possible to use iSCSI targets as virtual disks without the guest requiring support for iSCSI.

```

---

### Post by H.E. Pennypacker on 2007-05-04
> **Bloodfen Razormaw said:**
> The only version that was freed was crippleware.  Even the proprietary version can't match VMware's features, with what features it has removed it is very unimpressive.  It's practically trial software.

I am not sure where you're getting all this, but you should take into account how well VirtualBox has been working for many of us.  I can't even tell of a speed difference between running Windows XP under VirtualBox, and running Ubuntu (of course having VirtualBox on top of Ubuntu). 

It is so fast, I seriously can't tell the difference between running XP itself on its own hard drive, and running it under VB.  I am not saying that VB is fast.  I am saying I notice no difference in speed. 

I am very pleased with the speed.

As far as features, VB has everything I need.  Does it run XP, and does it run it well?  Yes.  Sounds like it includes everything I need.  See...we all have different needs here.

---

### Post by Bloodfen Razormaw on 2007-05-05
> **H.E. Pennypacker said:**
> I am not sure where you're getting all this, but you should take into account how well VirtualBox has been working for many of us.  I can't even tell of a speed difference between running Windows XP under VirtualBox, and running Ubuntu (of course having VirtualBox on top of Ubuntu). 

It is so fast, I seriously can't tell the difference between running XP itself on its own hard drive, and running it under VB.  I am not saying that VB is fast.  I am saying I notice no difference in speed. 

I am very pleased with the speed.

As far as features, VB has everything I need.  Does it run XP, and does it run it well?  Yes.  Sounds like it includes everything I need.  See...we all have different needs here.
Try using it in a production environment and see if it is still fast enough.  Home users don't need fast virtualization.  On the other hand, virtualization is very important to businesses (which are the primary target for virtual machine software) and VirtualBox is not nearly fast enough for a production environment.  It is much slower than QEMU, and a mile behind VMware.  Just because it works well for limited purposes doesn't mean its the better for more intensive tasks, or even the best for its own task.  VirtualBox simply has no reasonable niche.  A performance-conscious user can get many more features and optimal performance from VMware.  A user who wants a free software solution can get the same from QEMU.  And then there is VirtualBox, which lacks features like 64-bit or SMP guest operating systems, misses some hardware support entirely, and has no 3D acceleration support, yet also only provides a subset of functionality freely.  Considering one can get a better virtual machine without licensing issues out of QEMU, or the best virtual machine with many of the same licensing issues out of VMware, there isn't much place for VirtualBox.

---

### Post by maniacmusician on 2007-05-05
VBox, works perfectly for me. While Bloodfen Razormaw may be right about it not being the leader in production environments, we have to consider that it is the newest of all three of those products, so there's a lot of work to be done on it. Personally, I've experienced significant performance increases with VirtualBox as compared to VMWare, so I've let go of VMWare in favor of VBox. Plus, it's small, simple, and doing pretty well on features considering their recent startup. 

So for me, VBox wins out.

---

### Post by miggols99 on 2007-05-05
Tried VMware, but it was slow. Didn't want to use Virtualbox, because I'd had to build from source. So I looked at Qemu. All I needed was a VM for winXP, nothing else much, and was easy to set up. So I choose Qemu.

---

### Post by FoolsGold on 2007-05-05
Only ever tried VMWare. Not a legit copy, but then again my XP wasn't either, so...

Then again I am trying to become more legit, so I'll probably try something like VirtualBox from the responses here.

---

### Post by Bloodfen Razormaw on 2007-05-05
> Personally, I've experienced significant performance increases with VirtualBox as compared to VMWare, so I've let go of VMWare in favor of VBox. Plus, it's small, simple, and doing pretty well on features considering their recent startup. 
 
 So for me, VBox wins out.
You gave reasons for choosing it over VMware, but not QEMU.  Given that QEMU provides a more mature virtualization package, is supported in the default kernel release with KVM, with a richer feature set and better performance without proprietary restrictions, why choose VirtualBox over QEMU?

---

### Post by starfry on 2007-05-06
I've used VirtualBox and VMWare Player.
I use VMWare Player to run my native XP install in a VM when booted into Ubuntu. I can still choose to boot my XP natively too, so it gives me the best of both worlds.
I hae used VirtualBox to run a trial of VIsta and also to try and get a seamless Ubuntu/XP destop working (as per this thread: [http://ubuntuforums.org/showthread.php?t=433359)](http://ubuntuforums.org/showthread.php?t=433359)). While VirtualBox works, I can't get the seamless thing to work as expected, but that is another story.
VMWare Player can use a real hard disk in a VM, allowing you to boot your native XP in a VM. You can't do this with VirtualBox.
I find my VMWare Player system to be slow. Maybe this is because I have loads of things installed on that XP. Time will tell as I play more - I've just started to evaluate this stuff.
I think the VirtualBox interface, with its RDP facility is great, but it is too early to make a choice as to which is best. Right now, they each have there advantages for me.
I have not used QEmu.

---

### Post by jiminycricket on 2007-05-06
I also like Virtualbox because it's easy to install and the interface is the same on Windows and Linux hosts, but I don't think Qemu's slow anymore if you install the newly GPL'd kqemu accelerator (kqemu-common I think) in Feisty and Gutsy universe.

---

### Post by SlCKB0Y on 2007-05-08
> **Bloodfen Razormaw said:**
> Try using it in a production environment and see if it is still fast enough.  Home users don't need fast virtualization.  On the other hand, virtualization is very important to businesses (which are the primary target for virtual machine software) and VirtualBox is not nearly fast enough for a production environment.  It is much slower than QEMU, and a mile behind VMware. 

Got some benchmarks for us to see? I'm really curious to get at least a somewhat objective speed comparison between all these virtual machines. From the way you are speaking I am sure you would have done some study or have something to back up your claims. I'd be really interested to see these.

---

### Post by kaamos on 2007-05-08
Since it was missing from the poll, I'll just answer here.. KVM all the way!

---

### Post by DarkOx on 2007-05-08
> Given that QEMU provides a more mature virtualization package, is supported in the default kernel release with KVM, with a richer feature set and better performance without proprietary restrictions, why choose VirtualBox over QEMU?

I can't speak for the other fellow, but the reason why I chose VirtualBox over QEMU is that KVM only offers better performance if your computer supports it. My computer runs windows in VirtualBox just fine, but there's a noticeable performance decrease using QEMU, since I can't use KVM.

---

### Post by maniacmusician on 2007-05-09
> **Bloodfen Razormaw said:**
> You gave reasons for choosing it over VMware, but not QEMU.  Given that QEMU provides a more mature virtualization package, is supported in the default kernel release with KVM, with a richer feature set and better performance without proprietary restrictions, why choose VirtualBox over QEMU?
I haven't tried QEMU. From the impression that I got by watching people talk about it, it seems to be a bit of a hassle to set up properly. Also, VirtualBox is, in part, based on QEMU. They do share some code. I'll be honest though; I don't know much about QEMU/KVM. I don't know what kind of a featureset they posess, I don't know if they really do perform better, or anything like that. VirtualBox seems to offer me all the options that I need, and has reasonably performance. I may be inclined to switch if there are enough benefits, of course. But for now, my choice is based purely on convenience.

---

### Post by MRiGnS on 2007-05-09
[http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html](http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html)

there are benchmarks for vb qemu and vmware.


virtualbox is btw based on qemu.

---

### Post by VorDesigns on 2007-05-09
VMWare came out of the box and into production years ago.  Then when server and player came out free, off of the site and into production last year.
Simple to use most of the time, the VM appliances available for testing are great.
My only real complaint for VMWare is that there is no real support for running high end games on the guest OS.

---

### Post by aryah on 2007-05-25
> **MRiGnS said:**
> [http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html](http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html)

there are benchmarks for vb qemu and vmware.


virtualbox is btw based on qemu.

these hardly support the initial proclamations on the thread how vmware is superior to all others without question, and these are actually tests. If im not mistaken, till recently, vmware forbade in his EULA to ever publish any benchmarks of vmware. Ive heard they are nevertheless not a bad free software citizen, but IMO this is too deep in the system to use anything but completely free software sollution (as opposed to say, games)

Id use Qemu+kqemu  (thats what I do, though very rarely, wine is regularly enough even if there isnt a good native replacement). Or if the drivers are impractical, the free software version of virtualbox.

---

### Post by starcraft.man on 2007-05-25
I have to cast my vote for VMware. Been a user a long time and very happy with it, I don't know the exact features not present in Virtual box, I do know some of my favourites (I have workstation copy) are snapshots (take a back up of way it is at an instant), cloning feature and also the team networking feature. I don't think those 3 in Vbox, I could be wrong. It's a very powerful and refined platform. I will give virtual box a shot, I was aiming for a leaner one just to use when not needing VMware's feature set. I haven't seen any slowdown with VMware just to note.

Edit: Virtual box wouldn't happen to be able to open VMDK files would it? Then I could access my VMs with it, if not might be somewhat of a pain to make em over again...

---

### Post by bodhi.zazen on 2007-05-28
> **Bloodfen Razormaw said:**
> Try using it in a production environment and see if it is still fast enough.  Home users don't need fast virtualization.  On the other hand, virtualization is very important to businesses (which are the primary target for virtual machine software) and VirtualBox is not nearly fast enough for a production environment.  It is much slower than QEMU, and a mile behind VMware.  Just because it works well for limited purposes doesn't mean its the better for more intensive tasks, or even the best for its own task.  VirtualBox simply has no reasonable niche.  A performance-conscious user can get many more features and optimal performance from VMware.  A user who wants a free software solution can get the same from QEMU.  And then there is VirtualBox, which lacks features like 64-bit or SMP guest operating systems, misses some hardware support entirely, and has no 3D acceleration support, yet also only provides a subset of functionality freely.  Considering one can get a better virtual machine without licensing issues out of QEMU, or the best virtual machine with many of the same licensing issues out of VMware, there isn't much place for VirtualBox.

I agree 150% VirtualBox is NOT ready for what you are terming a "production environment", but I would disagree with the statement "VirtualBox simply has no reasonable niche."

VirtualBox wins out for home users new to virtualization  looking for a open source solution with a reasonable gui interface. I know quemu has a gui interface, and I agree it is powerful, but Virtual Box is MUCH easier for users new to virtualization.

Hat's off to VirtualBox for a simple, easy to use and understand GUI :)

VirtualBox is also not as mature as VMWare, but it is under rapid development and I think they are beginning to see the advantages of open source. It remains to be seen, but I think VirtualBox will give BOTH quemu and VMWare a "run for the money" for non-production environments.

In time it may even give VMWare a run for the money in Production environment ...

---

### Post by starfry on 2007-07-16
I guess they all have their pros and cons.

My favourite right now is QEmu, as it works well and I can control it from the command line easily. I have yet to install KQEmu to get the speed increase but will try that soon.

I like Virtualbox too, but I don't like the fact you have to create VMs before you can run them: it seems to be an unnecessary step. Contrast with QEMu where you can just bung the parameters on the command line and off it trots...

I've used VMWare player to run a native XP install which was good, but I haven't looked further into vmware.

I've also heard of Xensource but this requires a tricky set-up of the host which I decided to steer clear of.

I think if you are a "noob" and want something pretty that "just works" then go Virtualbox. However, anything more and I think QEmu is the way to go...

---

### Post by runningwithscissors on 2007-07-16
QEMU is nice. I've been using it for a long time.

Only problem could be that it'll only compile with gcc3, but I maintain a seperate gcc3 toolchain anyway, so it's cool.

---

### Post by CPImmanuel on 2007-09-26
I have not tried VMWare yet, although I have heard here and in other forums that it is technically superior to the others. I had no trouble setting up VBox, and I have XP running under Ubuntu. This is blazingly faster on a slower machine than Vista running on a super fast Thinkpad. So I am planning to migrate completely to Linux using VMs for running those windows applications that I need that do not run under Wine.  Vbox was a breeze to set up and once i figured out how to get USB support working, I became a happy camper. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

Regards, 
Paul Immanuel

---

### Post by HermanAB on 2007-09-26
I have actually tried them all.

Virtualbox is based on Qemu, so speed wise they must be the same.  Some people perceive it as fast or slow, but that is depending on whether they have the accelerator kqemu installed or not.

Without acceleration, Qemu/Vbox is slower than VMware, but with acceleration it is faster.

To me the clincher is whether it can run the Operating Systems that I need to run and Qemu/Vbox cannot run Win2003.  It installs OK and runs for a while and then it crashes.  Consequently I use Vmware.

However, if you only need WinXP, then I'd suggest using Qemu/Vbox.

---

### Post by thisllub on 2007-09-26
I have used VMWare for about 2 years. The installation problems with newer kernels seem to extend to problems running with the newer kernels. I do use it in a production environment on SUSE 10.2 machines. 

I have only recently installed VirtualBox. It runs beautifully on my laptop in seamless mode far better than any VMWare install. I am a convert. It won't run at all on this machine, neither does VMWare but I suspect the low latency kernel might be the problem.
I tried QEMU on Fedora 7 and found it so slow as to be unusable.

I might use Xen but I would like a GUI so it is out of the question - no NVIDIA support.

On balance a vote for VirtualBox.

---

### Post by Frak on 2007-09-26
Parallels then VMware

---

### Post by demonbane on 2007-10-09
I've used VMWare for about 6 years now, I've been using virtualbox for a little over a month, and I've been using Xen for about a year. If you need to run multiple machines with a simple admin interface with different OS's and different architectures, VMWare is the only way to go right now.

Xen has some wonderful multi-machine features, but they largely go out the window when you get into running a Windows guest on them. And, as stated earlier, Xen has no direct GUI support. But if you're running primarily Linux guests on it nothing else comes close in terms of performance.

VirtualBox has really blown me away for simple desktop use. It's about as full featured as VMWare, the interface is actually better in my opinion, it has Seamless Mode, which VMWare doesn't have yet, and best of all, it's a much cleaner install. There's a single kernel module to load and you're done. With VMWare you've got 4 different kernel modules and a handful of daemons running at all times.

Also, from a pure usability perspective, VirtualBox is much more responsive than VMWare when running an XP guest. I've seen some benchmarks which show VMWare being slightly faster at processor intensive tasks, but as far as how USING the OS feels, VirtualBox feels much snappier to me.

So what it comes down to:

If you want to:

1) Run a Linux host, with a bunch of Linux guests at max performance -- Xen, no question
2) Run a Linux host, with a Windows XP guest for basic desktop use -- VirtualBox
3) Run a collection of different guests on different hosts, with an assortment of guests on different architectures and OS's, and have an easy way to manage them all, and get good server performance out of them -- VMWare no question.

Right now there's no way to run multiple Windows guests in a processing-heavy production environment without using VMWare. If you're going to be using Linux guests, look no further than Xen. And, if you're just a desktop user than needs a snappy VM to run XP in without doing a bunch of fancy graphical stuff, look no further than VirtualBox. They're all good at different things, so just pick based on what it is that YOU want to do.

---

### Post by AndyCooll on 2007-10-09
I've just had to give my vote to VMware. My heart is with VirtualBox but my head (for the moment) is with VMware. 

Just tried running the latest Football Manager 2008 demo. It simply won't run under my XP VirtualBox image. The games security keeps telling me its detected a virtual environment and to install a native copy. With VMware however the game runs fine. Up to that point I've been quite happily using VirtualBox when looking at other distros.

I use XDMCP alot. I have an old laptop and a new box upstairs in the office. This works great. And VirtualBox (with GuestAdditions installed) will happily display a guest full screen even when using XDMCP. 
I've not used VMware for ages, but it won't. Maybe there's a tweak I've got to make to force it. 
This is a nuisance since the game runs full screen and when it's in a window you're constantly having to use the scrollbar to move up and down the screen.

:cool:

---

### Post by siepo on 2007-10-11
In my experience, VMware and VirtualBox are both fine. I only tried Qemu years ago, on a powerpc, before it became a serious option. For simple desktop use, VirtualBox will probably be fine. For gaming or heavy-duty production work, I have no idea.

I have been a happy user of VMware workstation for years, running various Windows versions. The main things I do with virtual machines is testing scripts and providing tech support to Windows-using colleagues.

But when it became time to upgrade, I didn't want to pay money while there existed several good free alternatives. I picked VirtualBox, both because I like open source and because even the open source version isn't crippled in any way that matters to me.

As others remarked, basic installation is a lot simpler with VirtualBox. On the other hand, it took some work to configure VMware-style host-only networking with VirtualBox, but once it was done, it worked just fine. I also experience some minor interface glitches with the keyboard and the mouse pointer, but nothing show-stopping.

---

### Post by vanDrunen on 2007-11-25
I have been using Qemu (with and without KVM and Kqemu) and VMware (commercial and -player) for a few years and have tested Virtualbox for a few months now.
The best VM to use depends a lot on what you want to do with it. All my experience goes to running Windows 2000, XP and 2003 on top of a Debian/Ubuntu host. Here's some comments on each of these VM's:

*** QEMU ***
Qemu without KVM or kqemu is extremely slow. Check if your CPU supports hardware virtualisation and use KVM whenever possible!!!
In "raw" computing Qemu with KVM outperforms VMware and VirtualBox with ease. It has very little overhead (CPU and memory wise) and is very stable.

The downside of Qemu is that it emulates a really crappy videocard (cirrus 
logic) and the graphics performance is really bad (mouse lag).
If you would run a Windows server in a "headless" virtual machine though and then log on to it using RDP (can be "seamless") then the crappy graphics-card emulation is not a problem at all and the better "raw" performance is a huge benefit!

+ The best "raw" performance
- crappy graphics emulation when running full-screen or windowed
!!! Best used as a server for remote desktop connections (works very well with seamless RDP)

*** VMware ***
VMware is slower than Qemu with KVM in "raw" computing power and without the "guest addons" (the way it is distributed in VMware-player) the graphics are just as crappy as with Qemu.
The commercial version comes with guest add-ons that contain windows drivers for improved performance. These guest add-ons (an iso image with drivers) can also be installed in VMware-player which will give you (almost?) the same performance!

VMware so far is the only VM that has good direct-draw and even some (limited) direct-3D acceleration. You'll see the most benefits of VMware when you're running it full-screen and play 3D-games or CAD/CAM programs that require direct-draw.

+ Very good direct-draw and some direct-3D support
- "Raw" performance is sub-par
!!! Best used for some games and CAD/CAM

*** VirtualBOX ***
VirtualBox is comparable to Qemu with kqemu in "raw" performance but still slower than Qemu with KVM (even if KVM support is enabled in VirtualBox).
With the guest add-ons installed the graphics performance is really good, almost as good as with VMware except for Direct-3D.

VirtualBox just "feels" better than Qemu if you are running windows locally, full-screen or in a window, because of the better graphics support. The closed source version also gives you a "seamless desktop" option which also makes it more usable.
If you're going to run Windows in a headless VM and want to connect to it using RDP then the graphics advantage is gone and it will be outperformed by Qemu with KVM.

+ Better graphics than Qemu
- Slower than Qemu with KVM
!!! Best used for general purpose windows tasks

---

### Post by kanem on 2007-11-25
I don't know what all this talk about Virtualbox not being good enough in a "production" or work environment is about. I use it at work all the time. I import and analyze very large sets of data. I've been running 12 hour simulations over the past week. When I ran a benchmark on it, XP in VBox did better than the native installation on the same computer (probably due to some ad/spyware, someone else had that computer before I did). Anyway, VBox has done everything I've thrown at it and the only drawback I've noticed is a slight slow down on graphics-heavy apps.

The last time I tried VMware it was slow on my laptop and wouldn't let me install it on my work machine because that one has two CPUs. It doesn't have a problem working with 2 CPUs, but the people who make it decided to make users pay for that feature. Yay closed source :roll:. VBox works perfectly on both.

---

### Post by HermanAB on 2007-11-25
Hmm? VMware supports dual core processors very well thanks - using it every day.

The only reason  I use VMware is because of Windows 2003 Server doesn't run reliably on the others.

---

### Post by kanem on 2007-11-26
> **HermanAB said:**
> Hmm? VMware supports dual core processors very well thanks - using it every day.

The only reason  I use VMware is because of Windows 2003 Server doesn't run reliably on the others.
I didn't say dual core. 2  physically separate processors. I Got a very clear message that went something like "Sorry, this computer has two processors. The free version of VMWare for personal use does not support that feature".

---

### Post by de_valentin on 2007-11-26
I may not be the best judge here (definitely not) since I have only used Vbox untill now and I am but a lowly homeuser that wanted to play around with sketchup and try a few things with arcgis. 

But the ease of install even the seamless, the fact that it does all i need, use a network printer, go online as well as the home network, lets me install what i needed and does it as far as i can tell faster than the normal xp-install on the same machine does it makes vbox  a winner for me

---

### Post by n3tfury on 2007-11-26
> **kanem said:**
> I don't know what all this talk about Virtualbox not being good enough in a "production" or work environment is about.

probably talking about larger scale server environments.

---

### Post by jayson.rowe on 2007-11-26
Be sure to check out the Vmware Server 2.0 Beta if you want a nifty experience...I've been pretty pleased so far. 

Check out my blog for a mini-review and screenshots.

---

### Post by vanDrunen on 2007-11-26
Most people reading this thread for VM comparisons (I think) are using Ubuntu as their main desktop OS and just want to run Windows on the side for some "odd" windows applications. For this purpuse Qemu/KVM is perfectly fine, fully open source and has very good performance. It's too bad that Qemu/KVM doesn't get the attention it deserves.

Unless you are going to run many VM's in a corporate environment, want to spend $$$ on a piece of closed source software, don't mind to run an illegal copy or really need some Direct 3D graphics support, there's no good reason to use VMWare.

VirtualBox is hyped a little bit too much. The Open Source version is just a polished up Qemu and doesn't perform as well (except for the local graphics card emulation). Only the closed source version adds some real value: a locally rendered Seamless Desktop with only one press of a button with relatively good graphics performance.

With Qemu/KVM it's very easy to set up Seamless Virtualisation through RDP and it will give you the best raw performance. Guides for setting this up:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by akiratheoni on 2007-11-26
I use VirtualBox. Very easy to use; I could hardly get VMWare to work, and when it did, it screwed up some commands, I think namely apt-get which, like others, I really like.

---

### Post by gilf on 2008-01-08
It's probably time for a little informational updating in this thread.

I can't speak for the other two, but I just installed VMWare Player on my Gutsy machine.

1.) VMWare Player is now free, and can be downloaded from the VMWare site.

 So is VMWare Server (and open source)

2.) VMWare player is shipped crippled, but converts into a maximum speed and resolution virtual machine simply by adding VMWare Tools. These were previously commonly taken (free) from VMWare Server archives, but now:

3.) VMWare has made VMWare Tools open source and free. See:
[http://open-vm-tools.sourceforge.net/faq.php](http://open-vm-tools.sourceforge.net/faq.php)
    -and-
[http://sourceforge.net/project/showfiles.php?group_id=204462&package_id=244023](http://sourceforge.net/project/showfiles.php?group_id=204462&package_id=244023)

4.) Installing VMWare Player was easy. Creating a Virtual Machine for it was more complicated, but is now considerably eased by a website application EasyVMX:  [http://www.easyvmx.com/](http://www.easyvmx.com/)

5.) The greatest difficulty I had was not caused by software but by deciding to copy my existing dual Boot Windows partition to a virtual machine, in order to avoid installing software and OS. I naturally wanted to do that with free software. I wrote about that process here:
[http://ubuntuforums.org/showthread.php?t=660511](http://ubuntuforums.org/showthread.php?t=660511)

I've run the VMWare Player on two machines so far and am very impressed by the speed and compatibility. I've used 3D CADS (DesignCad, and TurboCAD) without a hitch. Wine had always crashed with them. A screenshot of a 3D design in progress under VMPlayer is attached here. I can't tell any difference in rendering speed between native and VM versions -- under one second for render from file for this project.

I've also tried as an acid test a couple flight simulators (FMS and DOA) DOA wouldn't display. FMS ran at 10 frames per second on 2.4 Ghz single proc Pent 4 w/ total memory of only 500 megs.

I'm not really interested in gaming -- CAD is a definite requirement, and there is little in the way of free 3D CADs in Linux. I'll probably use the Win VM for tax software (if it doesn't run on Wine) and a few other oddball programs collected over the years -- more intensively with CAD until a good one appears in linux

 If I want to run those two specialty flight sims, I'll dual boot. My wife requires MSWord for track changes in her editing work (OO doesn't cut it for her, there), and the VM is perfect for that while weaning her towards Ubuntu, otherwise.

I'm very happy with the performance of VMWare Player with VMWare Tools. The earlier benchmarks quoted in this thread by others lacked the VM Tools, which are essential.

I have no experience with Qemu or VBox, so this isn't a comparison, just an update on the free availability of VMWare, and a report of performance, in my installation.

---

### Post by AndyCooll on 2008-01-08
> **gilf said:**
> 1.) VMWare Player is now free, and can be downloaded from the VMWare site.

 So is VMWare Server (and open source)

Have I missed something? When did VMware Server become open-source. VMware Tools might have been open-sourced, however I wasn't aware that this was the case with VMware Server itself.

:cool:

---

### Post by hyper_ch on 2008-01-08
What I still have problems with VBox is that I just cannot get networking done between guest and host. Both, guest and host can access the inet but I can't use Samba or SSH or ... to exchange between those two. I also haven't found any guide and tried many things.

VmWare however, makes that very simple. Additionally I think the USB device support is much better in VmWare. On the dark side, I tend to think VBox is faster and uses less resources.

As I normally want to exchange stuff, the networking capabilities is for me essential. For that reason VmWare is my favourite. Although I have to admit, I've never tried QEMU.

But that's my experience.

---

### Post by lvleph on 2008-01-08
I have tried all three and VirtualBox was the only one that pretty much just worked. The only thing you have to remember is adding your self to the vbox group.

---

### Post by mips on 2008-01-08
> **AndyCooll said:**
> Have I missed something? When did VMware Server become open-source. 


Yes. It was a long time ago, February 2006.

---

### Post by paul.matthijsse on 2008-01-08
> **hyper_ch said:**
> What I still have problems with VBox is that I just cannot get networking done between guest and host.Hello, it's the easiest way to activate 'Shared folders' in the virtual machine. Press F1 and look in the index to find out how to do that. In order to activate this, you need to run, as root if I remember well, the VBoxLinuxAdditions or something like that. 

Cheers, Paul.

---

### Post by hyper_ch on 2008-01-08
I don't want just to share I want to SSH into the box

---

### Post by lvleph on 2008-01-08
Well your virtual machine if connected to the net will have an ip address. If you setup ssh server on your virtual machine you should be able to 
```
ssh <user>@<ip address>
```
But maybe I am over simplifying.

---

### Post by popch on 2008-01-08
> **hyper_ch said:**
> I don't want just to share I want to SSH into the box

With VirtualBox you ought to have the option to declare the network interface of your virtual machine to be either bridged or NAT. I can not tell from off the top of the head if VirtualBox also offers an option for a 'virtual network' within one host only. VMWare does.

If you define your interface as 'bridged', the virtual machine can be seen from all nodes in your network. It should also be visible for the host it is running in. 

If, on the other hand, you use NAT for your virtual machine, it will see your network but remain largely invisible for all nodes in the network.

However, I seem to remember that VirtualBox creates a virtual NIC in the host and assigns it an IP address which is on the same subnet as the virtual NIC in the guest. I rather think it should be possible to access the virtual machine (the guest) from the host it is running in even with NAT.

---

### Post by hyper_ch on 2008-01-08
> **lvleph said:**
> Well your virtual machine if connected to the net will have an ip address. If you setup ssh server on your virtual machine you should be able to 
```
ssh <user>@<ip address>
```
But maybe I am over simplifying.

I couldn't ssh from host to guest although both were able to access the internet...

---

### Post by lvleph on 2008-01-08
And you have the ssh server setup on the machine you are sshing into? I know that is a lame question, but sometimes it has to be asked.

---

### Post by hyper_ch on 2008-01-08
I couldn't even ping it and the server was setup.

---

### Post by gilf on 2008-01-08
> **AndyCooll said:**
> Have I missed something? When did VMware Server become open-source. VMware Tools might have been open-sourced, however I wasn't aware that this was the case with VMware Server itself.

:cool:

[http://www.vmware.com/download/server/open_source.html](http://www.vmware.com/download/server/open_source.html)

---

### Post by Methuselah on 2008-01-08
A vote for QEMU here.

For one, it's the ONLY thing that works on FreeBSD which I also run.(apart from Win4BSD which is QEMU based) 

Thumbs down for VirtualBox being based on QEMU but somehow managing not to work on FreeBSD.

VMWare Server also doesn't work on BSD so it gets no votes from me.

I have used VMWare Server though and though it was pretty slick.
I was playing with VirtualBox on an ubuntu partition but ran out of disk space and couldn't finish the installation.

---

### Post by thisllub on 2008-01-09
The only one I haven't had success with is QEMU. I installed that under Fedora 7 about 6 months ago and it was so slow as to be useless.

VMware Server has very good if slightly confusing support for multiple network cards. Any more than about 3 simultaneous VMs and it can bog down and turn them all off. I suspect that the non-free versions of VMWare are better at this. It seems more trouble free with pre 2.6.20 kernels too.

VirtualBox has some work to do on networking but if you just want to run Windows on your Linux desktop, this is the way to do it.
Seamless mode is cute if a gimmick but the dynamic resizing of the OS window is ahead of VMware. 

I would like to try Xen but the lack of NVIDIA support has kept me away from it.

I don't believe that any of them will run if you have a low latency kernel (e.g. UbuntuStudio) installed. I run Arch on this PC and I had to recompile the kernel to get VirtualBox to work.

---

### Post by Methuselah on 2008-01-09
> 
The only one I haven't had success with is QEMU. I installed that under Fedora 7 about 6 months ago and it was so slow as to be useless



QEMU is actually flexible enough to run code intended for one processor on another...ie a true emulator. By default it will run in the mode even when the emulated processor and the host processor are the same. You need to also use the QEMU accelerator module KQEMU or else it will be slow indeed! 

On FreeBSD KQEMU is installed as a kernel module and I guess it's the same on Linux.
VirtualBox and Win4Lin are both based on QEMU/KQEMU IIRC.

---

### Post by AndyCooll on 2008-01-09
> **gilf said:**
> [http://www.vmware.com/download/server/open_source.html](http://www.vmware.com/download/server/open_source.html)

I was always under the impression that it free but only as in beer. So, thanks for that. I've learnt something. 

:cool:

---

### Post by swoll1980 on 2008-01-09
Vbox everyday and twice on Sunday

---

### Post by schumifer on 2008-01-24
Just installed virtualbox and i am learning. Have to admit though that convertXtoDVD is wayyyyyy slower on vbox than it was on vmware. Checking the setting i seem to have  forgotten to use the virtualization instruction of my 144. Shouldn't those be automatically used anyhow?
Liked the seamless mouse thing though i cannot say i got tired of pressing left control alt in vmware.
Oh ,did i mention how slow convertX2DVD is on vbox?  Get this. Vmware -> 2,13X   Vbox ->0,75X  .
I seriously hope it is simply the virtualization i left out
And here is a BIGGGGGGGGGGGG plus for vbox.
     When i needed to read and write to a physical ntfs partition i always needed to umount it , use it in vmware , then restart twice, then shutdown, then remount it. IF i ever left out one of those steps i usually ended up with an unmountable ntfs partition. Then back in vmware, chkdsk , restart, restart shut down, cross fingers , mount ...DONE.
With vbox the hussle is over. Just use everything you need as a network drive. 
I'll probably be getting back top this thread as i use vbox more

---

### Post by schumifer on 2008-01-27
OK i am back.
I am running out of reasons to boot my native XP install. Finally i can have my pocketpc synchronizing. No more weird "not-working-properly-please-reinstall" ballon tips from virtual XP.

As for the speed i can honestly admit i am slower , not by as mush as in my previous post but still slower, BUT I DO NOT CARE. Instead of 2,13X i now get a maximum of 1,75 but that is accceptable, and by far faster than 0,75X!!!

---

### Post by lefnire on 2008-02-10
I've got a question.  I have a windows partition for my ipod because linux f's it up (amarok, gtkpod, bla bla bla... don't bother recommending, I've tried wrestled with them all for a very long time and they just don't work).

I use vmware primarily, but vmware seems to have trouble interfacing with hardware.  I can plug in my ipod & it's recognized on my vmware windows install, I download music in itunes... but when I try to transfer music to the ipod through vmware, it corrupts the ipod.

vmware vs. qemu vs. virtualbox: are any of these better than the other at handling hardware?  what about wine?

---

### Post by popch on 2008-02-10
> **lefnire said:**
> 
vmware vs. qemu vs. virtualbox: are any of these better than the other at handling hardware?  what about wine?

The last version of VMWare I had a close look at supported USB 1.1. VirtualBox supports USB 2.0. That could make a difference for the iPod. 

I have not tested it, though, because my iPod ran reasonably well with RhythmBox the last time I tried it.

---

### Post by Dark-Penguin on 2008-02-10
Well peeps I have a question. I really can't comment too much on which is better. I like VMWare but I want it free so I decided to use VB. 

I'm really new to linux, especially Ubuntu. My first attempt at installin Ubuntu went fine. I was using the native NV video driver and had not played around with compiz.

I installed VB 1.5 on my Ubuntu 7.10 and it worked with no problem.

Here's the prblem and maybe someone can help me. I have gone through a rebuild wit working nvidia drivers to do compiz. When I installed VB it seemed to install ok but when I looked under the menu options at I didn't see it in the list. I'm forced to run it through Terminal. I created a desktop shortcut but I don't wast the terminal windowd to open everytime. How do I find the app on my system and put a shortcut on the desktop?

---

### Post by Dark-Penguin on 2008-02-10
Well peeps I have a question. I really can't comment too much on which is better. I like VMWare but I want it free so I decided to use VB. 

I'm really new to linux, especially Ubuntu. My first attempt at installin Ubuntu went fine. I was using the native NV video driver and had not played around with compiz.

I installed VB 1.5 on my Ubuntu 7.10 and it worked with no problem.

Here's the prblem and maybe someone can help me. I have gone through a rebuild wit working nvidia drivers to do compiz. When I installed VB it seemed to install ok but when I looked under the menu options at I didn't see it in the list. I'm forced to run it through Terminal. I created a desktop shortcut but I don't wast the terminal windows to open every time. How do I find the app on my system and put a shortcut on the desktop?

---

### Post by a94060 on 2008-02-10
vmware server is free (whcih i found out only sometime ago. It is also good for the regular home users. I have never tried it for gaming though ( I thought that it would look like crap and lag)  Is this true?

---

### Post by altariel on 2008-02-11
I like qemu (+kqemu) very much ... 
especially the fact that you can take a dd-dumped image of your harddrive and start it in qemu is very cool and handy :)

---

### Post by Incense on 2008-02-11
> **Dark-Penguin said:**
> Well peeps I have a question. I really can't comment too much on which is better. I like VMWare but I want it free so I decided to use VB. 

I'm really new to linux, especially Ubuntu. My first attempt at installin Ubuntu went fine. I was using the native NV video driver and had not played around with compiz.

I installed VB 1.5 on my Ubuntu 7.10 and it worked with no problem.

Here's the prblem and maybe someone can help me. I have gone through a rebuild wit working nvidia drivers to do compiz. When I installed VB it seemed to install ok but when I looked under the menu options at I didn't see it in the list. I'm forced to run it through Terminal. I created a desktop shortcut but I don't wast the terminal windows to open every time. How do I find the app on my system and put a shortcut on the desktop?

It should be under Apps - System Tools - and Innotek Virtualbox. It's a little blue box icon. 

[IMG]http://images.howtoforge.com/images/virtualbox_ubuntu/0.jpg[/IMG]

---

### Post by Christmas on 2008-02-11
I use Qemu and like it a lot, it seems very simple after you configured it.

---

### Post by mysidia on 2008-03-08
> **AndyCooll said:**
> I was always under the impression that it free but only as in beer. So, thanks for that. I've learnt something. 

:cool:

You've learned something that's incorrect. VMware Server is not open source, and not even close.

These are just modified Open Source pieces that are incorporated into VMware products.

Since the Linux kernel is GPL'ed, and ESX utilizes modified SCSI drivers, they have to release the modified open source driver.

Since the GDK-PIXBUF library is LGPL'ed they have to release modified source code to the library.

This is the only open source code at that URL, sorry.

---

### Post by FuturePilot on 2008-03-08
I like VirtualBox. VMWare was a headache for me, literally. I had way too many problems with it. Then I tried VirtualBox and everything just automagically worked. :D

---

### Post by ODF on 2008-03-08
Virtualbox = easy, seamless mode is cool ... and almost everything  needed is easy to get working. It's also a lot faster than VMware.

---

### Post by AndyCooll on 2008-03-09
> **mysidia said:**
> You've learned something that's incorrect. VMware Server is not open source, and not even close.

These are just modified Open Source pieces that are incorporated into VMware products.

Since the Linux kernel is GPL'ed, and ESX utilizes modified SCSI drivers, they have to release the modified open source driver .

Since the GDK-PIXBUF library is LGPL'ed they have to release modified source code to the library.

This is the only open source code at that URL, sorry.
Thanks for clearing things up with that information. As I indicated in my original query, I had always thought that it wasn't open-source ...so it was surprising news to me when someone said it was. And even more surprising when they seemed to provide evidence. So your information simply re-confirms that I hadn't been going bonkers with my original undertanding! 

:cool:

---

### Post by deletarus on 2008-04-03
I have long been a fan of VMWare. As of version 6 it has full support for USB 2.0 as well as (last time I checked) limited support for full 3d acceleration (needs to be configured). 
I have mainly used it on native windows running windows and linux guests. I have not used the alternatives.  I have found that without running VMWareTools it is quite slow, but with them installed, it is very useable.
I really like how you can have multiple VMs running at the same time, switch between them, drag and drop files between host and guest, etc.

I was wondering... what kind of support for usb, cd, etc, devices are supported in each of the VMs?

VMWare allows for  cdrom from img, actual cdrom, floppy img, actual floppy, usb 1.1 and 2.0 (all adjusted on the fly if you like).
Are these features also supported in VBox and Qemu? what about multiple VMs running at the same time?

The one thing I don't really like about VMware is that it installs several "virtual nics" If VBox supports many of the same features and is less resource intensive, I may just have to switch.

The main features I would like are cdrom and usb 2.0 support.

---

### Post by kaylus on 2008-04-22
To answer your question somewhat:

VirtualBox allows:

Cdrom from image, actual cdrom, floppy image, actual floppy.
Usb 1.1, Usb 2.0, Remote USB over RDP
Limited 3D
Virtual Machines over RDP / Headless Host Machines
Full Seamless mode without configuring SeamlessRDP
Shared Folders and Clipboarding
And some standard features like Configurable Memory, Video Memory, HD-Space, Shared Folders, Clipboarding, etc.

I think that the people who bible-thump for VMware, QEmu, or VirtualBox are just full of flap themselves. An earlier poster recommended not using VirtualBox in a production environment -- I disagree, it runs just fine and with enough speed. The featureset is more than adequate.

There was a small configuration error with USB gunk that required manual editing of files, but after that no issues.

---

### Post by opm8 on 2008-08-31
Having tried virtualbox, qemu and vmware I have settled on vmware.

What I needed was a Win XP virtual machine on a Debian host that I would be connecting to through Remote Desktop.

Virtualbox was the first I tried and by far the worst.  It would constantly hang my guest XP machine suddenly becoming non-responsive and forcing me to hard kill the virtual box process.  Maximum uptime was about 12 hours.  Local connections were great (from the host to the guest) but remote RDP reconnects would instantly hang the guest.

Qemu was a little better in the stability department but would then completely crash after about a day of uptime.  Performance was slightly better than virtualbox.  Disconnecting RDP and reconnecting again proved almost impossible.

Vmware has been a treat from day one with its rock-solid stability.  I couldn't make it flinch no matter what I tried.  Plus it has a web interface great for remote management and a console, which can also be run remotely. This is huge and way ahead of the other two products.  I can restart the virtual machine remotely and change every setting and never have a problem.  Local and remote RDP is seamless.

I can't say a single bad thing about vmware.  This thing just works.

opm8

---

### Post by Dixon Bainbridge on 2008-08-31
> **Bloodfen Razormaw said:**
> Try using it in a production environment and see if it is still fast enough.  Home users don't need fast virtualization.  On the other hand, virtualization is very important to businesses (which are the primary target for virtual machine software) and VirtualBox is not nearly fast enough for a production environment.  It is much slower than QEMU, and a mile behind VMware.  Just because it works well for limited purposes doesn't mean its the better for more intensive tasks, or even the best for its own task.  VirtualBox simply has no reasonable niche.  A performance-conscious user can get many more features and optimal performance from VMware.  A user who wants a free software solution can get the same from QEMU.  And then there is VirtualBox, which lacks features like 64-bit or SMP guest operating systems, misses some hardware support entirely, and has no 3D acceleration support, yet also only provides a subset of functionality freely.  Considering one can get a better virtual machine without licensing issues out of QEMU, or the best virtual machine with many of the same licensing issues out of VMware, there isn't much place for VirtualBox.

I find it very fast in a production environment. Perhaps you've not set it up properly?:)

---

### Post by doorknob60 on 2008-09-02
I've used VMware and Vbox. I like VMware a little better, but it's pirated so I prefer to use Virtualbox so I'm being legal, and it's almost as good, and open source :) EDIT: Meaning I like Virtualbox better

---

### Post by swoll1980 on 2008-09-02
I have a two headed system I run Ubuntu on the left and vbox running win2k in the right. The win2k runs faster in the vm than xp runs natively on the same computer.

---

### Post by zoeken on 2008-09-23
From my point of view (beginner linux and virtual machine :D) Scale 1-10:

Speed: XP - same in both VM software; Suse - VMware 10, Vbox 6; Slackware - same; Ubuntu - Vbox faster; Win2000 - VMware faster

USB: works for me in both

Instalation: Vbox 10, Vmware 7 (forum info helped alot)

64bit CPU support: Virtualbox has 64bit support if you check the box for VT-x/AMD-V but the 64bit guest OS is slower compared with VMware (i do not need 64 bit...) 

It is useful for me the option in vbox for video ram because i need more video ram for 3D mechanical design software, and some OS (Vista) ask for more.
I will saty with Vbox if someone help me with info: how to change guest OS resolution for wide screen(1680x1050) to have a better full screen mode.

[COLOR="Red"]So, the latest news: virtualbox wins! After instaling Guest Addition in virtual box when switch to full screen the resolution atomatically changes to 1680x1050 and i still have 128 video RAM :D [/COLOR]

---

### Post by wroopy on 2008-09-23
If you add KVM to the comparision, how would that be rated?

I'm running a server (Ubuntu 8.04) and also has a need for a XP session. I'd also like to have the possibility to start different virtual machines to play/test with.

/Andreas

---

### Post by Hiperi0n on 2008-10-04
I have been using VirtualBox because I have been recently doing some editing with Premiere Pro 2.0 and it doesn't work under WINE.

VBox works flawlessly. Awesome, it felt it was being quite faster than native XP. I guess that could be due to the fact that it was a fresh install of Windows XP SP3. Anyway I have never used virtualization, just a couple days ago, and I must say I am very pleased with the results VirtualBox has given me.

---

### Post by toupeiro on 2008-10-04
I look at virtualization a bit differently.  Desktop host virtualization isn't as important to me, I am interested in Bare Metal virtualization, and there is nobody even in same ballpark as VMWare in this catagory.

---

### Post by bodhi.zazen on 2008-10-04
> **toupeiro said:**
> I look at virtualization a bit differently.  Desktop host virtualization isn't as important to me, I am interested in Bare Metal virtualization, and there is nobody even in same ballpark as VMWare in this catagory.

VMWare bare metal ? LOL

Try Xen, KVM, or if you really want bar metal OpenVZ.

---

### Post by Phreaker on 2008-10-04
I use Virtualbox and it runs perfectly

---

### Post by toupeiro on 2008-10-04
> **bodhi.zazen said:**
> VMWare bare metal ? LOL

Try Xen, KVM, or if you really want bar metal OpenVZ.

As I said, I look at Virtualization differently.  I care about things like vFault Tolerance, Shared SAN Storage connections, and Moving virtual machines from 1 clustered host to another without bringing them down, and running and balancing upwards of 100 VM's not 1-10...  I've Tried all of the choices which you mentioned, and I stand behind my statement.  **nobody** is even in the same ballpark as VMWare.  Just because its open source doesn't always mean it performs better.  In fact, I see better Linux VM performance on VMWare than I do on Xen, nearing close to 100,000 iops/sec.

If you're trying to virtualize 100's of machines, you have to build up some powerful host servers.  If you're in a financial position to invest that much into hardware, the VMware software costs aren't going to phase you.  When FOSS can give me the same functionality, I see no reason not to give it another shot, but VMWare is several cuts above at this point in time.  If all I care about is virtualizing 1 - 5 machines for very lightweight usage, then VBox is fine, and is likely fine for most people.  Thats not what I do.

---

### Post by InfinityCircuit on 2008-10-04
I use virtualbox for Windows XP, and Xen for everything else.

---

### Post by Frak on 2008-10-04
> **toupeiro said:**
> As I said, I look at Virtualization differently.  I care about things like vFault Tolerance, Shared SAN Storage connections, and Moving virtual machines from 1 clustered host to another without bringing them down, and running and balancing upwards of 100 VM's not 1-10...  I've Tried all of the choices which you mentioned, and I stand behind my statement.  **nobody** is even in the same ballpark as VMWare.  Just because its open source doesn't always mean it performs better.  In fact, I see better Linux VM performance on VMWare than I do on Xen, nearing close to 100,000 iops/sec.

If you're trying to virtualize 100's of machines, you have to build up some powerful host servers.  If you're in a financial position to invest that much into hardware, the VMware software costs aren't going to phase you.  When FOSS can give me the same functionality, I see no reason not to give it another shot, but VMWare is several cuts above at this point in time.  If all I care about is virtualizing 1 - 5 machines for very lightweight usage, then VBox is fine, and is likely fine for most people.  Thats not what I do.
We use Xen and VMWare where I work. It gives us the most for our bucks.

Xen on the RedHat cluster and VMWare on the Server 2003 cluster.

---

### Post by toupeiro on 2008-10-04
> **Frak said:**
> We use Xen and VMWare where I work. It gives us the most for our bucks.

Xen on the RedHat cluster and VMWare on the Server 2003 cluster.

Cool :)

I should probably reclarify, that in my case when I refer to VMWare and bare metal, I am referring to ESX.  in other words, I put windows server and Redhat on bare metal VMWare clusters.  In my tests, I've gotten almost 2-3 times the I/O out of ESX over Xen, but like everything else, mileage will vary based on your usage.

---

### Post by Frak on 2008-10-04
> **toupeiro said:**
> Cool :)

I should probably reclarify, that in my case when I refer to VMWare and bare metal, I am referring to ESX.  in other words, I put windows server and Redhat on bare metal VMWare clusters.  In my tests, I've gotten almost 2-3 times the I/O out of ESX over Xen, but like everything else, mileage will vary based on your usage.
Ah yes, we have been planning to use ESX for awhile now, but we are still under RedHat support, so we'll ride that out until we flip to a Bare-Metal server.

---

### Post by K.Mandla on 2008-10-04
Moved to Virtualization.

---

### Post by Cresho on 2008-10-20
I love virtualbox  I always make a copy of the vdi file.  when I want to experiment, all I need to do is destroy the winxp.vdi file by installing malware or such or what ever I want, then delete the file and replace with the backup winxp.vdi file.  As good as the first time installed or backed up.  So now, I have my favorite windows configured with no antivirus, no malware, no nothing installed but the vital softwares I love to use which will not run in wine......hmmm I take that back, they now run in wine.

Virtualbox is just an extra aplication I have installed running windows so when I give free customer support to the dying breed of windows users. :popcorn:

---

### Post by SSVegito888 on 2008-10-24
I know xen requires a different Linux Kernel, but do qemu, kvm, and virtualbox?


Also, What are the main differences between VirtualBox and VirtualBox OSE.


PS: I will be using for home\personal use.

---

### Post by bodhi.zazen on 2008-10-24
> **SSVegito888 said:**
> I know xen requires a different Linux Kernel, but do qemu, kvm, and virtualbox?

No, but you can not run KVM and VMWare at the same time. Not sure about Virtualbox + KVM.

> Also, What are the main differences between VirtualBox and VirtualBox OSE.


PS: I will be using for home\personal use.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by SSVegito888 on 2008-10-24
Thanks for the info and link.

---

### Post by unclecameron on 2008-10-25
I've used Xen for years, still use it in production for serious uptime, basically never breaks, nothing close in speed (e-mail servers, nameservers, etc.), but when it comes to writing python code and testing it in multiple OS'es (win, lin, solaris, BSD) I simply *had* to get vmware, though I hated the idea of it. Now it seems VMware is really crappy at handling substantial known bugs (ubuntu host keymapping, bridge networking on same host) where vmware forum questions go frequently unanswered. Would VirtualBox be a candidate for what I'm doing? I must say VMware 6.5 Workstation is MUCH better than the previous releases I've seen. It seems (to me) like VMware has a much more significant interest in Windows users (hosts) than Linux, which concerns me. I still would prefer to use xen for everything, but I just don't want to spend the time to hack that much to make it happen if I needed a quick OS scenario like Solaris. Advice?

---

### Post by warped0ne on 2008-10-25
Virtual Box is free and I find it's easier to set up than VMWare.  I use Virtual Box to test all my new OS opportunities (Vista, Intrepid Ibex, NimbleX, OpenSUSE 11, etc) and it works like a charm.

---

### Post by dunkar70 on 2008-10-26
I use VirtualBox 2.0.4 on a 32-bit version of Hardy. The version of VB that I use is proprietary, not open source, but it is free for personal use. 

Performance of Windows XP in VB is actually better than native. My assumption (a complete guess anyway) is that since VB is using virtual hardware, it can multi-thread the hardware requests and manage the virtual bus better than the real hardware.

---

### Post by lumix on 2008-11-18
A handy reference (hopefully not already posted):

[http://virt.kernelnewbies.org/TechComparison]("http://virt.kernelnewbies.org/TechComparison")

---

### Post by mtantawy on 2009-01-25
Another reference
hopefully not listed and hopefully to be up-to-date :D

[http://www.virtualbox.org/wiki/VBox_vs_Others]("http://www.virtualbox.org/wiki/VBox_vs_Others")


Mahmoud Tantawy

---

### Post by djrakun on 2009-03-23
[QUOTE=MRiGnS;2619815
virtualbox is btw based on qemu.[/QUOTE]

this is what I expected.  I started using Virtualbox a few months ago and while going through a how-to on getting windows xp running on a ps3 I wanted to follow form and used qemu like the tutorial suggested.  The differences between VB and Qemu were slight if any and I actually found Qemu maybe slightly easier to configure.  If the consensus between at least these to is Qemu i'm on board with that

As far as what is suitable for production, any type 2 hypervisor is going to be 'too slow for production'.  In our office we use ESX because we can afford it, and nobody has any complaints about latency.  I tried to use the open source ESX on my home servers but the installer failed due to insufficient system resources ( 2.4 dual xeon hyperthreaded cpus and 1gb of ram.  i'm pretty sure the ram is why it bong'ed).  So I use VB on top of hardy heron and it's working well so far.  Will probably switch to QEMU on the next server nuke though

---

### Post by lewtwo on 2009-03-24
Your poll is a little generic. What version of VMware as they are radically different from a cost and feature standpoint. You also missed failed to include Virtual PC and HyperV (and a raft of other also ran's).It also depends on what your needs are. For strictly personal home use I would choose Vmware Workstation because it has all (if not more) the features and I just hapen to have a license. From more general perspective I like KQemu (with KVM under it) ... its biggest limitation the default natted networking. Virutal box falls more in the middle. At the moment for a production enviroment VMware is the only leading product that is mature.

---

### Post by Fatman22 on 2009-05-24
HI, I currently run Intrepid & have was wondering which would be best for SAS (windows) & visual Studio 2008 Pro.

Thanks,

---

### Post by bodhi.zazen on 2009-05-24
> **Fatman22 said:**
> HI, I currently run Intrepid & have was wondering which would be best for SAS (windows) & visual Studio 2008 Pro.

Thanks,

FYI : this is a very old thread. qemu is oudated and kvm is far superior to qemu.

google is your friend here (in terms of specific apps).

---

### Post by Russell Burrows on 2009-05-24
> **Bloodfen Razormaw said:**
> Try using it in a production environment and see if it is still fast enough.  Home users don't need fast virtualization.  On the other hand, virtualization is very important to businesses (which are the primary target for virtual machine software) and VirtualBox is not nearly fast enough for a production environment.  It is much slower than QEMU, and a mile behind VMware.  Just because it works well for limited purposes doesn't mean its the better for more intensive tasks, or even the best for its own task.  VirtualBox simply has no reasonable niche.  A performance-conscious user can get many more features and optimal performance from VMware.  A user who wants a free software solution can get the same from QEMU.  And then there is VirtualBox, which lacks features like 64-bit or SMP guest operating systems, misses some hardware support entirely, and has no 3D acceleration support, yet also only provides a subset of functionality freely.  Considering one can get a better virtual machine without licensing issues out of QEMU, or the best virtual machine with many of the same licensing issues out of VMware, there isn't much place for VirtualBox.


When I run XP with virtualbox with my main or host OS system being Ubuntu 9.4.

I run Nero Seven Recode and let me tell ya that recodeing 1080p and 720p movie source material will suck the juice out of most computers so yes we home users need a lot of power when doing this and Virtualbox fits the bill for simple, secure and fast operation of my virtual xp os.

And as one pal said you really come to feel good about the reliability of Virtualbox when the laptop shows twenty minutes to finish the recode and the show or on/air director of the budget local show wanders by and tells you have twenty three minutes to deliver the recoded show segment or its good bye to your job..........gee no pressure,right.

Thank God I only do video recodeing for a hobby instead of a living.:popcorn:

---

### Post by RedSingularity on 2009-05-24
I have been using VirtualBox for a long time now.  I am very happy with it and the way it works.  Not only does it do what i need it to, but it is very easy to use even for the beginners.

---

### Post by Sunnz on 2009-05-25
> **bodhi.zazen said:**
> FYI : this is a very old thread. qemu is oudated and kvm is far superior to qemu.



Hey wait a minute, KVM is a Linux specific thing right?

Yes this may be a Ubuntu community forum but the advantage QEMU have over KVM is that it runs on almost anything, you could have an arm-based OpenBSD and emulating a SPARC chip.

Yes that would run terribly slow and KVM would give you better performance for virtualising x86 instruction on x86 platform...

Still, each have their own strength, and QEMU is still being developed and updated.

Obviously I do use QEMU on OpenBSD, it isn't that bad really. :D

---

### Post by bodhi.zazen on 2009-05-25
Yes, KVM is for Linux and Yes this is a Linux forum.

KVM will run Windows and Linux guests.

If you are running qemu on openbsd, yes that is very slow. While it can be done, it is very very slow.

I am not sure what options you have for BSD, either host or guest. Perhaps VMWare would be your best option, at lease for guests, I would gave to consult google.

---

### Post by Sunnz on 2009-05-26
> **bodhi.zazen said:**
> If you are running qemu on openbsd, yes that is very slow. While it can be done, it is very very slow.

Yes it would be slower than other alternatives for running a x86 guest on a x86 host, but saying that it is very very slow could be an over generalisation.

It depends on what you are doing with it, I have been experimenting it as a web server and so far the experience is pretty good, it is just like another box sitting on my home network.

If you are playing HD video then yes it will be terribly slow, it won't be usable, but again this thread isn't only for home users so I am talking about it just in general.

I love the way it the network is configured with QEMU, works very well with PF and OpenBSD; it is not for the faint of heart because you need to know precisely how to plan your network, but it is great for people who know what they are doing!! :D

> **bodhi.zazen said:**
> I am not sure what options you have for BSD, either host or guest. Perhaps VMWare would be your best option, at lease for guests, I would gave to consult google.

I am not aware of any release of VMware for BSD... yes it is certainly true that BSDs works as guest with VMware, but I am mainly concern with the host here.

NetBSD comes with XEN which supposedly have very good performance, it is something I would look into in the future.

---

### Post by KB2HSH on 2009-05-26
VirtualBox.  Can't beat the price or the performance!  I can run XP on my Ubuntu/Xubuntu partition, and run Ubuntu on the XP partition.  Love it!  I have even moved my XP.vdi from one machine to another, and it opens exactly the same...but of course it would...nevertheless, even with my sub-1 GHz Athlon, the performance is fantastic.

---

### Post by bodhi.zazen on 2009-05-26
Interesting.

How does it compare to the BSD jail system?

[http://www.freebsd.org/doc/en/books/handbook/jails.html](http://www.freebsd.org/doc/en/books/handbook/jails.html)

From what you are describing (running servers) it sounds like a jail would be perfect.

Personally I use OpenVZ / KVM and I am betting openvz is similar to the BSD jail and if so I would bet that if you run performance tests , jails are better then qemu. Would be interesting to see the results anyway.

Other the jails, virtualization seems to be an achillies heal of the BSD's . Sure you may know what you are doing, but in my experience it is not so easy to install openbsd, let alone get it running in a virtual machine. I think if they worked on the installer openbsd would be more popular.

---

### Post by HDave on 2009-05-27
> **bodhi.zazen said:**
> Personally I use OpenVZ / KVM

I checked out the OpenVZ site and it left me wondering how much of a performance difference there is between OpenVZ and it's jail/zone approach versus KVM paravirtualization.  Seems like it would be a tie.  What is your experience?

---

### Post by bodhi.zazen on 2009-05-27
I believe openvz / BSD jails are faster then KVM and they have the additional advantage of using your hardware directly (when you cat /proc/cpuinfo you see your native core).

---

### Post by Fatman22 on 2009-05-27
I just installed Virtual box 2.1.4, It works fine under Ubuntu Intrepid 8.10 & ran Windows Xp SP3 Spanish Just fine!
 
I installed Office 2007 Spanish just fine, however the installer froze once the progress bar hit 100%. I had to kill the installer process, but all of the apps appear to run fine.
 
On another unrelated note, I cannot figure out to which folder Dosbox loads in Ubuntu.
 
I can open it, I get the terminal (Dosbox screen, but It is not running in my /user/home directory. In fact I have no idea where it is as I cannot mount any directory, nor will the Dir command work other than giving dosbox files.
 
Anyway I guess I can just run the dos games in Win XP under compat mode but I hate runnung VB for just a 5,000kb game. like Doom.
 
And yes, the fireball throwing demons still scare me! )-:
 
[CRIES]

---

### Post by HDave on 2009-05-28
> **bodhi.zazen said:**
> I believe openvz / BSD jails are faster then KVM and they have the additional advantage of using your hardware directly (when you cat /proc/cpuinfo you see your native core).

Do you use OpenVZ with Ubuntu?  If so, do you compile your own kernel or snag one from somewhere?

---

### Post by whoop on 2009-05-28
I always use vmware, I find it easy to install configure and it is quite flexible and powerful. I really don't like the browser based client in vmware server though. It's a bit unresponsive at times (not the guest luckily). When I access the client through https I sometimes don't even get a login box, I have to refresh a couple of times. Other than that I like it.

---

### Post by x33a on 2009-05-28
i only use vms sometimes and virtualbox does the job. never tried vmware since switching to linux, but i remember it being a bit heavy on the resources during the windows days.

---

### Post by HDave on 2009-05-28
> **whoop said:**
> I always use vmware, I find it easy to install configure and it is quite flexible and powerful. 

I have to add that I just tried out VMware server this week having used it a little bit a couple years ago.  I am simply blown away by the easy install on Ubuntu 9.04 as well as the terrific management interface.  The performance of the local console is such that once you maximize the window you can forget you are in a virtual machine.  It really has come a long way in 2 years.

---

### Post by rliegh on 2009-05-28
idk how's the disk i/o, though? I always prefer VB b/c it seems like if you choose an SATA controller you get better disk performance than you do w/ vmware.

---

### Post by Gamefreak94 on 2009-05-31
VirtualBox is the only virtualizing client I've used so far, and I never felt the need to try anything more. It works beautifully with all OSes!

---

### Post by macpointman on 2009-05-31
what is the best way to do it.  I would really like Ubuntu to be my primary and be able to run my existing windows XP installation inside it using a virtual machine.  However this is something that i have never until now tried doing.

---

### Post by abhishekp on 2009-05-31
I havent used Vbox, but have no problem running 3 OSes simultaneously on VMWare. What about VBox is it good for running multiple oses simultaneously? Oh and by the way i use it as a team (LAN simulation) One server and 2 clients.

---

### Post by stevepb on 2009-06-04
I've used Vbox on Gusty and Jaunty, I must say it's much quicker on Jaunty, but most things are to be honest.

I had no problem running 7 OSs simultaneously, granted some of these were very small and not resource intensive such as DSL, Puppy Linux, Slax. I also had two versions of XP running.

I only noticed problems when setting all OS to do something a bit intensive, it was fine if only one or two OSs needed to do some heavy processing, but with all 7 my Laptop was considerable slower.

So I'd say it's great unless you plan on using any more than 2 Operating systems simultaneously, (excluding the Ubuntu it's all running under).

I'm interesting in QEMU as i'm looking for something that will satisfy business requirements, it seems that Qemu is loosing in the polls hmm. I'm after probably 3 virtual servers all running windows server 2008 (possibly RC2). I know 2008 is a resource eater, but with a 2 x quad core Xeon 2.5GHz CPUs and 8 GB RAM & 6xSAS ENT HD's @ RAID 5(+1) it should cope :-):D  

Will QEMU satisfy my business needs? I need a domain controller, application server, an SQL server, and a File Server.

I spent a fortune on the server and now i'm really trying to save money, I don't want to folk out thousands for VMware. I wonder what is the best solution? for spending the least money..... i think i'm going to give QEMU a try.

---

### Post by HDave on 2009-06-04
> **stevepb said:**
> Will QEMU satisfy my business needs? 

I literally just went through this process having built a killer virtualization server myself.  I can tell you three things I learned after 2 weeks of hard work:

1) KVM is Solid & Superfast
2) The QEMU video emulator is 10X slower than VMWare workstation and makes it too slow IMHO to work in for any length of time
3) The "virtlib" applications are unusable. Too new, too many missing features.

So if you don't mind managing them from the command line and you don't have to work in a graphical desktop environment for any real length of time, then I found KVM/QEMU is an excellent choice.

However, both of those negatives were killers for me so I went with VMWare Server.  It's still free and it is really solid so far.

---

### Post by Sunnz on 2009-06-10
> **bodhi.zazen said:**
> Interesting.

How does it compare to the BSD jail system?


Hey.

Sorry for the late reply, I don't have much experience with jails myself, but the answer to your question is apparently, 10x faster with jails:

[http://www.playingwithwire.com/2009/06/virtual-failure-yippiemove-switches-from-vmware-to-freebsd-jails/](http://www.playingwithwire.com/2009/06/virtual-failure-yippiemove-switches-from-vmware-to-freebsd-jails/)

"We doubled the amount of memory per server, we quadrupled sqlite’s internal buffers, we turned off sqlite auto-vacuuming, we turned off synchronization, we added more database indexes. These things helped but not enough. We twiddled endlessly with NFS block sizes but that gave nothing. We were confused. Certainly we had expected a performance difference between running our software in a VM compared to running on the metal, but that it could be as much as 10X was a wake-up call."

> **bodhi.zazen said:**
> From what you are describing (running servers) it sounds like a jail would be perfect.

Yes in some cases a jail or even a simple chroot is enough. OpenBSD for example uses chroot for Apache, bind and various other services by default, all you had to do is to start the service and the default configuration is already being chrooted.

There are other cases where you might use a VM though, mostly when you actually want to use another OS, say if you want to run some Windows only stuff, or say you want to provide a nix box to somebody without having an actual machine.

> **bodhi.zazen said:**
> Other the jails, virtualization seems to be an achillies heal of the BSD's.

Well, BSD in general just have way less support from proprietary vendors anyway, virtualization is no exception... so their only option is pretty much the open source stuff. If somebody actually choose to use BSD then surely they should know what the options are and can see the benefit of running BSD outweights other choices for their specific cases... after all there aren't many BSD zealots, they tend to use the best tool for the best job

> **bodhi.zazen said:**
> Sure you may know what you are doing, but in my experience it is not so easy to install openbsd, let alone get it running in a virtual machine. I think if they worked on the installer openbsd would be more popular.

I think this is a misunderstanding most people have when BSD is mentioned in a typical Linux forum... OpenBSD in particular, isn't out there to compete against Linux, Mac and Windows, that's just not their goal. It is perhaps a different mindset to the usual "Windows suck Linux rule" you might see around here. (But, of course, a famous quote from Linus Torvalds: we are not out there to destroy MS, that would be an unintentional side effect.)

So most OpenBSD users actually like the OpenBSD installer, because they usually know what they are doing and that's all they need. And I think it is a rather nice self selecting process, those who are keen enough to get their self up to speed with it tend to love it after installing it, so you end up with users who know what they are doing and loves the OS for what it is rather than reaching everyone at all cost.

But anyway let's not shift off topic shall we? ;) If you are interested to discuss BSD stuff with me feel free to drop me a PM or add me on jabber. :D

---

### Post by EoRaptor013 on 2009-06-17
> **Bloodfen Razormaw said:**
> Try using it in a production environment and see if it is still fast enough.  Home users don't need fast virtualization.  On the other hand, virtualization is very important to businesses (which are the primary target for virtual machine software) and VirtualBox is not nearly fast enough for a production environment.  It is much slower than QEMU, and a mile behind VMware.  Just because it works well for limited purposes doesn't mean its the better for more intensive tasks, or even the best for its own task.  VirtualBox simply has no reasonable niche.  A performance-conscious user can get many more features and optimal performance from VMware.  A user who wants a free software solution can get the same from QEMU.  And then there is VirtualBox, which lacks features like 64-bit or SMP guest operating systems, misses some hardware support entirely, and has no 3D acceleration support, yet also only provides a subset of functionality freely.  Considering one can get a better virtual machine without licensing issues out of QEMU, or the best virtual machine with many of the same licensing issues out of VMware, there isn't much place for VirtualBox.
Re QEMU has "all the features." I switched to Vbox because I couldn't get USB devices to work under QEMU. Has this been fixed?

Thanks.

---

### Post by bodhi.zazen on 2009-06-17
> **EoRaptor013 said:**
> Re QEMU has "all the features." I switched to Vbox because I couldn't get USB devices to work under QEMU. Has this been fixed?

Thanks.

yes =)

-usb
-usbdevice tablet

or use flash drive

-hdb /dev/sdb1 #assuming usd = /dev/sdb1

Just as in Vbox, and not use usb flash drive that way on both guest and host at the same time.

---

### Post by xebian on 2009-06-17
Vbox hands down.  BTW VB 3.0 B1 is out

```
Sun Microsystems has announced the first beta release of VirtualBox 3.0 Beta 1. 
The major additions to VirtualBox 3.0 so far is 
guest SMP (Symmetric Multi-Processing) support for up to 32 virtual CPUs,
 Windows guests now support Direct3D 8/9 applications and games, 
and there is now OpenGL 2.0 support for Windows, Linux, and Solaris guests. 

```

You can get it here
[http://download.virtualbox.org/virtualbox/3.0.0_BETA1/](http://download.virtualbox.org/virtualbox/3.0.0_BETA1/)

---

### Post by EoRaptor013 on 2009-06-18
> **bodhi.zazen said:**
> yes =)

-usb
-usbdevice tablet

or use flash drive

-hdb /dev/sdb1 #assuming usd = /dev/sdb1

Just as in Vbox, and not use usb flash drive that way on both guest and host at the same time.

Actually, I now recollect that I was trying to attach a Zune MP3 player and use the Windows Zune software. I could attach USB drives, but the Zune wouldn't show. The Zune worked, however, with VirtualBox. Since then, I've gotten rid of the Zune but haven't tried QEMU and KVM again.

---

### Post by supremedalek on 2009-06-22
In my case, at work we are running SCO unix (!) 5.0.6 and 6 in vmware. I installed 5.0.6 in VBox without any issues. What we found is that at idle the 5.0.6 vm uses up to 20% of cpu under vmware but I could not make it use more than 9% under VBox. In normal use it also seems to be faster. We have not been able to get SCO6's network stuff to run in VBox. As soon as we do, vmware will be bagged.

---

### Post by brad_mssw on 2009-06-22
supremedalek, I am also attempting to run SCO OpenServer 6 and seeing the same network issues (inability to load the network driver), whereas SCO OpenServer 5.0.6 runs fine (by fine, I mean an order of magnitude better than VMware). 

We've been looking a bit and it appears the most likely cause the DMI/SMBIOS information presented by VirtualBox being woefully inadequate.  When running 'dmidecode' on a linux guest on VMWare vs VirtualBox we see 45 vs 2 tables, respectively.  Notably missing is the PCI slot information, and considering SCO can't see the board ids for the network adapters (or anything else that would show up as a pci device), and therefore won't allow installation of the network drivers, that seems to be my leading assumption at this point.

Regarding courses of action, I'm going to try KVM/QEMU and see if it works there, if it does, since the VirtualBox bios is supposedly based off that of an older QEMU/BOCHS bios, I'll try to see if I can get VirtualBox to use the current QEMU bios which is supposedly supported using something like this:  
VBoxManage setextradata MyVM  "VBoxInternal/Devices/pcbios/0/Config/BiosRom" "MyBIOS.bin"

If you find a workaround for the issue, please don't keep it to yourself!

Thanks.
-Brad

---

### Post by TechServsys on 2009-07-04
I have a very aging server running SCO 5.06 and am in the process of recoding the app to LAMP - it is now written in DataFlex.

I would like to try running SCO in Vbox as a backup in case my server dies, but (I hesitate to admit it) I stepped on the distribution CD and SCO (dysfunctional as always) will not replace 5.x cds.

I do have a proper license.  If anyone could send me distribution cds I would be very, very appreciative and sleep better at night.

You may reach me privately at william {at} TechServSys  dot com

Thanks all.

---

### Post by Pinball on 2009-07-13
I wanted to set up a new W2K virtual on Ubuntu 9.04. I already had one running in VMware player, but I couldn't find any "appliances" to create a new one, so I started looking for other ways to do the job.

My requirements were **really** simple - the VM had to support USB devices and bridged networking. Speed was not important, neither was high resolution graphics. All I wanted to do was run some legacy software.

"Qemu Launcher" v1.7.4 (underlying qemu = 0.10.0).
USB did not work - many 'net pages later I realised that USB was only possible with prior knowledge of the device. Then it always grabbed the device that was pre-specified if Qemu was running. Too bad if you wanted to connect to the host and the guest at random times.
Network setup was proving to be just as difficult. Various guides started talking about editing config files - no thanks. Even though I can (and have), I have too many more important things in life to do.

"VirtualBox OSE" v2.1.4_OSE.
USB didn't work at all, I assume you need the full version for that. Canned VB at that point, although a quick try at the networking proved fruitless - couldn't get it to work either.

I also tried VBoxGTK, but it was worse than OSE.

Some people may love hacking config files, but as I said, even though I can, I just don't have the time to waste on that stuff anymore.

I'm not saying that VMware is great, the "features" that have been included in the free 'player' are really very poor. OK, extremely poor. But at least the functionality is good...
If the VM is in focus when a USB is activated, the VM grabs it - otherwise it goes to the host. Very nice concept, focus the VM and turn on USB printer, VM has it. Minimise before turn-on, the host gets it.
Bridged networking just works, no fooling around to get it to work, it just does.

How about it guys, get Qemu to capture USB if in focus!

I *really* wanted to use OSS, or at least close to it, but after giving a week to the cause, I regret to succumb and admit that I will just have to find a VMware "appliance"to suit!

P.

---

### Post by WitchCraft on 2009-10-11
I recommend Xen Paravirtualisation.

Cheapest, fastest, most efficient, most advanced, most flexible and opensource.
A bit harder to setup than VirtualBox, though.
But who cares, after you did it once, you know the game.

---

### Post by maxxjr on 2009-10-12
> **Pinball said:**
> I wanted to set up a new W2K virtual on Ubuntu 9.04. I already had one running in VMware player, but I couldn't find any "appliances" to create a new one, so I started looking for other ways to do the job.

My requirements were **really** simple - the VM had to support USB devices and bridged networking. Speed was not important, neither was high resolution graphics. All I wanted to do was run some legacy software.

"Qemu Launcher" v1.7.4 (underlying qemu = 0.10.0).
USB did not work - many 'net pages later I realised that USB was only possible with prior knowledge of the device. Then it always grabbed the device that was pre-specified if Qemu was running. Too bad if you wanted to connect to the host and the guest at random times.
Network setup was proving to be just as difficult. Various guides started talking about editing config files - no thanks. Even though I can (and have), I have too many more important things in life to do.

"VirtualBox OSE" v2.1.4_OSE.
USB didn't work at all, I assume you need the full version for that. Canned VB at that point, although a quick try at the networking proved fruitless - couldn't get it to work either.

I also tried VBoxGTK, but it was worse than OSE.

Some people may love hacking config files, but as I said, even though I can, I just don't have the time to waste on that stuff anymore.

I'm not saying that VMware is great, the "features" that have been included in the free 'player' are really very poor. OK, extremely poor. But at least the functionality is good...
If the VM is in focus when a USB is activated, the VM grabs it - otherwise it goes to the host. Very nice concept, focus the VM and turn on USB printer, VM has it. Minimise before turn-on, the host gets it.
Bridged networking just works, no fooling around to get it to work, it just does.

How about it guys, get Qemu to capture USB if in focus!

I *really* wanted to use OSS, or at least close to it, but after giving a week to the cause, I regret to succumb and admit that I will just have to find a VMware "appliance"to suit!

P.

The full version of VirtualBox is free (just not open source because Sun isn't able to release source code for things like the USB).  There is a .deb installer on the virtualbox.org website.  Installs fine on Ubuntu.  USB is easy.  Networking is easy.

---

### Post by nooblot on 2009-10-14
I tried last nite the latest VMWare Player (2.5.3) on Jaunty running an existing XP v-machine (quite "lean') - the performance is unacceptable beyond just running firefox....

I don't know if this has anything to do w/ the fact my Jaunty install is via Wubi.
(but v-machine is on ext. HDD)

Can VirtualBox run vmware's machine ?

---

### Post by thomas_d_j on 2009-11-20
> **nooblot said:**
> 
Can VirtualBox run vmware's machine ?

Not exactly.  You can import the virtual hard drive into VBox and then boot from that, and you will get all your files intact.  But because the virtual "hardware" has changed, you may have trouble getting the client XP to boot.  It's like moving a hard drive from one computer to another.  You could try this method to prepare the VMWare machine first: [http://arstechnica.com/hardware/news/2007/09/how-to-install-a-new-motherboard-without-reinstalling-windows.ars](http://arstechnica.com/hardware/news/2007/09/how-to-install-a-new-motherboard-without-reinstalling-windows.ars)

If that doesn't work then you can always do a repair install.

But personally I would just create a new XP machine VBox and transfer your documents across.

---

### Post by degarb on 2010-02-28
> **vanDrunen said:**
> I have been using Qemu (with and without KVM and Kqemu) and VMware (commercial and -player) for a few years and have tested Virtualbox for a few months now.
The best VM to use depends a lot on what you want to do with it. All my experience goes to running Windows 2000, XP and 2003 on top of a Debian/Ubuntu host. Here's some comments on each of these VM's:

*** QEMU ***
Qemu without KVM or kqemu is extremely slow. Check if your CPU supports hardware virtualisation and use KVM whenever possible!!!
In "raw" computing Qemu with KVM outperforms VMware and VirtualBox with ease. It has very little overhead (CPU and memory wise) and is very stable.

The downside of Qemu is that it emulates a really crappy videocard (cirrus 
logic) and the graphics performance is really bad (mouse lag).
If you would run a Windows server in a "headless" virtual machine though and then log on to it using RDP (can be "seamless") then the crappy graphics-card emulation is not a problem at all and the better "raw" performance is a huge benefit!

+ The best "raw" performance
- crappy graphics emulation when running full-screen or windowed
!!! Best used as a server for remote desktop connections (works very well with seamless RDP)

*** VMware ***
VMware is slower than Qemu with KVM in "raw" computing power and without the "guest addons" (the way it is distributed in VMware-player) the graphics are just as crappy as with Qemu.
The commercial version comes with guest add-ons that contain windows drivers for improved performance. These guest add-ons (an iso image with drivers) can also be installed in VMware-player which will give you (almost?) the same performance!

VMware so far is the only VM that has good direct-draw and even some (limited) direct-3D acceleration. You'll see the most benefits of VMware when you're running it full-screen and play 3D-games or CAD/CAM programs that require direct-draw.

+ Very good direct-draw and some direct-3D support
- "Raw" performance is sub-par
!!! Best used for some games and CAD/CAM

*** VirtualBOX ***
VirtualBox is comparable to Qemu with kqemu in "raw" performance but still slower than Qemu with KVM (even if KVM support is enabled in VirtualBox).
With the guest add-ons installed the graphics performance is really good, almost as good as with VMware except for Direct-3D.

VirtualBox just "feels" better than Qemu if you are running windows locally, full-screen or in a window, because of the better graphics support. The closed source version also gives you a "seamless desktop" option which also makes it more usable.
If you're going to run Windows in a headless VM and want to connect to it using RDP then the graphics advantage is gone and it will be outperformed by Qemu with KVM.

+ Better graphics than Qemu
- Slower than Qemu with KVM
!!! Best used for general purpose windows tasks

Above is great, but 3 years old.
This still true in 2010?

---

### Post by nistrum on 2010-03-19
Speaking from my own subjective experience here in 2010; VMWare Player 3.0.1 has some nasty performance issues under a Karmic host with a Windows 7 guest, all x64. I've been led to believe that there are some CPU scheduling issues in the pre 2.6.32 kernel potentially affecting VMWare's SMP but running uniprocessor it's still slower than Virtual Box by a long chalk. The latest PPA of a .32 kernel doesn't fix VMWare for me.

Virtual Box 3.1 runs well. Features are pretty much like-for-like these days apart from the fact that the VMWare graphics driver will support the GPU acceleration required for Aero (if you have nvidia hardware) and Virtual Box will not (although it is on their task list and has been for a while - maybe soon). Virtual Box has a much slower graphics adapter but the CPU and IO performance is far superior.

At the moment I'd recommend Virtual Box if you want to run a virtual Windows 7 on Karmic... unless you have some tremendous hardware and want Aero.

---

### Post by maxadamo on 2010-09-13
> **Bloodfen Razormaw said:**
>  VirtualBox doesn't have VMware's speed or features, and it isn't free either.

This is absolutely wrong. If you state this you have never tried VirtualBox and you behave like a fanboy.
It's true that Vmware has more features.
It's true, for instance, that you cannot split CPU usage with virtualbox, and in server environment this is an important lack of feature.
On the other side, it's also true that desktop users, who usually run a Win XP guest, don't need these features.
It's absolutely false and completely wrong that vmware is faster than virtualbox.
Whoever tried both softwares, can see immediately that virtualbox is many times faster than vmware.

---

### Post by gridleaf on 2010-10-08
I have experimented with vmware and virtualbox, and between those two, I prefer vmware. Yes, virtualbox may be faster, yet I like the features and hardware integration support from vmware more than I like the speed of virtualbox. Unfortunately, I can't comment on QEMU.

---

### Post by HermanAB on 2010-10-10
Hmm, in my experience, if you got your VMware and Virtualbox systems configured properly, then they run at the same speed.

---

