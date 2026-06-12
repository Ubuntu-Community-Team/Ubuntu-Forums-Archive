---
title: "Current Recommendations for Installing Server Software?"
date: 2023-01-10
forum: Server Platforms
---

### Post by snarke on 2023-01-10
My apologies if this is the wrong place to ask this question: I will be happy to move it if I have chosen the wrong forum.


I've been running my own web server, DNS server, mail server, and various other servers on a rack-mount machine at home for about two decades. I def. remember installing Ubuntu 2004.04 LTS, for example. Back in the dark ages, one just, well, installed things. I have migrated up from '04, as you might expect, and have upgraded the hardware more than once.


Well, it's time to do it all again. I think my current server is running Ubuntu '16 or maybe '18 LTS, but the current server has some weird hardware quirks, so it's getting retired. It's also booting into/off of an mdadm software RAID6 array, which is only one of a handful of reasons why I'm planning on doing a clean install on the new machine, then porting things over one application at a time, as opposed to an upgrade of the current install. File server, AppleTalk, backup, Postgres, Postfix, Apache, Ruby (and some web sites running on it), and so forth and so forth and so forth.


Now, since I first started doing all this, there've been a few changes in best or recommended practices. Virtual machines, Docker, a new kernal or two; I don't even know what all has been invented since I started, since I don't do IT for a living any more; I'm a composer and artist these days.


So my question is: is there a better/smarter/safer/easier to maintain way of setting up a multi-application Ubuntu server besides just installing everything right into the main/root system, and if so, how should it be organized?


About the hardware: the new machine is a cute little Dell PowerEdge R210. 16 GB RAM and a 128G SSD drive. Most of the storage will be provided by a hardware RAID box, a Dell PowerVault with about 15 terabytes of available storage, connected with a dedicated gigabit ethernet cable and iSCSI. I'm not doing anything that should strain the system, so there's no reason to be worried about performance limitations. At some point I might put a rotating drive inside the server itself to mirror the boot drive, but for now, the SSD drive ought to be sufficient.


The system's behind a typical home router, with specific ports opened for the outward-facing servers (as opposed to putting the server in a DMZ, for instance). My instincts say that running a separate virtual machine for outward-facing servers might be a good idea, but do I want to run, say, the netatalk (AFS/apple file services), backup server, and other local services in the main partition, in another virtual machine, or should each one get its own "box"? (That seems inefficient, but again, just guessing here.)


Hopefully you can tell I probably don't need somebody holding my hand and walking me through the whole process. I'm just looking for general guidelines. Easy to set up and easy to maintain has higher priority than efficient or secure, although normal appropriate security still should be there, of course.


Finally, there's probably more than one good way to do this. I don't have to have the best possible totally optimal solution, just some advice for taking advantage of all the new-fangled-ness that's come along in the past decade or so. Thanks!


I haven't actually tried anything yet. I've downloaded Ubuntu 22.04 LTS and will be installing it on a USB drive in order to set up the server in the next day or so. Once I get the base system in place, then I have to decide what to do next.

---

### Post by SeijiSensei on 2023-01-11
I just rent virtual machines from [Linode]("https://www.linode.com/products/shared/"). I'm no longer required to make sure I have continuous power, Internet, and drive space. You can run a full-blown server with mail, web, DNS, PostgreSQL, and various other things for $5-10/month depending on the amount of storage you need. Extensive management tools as well, and nightly snapshot backups for a few bucks more.

I'm running instances of Ubuntu 20.04 and 22.04, along with a CentOS machine that uses legacy software.

---

### Post by snarke on 2023-01-11
Thanks for the pointer, but I will still need the home server for file serving and backup serving. Since I'm running the server anyway, I can save the $120 and have (as noted) all the storage I could possibly want. I've tried redeploying to a hosted solution before. AWS was just completely baffling, in that nearly every function I wanted had been renamed or redesigned to be unfamiliar. The time before that, the service claimed that I could put incoming mail filters/sort rules in place, but after spending a day or so testing, I determined that my rules *only* worked in their test environment, but did not work when actually deployed. Some of my web sites are dynamic, running custom Ruby code with a variety of Ruby-based support libraries. The time it takes even to identify what terminology is currently used to describe what I'm looking for is not insignificant (nobody calls it CGI any more, for instance), and figuring out if I can actually *do* that on a particular service is also time-consuming. For now, I'd rather just keep most of it here where I can get my hands on it.

---

### Post by QIII on 2023-01-11
Support request, not chat.

Moved to Server Platforms as a more appropriate sub-forum.

---

### Post by TheFu on 2023-01-11
> **snarke said:**
> My apologies if this is the wrong place to ask this question: I will be happy to move it if I have chosen the wrong forum.
 Seems like a good place "Server Platforms". Don't know if this was relocated from Chat or elsewhere. Doesn't matter.

With the questions you've asked, you'll get lots of opinions based on the different experiences of each responder.  They will all be valid ... well, most of them.

> **snarke said:**
> I've been running my own web server, DNS server, mail server, and various other servers on a rack-mount machine at home for about two decades. I def. remember installing Ubuntu 2004.04 LTS, for example. Back in the dark ages, one just, well, installed things. I have migrated up from '04, as you might expect, and have upgraded the hardware more than once.

Since around 2005, enterprises have been putting different systems onto virtual machines. Where I worked back then, we weren't allowed to run anything directly on hardware without lots of architecture variance signoffs, which were seldom granted.  I throught the first Ubuntu release was in 2006, no matter.

> **snarke said:**
> Well, it's time to do it all again. I think my current server is running Ubuntu '16 or maybe '18 LTS, but the current server has some weird hardware quirks, so it's getting retired. It's also booting into/off of an mdadm software RAID6 array, which is only one of a handful of reasons why I'm planning on doing a clean install on the new machine, then porting things over one application at a time, as opposed to an upgrade of the current install. File server, AppleTalk, backup, Postgres, Postfix, Apache, Ruby (and some web sites running on it), and so forth and so forth and so forth.

Don't run any unsupported distro.  16.04 support ended 2 yrs ago. 18.04 support ends in March.  5 yrs of standard support is normal for Ubuntu LTS releases.  That means you can skip every other LTS release, if you want to minimize forced upgrades.  Upgrades are possible, but introduce all sorts of undesirable cruft. Every 2-4 yrs, Canonical has drastically changed how at least 1 if not 5 subsystems work and are configured.  Only a fresh install will prevent confusion (system and human) so when you ask questions and say which release you are running, people will assume the "new" way for that release is being used, not the 1-2 LTS release prior method.  Best to avoid all that cruft by doing fresh installs, then migrating the daemons over with any data.  This isn't as complex as it seems anymore.

> **snarke said:**
> Now, since I first started doing all this, there've been a few changes in best or recommended practices. Virtual machines, Docker, a new kernal or two; I don't even know what all has been invented since I started, since I don't do IT for a living any more; I'm a composer and artist these days.

Virtual machines were a way of life the last 20+ yrs.  Since around 2010, Linux Containers have been viable for certain classes of needs.  There are 10+ different VM hosts and 10+ different Linux Container systems.  Each has pros and cons.  Going with the most popular isn't always smart, especially if the most popular option has poor security defaults.  Just sayin'.

> **snarke said:**
> So my question is: is there a better/smarter/safer/easier to maintain way of setting up a multi-application Ubuntu server besides just installing everything right into the main/root system, and if so, how should it be organized?
YES!  Your physical machine shouldn't really have much directly installed onto it.  A mix of VMs and Containers would be recommended.  You are probably aware of how incompatible software stacks can get in the way and prevent correct maintenance of an OS and applications.  That's a key reason why we want each major application to be in a self-contained environment like a VM or a linux container.

> **snarke said:**
> About the hardware: the new machine is a cute little Dell PowerEdge R210. 16 GB RAM and a 128G SSD drive. Most of the storage will be provided by a hardware RAID box, a Dell PowerVault with about 15 terabytes of available storage, connected with a dedicated gigabit ethernet cable and iSCSI. I'm not doing anything that should strain the system, so there's no reason to be worried about performance limitations. At some point I might put a rotating drive inside the server itself to mirror the boot drive, but for now, the SSD drive ought to be sufficient.

SSDs don't really fail very often, just mark down to check the TBW every year, so you can predict when a replacement will be needed prior to any issues.  Running SMART tests weekly and long SMART tests monthly is standard too.  Script that.  15TB really isn't much anymore considering we can get 16TB or 18TB HDDs for under $300.  RAID1 1 of those and have a 3rd for versioned backups. That would be cheaper and use less power than an iSCSI NAS.  Access will be faster too.  Just sayin'.

> **snarke said:**
> The system's behind a typical home router, with specific ports opened for the outward-facing servers (as opposed to putting the server in a DMZ, for instance). My instincts say that running a separate virtual machine for outward-facing servers might be a good idea, but do I want to run, say, the netatalk (AFS/apple file services), backup server, and other local services in the main partition, in another virtual machine, or should each one get its own "box"? (That seems inefficient, but again, just guessing here.)


Get a better router ASAP.  You don't want typical home routers if it is part of your security.  The WAN router should be a hardware device that does 2 things - routing and firewalling.  Perhaps sending SNMP data to a VM inside your network too.  It shouldn't do VPNs or reverse proxies or anything else.  You probably will want separate LAN subnets to aid with security.  I run OPNSense on an APU2 and expect to get 10 more years from that fanless 12W AMD64 device. Not bad for $150 all in from 2015.  Other router options would be Microtik and Ubiquiti stuff and if you need to be really cheap, but care about security, Some $80 Asus routers have excellent support.  Other routers are mostly miss when it comes to support, I'm sad to say.  I know that OPNsense patches are released every 2 weeks or so.
Definitely don't do a DMZ. Good call.
You'll want a separate VM for each high-risk service.  You may want to use a linux container for some of those. Containers are 1/10th as heavy as VMs.
I'd never have my backup server on the same physical hardware as any internet facing server.  That's just not a good idea, IMHO.
If you can, I'd put each LAN service into a separate container.  Ubuntu has LXD/LXC containers. These can mostly be treated like a VM, with some restrictions on what they can/cannot do.  You'll not run a VPN or NFS inside any container.  Well, you can, but you shouldn't for many reasons. Basically, if there is need of a special kernel driver or module, then don't use a container. Put that into a VM.  I've used most hypervisors over the decades.  In 2010, I started looking at KVM/QEMU and in 2011, we switched from VMware ESXi and Xen to KVM/QEMU for servers and in 2014, we moved from VirtualBox/VMware Workstation/Player to KVM/QEMU as well.  If you want a pretty GUI, then Xen has a pretty webGUI that can be impressive.  

If you want a "cluster" of VM servers that allows moving VMs back and forth, you'll need that SAN and probably want to look at Proxmox.  Proxmox takes over the entire system, so it won't be a workstation too.  If you think you'll want 2 systems for redundancy, it is worth a look.  If you'll have 3+ physical hypervisor systems, then Proxmox is still a consideration, but you can do it with KVM/QEMU and allow replicated block storage on each system via Sheepdog to provide redundant storage.  The Proxmox method would be more point-n-click.

> **snarke said:**
> Hopefully you can tell I probably don't need somebody holding my hand and walking me through the whole process. I'm just looking for general guidelines. Easy to set up and easy to maintain has higher priority than efficient or secure, although normal appropriate security still should be there, of course.
It will be your mess, so your choices will only cause yourself pain. ;)
In general, you don't want to allow home-user-only systems to be available over the internet without a VPN.  Essentially, only open the VPN port and nothing else.

If you are hosting your own email, might I suggest a tiny email gateway server on the internet, but keep the main email server internal, only accessible from the LAN or using the VPN? That's what I do. After seeing thousands of attempted imaps logins coming from Russia, I decided forcing the employees to connect to the VPN was required.  The CEO was pissed, so I emailed him the logs of all the attempted logins for his email account for 1 day and he got behind my choice immediately.  I made the VPN a 1-button thing on his phone. That was key to making him accept it.

> **snarke said:**
> Finally, there's probably more than one good way to do this. I don't have to have the best possible totally optimal solution, just some advice for taking advantage of all the new-fangled-ness that's come along in the past decade or so. Thanks!

There are 500 ways. ;)
Split up the services that are internet facing and LAN-only facing.  Plan to put those on different subnets.  Setup wifi and IoT subnets for the LAN too. Neither should be trusted.  This is an FBI recommendation. Put the kid's gaming systems on the untrusted IoT subnet.

> **snarke said:**
> I haven't actually tried anything yet. I've downloaded Ubuntu 22.04 LTS and will be installing it on a USB drive in order to set up the server in the next day or so. Once I get the base system in place, then I have to decide what to do next.

If you aren't certain about storage, do yourself a favor and check the "Use LVM" box during your install.  You'll thank me later.  When you finish the install, assuming you don't pre-setup the PV, VG, and LVs for the most important needs, you'll want to reduce the "root" LV to about 35GB, add LVs for /var, swap, and /home as a minimum.  Size them to be only large enough for your immediate needs.  Extending LVs is 5 seconds and the system keeps running, assuming their is storage available in the VG.  KVM/Libvirt can create LVs for each VM as part of the new VM setup process. That's extremely handy.  Same for Linux Containers that are managed by libvirt.  With LVM, you can do proper snapshots like Veritas VM does and backup completely frozen blocks to avoid any backup corruption, provided there is room for the snapshots.  In short, never allocate the entire VG storage to LVs.   I try to have less than 50% allocated when new for the greatest flexibility in the future.  Here's an idea of what's possible:
```
nvme0n1                             465.8G disk                        
&#9500;&#9472;nvme0n1p1                            50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                           600M part ext4                   /boot
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9500;&#9472;vg00-swap                         4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                      35G lvm  ext4                   /
  &#9500;&#9472;vg00-var                           35G lvm  ext4                   /var
  &#9500;&#9472;vg00-home                          26G lvm  ext4        home       /home
  &#9500;&#9472;vg00-ubuntu2204--srv               15G lvm                         
  &#9500;&#9472;vg00-xubuntu22.04                  40G lvm                         
  &#9500;&#9472;vg00-test                          10G lvm                         
  &#9500;&#9472;vg00-ubuntu22.04--srv--2           15G lvm                         
  &#9492;&#9472;vg00-xubuntu22.10                  20G lvm                         
```

vg00 is the VG.
LVs are var, home, root-00, swap, and the rest are LVs for different virtual machines.
With LVM, there's no need to deal much with partitions.  My /var partition is so large because sometimes I need to drop a file-based VM onto the system to try out stuff.  If I'm creating the VM, I'll use LVM for storage.

VMs are handy for many reasons.  They are great for system migration testing.   Learning new storage techniques like how to use vgmove/pvmode to completely migrate storage to a new disk. Practice resizing running disks. Things like that.

BTW, you probably will want a few NICs in different PCIe slots of the physical system, so you can do PCI passthru for the NICs for high risk VMs and not mix traffic on different security networks on the same physical networks.  All security begins with network design and architecture.

I've probably babbled enough.

---

### Post by TheFu on 2023-01-11
If you are a software developer, then having production and pre-prod and dev systems separate, in different VMs/containers is important.  There's only so much that rbenv/rvm can do.  On the production system, you really don't want to place development tools and tools that aid bad-guys, right?  It is also nice to promote from the DVCS into pre-prod, get that all working perfect, before changing 1 thing and promoting into prod the specific branch desired.

---

### Post by MAFoElffen on 2023-01-12
+1 with TheFu... On using VM's, Subnets, LVM and separately things out. What he recommended aligns with what I would.
Mine is similar, but on ZFS instead of LVM...
```

bpool                                              253M  1.50G       96K  /boot
bpool/BOOT                                         252M  1.50G       96K  none
bpool/BOOT/ubuntu_2cwpns                           252M  1.50G      252M  /boot
datapool                                           533G  2.99T       96K  none
datapool/DATA                                      533G  2.99T      533G  /data
rpool                                             10.8G   881G       96K  /
rpool/ROOT                                        6.26G   881G       96K  none
rpool/ROOT/ubuntu_2cwpns                          6.26G   881G     3.91G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   881G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   881G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   881G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      2.35G   881G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   881G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  2.28G   881G     2.15G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   881G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    168K   881G      168K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              95.5M   881G     95.5M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             39.9M   881G     39.9M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                  64.0M   881G     64.0M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   881G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.42M   881G     1.42M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   881G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   881G       96K  /var/www
rpool/USERDATA                                    4.58G   881G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.58G   881G     4.58G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.09M   881G     1.09M  /root

mafoelffen@Mikes-B460M:~$ lsblk | grep -v 'loop'
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    0   7.3T  0 disk 
&#9492;&#9472;sda1        8:1    0   3.6T  0 part 
sdb           8:16   0 476.9G  0 disk 
&#9500;&#9472;sdb1        8:17   0    16M  0 part 
&#9500;&#9472;sdb2        8:18   0 476.3G  0 part 
&#9492;&#9472;sdb3        8:19   0   607M  0 part 
nvme0n1     259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part /boot/grub
&#9474;                                     /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0     2G  0 part [SWAP]
&#9500;&#9472;nvme0n1p3 259:3    0     2G  0 part 
&#9492;&#9472;nvme0n1p4 259:4    0   927G  0 part 


```
I made the jump consolidating 14 servers on metal down to 4 Virtual Hosts back in 2014. Now down to this new one above... Where the KVM guests and my network shares are all in the data pool.

I can do whole lots in virtual that I thought I needed on separate metal a decade ago.

---

### Post by TheFu on 2023-01-12
> **MAFoElffen said:**
> +1 with TheFu... On using VM's, Subnets, LVM and separately things out. What he recommended aligns with what I would.
Mine is similar, but on ZFS instead of LVM...
```

<snip>
```
I made the jump consolidating 14 servers on metal down to 4 Virtual Hosts back in 2014. Now down to this new one above... Where the KVM guests and my network shares are all in the data pool.

I can do whole lots in virtual that I thought I needed on separate metal a decade ago.

1 question.  
Is ZFS ready for use as the boot drive for an Ubuntu Server if someone isn't a ZFS guru?
I have no problem recommending ZFS for non-OS partitions - for data and even for holding VM and Container storage on the host, but I don't think it is there for OS booting.  
I have reservations about using BTRFS on servers too.

For people doing long term server deployments, avoiding complexities and issues before they happen is key.

---

### Post by MAFoElffen on 2023-01-12
> **TheFu said:**
> 1 question.  
Is ZFS ready for use as the boot drive for an Ubuntu Server if someone isn't a ZFS guru?
I have no problem recommending ZFS for non-OS partitions - for data and even for holding VM and Container storage on the host, but I don't think it is there for OS booting.  
I have reservations about using BTRFS on servers too.

For people doing long term server deployments, avoiding complexities and issues before they happen is key.

I recommended they go with LVM2, like you recommended. I'll PM you on the behind the scenes...

---

### Post by #&amp;thj^% on 2023-01-12
> **TheFu said:**
> 1 question.  
Is ZFS ready for use as the boot drive for an Ubuntu Server if someone isn't a ZFS guru?
I have no problem recommending ZFS for non-OS partitions - for data and even for holding VM and Container storage on the host, but I don't think it is there for OS booting.  
**_avoiding complexities and issues before they happen is key_**.

Please excuse my 2cents worth here.
1st the future of zfs-root is in question ATM (That's all I'll say here now), I'm sure things will get sorted out in time, but I'm with you>>> it will take a very experienced zfs user to maintain it. So no I wouldn't suggest it in any forum.
Best to build a good proven foundation, for optimal success, and overall enjoyment.
EDIT: While I'm here this needs to be addressed:
```
 fs: zfs logical: rpool/ROOT/ubuntu_gtwslu/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_gtwslu/var/lib/NetworkManager

```
It's not a file system,  so I'm confused why Ubuntu would use it like that...Not that I know more them but....
```
$ inxi -p | grep zfs
  ID-1: / size: 437.4 GiB used: 4.77 GiB (1.1%) fs: zfs
  ID-2: /boot size: 1.75 GiB used: 262.9 MiB (14.7%) fs: zfs
  ID-4: /home/me size: 437.6 GiB used: 4.96 GiB (1.1%) fs: zfs
  ID-5: /root size: 432.63 GiB used: 2.5 MiB (0.0%) fs: zfs
  ID-7: /srv size: 432.63 GiB used: 256 KiB (0.0%) fs: zfs
  ID-8: /usr/local size: 432.63 GiB used: 512 KiB (0.0%) fs: zfs
  ID-9: /var/games size: 432.63 GiB used: 256 KiB (0.0%) fs: zfs
  ID-10: /var/lib size: 435.31 GiB used: 2.68 GiB (0.6%) fs: zfs
    fs: zfs logical: rpool/ROOT/ubuntu_gtwslu/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_gtwslu/var/lib/NetworkManager
  ID-13: /var/lib/apt size: 432.71 GiB used: 84.8 MiB (0.0%) fs: zfs
  ID-14: /var/lib/dpkg size: 432.71 GiB used: 82.8 MiB (0.0%) fs: zfs
  ID-15: /var/log size: 432.66 GiB used: 28.5 MiB (0.0%) fs: zfs
  ID-16: /var/mail size: 432.63 GiB used: 256 KiB (0.0%) fs: zfs
  ID-17: /var/snap size: 432.63 GiB used: 384 KiB (0.0%) fs: zfs
  ID-18: /var/spool size: 432.63 GiB used: 384 KiB (0.0%) fs: zfs
  ID-19: /var/www size: 432.63 GiB used: 256 KiB (0.0%) fs: zfs

```

---

### Post by snarke on 2023-01-12
> **TheFu said:**
>  I throught the first Ubuntu release was in 2006, no matter.

LOL. I checked. We're both right. The first LTS was Dapper Drake 06.04, but the first Ubuntu release was Warty Warthog, 04.10. 


> **TheFu said:**
>  Running SMART tests weekly and long SMART tests monthly is standard too.  Script that.

Check. Makes sense. 
  

> **TheFu said:**
> 15TB really isn't much anymore considering we can get 16TB or 18TB HDDs for under $300.  RAID1 1 of those and have a 3rd for versioned backups. That would be cheaper and use less power than an iSCSI NAS.  Access will be faster too.  Just sayin'.

Yes, but I already have the PowerVault. I got it for free, but with no drives (the college decommissioning it reasonably felt that they'd need to shred the drives, given what might have been stored on them), and it insisted on official Dell server-certified drives (which I also don't blame it for, since it's trying to be extremely reliable), and those were a bit more expensive even used, so I stuck with the 1TB drives that were generally available. "Already paid for and ready to go" is cheaper than buying new drives. It will use more power, make more heat, and make more noise. But since I have 15 physical drives to work with, I can do RAID6 with hot-swap, so if I'm on vacation and two drives fail, I can come home and there will still be redundancy on the volume. [counts on fingers] Yeah. I'm not doing anything that esp. needs speed. Even the video files that it's likely to serve now and then aren't going to be 4K/blu-ray/latest-greatest level things. 

Also, the server box itself only has space for two drives, and the boot SSD is in one of them, so a different drive solution would mean scrounging up a different rack-mount box to hold them. Do-able, but as long as using the PowerVault NAS clears the "doesn't suck" bar, I think I'll just go with that. 


> **TheFu said:**
> Get a better router ASAP.  You don't want typical home routers if it is part of your security.  The WAN router should be a hardware device that does 2 things - routing and firewalling.  Perhaps sending SNMP data to a VM inside your network too.  It shouldn't do VPNs or reverse proxies or anything else.

Hmm. But our current router is "a hardware device" that's in charge of routing and firewalling. Specifically, a TP-Link Archer A7. Oh, and it's also currently handling the DHCP address pool. The servers and all my wired computers get fixed IPs, but the phones, pads, and other wifi widgets use the DHCP pool. 

I have tried using its VPN capabilities, but I can only get access to one machine, not the whole LAN subnet, despite what it says is supposed to happen. Mind you, FIRST i tried providing the VPN from my current Ubuntu server, but I never managed to get that to work. Not sure if I didn't find the right holes to drill through the firewall, or the server was being moody, or what. For a few years I had a lovely VPN running on a previous iteration of the server, probably the 12.04 LTS machine, over whatever was the alternative to PPTP (I can't recall the other letter-jumble off the top of my head), but I had to move, and everything changed, and I never got it running again. 

I do have SSH access to my current server, so when I need access to LAN resources when on vacation, I can set up a tunnel to that. But that's weird and slow and I have to look up how to do it every time. I definitely am planning to try to get a proper VPN running on the new server, since (I believe) that should reduce my exposure. More on that in a minute....
  


> **TheFu said:**
> You'll want a separate VM for each high-risk service.  You may want to use a linux container for some of those. Containers are 1/10th as heavy as VMs. If you can, I'd put each LAN service into a separate container.  Ubuntu has LXD/LXC containers. These can mostly be treated like a VM, with some restrictions on what they can/cannot do.  You'll not run a VPN or NFS inside any container.  Well, you can, but you shouldn't for many reasons. 

Now we're getting new-fangled, and I have to start paying close attention. :) I should put each *LAN* service in a separate container? But not NFS, which I'm translating to "file sharing." I think most of my file sharing is actually AFS, although the 2008 MacPro and 2012 MacBook Air aren't as picky. [I have quite a bit of lovingly restored or maintained antique hardware. My G4 XServe finally died just a couple of years ago; such a beautiful machine.]

So AFS and the VPN should be set up inside VMs, but Postgres, Apache, CUPS, et cetera can go in containers? I need to go take a quick crash course in containers, but depending on how much isolation they provide, I can see that I might be configuring various services to access other services via IP addresses rather than via pipes or localhost or the other "we're on on the same machine" methods. 



> **TheFu said:**
> I'd never have my backup server on the same physical hardware as any internet facing server. That's just not a good idea, IMHO.

Could you elaborate on that a bit? For years, I ran Retrospect as my backup system. I'd beta-tested it and in return had a copy of the Enterprise version that worked with tape libraries. Back when being able to back up 5Gb onto a tape was actually cool and useful. No, really, it was a thing. Trust me. But I lost Retrospect when I lost the XServe, and I'd retired the tape library years ago, so everything was getting backed up to files on the RAID array instead. 

Currently, except for "my server" (the machine we're basically talking about now), I run a mostly Mac ecosystem, and that means I get to use Time Machine as part of my backup strategy. Well, right now it's all I'm using, but trust me, I do understand that there are still some holes in the safety net. However, what I do get is silent, seamless, hourly backups of 100% (or less if I specifically request it) of the storage on all my desktops and laptops, stored in at least two different places on two different machines. One of those machines is the Ubuntu server, which is storing a separate encrypted disk image for each machine's TimeMachine to use. 

I'm guessing you wouldn't put backup on an internet-facing server because backups hold, well, *everything*, and keeping backups on a machine that is more exposed to malevolent actors is a lot of exposure. I'm not too worried about holding the TimeMachine disk images on this machine, because (AFAIK) Ubuntu can't even read them. This machine will have the files, but does not have the service/app required to access them, even if it had the passwords, which it also does not have. 

If I'm running the backup service on this machine . . . hmm. Ugh. I had planned to add a new backup service to the menagerie, so we could back up the household iPads and phones and whatnot as well, but I don't want to have to add a whole 'nother machine to the rack. 

> **TheFu said:**
>  If you want a "cluster" of VM servers that allows moving VMs back and forth, you'll need that SAN and probably want to look at Proxmox.  Proxmox takes over the entire system, so it won't be a workstation too.  If you think you'll want 2 systems for redundancy, it is worth a look.  If you'll have 3+ physical hypervisor systems, then Proxmox is still a consideration, but you can do it with KVM/QEMU and allow replicated block storage on each system via Sheepdog to provide redundant storage.  The Proxmox method would be more point-n-click.

{blink} Oh, golly. Okay, that one went sailing right over my head. To date, I think the only virtual machines I've ever actually run on my server were there to run Windows for my laser cutter's driver (since replaced) and for the software for configuring the PowerVault. Do I want a cluster? Where would I be moving VMs from and to? I would find Proxmox worth a look if I'm . . . running two hardware boxes for redundancy? Or more? What is a "hypervisor" system? KVM/QEMU would . . . let me have three hardware devices and I could slide VM instances from one to the other, with Sheepdog keeping the different machines' local hardware storage devices synchronized at some level? 

Dang. I think I know how my mom feels when I tell her I'm installing a new server. 


> **TheFu said:**
> In general, you don't want to allow home-user-only systems to be available over the internet without a VPN.  Essentially, only open the VPN port and nothing else. If you are hosting your own email, might I suggest a tiny email gateway server on the internet, but keep the main email server internal, only accessible from the LAN or using the VPN? 

You may indeed suggest that. That's pretty much what I do now, only without the VPN (because, as mentioned, I haven't gotten it working on the current setup). Something went haywire the last time I set up Ubuntu, and Postfix has been unwilling to enable IMAP/S. No way am I picking up email without encryption, so currently, I can only read my email when I'm home and on my LAN. It would be [very] nice to be able to check my email when I'm not home, but my plan has been to do that by getting VPN working rather than by enabling direct mail access. 

My current ISP is CenturyLink, and although we have glass fiber to the house, they're selfish [expletive deleted] in other ways, one of which is that they assassinate all incoming packets on port 80 or 25. Thankfully, there's a very very nice guy who runs a free reflection service, so all my inbound email goes to his machines, then comes to mine on a different, non-embargoed port. Outbound SMTP goes to CenturyLink's mail servers, and then onward. 

> **TheFu said:**
> Split up the services that are internet facing and LAN-only facing.  Plan to put those on different subnets.  Setup wifi and IoT subnets for the LAN too. Neither should be trusted.  This is an FBI recommendation. Put the kid's gaming systems on the untrusted IoT subnet. 

Hmm. I think this mostly makes sense. It makes more sense if I remember that all my internet-facing services are running in their own boxes, so giving them all their own IP addresses is easy-peasy. (yes?) But Postfix will need to be set up for both networks? We don't have any gaming systems in the house, so I can paper over that part, nor do we have much (any?) in the way of Things. There's one TV that can "do" internet, but it's not currently plugged in. Everything else is iPhones or higher. I'm not sure what you mean about not "trusting" the wifi, though. My MacBook Air can't do anything but WiFi, and it needs to get to files on the file server, so the WiFi address pool is part of the DHCP block and part of the primary LAN block. (I'm using 10.10.x.x/16) 

> **TheFu said:**
> {Discussion of LVMs}

Oh, thank you! When LVMs first appeared, I was all "what, you made this MORE complicated?" I eventually figured out what they were, but how to use them was super-unclear, and most "hey, here's how you should set up your system" guides would just say "do it like this" with no explanation at all as to why. 

So, hmm, let's see. I have the 128G SSD and the 15T NAS. I could fuse them into a single logical volume, but I'm pretty sure I don't want to do that. Do I want my swap on the SSD? If I'm swapping a lot, the speed would be really good, but if I'm swapping a lot, it could potentially wear out the SSD. My current server has only 2Gb RAM, and I don't think it swaps all that often, so swap on the SSD.  

So the SSD is going to have a couple of actual partitions, because the boot code wants a real partition all to itself, but whatever's left becomes a virtual drive that in turn can be divided up into LVs. One of those will be /swap. Another will be /. 

Huh. I can't remember how I did this last time I set up the PowerVault. I think it's possible to have the iSCSI bits initialize early enough that it would be possible to have / be on the NAS, but that would mean the iSCSI has to be folded into the EFI part of the process. Since I'm *not* booting off the NAS, do I need to do that anyway, or can it get mounted later? Or does 22.04 include all that in the kernel anyway, so I don't even have to worry about it? 

Anyway. The NAS gets most of its space blocked out as a big virtual drive, and I start slicing off bits as needed for VMs. Containers don't need LVs?



> **TheFu said:**
> BTW, you probably will want a few NICs in different PCIe slots of the physical system, so you can do PCI passthru for the NICs for high risk VMs and not mix traffic on different security networks on the same physical networks.

It's a 1U server with 2 built-in NICs and one slot. I think the slot is going to be needed for a video capture card; not sure yet. It would seem to me that the biggest danger in putting different security networks on the same wire is if somebody has physical access, so they could put a sniffer on it or set a machine to be promiscuous. (I am under the impression the router won't put out-of-network packets onto the WiFi.) My physical wired network is basically two rooms, one of which is my bedroom. I put intrusion fairly low on my list of vulnerabilities. By the time they can access the physical network, then can just take the server. :)

Which is not in any way to say I do not greatly appreciate you taking time to give me your opinion. This was exactly what I was hoping to get, and I think it will be extremely helpful as I set this thing up. When I push back against your recommendations, it is mostly so you have a chance to say "oh, you might THINK that, but that's actually a terrible idea, because [assumption X] is not correct," or something like that. 

I installed Ubuntu 22.04 on the machine a few days ago. Now I need to go back, make sure the drive is LVM'ed and/or otherwise partitioned appropriately, shrink the / partition down to leave a bunch of elbow room for other stuff, and get the NAS volume connected, mounted, and partitioned.  In the meantime, there's another question I'd like to tack onto the corkboard. See next message....

---

### Post by snarke on 2023-01-12
I believe all your statements are true. But, I am no longer a software developer. Once things are up and running, the actual code on the server (not including security updates) might not change at all for months. If I configure my drives as you suggest, I should have a pool of free space to spin up a dev VM if necessary. At least, that's the impression I'm under. {fingers crossed}

---

### Post by snarke on 2023-01-12
> **TheFu said:**
> For people doing long term server deployments, avoiding complexities and issues before they happen is key.

Yes, absolutely, totally, 100% 

Simple, reliable, secure, and easy to maintain entirely and completely outrank efficient, fast, and flexible. I want a frumpy, boring server. {chuckle}

---

### Post by snarke on 2023-01-12
At some point in the distant past, LDAP became the thing that managed email accounts on my mail server. Now, there's only six or seven actual accounts, although there are another 40-50 aliases that get mapped to one of those six, but I think when I was doing mail on my XServe, LDAP integration was the default, and the included management tools made things easy and obvious. 

At some point, mail moved to the Ubuntu system, and nearly every time there's an upgrade, I get to try to figure out how to get Postfix to authenticate the mail accounts with the LDAP server, which is still currently running on an absolutely antique G4 Mac tower. Why? Because my attempts to migrate the LDAP database have been massively unsuccessful, and I've been putting off replacing it because, well, it was at least working. 

LDAP is supposed to be a simple database, but the way one interfaces with it, the commands and protocols, are strange. I am the only person who actually logs in to the server, and I maintain a separate privileged account for that which does not receive email, so my current plan is to not install LDAP on the new server, and instead just make ordinary user accounts for the mail users. Less flexible, I suppose, but I am expecting/hoping it will make setting up the mail server an order of magnitude easier. 

If this plan seems alarming to you, please enlighten me. :)

---

### Post by snarke on 2023-01-12
I have been using WebMin to give me a remote interface to my servers for a long time. About half the time, I find I have to open a command line and edit config files by hand, but when WebMin does let me do what I want to do, it is almost always a lot easier than mucking about with the CLI. (I really wish they hadn't dropped support for Netatalk. Oh, well.)

I am not sure what happens if I containerize or VM my services. Is that going to isolate them from WebMin? Do I need to install a new copy for every service? Should I quit using it entirely? Is there something better? 

Input appreciated.

---

### Post by TheFu on 2023-01-12
> **snarke said:**
> Yes, absolutely, totally, 100% 

Simple, reliable, secure, and easy to maintain entirely and completely outrank efficient, fast, and flexible. I want a frumpy, boring server. {chuckle}

I deploy servers for 3-5 yrs, trying to only do weekly patching, unless something breaks forcing a change.  A "server" can be physical, virtual or a container in my world.

Good luck.

---

### Post by LHammonds on 2023-01-15
> **snarke said:**
> {blink} Oh, golly. Okay, that one went sailing right over my head. To date, I think the only virtual machines I've ever actually run on my server were there to run Windows for my laser cutter's driver (since replaced) and for the software for configuring the PowerVault. Do I want a cluster? Where would I be moving VMs from and to? I would find Proxmox worth a look if I'm . . . running two hardware boxes for redundancy? Or more? What is a "hypervisor" system? KVM/QEMU would . . . let me have three hardware devices and I could slide VM instances from one to the other, with Sheepdog keeping the different machines' local hardware storage devices synchronized at some level? 
I made the switch from physical servers to virtual servers when I thought VMware ESXi was stable enough to match the physical version...and have never looked back.

Using virtual servers provides a WHOLE lot of advantages if you are able to make use of it.

At the peak of my server management career, I was managing just over 100 virtual servers.  I used an IBM BladeCenter with about 8 physical host servers (blades) and a NAS array with a bunch of 8TB SAS drives.

Whenever I wanted to deploy a Linux box, all I had to do was right-click on a template server and deploy it....give it a name and then change the IP to a new static one and let it run any updates it needed since the template was last updated.

When setting up a new OS in a virtual environment for the 1st time, you typically do not have any hardware issues because the hardware that the host presents is the same every time...no driver woes, etc.   You are mainly focused on the OS and not the hardware.   You can also take one or more "snapshots" of the system at various stages during setup and roll back to a prior snapshot in seconds if you make a mistake or want to try a different method/software instead of re-installing the OS from scratch.

As for the purpose of "clusters" that was discussed, if you have 3 physical host servers, you can migrate the VMs they host between different hosts.  This can be helpful to maintain an even performance utilization among all the hosts.  You can also shift all the VMs off one host to the others so you can take the host down for maintenance without any disruption to your services provided by your VMs.  This assumes you do not overload your hosts to a point where the others cannot hold the VMs for the host that needs to go offline.

Regarding backups, they are not useful to you if the "bad guy" can find / access them from a compromised system.   My backup server is separate from everything else and is a black hole of unknowing.  What I mean by this is that no device backs itself up to the backup repository.  At most, the VMs will backup their own data and make it ready for pickup.   The backup repository reaches out to each device and grabs the data.   If any device is compromised in my network, none of them can see or access the backup server.

LHammonds

---

