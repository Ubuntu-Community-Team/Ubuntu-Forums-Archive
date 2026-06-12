---
title: "VirtualBox Vs Wine - Process"
date: 2013-03-07
forum: Virtualisation
---

### Post by itrogers on 2013-03-07
I definitely understand the difference between the two, however, what would be a good process to decide what program to run where? Should the first priority be Wine and if that doesn't work use a Virtual Machine?

I want to completely switch over but to Ubuntu but there are a few things I will need: Adobe CS6 / MS Office '13 / and EVE Online (game).

Just looking for any insight and experience from other users. What is the best possible scenario for running a windows program in Ubuntu?

---

### Post by DuckHook on 2013-03-07
I have both running on my boxes and have done so for years. There really is no rule here. It's a matter of personal preference. You will definitely need the VM for CS6 and MSO13. Don't know enough about EVE Online to give any advice. Check with the WINE apps database to determine compatibility. Some people will only run "Platinum" compatibility apps because they don't want to tweak anything at all.

My preference is to run as much in WINE as possible before resorting to Win VMs. The nature of VMs make them much inferior in performance to native apps running on bare metal, and I just prefer to not have to fire up the VM unless absolutely necessary. Others on these forums swear by their VMs and run WINE as little as possible.

Between instability/limitations running in WINE and big performance hit running in a VM, it will be up to you to decide which order you prefer them in.

---

### Post by itrogers on 2013-03-08
Thanks for giving a little insight DuckHook. 
> [COLOR=#000000]My preference is to run as much in WINE as possible before resorting to Win VMs. The nature of VMs make them much inferior in performance to native apps running on bare metal, and I just prefer to not have to fire up the VM unless absolutely necessary. Others on these forums swear by their VMs and run WINE as little as possible.[/COLOR]

This makes sense and I can see where the tradeoff really is. Like you, I think I'll try it in Wine before firing up the VM (which will be necessary for my setup anyhow). Thanks again.

---

### Post by Bucky Ball on 2013-03-08
As mentioned, check WineHQ for compatibility. Wine may be a waste of time and a VM your only solution but if you are going to/needing to use your Win apps a lot I'd probably stick with Windows and dual-boot.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Ubuntu isn't and will never be a drop in replacement for Win, with or without Wine.

---

### Post by itrogers on 2013-03-08
> **Bucky Ball said:**
> As mentioned, check WineHQ for compatibility. Wine may be a waste of time and a VM your only solution but if you are going to/needing to use your Win apps a lot I'd probably stick with Windows and dual-boot.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Ubuntu isn't and will never be a drop in replacement for Win, with or without Wine.

Great point. Perhaps I should first make Ubuntu my **main** OS rather than only and slowly switch if at ever all possible.

---

### Post by Bucky Ball on 2013-03-08
Sounds like a plan. ;)

See what you can and can't do in Ubuntu and play around a bit. Also look for Linux alternatives to Win apps and see what you can come up with. Depending on what features you use in Office you might find OpenOffice or LibreOffice will do just as well. 

Good luck with it and enjoy the learning curve.

---

### Post by PJs Ronin on 2013-03-08
fwiw, I tried Wine a couple of years ago after making a resolution to switch totally to Ubuntu but found that there were some 'graphics problems'... probably more due to my own lack of expertise than anything else.   That led me to Virtualbox and I was blown away at how easy it was to get my Windows requirements up and running. (In my case I needed Windows for a particular game, but linked to a PostgreSQL database on the Ubuntu side.)

Haven't looked back.   I now use the VMs for my games, testing new releases of Ubuntu b4 I migrate to the production side, and testing other Linux distros.   And all of this is neatly wrapped up in VMs that I regularly backup so that crashes/viruses are no longer a prob; reload, rinse, dry and away we go again.

---

### Post by foxmulder881 on 2013-03-09
Whether it's Windows, Linux or Mac OS. I just use and recommend others to use whatever OS suits your needs.

---

### Post by itrogers on 2013-03-10
> **PJs Ronin said:**
> fwiw, I tried Wine a couple of years ago after making a resolution to switch totally to Ubuntu but found that there were some 'graphics problems'... probably more due to my own lack of expertise than anything else.   That led me to Virtualbox and I was blown away at how easy it was to get my Windows requirements up and running. (In my case I needed Windows for a particular game, but linked to a PostgreSQL database on the Ubuntu side.)

Haven't looked back.   I now use the VMs for my games, testing new releases of Ubuntu b4 I migrate to the production side, and testing other Linux distros.   And all of this is neatly wrapped up in VMs that I regularly backup so that crashes/viruses are no longer a prob; reload, rinse, dry and away we go again.

Would love to hear more about this if you can or at least provide some links on some setup guides? Sounds very technical but it sounds like it was well worth it?

---

### Post by Bucky Ball on 2013-03-10
Virtualbox is in the repositories so just install via Synaptics or Software Centre, launch, install Windows as a virtual machine inside your Linux host. That's it.

One thing to remember is that you need to allocate some RAM to each install so if you have 1Gb you probably won't get far as that would be 512Mb for each. Sluggish.

Do a search for Virtualbox and related how-tos. There's stacks of info out there. Good luck.

---

### Post by DuckHook on 2013-03-11
> **PJs Ronin said:**
> fwiw, I tried Wine a couple of years ago


There are a number of very good observations in this post:


> ... probably more due to my own lack of expertise


This is hardly fair to yourself. WINE is notoriously hard to configure and is known to break functionality with updates that then require regression. When we consider what WINE does, it is hardly surprising that it breaks so often. In fact, it is surprising that works as well as it does.


WINE is basically an attempt to reverse-engineer a foreign operating system, map out its internal functions, and duplicate its effects on apps that are just as foreign as the operating system itself so that they will run efficiently, properly and quickly on an operating system for which they were never designed. WINE developers are on record as saying that one of the most difficult aspects of this task is accommodating the thousands of kludges that MS has written into their own OS. In general terms, this means purposefully writing inefficient, loopy and say-what? code that would not logically occur to a programmer trying to achieve an otherwise intended result.


This process can never be exact. WINE can only approximate Windows functionality to a greater or lesser degree and even the approximation varies from app to app depending on what functions and system calls the app uses. This is why most apps require a certain amount of tinkering and configuring to work. WINE developers try to focus on making WINE compatible with the apps that are most "popular" or "critical", but the more complex the app (i.e. the more obscure the functions it uses), the more difficult it is to achieve this compatibility. This challenge is also multiplied by how new the app is. When you factor in Windows updates, service packs and its ever-changing nature, to say nothing of the updates and changes made to the apps as well, the challenges are truly immense. As a non-programmer looking in from the outside, I marvel at how they achieve what they do. Remember, they aren't doing something so simple as re-writing Windows; they are translating Windows functions so that they will run on Linux.


I don't know about you, but given the magnitude and the complexity of the task, I simply expect WINE to be flaky and fussy and finnicky. Yet, I can run whole games on WINE that don't require any adjustment on my part. It's almost magic and, quite aside from the practical utility, I admire the expertise that went into putting together such an amazing product.


> That led me to Virtualbox and I was blown away at how easy it was to get my Windows requirements up and running.


With a little practice, it is amazing how easy it is to use VirtualBox. However, the other VMs are not as easy and require varyingly greater degrees of configuration. I recommend sticking to VirtualBox for new users.


> I now use the VMs for my games, testing new releases of Ubuntu b4 I migrate to the production side, and testing other Linux distros. And all of this is neatly wrapped up in VMs that I regularly backup so that crashes/viruses are no longer a prob; reload, rinse, dry and away we go again.


@OP


As previously mentioned, the biggest drawback with any VM is that you are necessarily nerfing system resources by using them. By creating a "make-believe" computer inside a real computer (which is what a VM is), you have no choice but to sacrifice power, speed and functionality. As only one example, VirtualBox creates a special Vbox videocard for your Windows VM that has significantly reduced functionality from your real videocard. Games that will run smoothly on a bare-metal Windows installation often choke, stutter or even refuse to run in a Windows VM. @PJs Ronin is either running older games that are not too resource-intensive, or else he is running his VMs on hardware with significant horsepower.


If you have the horsepower, your VM experience will likely also be gratifying if you run relatively resource light apps. However, if your HW is middle-of-the-road and more than four or five years old, you will likely find the experience frustrating, especially for games. In no case will bleeding-edge games run well. They require every edge they can get and will often choke even on modern bare metal. The added inefficiency of VM translation, doubled system calls, video downgrading and sandboxing will render such games unplayable. And the same consideration applies to resource-heavy apps like audio/video-editing, 3-D rendering CAD or professional simulation/math-heavy analytics.


To end on an upbeat note, I have tons of fun running both WINE and VMs. I use my VMs exactly as @PJs Ronin does. I have over a dozen different OSes installed on VMs and have more fun than flying monkeys exploring and breaking them. When I do break them, I just roll back to an earlier snapshot and the recovery is completely painless.

Hope you have the same fun and Happy Ubuntuing.

---

### Post by itrogers on 2013-03-11
> [COLOR=#000000]Virtualbox is in the repositories so just install via Synaptics or Software Centre, launch, install Windows as a virtual machine inside your Linux host. That's it.[/COLOR]

[COLOR=#000000]One thing to remember is that you need to allocate some RAM to each install so if you have 1Gb you probably won't get far as that would be 512Mb for each. Sluggish.[/COLOR]

[COLOR=#000000]Do a search for Virtualbox and related how-tos. There's stacks of info out there. Good luck.[/COLOR]

Thanks. I am familiar with the setup. I should have been more specific in my quoting of my last post. [COLOR=#000000]

[/COLOR]> [COLOR=#000000](In my case I needed Windows for a particular game, but linked to a PostgreSQL database on the Ubuntu side.)[/COLOR]

I was hoping that **[COLOR=#000000]PJs Ronin [/COLOR]**[COLOR=#000000]could provide documentation or guide on this which seems interesting.

[/COLOR]> [COLOR=#000000]In no case will bleeding-edge games run well.[/COLOR]
[COLOR=#000000]
I am realizing this is the cold truth. I have found many guides on WINE integration for my particular MMO of choice but as expected they aren't bug free. It seems like Dual Boot will be the main option for now. Until Linux becomes more mainstream and app and game developers (Adobe) provide their software in linux natively....dual boot it is. Thanks to everyone for their experience and feedback.

[/COLOR]

---

### Post by Bucky Ball on 2013-03-11
> **itrogers said:**
>  Until Linux becomes more mainstream and app and game developers (Adobe) provide their software in linux natively....
[/COLOR]

That day may never come. Don't hold breath. ;(

As the regular method of marking threads solved is broken due to upgrade the workaround is to edit the first post, click 'Go Advanced' and change the title prefix to 'Solved'. 

Good luck.

* I have marked it 'Solved' myself.

---

### Post by Kasuko on 2013-03-12
If you have an Nvidia graphics card EVE Online usually works in WINE. I play it fine (Captains Quarters crashes but who uses that feature anyways?)

---

### Post by itrogers on 2013-03-12
> **Kasuko said:**
> If you have an Nvidia graphics card EVE Online usually works in WINE. I play it fine (Captains Quarters crashes but who uses that feature anyways?)
Glad to hear! Agree with you on Captains Quarters (at least for this expansion).

---

### Post by PJs Ronin on 2013-03-13
> **PJs Ronin said:**
> 
[COLOR=#000000]snip ... In my case I needed Windows for a particular game, but linked to a PostgreSQL database on the Ubuntu side...
[/COLOR]
> **itrogers said:**
> Would love to hear more about this if you can or at least provide some links on some setup guides? Sounds very technical but it sounds like it was well worth it?

My 'vice' is online poker and I use a PostgreSQL database managed by a program called PokerTracker4 which does a whole bunch of things to support poker players.   I read somewhere (long time ago) that PostgreSQL started life on Linux/Unix systems and was ported to Windows at a later stage, so Linux is 'home' for PostgreSQL.   Unfortunately, most of the poker client programs are written for Windows with some also being web based java so that leaves Linux high and dry.   The solution was to use Wine/Virtualbox/VMWare to house the poker clients and PokerTracker and Linux to provide grunt for PostgreSQL. The only real issues that need to be addressed for this setup to work are:
[LIST]
[*]the guest network adapter must be set up as a Bridge and not NAT, and
[*]database backup/restore functions are better done with PGAdminIII (Linux side) rather than through PokerTracker's backup/restore.   This is a PostgreSQL limitation, not a PokerTracker limitation.
[/LIST]
Until recently I was doing all this on a Core 2 Duo 32 bit Ubuntu 12.04 with a Win XP Home guest and had no problems running all my poker stuff.   I once tested the system by running 5 poker tables, with PokerTracker providing a complex HUD on each table, and Pandora and some other webby stuff running on the Ubuntu side.   I had no problems except my old brain had difficulty keeping up with 5 tables.   Younger folk talk of running 24 tables simultaneously... good luck to them.

My current system is Ubuntu 12.04LTS, PostgreSQL 9.0, and a Windows 7 Pro VM (all 64 bit) backed by an Intel i7-3770K (not overclocked), 16Gb matched RAM, nVidia GeForce GTX 650 graphics and 2 x 500 GB HD (7200 rpm).   The younger poker fanatics use SSD, big and fast.

Was it worth it?   Yes.   Ubuntu is rock solid and by running Windows in a VM I don't have to worry about viruses/malware (I have no anti-virus progs in the VM and don't run anything other than PokerTracker and the poker clients).  An interesting thing that came out of this was that when I originally set up all the partitions I made a 'data' partition formatted ext4 where I intended PokerTracker to store processed hand histories (text files) not realising that Windows might have difficulty reading an ext4 partition.   Seems Virtualbox handles the conversion nicely as I have had no probs at all.

Setting a system up like mine is not difficult, the devil is in the fine detail, or fine tuning.   The support staff at PokerTracker are brilliant and seem to have a lot of Linux and Mac experience.   Check em out [here]("https://www.pokertracker.com/forums").

---

### Post by heiko_s on 2013-03-14
One option that hasn't been mentioned is using a Xen hypervisor (Xen is similar to VMware, but free and open source). But I don't recommend this to the inexperienced.

The reason why Xen stands apart from all other solutions mentioned here (Wine, VirtualBox, etc.) is a feature called VGA passthrough, which allows the guest OS to take full control of a graphic adapter and thus get native (bare metal) graphics performance. Xen is also very efficient with other tasks such as disk I/O so that in the end you can run Windows in a VM with next to no performance penalty.

This Xen solution (with VGA passthrough) requires specific hardware features, and unless they are all met, it won't work. The basic requirement is IOMMU support called VT-d for Intel CPUs, or AMD-Vi for AMD CPUs. For example, PJs Ronin Intel i7 3770K CPU will be useless, whereas a i7 3770 CPU will be just fine because it supports VT-d.

I've been dual-booting for many years because I needed Adobe Photoshop as well as support for monitor calibration. Wine doesn't support newer releases of Photoshop, and neither Wine nor VirtualBox (or any other VM solution except Xen) support my NEC monitor calibration system. Using Photoshop or similar to work on RAW photo files also benefits from every CPU resource you can throw at it, and VirtualBox is not the most efficient solution and doesn't compare with Xen or KVM in terms of performance.

While dual-boot worked fine, it was a pain in the neck for me. I use Linux for everything except photo processing. So if I wanted to send a few photos via email, I had to reboot into Linux. The OP uses a number of MS Windows based applications (Office, Adobe CS, games) and dual boot might be the best option if for example Ubuntu is only used occasionally, and if there is no need for exchanging data between Windows and Linux applications. In my case I use Linux and Windows 50/50 and I need to exchange data and switch between both in a quick and easy way (without rebooting).

Xen with VGA passthrough solved this problem for me. Since you get native graphics performance under the Windows guest OS, it is also a perfect solution for gamers who keep Windows to be able to play. I've written a "HOW-TO make dual-boot obsolete using XEN VGA passthrough" for Linux Mint, but this should work with little to no modifications for Ubuntu. See: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013").

The OP may also consider to migrate to Ubuntu. Here a few Windows based apps and their Linux equivalents:

MS Office - LibreOffice, Oracle OpenOffice (these two include all except an Outlook equivalent)
MS Outlook - Evolution (also connects to Exchange server), Thunderbird, and more
Adobe Photoshop - Gimp, and/or RAWtherapee and others for RAW photo conversion
Color management - LittleCMS 2, Argyll, and more.

---

### Post by itrogers on 2013-03-14
> **heiko_s said:**
> One option that hasn't been mentioned is using a Xen hypervisor (Xen is similar to VMware, but free and open source). But I don't recommend this to the inexperienced.

The reason why Xen stands apart from all other solutions mentioned here (Wine, VirtualBox, etc.) is a feature called VGA passthrough, which allows the guest OS to take full control of a graphic adapter and thus get native (bare metal) graphics performance. Xen is also very efficient with other tasks such as disk I/O so that in the end you can run Windows in a VM with next to no performance penalty.

This Xen solution (with VGA passthrough) requires specific hardware features, and unless they are all met, it won't work. The basic requirement is IOMMU support called VT-d for Intel CPUs, or AMD-Vi for AMD CPUs. For example, PJs Ronin Intel i7 3770K CPU will be useless, whereas a i7 3770 CPU will be just fine because it supports VT-d.

I've been dual-booting for many years because I needed Adobe Photoshop as well as support for monitor calibration. Wine doesn't support newer releases of Photoshop, and neither Wine nor VirtualBox (or any other VM solution except Xen) support my NEC monitor calibration system. Using Photoshop or similar to work on RAW photo files also benefits from every CPU resource you can throw at it, and VirtualBox is not the most efficient solution and doesn't compare with Xen or KVM in terms of performance.

While dual-boot worked fine, it was a pain in the neck for me. I use Linux for everything except photo processing. So if I wanted to send a few photos via email, I had to reboot into Linux. The OP uses a number of MS Windows based applications (Office, Adobe CS, games) and dual boot might be the best option if for example Ubuntu is only used occasionally, and if there is no need for exchanging data between Windows and Linux applications. In my case I use Linux and Windows 50/50 and I need to exchange data and switch between both in a quick and easy way (without rebooting).

Xen with VGA passthrough solved this problem for me. Since you get native graphics performance under the Windows guest OS, it is also a perfect solution for gamers who keep Windows to be able to play. I've written a "HOW-TO make dual-boot obsolete using XEN VGA passthrough" for Linux Mint, but this should work with little to no modifications for Ubuntu. See: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013](http://forums.linuxmint.com/viewtopic.php?f=42&t=112013).

The OP may also consider to migrate to Ubuntu. Here a few Windows based apps and their Linux equivalents:

MS Office - LibreOffice, Oracle OpenOffice (these two include all except an Outlook equivalent)
MS Outlook - Evolution (also connects to Exchange server), Thunderbird, and more
Adobe Photoshop - Gimp, and/or RAWtherapee and others for RAW photo conversion
Color management - LittleCMS 2, Argyll, and more.

Thanks a lot for the input and the guide you wrote. I'll have to do more research on Xen and my hardware to make sure I'm compatible on all machines involved. If the compatibility is there it can't hurt to test it out. I agree with you that a dual boot may be the best way to go.

---

### Post by DuckHook on 2013-03-14
Your How-To is awesome! Very much appreciated.

I've been wanting to fire up a XEN hypervisor for exactly the reasons you state, but the complexity of the install has always defeated me. Will try again with your How-To in hand. Have bookmarked it in my browser. Thanks for the public service.

---

### Post by heiko_s on 2013-05-04
> **itrogers said:**
> Thanks a lot for the input and the guide you wrote. I'll have to do more research on Xen and my hardware to make sure I'm compatible on all machines involved. If the compatibility is there it can't hurt to test it out. I agree with you that a dual boot may be the best way to go.

You definitely need to check your hardware before you try Xen, or kvm. VGA passthrough has seen some progress recently and I've seen reports of people having passed through some Nvidia cards. See [http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19875808]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19875808") for some more on kvm with Nvidia. If you go up some posts you'll find a how-to for kvm, but it may be a little more challenging (kernel compilation, etc.).

It's been a little challenging for me, but it was totally worth it. Right now my Windows VM is running some data backup while I'm writing this from Linux. Yesterday I screwed up my Windows VM with some bloody Samsung printer drivers that don't work and when I wanted to remove them they left all sorts of garbage behind. I reinstalled the entire Windows partition (72GB) from a gzipped backup in 6:24 minutes.

---

### Post by heiko_s on 2013-05-04
> **DuckHook said:**
> Your How-To is awesome! Very much appreciated.

I've been wanting to fire up a XEN hypervisor for exactly the reasons you state, but the complexity of the install has always defeated me. Will try again with your How-To in hand. Have bookmarked it in my browser. Thanks for the public service.

You are most welcome.

The most challenging part - I found - was to get the right hardware (or check that the hardware meets the requirements). But documentation is improving, so is support (at least with some vendors).

I hope more people can enjoy this solution. And with a larger audience there will be better documentation and support.

---

