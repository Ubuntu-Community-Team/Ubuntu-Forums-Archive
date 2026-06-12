---
title: "Disk setup, Partitioning, Mounting, Adding - Where to begin ?"
date: 2021-03-23
forum: Server Platforms
---

### Post by netrix-g on 2021-03-23
Hi all,
I'm after advice on disk setup, or a pointer to some guides - searching t'internet hasn't shown me anything that I can relate to thus far.
I'm new to Ubuntu - my current server is an HP DL380 with hardware Raid capabilities.
I currently have 2 x 300GB drives installed and have another 6 x 4TB drives being delivered - 8 Hard drive bays int he server (all used equipment -the drives have to be wiped of any data before I can use them)

Current setup:
2 x 300GB disks installed and setup as Raid 1 via HPE Disk Management Tools during bootup.
I installed Ubuntu 20.04 LTS from a USB stick and followed all defaults when it came to the hard disk/partition setup and if I'm honest I didn't take too much notice of what the setup was doing in terms of the partitioning etc - my bad I know!

I presumed the whole 300GB would be used as the OS drive (akin to C:\ on Windows) and when I install the other drives I could split them up into Backups, Music, Movies, Photos etc.

When I look in the Disks app I can see that only 149GB of the 300GB has been used for a "Block Device"
[ATTACH=CONFIG]288173[/ATTACH]          [ATTACH=CONFIG]288174[/ATTACH]

What has happened to the other 150-ish GB - and what can/should I do with it ? Unless you think otherwise I would like to have 1 x 300GB drive for the OS [set as Raid 1] and [once installed as Raid 5] around 20TB for "everything else"

I'm hoping any remedial action can be done without affecting the setup so far, in terms of application, SSH etc - but happy to re-install if need be, it will add to the learning experience !

Thanks in advance and regards

Netrix

---

### Post by CatKiller on 2021-03-23
You should be aware that you've chosen to use [Logical Volume Management](https://opensource.com/business/16/9/linux-users-guide-lvm) rather than normal partitions. You'll want to use LVM tools rather than partition tools to administer them.

It's not something I've played with, but I know that TheFu is a fan.

---

### Post by slickymaster on 2021-03-23
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2021-03-23
Yes. I like LVM.  These days, if I were just starting out again (pondering being young again.... ) I'd probably learn ZFS instead.  ZFS on Linux really isn't ready for OS use (booting the OS), but it is excellent for data storage needs.  ZFS doesn't use RAID hardware.  It like ECC RAM, which any real server should have.

As a server guy, you've probably used Veritas Volume Management already.  LVM is like that.  LVM has 3 objects that are used for management.  PV, VG, LV.  For nearly all uses, an LV can be considered a normal partition just like you already know - it is just logical and very flexible.  In reality, normally we'd make a PV use an enter partition, then put a VG into the PV, then have 1 or 50 LVs from the VG. LVM improves performance, which is counter intuitive.  Creating a new file system on a partition could take 5-120 minutes. It is 5-60 seconds if LVM is used, assuming the same size and file system is selected. Counter intuitive. LVM brings all sorts of features, but there is 1 negative - complexity.  Being able to move storage to a new disk WHILE THE OS KEEPS RUNNING can be done with LVM (look up **pvmove**). With hot-swap disks, zero downtime involved. That's important for enterprises. That's just 1 of the features. There are 50 others.  That's the $2 overview.

Ok ... onto the layout stuff. How to split up the different parts of the system?

Generally, the OS partition/LV, /, should only get 25-35G. The 149G shown above is 5x more than I'd ever need. When it comes time to upgrade to a new release, keeping the data separate from the OS is very handy.  Having room for 2 different OSes is also handy.  So, instead of (1) 149G partition for 1 OS, I'd consider
[LIST]
[*]35G - Linux 1 OS [currenly used Linux]
[*]35G - Linux 2 OS [testing for new Linux]
[*]4.1G - Linux swap (shared by all)
[*]50G - /home ... to start. May want to add more as needed, later.
[*]700MB - /boot ... /boot may or may not need to exist. With LVM and encryption, a separate /boot is mandatory. This is where init boot stuff and the kernels go. If it gets full during a kernel upgrade (which happens a few times every month), then a system may not boot. Don't let this fill up. Normally, only 350MB is used, but if full, this is a huge hassle for everyone to fix - much worse for people new.
[*]200MB - for the FAT32 EFI partition. I think the default is 500MB. I've never seen more than 10MB actually used, but my setups are simple. 200MB is probably 10x larger than needed.
[/LIST]

Splitting off /var and /home from the OS is often smart. LVM can help with that, but it isn't really beginner friendly.

With all LVM setups, it is best to never allocate all the storage.  You'll want some for snapshots (great for clean backups) and you'll want some excess room in the VGs to add quickly to LVs as needed.  Adding room to an LV is 5 seconds on a running system; zero interruption or downtime. Removing excessively large allocations from an LV requires backing up the data, umounting the storage, then running lvreduce. You'll want to remember the option to also reduce the file system size too. Or run a separate command to reduce the file system size inside the LV first.  Some file systems, like XFS, cannot be reduced. They have to be removed, then created at a smaller size.  ext4 supports reduction.  Let's just say, it is hard to reduce, but trivial to increase LV sizes.  Start out small and increase for 3 months of use at a time.

For me, storage design is all about backups.  I want my OS LV to be as small as possible, since it will have daily, automatic, versioned, backups. If a log file starts increasing 1G/hr, I'd rather learn of that faster. Logs go in /var/log ... so having a separate /var LV makes sense.  
```
$ sudo du -sh /var
5.9G    /var
``` is a little large.
On another system:
```
$ sudo du -sh /var
143G    /var
```
This system has some virtual machines and the storage for test VMs are in /var/lib/libvirt/ .... hence why that is so large.
```
$ df -Th
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   16G   15G  51% /
/dev/sdb1                         ext2  720M  212M  472M  31% /boot
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  123G   41G  75% /var/lib/libvirt

```
The *mapper* storage above is all LVM LVs.  That 143G for /var ... includes the mounted /var/lib/libvirt extra 173G. In Unix, mounts can be placed anywhere.  As you can see, I mount different LVs where it is needed.  Actually, for my production VMs, each gets a dedicated LV, or 2, which aren't mounted on the host server. Only the VM sees the block LV provide.

Ah ... and I always use a swap LV.  This doesn't show up in the above, but it exists.  This removes the need for a swap file inside the / partition and it can solve some other issues. Swap files are faily new in Linux and still have some faults.  Swap partitions or LVs have been around nearly 30 yrs - the entire history of Linux.

If all this is too technical - and it would be for people without enterprise storage experience - then you might prefer to learn basic Linux storage with inflexible partitions instead. At least while starting out.

I'm 100% serious about learning ZFS for data storage, however.  ZFS negates the RAID card use.  Just setup the RAID card to provide JBOD access to storage.  You can use RAIDz or RAIDz2 with ZFS, if you like. If you have room, adding an SSD to be the ZFS caching device will dramatically improve performance, if that is important.  For audio and video files, it just doesn't matter, but for virtual machines I'd just SSDs for everything to get 10-30x the storage performance.  ZFS merged LVM and file systems together into 1 tool. That can make for easier management.  But ZFS was designed by Solaris Engineers, so it is definitely different from what Windows people would have seen.  It is a different way of thinking about storage ... which some really great features.

[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) shows what I consider the ideal LVM setup for a Linux desktop. It also shows some storage commands which are handy to get the different views necessary.  There isn't a single tool that provides all the information needed to understand storage with ZFS or LVM. For straight partitions and file systems, gparted does show everything.

Servers have different storage layout needs that are drive by the purpose for the server and don't have any GUI or typically any end users.

Backups - Windows has that entire shadow copy stuff.  By default, Linux doesn't have anything like that. To avoid copying/backup a file while it is being written by multiple processes, LVM and ZFS support snapshots. These freeze specific storage blocks so they cannot be modified as long as the snapshot exists. This is handy for backups, but also before doing any upgrade.  Create a snapshot, then do the upgrade. If the upgrade fails or breaks something very important, reverting to the snapshot is 1 command and instantaneous.  Snapshots don't replace backups, but backing up storage frozen inside a snapshot **is** a best practice for backups.

So you have some decisions to make and probably some reading to do.

---

### Post by netrix-g on 2021-03-23
> **CatKiller said:**
> You should be aware that you've chosen to use [Logical Volume Management]("https://opensource.com/business/16/9/linux-users-guide-lvm") rather than normal partitions. You'll want to use LVM tools rather than partition tools to administer them.

It's not something I've played with, but I know that TheFu is a fan.


Thanks for the heads-up Catkiller - a reinstall is on the cards !!

Regards

Netrix

---

### Post by netrix-g on 2021-03-23
> **TheFu said:**
> Yes. I like LVM.  These days, if I were just starting out again (pondering being young again.... ) I'd probably learn ZFS instead.  ZFS on Linux really isn't ready for OS use (booting the OS), but it is excellent for data storage needs.  ZFS doesn't use RAID hardware.  It like ECC RAM, which any real server should have.

As a server guy, you've probably used Veritas Volume Management already.  LVM is like that.  LVM has 3 objects that are used for management.  PV, VG, LV.  For nearly all uses, an LV can be considered a normal partition just like you already know - it is just logical and very flexible.  In reality, normally we'd make a PV use an enter partition, then put a VG into the PV, then have 1 or 50 LVs from the VG. LVM improves performance, which is counter intuitive.  Creating a new file system on a partition could take 5-120 minutes. It is 5-60 seconds if LVM is used, assuming the same size and file system is selected. Counter intuitive. LVM brings all sorts of features, but there is 1 negative - complexity.  Being able to move storage to a new disk WHILE THE OS KEEPS RUNNING can be done with LVM (look up **pvmove**). With hot-swap disks, zero downtime involved. That's important for enterprises. That's just 1 of the features. There are 50 others.  That's the $2 overview.

Ok ... onto the layout stuff. How to split up the different parts of the system?

Generally, the OS partition/LV, /, should only get 25-35G. The 149G shown above is 5x more than I'd ever need. When it comes time to upgrade to a new release, keeping the data separate from the OS is very handy.  Having room for 2 different OSes is also handy.  So, instead of (1) 149G partition for 1 OS, I'd consider
[LIST]
[*]35G - Linux 1 OS [currenly used Linux]
[*]35G - Linux 2 OS [testing for new Linux]
[*]4.1G - Linux swap (shared by all)
[*]50G - /home ... to start. May want to add more as needed, later.
[*]700MB - /boot ... /boot may or may not need to exist. With LVM and encryption, a separate /boot is mandatory. This is where init boot stuff and the kernels go. If it gets full during a kernel upgrade (which happens a few times every month), then a system may not boot. Don't let this fill up. Normally, only 350MB is used, but if full, this is a huge hassle for everyone to fix - much worse for people new.
[*]200MB - for the FAT32 EFI partition. I think the default is 500MB. I've never seen more than 10MB actually used, but my setups are simple. 200MB is probably 10x larger than needed.
[/LIST]

Splitting off /var and /home from the OS is often smart. LVM can help with that, but it isn't really beginner friendly....................................

Wow !! thank you for your time there TheFu! Muchio appreciated ......
Unfortunately I do not understand most of it other than to have learned I need to reinstall the OS to get back to having "normal" partitions and then maybe have a chance of setting up an Ubuntu server. I have little prior "server knowledge" - my end goal is to try and emulate my Qnap NAS with my own Linux server - Time Machine backups, Plex server, CCTV storage - maybe a web server and maybe, if it can be done post Ubuntu install, stick a Windows VM on it. 

If I can get some more hardware to enable me to squeeze a decent graphics card in I might even run a few games on it.

I'll obviously have a learning curve for "normal" partitions, and setting up a 2nd instance of the OS for testing etc - but I do understand some of the jargon and acronyms already which I think will flatten out the curve a bit.

Thanks again the the pointers

Regards

Netrix

---

### Post by LHammonds on 2021-03-23
Here is something for you to read and all the commands to play with LVM

[https://hammondslegacy.com/forum/viewtopic.php?p=811#p811](https://hammondslegacy.com/forum/viewtopic.php?p=811#p811)

---

### Post by volkswagner on 2021-03-23
I don't think you need to reinstall at all.

LVM is the way to go for most servers. The flexibility it affords is great.

The fact that you have ~299Gigs in your Volume Group but roughly only
half allocated to block devices is okay. This allows you free space to create
new Logical Volumes/partitions or extend the size of existing partitions.

The fact is when starting a new server (bein experienced or novice) you may
not know exactly how much to allocate to /var /usr /home, etc. LVM affords
you the opportunity to start small, then extend as needed.

You will want to plan for your large disks. Create the RAID array (I like
raid 10 for speed + redundancy) but your needs may dictate otherwise.

Please post the output of your disk layout and consumption.

```
df -h
```
```
mount
```

Let us know how you'd like to allocate your large data array and
we can offer advice.

Again, I don't think you need to reinstall. Even if you decided
you'd like to add /var partition (or other) you can still do that by booting a 
live linux "CD" after creating the LVM. You would boot a live image, mount
/ and your new logical volume, copy the data, rename /var then add
the entry to fstab. Once you reboot and all is happy, you can delete
your renamed var directory to recover the used space.

The above is a general example and I'm not saying you need to create
a dedicated /var partition. It's just information to let you know you're
not stuck with your current install. It's all very flexible and you can
work with it while learning a whole lot. Folks are here to help
with specific questions.

---

### Post by netrix-g on 2021-03-24
> **LHammonds said:**
> Here is something for you to read and all the commands to play with LVM

[https://hammondslegacy.com/forum/viewtopic.php?p=811#p811](https://hammondslegacy.com/forum/viewtopic.php?p=811#p811)


Thanks for the link LHammonds - I had a cursory glance just now but alas have to sign on for work soon - I think with ThFu's post, your link and Volkswagner's post I will give LVM a go. I literally had my Ubuntu USB stick in my hand this morning ready to reinstall :)

Thanks for you help - I will need more !!

Regards

Netrix

---

### Post by netrix-g on 2021-03-24
> **volkswagner said:**
> I don't think you need to reinstall at all.

LVM is the way to go for most servers. The flexibility it affords is great.



Thanks for your advice volkswagner - along with TheFu's post and the link from LHammonds I will give LVM a go !

I do not have the large disks to hand yet, but will be back when I do ! 


Regards

Netrix

---

### Post by netrix-g on 2021-03-24
A quick question if I may - I am going to give LVM a go....

Regarding setting up a VM - Would or could I add a Windows VM to the current Ubuntu 20.04 setup or should I be installing a VM "host" (VMware ?) first, then install Ubuntu as a VM and then install Windows as a VM ?
This is only for play/learning - I have a copy of Windows7 lying around (don't laugh) but I would like to understand the VM concept a little more.

Thanks in advance

Regards

Netrix

---

### Post by LHammonds on 2021-03-24
If you want to make it a virtual server host, then you need a hypervisor such as VMware ESXi or Linux KVM such as [Proxmox](https://proxmox.com/en/downloads/category/iso-images-pve).

If you go the route KVM route, there are several [management tools](https://www.linux-kvm.org/page/Management_Tools) out there but of the ones I looked at, I liked Proxmox the best.

However, a hypervisor needs to be the base OS that is installed so you would need to re-format and re-install for that to happen.

I started to document how to [install and manage Proxmox](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=276) but due to a job change, that got put on hold but not before I got the initial part done.

LHammonds

---

### Post by TheFu on 2021-03-24
> **netrix-g said:**
> A quick question if I may - I am going to give LVM a go....

Regarding setting up a VM - Would or could I add a Windows VM to the current Ubuntu 20.04 setup or should I be installing a VM "host" (VMware ?) first, then install Ubuntu as a VM and then install Windows as a VM ?
This is only for play/learning - I have a copy of Windows7 lying around (don't laugh) but I would like to understand the VM concept a little more.

VM Hypervisors are a question for later. You don't need to answer that today, unless you want to completely dedicate this system to being a VM host.  VMware ESXi and Proxmox are examples of solutions that take over the entire machine - you'd install those, not ubuntu.

But, there are a number of hypervisors that run well on Ubuntu and are stable and fast. There are desktop-centric hypervisors and enterprise versions.

VMware Workstation, VMware Player, Virtualbox are desktop-centric. You won't see those used inside any enterprise data center.

The other 2 families of hypervisors are either KVM or Xen based.  KVM is what almost the entire VPS world uses - Linode, Amazon, OVH - the big players.  Xen was more popular in the 200x times.  Amazon used Xen back then.

I've run Xen for clients and KVM and VMware ESX and ESXi.  My first VM was using VMware Workstation back in the late 1990s. I've never successfully used either Virtualbox running ON Linux nor VMware Workstation or Player.  I did run Virtualbox on Windows systems for a few years.  

These days, I only use KVM with the libvirt and virt-manager addon packages. It is fairly simple and works for places with 5 hosts or less and 50 VMs.  For larger installations, there are more enterprisey solutions that still use KVM as the hypervisor. CloudStack, OpenNebula, oVirt are some examples.

If you are just learning Linux, I think starting out on a VM is the best way. Continue to use the OS you already know as the host, but run a few different Linuxen inside VMs.  This removes all the deep admin skills, since hypervisors present only the most compatible virtual hardware to the guest VMs.  But since you didn't ask that question, I didn't put that forth as a suggestion.  Fighting with hardware is not fun on an OS you don't know or haven't really used extensively.  Get your feet wet - start on a VM learning Linux and have the VM see  hardware that just works.

If nobody said this already - Linux servers don't have any GUI. You probably don't really want to install a Linux server. Install a light-desktop, then load whatever server things you'd like to learn.  Get familiar with using multiple accounts. It is common for each daemon to run under a different userid on Unix. That's part of the security architecture.  Of course, you don't really need to learn this if you just want to know what buttons to press to get something working and not understand the underlying OS, security, etc.  If that is the situation, many commonly wanted services can be installed a docker containers.  That's probably what your NAS did, just in an extremely specific way.  On a server that you run, there aren't mandated places for where docker containers must be placed or how to network them or 5000 other things. Unix is extremely flexible, which can frustrate Windows admins.  Nobody dictates were you must do things for much of the software deployed.  Sure, there are normal locations which are expected, but almost always, those aren't enforced.

I don't think anyone said anything about your planned programs for the box. Really, you'd probably want to make each of those programs a separate VM to logically segment the dependencies.  Long-term maintenance for server that run 10 important programs can be come difficult when 1 of them needs a different version of a core tool that the others can't/don't use.  There are important network design questions if you plan to make any of those services available over the internet too.  A professional system admin always considers risk management when architecting new systems.

---

