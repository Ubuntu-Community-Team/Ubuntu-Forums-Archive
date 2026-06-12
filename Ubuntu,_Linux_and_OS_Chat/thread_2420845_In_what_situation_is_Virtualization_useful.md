---
title: "In what situation is Virtualization useful ?"
date: 2019-06-11
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2019-06-11
Other than testing new distros in what way is virtualization useful ?

I simply don't see the point in maintaining another distro.

I just feel lazy to keep 2 distros up to date. 

In short why do you use virtualization ?

---

### Post by Frogs Hair on 2019-06-11
It is an option for those who need to use Windows software . I have some software that keeps me dual booting.

---

### Post by QIII on 2019-06-11
For a casual user?

---

### Post by kpatz on 2019-06-11
I use it to test other distros... and also for Windows VMs for things I don't want to install on my laptop (i.e. Quicken).

I also use them as "destructable systems"... if I want/need to try something that could mess up an install or infect it with malware, I can snapshot a VM, try it, and then revert back afterward.

They're handy for test beds as well... before deploying my new 18.04 based firewall I built it up in a VM first and tested it there, then transferred it to the hardware when I had it ready.

The virtual networking features in Virtualbox can be handy for testing things as well... I can put some VMs on an isolated virtual network for example, or put one VM behind a firewall running in another.

---

### Post by SeijiSensei on 2019-06-12
I use Windows-based software for taxes.  I also use Microsoft Access as a database client (the actual databases are in PostgreSQL on Linux).  I keep a Windows 7 virtual machine around when I need to do these tasks.  I find virtualization far superior to dual-booting.  Being able to work in both environments can sometimes be very helpful.

I keep a couple of Ubuntu flavors as VMs so I can answer questions here. I prefer KDE, so I have little experience with the vanilla Ubuntu interface. I have a VM with that. I have another with Ubuntu Server for the same reason.

---

### Post by lammert-nijhof on 2019-06-12
Virtualization is very useful, especially in combination with e.g. ZFS. My Host is a minimal install of Ubuntu 19.04, because I have a Ryzen 3 2200G with Vega-8 graphics and I want the newest drivers. It is a minimal install, because I do all my work in a VM. I use 4 GB of my 16 GB as ZFS disk IO cache, which means that after the first use, the VM runs completely from memory cache (Hit Rate 93%). 

I use virtualization for the following reasons:

[LIST]
[*]Excellent performance, I do all normal work (Email, Browsing, LibreOffice, Whatsapp, Torrents, etc.) in a Xubuntu 18.04.2 VM. Response times are instantaneous due to ZFS.
[*]Security, I use Ubuntu 16.04 VM for Banking and Paypal and I use it for nothing else. The system is only "powered on" for in total say 1 hour/week. This and all other VM firewalls are closed for inbound traffic.
[*]Reliability, I use Ubuntu Mate 19.04 VM for experiments. Yesterday, I tried Super TuxKart in a VM with 3D acceleration. The keyboard control did not work, so I restored the Virtualbox snapshot, I took before the experiment. I do not slowly contaminate my main systems with these try outs.
[*]Consistency, I moved the VMs from my old Phenom II to my new Ryzen and I did not have to worry about any re-installation or setting. For example the Windows XP VM installation is from 2011 and has run on three desktops (32-bits Pentium 4 HT, Phenom II X4 and Ryzen 3 2200G) and two laptops (2008 Dell Inspiron 1521 and 2012 HP Elitebook 8460p).
[*]Nostalgia, I like to play my old music with WOW and TrueBass effects in Windows XP and living abroad I like to read the Dutch News as presented by the Windows 10 News App once a day.
[*]My music keeps playing, while I reboot the Linux VM, I'm updating or I'm using for try-outs. I could reboot it each minute, but the XP music plays on.
[*]I like to try three of the new Ubuntu releases 19.10 in a VM, see the new features and look for bugs.
[/LIST]
Before the Ryzen I did the same with my 2008 HP dc5850 with a 4-core Phenom II at 3.2 GHz and 8 GB of DDR2, using 2 GB as disk IO cache. I also have exacly the same VMs and ZFS running on my laptop, an i5-2520M also with 8 GB of DDR3, for the times I go abroad.

For the host I did select the newest OS with the best hardware support for that hardware, while for the Application VMs I can select the OS, I prefer for that task. In my case mainly LTS releases. No compromises!

---

### Post by TheFu on 2019-06-12
I use virtualization for almost everything. Have at home since 2006-ish.  Been using it at work since the mid-1990s.

It decouples the OS from the hardware.  The virtual hardware provided to the guest OSes is very standardized. Moving a VM between physical machines doesn't usually freak out the OS, because the virtual hardware "appears" to be the identical.

Scaling a server for more CPU or more RAM is really, really easy for VMs. It can be done from halfway around the world. No screwdriver needed.

It makes performance upgrades trivial - just move the VM storage over to new hardware.  So, moving from a C2D VM host to a new Xeon VM host doesn't freak out the guest VMs, but they run 15x faster.

It can make DR trivial, which tied to near real-time block storage replication.

It makes HA and automatic failover for most servers much easier.  The VM host can monitor when a VM fails and automatically spin up a replacement.  

For many server needs, trying to mix multiple complex systems inside the same OS install is nearly impossible and next to impossible to maintain.  I'd hate to attempt putting Nextcloud on the same OS install as Zimbra or Redmine or vTiger or Alfresco on the same system.

Maintaining an "enterprise communications server" is complex, so patching it all the time isn't an option.  But having an unpatched email server on the internet is asking to be hacked.  So, put an email gateway VM on the internet, but keep the full "server" on a less hackable subnet to protect it.

Servers often need to be in different network zones based on the risk factors for the services being run.  VMs have the ability to be connected to different networks, as the security design dictates.

Better system utilization.  10 yrs ago, the average CPU utilization for server hardware was 13%.  5% of that was just the monitoring software.  So over 85% of the expensive CPUs weren't be utilized.  With virtualization, we can better utilize existing hardware. Our current target is over 75%, but under 80% utilization, with peaks in the 90% range.  The same goes for RAM.  We tune the RAM allocations through the VM to be sufficient on our servers so that no swap is needed, ever.  That's better for performance. Happier internal customers. More fully used hardware that is cheaper for the company.  Think of it like having a semi-tractor trailer than you drive to the corner store to pick up milk.  If you have a semi, don't you want it being fully utilized?  There is a time when a 200+ mph motorcycle is needed, but most people have a semi at home for their milk runs.

Advanced storage and VMs.  Check out sheepdog for n+1 storage replication at the block level.  DR and HA solved for zero extra money.

Remote desktops via SPICE are amazing.  Can't do that without VMs unless commercial software is used.  SPICE requires KVM and works with Windows and Linux VM guests. Might work with other guests. I don't know.

Fewer systems needed.  Thanks to a faster 65W CPU build late last year at home, I've been able to retire 2 other 125W computers thanks to virtualization.  In just under 2 yrs, the savings in electricity alone will have paid for the new computer, which is faster than those 2 older computers combined.  Because CPU+RAM prices have dropped so much, I'm considering replacing a 5 yr old system that handles everything I need today with a 5x faster system, close to the performance of the build done 6 months ago.  I think it will be under $200 for the needed parts - MB, CPU, RAM and reuse everything else.  If I sell the 3 used systems, I might have a slight profit after everything is done.

Inside most professional IT shops, virtualization isn't an option. **It is the only way to deploy servers. ** Since 2004, where I've worked, virtualized systems has been the rule and dedicated hardware deployments where the exception.  More and more are using Linux Containers, which allow for a 10x density increase over using VMs. I'm not sold on container security at this point, but it is very interesting.

If it isn't clear, desktops aren't really what I do, though I'm typing this from a laptop, connected through SPICE to a KVM VM desktop. GUIs and GPUs aren't very important to me.  For me, a desktop GUI is just useful to have more xterms up. Of course, a desktop is needed for a browser or two and fancy email, notes, spreadsheets, but the majority of my windows are just ssh sessions into other computers managing workloads.

I do have a Win7 VM running to do 3 things for which I've been unable to find acceptable replacements on Linux. One of those things ends in January, so I'll be down to two things.  I don't see any viable replacement happening for those in the foreseeable future, sadly.

---

### Post by lammert-nijhof on 2019-06-13
Looking at your configuration for virtualization. The i3-6100 is OK, in the middle between my old Phenom II X4 B97 and my new Ryzen 3 2200G and your CPU easily beats my i5-2520M. Nowadays 4 GB is the absolute minimum for virtualization, so forget about ZFS. It is easier to use the comparable BTRFS, also with good disk IO caching, but it is better integrated into the Linux kernel and it is fully integrated with the installer. 

I would use Virtualbox because it is more user friendly and it allows you to activate windows using e.g. the sticker on your PC. With Qemu/KVM disk IO faster, but the UI is somewhat primitive and it often blocks the (re-)activation of Windows.

For Host OS I would use Xubuntu or Ubuntu Mate to leave as much memory as possible free for the VMs. For the VMs I did use the following memory allowances in both of my 8 GB systems:
- Lubuntu or Windows XP: 1 GB.
- Normal Linux Distros: 1.5 GB
- Windows 7, 10 or Ubuntu 18.04: 2 GB

With 8 GB I could load 2-3 VMs at the same time, with 4 GB you will be limited in practice to one. With 16 GB, I use the same sizes, only I increased Windows 7 and 10 to 3 GB and my main Xubuntu VM to 2 GB. 
Virtualbox will probably protest about 2 GB allowance with a 4 GB memory PC, ignore it or allow 1.9 GB. 
You can try out virtualization with ext4, but if you really want to use it daily for hours, you need the advantages of disk IO caching of the more modern file systems to compensate for the virtualization overhead.

---

### Post by TheFu on 2019-06-13
BTRFS had huge issues with KVM VMs.  Data loss issues.  Be very careful using it.  libvirt provides controls for disk caching regardless of the hypervisor.  [https://wiki.debian.org/Btrfs](https://wiki.debian.org/Btrfs) spells out some of the issues.
> bcache can introduce grave errors is one.
> COW on COW: Don't do it!
    This includes unionfs, databases that do their own COW, certain cowbuilder configurations, and virtual machine disk images. Please disable COW in the application if possible.  ...  For example, for QEMU, refer to qemu-img(1) and take care to use raw images.   Basically, if you use btrfs, then you shouldn't use qcow2 for VMs.  That's one of the greatest things about virtualization, qcow2.

I ran 15 server VMs on 8GB RAM VM host.  Just leave at least 1GB of RAM for the hostOS and don't oversubscribe RAM or disk.  Lots of server VMs run fine in 384MB of RAM even on bloated Ubuntu Server. People do get DHCP and DNS servers below 256MB of RAM with lighter distros.  Obviously, if desktop VMs is the purpose, those hog more RAM.

If you intend to run desktop -on- desktop virtualization, then virtualbox is probably the best choice, but SPICE with KVM is actually pretty great now.  virt-manager is a virtualbox-like VM config manager.  F/LOSS, know it, love it, use it. ;)

---

### Post by Shibblet on 2019-06-13
> **linuxyogi said:**
> Other than testing new distros in what way is virtualization useful ?

I simply don't see the point in maintaining another distro.

I just feel lazy to keep 2 distros up to date. 

In short why do you use virtualization ?

I use it to run Windows 7, so that I can use Adobe Software.  And I cannot get these apps to run under Wine.  Plus, I am well trained with Adobe software.  Learned it back before Adobe purchased Aldus (Pagemaker).

GIMP is a great substitute for Photoshop
Inkscape is a great substitute for Illustrator

Scribus is a great page layout program, but it is not quite up to par with InDesign.

---

### Post by xavierbaez on 2019-06-16
A lot of finance software only runs on Windows, so there you go.

Plus with so many cores now a days, Virtualization is one of the top things I want to do the next 2-3 years.

---

