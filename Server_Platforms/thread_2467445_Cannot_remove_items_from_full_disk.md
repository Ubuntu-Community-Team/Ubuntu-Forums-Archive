---
title: "Cannot remove items from full disk"
date: 2021-09-26
forum: Server Platforms
---

### Post by Heeter on 2021-09-26
Hi all

This is for my Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-153-generic x86_64)

I have a qemu kvm only server that runs 2 images,webserver and mailserver. I cannot update or remove anything because my /var folder is maxed out. Cant uninstall unused kernels because it is too maxed out:

```

root@serv:~# df -h
Filesystem                  Size  Used Avail Use% Mounted on
udev                         48G     0   48G   0% /dev
tmpfs                       9.5G   18M  9.5G   1% /run
/dev/mapper/LVG-root        2.0G  1.2G  668M  65% /
/dev/mapper/LVG-usr         9.9G  1.7G  7.8G  18% /usr
tmpfs                        48G     0   48G   0% /dev/shm
tmpfs                       5.0M     0  5.0M   0% /run/lock
tmpfs                        48G     0   48G   0% /sys/fs/cgroup
/dev/mapper/LVG-var         2.0G  2.0G     0 100% /var
/dev/sdb1                   1.9G  222M  1.6G  13% /boot
/dev/mapper/LVG-vmstorage   1.6T  287G  1.2T  20% /var/vmstorage
/dev/mapper/LVG-isostorage  4.9G   20M  4.6G   1% /var/isostorage
/dev/mapper/LVG-opt          51G   20G   29G  41% /opt
/dev/mapper/LVG-bak         2.9G  3.1M  2.8G   1% /bak
/dev/mapper/LVG-srv         989M  2.7M  939M   1% /srv
/dev/mapper/LVG-home        481M  2.3M  453M   1% /home
/dev/mapper/LVG-tmp         984M  2.8M  932M   1% /tmp
tmpfs                       9.5G     0  9.5G   0% /run/user/1000
root@serv:~# 

```

Here is the list of kernels:
```

root@serv:~# dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
rc  linux-image-4.15.0-101-generic         4.15.0-101.102                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-108-generic         4.15.0-108.109                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-109-generic         4.15.0-109.110                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-112-generic         4.15.0-112.113                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-115-generic         4.15.0-115.116                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-117-generic         4.15.0-117.118                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-118-generic         4.15.0-118.119                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-122-generic         4.15.0-122.124                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-123-generic         4.15.0-123.126                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-124-generic         4.15.0-124.127                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-126-generic         4.15.0-126.129                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-128-generic         4.15.0-128.131                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-129-generic         4.15.0-129.132                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-134-generic         4.15.0-134.138                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-135-generic         4.15.0-135.139                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-137-generic         4.15.0-137.141                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-139-generic         4.15.0-139.143                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-140-generic         4.15.0-140.144                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-142-generic         4.15.0-142.146                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-143-generic         4.15.0-143.147                                  amd64        Signed kernel image generic
ii  linux-image-4.15.0-144-generic         4.15.0-144.148                                  amd64        Signed kernel image generic
ii  linux-image-4.15.0-147-generic         4.15.0-147.151                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-55-generic          4.15.0-55.60                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-70-generic          4.15.0-70.79                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-72-generic          4.15.0-72.81                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-74-generic          4.15.0-74.84                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-76-generic          4.15.0-76.86                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-88-generic          4.15.0-88.88                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-91-generic          4.15.0-91.92                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-96-generic          4.15.0-96.97                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-99-generic          4.15.0-99.100                                   amd64        Signed kernel image generic
root@serv:~# ^C
root@serv:~# 

```

Was wondering if someone can assist me on how to remove some items to restart the images and run updates.

Regards

---

### Post by TheFu on 2021-09-27
You are using LVM, so there is hope.  To provide an overview:
```
sudo vgs 
sudo lvs
```
If you've followed the best practice with LVM and haven't allocated all the VG storage to LVs, then you can extend the /var LV in about 5 seconds.
But if you have already allocated all the VG space to LVs, then you have some choices to make.

Kernels don't go into /var.  They go into /boot.
Your /var was only 2G in size, which is much, much, much too small for any VMs to be held there.  KVM/Qemu uses the /var/lib/libvirt/ area for KVM VMs.  I mount extra storage onto that location ...
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   16G   15G  52% /
/dev/sdb1                         ext2  720M  165M  519M  25% /boot
/dev/mapper/hadar--vg-libvirt--lv ext4  **173G**  139G   26G  85% [COLOR="#FF0000"]/var/lib/libvirt[/COLOR]
```
for that reason.

BTW, this alias will show only **real** storage:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```
It excludes junk that shows up in df output, but means nothing.
Of the stuff you posted, only these are real storage:
```
root@serv:~# df -h
Filesystem                  Size  Used Avail Use% Mounted on 
/dev/mapper/LVG-root        2.0G  1.2G  668M  65% /
/dev/mapper/LVG-usr         9.9G  1.7G  7.8G  18% /usr 
/dev/mapper/LVG-var         2.0G  2.0G     0 [COLOR="#FF0000"]100[/COLOR]% /var
/dev/sdb1                   1.9G  222M  1.6G  13% /boot
/dev/mapper/LVG-vmstorage   1.6T  [COLOR="#FF0000"]287G[/COLOR]  1.2T  20% /var/vmstorage
/dev/mapper/LVG-isostorage  4.9G   20M  4.6G   1% /var/isostorage
/dev/mapper/LVG-opt          51G   20G   29G  41% /opt
/dev/mapper/LVG-bak         2.9G  3.1M  2.8G   1% /bak
/dev/mapper/LVG-srv         989M  2.7M  939M   1% /srv
/dev/mapper/LVG-home        481M  2.3M  453M   1% /home
/dev/mapper/LVG-tmp         984M  2.8M  932M   1% /tmp
```

Why so many LVs?   The way we had to do storage in the 1990s doesn't generally apply today.  Our HDDs aren't 500MB anymore.

---

### Post by LHammonds on 2021-09-27
> **TheFu said:**
> 
Kernels don't go into /var.  They go into /boot.

This is true.  Removing kernels (even manually) will only affect /boot and /usr/src so your focus should not be on kernel removal (although you should only have just a couple in there by default...look at that issue later)

> **TheFu said:**
> 
Why so many LVs?   The way we had to do storage in the 1990s doesn't generally apply today.  Our HDDs aren't 500MB anymore.

That's probably my fault since I still do that and it looks like he followed my tutorial based on the naming scheme.

I still like controlling where space is allocated but should probably mention that volume management in my tutorials is based on being on top of a SAN where managing virtual hard drives is MUCH different than managing physical drives.

Heeter, let us know if you have space in your VG to allocate to VAR.

Run the vgs or vgdisplay command to see how much free space you have for allocation.

If you truly followed my tutorial, you "should" have unallocated space in your VAR LV and you can immediately expand your VAR file system into.  The whole point of my volume management section was to initially create very small LVs which the installer utilized 100% of it for the partitions, then expand the LVs in such a way they had a buffer in them to expand the file system in case of an emergency (usually via the "check-storage.sh" script)

LHammonds

---

### Post by TheFu on 2021-09-27
> **LHammonds said:**
>  
If you truly followed my tutorial, you "should" have unallocated space in your VAR LV and you can immediately expand your VAR file system into.  The whole point of my volume management section was to initially create very small LVs which the installer utilized 100% of it for the partitions, then expand the LVs in such a way they had a buffer in them to expand the file system in case of an emergency (usually via the "check-storage.sh" script)

LHammonds

+1.  

I love starting small, but being prepared to add more space as needed, where needed.  THAT is a chief reason for using LVM (along with snapshots and sparse LVs).

/var also contains the APT cache, so be certain you are running **sudo apt-get autoremove** every few weeks as well.  If you cannot extend the LV or manually remove a few 2-5MB apt packages, once there are ZERO (0) bytes left, which would include the 5% reserved for root emergencies, there isn't much more that can be done besides to boot from alternate media and manually mount and remove more cached apt packages.  Just last week, I manually removed all cached, but not accessed packages from my systems that hadn't been accessed in the last 180 days.  Anything in /var/cache/apt/archives is free game, especially in emergencies.

There is much to be said about limiting the size of /var to prevent run-away log files.  Perhaps once every 5-10 yrs, one of my systems will have that issue where a log file gets added lines around 2GB/hr.  That's always been due to an upstream issue, nothing wrong with the log files. They are working.  But the program writing to the log files has either hit a bug OR is being attacked. It isn't fun when your logs are filling up due to network attacks.

BTW, it appears you've moved the default location for the libvirt storage pool outside /var.  That would be excellent.  I usually cheat for the few VMs I still have that use file-based storage.  You do know that libvirt will happily use LVM as a storage pool, right?  There are some very interesting uses when LVM and libvirt work together. Very interesting.

I am a little worried that /dev/mapper/LVG-vmstorage is pre-allocated to be much larger than actually used.  LVs should be sized for 3 months of use and expanded as needed.  I fear that LVG-vmstorage is using all the remaining storage that /var's LV could sip 1G from today and make your issue go away from.
Reducing already allocated storage from an LV is a PITA and has some risks.  Huge LV allocations with lots of unused space ... not ideal.

BTW LHammonds, I've made my LV allocations slightly more complex thanks to your methods here and on your site. And for a VM host machine like Heeter has, there are some good reasons for non-trivial LV setups.  I'd only question 3 of the LVs above.

---

### Post by Heeter on 2021-09-27
Hi lhammonds

I did use your tutorial

Is there someway I can merge and remove some lvm's?

This is a straight up qemu KVM server with 2 images

Now I am realizing that I over thought this server setup

---

### Post by LHammonds on 2021-09-27
Priority #1 is to determine how much free space is in your VAR LV and in your LVG volume group.

If you have free space in VAR, you can simply expand your /var file system depending on how much space is available.

If you have no free space in VAR but you have free space in LVG, then you can expand the VAR volume and then expand the /var file system.

So...find this out with:

```
sudo vgs
sudo lvs
```

EDIT:  Wait a sec...do I know you IRL?  Did we work together before?

---

### Post by rsteinmetz70112 on 2021-09-27
> **Heeter said:**
> Hi lhammonds

Is there someway I can merge and remove some lvm's?



Not lhammonds but,

Since all of your LVs are in the root folder you can certainly move some of them to root, edit /etc/fstab then delete the LVs you moved and expand root to get more space there.

Depending on how much spare space you have it might get a little tedious.

As TheFU says I'd keep /var  and /home separate and maybe /tmp and /bak to guard against rogue processes filling things up.

---

### Post by Heeter on 2021-09-27
Hi Guys,

Thanks for your responses so far

Here is the result:
```

root@serv:/home/adminpc# sudo vgs 
  VG  #PV #LV #SN Attr   VSize VFree
  LVG   1  10   0 wz--n- 1.63t    0 
root@serv:/home/adminpc# sudo lvs
  LV         VG  Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  bak        LVG -wi-ao----  7.50g                                                    
  home       LVG -wi-ao----  1.80g                                                    
  isostorage LVG -wi-ao----  5.00g                                                    
  opt        LVG -wi-ao---- 52.00g                                                    
  root       LVG -wi-ao----  4.00g                                                    
  srv        LVG -wi-ao----  3.80g                                                    
  tmp        LVG -wi-ao----  3.50g                                                    
  usr        LVG -wi-ao---- 10.00g                                                    
  var        LVG -wi-ao----  4.00g                                                    
  vmstorage  LVG -wi-ao----  1.54t                                                    
root@serv:/home/adminpc# 

```

```

root@serv:/var# ls
backups  cache  crash  isostorage  lib  local  lock  log  lost+found  mail  opt  run  snap  spool  tmp  vmstorage
root@serv:/var#

```

```

root@serv:/var# ls -a backups
.                   alternatives.tar.1.gz  alternatives.tar.4.gz  apt.extended_states.0  dpkg.statoverride.0  gshadow.bak
..                  alternatives.tar.2.gz  alternatives.tar.5.gz  dpkg.arch.0            dpkg.status.0        passwd.bak
alternatives.tar.0  alternatives.tar.3.gz  alternatives.tar.6.gz  dpkg.diversions.0      group.bak            shadow.bak
root@serv:/var#

```

Looks like I am tapped out space wise, I can delete the /isostorage LVG, but what else?

Thanks again guys, for your help, totally stuck here

---

### Post by LHammonds on 2021-09-27
> **Heeter said:**
> 
Looks like I am tapped out space wise, I can delete the /isostorage LVG, but what else?

Hold up there boss.  Your total size for the VAR volume is 4 GB (as shown by lvs).  The size of your /var file system is 2 GB (as shown by the df).  That means you have 2 GB of room right?

Do this command and see if it gives you extra breathing room:

```
sudo resize2fs /dev/LVG/var 3G
```

If that command is successful, run this command to validate:

```
df -h /var
```

**EDIT:** Now that you provided the necessary info to get an accurate picture of what you have, here is my breakdown analysis:

LVG=1.63T, [COLOR=#ff0000]**free=0**[/COLOR] (not generally good, no flexibility for any LV)
root LV=4G, fs=2G, [COLOR=#008000]**2G unallocated**[/COLOR] (some flexibility)
var LV=4G, fs=2G, **[COLOR=#008000]2G unallocated[/COLOR] **(some flexibility)
opt LV=52G, fs=51G, **[COLOR=#008000]1G unallocated[/COLOR]** (some flexibility)
srv LV=3.8G, fs=1G, [COLOR=#008000]**2.8G unallocated **[/COLOR](some flexibility)
tmp LV=3.5G, fs=1G, [COLOR=#008000]**2.5G unallocated**[/COLOR] (some flexibility)
usr LV=10G, fs=10G, [COLOR=#ff0000]**0 unallocated**[/COLOR] (no flexibility, [COLOR=#ff0000]**DANGER**[/COLOR])
bak LV=7.5G, fs=3G, [COLOR=#008000]**4.5G unallocated **[/COLOR](some flexibility)
home LV=1.8G, fs=0.5G, [COLOR=#008000]**1.3G unallocated**[/COLOR] (some flexibility)
iso LV=5G, fs=5G, [COLOR=#ff0000]**0 unallocated**[/COLOR] (no flexibility, [COLOR=#ff0000]**DANGER**[/COLOR])
vm LV=1.54T, fs=1.6T, [COLOR=#ff0000]**0 unallocated**[/COLOR] (no flexibility, [COLOR=#ff0000]**DANGER**[/COLOR])

It is wise to have unallocated space at the logical volume group level so some can be assigned to whichever logical volume is in need.  I also like having some breathing room in each logical volume so my scripts can automatically increase space at the file system level as it starts to run out (and send me email notifications of the issue).

Not having free space at the LVG "and" at the LV screams "danger, danger Will Robinson" to me.  In your situation, if you have space issues in usr, isostorage or vmstorage, your only recourse is to delete files.  However, you "could" reduce another file system and its logical volume to free up space but that is asking for problems.  Always plan to expand, never contract.

LHammonds

---

### Post by Heeter on 2021-09-27
Hi LHammonds

Thank you!!

```

root@serv:/var# sudo resize2fs /dev/LVG/var 3G
resize2fs 1.44.1 (24-Mar-2018)
Filesystem at /dev/LVG/var is mounted on /var; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 1
The filesystem on /dev/LVG/var is now 786432 (4k) blocks long.

root@serv:/var# 

```

```

root@serv:/var# df -h /var
Filesystem           Size  Used Avail Use% Mounted on
/dev/mapper/LVG-var  3.0G  2.0G  889M  69% /var
root@serv:/var# 

```

```

root@serv:/var# du -h vmstorage
287G	vmstorage
root@serv:/var# ls -a vmstorage
.  ..  mailserv  mailserver.qcow2  webserv  webserver.qcow2
root@serv:/var# ls -a isostorage
.  ..
root@serv:/var#

```

If I could bring down this /vmstorage to half of what it is, that would be fine too, can still use it

I can remove /isostorage because I created for the sole purpose of holding ubuntu isos for any future image creations, deleted the isos that were sitting in there already

---

### Post by TheFu on 2021-09-27
> **LHammonds said:**
> Hold up there boss.  Your total size for the VAR volume is 4 GB (as shown by lvs).  The size of your /var file system is 2 GB (as shown by the df).  That means you have 2 GB of room right?

Do this command and see if it gives you extra breathing room:

```
sudo resize2fs /dev/LVG/var 3G
```
 

So, whenever using lvextend, **always** add the -r switch. This will do the resize2fs automatically.

I think your VM storage is the real issue long term.  You can easily cut that 50% to get some flexibility back for your LVM setup.  Probably best to do that from a *Try Ubuntu* boot so nothing gets mounted.  Definitely backup anything you cannot lose first.  And use  **lvreduce -r** (so it resizes the file system at the same time).

If this storage is on SSDs, leaving 20% unused should vastly increase the lifespan of the SSD.  Add in another 10% so you can easily have snapshots for backup purposes and you'd be doing well.  That will make a trivial 2G out of space issue 5 seconds to solve in any LV in the same VG.  Being able to quickly add 1-10GB to an LV is key. That's what not having the entire VG used up is good at.

BTW, none of us knew all this when we started with LVM.  Experience is the best teacher.  I once lost 80% of my personal data due to a bad LVM decision about 20 yrs ago.  Of course, at the time, I thought I was being brilliant and taking advantage of the capabilities of LVM.  1 disk in a 3 disk RAID0 failed. It wasn't good.  I bet those 3 disks are on a shelf here somewhere ... because I couldn't take the idea that the data was all gone.  Someday, I'd get it all back, right?

---

### Post by LHammonds on 2021-09-27
I have not ever used the "reduce" commands so I have no experience to share other than google searching which I'm sure you could do as well.

I have not removed an LV before either but know its possible.  Once removed, you might need to edit /etc/fstab and keep it from trying to mount the missing volume unless the lvremove command handles that for you too...but I don't know.

But no matter what you do, make sure you have a GOOD backup of your data.  Assume that a reduction or removal will go poorly and have a way to get it back.

**EDIT**: Ninja'd by TheFu!  :)

LHammonds

---

### Post by Heeter on 2021-09-27
Thanks guys I am going to read up on lvreduce first before anything else

---

### Post by TheFu on 2021-09-27
The **lvextend** and **lvreduce** commands can only resize certain file systems with the -r switch (there's a longer switch version, if you want more clarity), so be certain you have one of those file systems. I don't think XFS is supported - XFS can never be reduced. That's limitation of that file system.

Definitely read the entire manpage for lvreduce. There are gotchas.

---

### Post by Heeter on 2021-09-27
I managed to remove 24 unused kernels now, Yay. Also finally did updates. Now getting other errors, started a new thread :( 

Will read the manpage when I finally get the mail server and webserver backup and running

Thank you Fu!

---

