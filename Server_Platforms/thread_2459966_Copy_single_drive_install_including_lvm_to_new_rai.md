---
title: "Copy single drive install including lvm to new raid array"
date: 2021-03-30
forum: Server Platforms
---

### Post by agent-ibo on 2021-03-30
I am reading instructions about pvcreate and vg create but I'm confused about the process. 

Server Poweredge T410 with H700 controller. 
At the time I installed this I didn't have any caddies so I plugged the ssd into the sata connections in place of the DVD that is connected. 
Ubuntu server currently running on single sata ssd drive with default ubuntu options during installation. 
So pvdisplay give me vg name of "ubuntu-vg"

New Raid 5 array is created by the Raid Controller and there is no mdamdm setup atm. 

I assume that is the first part I need to do is pvcreate /dev/sdb/   However, I get a message that says "device excluded by filter" 

Am I suppose to create partition table and format the drive first ? Is this what this message is really telling me ? 
 
Please advise. Thanks

---

### Post by TheFu on 2021-03-30
I wouldn't use the HW-RAID controller except as a JBOD device. SW-RAID on Linux is much more flexible and part of LVM.  No need for mdadm at all.  HW-RAID is something to avoid for the lack of flexibility and poor handling when the RAID controller fails.

So, start with posting 
```
sudo pvs
sudo vgs
sudo lvs
```
so we get a lay of the LVM land. vgdisplay and similar commands have been old-school for a long time. They provide so much data that the important details are easily lost, unlike the commands requested above.  When posting, please, please, please use code-tags since the data will be in columns. If a column is misread, wrong decisions will be made.  I've shown what it should look like.
Instructions for Code Tags: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

If you already have a PV setup, read up on pvmove.
Then say what you desire for the final configuration.  Often, the solution for RAID is to create a backup of everything, pave and wipe all disks (except the backup), then start fresh.

And when posting errors, please copy/paste the entire line and a few above and below it.  What we will do is to put that into google (just like you could).  I'm guessing that sdb is the raw drive and that whatever the HW-RAID card created/or mdam ... another device has been created and that would be expected to be where you'd point for pvcreate - had you not read my most excellent advice above and already determined that's a bad idea. ;)

---

### Post by agent-ibo on 2021-03-30
Ok, answering my own post so far it seems that there is old gpt table even though I removed the partition from the drive with fdisk. There is still a label for it showing gpt. 

I was able to wipe this using the command wipefs -a dev/sdb
then I created volume with pvcreate /dev/sdb

Now I don't know what to do from here to get the sata drive OS and lvm moved over to the new raid array. 

I assume next step is vgcreate ? but I don't really know.

---

### Post by TheFu on 2021-03-30
> then I created volume with pvcreate /dev/sdb

That's a bad idea.  Always, always, have a partition. Don't do whole disks for lvm or RAID purposes. There are reasons.

---

### Post by agent-ibo on 2021-03-30
> **TheFu said:**
> I wouldn't use the HW-RAID controller except as a JBOD device. SW-RAID on Linux is much more flexible and part of LVM.  No need for mdadm at all.  HW-RAID is something to avoid for the lack of flexibility and poor handling when the RAID controller fails.

So, start with posting 
```
sudo pvs
sudo vgs
sudo lvs
```
so we get a lay of the LVM land. vgdisplay and similar commands have been old-school for a long time. They provide so much data that the important details are easily lost, unlike the commands requested above.  When posting, please, please, please use code-tags since the data will be in columns. If a column is misread, wrong decisions will be made.  I've shown what it should look like.
Instructions for Code Tags: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

If you already have a PV setup, read up on pvmove.
Then say what you desire for the final configuration.  Often, the solution for RAID is to create a backup of everything, pave and wipe all disks (except the backup), then start fresh.

And when posting errors, please copy/paste the entire line and a few above and below it.  What we will do is to put that into google (just like you could).  I'm guessing that sdb is the raw drive and that whatever the HW-RAID card created/or mdam ... another device has been created and that would be expected to be where you'd point for pvcreate - had you not read my most excellent advice above and already determined that's a bad idea. ;)

Ok, so here is what I did so far and I'll post some pics of things. 
I don't know if I'm actually doing things correct but this is what I read and where I'm at in the process. 
Descriptions of what I'm working with are below each step. 

I was attempting to follow this post there: 
[ubuntu - Migrate an entire volume group LVM2 to RAID5 - Unix & Linux Stack Exchange]("https://unix.stackexchange.com/questions/72099/migrate-an-entire-volume-group-lvm2-to-raid5")

**Here is where I'm at so far and what I actually did:**
pvcreate /dev/sdb   
   -this is the drive that consists of the entire raid 5 volume group but is a hardware raid
vgextend /dev/ubuntu-vg /dev/sdb   
  -ubuntu-vg is sda3 lvm and was the default ubuntu server installation option
pvmove -i 10 /dev/sda3    /dev/sdb      
  -I believe this puts the sdb raid 5 into the original vg called ubuntu-vg 
vgreduce /dev/sda3
  -this removes sda3 from the vg which was the original lvm

I have not formatted anything so far. This is because pvcreate requires that no partition or partition table is created otherwise it will error with "this is filtered out. I had to wipefs -a sdb before pvcreate or I get filter error just fyi

After pvcreate I used fdisk to create partition table - type 31 id which is Linux lvm type
 for large drives more then 2gb. Type e8 has 2gb limitation for partition table creation as far as I know. 

**Sooo..... **
*I think I need to do something like this* if I am to complete this project from that linked post above.
 
mount --move /boot /mnt
rmdir /boot
cp -a /mnt /boot
umount /mnt
update-initramfs -u
dpkg-reconfigure grub-pc

I'm really not sure if I am going about this the right way but it's very hard to understand or find consensus on this particular subject. 

**attemped to move /boot but didn't work = **
mount --move /boot /mnt
```
mount: /mnt: bad option; moving a mount residing under a shared mount is unsupported.



``` 
 
[B]Here is some details from the pvs,vgs,lvs:
[/B]```
sudo pvs
  PV         VG        Fmt  Attr PSize   PFree
  /dev/sda3            lvm2 ---  231.88g 231.88g
  /dev/sdb   ubuntu-vg lvm2 a--   <5.46t   5.34t
sudo vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- <5.46t 5.34t
sudo lvs
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 115.94g 

```

I see that there is a ubuntu-lv for LV as shown above. I do not know if I need to worry about this or if this is needed. However, I thought that "reduce /dev/sda3 would have taken it out of the ubuntu-vg "vg"  At least I think so. 

Please advise thanks

---

### Post by agent-ibo on 2021-03-30
> **TheFu said:**
> That's a bad idea.  Always, always, have a partition. Don't do whole disks for lvm or RAID purposes. There are reasons.

I wondered about this. I only considered this since ubuntu created lvm for entire disk by default but likely because the original installation to disk is already small ssd.

I was not intending to keep this server but later decided it's ok for what I'm doing. 
I appreciate any advise on what is recommended sizes for partitions. 

I hope to transfer the entire install to new raid 5 and create recommended partition sizes. 

I feel like I was getting pretty close except that the lvm is the entire raid 5 now
Also I was unable to "pvmove the sda1 and sda2 partitions. 
I was not sure what to do about that. 

Anyhow thanks for the help. I'm sure others will want to know how to do this too.

---

### Post by TheFu on 2021-03-30
> **agent-ibo said:**
>  
I appreciate any advise on what is recommended sizes for partitions. 
I hope to transfer the entire install to new raid 5 and create recommended partition sizes. 
There are 50+ threads about that in these forums already.

> **agent-ibo said:**
>  
Also I was unable to "pvmove the sda1 and sda2 partitions. 
I was not sure what to do about that. 
You can't pvmove non-LVM partitions.

I'm confused.  If you are using HW-RAID, why not just setup the presented drive from ESXi to be the size you want, then do a 20.04 install and use the "do something else" option to setup LVM LVs as you like?  It isn't like the machine is in production now.

Just be certain to use a GPT partition table to get passed the 2G limitation that MSDOS has. Let the installer create the needed /boot, /EFI, and force it to make LVs for "root", "home", "var" and "swap" to start.  Immediately, post-install, you'll probably want to boot from alternate media to reduce the "root" LV to 25G or so. The installer has a nasty habit of putting 200G into "root", on large drives.  This shoudln't be allowed, so fix it ASAP, before reducing the storage could cause data loss. Those are the minimal LVs I'd recommend.  

If the VM will be on the internet, there are some other LVs with specific mount options you'll want for security reasons. Mainly noexec, nosetuid, stuff like that for temporary areas to prevent hackers from having a trivial foothold place ... though they can get around it, many scripts won't. Anything to slow them down a little, right?  I love using read-only mounts for static files used by websites too.  Just another fly in the ointment for their automated scripting.

---

### Post by agent-ibo on 2021-03-31
Thank, I guess I'll just install from scratch. It is actually online but thought that moving the entire install to new raid would be much simpler then this like cloning use to be. However, it appears that cloning lvm is not easy and clonezilla nor gparted can do it.  I would have done this already if I could have.

---

### Post by TheFu on 2021-03-31
> **agent-ibo said:**
> Thank, I guess I'll just install from scratch. It is actually online but thought that moving the entire install to new raid would be much simpler then this like cloning use to be. However, it appears that cloning lvm is not easy and clonezilla nor gparted can do it.  I would have done this already if I could have.

Cloning LVM is easy from 1 PV to another. **pvmove**.
The problem is that the entire setup wasn't just LVM storage. There were regular partitions too - outside LVM's control.

If you wanted to clone those other partitions and perhaps resize them too, then something like **fsarchiver** or even **rsync** could do it. The partitions would need to be manually created first, but that's 20 seconds.  

I don't recall if the system was UEFI or BIOS booting - that would matter for cloning those boot partitions ... and obviously, would need to fix the /etc/fstab for the UUIDs of the new partitions before it would boot.  With a BIOS install, running grub-install and update-grub under a **chroot** to get everything just right is needed.  Not hard, but more steps and details. There could be others that I forgot. It would be clear to me based on the output along the way.

But if there isn't any stuff in the install (or even if there was), backing up the small amount of data, then doing a fresh install is most likely the fastest way.  As for reinstalling packages, make a list of the manually installed packages on the system - **apt-mark** can do that. snaps can use **snap list** ... though not all snaps get manually installed. Some are forced on desktops.  Actually, that would be a good question.  How can we get a list of manually installed snap packages?

Wouldn't hurt to understand more clearly how backup and recovery can be done based of the restore beginning with a fresh install. That's my process. Here's some information about what to get and what order to restore everything: 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

And because we're talking LVM, [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233) is aljames2 backup script that takes advantage of lvm snapshots for backups.  I disagree about taking snapshots at different times - that can lead to a data homogeneity problem, but Al didn't seem worried about that.  

Good, versioned, backups are necessary in these days of file corruption, malware, crypto-locker, and breaches. Oh ... and when RAID fails.

---

### Post by agent-ibo on 2021-04-02
I just did fresh install. I couldn't figure out how to move the /boot over from the terminal. I probably could have done it with gparted but wanted to move on from this. 

I did a fresh install with defaults. I don't really understand this layout.
Where does ubuntu install things ? Looks like everything goes to the 200gb partition unless I direct it to use storage elsewhere ? 

Hardware raid 5 with 3 drives totally 5.46GB 
I don't really understand what I have here but OpenStreamingPlatform is installed and it shows that my drive spaces is like 200gb which is not right. I don't know if this is the fault of opentstreamingplatform or if ubuntu needs to expand it's 200gb size to 5.46TB or something ? 

> 
sudo vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- <5.46t 5.26t
sudo pvs
  PV         VG        Fmt  Attr PSize  PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <5.46t 5.26t
sudo lvs
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 200.00g   


---

### Post by TheFu on 2021-04-02
200G for the "root" LV ... yours is called "ubuntu-lv" is LV abuse. Much too large. See post #7 above. 
The OS doesn't see your RAID as RAID.  It sees it as 1 HDD.

Post **sudo fdisk -l** - use code-tags.  BTW, it would be helpful if you **always** use code-tags for any terminal commands and output. Without seeing both the partitions and the LVM information, we can't say too much.

Or the output from :
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
```
can show an overview of LVs, partitions and physical disks.  For complex LV setups, this can be confusing, however.

---

### Post by agent-ibo on 2021-04-03
I figured out how to lvrextend and then resize2fs so I am able to make the HUGE root filesystem, but wonder if there is any performance issues with doing that vs creating a partition, and another lvm and mounting to something like /var/www/ or something. Instead of just extending the lvm ? Any ideas on this subject ? 
thanks

---

### Post by TheFu on 2021-04-03
Read post #7 and #11 above.
It isn't about performance, it **is** about long term maintenance, flexibility, and backups.
I like to googling for answers like:
 "lvm is great" 
 "lvm pitfalls" 
to get many varied answers.  

LVM is pretty much the same on all Linux systems. Everyone uses the same commands and has for 15+ yrs.  Any tutorial, regardless of distro, will be just as relevant.

LVM is about flexibility and reducing downtime.  Storage architecture is about performance and backups. Mux those two together for a high performance, flexible, backed up, nearly ZERO downtime solution. Only you can do it, since only you know your skills, hardware, workloads.

---

