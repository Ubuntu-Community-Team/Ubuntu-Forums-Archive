---
title: "Generall snap Discussion"
date: 2019-01-27
forum: Ubuntu, Linux and OS Chat
---

### Post by dabsig on 2019-01-27
Hey guys, I wanted to start a genrall discussion about snaps.

What do you guys think about it? What can we expect from the future? Does anyone know exactly how they work and why snaps are so slow?

The information I got is the following and might be outdated and/or wrong, so please don't hesitate to correct me.

Snaps were introduced to have a simple .deb replacement and make it easier for developers do release software for all linux distributions at once, because a snap can be installed on any linux machine and the developer doesn't have to release a package for each distrobution group.
Because of this each snap comes with all its libraries and is compiled at runtime? Wich is why they are so slow? Also if multiple snaps need the same lib, the lib will be duplicated on your system and take unncessary space.

I'm looking forward for the knowledge exchange and thanks in advance for your participitation.

Please excuse my spelling and so on, I'm not a native english speaker.

---

### Post by TheFu on 2019-01-27
Snaps do include all the dependent libraries.  They are not compiled at runtime, unless the language used would normally do that (python, php, perl6, ruby).

They are slower at startup because dependent libraries have to be loaded into RAM from storage. Even if the same library, just a different version, is already loaded into RAM, then another would be as part of the snap.  On systems with limited RAM, this is a huge problem.  

These days, duplicated storage is a fairly minor concern on desktops and servers. 

There are other important aspects to snaps.  They are "constrained" too. This means the libraries and programs inside the snap are limited in what they can and cannot access. We can lock down all networking or access to devices or allow read-only access to selected parts of the OS.

For a more technical discussion, it would be useful to have virtual machine, Linux container and compiled software development knowledge.  Without those backgrounds, we cannot really discuss at a much deeper level.

[https://snapcraft.io/](https://snapcraft.io/) has as much data as is available. Check out the documentation.

---

### Post by oldfred on 2019-01-27
I am not a fan of running snaps for current software in current install.

I potentially see an advantage if you have a very new system and want to run some very old software, or vice-versa, an old install and need one application that is a lot newer. It resolves the potential dependency issues.

Snaps also then have their own update schedule which may be good or not so good.

They also seem to be currently slow in loading.
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341) 
    Use standard calulator .deb, not snap
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)

---

### Post by charlesglowacki on 2019-01-30
Yes, snaps are slow. It appears to be bizarre that applications need to continually refresh the text style reserves instead of simply read what is there. Tragically the composed caches are not snap-explicit, so one snap could compose reserves that another snap could utilize (maybe stimulating bugs in fonctconfig to attempt to escape restriction). 

All things considered, it appears as though this could be added to work area inheritance (due to the non-snap-specifc nature of writing to records that different snaps and session [[COLOR=#000000]write my essay[/COLOR]]("https://writemyessaytoday.net/") applications may utilize) and unity7.

---

### Post by mastablasta on 2019-01-30
so it slows down the whole OS ? or just the application?

nomacs for example apparently abandoned PPA and uses snap for newer versions. not usually an issue. however, their stable version on LTS seems to have a major issue in slowing down the whole OS rather than being a "snappy"/fast app it used to be for watching photos and doing some minor editing on them.

---

### Post by TheFu on 2019-01-30
I've been removing snap-everything from my systems. When I saw they were pushing calc out in a snap, which seemed ill-advised, I decided someone was being overzealous about snaps compared to my needs.

I hate how snaps use loop mounts and pollute the output from df.
I hate how early versions broke apps that needed external libraries to be useful like VLC.
I like the idea of snaps being available, for needs like oldfred mentioned.  Really old or really new programs.

A slow, voluntary, rollout would have been much better instead of trying to forced it on everyone.  Feels like the Wayland and Netplan push in 17.10 all over again to me.  Someday I hope systemd is ready for production too. ;)

Snaps aren't ready for my use.

In the mean time, I'll constrain the most dangerous programs using **firejail**.  Sometimes it is a hassle to setup custom settings, like I always want browser downloads to go to /tmp/ not $HOME/Downloads/ and sometimes I start a browser using a tempfs overlay, so nothing will touch the actual file system.  But those are my choices, dependent on the purpose of that browsing session.

---

### Post by maglin2 on 2019-01-30
I use one snap - chromium (in Kubuntu 18.04).
My idea is that it might help maintain as much segregation as possible between the user account and browser (chromium snap) where I do most stuff and the user account and browser (firefox from repo) where I only do sensitive stuff.
Other than on first starting it up I don't notice chromium snap being much slower than firejail chromium was when I used that approach.
I am pondering extending the concept and using flatpak firefox in place of firefox from repo (edit - scrap that idea - there isn't a firefox flatpak (except Nightly or DevEdition)). 
I have little idea if chromium snap really adds much to security though.

---

### Post by Tadaen_Sylvermane on 2019-01-31
All I see when I think about Snaps / Flatpack / Appimage is Windows. The biggest selling point for Linux to me is efficiency. Shared libraries are the big point of this for me. Why load 5 different versions of a given library into memory when you can load just one. And the only explanation is laziness by developers imo not wanting to keep their software current and relying on old stuff that has holes. I'm reminded of the ssl bug awhile back, Heartbleed I think? It was fixed on Linux by patching a single library and every single program that relied on that library was fixed. I'd bet anything there is plenty of Windows software floating around for download that still is not fixed. I also like the unity it provides. Makes maintaining things easier. Makes a system simpler.

The only positive thing I see from them is the ease of bringing big name software to the Linux ecosystem.

---

### Post by mastablasta on 2019-02-01
bu stable OS means same often old packages. with PPA one got arround that but PPA could cause other issues. with SNAP those issue were addressed. if i understand correctly the separation of snap from OS provides security.

windows was patched via security patch. libraries were not the issue there. on the other hand i can run games from 2003 or 2007 on windows while on linux some are now forever lost on the internet. dev stopped, new libs no longer support them... just look at the software center so many are gone now.

then playdeb went out and even more apps and games got lost or got unsupported.

---

### Post by leed-f on 2019-02-05
Im actually shocked how useless Snaps are, as they are ruining my whole desktop experience. While I used to have my Windows Dual-Boot only for emergencies, today I find myself rebooting into windows more and more, simply because many things don't work anymore with snaps. 

Chromium won't let me save to my NTFS drives, it can only save to the ubuntu user folder
Handbrake cannot read optical drives, cannot read from NTFS drives, cannot read network drives, can't really do anything
Gimp Snap refuses to accept new data from the clipboard. Only after a restart this seems to work once. 

When I first read about how snaps are sandboxed, I didn't expect them to also Sandbox the user. It seems like a bad joke. 

And for some reason my Chromium Icon keeps dissapearing from the quicklaunch bar. I assume this has something to do with chromiums auto update

---

