---
title: "Ubuntu in windows 7"
date: 2014-07-02
forum: Virtualisation
---

### Post by RaoulJWZ on 2014-07-02
hello everyone
I want to install ubuntu on a virtual machine on my windows 7 pc.
I only have some questions before i can do it:
Will my windows 7 system stay?
Will all my files, games, etc., which are on my pc now?
If i won't like ubuntu, is it possible to delete it then without problems?
Thanks

---

### Post by Bucky Ball on 2014-07-02
*Thread moved to **Virtualisation**.*

Welcome. You will get more knowledgeable responses here.

Perhaps do some more research regarding virtual machines. Do you know what software you will be using to run one? ;)

None of the things you mention will happen. If you're running a virtual machine, it has nothing to do with your current OS. Their only relationship would be that Win would be the host, Ubuntu would be the guest. They are not related in anyway, apart from one is hosting the other. Doesn't affect anything in Win.

If you don't like Ubuntu then just unmount/delete the virtual machine. You might be better simply booting from the Ubuntu LiveDVD or USB and 'Try Ubuntu' if you want to test it out. Then, if you like, do a regular dual-boot or create a VM.

Here's a start for your research.

[https://duckduckgo.com/?q=what+is+a+virtual+machine](https://duckduckgo.com/?q=what+is+a+virtual+machine)

---

### Post by marco-parillo on 2014-07-02
Yes, I am currently running Kubuntu in a VMware Player under Win7, but the answers would be the same for the other popular Virtualization Program for Windows (Virtual Box).
I like VMware Player because it is no-cost, and it features an easy install option for Ubuntu. All you need to do is point it to your ISO, give it your name, login id, and password, and I simply take all the defaults.
Your host machine should have at least 2GB of memory, if you want to dedicate the VMware Player default of 1GB to your virtual machine.
Another default is to have your disk dynamically allocated. For best performance, you want a static allocation, but I find my performance adequate anyway.
Once installed,  you would login to Win7 the same as always, Launch your VMware Player Icon, select the virtual machine you want to play, and it (the VMware player) runs as a Win7 program.

To answer your questions:
> [COLOR=#000000]Will my windows 7 system stay?[/COLOR]

Yes, VMware Player is simply another Win7 Application.

> [COLOR=#000000]Will all my files, games, etc., which are on my pc now?[/COLOR]

Yes.

> [COLOR=#000000]If i won't like ubuntu, is it possible to delete it then without problems?[/COLOR]

You can remove individual VMs (as the files for them all sit in your Windows file System) very easily.

---

### Post by TheFu on 2014-07-02
@marco-parillo's answers are good for virtualbox too (except where he says MB - I think he meant to use GB) ... provided you don't go out of your way to use more advanced storage features. You won't accidentally do this - no worries.

I'm less than thrilled with either Oracle or VMware companies, but that is a personal issue for me (been screwed by both). Many people use both tools and are happy for many years.  I switched to KVM a few years ago from ESXi, Xen and virtualBox and find it works at least as good as those options, but as 100% F/LOSS.  Used to run VMware Workstation, and VMware Server before that.  Also used IBM LPARs, HP vPar and nPar, Solaris containers and domains, ... the list goes on ... 

With either of these virtualization tools, there is very little risk of harm to your Windows data or programs. Read the links that that moderator provided to get a better understanding - generally, these VM tools create a virtual hardware environment for the new OS to run inside - that means everything is virtual ... cpu, ram, disk, networking, video ... the actual hardware inside your physical machine does NOT matter to the VM (guestOS).  Clearly, the guestOS will need storage, 10G is fine to get started. Linux is NOT windows and doesn't hog space relatively speaking. Heck - I have a few VMs that are less than 1G for storage, but those are not Ubuntu or desktop installs. GUIs lead to bloat, that is just the way of the world.

So .... during installation of the GuestOS, don't worry when it says that "all data will be wiped/lost" ... that is just for the virtual HDD, not your real HDD. ;)  Trust us, it will be fine.

Of course, there are a few settings that will make any virtual machine perform better. Getting 90-95% of native performance isn't hard anymore. For now, just go with the defaults and if that doesn't work for you, come back and ask for help.

---

### Post by marco-parillo on 2014-07-02
Thank you TheFu, and I have corrected my post. Separately, you are running KVM now, but **[COLOR=#000000][RaoulJWZ]("http://ubuntuforums.org/member.php?u=1932123") is interested in using Win7 as a host. KVM does not support Win7 hosts, right?[/COLOR]**

---

### Post by TheFu on 2014-07-02
> **marco-parillo said:**
> Thank you TheFu, and I have corrected my post. Separately, you are running KVM now, but **[COLOR=#000000][RaoulJWZ]("http://ubuntuforums.org/member.php?u=1932123") is interested in using Win7 as a host. KVM does not support Win7 hosts, right?[/COLOR]**

That is correct.  Virtualbox or VMware (player/workstation) are the primary options, though some purists may try to get QEMU working (beyond me).

I've posted my virtualbox-performance link here enough already that anyone interested can find it. ;)  It does work and not just for vbox systems, but as a general guide for performance tuning of HVM VM settings. I'll post something about LXC and Docker once I'm familiar with those too.  They are mainly for servers, so not-so-much for general end-user VMs.

---

### Post by RaoulJWZ on 2014-07-02
Okey i know enough to now that i'm gonna like it :).
Thanks all!

---

### Post by squakie on 2014-07-03
Your experience will based on your hardware - the CPU type, number of cores, memory, etc., all make a huge difference.

---

### Post by marco-parillo on 2014-07-03
> [COLOR=#000000]Your experience will based on your hardware - the CPU type, number of cores, memory, etc., all make a huge difference.

For me, the biggest difference was in the etc. (an SSD disk). It greatly improves boot times. Most users only re-boot their native Linux Distro installs when their update manager tells them to, but in a personal VM (say VMware Player, not a server ESXi), [/COLOR][**[COLOR=#000000]RaoulJWZ[/COLOR]**]("http://ubuntuforums.org/member.php?u=1932123")[COLOR=#000000] will boot his distro at least as often as he will boot his Windows Host OS.[/COLOR]

---

### Post by TheFu on 2014-07-03
SSDs make everything feel faster, but if you preallocate the storage, it will be almost native speed. Sparse files are slow, except on SSDs.  When choosing virtualbox/VM-player, these are end-users, not running real servers. That tool isn't meant to be used on servers where long uptimes are expected and definitely NOT on a Windows host where reboots still happen as a surprise. ;)

I can say that in over 2 yrs running KVM, almost 3 now, never has a VM or hostOS rebooted without me asking it.  I patch weekly, so reboots only happen during approved maintenance periods, but we are still current on every system from 10.04, 12.04 and 14.04. We don't bother with non-LTS releases or unsupported versions. 

I did some testing of 14.04 boot performance on virtualbox and posted the result here in a different thread in April. Config DOES matter - though sparse VDI files are much better now than they were a year ago.  Of course, this also assumes the hostOS file system on a spinning HDD isn't fragmented.

Really, the CPU (C2D or better) and RAM matters more than disk. At least in my testing.

---

### Post by squakie on 2014-07-04
+1.  You could have the fastest disk invented by man, but if your CPU isn't powerful enough, if it doesn' have at LEAST 2 cores, if your memory is below 4gb or so, your virtual machine performance will suffer badly.

---

