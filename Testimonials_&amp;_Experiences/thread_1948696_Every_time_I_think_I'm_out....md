---
title: "Every time I think I'm out..."
date: 2012-03-28
forum: Testimonials &amp; Experiences
---

### Post by MBybee on 2012-03-28
They pull me back in!

So as some of you know, I run quite a collection of systems. I'm very platform agnostic, and use my computers for all sorts of stuff.
I also have a background in Unix stretching back to the 80's, so I'm deeply embedded in things like IRIX, AIX, BSD, etc.

Well, I recently had to do some system rebuilds, and decided that I was *absolutely not* going to use either Win7 or Ubuntu. Tired of Win7 for all the usual reasons (and dreading Win8 ) - tired of dealing with Unity or a half-hearted Gnome 3 Shell implementation. I also wanted to seriously lock down my system and secure it pretty effectively. I need things like Truecrypt or an equiv to store customer data, and use it for personal data as well. I also work extensively with VMs, and do a lot of hobby stuff that really is easier with a Win VM around.

So I went and tried all sorts of stuff. Since this is my testimonial, I'll be specific :D

1) OpenBSD - I love it, I use it for firewalls and such... but it has terrible VM support and not very good performance. Since working with VMs is a *huge* part of my job, I worked with it for over a month trying to get Qemu to work. Never did perform better than "ok" on a hugely powerful host. LOVED the startup/shutdown times, the emphasis on security, XFCE, etc. Couldn't get Pidgin-SIPE working to save my life. Unfortunately, OCS is fairly important.

2) FreeBSD - I have more hours into FreeBSD than probably any OS I've ever used, so I was able to get it up and functional the fastest of any of the BSDs I tried. Day and a half to have every little app set up properly. What finally killed this was NTFS-3G. It seems like a small deal, but when you have to share a 1TB external backup drive between half-a-dozen systems ranging from OSX to Windows to RHEL to who-knows-what, NTFS is pretty much the way to go.
Unfortunately, XFCE just wouldn't play nice with it - and while Gnome2 did... every time I'd kick off a large restore/backup on the drive (like moving music or pics), the whole machine would hang and crash. 
This happened enough times that it ended up corrupting the system and I had to re-install anyhow.

On to... the RPM based distros!
3) SuSE - wow, I just wish I had something nice to say about SuSE. I don't, so I'll just mention that I tried it and didn't like any single thing about it :)

4) Fedora - I used to be a big fan of the RedHat desktops, especially pre-Ximian. Fedora Core 6 was once installed on every x86 machine I owned. I tried to get Fedora 16 up and running, and it just *hated* both my desktop and laptop. No idea why. Basic stuff that worked even under OpenBSD didn't work.
It hated my NIC, it didn't like my FW, it wouldn't recognize my WiFi, etc. I even had video issues on my AMD video that was supposed to be supported. 
I could probably have put the time in it to make this work... but it just wasn't getting off on a good foot. It felt like 1997 all over again, feeling totally pumped when you get X to come up.

5) Kororaa - This is a seriously cool distro. I ran it for about a week, and actually sorta liked it, and it even worked pretty well. I seriously considered using it, but I was just not loving some of the environment choices. It seemed sluggish, and there were so many processes running as root it was ridiculous. 
Honestly, I could have given this a better chance, and I probably will next time.

Ok - so back to Debian-based!

6) Debian - Now, I have a love-hate relationship with Debian. It was the first Linux I really liked, waaaaay back when, and I felt the Corel distro of it proved that Linux could be a viable alternative to FreeBSD. Unfortunately, I really stopped agreeing with where the distro was going about Woody era, and now configuring a Debian box is mostly about removing stupid stuff like IceWeasel and putting back more sensible code. It's like Debian has all the "open source" arguments of OpenBSD, but without the focus... and makes no nods to pragmatism for the real world. I was disappointed that I *still* had to fight to get my video card running, and it feels so retro to be stuck in a distro that seems to still be current with RH7.

7) Bodhi - With some regret, I ended up on the Ubuntu spin-offs. I have done my time with Kubuntu, Xubuntu, Ubuntu Studio, etc - I wanted to try something different. Also, I was starting to get short on time. My Win7 machine was approaching 'rebuild' status, and limping along. I was getting disk failures whenever I tried to back it up, and so I didn't really give Bodhi enough time. 
The Enlightenment based desktop is SO nice, and the distro feels really well done.
Unfortunately, I couldn't figure out how to get an actually solid desktop working with it in the 2 days I played with it - so it's been shelved for now.

8 ) Ubuntu 11.10... again. So I'm back. The new guts on my box were instantly recognized by Ubuntu, everything worked flawlessly, and the new Gnome Shell package in the Ubuntu Store accomplished in 15 minutes what I previously had spent days on. Gnome Shell now works VERY well for the Unity haters, and the system was rock solid.
Naturally, I had all the reference I needed in my Ubuntu 11.10 work machine - so I didn't have to look much up. Everything I wanted was basically already handy. I found good hardening guides and was able to get the ports shut down. App Armor was easy to crank into paranoid mode, I was able to break out the partitions and even later resize /var (freaking /var/cache/apt) without breaking a sweat.



So - tl;dr - Ubuntu was the only one that was Fast, Secure, and Easy, check all 3. I will be watching Bodhi and Kororaa with interest... and I hope that the BSD crews get NTFS-3G working properly. It really does matter.

:popcorn:

---

### Post by BertN45 on 2012-03-28
Wait until you see Ubuntu 12.04. Already the Beta is the most robust system I have seen in a long time, say since 8.04. Even the Unity haters will like it. And there are some tweaking facilities now with e.g. My Unity.

---

### Post by MBybee on 2012-03-29
> **BertN45 said:**
> Wait until you see Ubuntu 12.04. Already the Beta is the most robust system I have seen in a long time, say since 8.04. Even the Unity haters will like it. And there are some tweaking facilities now with e.g. My Unity.

I've played with some of the dailies. Could be interesting - looking forward to it.

---

### Post by lancest on 2012-03-29
12.04 is the fastest ever. 
Enjoying the snappy performance and *[COLOR="Red"]three second shutdown*.[/COLOR]

12.04 on 4 machines- rock stable allready. 
(enjoyed tinkering with Optimus laptop too)

Can I stop admiring my system and get back to productivity?
You bet, Ubuntu is my office- cloud or local.

---

### Post by QIII on 2012-03-29
I've been using Precise (Kubuntu) as my primary for quite some time.

I just do thorough backups before updates.  Haven't needed to go back for them yet in the Beta stage.

Very, very stable even considering the odd issue in the Alphas.

(BTW -  get on the stick with Bodhi.  It is really nice.  Mark plans to have an updated version based on 12.04 within a couple of months of the Ubuntu release.  Unfortunately, it looks like a reinstall rather than a straight upgrade.)

---

### Post by MBybee on 2012-03-29
> **QIII said:**
> I've been using Precise (Kubuntu) as my primary for quite some time.

I just do thorough backups before updates.  Haven't needed to go back for them yet in the Beta stage.

Very, very stable even considering the odd issue in the Alphas.

(BTW -  get on the stick with Bodhi.  It is really nice.  Mark plans to have an updated version based on 12.04 within a couple of months of the Ubuntu release.  Unfortunately, it looks like a reinstall rather than a straight upgrade.)

Bodhi is seriously cool. I have always liked enlightenment (despite the insanely long dev cycle), and an Ubuntu-based one seems like a great pairing.

I'll probably jump on the 12.04 based version :D

---

