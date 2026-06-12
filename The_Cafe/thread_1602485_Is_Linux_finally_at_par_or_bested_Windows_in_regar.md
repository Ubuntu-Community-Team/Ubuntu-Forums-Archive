---
title: "Is Linux finally at par or bested Windows in regard to hardware compatibility?"
date: 2010-10-21
forum: The Cafe
---

### Post by lnxuser200 on 2010-10-21
I recently purchased a new laptop and passed my old dual boot (lucid/XP) laptop to my youngest child.  
Who incidentally grew up using Ubuntu exclusively, in school and at home. 

        I've always kept my systems dual boot since there is some software that I use which requires that I have 
Windows(XP).  For the most part it's been workable solution.

    My new system was preloaded with Windows 7 64bit,  After purchase I quickly created a sizable partition 
on the drive and installed a lucid 32bit from a disk which I had  burned earlier.  I would have installed a 64bit version 
but since I didn't have one available, nor could download it from the net, (I live in an area without broadband coverage).
I had to wait awhile until I could get my hands on a copy. 

    I use Linux almost exclusively and as such didn't go into the Windows 7 OS, except for a short look around when 
I first purchased the machine.  Just a few days ago I finally booted into Windows and much to my dismay and subsequent 
anger discovered that almost all of my external hardware no longer functions with this 64bit version. No Modem (Actiontec),
no external optical drive (LG), no joystick (Microsoft, yup you read right), and others.  After searching for new drivers 
I discovered that in all but one case, most of these companies did not offer 64bit drivers for these peripherals nor will 
they in the future. Apparently it is not cost effective for them to do so. Since all this hardware worked with my 32bit lucid  
I thought that this was strictly a 64bit issue and gritted my teeth and carried on. When I finally got hold of a 64bit iso of 
10.10 I expected the worse.  Let's face it, one of Linuxes widely publicized drawbacks has always been hardware compatibility.  
Well not this time!  After installing Maverick I was thrilled to find that almost all of my peripherals, which didn't work with 
Windows 7 worked perfectly with Maverick from the start.  No downloading of drivers required,  no dirty fixes or recompiling 
of the kernel to get this or that external peripheral to function.  To be fair, I did have had issues with various bits of internal hardware 
in my laptop but I'm working through them and I'm starting to see progress thanks to the help other readers in these forums

        However, after some consideration in regards to this issue I started to fume again.  Since the mast majority of PC users 
use Windows there must be is a heck of a lot of people in the same predicament .  Ergo, a huge amount perfectly good and 
functioning hardware is being thrown out filling already packed landfills adding unnecessarily to the environmental catastrophe 
we are already suffering under. What makes this especially painful is that it is necessary.  I would suggest the next time a 
computer hardware company claims that they are green, that you think about it. What does their green really mean?

    In the mean time I am searching for Linux alternatives to the Windows software that has kept me chained to that operating 
system for so many years.  When I do, I think I'll have a freedom from MS party and invite all my friends over to celebrate my 
new found freedom.  Then I'll have my 10 year old son show them Ubuntu and let them see first hand just how easy it would be 
for them to throw off the Windows shackles as well.   

Who else is up for having a freedom from windows party? :guitar:

P.S. Don't forget to have your friends and family bring over their working, but now useless hardware.

---

### Post by CharlesA on 2010-10-21
It really depends on your hardware. If you have old hardware, don't expect all of the hardware to work with a 64-bit version of Windows - use the 32-bit version. It's up to the hardware vendor to write drivers for a 64-bit version on Windows.

I haven't had any problems with external optical drives in either Win7 32-bit or 64-bit, but the only external drive I have is USB powered.

I had a hell of a time trying to get an old-as-hell SoundBlaster Xgamer (not 5.1) working with WinXP, but had to use some garbage driver written for Win2K, but it worked in the end.

---

### Post by Spice Weasel on 2010-10-21
Never had any problems with hardware compatibility here (but maybe that's because I only ever use Intel + Nvidia graphics cards...) My printer (HP) has always worked fine, wireless adapter on laptop always worked fine (Belkin) etc.

---

### Post by blueturtl on 2010-10-21
It's not that Windows supports a lot of hardware, never has been. It's that all the vendors support Windows. This means the out-of-store-box experience is usually very pleasant on Windows. However the same vendors, in order to sell more hardware, usually stop supporting their own hardware for newer versions of Windows.

With Linux on the other hand, once support is included it's pretty much there for all architectures and rarely deprecates. This is bad for hardware sales, but good for consumers.

Linux hardware support is leaps and bounds better than Windows, only problems exhibited in this regard are with closed-spec-hardware or rare specialty hardware or win-only-crapware (hardware without the actual hardware, replaced with a software driver).

---

### Post by lnxuser200 on 2010-10-21
> **CharlesA said:**
> It really depends on your hardware..

My modem is only a few years old, I don't think it's old but I'll admit ones perspective is relative. Its an external USB. It works as is with Lucid 32bit and Maverick 64bit right after I installed it and set it up with pppconfig. 

In Win 7-64 nothing, their isn't even a generic 56k modem driver to pick from like there used to be in XP. At least none I could find. If someone knows different I'd sure like to know where to find them.

My optical drive is old granted, none the less, it it to works perfectly with every flavor of Ubuntu no problem. Once again in Win 7-64 zip, like it's not even there.

 So why does it work with Linux and not Windows?  

My Hp printer is the my only external peripheral that works with Win7-64,  Then again it's brand new.  

I'm just glad I'm using Linux and what worked before, still does.

---

### Post by lnxuser200 on 2010-10-21
> **blueturtl said:**
> It's not that Windows supports a lot of hardware, never has been. It's that all the vendors support Windows. This means the out-of-store-box experience is usually very pleasant on Windows. However the same vendors, in order to sell more hardware, usually stop supporting their own hardware for newer versions of Windows.

With Linux on the other hand, once support is included it's pretty much there for all architectures and rarely deprecates. This is bad for hardware sales, but good for consumers.

Linux hardware support is leaps and bounds better than Windows, only problems exhibited in this regard are with closed-spec-hardware or rare specialty hardware or win-only-crapware (hardware without the actual hardware, replaced with a software driver).

It's also a circular game.   If you get pissed off with manufacturer A and swear never to buy their products again, they don't care. They know your neighbor, who owns manufacturer B's product has just done the same thing and goes out and buys manufacturer A's product.. You on the other hand are smugly standing in line behind him at the checkout with product B.  

I'm no economist, as you can obviously tell from my description above. I understand it's not quite so simple.  What I do know is that I once owned an Kaypro  computer (considered then to be portable, ha) It was one thing and worked perfectly for many years. Now I have dozens of assorted gadgets and gizmo's to support other gadgets and so forth, all of which, although perfectly good,  need replacing when somebody somewhere deems it so. 

Like I said, I'm no economist. :lol:

---

### Post by Yavatar on 2010-10-22
Starting with Windows Vista, MS dumped all the legacy stuff. No more 486SX support with original soundblasters and 8mb Stealth 2D video cards. ;) Microsoft had been trying to do this for years but kept holding back dropping all the legacy stuff.

Finally MS said, "Hey, it's time to get with the times. We can't keep supporting all this old stuff and have a good (sic) OS." (Note that every promise of what the new OS will do is not fulfilled until the next generation.)

Even straight Ubuntu has its limitations. The peripherals aren't quite as important as in Windows, but you still need a decent CPU, graphics chip, and RAM although you'll get farther back than you would for Windows. Of course, the more up-to-date things you use the better the experience will be. ;)

The problem with Windows is that even though Windows 95 is 16 years old, the newer Windows are still built on the same core technologies so MS will never release the code. That incidentally is why OS/2 will never be fully open-source. I actually asked one of the IBM Unix guys about this and he explained that because OS/2 was codeveloped with MS, it still contains core elements still used in current Windows (likely modified and updated but its kind of like the Linux kernel).

Of course, the flip-side of that is who really is going to make an alternative to Windows? Apple is probably the only big player who could, but they aren't going to commit blasphemy touching non Apple-blessed hardware. Oracle bought out Sun, but I doubt they could care developing a Windows alternative when they have UNIX or Linux which they can modify as they like. My understanding is Solaris is a dying breed and Sun was moving away from it before they were gobbled up by Oracle. Oracle probably could care less about the hardware. If 90% of the populace wants Win machines, they'll make some damn impressive applications for it. If everybody switches to Linux, they'll still do it. =)

Okay, enough rambling for now. ;)

Yav

---

### Post by JDShu on 2010-10-22
Printers, Wireless cards, and Graphics cards are still behind, but we're getting there :)

---

### Post by Khakilang on 2010-10-22
That's why we are here and free from proprietary software vendor lock in without much help.

---

### Post by the8thstar on 2010-10-22
I'd like to add my own point of view. I recently installed a copy of Vista Home Premium on my old trusted P4 (3GHz, 1Gb RAM, 256 Mb GeForce 6200, 40Gb partition on my HDD) as a dual booter with Ubuntu 10.04.

What a pain it was. The updates (all the way from 2007 vanilla edition to full on 2011 Windows Live latest updates) took TWO days! Two days to get a full hardware compatibility and all the security patches. Yikes... Ubuntu is so much faster to update and upgrade in that aspect, it's simply CRAZY.

---

### Post by oregonbob on 2010-10-22
No. Linux is not as good as Windows because all the hardware vendors do WIndows first and best. Buit Linux is getting real good, better all the time.

---

### Post by 3rdalbum on 2010-10-22
Linux driver developers have to write their drivers to work on 11 different CPU architectures, and provide the source code so it can be compiled for anything. Whereas on Windows, many drivers were written specifically for 32 bit x86 and would have to be rewritten for anything else. Or the developer decides not to bother compiling for 64 bit because "nobody uses it" - and nobody uses it because there are no drivers.

Your optical drive should not require external drivers though, they are all standard devices.

---

### Post by Half-Left on 2010-10-22
Linux has better hardware support out of the box, end of story.

---

### Post by Grenage on 2010-10-22
> **CharlesA said:**
> It really depends on your hardware. If you have old hardware, don't expect all of the hardware to work with a 64-bit version of Windows - use the 32-bit version. It's up to the hardware vendor to write drivers for a 64-bit version on Windows.

From Vista onwards, MS won't sign a 32-bit driver unless a 64-bit driver is also included.

---

### Post by julio_cortez on 2010-10-22
> **Grenage said:**
> From Vista onwards, MS won't sign a 32-bit driver unless a 64-bit driver is also included.Yes it's a step forward but.. Aren't only the x64 versions of Windows that require signed drivers?
*I may be wrong though, but I think that on Windows 7 x86 you could still install unsigned drivers. Thing that you cannot do on Windows 7 x64 (talking about the Professional version).*

So, if a company only produces an x86 driver, it won't be signed according to Microsoft's policy, but it'll just work on x86 machines because they don't need signed drivers.
*Again, might be wrong.*

---

### Post by Grenage on 2010-10-22
> **julio_cortez said:**
> Yes it's a step forward but.. Aren't only the x64 versions of Windows that require signed drivers?
*I may be wrong though, but I think that on Windows 7 x86 you could still install unsigned drivers. Thing that you cannot do on Windows 7 x64 (talking about the Professional version).*

So, if a company only produces an x86 driver, it won't be signed according to Microsoft's policy, but it'll just work on x86 machines because they don't need signed drivers.
*Again, might be wrong.*

Yes, I believe that is the case.  It's still a major motivation for manufacturers, because they don't want customers to get worried when a big message pops up:

> WINDOWS CANNOT VERIFY THE PUBLISHER OF THIS DRIVER SOFTWARE.
It may harm your computer, steal your data, or molest your children

Naturally, I had to embellish.

---

### Post by toupeiro on 2010-10-23
In my opinion, this happened a long time ago.  Here I'll demonstrate: 


Let me borrow your sprint air card, no no software, just the card please, and I'll show you how I can use my Wiimote as a RF mouse at a coffee shop running modern linux on a 6 year old laptop, all with no driver installation CD's or reboots. 

Windows cannot compare anymore when it comes to hardware support.  I'm not saying linux supports *everything*, but it supports a hell of a lot more than windows out of the box.

---

### Post by Dr. C on 2010-10-23
When comparing hardware support between Linux and Microsoft Windows it is critical to consider which version of Microsoft Windows one is taking about. The different driver models are at the heart of this. 

For Linux the drivers are for the most part available as FLOSS either because the source is provided by the manufacturer or it is reversed engineered by the community. The advantage is that migration from 32 bit to 64 bit or from x86 to ARM becomes a simple recompile. The disadvantage is that this does take time for a driver to work its way into the latest version of Ubuntu. By the way I have repeatedly found that a peripheral (wireless, modems, USB sound, video capture, etc. ) that did not work in a previous version of Ubuntu works flawlessly in the latest version. 

For Microsoft Windows the driver is provided right away as propriety software. The advantage is that it is available right away. The disadvantages are many but long term. If the driver model is changed then only the original manufacturer can release a new driver, but in most cases they have little or no financial incentive to do so. In addition Microsoft's signed driver policy would preclude a "reverse ndiswrapper" approach of using the Linux driver in Windows. The result as the OP has correctly posted is that one must either get rid of Windows or dispose of the peripheral in question. The latter of course will cause environmental damage, global warming, exposed children in developing countries absorbing toxins etc.

As for current driver support. 

1) Microsoft Windows XP 32 bit. This one is still on top as most hardware manufactures are still providing propriety drivers. XP will not hold top position for long. 

2) Linux 32 bit close second to XP

3) Linux 64 bit and Linux on ARM very close third.

Big gap

4) Windows Vista / 7 32 bit

Another big gap as the 32 bit versions of Windows Vista / 7 allow unsigned drivers but the 64 bit versions do not 

5) Windows Vista / 7 64 bit

PS Ever wonder why the iPad does not have USB ports, while Linux tablets do? Same problem as with Microsoft Windows.

---

### Post by clay_in_nj on 2010-10-23
From my personal experience (FWIW) every Windows install has required getting drivers from disk or online to make everything work.  Every Ubuntu install I've done just works.  Just look at the fact that so many Linux distros have live discs, which just boot up and run.  The only Windows live disc I've tried is the XP BartPE, and it takes forever to boot, doesn't work on all machines, and gives a very limited OS experience.

---

### Post by MisterGaribaldi on 2010-10-23
I used to work for a big technology company, and when we switched from Win 95/98/ME to WinXP, many of our customers went through the same thing. They had to replace all kinds of things -- scanners, printers, etc. -- because either there was no XP support for them, or because (for instance) we quit putting "real" parallel ports on our systems, and their drivers -- which might otherwise work under WinXP -- wouldn't adapt over to other busses, such as USB, which is how our parallel ports got connected to the internals.

As to the OP's point about being "green" and all that, remember that companies will always try to do what's in their perceived financial best interest. Arguably, many companies have done a lot of bad things, but there also comes a point when rules and laws contravene legitimate profitability-related business interests. (And I think we all know what happened to Soviet Russia.)

Anyhow, I think hardware makers would earn a LOT more respect if they would just open up their APIs to the open-source community and let them develop drivers (whether for Linux, Windows, or Mac OS X). This would cut out a LOT of their overhead and perhaps make up for sales losses otherwise associated with legacy device support.

---

### Post by phrostbyte on 2010-10-23
I'd like to see Windows running on my VAXstation! :eek:

Linux is by far the most flexible operating system in the world when it comes on running on different hardware systems.

---

### Post by weasel fierce on 2010-10-23
Out of the box, windows doesn't support very much hardware at all. 
The illusion comes from most hardware vendors providing drivers to install.

When was windows coming out for power PC, ARM and 68K btw ?

---

### Post by Dr. C on 2010-10-23
> **MisterGaribaldi said:**
> I used to work for a big technology company, and when we switched from Win 95/98/ME to WinXP, many of our customers went through the same thing. They had to replace all kinds of things -- scanners, printers, etc. -- because either there was no XP support for them, or because (for instance) we quit putting "real" parallel ports on our systems, and their drivers -- which might otherwise work under WinXP -- wouldn't adapt over to other busses, such as USB, which is how our parallel ports got connected to the internals.

As to the OP's point about being "green" and all that, remember that companies will always try to do what's in their perceived financial best interest. Arguably, many companies have done a lot of bad things, but there also comes a point when rules and laws contravene legitimate profitability-related business interests. (And I think we all know what happened to Soviet Russia.)

Anyhow, I think hardware makers would earn a LOT more respect if they would just open up their APIs to the open-source community and let them develop drivers (whether for Linux, Windows, or Mac OS X). This would cut out a LOT of their overhead and perhaps make up for sales losses otherwise associated with legacy device support.

There is a direct correlation between using FLOSS drivers and being green. There is no need for new regulations however, one can make existing regulations smarter. For example many jurisdictions charge a recycling fee on computer components. One can levy a lower recycling fee on computer components with FLOSS drivers as they are less likely to require recycling.

---

### Post by SeijiSensei on 2010-10-23
Given the large number of postings about wireless connectivity that I see in Networking and Wireless, Linux still has a ways to go in this department.

Windows 7 does a better job of finding the drivers it needs automatically off the Internet than any version of Windows before it.  I was quite surprised when I installed it from scratch the first time.  I believe there are ways to make the 32-bit drivers work in 64-bit Windows, but I don't care enough to search the Internet for that.

@ Yavatar
Windows versions starting with [XP]("http://en.wikipedia.org/wiki/Window_XP") are based on the NT platform, not the DOS/Win95/Win98 platform.  I'm hardly a Windows guy, but let's at least be accurate.  NT has roots back to Digital [VMS]("http://en.wikipedia.org/wiki/VAX/VMS") and was designed as a multi-user, multi-taking operating system from the ground up.  That said, I still think Windows has fundamental security problems because it still wants to support the model of a single user on a non-networked PC.  Win7 is certainly much better in this regard than in the XP days, but Windows was never developed with the Unix philosophy of full-time networking with the security problems that entails.

---

### Post by lancest on 2010-10-23
Just an observation about Linux connectivity wireless vs XP/Vista.
 
On several occasions I've witnessed Linux wireless to function better than Windows. In public and at home various chipsets.
 
We've got an older ASUS notebook that for instance that can't connect at all (using the Intel driver) at home but works great with Ubuntu. 
Windows users have often told me they can't connect to WIFI in cafe's but I never seem to have a problem with two MSI netbooks.
 
IMHO better connectivity is a good reason to consider dual booting Windows with Ubuntu.

---

### Post by weasel fierce on 2010-10-23
Anecdotal evidence and all, but the last laptop we had that ran XP several years back failed to connect wireless without a driver install, ditto for the desktop before it was converted to linux.

So if "par" means "neither bloody works", linux has been on top of it for years :)

---

### Post by Chame_Wizard on 2010-10-23
It's already common knowledge that the penguin OS recognize a lot of hardware.Most of those are not even yet supported on the other OS.:guitar:

---

### Post by smellyman on 2010-10-23
> **SeijiSensei said:**
> Given the large number of postings about wireless connectivity that I see in Networking and Wireless, Linux still has a ways to go in this department.


When I install an over the counter Windows os and not the oem's disc with all the drivers almost always the wireless does not work.  Sometimes the ethernet doesn't work.  getting on the web to find drivers obviously becomes difficult at that point.

It is a giant pain to install windows without an oem driver disc.

---

