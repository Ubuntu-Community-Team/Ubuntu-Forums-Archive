---
title: "System for VM and work use"
date: 2016-07-28
forum: Ubuntu, Linux and OS Chat
---

### Post by UDroidie626 on 2016-07-28
Hi All,
I am looking at a distro for my work laptop, I will mostly be using KVM to VM a windows machine I need and the rest I can do on any distro (Word processing, emails etc)
So I am a bit stuck between Debian and Ubuntu (Or a spin of it), I am undecided if to go super stable or a bit more bleeding edge, the kernel will be rebuilt every .X release with GRSec possibly (I deal with some information I would rather be better protected)

What would you suggest between these two? I know they are both great systems but I cannot decide between.

Thanks

---

### Post by TheFu on 2016-07-29
That is a huge question. 1,000s of blogs and other articles have been written about it.  What has your research found so far?  I've written a few articles too:
* [http://blog.jdpfu.com/2013/07/29/which-distro-do-you-run-why](http://blog.jdpfu.com/2013/07/29/which-distro-do-you-run-why)
* [http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release)

I use both.  Debian for some servers (not desktops) and Ubuntu LTS releases for other servers and a few desktops.  I don't touch non-LTS releases. Not worth my time to only have 6 months of real support because I won't load an OS within a month of release and it takes a few months to get the next release out and stable.  LTS every other year has been sufficient for all my server needs.  For desktops, after about 18 months, a few of the social networking programs stop working - not a big deal.  Plus, many GUI programs used in desktops don't really get 5 yrs of support for an LTS. That is only for programs maintained by Canonical, not the upstream or PPA programs.  All distros have this issue, they just don't make it easy to find what is and isn't supported.

I don't know anything about GRSec. Sorry.  Between apparmor, dm-crypt, VMs, containers, and jails, I feel there is sufficient security in Ubuntu.

In the end, it is personal choice.

Why limit yourself to debian/ubuntu as solutions?  Check out Qubes for a little more separation between different projects/workspaces.

Might try each for a few weeks to see what you like.  Also, know that you aren't stuck with any single GUI with either distro. The GUI is just another program, not the OS. Don't like one, swap in another.

---

### Post by Tadaen_Sylvermane on 2016-07-29
I was tossing between Ubuntu & Debian a few years back. I've been using Ubuntu almost exclusively since. It came down to ease of packages for me. Ubuntu has been rock solid as long as I avoid Unity and does everything I've asked it to without fuss. In the end I prefer ppas to compiling stuff myself.

If you choose Ubuntu then as you said stick with the LTS versions, avoid Unity as well. Unity has been the sole source of random unexplainable errors in my experience so far. Now I use Ubuntu Server with a custom i3 setup on my laptop. Server runs direct boot to kodi and doubles as media center.

---

### Post by T.J. on 2016-07-30
> **UDroidie626 said:**
> Hi All,
I am looking at a distro for my work laptop, I will mostly be using KVM to VM a windows machine I need and the rest I can do on any distro (Word processing, emails etc)
So I am a bit stuck between Debian and Ubuntu (Or a spin of it), I am undecided if to go super stable or a bit more bleeding edge, the kernel will be rebuilt every .X release with GRSec possibly (I deal with some information I would rather be better protected)

What would you suggest between these two? I know they are both great systems but I cannot decide between.

Thanks

As a general disclaimer, I do not recommend using a VM on a laptop if you have other means - regardless of the OS you use.  The hardware they put in laptops is not extraordinarily powerful, compared to their workstation counterparts for serious number crunching.  I'm not saying you can't make it work, but you should expect a few problems with sleep states and performance.  They put in really cheap hardware, and sell it at a higher price.

With respect to everyone else's stance on the matter, I suggest Debian Stable, hands down - with no doubts whatsoever. I prefer it for all serious work, as I can depend on software in its stable repositories to work as intended. Ubuntu is a good distro, and I have no fear or qualms about using it, but it is simply not as stable or well built as Debian. That is not a criticism, just an observation, after using both and porting code to both. 

Ubuntu's source code is pulled from the Debian Testing and Unstable source trees. That in itself is not a bad thing, but it is also true that software in those trees can be randomly broken, even on an Ubuntu LTS. Since Canonical actually supports only a tiny fraction of what Debian does, they do not check the testing/unstable source for breakage when pulling it in. I've noted this a lot, especially with Kubuntu and KDE applications, although the other desktops have had examples as well.Ubuntu's advantage of PPA's is not really an advantage in my mind.  I've had badly built PPA's trash the package database, leaving the system in an irreparable state without directly hacking the files. For most users who are not programmers, that is not an option. Sadly, no one has any required testing standards for PPAs; so you are taking a chance of breaking your system whenever you use them.

 Comparing that to the Debian Stable versions, the Debian Stable versions normally work as intended.  If you do find a bug, it is minor.

If you are serious about using it for work, it is my opinion that you would want stability first.  If decide later that you need updates and don't mind risking major bugs, you can get them pre-built via "Debian Backports" or build them yourself using [https://wiki.debian.org/SimpleBackportCreation](https://wiki.debian.org/SimpleBackportCreation). All that said, Debian is not a bed of roses either.  Since Debian does not package some proprietary wireless drivers on the install disk for license reasons, you may have trouble with the install.  There is a special install disc you can download to help you make things go more smoothly.

Naturally, if you decide to take my advice, I'll be happy to help you get things arranged.

---

### Post by TheFu on 2016-07-31
> **T.J. said:**
> As a general disclaimer, I do not recommend using a VM on a laptop if you have other means - regardless of the OS you use.

People using VMs aren't normal end-users. They understand more about computers and sharing resources than average end-users.

Virtualization works fine on laptops, with a few caveats. People use it all the time and get 90-95+% of native performance for non-GPU applications.  If all you need Windows for is Visio or Quicken then running a small VM on any C2D or better system made in the last 8 yrs works great. Even on many cheap laptops, it works fine.  Sure, you need to be aware of networking, power, differences for VMs and networking without static IPs can be a hassle, but it isn't THAT hard to understand and make workable.

Windows works fine running inside a VM with 4G physical RAM system running a C2D or better CPU.  Just allocate 1.5G vRAM, 128MB of Video RAM and 1 vCPU to Windows. If you have an SSD, do whatever you like with the storage. The only thing that sucks about Windows is how much disk storage it requires (5-8x what a Linux VM would usually need). If course, if you have more RAM, more CPUs and more disk, these things allow a little more resources to be shared with the VM(s).

There isn't any need to have a monster system to run VMs for most end-users.  Of course, if you are hoping to make an ultra HiDef video processing workstation from a low-end laptop running Windows inside a VM, it is likely to lead to disappointment, but with reasonable expectations and reasonable laptop hardware, it works just fine.  Or if you are a Java programmer ... well, then nobody has enough resources to be happy doing that. ;) The dev environments for Java are extremely bloated, resource hungry and slow.

Heck, I've run KVM VMs on a $299 chromebook (HW, not OS) with 2G of RAM thanks to VT-x support in the Celeron. It greatly exceeded my expectations. I wouldn't attempt to run Windows on that machine, but a few Linux servers worked great.  My current $450 chromebook has plenty of CPU, plenty of RAM, and enough HDD that I'd be willing to run any OS in a VM on it.  Sure, I'd lean towards using containers instead but it can do full KVM VMs too.

---

### Post by T.J. on 2016-07-31
> **TheFu said:**
> People using VMs aren't normal end-users. They understand more about computers and sharing resources than average end-users.

Virtualization works fine on laptops, with a few caveats.


All true. I just make a general disclaimer on some things, because I do not want to give false expectations.  Engineers tend to be conservative on estimates of performance, so that the end result is pleasing, nothing more.  Not all laptops are created equal.  It may work really well, and then there might be hardware issues with chipsets.


> Windows works fine running inside a VM with 4G physical RAM system running a C2D or better CPU.

It can, although I recommend twice that if you are trying to use Visual Studio.

> There isn't any need to have a monster system to run VMs for most end-users. 

In some cases, I must disagree, especially if your software uses a lot of threading. 

> The dev environments for Java are extremely bloated, resource hungry and slow.

All Java performance issues are relative to whether or not you are using a decent JIT environment.  If you are using  JIT to convert to native code, it can be more reasonable.  I personally do not like Java, .NET, or Python as all of them have similar issues - no legal protection via the ISO;  and all waste finite resources with less benefit than their fans promote.  But it is also true that you can convert them through an intermediate stage into native code.


>  My current $450 chromebook has plenty of CPU, plenty of RAM, and enough HDD that I'd be willing to run any OS in a VM on it.  Sure, I'd lean towards using containers instead but it can do full KVM VMs too.

Naturally, however, only Linux can be used in containers.

---

