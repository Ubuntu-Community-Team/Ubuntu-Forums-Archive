---
title: "VMWare Fusion in all its glory"
date: 2007-08-11
forum: The Cafe
---

### Post by sefs on 2007-08-11
[http://blogs.vmware.com/vmtn/2007/08/top-10-things-y.html](http://blogs.vmware.com/vmtn/2007/08/top-10-things-y.html)

This blurs the borders between OS's.  The wow really start now.

---

### Post by tigerpants on 2007-08-11
I guess this sort of thing is useful for those that *just have to have a window app* but how many people is that? Filemaker, photoshop, quark etc all run natively on OSX anyway, as do many other pro apps - what is there that windows has that non-windows users really need? Office? *shudders* Outlook? *shudders* IE *shudders*? The alternatives are so much better. Or am I missing the point? If you positely have to VM loads of apps anyway, why not just have a native install anyway?

---

### Post by racoq on 2007-08-11
> **tigerpants said:**
>  If you positely have to VM loads of apps anyway, why not just have a native install anyway?

Because you can use windows applications, along with mac applictatios without rebooting.

Whats the hassle of that? Thats an handy feature. That sounds coming from someone who doesn't understand the potential of virtual machines.

---

### Post by darksidedude on 2007-08-11
virtual machines are clumsy, (there I said it) i had a real server running vmware, I would never do it again, they are usefull I guess but crossover would be better
( yes there is a mac vers) and trans games is working on CIDER so there is really no point as I see it, why emulate a whole computer for 1 or 2 programs?

---

### Post by racoq on 2007-08-11
> **darksidedude said:**
> virtual machines are clumsy, (there I said it) i had a real server running vmware, I would never do it again, they are usefull I guess but crossover would be better
( yes there is a mac vers) and trans games is working on CIDER so there is really no point as I see it, why emulate a whole computer for 1 or 2 programs?

Virtual machines aren't clumsy at all, and you'll never now if those 1 or 2 programs doesn't become 5 or 10 applications. But why would you need vmware for a server? Virtual machines are more useful to end users like you and me, that need to a certain OS for certain tasks, like programming, multimedia authoring, CAD, etc...

And it those tasks can't be reproduced in your daily used OS, VM are very handy, because you can run those withou having to reboot as i have said.

---

### Post by starcraft.man on 2007-08-11
> **sefs said:**
> [http://blogs.vmware.com/vmtn/2007/08/top-10-things-y.html](http://blogs.vmware.com/vmtn/2007/08/top-10-things-y.html)

This blurs the borders between OS's.  The wow really start now.

Correct me if I'm wrong but Parallels 3.0 been out before Fusion went official release and has/had most of these features (except 64 bit support I believe). Anyway, doesn't matter... I don't think Windows/Linux (as host) will be seeing these features for a long while if ever from either. I know Parallels doesn't care, they all but abandoned their Windows/Linux workstation at version 2.2. And somehow I just don't see VMware that interested...

Oh well, I guess the community will have to do it on it's own.

---

### Post by tigerpants on 2007-08-11
> **racoq said:**
> Because you can use windows applications, along with mac applictatios without rebooting.

Whats the hassle of that? Thats an handy feature. That sounds coming from someone who doesn't understand the potential of virtual machines.

I understand VM machines perfectly. I just dont see the point of them. To me, they are for ex-windows users that cant quite make the break.

---

### Post by popch on 2007-08-11
There are some areas where VMs are immensely useful, and I actively support those solutions in my work.
[LIST=1]
[*]We have standardized our fleet of 400 clients; all do Windows XP :oops: and a standardized set of applications. They are managed with - among others - automated software distribution. Applications which are used on more than four seats are installable as options. There remains a smallish number of users with unusual demands such as applications which are not compatible with the OS or some APIs in our standardized environment. VM - presto - working solution with minimum support overhead. Give the user some additional RAM and a second monitor, and he is reasonably happy. We're not responsible for a more than reasonable happiness.

[*]On those standardised clients we have to use some applications which are supplied and managed - even remotely supported - by another department which is also another Windows domain and which requires another version as MS Office than the one we use in our department. Running that application with its own MS Office installation in a virtual machine yields a solution which is easy maintained, quite secure and - again - reasonably comfortable for the user.

[*]I use Linux at home, Windows at work because I must. I carry home a virtualized copy of the machine at work. This saves me the hassle of installing that 'other' software in my otherwise tidy private machine.

[*]Using VMs, you can afford to give each application its dedicated albeit virtual server. There will be no conflict in API, dll or other component version; you can assign very precisely defined privileges for the administration accounts (also for the remote accounts used by your software suppliers). Once a real server turns on the smoke signal feature or needs more power, you just move your virtual servers to other real ones. AT the same time, you have a very cost effective way of building a testing environment where you can - for instance - exercise installing and debugging the next release of your application.
[/LIST]

---

### Post by forrestcupp on 2007-08-11
I wish they would make the Linux version that good.  But it looks like they still aren't up to par on 3D gaming.

---

### Post by starcraft.man on 2007-08-11
> **forrestcupp said:**
> I wish they would make the Linux version that good.  But it looks like they still aren't up to par on 3D gaming.

Don't hold your breath. The 3d gaming/render VM userbase is mostly niche on the Mac, and their 22-25 milion user base is a lot bigger than the x number of Ubuntu/GNU/Linux. And on Windows we all know those games run native. So I don't think it'll be that soon unless a Linux company takes up the task to target us specifically.

---

### Post by jdrodrig on 2007-08-11
Continuing the discussion of the role of VirtualMachines.
It is true at the server, corporate level they are very useful. But I think that tigerpants meant for the average single user.

My answer would be that in the no so distant future you could have each application running on its own virtual machine, so that a crash in one, is even less likely to affect the others.

And of course, AMD and Intel have modified their mainstream processors so that some of the virtualization work can be done at the hardware level instead of just software...

---

### Post by popch on 2007-08-11
> **jdrodrig said:**
> Continuing the discussion of the role of VirtualMachines.
It is true at the server, corporate level they are very useful. But I think that tigerpants meant for the average single user.

My answer would be that in the no so distant future you could have each application running on its own virtual machine, so that a crash in one, is even less likely to affect the others..

For the average, single user there are indeed fewer scenarios where VMs will be useful enough.

Again, two come to mind immediately.

[LIST=1]
[*]As already mentioned in this thread for those who can not let go of an Windows application or two (or the reverse case, where they have to use Linux applications in a Windows world).

[*]As a convenient container to carry one's favorites applications with oneself, including all configurations, plugins and whatever, possibly also with some data, why not in a database such as mySql. A wiki in a pocket comes to mind. No matter what firewalls and so on, and no matter if the content are to be invisible in the web, you can carry it all with you.
[/LIST]

Yes, I do get carried away at times.

---

### Post by Kosimo on 2007-08-11
Wow...

In my opinion this is just SPECTACULAR!!!

I would love to have a mac, and my 3/4 preferred windows apps running on the same machine.!!  

Guys, the transition period to leave Windows behind are just starting...

When the Linux Version??

---

### Post by jdong on 2007-08-11
VMWare Fusion is really wonderful on my Macbook. I use it to run MS Streets and Trips under a 128MB RAM XP VM with fusion, which makes applications natively managed under the OS X window manager. It removes some of the "clumsiness" you feel from using VM's.

I also use it to run 3 32-bit and 2 64-bit Ubuntu environments for backports development and other testing configurations. There's also a FreeBSD VM and another VM for testing LiveCD's.

The ability to test several configurations of a system without rebooting is crucial for developers and a timesaver for even your everyday user.

Retailing at $80, it's one of the best VM's for the money. I've rarely had an OS that fails to work in VMWare, unlike Parallels and VirtualBox.

---

### Post by starcraft.man on 2007-08-11
> **jdong said:**
> 
I've rarely had an OS that fails to work in VMWare, unlike Parallels and VirtualBox.

Ahem! Ummm, excuse me but just what OS that you need doesn't work in Virtual box? On my old p4 box with only a GB of old RAM I've been able to run countless copies (not all simultaneously, it's a bit old for more than one or two) of Windows, BSD and Linux. Care to be specific please?

Edit:
> **Kosimo said:**
> 
When the Linux Version??

Don't hold your breath like I said. I don't think it's VMware's or Parallel's priority. They haven't done that much for Windows in the past year or so, so I just don't think it's that important to them.

---

### Post by jdong on 2007-08-11
> **starcraft.man said:**
> Ahem! Ummm, excuse me but just what OS that you need doesn't work in Virtual box? On my old p4 box with only a GB of old RAM I've been able to run countless copies (not all simultaneously, it's a bit old for more than one or two) of Windows, BSD and Linux. Care to be specific please?

Edit:


Don't hold your breath like I said. I don't think it's VMware's or Parallel's priority. They haven't done that much for Windows in the past year or so, so I just don't think it's that important to them.

I had ffmpeg SSE2/3 running in a FreeBSD host and VirtualBox consistently kernel panicked the host after a few minutes. A lot of other things that are compiled/tuned for the host CPU's instruction sets will behave similarly.

I also had some issues booting up some Linux distributions that used Vesa-TNG, and also ReactOS and DrDOS both have quirks.

VirtualBox handles mainstream OS'es pretty well, but if you do something a bit "out there", VirtualBox quickly reminds you that you aren't on a real PC. And I've rarely, if ever, had similar problems on VMWare products.

---

### Post by starcraft.man on 2007-08-11
> **jdong said:**
> I had ffmpeg SSE2/3 running in a FreeBSD host and VirtualBox consistently kernel panicked the host after a few minutes. A lot of other things that are compiled/tuned for the host CPU's instruction sets will behave similarly.

I also had some issues booting up some Linux distributions that used Vesa-TNG, and also ReactOS and DrDOS both have quirks.


Hmmm, never did those specific situations. I assume you reported those to the VirtualBox team for fixing in the next version?

> VirtualBox handles mainstream OS'es pretty well, but if you do something a bit "out there", VirtualBox quickly reminds you that you aren't on a real PC. And I've rarely, if ever, had similar problems on VMWare products.


Aye, I guess VBox isn't perfect (I even have a VMware workstation copy for the odd time). I'd say it's still pretty good for a fresh project though (and free to boot). I'm glad we don't have to depend on VMware or Parallels for delivering an easy and functional desktop VM, cuz they sure haven't been that interested in us. Hopefully added competition from Parallels and VBox with VMware will generate a lot of innovation in the VM field and propel the Windows/*nix side forward same as the Mac, that's just my sceptical optimism talking though >.>.

---

