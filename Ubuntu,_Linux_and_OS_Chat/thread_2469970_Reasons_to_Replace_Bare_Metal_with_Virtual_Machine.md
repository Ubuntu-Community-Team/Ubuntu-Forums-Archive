---
title: "Reasons to Replace Bare Metal with Virtual Machines."
date: 2021-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2021-12-15
I run a **minimal Install of Ubuntu 21.10** on OpenZFS 2.0 and I moved all my applications to Virtualbox Virtual Machines (VM). My oldest VM is Windows XP Home and that one has been installed and activated March 2010. It has survived 3 PCs and 4 CPUs. The first one was a 32-bits Pentium 4 HT and the last one a 64-bits Ryzen 3 2200G. 
What are the advantages/disadvantages of moving your stuff to VMs:
[LIST]
[*]You can't use Virtualization for modern games, however you can play some modest games in a VM using 3D acceleration. I tried LInux games like e.g SuperTuxKart or Extreme Tux Racer and the Vega 8 iGPU did run at ~80% for these games at 1080p and 60Hz. 
[*]Your installation lives longer and will survive all HW upgrades. 
[*]It runs at ~95% of the CPU performance of bare metal. 
[*]Boot speed on the Ryzen 3 is good, Ubuntu VMs and its derivatives boot in ~10 seconds and Windows 11 VM in 33 seconds from a SP nvme-SSD (3400/2300MB/s). My Ubuntu VM boots faster than the bare metal Ubuntu due to ZFS caching. 
[*]Using OpenZFS you can always restore a VM disk image from an old snapshot, after being hacked or after you made a mistake. You could also use the Virtualbox snapshots for that purpose, but the OpenZFS ones are extremely fast (~1 second) and more efficient in storage usage. 
[*]You can encrypt critical VMs using ZFS or Virtualbox. 
[*]I only have open ports in one VM, the VM used for communication apps. All other VMs and the Host OS are closed for all inbound traffic. 
[*]You can use specialized distros for certain application areas; 
[*]You can use VMs to replace distro hopping. 
[*]All VMs use the shared folders stored on the Host, but they only get access to the part(s) they need. 
[/LIST]
I use the following VMs:
[LIST]
[*]Xubuntu 20.04 LTS for all communication apps, the only one with open ports; 
[*]Ubuntu 16.04 ESM for banking and PayPal, encrypted by Virtualbox; 
[*]Ubuntu Studio 20.04 LTS for multimedia; 
[*]Ubuntu 20.04 LTS for experiments, e.g. running Linux games in a VM or running Wolfenstein-3D or WordPefect 5.1 in DOSBOX. 
[*]Windows 10 Pro 
[*]Windows XP Home to play the wma copies of my LPs and CDs with WoW and TrueBass effects. 
[/LIST]
I also run the development editions of the future 22.04 LTS.
[LIST]
[*]Ubuntu to run Virtualbox and to test my Host OS functions; 
[*]Ubuntu Mate to run QEMU/KVM, just to keep an eye on that development; 
[*]Ubuntu Budgie to run Gnome Boxes, just to keep an eye on that development; 
[*]Xubuntu with the same communication apps than 20.04 and sometimes used hours for the real work instead of 20.04; 
[*]Ubuntu Studio, to check whether I like the change to KDE. 
[*]Windows 11 Pro 
[/LIST]
I'm a collector of VMs. In total I have now ~70 VMs. all Windows VMs from 1.04 to 11. All Ubuntu LTS releases, the first 4.10 release and my first 5.04 release. I have many many other distros with one or sometimes 4 release, examples Manjaro; Garuda Linux; Fedora (33 and 35); Deepin; Linux Mint; Peppermint (3; 7; 9 and 10); Xubuntu (12.04; 18.04; 20.04 and 22.04) etc etc.

 I've been hacked twice this year and 0 times in all previous years. Most hacks nowadays are caused by Internet Browsing; Email or Messenger etc. The first time I did catch it through the browser and they asked for $4500. The second time it looked like a Windows hack, coming from a friend through a facebook messenger annex send from his hacked Windows computer. In both cases I rolled back Xubuntu 20.04 and did rerun the last OS updates. Worst case I would have deleted the Xubuntu 20.04 VM and restored it from my backup server or reinstall it. I could even fallback to Xubuntu 18.04, that I used till Apr 2020 or valiantly move to 22.04.

---

### Post by TheFu on 2021-12-16
Nicely laid out.  I've been running my main desktops inside a VM for over a decade. Mainly because it was portable between different physical hardware.  Had a laptop stolen in an airport on the way to a destination.  I picked up a cheap laptop and loaded my "desktop" VM onto it. It was "my" desktop with everything installed, configured and ready for use. The only time lost was buying the new laptop in a store in a foreign country.

Virtualbox is fine for desktop-on-desktop needs.  Not so great for running servers, unfortunately. That's where KVM+libvirt is the solution today.

Where I worked mandated that VMs be used for all new systems in 2005. It required an approved architecture board variance to install directly onto hardware. Initially, some companies balked at supporting VMs, but that quickly changed. We were the 2000 lb gorilla and they had to do what we said ... well, every vendor except about 5.  We were actually using VMs in production on Unix in 1999 and for test teams from 1997 with VMware workstation.

When Core2 Duo systems became available, running nearly all systems in a hypervisor became very nice. It took just a few tweaks in the defaults to get excellent performance for non-high-end graphic needs.  My interests have always been with running non-GUI servers, so using VMs and now Linux Containers has really become a solved issue.  VMs were solved in 2010 with a solid KVM+libvirt. They became much better in 2018 with SPICE "just working" for GUI stuff.

As for old OSes.  I noticed a box with DesqView386 in it. That was my first multi-tasking OS overlay. Running both QuattroPro AND Word5.0 concurrently was a big deal. Seems it would be fun to get some old MS-Dos games running inside it today.  I got that less than a year before OS/2 Warp was released.  Warp changed everything for me.  32-bit was good. It was the best DOS programming environment available at the time.  Windows was still crashing back then.  OS/2 and Windows both had very ugly GUIs.  Win95 make a usable, pretty GUI.  Remember, this was all before SATA and USB.  I also had a Slackware boot. At the time, I was booting about 10 different OSes.  The trick was to get booting to be possible in the first 1024 sectors. That was a LILO limitation.  These were the days of a 240MB HDD.

I have a WinXP VM somewhere. It has full licensed versions of MS-Office, especially Visio and a few games.  With XP, MS-Dos games still worked mostly.

---

### Post by Shibblet on 2021-12-16
I think you hit the nail right on the head.  Bare Metal = Hardware.  Software that requires direct HW access (sometimes) doesn't function as well under a VM.  Gaming is probably one of the more known aspects.
I have heard of people getting the best performance with KVM.  But if you're a gamer, it seems more practical to just make a Windows boot partition, and game on "Bare Metal" instead of trying to set up a VM.

Personally, I use a Windows 7 VM on VirtualBox for one bit of software that doesn't have an acceptable replacement in Linux... namely Adobe InDesign.  I have an old copy of Adobe CS6 that I purchased many years ago.  The alternative software is acceptable, but since I've been using Adobe software as a professional graphic artist for over 25 years, it's hard to switch to things like GIMP and InkScape.  

GIMP and InkScape are great alternatives for Photoshop and Illustrator... but Scribus is a sad replacement for InDesign.

It's not that I can't learn it, it's that I know instead of spending the time to learn the new software, I could be productive using Adobe instead.

Since I am not much of a gamer anymore, I don't really need a Windows partition, so the VirtualBox VM works for all my needs.

---

### Post by lammert-nijhof on 2021-12-16
You did give me and idea, i still have the 3 floppy images and the 2 ISO files for OS/2 Warp, it would be fun to re-install it in a VM. I used it in the past, dual booting OS/2 Warp and Windows for Workgroups 3.11 on my 486DX66 from 1993.
That 486 had 8MB of memory and I think a 300MB HDD, 5.25" and 3.5" floppy drives and later I added a CD reader. I still have that PC and last time I tried it was in 2014. I have no space, so it is in a cabinet. 

Some years ago I dual booted virt-manager/kvm and Virtualbox. Virt-manager/kvm was faster, especially in its disk IO, but Virtualbox was more user-friendly and everything just worked.

---

### Post by TheFu on 2021-12-16
> **lammert-nijhof said:**
>  Some years ago I dual booted virt-manager/kvm and Virtualbox. Virt-manager/kvm was faster, especially in its disk IO, but Virtualbox was more user-friendly and everything just worked.

virt-manager is 100x more friendly today and still faster with the enterprise capabilities still. If you haven't looked at it since 18.04, it is worth looking again. Most of the defaults now are also good for performance.

Of course, it isn't great for high-end gaming where the GPU performance is 99% of the need.

---

### Post by DuckHook on 2021-12-17
You may wish to consider containers. I use LXD, but there are others (Docker comes to mind).

Pros:
[LIST=1]
[*]Less resource intensive: mapping onto base OS eliminates the inefficient translations needed in a VM. Container sizes start out tiny and can grow dynamically with little performance degradation (especially on SSDs).
[*]Bare metal performance: the container simply passes system calls to the host OS. For example, my Linux and Steam games run at native speeds.
[*]Insanely versatile: Example, I have one LXD container set up with a permanent VPN so that browsers launched from within it are automatically shielded from my ISP and/or geo&#8209;located to another region.
[*]
[/LIST]
Cons:
[LIST=1]
[*]Non-trivial: Getting containers to work and getting the kinks worked out is a high learning curve. They were designed for CLI containment; GUI functionality is an afterthought. Uses ZFS which is another bag of tricks of its own.
[*]Lousy documentation: it suffers from the worst of the obscurity and arcanery that characterizes Linux.
[*]Less secure: VMs are still better jails.
[/LIST]
If interested, there's a link in my sig.

I also have VMs installed and like them too. It's a necessity for something like W10. Like TheFu, I switched from quasi&#8209;proprietary VMs to KVM. I found that a kernel&#8209;resident VM was just faster and slicker.

Speaking of kernel&#8209;resident VMs, is Zen still a factor? It's been years since I've heard of anyone using it but, as far as I know, it is still part of the Linux kernel.

---

### Post by TheFu on 2021-12-17
+1 for using LXD in specific situations.  It is very much like a HVM setup, but with much less overhead, more speed. There are lots of base OS images for LXD containers. Ubuntu Cloud Server is one, but for lighter setups, there's alpine which is 10M or so. LXD VMs need to be patched like a normal Ubuntu OS, IME.

Using some normal features of a full kernel will break the ability to run in non-privileged mode in lxd. I know that NFS and every firewall/vpn I've looked at required it

LXD doesn't mandate using ZFS, but the way it is setup, it really (x1000) wants ZFS as the storage. I failed to get any other storage backend working. In theory, it should work with thin-provisioned LVM.  The lxd storage commands seem to be rumor documentation.  You know - nothing works except exactly what the LXD team uses. Everything else is just a rumor, documented or not.

The biggest downside to LXD, from my perspective, is that Canonical only distributes it as a snap package. That's the fairly huge negative. Right now I'm running these things in lxd containers:
[LIST]
[*]pi-hole/dnsMasq/DNS server
[*]wallabag
[*]nextcloud
[*]email gateway
[*]backup server (for testing)
[/LIST]
The learning curve for how to deal with the OS after the initial setup doesn't require any learning curve. Treat LXD containers like VMs, not the typical container.

---

