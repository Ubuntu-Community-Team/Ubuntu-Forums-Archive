---
title: "Increase the size of kvm guest image"
date: 2022-05-27
forum: Virtualisation
---

### Post by Heeter on 2022-05-27
Hi all,

I have an Ubuntu 20.04.4 LTS server running KVM

There is one lvm partition on this server that has 2 VM running, The size of this partition 1.6TB

One of the images in this partition is 240GB in size running Ubuntu 20.04.4 LTS in it.

```

ot@serv:/var/vmstorage# ls -l -h
total 281G
drwx------ 2 root         root 4.0K Oct  4  2021 lost+found
-rw------- 1 libvirt-qemu kvm   46G May 27 18:22 mailserv
-rw------- 1 libvirt-qemu kvm  239G May 27 18:22 webserv
root@serv:/var/vmstorage# 

```

Inside the image itself the LVM size is 322GB:
```

root@webserv:/home/adminpc# df -h --total
Filesystem                    Size  Used Avail Use% Mounted on
udev                          2.4G     0  2.4G   0% /dev
tmpfs                         494M 1020K  493M   1% /run
/dev/mapper/webserv--vg-root  313G  124G  176G  42% /
tmpfs                         2.5G     0  2.5G   0% /dev/shm
tmpfs                         5.0M     0  5.0M   0% /run/lock
tmpfs                         2.5G     0  2.5G   0% /sys/fs/cgroup
/dev/loop0                     44M   44M     0 100% /snap/certbot/2035
/dev/loop2                     44M   44M     0 100% /snap/certbot/1952
/dev/loop3                     56M   56M     0 100% /snap/core18/2344
/dev/loop5                     56M   56M     0 100% /snap/core18/2409
/dev/loop6                    111M  111M     0 100% /snap/core/12834
/dev/loop7                     62M   62M     0 100% /snap/core20/1434
/dev/loop8                     45M   45M     0 100% /snap/snapd/15904
/dev/loop9                     45M   45M     0 100% /snap/snapd/15534
/dev/loop10                    68M   68M     0 100% /snap/lxd/22526
/dev/loop11                    68M   68M     0 100% /snap/lxd/22753
/dev/loop12                   112M  112M     0 100% /snap/core/13250
/dev/loop1                     62M   62M     0 100% /snap/core20/1494
tmpfs                         494M     0  494M   0% /run/user/1000
total                         322G  125G  184G  41% -

```

How can I expand the size of this image to 500GB?

Do I do it from the the server side, or within the image itself?

I am running a backup of the image before this

Regards

---

### Post by TheFu on 2022-05-27
Both.

What is the backing storage used by the hypervisor?  ZFS, LVM, something else?  Are those raw images?  If so, what is the internal format?  **qemu-img** has lots of options to gather information, convert between different image types and to resize, but most resize operations require 2x the storage.

After you modify the storage from the hypervisor side, then you have to allow/tell, the VM from inside that the storage has changed. This will often be recognized, but it won't magically expand the file system or add partitions or handle other details which are completely dependent on the file system(s) involved.

---

### Post by TheFu on 2022-05-27
BTW, I don't see anything related to LVM in your post.  If you think it is, please post
```
sudo pvs
sudo vgs
sudo lvs
```
commands and output for both the hypervisor host system AND each VM, from inside the VM.

---

### Post by Heeter on 2022-05-29
Hi Thank you TheFU

Here is the virt file system output from the kvm host, LVM partitioned
```

root@serv:/home/adminpc# cd /var/vmstorage
root@serv:/var/vmstorage# virt-filesystems -l -h --all -a webserv
Name                   Type       VFS  Label MBR Size Parent
/dev/webserv-vg/root   filesystem ext4 -     -   318G -
/dev/webserv-vg/swap_1 filesystem swap -     -   980M -
/dev/webserv-vg/root   lv         -    -     -   318G /dev/webserv-vg
/dev/webserv-vg/swap_1 lv         -    -     -   980M /dev/webserv-vg
/dev/webserv-vg        vg         -    -     -   319G /dev/sda1
/dev/sda1              pv         -    -     -   319G -
/dev/sda1              partition  -    -     8e  319G /dev/sda
/dev/sda               device     -    -     -   719G -
root@serv:/var/vmstorage#

```

Looks like the whole guest drive is at 719G, which would be oversized for my tastes, my goal was 500G, looks like the LVM is only using 319 gig from it.




From the guest:
```

root@webserv:/home/adminpc# pvs
  PV         VG         Fmt  Attr PSize    PFree
  /dev/vda1  webserv-vg lvm2 a--  <319.00g    0 
root@webserv:/home/adminpc# vgs
  VG         #PV #LV #SN Attr   VSize    VFree
  webserv-vg   1   2   0 wz--n- <319.00g    0 
root@webserv:/home/adminpc# lvs
  LV     VG         Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   webserv-vg -wi-ao---- <318.04g                                                    
  swap_1 webserv-vg -wi-ao----  980.00m                                                    
root@webserv:/home/adminpc# 

```

---

### Post by TheFu on 2022-05-30
Did I miss the pvs, vgs, and lvs for the VM host?  

If sda1 is the entire PV and already fully used, you'll need a different PV to use with vgextend. Using a different physical storage device to extend a VG is dangerous, unless it is for a RAID1 or mirrored situation. I've lost 80% of my data about 20 yrs ago doing that. I extended a VG across 3 disks and didn't have backup religion.

I don't have anything like /var/vmstorage/ for any VM storage with LVM access.

On this hostOS (hadar), I assign an LV to each VM - it is a block device and the size is the same on the hostOS as seen inside each guestOS with parted.  

The block storage provided the the VM is handled by libvirt which can access the VG as a libvirt storage pool.
Back on the hostOS (hadar), the LVM stuff looks like this:
```
$ sudo pvs
  PV         VG       Fmt  Attr PSize   PFree 
  /dev/sdb5  hadar-vg lvm2 a--  476.22g 46.00g

$ sudo vgs
  VG       #PV #LV #SN Attr   VSize   VFree 
  hadar-vg   1  12   0 wz--n- 476.22g 46.00g

$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv     hadar-vg -wi-ao---- 175.00g                                                    
  lv-tp-lxd      hadar-vg twi-a-tz--  32.23g             0.00   10.06                           
  lv-vpn09-2004  hadar-vg -wi-ao----   [COLOR="#FF0000"]7.50g[/COLOR]                                     
  lv-zcs46       hadar-vg -wi-a-----  25.00g                                                    
  lxd-lv         hadar-vg -wi-ao----  60.00g                                                    
  root           hadar-vg -wi-ao----  32.33g                                                    
  swap_1         hadar-vg -wi-ao----   4.25g
....
```

Don't know how much any of this is to help you.  

If I wanted to make increase the storage available to vpn09, I'd use 
```
sudo lvextend -L +5G /dev/hadar-vg/lv-vpn09-2004
``` on the hostOS.  Then I'd go into the VM, run parted to get the new size recognized.  Because that VM doesn't use GPT or LVM, I'd probably need to boot from a gparted ISO (or Try Ubuntu-Mate) into the VM, so the storage could be modified.  Depending on how much I wanted to add and where, it is likely that I'd add a new partition (logical) after expanding vda2. I suspect that /var/ would be what I'd need to be larger, so the new partition would get all the files from /var on the old / partition (moved), fstab modified to mount it, then I'd reboot into the OS.  

See how my hadar-vg still has 40+GB available?  I do this on purpose to ensure I'm not stuck without any storage for snapshots or when I need to add a few GB to a VM to keep it running a few more weeks as new storage is acquired.  Depending on the new storage size and type, I'd use **pvmove **to migrate some LVs from the existing VG over to a new VG on the new storage.  pvmove can move PVs, VGs, and/or LVs. What gets moved is our choice.  I've used to to move an entire PV onto new storage while everything kept running (including VMs). In that instance, 1 PV == 1VG, so that use wasn't too complex.  The pvmove manpage goes into how to do all this.

That's 2 methods. In the real world, for my VPN VM, I'd probably just wipe the entire OS and VM, then install a fresh 20.04 (I'm not ready for 22.04) and restore the necessary files into it from the most recent backup (nightly). Then I'd have a fresh LV sized a little larger and fresh OS without any cruft, and all the VPN settings back.  Doubt it would take 30 minutes total (actually, I'm thinking more like 20min). 

I don't have any servers with more than 40G internal storage. Even our Nextcloud server only has 20G.  If more storage is needed for a VM, NFS is used with many, many, TB available.  NFS is on real hardware.

OT: I did screw around with thin-provisioning for LXD, but found the lack of certainty too worrisome. I couldn't sleep.  Sleep is too important, so I took that as a "sign" and stopped using TP (thin provisioning).

---

### Post by Heeter on 2022-05-30
OOOOOPPPPPSSSS

Here it is TheFU, Thank you

KVM Host
```

root@serv:/home/adminpc# pvs
  PV         VG  Fmt  Attr PSize PFree
  /dev/sdd5  LVG lvm2 a--  1.63t 5.00g
root@serv:/home/adminpc# vgs
  VG  #PV #LV #SN Attr   VSize VFree
  LVG   1   9   0 wz--n- 1.63t 5.00g
root@serv:/home/adminpc# lvs
  LV        VG  Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  bak       LVG -wi-ao----  7.50g                                                    
  home      LVG -wi-ao----  1.80g                                                    
  opt       LVG -wi-ao---- 52.00g                                                    
  root      LVG -wi-ao----  4.00g                                                    
  srv       LVG -wi-ao----  3.80g                                                    
  tmp       LVG -wi-ao----  3.50g                                                    
  usr       LVG -wi-ao---- 10.00g                                                    
  var       LVG -wi-ao----  4.00g                                                    
  vmstorage LVG -wi-ao----  1.54t                                                    
root@serv:/home/adminpc# 

```

Thank you

---

### Post by Heeter on 2022-05-30
Thank you TheFU

---

### Post by TheFu on 2022-05-30
You've lost me.  My LVM and libvirt+kvm setup seems very different.

See in my last post where my **lvs** shows different LVs for each mount and each VM?  I didn't expect to see a single vmstorage LV, like you are using.  I don't know what to make of that. 
Seems the VG is already fully allocated. I think you are screwed.

My setup is 
LV (block device for each VM)  ---> VM-storage (often with a full LVM stack) --> PV->VG->LVs
Plus, my VG isn't fully used.
```
$ sudo vgs
  VG       #PV #LV #SN Attr   VSize   VFree 
  hadar-vg   1  12   0 wz--n- 476.22g [COLOR="#008000"]**46.00g**[/COLOR]
```
I have a little wiggle room for when a bit more storage is needed for any specific LV.  Not allocating all the VG to LVs is a core technique for LVM.  Plus, my libvirt storage for toy file-based VMs has lots of room I could steal for other uses.
```
$ dft
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  132G   33G  81% /var/lib/libvirt
```
I could certainly grab at least 60G from it.  I have a view old MS-Windows VMs in there, but those aren't running very often. I really should move them to a different VM host.  When they were installed, that VM was a Windows media center to record TV. It hasn't been used in that way for about 3 yrs now, so the "data" storage added for recordings isn't needed any more.
```
hadar:/var/lib/libvirt/images# du -hsh Win*
93G     Win7Ult
20G     WinXPPro.vdi

```
All that can easily be moved/removed. I do need to keep it, somewhere for some financial and tax software.

---

### Post by Heeter on 2022-05-30
Hi TheFU

My apologies if I lost you

I am interested in increasing the size of one KVM guest, currently at 319G inside the guest:
```

root@webserv:/home/adminpc# pvs
  PV         VG         Fmt  Attr PSize    PFree
  /dev/vda1  webserv-vg lvm2 a--  <319.00g    0 
root@webserv:/home/adminpc# vgs
  VG         #PV #LV #SN Attr   VSize    VFree
  webserv-vg   1   2   0 wz--n- <319.00g    0 
root@webserv:/home/adminpc# lvs
  LV     VG         Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   webserv-vg -wi-ao---- <318.04g                                                    
  swap_1 webserv-vg -wi-ao----  980.00m                                                    
root@webserv:/home/adminpc#

```


On the KVM host side, I don't need to adjust the actual LV's
```

root@serv:/home/adminpc# pvs
  PV         VG  Fmt  Attr PSize PFree
  /dev/sdd5  LVG lvm2 a--  1.63t 5.00g
root@serv:/home/adminpc# vgs
  VG  #PV #LV #SN Attr   VSize VFree
  LVG   1   9   0 wz--n- 1.63t 5.00g
root@serv:/home/adminpc# lvs
  LV        VG  Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  bak       LVG -wi-ao----  7.50g                                                    
  home      LVG -wi-ao----  1.80g                                                    
  opt       LVG -wi-ao---- 52.00g                                                    
  root      LVG -wi-ao----  4.00g                                                    
  srv       LVG -wi-ao----  3.80g                                                    
  tmp       LVG -wi-ao----  3.50g                                                    
  usr       LVG -wi-ao---- 10.00g                                                    
  var       LVG -wi-ao----  4.00g                                                    
  vmstorage LVG -wi-ao----  1.54t                                                    
root@serv:/home/adminpc#

```

The actual guest that I am interested in increasing is located in LV/vmstorage, and it is called "webserv"
```

root@serv:/home/adminpc# cd /var/vmstorage
root@serv:/var/vmstorage# virt-filesystems -l -h --all -a webserv
Name                   Type       VFS  Label MBR Size Parent
/dev/webserv-vg/root   filesystem ext4 -     -   318G -
/dev/webserv-vg/swap_1 filesystem swap -     -   980M -
/dev/webserv-vg/root   lv         -    -     -   318G /dev/webserv-vg
/dev/webserv-vg/swap_1 lv         -    -     -   980M /dev/webserv-vg
/dev/webserv-vg        vg         -    -     -   319G /dev/sda1
/dev/sda1              pv         -    -     -   319G -
/dev/sda1              partition  -    -     8e  319G /dev/sda
/dev/sda               device     -    -     -   719G -
root@serv:/var/vmstorage#

```

The virtual harddisc space shows as 719G, the filesystem shows as 319G

I believe from reading and studying your posts that I actually don't need to touch the host side of the image, just need to increase to image from inside the guest side.

---

### Post by TheFu on 2022-05-30
I understand that, but the PV and VG are already fully used in 
/dev/sda1              partition  -    -     8e  319G /dev/sda

I haven't seen a full picture of how sda is used that I recall. Is there an sda2?  If not, then create one (**parted**/gparted). Make it the size of the unused space on the drive, mark it as LVM, then create a PV there, add it to the webserv-vg (**vgextend**), then you can use **lvextend** on any LV you like, though making the VM root LV over 40G is really a poor idea. It shouldn't be allowed.  If it were me, I'd make another LV just for the data inside the web server and move the existing data, probably in  /var/www over and perhaps the /var/lib/mariadb stuff too.  Keeping the OS separate from data is a core "best practice" on all OSes.

But I really don't know. I don't know how to read virt-filesystems output.

---

### Post by Heeter on 2022-05-30
Ok thank you TheFU

I am going to install gparted and create a lvm for the rest of the /sda.

---

