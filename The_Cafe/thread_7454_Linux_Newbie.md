---
title: "Linux Newbie"
date: 2004-12-07
forum: The Cafe
---

### Post by battlepanda on 2004-12-07
Hi guys. I'd just like to say up front that I'm NOT the kind of person who'd usually think about installing a Linux-based OS. While I'm not a technophobe, my understanding of computers is limited. So why am I here?

Well, recently I borrowed my sister's Windows XP disk to install on my desktop. It wasn't until after the installation that I realized that those *&^%s at Microsoft required me to activate XP in order to keep using it as a way of preventing the same copy of software from being used in two machines. I inherited my PC from my brother who moved overseas, and as he have no idea where his Windows 98 disks got to, I couldn't even go back to Windows 98. Oops. In 29 days I'll have no OS.

I'd hate to have to shell out for a new copy of XP as this desktop is just a second computer I don't often use (I have an apple iBook that I'm pretty much in love with.) On the other hand, what I do have is plenty of free time (currently unemployed). So I rooted around a little on the web and found Ubuntu recommended as an user-friendly OS. I like the philosophy as much as I like the price. 

The question is, am I biting off more than I can chew? I looked around the FAQs and the terms "debian", "gnome" etc. etc. are foreign to me. I also get the impression that things I take for like installing new hardware and burning audio CDs are going to become a hairy adventure every time. 

What I want to use this computer for is very basic -- web surfing (linksys wusb11v2.5) , word processing, printing (HP Photosmart P1100) and syncing with my Palm IIIxe. Is Ubuntu right for me? If not, what would you do in my situation?

Thanks

---

### Post by arekmenner on 2004-12-07
I think that sounds good, all except the linksys.

---

### Post by jdong on 2004-12-07
Hmm... Every task you mentioned is  accomplishable, and with a **little bit of extra work**, you can probably get that WUSB card to work.


Linux is VERY simple to use -- ask us anything you want!

Post separate threads if you need help setting up hardware!

---

### Post by arctic on 2004-12-07
hi there.

well, first of all, ubuntu can be used by you. just set your box to boot from cd, enter the ubuntu cd and off you go. what you need to know, when using the installation-tool is partitioning in linux. you will be asked to set up some partitions for ubuntu, so no problem there: simply create one partition in e.g. ext3 format, make it bootable and define it as "/", then create another partition as /swap (double size of your ram) and one partition in e.g. ext3 for your /home folder (this where your personal data will be stored). when asked about the bootmanager, install it to the mbr of your first harddrive (or alternatively on a floppy-disk if you really want that).

and: DO NOT FORGET YOUR PASSWORDS. many first time users do not care about passwords and wonder later, why they can not log into their box :D

in case you want to try ubuntu (or any other linux distribution) before finally installing it on your box, you can use live cds like ubuntu-live or knoppix for getting an idea of how linux works.

gnome is a desktop manager = the same stuff you know from windows. the desktop (with icons if you want) and the link to all applications. browse for some screenshots of gnome and you will see what i mean. while gnome and any other window-manager for linux (like kde, xfce4,...) are basically similar to a windows-desktop, they are more powerful. just explore the linux-world and you will see that there are possibilities in linux you never thought of as being possible.

for distributions, check also [www.distrowatch.com](www.distrowatch.com). there you will find many many alternatives to ubuntu if that does not satisfy your needs. for newbies to linux, the best starting distributions are imho mandrake, suse and ubuntu.

p.s.: you can always reinstall your winxp after 30 days but that is rather annoying :P

---

### Post by battlepanda on 2004-12-07
Argh! Just got that linksys adapter too. Oh well. Only $25 from eBay. And if I can't get it to work I guess I can always sell it on eBay again too.

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=battlepanda]Hi guys. I'd just like to say up front that I'm NOT the kind of person who'd usually think about installing a Linux-based OS. While I'm not a technophobe, my understanding of computers is limited. So why am I here?

Well, recently I borrowed my sister's Windows XP disk to install on my desktop. It wasn't until after the installation that I realized that those *&^%s at Microsoft required me to activate XP in order to keep using it as a way of preventing the same copy of software from being used in two machines. I inherited my PC from my brother who moved overseas, and as he have no idea where his Windows 98 disks got to, I couldn't even go back to Windows 98. Oops. In 29 days I'll have no OS.

I'd hate to have to shell out for a new copy of XP as this desktop is just a second computer I don't often use (I have an apple iBook that I'm pretty much in love with.) On the other hand, what I do have is plenty of free time (currently unemployed). So I rooted around a little on the web and found Ubuntu recommended as an user-friendly OS. I like the philosophy as much as I like the price. 

The question is, am I biting off more than I can chew? I looked around the FAQs and the terms "debian", "gnome" etc. etc. are foreign to me. I also get the impression that things I take for like installing new hardware and burning audio CDs are going to become a hairy adventure every time. 

What I want to use this computer for is very basic -- web surfing (linksys wusb11v2.5) , word processing, printing (HP Photosmart P1100) and syncing with my Palm IIIxe. Is Ubuntu right for me? If not, what would you do in my situation?

Thanks[/QUOTE]


Go for it mate, we'll try to help. If you have free time, why not learn something new? For the record: debian is the OS Ubuntu is based on. Gnome is the desktop environment Ubuntu uses.

---

### Post by jdong on 2004-12-07
[QUOTE=battlepanda]Argh! Just got that linksys adapter too. Oh well. Only $25 from eBay. And if I can't get it to work I guess I can always sell it on eBay again too.[/QUOTE]

NOTE: I don't know anything about that adapter! I'm just saying, it's USB AND wireless, twice the chance of incompatibility.
Probably NDiswrapper can handle it, but setting it up could really disgruntle newbies!

---

### Post by battlepanda on 2004-12-07
Well, I have nothing to lose but the annoyance of re-installing Windows XP every 30 days. 

Now I wait for the CDs to arrive...

So if "Debian" is the OS and "Gnome" is the desktop environment, what would Ubuntu be? The "distribution"? But what does that even mean?

---

### Post by jdong on 2004-12-07
[QUOTE=battlepanda]Well, I have nothing to lose but the annoyance of re-installing Windows XP every 30 days. 

Now I wait for the CDs to arrive...

So if "Debian" is the OS and "Gnome" is the desktop environment, what would Ubuntu be? The "distribution"? But what does that even mean?[/QUOTE]

Ubuntu and Debian are both distributions. Ubuntu is a distribution based on another distribution, called Debian. Many other distributions exists -- each has its own set of features, but overall they accomplish the same tasks. Linux is only the 'kernel' of the operating system -- like Windows is only kernel32.dll, ntoskrnl386.exe, user32.dll, and gdi32.dll.


GNOME is a 'desktop environment'. It provides a uniform desktop experience by providing windows with title bars, a taskbar, "start menu" equivalent, filebrowser, and a standard set of programs (like a calculator and such).

The most comparable Windows counterpart to GNOME is explorer.exe, which provides the desktop and taskbar system. GDI32.dll actually provides the title bars, but that's a different story!

---

### Post by battlepanda on 2004-12-07
Cool. Now I won't sound all ignorant by referring to ubuntu as an OS.

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=battlepanda]Well, I have nothing to lose but the annoyance of re-installing Windows XP every 30 days. 

Now I wait for the CDs to arrive...

So if "Debian" is the OS and "Gnome" is the desktop environment, what would Ubuntu be? The "distribution"? But what does that even mean?[/QUOTE]


[Linux Distro](http://en.wikipedia.org/wiki/Linux_distro) 

[Debain](http://en.wikipedia.org/wiki/Debian) 

[Gnome](http://en.wikipedia.org/wiki/GNOME)

---

### Post by BWF89 on 2004-12-07
Hey, I'm BWF89. I don't have Linux yet but I use live CD distros (Linux operating systems you can run off of a CD) and I'm saving up to get a new computer I can install it on...

If you want to know more about Linux here are some of the Linux news sites I often visit:

[Linuxtimes.net](http://linuxtimes.net/) 
[OSNews.com](http://www.osnews.com/topic.php) 

Read the new articles on Open source/free software everyday and you'll know all the terms and get the swing of what's going on with the operating system in no time...

---

### Post by jakeslife on 2004-12-16
Another great resource for *nix information is distrowatch.com. 

I bet in the time it takes you for that copy of Windows to lock up you could learn all you need to know about linux or Ubuntu. Costs less too. Even better than FCKGW'ing it through things. :-P

---

### Post by adbak on 2004-12-16
[http://www.LXer.com](http://www.LXer.com) - My number one site for Linux/FOSS (free & open source software, also known as FLOSS, free, libre, and open source software) news.

---

### Post by Quest-Master on 2004-12-16
I'm using a LinkSys adapter and it was automatically recognized through DHCP. ;)

---

