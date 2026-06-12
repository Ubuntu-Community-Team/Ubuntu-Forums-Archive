---
title: "Looking to Transition to BSD"
date: 2010-05-04
forum: The Cafe
---

### Post by purgatori on 2010-05-04
Linux and me used to be the best of pals, but lately our relationship has become very strained. Once upon a time, I felt I could depend on Linux to be a reasonably dependable and stable platform for me to conduct my work, but lately, but lately there seems to have been a push -- especially in Ubuntu-land -- to make Linux more of a competitor with Windows and OSX. What this has meant, for the most part, is the implementation of a lot of bells and whistles, such as fancy graphical startup sequences, which tend to break or impair compatibility with old hardware (like mine), and reduce transparency/availability of information. Somewhere along the way, the Linux philosophy seems to have gone in a direction which I cannot endorse.

I don't want to get into a philosophical debate, however, as the main problem for me is that Linux has become very unstable on my old hardware -- namely my 82845g integrated graphics chipset -- and with no fix on the immediate horizon, and lots of work that I need to get done, I think that it's perhaps time for me to look around for other operating systems. Windows is one possible alternative, but to be honest, the thought of that horrid window manager/desktop, and the lack of a CLI that is anywhere close to being as good as those on offer in Linux makes me cringe.  

Another alternative is BSD, and I have heard a lot of good things about it in terms of stability and hardware management (if not necessarily support). The only problem is that I lack any kind of experience in installing, setting up, or using BSD, and I can't really afford to spend months learning how, because I have other demands on my time, and need to be able to set up a viable work environment on my machine within a relatively short amount of time. 

From what I've heard, DesktopBSD and PCBSD are both easy to use and install, but they both use KDE, which is not what I'm looking for at all (I like tiling wms, like scrotwm and wmii), and I have read that a lot of functionality is lost if one happens to manually install other desktop environments/wms. I'd also like a distribution with some kind of LiveCD that I can use in order to test it out and make sure that it actually works better with my hardware than Linux currently does, but as far as I know, there are only a handful of BSD distros that do this? 

Anyway, if BSD users or those generally 'in the know' when it comes to BSD can make any suggestions as to where a fairly proficient Linux user, but total BSD n00b, should start, I would greatly appreciate it.

---

### Post by Pogeymanz on 2010-05-04
I feel your pain. May I ask which distros you've tried? It could make a difference.

As far as BSD goes, I loved FreeBSD, but the installer is similar to Arch Linux's, so PCBSD would get my vote. Although, BSD does a few things differently than Linux does, so there will be a learning curve no matter how simple the installer is.

Maybe try Chakra for an easy way to install Arch Linux, since it adheres to a BSD style of doing things. The truth is, "Linux" is just the kernel, so unless you have an issue with kernel development, you might just need a different distro.

---

### Post by MarcusW on 2010-05-04
What dists have you tried? Have you tried one considered more stable than Ubuntu, like Debian or RHEL or something like that?

Not that I have anything against you switching to *BSD ofc, just curious. :)

---

### Post by kk0sse54 on 2010-05-04
As Pogeymanz stated, *BSD , although similar, is quite different linux and you will notice various quirks. It's like trying to transistion to linux from windows in that don't approach *BSD with the linux mindset on how to do things. 

If you don't have any experience with *BSD at all I second PC-BSD as DesktopBSD has been effectively dead since it's last release. Personally though I hate the concept of PBIs (PC-BSD installers) and prefer vanilla FreeBSD + ports which in of itself isn't too hard to set up as long as you follow the handbook as all the *BSDs have excellent documentation. Furthermore, a minimalistic FreeBSD install might be more of what you're looking for if you're trying to get away from KDE and just trying to stick with the tiling WMs. As for NetBSD and OpenBSD, both are great systems but  I've found FreeBSD to be the most practical in that it has the most software available and is the only one I gotten flash to work on though linux compatibility.

P.S. all the *BSDs have liveCDs but personally I've never really used them except for Jibbed which is a NetBSD liveCD. I've tried a few FreeBSD liveCDs which didn't work with my hardware even though I have FreeBSD installed right now and it works great. Nevertheless hardware compatability is still the biggest downside to *BSD.

---

### Post by gletob on 2010-05-04
You probably be better of in a BSD forum...

But I like FreeBSD, just so you know.  Find some stuff and play with it in a virtual machine.

---

### Post by purgatori on 2010-05-04
> **Pogeymanz said:**
> I feel your pain. May I ask which distros you've tried? It could make a difference.

As far as BSD goes, I loved FreeBSD, but the installer is similar to Arch Linux's, so PCBSD would get my vote. Although, BSD does a few things differently than Linux does, so there will be a learning curve no matter how simple the installer is.

Maybe try Chakra for an easy way to install Arch Linux, since it adheres to a BSD style of doing things. The truth is, "Linux" is just the kernel, so unless you have an issue with kernel development, you might just need a different distro.

A different distro was my first thought as well, but I have seen this same bug reported across multiple distros, including: RHEL, Arch, Gentoo, and SuSE -- so it appears to be at the level of the kernel, xorg/intel-xorg. After searching both Google, and BSD-related forums, I have not seen anyone reporting the same bug over there, despite the fact that they use Xorg + intel-xorg as well, which makes me think it has something to do with the kernel development on Linux itself... though that is simply an uneducated guess. 

FreeBSD looks awesome, but very daunting at the same time. I did start to download it, but when I was reading the handbook I learned that if you wanted to install additional packages in the beginning, you needed two other installation CDs, unless you wanted to reboot into a working OS, use sysinstall, blah blah, and I could only find one installation CD (apart from the boot only) on their FTP... which I figure isn't exactly a good sign. 

I'm quite comfortable with the command-line, but I am not an expert by any means, and so FreeBSD, like Arch, looks a little bit out of my depth. Not only that, but I'm not a PC hobbyist -- I use these things for work -- and simply can't afford to spend weeks building a system... so perhaps PCBSD is my only option, even though I'm uncomfortable with KDE as the default desktop, and all their custom-built graphical apps and scripts -- my experience with Ubuntu has taught me that such features, while initially making things easier, only makes it more difficult when you need to get down to the nitty gritty of the system, and then find that the core system and whatever custom stuff they've added come into conflict, essentially creating an additional layer of complexity.

---

### Post by kk0sse54 on 2010-05-04
> **purgatori said:**
> 
FreeBSD looks awesome, but very daunting at the same time. I did start to download it, but when I was reading the handbook I learned that if you wanted to install additional packages in the beginning, you needed two other installation CDs, unless you wanted to reboot into a working OS, use sysinstall, blah blah, and I could only find one installation CD (apart from the boot only) on their FTP... which I figure isn't exactly a good sign.
You can just use the boot-only CD and grab all the packages through ftp/http. Also doing a minimal install and running sysinstall later is a lot easier than you think. After the install all you need to do is type in the command "sysinstall" and the exact menu that you got during installation will be present again and all you to install different package sets from the net or do any additional configuration. That being said I find FreeBSD's sysinstall to be quite dated for such things as ZFS, but in most cases it gets the job done.

> Not only that, but I'm not a PC hobbyist -- I use these things for work -- and simply can't afford to spend weeks building a system... 
You don't have to use ports to compile everything, there's binary packages available that you can install through pkg_add. It's all in the handbook :)

---

### Post by cb951303 on 2010-05-04
Note that BSD distros uses Xorg, GNOME and KDE too.
If your problems are UI based then they won't go away.

---

### Post by Gone fishing on 2010-05-04
I've used PCBSD (just a quick play) and it worked the KDE was quite polished and most things worked well. I didn't like the idea of PBIs but they did work smoothly.

I believe the PCBSD will now let you install a straight FreeBSD?

On the negative side a lot less software, a little more fiddly and well I preferred my Ubuntu. I'm sure you can set up PCBSD or FreeBSD with another desktop, but I wondering if something like Crunchbag would do what you want with less of a learning curve?

---

### Post by Pogeymanz on 2010-05-04
> **purgatori said:**
> A different distro was my first thought as well, but I have seen this same bug reported across multiple distros, including: RHEL, Arch, Gentoo, and SuSE -- so it appears to be at the level of the kernel, xorg/intel-xorg. After searching both Google, and BSD-related forums, I have not seen anyone reporting the same bug over there, despite the fact that they use Xorg + intel-xorg as well, which makes me think it has something to do with the kernel development on Linux itself... though that is simply an uneducated guess. 

FreeBSD looks awesome, but very daunting at the same time. I did start to download it, but when I was reading the handbook I learned that if you wanted to install additional packages in the beginning, you needed two other installation CDs, unless you wanted to reboot into a working OS, use sysinstall, blah blah, and I could only find one installation CD (apart from the boot only) on their FTP... which I figure isn't exactly a good sign. 

I'm quite comfortable with the command-line, but I am not an expert by any means, and so FreeBSD, like Arch, looks a little bit out of my depth. Not only that, but I'm not a PC hobbyist -- I use these things for work -- and simply can't afford to spend weeks building a system... so perhaps PCBSD is my only option, even though I'm uncomfortable with KDE as the default desktop, and all their custom-built graphical apps and scripts -- my experience with Ubuntu has taught me that such features, while initially making things easier, only makes it more difficult when you need to get down to the nitty gritty of the system, and then find that the core system and whatever custom stuff they've added come into conflict, essentially creating an additional layer of complexity.

Have you tried using an older version of the intel graphics driver? Or maybe even an older version of Xorg?

You can always uninstall KDE from PCBSD and install Gnome.

---

### Post by lykwydchykyn on 2010-05-04
I completely understand the frustration with i845 support, I've been bit by it too.

But -- dare I suggest -- if these are machines you need to accomplish work, and you don't want to spend weeks learning a new OS -- why not just buy a graphics card that is decently supported and get on with life?

That, plus a switch to debian, would probably go a long way towards addressing the issues you mention with a minimum of re-education.

Not that there's anything wrong with learning BSD, but you keep saying you need to make a quick and seamless transition.

---

### Post by swoll1980 on 2010-05-04
Grab a pcBSD iso, and see if it works with your hardware. It has a live cd environment like Ubuntu, so it should at least give you an indication of how much playing around you will have to do. BSD is no where near as far along on hardware support as Linux is, so the chances you may run into some kind of show stopper is increased significantly, but if it works for you then great. BSD is a good piece of software. If you want an operating system with rock solid stability Ubuntu isn't the best choice. Go with Debian, or Red Hat.

---

### Post by purgatori on 2010-05-04
> Have you tried using an older version of the intel graphics driver? Or maybe even an older version of Xorg?

Yep, I went back to the Jaunty driver, and while it seemed to decrease the frequency of crashes for a little while, they soon came back with a vengeance. I haven't tried an older version of X because I assumed that would wreak all kinds of dependency havoc. 

> You can always uninstall KDE from PCBSD and install Gnome.

Indeed, or -- in my case -- scrotwm :p It's just that I know some of the specialized tweaking they've done doesn't work outside of KDE... which might actually be a good thing, I dunno.

> On the negative side a lot less software, a little more fiddly and well I preferred my Ubuntu. I'm sure you can set up PCBSD or FreeBSD with another desktop, but I wondering if something like Crunchbag would do what you want with less of a learning curve?

Isn't Crunchbang based on Ubuntu? My Ubuntu system is already extremely stripped down, so that's not really the issue -- the problem is that X keeps crashing on my hardware, and this seems to be a problem for people with the same hardware regardless of which flavor of Linux they happen to be using -- although it does seem to be something that was introduced with newer versions of kernel/x/drivers. 

> Note that BSD distros uses Xorg, GNOME and KDE too.
If your problems are UI based then they won't go away.

I know, but I'm not seeing the same issue reported on their buglists/forums/etc. so I'm *hoping* that means that it's not an issue in BSD land.

> You don't have to use ports to compile everything, there's binary packages available that you can install through pkg_add. It's all in the handbook

That may be, but I'd still have to build my system from the 'ground up', more or less, which is something that I'm not accustomed to as a Ubuntu user, so it would probably take quite awhile until I had my system setup the way I wanted it... whereas with Ubuntu is was just a matter of removing a lot of stuff that I didn't want (Gnome, GDM, etc.), and installing scrotwm, zsh, etc.

> But -- dare I suggest -- if these are machines you need to accomplish work, and you don't want to spend weeks learning a new OS -- why not just buy a graphics card that is decently supported and get on with life?

Because I'm even worse with hardware than I am with software. This is an old maching (IBM Netvisa), and I have no idea if it would even be compatible with most of the graphics cards available now.

> Grab a pcBSD iso, and see if it works with your hardware. It has a live cd environment like Ubuntu, so it should at least give you an indication of how much playing around you will have to do. BSD is no where near as far along on hardware support as Linux is, so the chances you may run into some kind of show stopper is increased significantly, but if it works for you then great. BSD is a good piece of software. If you want an operating system with rock solid stability Ubuntu isn't the best choice. Go with Debian, or Red Hat.

That's what I ended up doing :) It ran fine for awhile, albeit extremely slowly (which I assume was due to my limited RAM), and then it crashed altogether with a bunch of screen corruption blanketing the screen that required me to reboot.... If this is an alternate manifestation of the xorg crashing/freezing bug, then this is not a good sign :(

Thanks for the suggestions everyone! Once I've backed up my data, I think that I'll probably proceed with installing PCBSD and hope for the best. If that doesn't work out, then the next stop, unfortunately, is Windows :(

---

### Post by lykwydchykyn on 2010-05-04
> **purgatori said:**
> 
Because I'm even worse with hardware than I am with software. This is an old maching (IBM Netvisa), and I have no idea if it would even be compatible with most of the graphics cards available now.

Thanks for the suggestions everyone! Once I've backed up my data, I think that I'll probably proceed with installing PCBSD and hope for the best. If that doesn't work out, then the next stop, unfortunately, is Windows :(

Well, you can do what you want; but since you seem to be suggesting you are unhappy with the prospect of Windows, if BSD doesn't work out I suggest you post the exact model of the machine in question.  Undoubtedly those of us with some hardware knowledge can suggest an inexpensive video card that will be more satisfactory.

---

### Post by purgatori on 2010-05-04
> **lykwydchykyn said:**
> Well, you can do what you want; but since you seem to be suggesting you are unhappy with the prospect of Windows, if BSD doesn't work out I suggest you post the exact model of the machine in question.  Undoubtedly those of us with some hardware knowledge can suggest an inexpensive video card that will be more satisfactory.

It's an IBM NetVista 8304-LAK (Intel Pentium 4 2.66GHz, 512MB, 82845g). 

Ironically, I thought that buying an old machine like this would mean that hardware support in Linux would be better, given that all the components have been around for such a long time :lolflag:

---

### Post by Irihapeti on 2010-05-04
> **purgatori said:**
> It's an IBM NetVista 8304-LAK (Intel Pentium 4 2.66GHz, 512MB, 82845g). 

Ironically, I thought that buying an old machine like this would mean that hardware support in Linux would be better, given that all the components have been around for such a long time :lolflag:

Same thoughts here.

As for buying compatible hardware, there's no guarantee that it will still be compatible next release.

---

### Post by kmsalex on 2010-05-04
just throwing a suggestion out there I've been having surprisingly good results with 
Lubuntu 10.04 on a dell latitude cpi (from 1998  pII 257mhz  128mb ram 2mb video.
I don't know if the hardware support is any better but the system resource usage definitely is.

---

### Post by Ibidem on 2010-05-04
Be aware that Xorg is cross platform.  In other words, if the graphics drivers on Linux have issues, you're talking about moving over to a different OS that has the exact same drivers.
The only difference in drivers is over time, unless you switch from Xorg to Xf86 or start using generic drivers (UVESA, VESA, fbdev, or vga).
RHEL5 is a significant ways back (2007-2008, with some updates), and RHEL 4 & 3 are ancient history.

NOTE: Issues with i845 graphics on BSD--
[http://www.mavetju.org/mail/view_message.php?list=freebsd-i386&id=2890939](http://www.mavetju.org/mail/view_message.php?list=freebsd-i386&id=2890939)
[http://lists.freebsd.org/pipermail/freebsd-current/2009-April/006380.html](http://lists.freebsd.org/pipermail/freebsd-current/2009-April/006380.html)

Looks like FreeBSD has its share of issues...

---

### Post by purgatori on 2010-05-05
> **Ibidem said:**
> Be aware that Xorg is cross platform.  In other words, if the graphics drivers on Linux have issues, you're talking about moving over to a different OS that has the exact same drivers.
The only difference in drivers is over time, unless you switch from Xorg to Xf86 or start using generic drivers (UVESA, VESA, fbdev, or vga).
RHEL5 is a significant ways back (2007-2008, with some updates), and RHEL 4 & 3 are ancient history.

NOTE: Issues with i845 graphics on BSD--
[http://www.mavetju.org/mail/view_message.php?list=freebsd-i386&id=2890939](http://www.mavetju.org/mail/view_message.php?list=freebsd-i386&id=2890939)
[http://lists.freebsd.org/pipermail/freebsd-current/2009-April/006380.html](http://lists.freebsd.org/pipermail/freebsd-current/2009-April/006380.html)

Looks like FreeBSD has its share of issues...

That's what I feared :( But wouldn't the kernel also be a factor?

Also, I've tried some of the generic drives: vesa won't go above 640x480 even when I supply the horizontal scan and vertical refresh frequencies for my monitor, X crashes with fbdev, and I didn't even know there was a 'vga' and 'vesa' option. Also, how would one go about use xfree86 instead of xorg?

---

### Post by Dixon Bainbridge on 2010-05-05
Slackware. The original and the best.

---

### Post by robvas on 2010-05-05
You can get a FreeBSD system up and running with Gnome, wireless and everything fairly quickly. It's a little different but very capable. If you want more of a challenge, use OpenBSD. It will take you back to the old days of Linux when you had to know what you were doing and we didn't have the great graphical installers and hardware detection like in Ubuntu!

I would say that the most challenging part is system setup and disk setup, especially in OpenBSD. Both have documentation that will explain everything, but if you don't get it setup on right on your first try, don't be surprised.

---

### Post by purgatori on 2010-05-05
Well, I took the coward's way out and installed PCBSD. I noticed, during the installation process, that there was an option to install FreeBSD proper, so I might try that later, after I have become acclimatized. 

I must say that the installation went very smoothly indeed, and I didn't encounter any hiccups -- major or minor. The only thing that didn't work when I loaded up the desktop (KDE >.<) was the sound, but there was a patch ready and waiting to be downloaded to fix a 'mute' bug in kmix (or something of the sort), which resolved the problem straight away. 

Best of all, X is no longer freezing or crashing at all, even when I subject it to the same conditions which would usually trigger a crash under Ubuntu: i.e. switching between tabs/desktops, loading up a new GUI application, etc. when the system is under a fairly heavy load. Even if the problem does happen to reappear, vesa seems to work quite well @ 1024x768, whereas in Ubuntu I got a weird/distorted display that would not exceed 640x480. 

There are a few drawbacks though. The PCBSD knowledge-base/handbook seems to be out-of-date, and things aren't where the documentation says they should be. As a result, I'm having a tough time installing things from ports, because when I follow the instructions and try to execute 'runports', I get a command not found error. No biggie though, as KDE4 is usable enough... for now.. .and I'm sure that I'll figure these sorts of things out eventually. Besides, all I really need to do is install scrotwm, texlive, rxvt-unicode, zsh, etc. and I'll truly be back in business :)

---

### Post by lykwydchykyn on 2010-05-05
> **purgatori said:**
> It's an IBM NetVista 8304-LAK (Intel Pentium 4 2.66GHz, 512MB, 82845g). 

Looking here: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-42919](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-42919)

Some models apparently have a 4x AGP slot, though IBM isn't clear on which models that is.  My suggestion is to pop the case open and see if the slot closer to the processor is positioned differently than the others (it'd be further back from the back of the case).  If so, you have an AGP slot.  If not, then you don't and probably are out of luck upgrading the video.

You should be ok with anything on this page as long as it says 4x/8x:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609639&name=AGP%204X%2f8X](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609639&name=AGP%204X%2f8X)

Though you might want to individually check to see if anyone has experience with the particular card before purchasing.  


> 
Ironically, I thought that buying an old machine like this would mean that hardware support in Linux would be better, given that all the components have been around for such a long time :lolflag:

Most of the time you'd be right.  The i845 has been a notorious exception to the rule.  I've run Linux on numerous intel chipsets, and most of the time it runs well and I even get 3d acceleration with no problem.  I don't know what happened to the i845 driver, but it sure stinks these days.

Come on, Intel!

---

### Post by Pogeymanz on 2010-05-05
> **purgatori said:**
> Well, I took the coward's way out and installed PCBSD. I noticed, during the installation process, that there was an option to install FreeBSD proper, so I might try that later, after I have become acclimatized. 

I must say that the installation went very smoothly indeed, and I didn't encounter any hiccups -- major or minor. The only thing that didn't work when I loaded up the desktop (KDE >.<) was the sound, but there was a patch ready and waiting to be downloaded to fix a 'mute' bug in kmix (or something of the sort), which resolved the problem straight away. 

Best of all, X is no longer freezing or crashing at all, even when I subject it to the same conditions which would usually trigger a crash under Ubuntu: i.e. switching between tabs/desktops, loading up a new GUI application, etc. when the system is under a fairly heavy load. Even if the problem does happen to reappear, vesa seems to work quite well @ 1024x768, whereas in Ubuntu I got a weird/distorted display that would not exceed 640x480. 

There are a few drawbacks though. The PCBSD knowledge-base/handbook seems to be out-of-date, and things aren't where the documentation says they should be. As a result, I'm having a tough time installing things from ports, because when I follow the instructions and try to execute 'runports', I get a command not found error. No biggie though, as KDE4 is usable enough... for now.. .and I'm sure that I'll figure these sorts of things out eventually. Besides, all I really need to do is install scrotwm, texlive, rxvt-unicode, zsh, etc. and I'll truly be back in business :)

Excellent. I'm relieved to hear that BSD is not giving your hardware a hard time. Ports is something you have to install first from the CD (at least, it is in FreeBSD), so maybe you don't actually have ports installed and that's why the command isn't working?

BSD is really great software. The only reason I'm still using Linux is because Arch is close enough to FreeBSD (has ABS which is like ports) and Linux gets new features faster.

---

### Post by purgatori on 2010-05-05
@lykwydchykyn: Things seem to be running ok so far, but if the system starts misbehaving again, I'll be sure to pop open the case and check as per your instructions. 

@Pogeymanz: When I was going through the installation process, PCBSD presented the option to install various 'components', one of them being 'FreeBSD Ports', which I selected. I also checked to see whether I have anything in /usr/ports, and sure enough, I do... or is that always the case, whether or not you have installed ports?

And yeah, I've gotta say that I'm impressed by BSD so far. I love Linux, and I used to be into all the bleeding edge stuff, but nowadays stability is my main priority, and it seems that BSD has got that covered. I doubt I would have switched to BSD if my hardware hadn't made things unbearable on Linux, but so far, I'm not regretting my decision :) 

Oh, and yes, the documentation regarding the ports system that I read reminded me a lot of the way that both Arch and Gentoo operate.

---

### Post by cascade9 on 2010-05-06
> **lykwydchykyn said:**
> Looking here: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-42919](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-42919)

Some models apparently have a 4x AGP slot, though IBM isn't clear on which models that is.  My suggestion is to pop the case open and see if the slot closer to the processor is positioned differently than the others (it'd be further back from the back of the case).  If so, you have an AGP slot.  If not, then you don't and probably are out of luck upgrading the video.

Even if there is no AGP slot, a PCI card should still work fine. Thats not quite as reliable an indicator as AGP (basicly, if you have an AGP slot, it should work, some motherboards/chipsets/BIOSes have problems with PCI). 

> **lykwydchykyn said:**
> 
You should be ok with anything on this page as long as it says 4x/8x:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609639&name=AGP%204X%2f8X](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609639&name=AGP%204X%2f8X)

Though you might want to individually check to see if anyone has experience with the particular card before purchasing.  

Everything on that newegg page will be AGP 4x/8x. You shouldnt need a AGP 4x/8x card, though, 2x (and in some cases 1x) could work in an AGP 4x slot. I'll actually check this....I've got a 845 chipset machine hanging around, and I'm 90% sure I have some anciant nVidia cards (I might even have a riva somehwere, adn they are mid/late 1990s cards!). 

> **lykwydchykyn said:**
> 
Most of the time you'd be right.  The i845 has been a notorious exception to the rule.  I've run Linux on numerous intel chipsets, and most of the time it runs well and I even get 3d acceleration with no problem.  I don't know what happened to the i845 driver, but it sure stinks these days.

Come on, Intel!

i845 was always a problem child chipset. IMO anyway. I'm going to have to check i845 video, and see if I can get problems. All my i845 chipset computers have a video card installed...seeing how I seem to always have a few of them hanging around, why use that awful intel video if I dont have to? But it could be interesting to check it, I have to do some work on a i845 machine in the next day or three anyway.

---

### Post by lykwydchykyn on 2010-05-06
> **cascade9 said:**
> 
Everything on that newegg page will be AGP 4x/8x. You shouldnt need a AGP 4x/8x card, though, 2x (and in some cases 1x) could work in an AGP 4x slot. I'll actually check this....I've got a 845 chipset machine hanging around, and I'm 90% sure I have some anciant nVidia cards (I might even have a riva somehwere, adn they are mid/late 1990s cards!). 

Absolutely.  I just had the impression that purgatori didn't have a lot of spare video cards around, and didn't want to muck around too much on this.  Just trying to provide a quick and simple solution.

> 
i845 was always a problem child chipset. IMO anyway. I'm going to have to check i845 video, and see if I can get problems. All my i845 chipset computers have a video card installed...seeing how I seem to always have a few of them hanging around, why use that awful intel video if I dont have to? But it could be interesting to check it, I have to do some work on a i845 machine in the next day or three anyway.

At work, I'm awash in spare i845 machines that have been decommissioned from some purpose or another.  I generally use these as test machines to stage various project, and if memory serves a few years ago I could get 3D acceleration, compiz, and generally decent performance out of them.  That may have been in the i810 driver days, before the new intel driver.

Or I could be wrong, memory gets hazy after a while...

---

### Post by DeadSuperHero on 2010-05-07
Bit of a self-plug here, but I did a writeup for installing FreeBSD not too long ago. I figure it'd be a very educational experience for you.

[http://writerofthings.blogspot.com/2010/04/so-you-want-to-run-freebsd.html](http://writerofthings.blogspot.com/2010/04/so-you-want-to-run-freebsd.html)

---

### Post by Xanavi on 2010-05-07
The Intel 845 was gross when it was new. I have always had driver and no 32bit support problems with the few desktops that I had with it, Windows OR Linux.

I don't understand the obsession with running the old hardware. More efficient hardware can be had for cheaper than cheap. $5/$10?

:redface:

---

### Post by purgatori on 2010-05-07
> **DeadSuperHero said:**
> Bit of a self-plug here, but I did a writeup for installing FreeBSD not too long ago. I figure it'd be a very educational experience for you.

[http://writerofthings.blogspot.com/2010/04/so-you-want-to-run-freebsd.html](http://writerofthings.blogspot.com/2010/04/so-you-want-to-run-freebsd.html)

Thanks, that was a very informative read :) PCBSD was very much a breeze to install, but the selection of pre-installed packages and desktop environment weren't really what I was after, so I'm having to learn more about Free/BSD itself in order to setup my system the way I want it, and documents like your own are quite helpful toward that end.

---

### Post by jonnny_j22 on 2010-05-11
I have to agree with what others have said, in your instance I would say a different distro sounds more like your best bet. If you are considering pcbsd, I think ultimately you will be let down as like ubuntu, this variant aims itself at making the platform more accessible to new users and it sounds as though this is where you have run into difficulties with ubuntu. If you are looking at a bsd switch, you may wish to consider netbsd as this is very low system requirements for older systems.

I run pcbsd as well as several linux disrtos and windows. You need to consider what you want from an OS - now that it's all set up i find that my linux and bsd are pretty much the same becuase I end up using all the same programs with the  same desktop as half my distros, there's just extra code to remember. bsd is more of a pain to set up and i wouldn't say at present it's particularly worth it - you have to bare in mind that the community (the main reason i use ubuntu as my primary desktop) Can be quite a pain for the beginner. This is nothing against them, It's not really any different to linux 12 years ago; you'd ask a basic question and just be told to go and read something that more often than not was a bit too complicated to understand. This will change as the likes of pcbsd make the system more popular with newbies, but at present I would say is quite a limiting factor.

 You may also want to consider qubes if you want simple reliability and security? it's a xen/linux os designed for stability and security, though you may have to check your hardware compatability first. I think the main thing to remember is that really bsd and linux distros aren't that different when it comes to using them for home computing - i doubt you are going to find something new by making the switch. That is not to say you shouldn't try it out, like i said i currently have 7 different os on my computer because i like the variation, i just think you should also try out many different linux distros people have suggested as i think there are many OS that can answer your question, and you have to take into account the move to bsd does put you into one of the smallest communities for online support.

Hope you find an operating system that works for you!

---

### Post by purgatori on 2010-05-14
> **jonnny_j22 said:**
> I have to agree with what others have said, in your instance I would say a different distro sounds more like your best bet. If you are considering pcbsd, I think ultimately you will be let down as like ubuntu, this variant aims itself at making the platform more accessible to new users and it sounds as though this is where you have run into difficulties with ubuntu. If you are looking at a bsd switch, you may wish to consider netbsd as this is very low system requirements for older systems.

I run pcbsd as well as several linux disrtos and windows. You need to consider what you want from an OS - now that it's all set up i find that my linux and bsd are pretty much the same becuase I end up using all the same programs with the  same desktop as half my distros, there's just extra code to remember. bsd is more of a pain to set up and i wouldn't say at present it's particularly worth it - you have to bare in mind that the community (the main reason i use ubuntu as my primary desktop) Can be quite a pain for the beginner. This is nothing against them, It's not really any different to linux 12 years ago; you'd ask a basic question and just be told to go and read something that more often than not was a bit too complicated to understand. This will change as the likes of pcbsd make the system more popular with newbies, but at present I would say is quite a limiting factor.

 You may also want to consider qubes if you want simple reliability and security? it's a xen/linux os designed for stability and security, though you may have to check your hardware compatability first. I think the main thing to remember is that really bsd and linux distros aren't that different when it comes to using them for home computing - i doubt you are going to find something new by making the switch. That is not to say you shouldn't try it out, like i said i currently have 7 different os on my computer because i like the variation, i just think you should also try out many different linux distros people have suggested as i think there are many OS that can answer your question, and you have to take into account the move to bsd does put you into one of the smallest communities for online support.

Hope you find an operating system that works for you!

Not to be impolite, but, what page did you get up to in your reading? I made the switch to PC-BSD, and it fixed the problem :)

---

### Post by Daisuke_Aramaki on 2010-05-14
> **Pogeymanz said:**
> Excellent. I'm relieved to hear that BSD is not giving your hardware a hard time. **Ports is something you have to install first from the CD (at least, it is in FreeBSD)**, so maybe you don't actually have ports installed and that's why the command isn't working?


Err! Misinformation! Who told you that's the only way to install ports? Ever heard of portsnap?

---

### Post by Daisuke_Aramaki on 2010-05-14
> **C!oud said:**
> That being said I find FreeBSD's sysinstall to be quite dated for such things as ZFS, but in most cases it gets the job done.


Exactly. I wouldn't advise a first time user to bypass sysinstall. Setting the system up with sysinstall is child's play.

Once you are used to it, as C!oud says, you can bypass sysinstall and use the Fixit option to completely configure your base system as you wish. Best way to build the system with zfs.

---

### Post by HermanAB on 2010-05-14
Hmm, whenever I have to use BSD it feels like I discovered the secret of time travel and went back 10 years.  Then I look in the mirror and still see the same gray hair...

Anyhow, when I need something stable, I use Scientific Linux (which is Red Hat without the trademark crap, which keeps the lawyers happy).  Ubuntu is good for fun and games and not so hot for corporate systems where time is money.

---

### Post by purgatori on 2010-05-14
> **HermanAB said:**
> Hmm, whenever I have to use BSD it feels like I discovered the secret of time travel and went back 10 years.  Then I look in the mirror and still see the same gray hair...

Anyhow, when I need something stable, I use Scientific Linux (which is Red Hat without the trademark crap, which keeps the lawyers happy).  Ubuntu is good for fun and games and not so hot for corporate systems where time is money.

What, specifically, contributes to that impression? Personally, unless I started playing around with the terminal, I'd be hard-pressed to differentiate the default desktop in PCBSD and, say, Kubuntu (theming differences aside).

---

