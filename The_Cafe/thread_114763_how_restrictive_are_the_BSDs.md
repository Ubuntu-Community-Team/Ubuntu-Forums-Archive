---
title: "how restrictive are the BSDs?"
date: 2006-01-09
forum: The Cafe
---

### Post by fuscia on 2006-01-09
compared to linux, does one have to go through more gauntlets in order to make changes? if so, at what level, or is it everywhere?
as i understand it, the BSDs are more restrictive about the types of programs one can use as they must intergrate with the 'system'.

any thoughts on the various versions? 

how different are the commands?

---

### Post by BSDFreak on 2006-01-09
[QUOTE=fuscia]compared to linux, does one have to go through more gauntlets in order to make changes? if so, at what level, or is it everywhere?
as i understand it, the BSDs are more restrictive about the types of programs one can use as they must intergrate with the 'system'.

any thoughts on the various versions? 

how different are the commands?[/QUOTE]

I'd recommend FreeBSD for your desktop.

It differs from Linux in the way that everything is originally allowed so you'll have to secure the box by yourself. IOW it's less restrictive in a security sense, you'll be able to run any Linux program through the compatibility layer but chances are that you'll find what you need in the ports collection. If you have ever used aptitude you'll know how portsman works.

I recommend taking advantage of the excellent documentation at: [http://www.freebsd.org/docs.html](http://www.freebsd.org/docs.html)

Two things to remember, it needs to be on a primary partition (as opposed to a logical partition) and you'll want to have some time on your hands because selecting what you want to install takes a long time in FreeBSD. (don't forget to install Gnome, XFCE or whatever WM you want other than the default KDE)

Once up and running you'll be surprised about how fast it is.

The other flavors are NetBSD and OpenBSD, NetBSD has less supported software (even though any Linux software can be installed and work through the compatibility layer you'll want as much as possible native) but it doesn't differ all that much. OpenBSD is the king when it comes to computer security, if you need a secure box, this is the OS to use, it's high maintnance and you'll need to know what you're doing to use it properly but once it's set up properly there is no system in the world that is more secure.

---

### Post by fuscia on 2006-01-09
thanks for the response, freak. i sure don't need much security (it's just a toy, to me. LOL at someone who breaks into my computer - "looks like they've already been robbed!"). i had never heard about freebsd allowing everything by default. 

when you say it's faster, in what way is it faster? do the apps open more quickly? do the browsers go from site to site more quickly? why is it faster, etc.?

---

### Post by MetalMusicAddict on 2006-01-09
Ive kept an eye on FreeBSD because a friend uses it some. When does it get its facelift based on their [new art]("http://logo-contest.freebsd.org/result/")?

---

### Post by BSDFreak on 2006-01-09
[QUOTE=MetalMusicAddict]Ive kept an eye on FreeBSD because a friend uses it some. When does it get its facelift based on their [new art]("http://logo-contest.freebsd.org/result/")?[/QUOTE]

If you want artwork in FreeBSD, you'll have to download it. It uses the KDE artwork without adding to it, the new logo is just for webpages, backgrounds and such and you'll have to download the images to use them as a background, you'll be in text mode when you start FreeBSD, no bootsplash, no nothing.

While FreeBSD aims for the desktop more than Net and OpenBSD it's still mainly focused on speed and if you ever run it, you'll notice that. It's incredibly fast.

---

### Post by xequence on 2006-01-09
I can tell you this: The installation is considerably harder then ubuntu's. Also, I hate its partition manager, its horrible and confusing in my opinion. (Enter BSDFreak to tell me how awesome it is). I had to partition with ubuntu's partition manager instead.

And when I installed it, no GUI came along with it. I had to work for along time to trying to get it working and it didnt so I gave up...

Not saying FreeBSD is bad or anything, I love it as much as you can without using it, but im just giving my experience. *hopefully* ill get it installed right on my new computer when I get it.

---

### Post by BSDFreak on 2006-01-09
[QUOTE=xequence]I can tell you this: The installation is considerably harder then ubuntu's. Also, I hate its partition manager, its horrible and confusing in my opinion. (Enter BSDFreak to tell me how awesome it is). I had to partition with ubuntu's partition manager instead.[/QUOTE]

You rang?

I don't mind the FDISK at all, in fact it is VERY similar to the cfdisk interface, just move the bar to where you want to create the partition and press c, tell it how large you want the partition to be and you are done. Either way you'll still have to use the label editor. BSD differs from Linux in that if you want a separate /home or /usr, it's usually on the same *partition* but on different labels. Think of it as having a separate /home and /usr as logical partitions on an extended partition, it's still on the same primary partition but on different logical partitions or in BSD "labels".

I absolutely hate the rest of the installation program though, but probably for the opposite reason of why most others dislike it (i dislike Ubuntu/Slackware/winXP installation programs too), i love the Open and NetBSD installation programs which are more straightforward (but will confuse the heck out of any new user who isn't used to it and hasn't read up on it before installing) 

> And when I installed it, no GUI came along with it. I had to work for along time to trying to get it working and it didnt so I gave up...

It's installed in the default installation, if you chose anything other than defaults without knowing what you were doing then i'd say you messed up. You can choose between Gnome, XFCE or KDE, KDE is default.


> Not saying FreeBSD is bad or anything, I love it as much as you can without using it, but im just giving my experience. *hopefully* ill get it installed right on my new computer when I get it.


I recommend reading the handbook before you install if you intend to change any default installation options. (I'd recommend that regardless of which OS you install)

Regardless of what OS you install, make a plan so you know what you want to do before you start your installation, know what you want to install and know how to get it installed, know how you want to use your hard drive and how to use FDISK, remember that even if you screw up, changes aren't written until you commit them, DON'T commit changes before you are sure you got everything right.



Oh, and if you are missing anything or want to change anything that you did during your installation, just type sysinstall to bring up the installation program and you can install what you are missing or change what you did wrong from there.

---

### Post by xequence on 2006-01-09
> You rang?

Im getting so good I know who will reply to my messages and what they will say.

> I don't mind the FDISK at all, in fact it is VERY similar to the cfdisk interface, just move the bar to where you want to create the partition and press c, tell it how large you want the partition to be and you are done. Either way you'll still have to use the label editor. BSD differs from Linux in that if you want a separate /home or /usr, it's usually on the same *partition* but on different labels. Think of it as having a separate /home and /usr as logical partitions on an extended partition, it's still on the same primary partition but on different logical partitions or in BSD "labels".

Heh, I just didnt like the freebsd partitioner at all :P

> It's installed in the default installation, if you chose anything other than defaults without knowing what you were doing then i'd say you messed up. You can choose between Gnome, XFCE or KDE, KDE is default.

I picked the one that to me said it had the most things, and it said it had X. Didnt say anything about any GUI... But after, I did sysinstall to go back to it and installed gnome. But when I did startx all that came up was TWM, and I absolutly despised it :P

---

### Post by franklee on 2006-01-09
An alternative method for those who fear BSD in terms of its complexity is to perhaps consider investigating Slackware as an intermediary OS. Slack allows for only manual installation with manual config of most drivers, adaptors and apps but its a fantastic learning curve.

Got Slack?

---

### Post by BSDFreak on 2006-01-09
> **xequence]Im getting so good I know who will reply to my messages and what they will say.[/QUOTE]

My name kinda gives it away, doesn't it?  said:**
> Heh, I just didnt like the freebsd partitioner at all :P

OK

> I picked the one that to me said it had the most things, and it said it had X. Didnt say anything about any GUI... But after, I did sysinstall to go back to it and installed gnome. But when I did startx all that came up was TWM, and I absolutly despised it :P

You shouldn't have picked anything, you should have gone with the standard install instead. If you installed X you most probably got KDE with it (unless you chose "all" and started deselecting packages).

Which window manager that starts is up to your configuration, it can be system wide or individual, FreeBSD won't screw up your configuration just because you install a new WM, it will go with what you tell it to go with, it defaults to TWM, changing it is easy enough.

OR you can run KDM and use the graphical login just like you do with GDM in Ubuntu.

---

### Post by tseliot on 2006-01-09
[QUOTE=fuscia]when you say it's faster, in what way is it faster? do the apps open more quickly? do the browsers go from site to site more quickly? why is it faster, etc.?[/QUOTE]
It's very fast. I can't use KDE (or GNOME) on my notebook with Linux because it's slow (it has 192mb RAM). When I tried FreeBSD KDE (3.4.2) felt much more responsive (even fast!). Apps open much more quickly. I don't know why though but it's amazing.

The only problem (if we wanted to call it a problem) was that I had to recompile the kernel (it's easier than in Linux) in order to enable the support fo my soundcard. Then I had to create (with a command) and configure my xorg.conf.
If you read the documentation everything will go fine.

There aren't as many apps as in Linux but you can install Linux apps as well. Sometimes you have to compile the applications from source (not only those for Linux) but if you like Gentoo you'll have no problems whatsover (Don't get me wrong I found FreeBSD easier than Gentoo).

---

### Post by Krigl on 2006-01-09
[QUOTE=BSDFreak] Two things have come out of UC Berkeley, LSD and BSD. This is not a coincidence. [/QUOTE]
LSD comes from Switzerland, actually, but as a quote it's nice.

---

### Post by mstlyevil on 2006-01-09
[QUOTE=Krigl]LSD comes from Switzerland, actually, but as a quote it's nice.[/QUOTE]

I think he was referring to the fact that Berkley was the first place in the US that LSD became popular. In fact it probally still is if you listen to some of the crackpots that come from that university.

---

### Post by poofyhairguy on 2006-01-09
I have a question about BSD now that people are here to answer it.

The thing that brought me into Linux (aka "I knew when it was ready for me") was Project Utopia. 

Does BSD have something like this? When I plug my USB Drive into a BSD Gnome does it pop onto the desktop?

I want to try it on an older laptop I have because I hear the suspend and wireless support is great for old stuff...but I HATE manually mounting stuff. I refused to even look at Linux till that happened. 

What does BSD have?

---

### Post by BSDFreak on 2006-01-09
[QUOTE=poofyhairguy]I have a question about BSD now that people are here to answer it.

The thing that brought me into Linux (aka "I knew when it was ready for me") was Project Utopia. 

Does BSD have something like this? When I plug my USB Drive into a BSD Gnome does it pop onto the desktop?

I want to try it on an older laptop I have because I hear the suspend and wireless support is great for old stuff...but I HATE manually mounting stuff. I refused to even look at Linux till that happened. 

What does BSD have?[/QUOTE]

Yes, when you plug in your USB drive it will pop onto the desktop in KDE, automounting usb devices works out of the box in FreeBSD 6 default installation. Overall, hw support in FreeBSD is pretty great, it has worked on anything i've thrown at it yet.

---

### Post by fuscia on 2006-01-09
what about usb wireless adapters? i had a hard enough time getting that done with linux and i hear freebsd doesn't accomodate as many as linux does. (i have a linksys 802.11b - wusb11 v.2.6) i checked out the hardware lists and i got pretty much lost.

---

### Post by Adrian on 2006-01-09
[QUOTE=BSDFreak]Yes, when you plug in your USB drive it will pop onto the desktop in KDE, automounting usb devices works out of the box in FreeBSD 6 default installation. Overall, hw support in FreeBSD is pretty great, it has worked on anything i've thrown at it yet.[/QUOTE]

Can the new versions of Freebsd hibernate (i.e. suspend to disk)?. I never managed to do that last time I tried (Freebsd 5.3).

Also, changing the behavior of the laptop lidswitch would be nice. I tried that too and failed, but that doesn't mean that it doesn't work :)

Edit: I just remembered that the reason why I couldn't "reprogram" the lidswitch was because ACPI didn't work on my laptop. Instead I had to use apm.

---

### Post by BSDFreak on 2006-01-09
[QUOTE=fuscia]what about usb wireless adapters? i had a hard enough time getting that done with linux and i hear freebsd doesn't accomodate as many as linux does. (i have a linksys 802.11b - wusb11 v.2.6) i checked out the hardware lists and i got pretty much lost.[/QUOTE]

You'll need [http://vitsch.net/bsd/atuwi/](http://vitsch.net/bsd/atuwi/) if you don't track current.

---

### Post by BSDFreak on 2006-01-09
[QUOTE=Adrian]Can the new versions of Freebsd hibernate (i.e. suspend to disk)?. I never managed to do that last time I tried (Freebsd 5.3).

Also, changing the behavior of the laptop lidswitch would be nice. I tried that too and failed, but that doesn't mean that it doesn't work :)


Edit: I just remembered that the reason why I couldn't "reprogram" the lidswitch was because ACPI didn't work on my laptop. Instead I had to use apm.[/QUOTE]

It really depends on the laptop, see [http://gerda.univie.ac.at/freebsd-laptops/](http://gerda.univie.ac.at/freebsd-laptops/) for more information.

ACPI support (and APM when enabled in kernel and ACPI disabled) has gotten a lot better with 6.0 and beyond.

---

### Post by poofyhairguy on 2006-01-10
[QUOTE=BSDFreak]Yes, when you plug in your USB drive it will pop onto the desktop in KDE, automounting usb devices works out of the box in FreeBSD 6 default installation. Overall, hw support in FreeBSD is pretty great, it has worked on anything i've thrown at it yet.[/QUOTE]

Thanks for a straight answer. Sounds good.

---

### Post by DaMasta on 2006-01-10
[QUOTE=franklee]An alternative method for those who fear BSD in terms of its complexity is to perhaps consider investigating Slackware as an intermediary OS. Slack allows for only manual installation with manual config of most drivers, adaptors and apps but its a fantastic learning curve.

Got Slack?[/QUOTE]
Yeah, I think my next install will be Arch. Once I piece my new computer together....(been so long since I built one that I had to learn what sata was).

---

### Post by MetalMusicAddict on 2006-01-10
[QUOTE=BSDFreak]Overall, hw support in FreeBSD is pretty great, it has worked on anything i've thrown at it yet.[/QUOTE]
Nice to know. Last time I was playing with that was my main problem. Was many years ago. 4 or so.

---

### Post by rpgcyco on 2006-01-11
BSD has been capturing my interest lately, mainly for the same reason Linux did, something different, so I may try it out sooner or later. I have a spare 40GB laying around here somewhere.

- Rpg Cyco

---

