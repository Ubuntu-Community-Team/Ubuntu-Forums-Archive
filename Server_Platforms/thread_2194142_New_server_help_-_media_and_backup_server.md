---
title: "New server help - media and backup server"
date: 2013-12-16
forum: Server Platforms
---

### Post by drfox on 2013-12-16
I bought a new HP Microserver N54L to use as a home media server, to back up our family computers' files (my Linux and wife's Windoze), and to back up 3 separate company files. It will be replacing a Netgear NAS which can't decode DVDs.
Questions:
1. RAID: I am familiar with hardware RAID from my company servers. They require identical size HDs. I guess with mdadm software RAID, the HDs can be different sizes. This microserver comes with a 250GB drive. I was planning on adding two 2TB drives for data. I was planning on using RAID 1 for the data, but not for the OS. When I installed the OS on the server, I used LVM. I was not planning on using RAID for the OS, but in reading this forum, it seems I should have configured it with RAID first, then LVM. Comments? Suggestions?

2. Security: how should I handle security? Should I have separate VMs with separate IPs for the backups of the companies (we have a VPN so that would be simple) so that the data is segregated, or would it be better to just make separate "users"?
I don't (or do I?) want security for reading/serving the DVDs and music, but I don't want my grandchildren accessing the backups and other data. 

3. Any other recommendations?  I've been reading this:   
[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)
and this: 
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

Thanks for any and all help!

---

### Post by nerdtron on 2013-12-16
Are you planning to expand storage? If yes, LVM is a must. But I don't think you will be able to add physical drives if you already have RAID configured. I believe the correct way is setup RAID and then setup LVM. But if you just use the whole RAID array into a single LVM, I don't see any advantage for LVM because you can no longer expand the storage physically.

I say, go with this route:
Install the os on the smaller drive, then make a software raid for the 2x2TB drives.
Mount the array as just like normal drive.
If you need to add more storage, say add another 2x2TB drives, make another separate software raid on them and then mount them to another directory.

You won't get to combine the storage of the 2 raid setups but at least you have expanded the storage.

For security, I say you just setup a network share (either samba or NFS) and let permissions do the work for you. Assign each company a user so that they can only access the folder assigned to them.
Also assign a separate folder share for DVD and music wherein everyone can read/access it.

---

### Post by povlhp on 2013-12-17
Have one of those boxes as well, with 4x3TB + the 250GB disk laying in a CD bay.

Install OS on the 250GB disk, and use LVM or ZFS on the hot-swap bays (you can hot-swap enable them by using 3rd party bios).

My setup ended being (after having tested the above) VMWare ESXi 5.5, Ubuntu with Virtual RDM access to the 4 big drives, and other VMWare machines running as a test lab (Win7 + XP + Synology + other stuff for testing). Ubuntu as the main server, sharing disk for all other clients I have (including the on-host VMware hosts).

---

### Post by SeijiSensei on 2013-12-17
> **drfox said:**
> it seems I should have configured it with RAID first, then LVM. Comments? Suggestions?

That's the usual method, yes.

However I don't see much argument for LVM in your case.  It sounds like you will just be using the RAID drives as one big storage area.  I'd just build the RAID1 array and format the whole thing as a single filesystem with ext4.

> 2. Security: how should I handle security? Should I have separate VMs with separate IPs for the backups of the companies (we have a VPN so that would be simple) so that the data is segregated, or would it be better to just make separate "users"?  I don't (or do I?) want security for reading/serving the DVDs and music, but I don't want my grandchildren accessing the backups and other data.

If you back up as root, you can put the images in directory owned only by root.  If you give it 700 permissions, no one without root privileges will be able to access the backups. 

Having separate VMs is overkill for this purpose.

---

### Post by drfox on 2013-12-17
> **povlhp said:**
> 
you can hot-swap enable them by using 3rd party bios

What a great find! Thanks very much!

> **povlhp said:**
> My setup ended being (after having tested the above) VMWare ESXi 5.5, Ubuntu with Virtual RDM access to the 4 big drives, and other VMWare machines running as a test lab (Win7 + XP + Synology + other stuff for testing). Ubuntu as the main server, sharing disk for all other clients I have (including the on-host VMware hosts).

Do you prefer VMWare over VirtualBox? Why?
You don't think that the OS needs to be mirrored, right? One can always rebuild it.
Someone also suggested using a small USB stick for the OS and then you have a DVD and 4 HDs

Thanks again!

---

### Post by CharlesA on 2013-12-17
> **drfox said:**
> I bought a new HP Microserver N54L to use as a home media server, to back up our family computers' files (my Linux and wife's Windoze), and to back up 3 separate company files. It will be replacing a Netgear NAS which can't decode DVDs.
Questions:
1. RAID: I am familiar with hardware RAID from my company servers. They require identical size HDs. I guess with mdadm software RAID, the HDs can be different sizes. This microserver comes with a 250GB drive. I was planning on adding two 2TB drives for data. I was planning on using RAID 1 for the data, but not for the OS. When I installed the OS on the server, I used LVM. I was not planning on using RAID for the OS, but in reading this forum, it seems I should have configured it with RAID first, then LVM. Comments? Suggestions?

That's the usual way to do it RAID then LVM. I recently moved from a cheap "hardware" RAID card to an actual hardware RAID card (LSI 9260 8i) which is running a RAID6 for my data. If you are just going to run the OS drive as a single drive it shouldn't matter that it made it an LVM volume instead of RAID.

> 2. Security: how should I handle security? Should I have separate VMs with separate IPs for the backups of the companies (we have a VPN so that would be simple) so that the data is segregated, or would it be better to just make separate "users"?
I don't (or do I?) want security for reading/serving the DVDs and music, but I don't want my grandchildren accessing the backups and other data. 

I'm going to echo  SeijiSensei's suggestion about storing the company files in a folder owned by root. You could go one step further and encrypt the files so they will be unable to be read, but that's up to you. For anything work related, I would look at encryption.

> 3. Any other recommendations?  I've been reading this:   
[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)
and this: 
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

Thanks for any and all help!

No idea. My server has been set up, broken, rebuilt, migrated and all that good stuff so many times I have lost track of how I even started it except that it was using Ubuntu 9.04 and webmin. Now I'm running Debian Wheezy with Proxmox (OpenVZ + KVM) for Virtualization.

I did fine this page: [https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) very helpful when setting up LVM.

---

### Post by drfox on 2013-12-18
Thanks everyone. I wound up taking a 500GB drive I had lying around and using RAID1 to mirror it to the 250GB drive the server came with. I found this tutorial very helpful in configuring RAID over LVM (but I didn't encrypt anything):
[http://www.itfromscratch.com/install-ubuntu-server-12-04-with-encrypted-lvm-on-raid1/](http://www.itfromscratch.com/install-ubuntu-server-12-04-with-encrypted-lvm-on-raid1/)
Thanks to povlhp for his tip on configuring hot swap. I used this information:
[http://terfmop.co.uk/blog/2013/07/31/allow-hot-plug-sata-and-5th-sata-port-full-speed-on-hp-n54l-proliant-microserver/](http://terfmop.co.uk/blog/2013/07/31/allow-hot-plug-sata-and-5th-sata-port-full-speed-on-hp-n54l-proliant-microserver/)
I'm planning on adding two 2 TB drives for office data and will probably either VM our home stuff or VM the offices to keep stuff segregrated.
It's a work in progress and I'm sure I'll be needing some other help, but thanks for all your replies!

---

