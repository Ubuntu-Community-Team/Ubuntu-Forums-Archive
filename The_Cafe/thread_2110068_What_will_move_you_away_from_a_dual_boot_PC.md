---
title: "What will move you away from a dual boot PC"
date: 2013-01-29
forum: The Cafe
---

### Post by waltd on 2013-01-29
Hi all,
    I'm new to ubuntu and Linux.  I love Ubuntu, the Linux ecosphere and community.  But here's two reasons I keep a dual boot PC with Windows and Ubuntu until I find a solution.  
     1. Quicken -   I keep it because it has several features, like automatic reconcile, I can't be without.  Doesn't work well in Wine. 
     2. VPN -  most VPN types don't come out of the box with Ubuntu.  Installing the missing VPN types is challenging.

---

### Post by BlinkinCat on 2013-01-29
Hi waltd,

Firstly don't concern yourself about dual booting.

Quite a high proportion of members would do just that too - :P

---

### Post by fyfe54 on 2013-01-29
Turbotax is the ONLY thing I need that requires Windows..  No Linux version and is useless in Wine.

---

### Post by Umbra Diaboli on 2013-01-29
Set up a Windows VirtualBox with Oracle's VB - that way you wont have to dual boot, and you'll be able to share your files between Ubuntu and Windows.

---

### Post by waltd on 2013-01-29
> **fyfe54 said:**
> Turbotax is the ONLY thing I need that requires Windows..  No Linux version and is useless in Wine.

May I suggest using the Turbo Tax web site.  The desktop program is no longer needed.  All the functions that are in the desk top program are now on the web site.  I've been doing my taxes online for many years.   :D

---

### Post by waltd on 2013-01-29
> **Umbra Diaboli said:**
> Set up a Windows VirtualBox with Oracle's VB - that way you wont have to dual boot, and you'll be able to share your files between Ubuntu and Windows.

An Oracle VB is a good idea.  Is it working ok for you?  Any problems?

---

### Post by omeomi on 2013-01-29
> **Umbra Diaboli said:**
> Set up a Windows VirtualBox with Oracle's VB - that way you wont have to dual boot, and you'll be able to share your files between Ubuntu and Windows.

After having had a dual boot for many years, I find this solution fits all of my needs entirely. And even with that I think I only used the virtual machine about 4 times in the last year...

Aside from programs that require heavy graphics everything runs perfect in a virtual machine.

---

### Post by montag dp on 2013-01-29
The one real thing keeping me from booting only Linux is this:

[http://www.rhino3d.com/]("http://www.rhino3d.com/")

---

### Post by mastablasta on 2013-01-29
online banking - the chip can only be read in windows by some programme
games, games, games.... - i would miss some that are windows only
 
otherwise nothing much else. if linux works fine on the hardware (drivers and all) then it is quite pleasant and fast to use.

---

### Post by Autofac on 2013-01-29
For now, games.

I've been told and assured that there maybe ways to do everything I want on Linux but the time required to learn how to do that and then implement it, truthfully, is more than I care to take on right now. It's easier to simply have a second HD and dual boot into XP for games--too much instant gratification, but oh well.

It's something when I have more time, and in the future, I would like to nix out, but until then I plan to dual boot. 

That said, I've found myself able to do pretty well everything else I could want to do in Linux, both through Linux Apps and Wine. Plus I am not as worried about devastating crashes like the last one that caused me to try Ubuntu to begin with.

---

### Post by HermanAB on 2013-01-29
Dual booting is sooo last century.  I haven't used dual booting since about, well, uhm, I can't remember when. Virtualbox and VMWare is the solution.

---

### Post by santosh83 on 2013-01-29
> **waltd said:**
> Hi all,
    I'm new to ubuntu and Linux.  I love Ubuntu, the Linux ecosphere and community.  But here's two reasons I keep a dual boot PC with Windows and Ubuntu until I find a solution.  
     1. Quicken -   I keep it because it has several features, like automatic reconcile, I can't be without.  Doesn't work well in Wine. 
     2. VPN -  most VPN types don't come out of the box with Ubuntu.  Installing the missing VPN types is challenging.

To answer your subject question, I'm already purely with Linux since 2005, and the last time I touched Windows was during the XP SP2 era. :-)

Sometimes I do get the urge to try out the latest games, but so far I've resisted, and since it looks like Steam has finally arrived, the last and only reason I might've gone back to Windows is now gone!

What worries me for the future is the current focus on so-called Secure Boot by all the industry heavyweights, guided by heaviest of them all.

Secure boot shouldn't become the '*One Ring*' that '*rules them all, and in the darkness, binds them.*' In that world, Linux (the Hobbits) won't long survive. :-(

---

### Post by Umbra Diaboli on 2013-01-29
> **waltd said:**
> An Oracle VB is a good idea.  Is it working ok for you?  Any problems?

It is now working perfectly with Windows 7 x86. 

I did have 2 problems though. I'll write them here with the solutions in case you decide to use Oracle's VirtualBox and you encounter the same errors.

The first one was the following error:[INDENT]   *Kernel driver not installed (rc=-1908)*
*The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or   there is a permission problem with /dev/vboxdrv. Please reinstall the   kernel module by executing*
*'/etc/init.d/vboxdrv setup'*
*as root. If it is available in your distribution, you should install   the DKMS package first. This package keeps track of Linux kernel   changes and recompiles the vboxdrv kernel module if necessary.*


[/INDENT]Which I solved by doing the following on terminal:

(Close Oracle's VB, then type on terminal)

```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get remove dkms   sudo apt-get install dkms virtualbox-dkms  
modprobe vboxdrv
```

With no reboot required.

The second was that the VirtualBox did not recognize my internet connection, it was easily solved with the following command:

```
VBoxManage modifyvm "VM name" --natdnshostresolver1 on
```Replacing the VM name with the name of your guest (in my case I just named it Windows 7)

However, this is per VM, if you want to set it globally type the following:

```
VBoxManage setextradata global natdnshostresolver1 on
```Cheers,
***Umbra Diaboli***

---

### Post by Frogs Hair on 2013-01-29
Having an employer and school that supports Linux would help. I have never worked for anyone that allows a person to use their own software. 

When it comes to school instructors will lower grades for formatting errors and don't want documents from programs other than MSO. Course related software for many study programs often only runs in Windows also.


Dual booting at least for me makes more sense that fooling around with Wine and I haven't tried any VM programs since Windows is already installed. If I wipe the hard-drive I will consider it.  

Removing Windows so I can run it in V Box or VM ware doesn't make sense to me and doesn't make me Windows free.

---

### Post by Dr. C on 2013-01-29
> **mastablasta said:**
> online banking - the chip can only be read in windows by some programme
games, games, games.... - i would miss some that are windows only
 
otherwise nothing much else. if linux works fine on the hardware (drivers and all) then it is quite pleasant and fast to use.

Oneline banking: If a bank tries to force clients to use Microsoft Windows or not use GNU/Linux I would suggest withdrawing all deposit funds from such a bank ***even if one uses Microsoft Windows as one's primary operating system***. 

Why because given the nature of modern fractional reserve banking if say 1% of a bank's customers were to withdraw thier funds from a bank, it could easily trigger a run on the bank, and GNU/Linux has over 1% market share on the desktop. 

[http://blog.emergencyoutdoors.com/how-to-survive-protect-yourself-from-a-bank-run-on-the-banks/]("http://blog.emergencyoutdoors.com/how-to-survive-protect-yourself-from-a-bank-run-on-the-banks/")
[http://www.forbes.com/sites/greatspeculations/2012/09/21/run-on-the-banks-would-make-fiscal-cliff-look-like-a-speed-bump/]("http://www.forbes.com/sites/greatspeculations/2012/09/21/run-on-the-banks-would-make-fiscal-cliff-look-like-a-speed-bump/")

---

### Post by fyfe54 on 2013-01-29
Yeah, I could, but I file electronically and also have New York to file.

---

### Post by BigCityCat on 2013-01-29
> **fyfe54 said:**
> Turbotax is the ONLY thing I need that requires Windows..  No Linux version and is useless in Wine.

The website works good.

---

### Post by offgridguy on 2013-01-29
> **BlinkinCat said:**
> Hi waltd,

Firstly don't concern yourself about dual booting.

Quite a high proportion of members would do just that too - :P
Agreed

---

### Post by Nr90 on 2013-01-29
> **Frogs Hair said:**
> Having an employer and school that supports Linux would help. I have never worked for anyone that allows a person to use their own software. 

When it comes to school instructors will lower grades for formatting errors and don't want documents from programs other than MSO. Course related software for many study programs often only runs in Windows also.


Just hand it in as a PDF?

Meh, my teachers recommend / require all assignments be created in latex anyway.

---

### Post by craig10x on 2013-01-29
> **fyfe54 said:**
> Yeah, I could, but I file electronically and also have New York to file.

You can do your New York State/City Income Tax form as well as the Federal Tax form and e-file BOTH using the online programs of most major companies including Turbo Tax and Tax Act (i have used both and they work fine...these days, mostly i use Tax Act)...

So, if that is the ONLY reason you are keeping windows, go ahead a "chuck it" ;)

---

### Post by Copper Bezel on 2013-01-29
[QUOTE=Nr90]Just hand it in as a PDF?

Meh, my teachers recommend / require all assignments be created in latex anyway.[/QUOTE]
For my online classes, I wouldn't accept PDFs - I can't use Word or LibreOffice to make comments on them, and I frankly don't want to disrupt my workflow to deal with a PDF annotator. I do accept .odt, but the point is that there really are reasons behind format requirements in some cases.

---

### Post by 8BitDoughnut on 2013-01-29
I can't say that I would stop dual booting,  but the one thing that keeps a windows partition on my hard drive is the  lack of being able to use Netflix on a 64 bit version of Ubuntu 12.04.  It still does rely on the writers of the Ehoover Compolio Netflix package to provide that support though, but if the Ubuntu developers were to create a package for the 64 bit version of Ubuntu 12.04, I would remove my windows partition completely.

---

### Post by waltd on 2013-01-30
> **HermanAB said:**
> Dual booting is sooo last century.  I haven't used dual booting since about, well, uhm, I can't remember when. Virtualbox and VMWare is the solution.
  
I went to the VMWare web site and it seems orientated toward big business and corporations.  Is there a way to use VMWare for home PC that's, hopefully, free, or very inexpensive and needs to run only a few Windows programs and games?  What is your arrangement.   Thanks.

---

### Post by undecided4 on 2013-01-30
dual boot tends to add up to the booting time.

---

### Post by Laiquendi on 2013-01-30
VM does not let you use full graphic potential, and I unfortunately need it sometimes... For games which are windows only (though I deeply believe it will change :D) and also my wife uses some programs as an architect, and those are usually strictly one-platformed :/

So I envy those who can delete windows completely ;D

---

### Post by santosh83 on 2013-01-30
> **waltd said:**
> I went to the VMWare web site and it seems orientated toward big business and corporations.  Is there a way to use VMWare for home PC that's, hopefully, free, or very inexpensive and needs to run only a few Windows programs and games?  What is your arrangement.   Thanks.

I believe the VMWare Player is free for personal use. It can run existing virtual machine images in compatible format and also create virtual machine images. There's also VirtualBox which you can consider, and it's also open source, unlike VMWare Player.

But games with serious graphics use are still poor in performance under any virtualisation solution. Small games are okay, but if you want to run games which make use accelerated graphics, 3D and such then nothing beats running directly on the hardware.

---

### Post by JCC955i on 2013-01-30
Games here too. I don't mind running a dual boot setup though, and a lot of apps - keepass, truecrypt, etc etc... work perfectly across both platforms, so inetoperability isn't really an issue outside of gaming.

I think the advent of Windows 8 has pushed me further towards fully replacing my day to day with Ubuntu than anything else. I suspect Windows 7 will be the last Microsoft OS that I install at home.

---

### Post by linuxcoffeelover on 2013-01-30
> **JCC955i said:**
> Games here too. I don't mind running a dual boot setup though, and a lot of apps - keepass, truecrypt, etc etc... work perfectly across both platforms, so inetoperability isn't really an issue outside of gaming.

I think the advent of Windows 8 has pushed me further towards fully replacing my day to day with Ubuntu than anything else. I suspect Windows 7 will be the last Microsoft OS that I install at home.

When I found out and saw Windows 8 I swore it would never see the light of day on any of my computers, And now with steam for linux I no longer have to think about windows.

---

### Post by Artemis3 on 2013-02-01
After a year of not using it, i removed my last windows HD, dual boot is now completely gone. Plenty of games run in wine, plus the many emulators and many native ones are coming with steam. Banking works just fine with the banks i use, and the taxes are done online. Netflix doesn't work here and i don't need it anyway.

If you are only running a couple of apps, do try the virtual machine route (vbox, vmware, qemu, etc).

---

### Post by monkeybrain2012 on 2013-02-01
> **waltd said:**
> I went to the VMWare web site and it seems orientated toward big business and corporations.  Is there a way to use VMWare for home PC that's, hopefully, free, or very inexpensive and needs to run only a few Windows programs and games?  What is your arrangement.   Thanks.

Get virtualbox. You can get the opensource version (community version) from the software centre, or you can get Oracle's version by adding a ppa (has some extra stuffs like usb support)[http://www.webupd8.org/2012/04/virtualbox-ubuntu-1204-precise-pangolin.html](http://www.webupd8.org/2012/04/virtualbox-ubuntu-1204-precise-pangolin.html)

I need one or two application in Windows (come to think of it actually only one) and Vbox solved my problem.

---

### Post by PSBTornado on 2013-02-01
I've gone to a virtual machine for Windows. No dual booting for me. Thanks to my brother in law for the idea.

---

### Post by cg40k on 2013-02-01
Steam coming to Ubuntu has made Windows obsolete IMO. The only thing that Windows had was gaming and now, with Win8, that is changing.

---

