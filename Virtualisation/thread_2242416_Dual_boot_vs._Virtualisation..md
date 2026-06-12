---
title: "Dual boot vs. Virtualisation."
date: 2014-09-01
forum: Virtualisation
---

### Post by nosto53 on 2014-09-01
Have been using dual boot/grub2 (Windows 7 Ultimate x64/Ubuntu 14.04lts 64-bit) for 6-7 months.

Hardware: DIY desktop, AMD FX6300 3.5Ghz, 8GB Ram, one Raptor 150GB(UbuntuOS), one Seagate 1T(WindowsOS).
Everything  seems to works fine.

With dual boot, I think I can only use one OS at a time, then shutdown and re-boot each OS to 'switch' to the other OS. (right?)

In visualization, I think I can start on Windows OS (as host), use Virtualbox, for an example, and run Ubuntu as the guest, right?

Whew... QUESTION: When using Windows on the desktop, can I open a window and "peak inside" in the Ubuntu stuff and 

share data/use (some)apps for each OS side?

Only one more, please: I see that Ubuntu desktop download can be in "x64" or "x86(for 2GB ram)" - which should I use to

run Ubuntu as a guest?

Thanks, Rick 111101

---

### Post by ibjsb4 on 2014-09-01
My setup is a bit different.  I have win7 on its own partition and virtualbox setup on ubuntu running ubuntu virtual machines for testing.

So I can't really tell you about windows with vBox, but I can tell you that VMs work nicely for everyday work.  Games and 3D apps tend to suffer in performance.  So if your a gamer or do things like CAD, I would say its better to do this on a physical partition.  But you never know till you try.

With vBox you can have both OS running at the same time, with either being just a mouse click away.

I run guest machines using either one or a max of two processors and either 2 or 4G of ram.  You can actually decrease performance by having too many processors in the guest system.  And I to date, I cannot tell the difference between 2 or 4G of ram, but I do not do anything that really puts the guest to the test (64bit guest systems).  

[http://ubuntuforums.org/showthread.php?t=2241504&p=13108768&viewfull=1#post13108768](http://ubuntuforums.org/showthread.php?t=2241504&p=13108768&viewfull=1#post13108768)

---

### Post by mastablasta on 2014-09-02
why do you need two Operating Systems? - that's the main question.

no you can't share it like that. I mean theoretically you can but it will only cause problems. you can look at ubuntu data (using 3rd party software) and Ubuntu can read windows.

64bit vs 32bit. for virtual guest use whichever you want (depends why you need it), for install use 64bit.

I run Xubuntu and many others in virtual PC to use them for testing and such. make a snapshot, test it, possibly break it, restore snapshot.

---

### Post by TheFu on 2014-09-04
> **nosto53 said:**
> Whew... QUESTION: When using Windows on the desktop, can I open a window and "peak inside" in the Ubuntu stuff and 

share data/use (some)apps for each OS side?

The other answers above are great.

For the quote above, ... well ... the answer is maybe.

A VM running Linux can provide network shares just like any normal computer on the network.  Generally, it is bad to share the entire OS due to file permissions. Liniux **is** a multiuser OS and file/directory permissions are really, really important. Windows touching any of those files could be bad.

For programs - Windows programs and Linux programs are not compatible, so sharing those really isn't useful.

It really isn't possible for Windows to look inside Linux VMs without the VM running. The file systems are not compatible - that's probably the best way to put it.

For data - Linux and Windows can often share data. It is usually best to have shared data stored on the hostOS and allow access from Linux to the host using either the file sharing capabilities built-into virtualbox or with normal Windows network shares.

In short, keep Linux specific data inside Linux, keep all other data on the hostOS - and especially keep media files (audio/video) on either the hostOS or somewhere else on the network in storage.

---

### Post by vincentertainment on 2014-12-22
I'm pretty new to virtualisation myself.I recently bought a laptop with more resources than I normally get so that I can run Ubuntu and Windows simultaneously. Ubuntu handles most of what I need. There are only a handful of Windows programs that I need and having to leave Ubuntu to run them gets old. Wine is hit or miss. I'd really love to be able to raw mount my windows partition as a guest. What I've gathered so far is mounting raw discs is tricky and risky. Still something I'd like to learn more about.

---

### Post by Tom_ZeCat on 2014-12-29
I've been running Windows 7 under Kubuntu via VirtualBox.  (I'm actually in the process of reinstalling it.)  I also have Windows 7 available as a dual boot.  I rarely ever use the dual boot Windows 7.  The advantage of the dual-boot Windows is when Windows is running it's the only OS running and therefore  has access to all the system resources.  The disadvantage is you have to leave Ubuntu to use it.  

If there's a Windows program I need, I prefer to run it in WINE, if possible.  Some programs run really well in WINE.  Some are a little buggy; some are awful; and some don't run at all.  If something runs really well in WINE, I do that because I prefer to have  the app integrated into Kubuntu.  I run Treepad and Ultralingua in WINE.  They both run well.  If a program doesn't run well enough in WINE, my second choice is to run it in VirtualBox.  VB has a seamless mode which makes it a lot like the Windows app is integrated into *buntu.  I run Quicken, Final Draft, and ConverXtoDVD is VirtualBox.  

When I spend a bunch of money on DVD movies, the last thing I'm going to do is let the kids get their fingerprints all over them, so I make backup copies that I don't care if they destroy.  To do so, I use some excellent software, AnyDVD and DVDShrink that let you copy onto a cheap 4.7 GB DVD.  However, I can't get this to run under VirtualBox, try as I might.  That's the only software I need to boot straight into Windows for.

---

### Post by monkeybrain20122 on 2014-12-29
Dualboot is a pain especially with the new Win8 uefi machines. I just wipe Windows and install Ubuntu. In one of my machines I install Win7 in Vbox for basically one program which doesn't work with wine and set up a shared folder only for those data, otherwise Windows has no access to my files.

---

### Post by Tom_ZeCat on 2014-12-29
> **monkeybrain20122 said:**
> Dualboot is a pain especially with the new Win8 uefi machines. I just wipe Windows and install Ubuntu. In one of my machines I install Win7 in Vbox for basically one program which doesn't work with wine and set up a shared folder only for those data, otherwise Windows has no access to my files.

Plus, the Windows 8 interface is atrocious.

---

