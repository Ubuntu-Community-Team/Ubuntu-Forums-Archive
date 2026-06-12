---
title: "Partition Setup"
date: 2021-04-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Graham1 on 2021-04-09
Hi All

I'm considering changing my Linux setup and curious as to what others are using and why. Currently multibooting between Windows 10 Home and Ubuntu 20.04. Within Ubuntu, running 18.04 (work), 20.04 (test) & 21.04 (daily) in Boxes. 

Thinking of changing to Windows 10 Home, latest Ubuntu LTS (20.04) and latest Ubuntu (20.10, soon 21.04). Looking at using 20.10 for testing and running Boxes (daily build) and LTS for stable/serious stuff. 

My main question is whether I should switch from BRTFS to Ext4 on LTS. Currently using BRTFS for OS, swap and ext4 for home on 250GB SSD. Thinking of splitting to 125 GB (LTS) and 125 GB (latest) using single partitions on each.

:)

---

### Post by TheFu on 2021-04-09
The poll is confusing.  Is an LV the same as a partition for the purpose of this poll?  What about people using ZFS with a single pool, but with many datasets?
```
$ lsblk
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                  1024M rom              
vda                    30G disk             
&#9500;&#9472;vda1                512M part vfat        /boot/efi
&#9500;&#9472;vda2                  1K part             
&#9492;&#9472;vda5               29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--root     17G lvm  ext4        /
  &#9500;&#9472;vgubuntu--swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--home     12G lvm  ext4        /home
vdb                    10G disk             
&#9492;&#9472;vdb1                 10G part LVM2_member 
  &#9492;&#9472;vgubuntu--root     17G lvm  ext4        /
```

What is that for this poll?  There are two disks (virtual), 4 partitions, and 3 file systems + 1 swap.

Or how about this:
```
$ lsblk
NAME                              SIZE TYPE  FSTYPE      MOUNTPOINT
sda                       465.8G disk              
&#9500;&#9472;sda1                      512M part  vfat        /boot/efi
&#9500;&#9472;sda2                      732M part  ext2        /boot
&#9492;&#9472;sda3                    464.6G part  crypto_LUKS 
  &#9492;&#9472;sda3_crypt            464.6G crypt LVM2_member 
    &#9500;&#9472;ubuntu--vg-root        25G lvm   ext4        /
    &#9500;&#9472;ubuntu--vg-swap_1     4.5G lvm   swap        [SWAP]
    &#9500;&#9472;ubuntu--vg-home--lv    75G lvm   ext4        /home
    &#9492;&#9472;ubuntu--vg-stuff      100G lvm   ext4        /stuff
```

Or this one:
```
$ lsblk
NAME                              SIZE TYPE FSTYPE      MOUNTPOINT
sda                             465.8G disk             
&#9492;&#9472;sda1                          465.8G part LVM2_member 
  &#9492;&#9472;vg--hadar-lv--backups       465.7G lvm  ext4        /Backups
sdb                               477G disk             
&#9500;&#9472;sdb1                            731M part ext2        /boot
&#9492;&#9472;sdb5                          476.2G part LVM2_member 
  &#9500;&#9472;hadar--vg-root               32.3G lvm  ext4        /
  &#9500;&#9472;hadar--vg-swap_1              4.3G lvm  swap        [SWAP]
  &#9500;&#9472;hadar--vg-libvirt--lv         175G lvm  ext4        /var/lib/libvirt
  &#9500;&#9472;hadar--vg-lv--vpn09--1804     7.5G lvm              
  &#9500;&#9472;hadar--vg-lv--xen41--1804    12.5G lvm              
  &#9500;&#9472;hadar--vg-lv--blog44--1804   16.2G lvm              
  &#9500;&#9472;hadar--vg-lv--zcs45--1804      25G lvm              
  &#9500;&#9472;hadar--vg-lv--spam3            10G lvm              
  &#9500;&#9472;hadar--vg-lxd--lv              60G lvm  ext4        /var/lib/lxd
  &#9500;&#9472;hadar--vg-lv--regulus          30G lvm              
  &#9500;&#9472;hadar--vg-lv--regulus--2       10G lvm              
  &#9500;&#9472;hadar--vg-lv--opnsense          5G lvm              
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tmeta   108M lvm              
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm              
  &#9492;&#9472;hadar--vg-lv--tp--lxd_tdata  32.2G lvm              
    &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm      
```

I didn't show the complex storage servers with many TBs and RAID. ;)

Rather than multi-boot, why not use VMs?
I'm not a fan of btrfs due to early issues with data loss for some virtual machine configurations. That has probably been solved, but when redhat deprecated btrfs, that spoke to me on data safety. Perhaps it is all better now, but I've moved on to playing with ZFS and f2fs instead.

---

### Post by ajgreeny on 2021-04-09
My gut reaction is definitely to stick with ext4 for all your Linux partitions as it is much more the normal and default filesystem of Ubuntu; certainly there will be many more users here in the forum who can answer queries if you stay on ext4 than if you move to btrfs which many (most?) of us know little or nothing about.

I've nothing to add re your Windows query as I do not use it any more.

---

### Post by Graham1 on 2021-04-09
> **TheFu said:**
> The poll is confusing.  Is an LV the same as a partition for the purpose of this poll?  What about people using ZFS with a single pool, but with many datasets?

Apologies if the poll is confusing :). I've never used an LV setup, so cannot comment on that. My setups are usually simple, just simple primary partitions (nothing fancy). The same with ZFS (never used it). My reason for using BTRFS is for Timeshift. Without that application, I would not use BTRFS. A while back, I posted another poll about the file system used. I was the only person to use BTRFS. I suppose that answers my question but coming from BTRFS and Timeshift, I cannot understand why this setup is not popular (am I missing something).

Regarding my original question about partitions, I would say a single partition includes root, home, swap files, etc. Multiple partitions would included a partition for root, another for swap and another for home, etc.

> Rather than multi-boot, why not use VMs?
I'm not a fan of btrfs due to early issues with data loss for some virtual machine configurations. That has probably been solved, but when redhat deprecated btrfs, that spoke to me on data safety. Perhaps it is all better now, but I've moved on to playing with ZFS and f2fs instead.

As my computer came with Windows 10, made sense to add to it rather than delete a licensed OS. I am using VMs in Boxes on 20.04 but it's not the same as real hardware. 

:)

---

### Post by Graham1 on 2021-04-09
> **ajgreeny said:**
> My gut reaction is definitely to stick with ext4 for all your Linux partitions as it is much more the normal and default filesystem of Ubuntu; certainly there will be many more users here in the forum who can answer queries if you stay on ext4 than if you move to btrfs which many (most?) of us know little or nothing about.

I've nothing to add re your Windows query as I do not use it any more.

Windows is there simply because it came with the computer (I hardly use it tbh). I guess I use BTRFS / Timeshift as a backup (my recovery). Prior to this, Clonezilla. I would still have the recovery on ext4 with Timeshift (but not instant). 

:)

---

### Post by oldfred on 2021-04-09
My partitions:
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk  -o NAME,LABEL,PARTLABEL,SIZE,fsused,MOUNTPOINT | egrep -v "^loop" [/COLOR]
NAME        LABEL     PARTLABEL              SIZE FSUSED MOUNTPOINT 
sda                                        931.5G         
&#9500;&#9472;sda1      ESP_B     EFI System Partition 510.2M         
&#9500;&#9472;sda2      hirsute   hirsute               30.3G         
&#9500;&#9472;sda3      ISO_b     ISO_b                 49.8G         
&#9500;&#9472;sda4      backup_b  backup_b             147.6G 103.3G /mnt/backup 
&#9500;&#9472;sda5      focal_a   focal_a               30.3G         
&#9500;&#9472;sda6      data      data                 302.8G         
&#9500;&#9472;sda7                                       2.1G         
&#9500;&#9472;sda8      groovy    groovy                24.4G         
&#9492;&#9472;sda9      groovy_k  groovy_k                24G         
nvme0n1                                    465.8G         
&#9500;&#9472;nvme0n1p1 ESP_NVME  esp_nvme               512M  11.9M /boot/efi 
&#9500;&#9472;nvme0n1p2 focal_0   focal_0               29.3G         
&#9500;&#9472;nvme0n1p3 focal_k   focal_k               29.3G  10.2G / 
&#9500;&#9472;nvme0n1p4                                 29.3G         
&#9492;&#9472;nvme0n1p5 nvme_data nvme_data            195.3G   140G /mnt/data
[/FONT]
```

Been planning on trying a virtual box or container for test install, but have not yet tried it.

---

### Post by Graham1 on 2021-04-09
My current setup:-

```
NAME   LABEL            PARTLABEL                      SIZE FSUSED MOUNTPOINT
sda                                                  119.2G        
&#9500;&#9472;sda1 SYSTEM           EFI system partition           100M  44.5M /boot/efi
&#9500;&#9472;sda2                  Microsoft reserved partition    16M        
&#9500;&#9472;sda3                  Basic data partition         117.4G        
&#9492;&#9472;sda4 Windows RE tools Basic data partition           1.8G        
sdb                                                  232.9G        
&#9500;&#9472;sdb1                                                37.6G    27G /run/timeshift/backup
&#9500;&#9472;sdb2                                                 9.8G        [SWAP]
&#9492;&#9472;sdb3                                               185.6G  73.2G /home
sdc                                                  931.5G        
&#9500;&#9472;sdc1 Data                                          465.7G        
&#9492;&#9472;sdc2 Filesystem                                    465.9G  87.8G /mnt/data
sr0                                                   1024M
```

---

### Post by TheFu on 2021-04-09
Graham1, I'm concerned that you have /home and backups on the same physical device.  That isn't a backup - unless you have some external, detached, storage that gets the backup data?

The main reason to use LVM is for flexibility. Many changes don't require any downtime or rebooting with LVM.  Plus, merging available storage that isn't contiguous into a single file system is trivial using LVM.  For example, say your sdb needs to have swap reduced to a reasonable 4.1G and you'd like to add the extra storage 50% to timeshift and 50% to /home. With LVM, that is really easy.  Without LVM, all the data in /home will need to be shifted left 2.1G which will take some time.  Yes, it is a contrived example.

> I suppose that answers my question but coming from BTRFS and Timeshift, I cannot understand why this setup is not popular (am I missing something).
Or perhaps we are all missing something?  
May want to read this: [http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM)
> Don't use the linux filesystem btrfs on the host for the image files. It will result in low IO performance. The kvm guest may even freeze when high IO traffic is done on the guest. 

Doesn't Gnome-Boxes use KVM?
I know that libvirt works with LVM nicely. It presents block LV storage to each VM which can be extended like any other LV. Plus, snapshots - real snapshots.  I use LVM snapshots all the time for a quick fallback capability when doing something slightly risky - say patching weekly.  True snapshots are available in ZFS, LVM and btrfs.  LVM doesn't force any specific file system type, which means snapshots aren't tied to the file system. That can be very  handy ... for Windows VMs, for example.

And only LVM has been enterprise ready for 20+ yrs.  All the other options are total noobs in comparison. ;)

---

### Post by Graham1 on 2021-04-09
> **TheFu said:**
> Graham1, I'm concerned that you have /home and backups on the same physical device.  That isn't a backup - unless you have some external, detached, storage that gets the backup data?

The home folder isn't really used that much (for storage anyway). Anything important, is moved over to sdc2. I guess I could have pointed /home to sdc2 but have kept the Linux side to sdb. The 75GB in use are VMs, so I'm not too worried should I loose those. I did have Backups doing this automatically for home (minus VMs) but reverted to doing this manually again.

> The main reason to use LVM is for flexibility. Many changes don't require any downtime or rebooting with LVM.  Plus, merging available storage that isn't contiguous into a single file system is trivial using LVM.  For example, say your sdb needs to have swap reduced to a reasonable 4.1G and you'd like to add the extra storage 50% to timeshift and 50% to /home. With LVM, that is really easy.  Without LVM, all the data in /home will need to be shifted left 2.1G which will take some time.  Yes, it is a contrived example.

LVM does sound useful and something I will look into. Previously, I have been using GParted to do this when the BTRFS partition has been low on space. Tbh, it was fairly quick though (a lot quicker than I expected).

> Or perhaps we are all missing something?  
May want to read this: [http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM)

Thanks for the link. The VMs are stored on /home which is ext4. Only the OS is on BTRFS. I have read other articles about performance with BTRFS but tbh, personally I haven't noticed any difference between BTRFS and Ext4.

> Doesn't Gnome-Boxes use KVM?
I know that libvirt works with LVM nicely. It presents block LV storage to each VM which can be extended like any other LV. Plus, snapshots - real snapshots.  I use LVM snapshots all the time for a quick fallback capability when doing something slightly risky - say patching weekly.  True snapshots are available in ZFS, LVM and btrfs.  LVM doesn't force any specific file system type, which means snapshots aren't tied to the file system. That can be very  handy ... for Windows VMs, for example.

Yes. The ability to change partition sizes on the fly is really appealing. So, would you recommend using LVM over ZFS? Is there a GUI available (like Timeshift) to manage this? (take or recover from snapshots without using a CLI). This is something I could test on my test laptop or is this possible in Boxes? 

> And only LVM has been enterprise ready for 20+ yrs.  All the other options are total noobs in comparison. ;)

Can't argue with that. Thanks for the advice :)

---

### Post by TheFu on 2021-04-09
> **Graham1 said:**
>  
Thanks for the link. The VMs are stored on /home which is ext4. Only the OS is on BTRFS. I have read other articles about performance with BTRFS but tbh, personally I haven't noticed any difference between BTRFS and Ext4.
For a long time, there was a problem with data corruption on btrfs with VMs too.  If you look at my lsblk output above, you can see lots of VMs using storage ... but none have a file system that the hostOS knows about.  Each VM uses the LV directly and it doesn't have any file system underneath. That's 1 less layer between the VM and the disk.

> **Graham1 said:**
>  
Yes. The ability to change partition sizes on the fly is really appealing. So, would you recommend using LVM over ZFS? Is there a GUI available (like Timeshift) to manage this? (take or recover from snapshots without using a CLI). This is something I could test on my test laptop or is this possible in Boxes? 

ZFS isn't ready for the OS or booting yet.  Use ZFS for data for now, not the OS, not boot, not /home.  Perhaps in 22.04, ZFS will be fully ready?

No GUI for LVM. Plus, enterprise servers don't have any GUI, so why bother?  Avoiding a GUI is something I do. GUIs are too slow and in-exact. Generally, they provide just 20% of the features that the CLI versions provide.  Read the manpage for **lvcreate** and **lvconvert** - try to put that into a GUI that isn't so simplified as to be useless.  I dare you.  How do you do thin provisioning on a RAID1 LVM setup in the GUI?

Ok, someone did post about a commercial LVM GUI program here in the last few months. It wasn't F/LOSS, so I wasn't interested. There was a very simple GUI available for 16.04, but it was a 10% solution.  If you only need the 10% of features that a GUI offers, great.  But most people would think that's all LVM can do.

I've never seen timeshift. I've written at least 1 book about backups and restore stuff in these forums. My reading of timeshift says it is a 50% solution and that some other backup/cloning tool is still required.  Why learn 2 backup tools when 1 is sufficient?
I've never used Boxes and haven't touched end-user VM tools in years.

I can't think of any reason why LVM can't be tried inside VMs.  One of my lsblk output posts above is from inside a VM.  Using a VM is a great way to try out complex settings.  With LVM, allocate only the amount of storage you need for 3 months at a time, never all of it.  Snapshots are created and use the unused storage in the VG, but if all the storage is already allocated to LVs, then there isn't any room for any snapshots.  Also, **lvextend** is 5 seconds and zero downtime and the system can be busy.  lvreduce requires umounting the storage and probably downtime for the application, if not the entire system.   Look at my lsblk output that has the "/stuff" mount.  I'm pretty certain there is hundreds of GB of unallocated storage.

---

### Post by Graham1 on 2021-04-09
> **TheFu said:**
> No GUI for LVM. Plus, enterprise servers don't have any GUI, so why bother?  Avoiding a GUI is something I do. GUIs are too slow and in-exact. Generally, they provide just 20% of the features that the CLI versions provide.  Read the manpage for **lvcreate** and **lvconvert** - try to put that into a GUI that isn't so simplified as to be useless.  I dare you.  How do you do thin provisioning on a RAID1 LVM setup in the GUI?

I'm the opposite, a GUI is a must for me. I just want to be able to use something without having to work out what command does what. Regarding Timeshift, I can't fault it (well, only on Fedora). Simple to setup and then I can just let it do it's thing. As LVM does not have a GUI, it's a no go for me (sorry).  

> I've never seen timeshift. I've written at least 1 book about backups and restore stuff in these forums. My reading of timeshift says it is a 50% solution and that some other backup/cloning tool is still required.  Why learn 2 backup tools when 1 is sufficient?
I've never used Boxes and haven't touched end-user VM tools in years.

Tbh, only really needed to use Timeshift on my test laptop (from the CLI) to get back to a desktop. More of a tool to recover the OS from a bad update. As the data is on another disk, even installing the OS again takes no time at all but still nice to recover instantly. Again, Boxes is a very simple (to use) VM that doesn't require any configuration (get's a distro up and running in no time). Ideal for someone like me.

:)

---

### Post by TheFu on 2021-04-09
> **Graham1 said:**
> I'm the opposite, a GUI is a must for me. I just want to be able to use something without having to work out what command does what. Regarding Timeshift, I can't fault it (well, only on Fedora). Simple to setup and then I can just let it do it's thing. As LVM does not have a GUI, it's a no go for me (sorry).  
Don't be sorry. We are all different.

Just be aware that 80% of the computing power in Unix systems comes from non-GUI stuff.  For example, some jobs pre-scheduled to run at specific times in the future. .... One is running now:
```
$ ats
2164    Fri Apr  9 18:58:00 2021 = thefu
2165    Fri Apr  9 19:58:00 2021 a thefu
2166    Fri Apr  9 19:58:00 2021 a thefu
2167    Sat Apr 10 06:28:00 2021 a thefu
2168    Sat Apr 10 19:58:00 2021 a thefu
2173    Sun Apr 11 18:58:00 2021 a thefu
2169    Sun Apr 11 19:58:00 2021 a thefu
2170    Sun Apr 11 21:58:00 2021 a thefu
```
These will run whether anyone is logged in or not.  The results will be waiting when we get around to them.
Other jobs need to run as quickly as possible, just 1 at a time to prevent storage thrashing. That's where a job queue system comes in handy.
No GUI for either of those and those tasks run whether anyone is logged in or not. To ensure they don't impact performance, they are run at a lower priority - called "**nice**".  There are 10 nice levels so higher numbers get more scheduled CPU or I/O time.  There is an **ionice** tool.  Anyway, they run in the background at a lower priority than normal programs, which remain snappy.

> **Graham1 said:**
> 
Tbh, only really needed to use Timeshift on my test laptop (from the CLI) to get back to a desktop. More of a tool to recover the OS from a bad update. As the data is on another disk, even installing the OS again takes no time at all but still nice to recover instantly. Again, Boxes is a very simple (to use) VM that doesn't require any configuration (get's a distro up and running in no time). Ideal for someone like me.

For instant recovery from a bad update, I'd just use the snapshot.  Lacking snapshot, there's a daily backup for all my systems created nightly - about once a year, I need to wipe and start over from scratch completely, but most of the time, I just need a few files from the backups - that's just a cp or rsync to get it back.  Once I missed a corrupted DB for over a month and had to go back 37 days to that DB backup.  All the newer backups included the corruption.  Very happy I have at least 60 days, often 90 and 180 days of versioned backups for higher risk systems.  I can't keep 180 days of snapshots. Doubt I have enough storage for more than about 20 snapshots to be kept.

---

