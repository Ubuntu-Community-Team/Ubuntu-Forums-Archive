---
title: "New UBUNTU Server"
date: 2018-06-21
forum: Server Platforms
---

### Post by mariuszmajcher on 2018-06-21
Hello All

This is my first post on this forum , any way I need some help .
I need to setup new home server with ubuntu server  18.04 amd64.
My configuration is DELL PowerEdge T30 with 1 x hdd 1tb , 2 x hdd 6tb  8gb ram , intel xeon.
In this server I need to have in first disk 1TB :
50GB UBUNTU SERVER SYSTEM
150gb  FILE PARTITION
150GB FILE PARTITION
600GB FILE PARTITION
2x 6TB HDD need to be in RAID 1 configuration becasue I want to use to store files mostly windows based.

I want to use for file storage and ftp storage + www server + 2-3 virtual machines.
 
At this moment biggest problem for me is setup with hard drives basicaly proper configuration ( what type  should be each partition), i know also i need to get swap partition .

Can someon help me with that ?

---

### Post by LHammonds on 2018-06-21
> **mariuszmajcher said:**
> I need to setup new home server with ubuntu server  18.04 amd64.
You have come to the right place.  Make sure you install using the "alternative" ISO image and not the "LIVE" ISO because the "LIVE" image does NOT support customized partitions like LVM or RAID during install.

> **mariuszmajcher said:**
> 
My configuration is DELL PowerEdge T30 with 1 x hdd 1tb , 2 x hdd 6tb  8gb ram , intel xeon.
In this server I need to have in first disk 1TB :
50GB UBUNTU SERVER SYSTEM
150gb  FILE PARTITION
150GB FILE PARTITION
600GB FILE PARTITION
2x 6TB HDD need to be in RAID 1 configuration because I want to use to store files mostly windows based.

Does the server have built-in RAID controller?  If so, you can use that to create the mirror on your two 6TB drives which will perform better.  Or you can go the software route and use mdadm once you get Ubuntu Server installed on the smaller drive.

> **mariuszmajcher said:**
> I want to use for file storage and ftp storage + www server + 2-3 virtual machines.
 You only have 8 GB of RAM so be careful how many VMs you spin up.  You  can do quite a few Linux servers but not many Windows machines which  have a GUI.

> **mariuszmajcher said:**
> At this moment biggest problem for me is setup with hard drives basically proper configuration ( what type  should be each partition), i know also i need to get swap partition.
You do NOT have to have a swap partition anymore...at least not since 17.x.  You can skip creating a swap partition and just swap files which are much more flexible and there is no longer a performance difference when using partition vs file.

I would use EXT4 for most of the partitions.  EXT4 can support 1 exabyte and a maximum individual filesize of 16 TB inside a partition if I recall correctly.

You could use zfs for the larger drives but I'm not sure you would need it for just 6TB.

As for the Ubuntu OS, you can install a bare system comfortably with 25GB and I have [documented how to](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244) use LVM to slice up the partitions on my website as well as how to dynamically add more space as needed.  I also documented how to modify swapfile sizes and placement.

LHammonds

---

### Post by oldfred on 2018-06-22
In addition to LHammonds good info above, TheFu has posted many good threads. You can search forum if you have specific issue. He also has a blog.

       [https://ubuntuforums.org/showthread.php?t=2364817&p=13660695#post13660695](https://ubuntuforums.org/showthread.php?t=2364817&p=13660695#post13660695)
[http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
[http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)

---

### Post by mariuszmajcher on 2018-06-22
Hello and thank you for answer .
I read about it and i have alternative version .
This server have only Intel Rapid Storage Controler 12 so only is possible to use software raid 1 controller, or I need to buy some hardware version(do you have some idea what will be good one ?) , on all forums i read hardware raid1 is much better because didnt use memory and cpu from server .  
So for virtual i need more ram memory, currently i have HMA81GU7AFR8N-UH so i need to buy same 2400mhz from hynix or can be other brand ? I think to buy 8GB extra  or 16GB dependency of price.
 

One extra question , do I have to configure RAID1 during first instalation or I can do it later for does 2 HDD's ?

Regards 
Mariusz

---

### Post by oldfred on 2018-06-22
Do not have server, but everyone says mdadm is better. 

If you use hardware RAID or even BIOS RAID, you really need to buy two. By the time it fails, that specific hardware may not be available and then you may not have access to your data. IF mdadm, you can use any other Linux server or even desktop with severs mdadm software added.

---

### Post by darkod on 2018-06-23
Maybe it's personal preference but I would go with mdadm too. It's HW independent and if the server dies you can read the disks on any machine. Which is not always the case with HW raid controllers.

You do not have to configure the data raid1 during install. Because the OS will not be on it, you can configure that array later.

But seeing your HDD layout, I don't think it's very optimal. You plan to have the OS (plus other partitions) on the 1TB disk, not protected by raid. It will work, but if that disk fails your OS fails. Your data will be protected by the raid1 6TB array, but not reachable if the OS fails. Depending how much downtime you can accept, it is something to think about...

Why not buying another 1TB disk and make two raid1 arrays, one of 1TB and one of 6TB. Then you will use LVM to set up one big continuos space of 7TB.

The root will be a LV inside the LVM. And you can configure any other LVs that you consider necessary. That way you also avoid fragmentation of the space.

It is not necessary but I would also make small 2GB array at the start of the 1TB disks, to be used as /boot raid1. It can be also inside the LVM, but I prefer it outside.

That's what I would do... It protects your OS with raid1 too.

So, the layout would be something like:

On the 2x 1TB disks:
2GB mdadm raid1, ext4, for /boot
1TB (the rest) mdadm raid1, LVM

On the 2x 6TB disks:
6TB mdadm raid1, LVM

Inside the LVM:
32GB LV for /
the rest LVs that you want

You don't need to make / very big (even 32GB is plenty) because in LVM you can easily extend it online. And DO NOT assign all the LVM space to data LVs!!! You can easily extend LV if you have free space in the VG. If you assign all the VG space, it complicates your life...

Start with smaller LVs and extend as needed. That is very easy to do online with LVM.

---

### Post by mariuszmajcher on 2018-06-23
Hello 

Dear  darkod that is good point 1tb hdd cost nothing but safe time in case of crash. 

so now i need to order 1 hdd and 8gb ram.

regards
Mariusz

---

### Post by volkswagner on 2018-06-23
With the additional 1TB drive and the flexibility
of MDADM, you could even create a nice size RAID10
for performance. You may consider this for the underlying
OS and/or for /var/lib/libvirt/images (if using KVM hypervisor) so your VM's get a decent
disk I/O for their OS. This is of course if you can spare the
space on your 6tb disks.

Also consider limiting services on the host OS (just run the hypervisor) and use the VM's to run everything else.

Additionally, get as much RAM as you can afford, especially if you plan to run any Windows or GUI based VMs.

---

