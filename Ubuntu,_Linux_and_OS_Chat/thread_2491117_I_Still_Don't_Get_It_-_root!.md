---
title: "I Still Don't Get It - root!"
date: 2023-09-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-09-26
My root filled up again.  I disconnected all my drives and started an experiment with a free SSD.   Created two logical volumes, LV1 for **/ **and LV2 for **/home** - plenty of physical space within the two LVs.  I then started to add additional LVs - this time for virtual machines.  Then my **/ **started to fill and suddenly I was at the end of a precipice, **/ **was full up. So .... I'm thinking I should not think of **/** being all the files and folders that were installed in LV1 but, because everything in Linux is under **/**, **/** is in fact everything that is loaded onto my PC.  So ... the more additional LVs I create the more **/** fills up.  To address this I have to expand LV1 to accommodate more space.   To me this is odd, these extra LVs have their own space on the SSD, separate from LV1.  If I add three extra LVs (with still plenty of physical space/capacity on the SSD) how does increasing the size of LV1 stop my **/** from filling up?   I have played with different mount points but as everything is under **/** this doesn't really matter.

---

### Post by Dennis N on 2023-09-26
When file system B is mounted on File system A, it doesn't change the reported size of file system A. So I think something else is causing what you observe.

Here, two file systems (in LVs) mounted to / and yet 31G used in root, not 31+81+128:

```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/os_vg-fedora      44G   31G   12G  74% /
/dev/mapper/os_vg-Common     214G   81G  124G  40% /mnt/Common-Files
/dev/mapper/os_vg2-vm_disks  296G  128G  156G  46% /mnt/vm-disks 

```

---

### Post by Quarkrad on 2023-09-27
I pulled out my test SSD and plugged in my main 1T HD that I use day-to-day.  This is the state as it stands:

```
dad@dadubuntu:~$ df -h
Filesystem             Size  Used Avail Use% Mounted on
tmpfs                  1.6G  2.0M  1.6G   1% /run
/dev/mapper/vg01-root   40G   12G   26G  32% /
tmpfs                  7.7G  4.0K  7.7G   1% /dev/shm
tmpfs                  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1         197M  8.6M  189M   5% /boot/efi
tmpfs                  7.7G     0  7.7G   0% /run/qemu
/dev/mapper/vg01-home   49G   19G   28G  41% /home
tmpfs                  1.6G  140K  1.6G   1% /run/user/1000
dad@dadubuntu:~$ 
```

I have four logical volumes set up on this 1T device.

```
dad@dadubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg01/root
  LV Name                root
  VG Name                vg01
  LV UUID                Q9V1MZ-K1yj-KyPB-Ax2Q-Cehr-yrxK-L9uVH3
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:48:57 +0000
  LV Status              available
  # open                 1
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vg01/home
  LV Name                home
  VG Name                vg01
  LV UUID                k2I519-SiTv-PXYV-LBTB-Bquo-3jm8-LVgvgU
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:49:35 +0000
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/vg01/workspace
  LV Name                workspace
  VG Name                vg01
  LV UUID                E2gsIe-lcni-ROxO-UIm8-KnLv-5dAl-p3NhT2
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-02-21 20:45:28 +0000
  LV Status              available
  # open                 0
  LV Size                250.00 GiB
  Current LE             64000
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
   
  --- Logical volume ---
  LV Path                /dev/vg01/swap
  LV Name                swap
  VG Name                vg01
  LV UUID                LtHzWU-FlDd-EzCB-4VGg-vR5E-hD86-HFV7f8
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-02-27 12:58:47 +0000
  LV Status              available
  # open                 2
  LV Size                8.00 GiB
  Current LE             2048
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:3
   
dad@dadubuntu:~$ 

```

At this point I launch a terminal and execute the following commands:

```
dad@dadubuntu:~$ sudo lvcreate -L 40G -n ubuntuvm vg01
  Logical volume "ubuntuvm" created.
```

```
dad@dadubuntu:~$ sudo mkfs.ext4 /dev/vg01/ubuntuvm
mke2fs 1.46.5 (30-Dec-2021)
Discarding device blocks: done                            
Creating filesystem with 10485760 4k blocks and 2621440 inodes
Filesystem UUID: d7d6431c-15f1-4a62-a347-e80fa58630fe
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (65536 blocks): done
Writing superblocks and filesystem accounting information: done
```

```
dad@dadubuntu:~$ sudo mkdir /ubuntuvm

```

So I now have 5 logical volumes on my 1T HD

```
dad@dadubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg01/root
  LV Name                root
  VG Name                vg01
  LV UUID                Q9V1MZ-K1yj-KyPB-Ax2Q-Cehr-yrxK-L9uVH3
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:48:57 +0000
  LV Status              available
  # open                 1
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vg01/home
  LV Name                home
  VG Name                vg01
  LV UUID                k2I519-SiTv-PXYV-LBTB-Bquo-3jm8-LVgvgU
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:49:35 +0000
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/vg01/workspace
  LV Name                workspace
  VG Name                vg01
  LV UUID                E2gsIe-lcni-ROxO-UIm8-KnLv-5dAl-p3NhT2
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-02-21 20:45:28 +0000
  LV Status              available
  # open                 0
  LV Size                250.00 GiB
  Current LE             64000
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
   
  --- Logical volume ---
  LV Path                /dev/vg01/swap
  LV Name                swap
  VG Name                vg01
  LV UUID                LtHzWU-FlDd-EzCB-4VGg-vR5E-hD86-HFV7f8
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-02-27 12:58:47 +0000
  LV Status              available
  # open                 2
  LV Size                8.00 GiB
  Current LE             2048
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:3
   
  --- Logical volume ---
  LV Path                /dev/vg01/ubuntuvm
  LV Name                ubuntuvm
  VG Name                vg01
  LV UUID                kJhP0p-XJ4l-aMmq-3jcH-ps1L-m9kd-Z2X9OK
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-09-27 14:19:48 +0100
  LV Status              available
  # open                 0
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:4
   
dad@dadubuntu:~$ 

```

Using the Virt Manager gui I install ubuntu 22.04 into my new logical volume and use /ubuntuvm as the pool for the .qcow2 virtual machine.  Once the new vm is install and rebooted I close down the vm and virt manager and shutdown my pc.  On rebooting my df -h now looks like:

```
dad@dadubuntu:~$ df -h
Filesystem             Size  Used Avail Use% Mounted on
tmpfs                  1.6G  2.0M  1.6G   1% /run
/dev/mapper/vg01-root   40G   29G  8.8G  77% /
tmpfs                  7.7G  4.0K  7.7G   1% /dev/shm
tmpfs                  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1         197M  8.6M  189M   5% /boot/efi
tmpfs                  7.7G     0  7.7G   0% /run/qemu
/dev/mapper/vg01-home   49G   19G   28G  41% /home
tmpfs                  1.6G  148K  1.6G   1% /run/user/1000
dad@dadubuntu:~$ 

```

So my root has gone up from 32% to 77%.  If I were to add another logical volume/vm my root would not cope.  Hence my confusion - it seems the more devices you add the more root will grow and my lv that contain **/ **will have to get larger and larger.  Or am I doing something fundamentally wrong?

---

### Post by deadflowr on 2023-09-27
You never mounted the new volume in the designated mount location.
All you posted was that you made a new directory called /ubuntuvm.
/ubuntuvm is a sub-directory and part of the root volume until you mount the new volume there.

So all new files added were simply added to the main root volume.

---

### Post by TheFu on 2023-09-27
If you have LVM, why not just create an LV for each VM to use, separate from any mounted file systems?  Inside each VM, you'll see a block device and it will be partitioned and managed like any other install.  For example, here's a 500G SSD that has both the hostOS and a few VM LVs setup:
```
NAME                                TYPE FSTYPE        SIZE FSAVAIL FSUSE% LABEL      MOUNTPOINT
nvme0n1                             disk             465.8G                           
&#9500;&#9472;nvme0n1p1                         part vfat           50M   43.2M    12% EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                         part ext4          600M  250.9M    49% boot       /boot
&#9492;&#9472;nvme0n1p3                         part LVM2_member   465G                           
  &#9500;&#9472;vg00-swap                       lvm  swap          4.1G                           [SWAP]
  &#9500;&#9472;vg00-root--00                   lvm  ext4           35G    5.5G    79% root       /
  &#9500;&#9472;vg00-var                        lvm  ext4           55G   34.6G    31% var        /var
  &#9500;&#9472;vg00-home                       lvm  ext4           26G   14.9G    36% home       /home
[B]  &#9500;&#9472;vg00-ubuntu2204--srv            lvm                 15G                           
  &#9500;&#9472;vg00-ubuntu22.04--srv--2        lvm                 15G                           
  &#9500;&#9472;vg00-Mint21.1                   lvm  zfs_member     40G                rpool      
  &#9500;&#9472;vg00-lxd                        lvm  zfs_member     50G                lxd        
  &#9500;&#9472;vg00-lv--vpn09--2004            lvm                7.5G                           
  &#9500;&#9472;vg00-lv--blog44                 lvm               30.2G                           
  &#9500;&#9472;vg00-lv--xen41--1204            lvm               12.5G                           
  &#9500;&#9472;vg00-lv--zcs45--1604            lvm                 35G                           
[/B]  &#9492;&#9472;vg00-lv--tv                     lvm  ext4          100G   38.1G    56%            /TV
```

See how most of the LVs don't have any mount location?  That's because they aren't mounted inside the hostOS. If you do that and don't allow LVs to auto-expand (which is an advanced thin-pool allocation method), then a VG won't become full.
```

$ sudo pvs
  PV             VG             Fmt  Attr PSize    PFree  
  /dev/nvme0n1p3 vg00           lvm2 a--  <464.98g  39.67g

$ sudo vgs
  VG             #PV #LV #SN Attr   VSize    VFree  
  vg00             1  13   0 wz--n- <464.98g  39.67g

$ sudo lvs
  LV                VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  Mint21.1          vg00           -wi-ao----   40.00g                                                    
  home              vg00           -wi-ao----   26.00g                                                    
  lv-blog44         vg00           -wi-ao----   30.20g                                                    
  lv-tv             vg00           -wi-ao----  100.00g                                                    
  lv-vpn09-2004     vg00           -wi-ao----    7.50g                                                    
  lv-xen41-1204     vg00           -wi-ao----   12.50g                                                    
  lv-zcs45-1604     vg00           -wi-ao----   35.00g                                                    
  lxd               vg00           -wi-ao----   50.00g                                                    
  root-00           vg00           -wi-ao----   35.00g                                                    
  swap              vg00           -wi-ao----    4.10g                                                    
  ubuntu22.04-srv-2 vg00           -wi-a-----   15.00g                                                    
  ubuntu2204-srv    vg00           -wi-a-----   15.00g                                                    
  var               vg00           -wi-ao----   55.00g            
```                                        
Posted just so you have a full view of the relevant LVM setup.  Actually, there are over 30 LVs on that host system, but I didn't want to muddy the waters too much.
Once a VG has been added to the libvirt storage pool, it can be trivially used for VMs.

I find that **lvdisplay** has too much junk output when all we need is the summary (pvs, vgs, lvs), as shown above.  Those commands aren't fancy aliases. They are already on your system and get to the point for showing LVM data in a tabular format.

Oh, I see that others pointed out that the file system wasn't mounted, so it wasn't being used.  If you add the VG to the libvirt storage pool, you'll not have that problem anymore.

---

### Post by Quarkrad on 2023-09-28
OK - thank you all.  This is becoming a little clearer although still a little foggy - you have confirmed my suspicion that my lack of understanding is with mounting (also with qemu/Virt Manager).  Although I only have one vm at the moment I do create separate LVs for each one so I'm on the right track.  I can see (I think???) that by creating a mount point under **/** (/ubuntuvm) I have done exactly what I want to avoid.  I've put the virtual machines 32G qcow2 file under **/** so obviously I've increased **/**!  Taking into account I use Virt Manager to create the VMs where should I put the pool and hence the qcow2 file if not under** /**?  Should I create a separate lv to be used as a common pool for each vm?

---

### Post by TheFu on 2023-09-28
> **Quarkrad said:**
> OK - thank you all.  This is becoming a little clearer although still a little foggy - you have confirmed my suspicion that my lack of understanding is with mounting (also with qemu/Virt Manager).  Although I only have one vm at the moment I do create separate LVs for each one so I'm on the right track.  I can see (I think???) that by creating a mount point under **/** (/ubuntuvm) I have done exactly what I want to avoid.  I've put the virtual machines 32G qcow2 file under **/** so obviously I've increased **/**!  Taking into account I use Virt Manager to create the VMs where should I put the pool and hence the qcow2 file if not under** /**?  Should I create a separate lv to be used as a common pool for each vm?

With LVM and libvirt, you can directly create LVs to be provided directly to the virtual machines without using qcow2 or any file system on the VM host.  No qcow2 used at all this way.

In the VM host settings for virt-manager, there's Overview, Virtual Networks, and Storage tabs.
Under "Storage", we can add different types of storage areas.  There are 12 different options in mine.  

I have 1 called "default" which with the type "Filesystem Directory" ... is is where typical img/vdi/vdmk and qcow2 files would be created for VMs.
The other has a type "LVM Volume Group" ... this is a VG pool that gets used for logical volumes.  It doesn't need to be dedicated just to VMs, so I see my "home" and "root" and "var" and "swap" LVs in the list, along with all the LVs setup for VMs and lxd+lxc containers.

That's it for the storage setup. Easy.

When I create a new VM, in the storage setup of virt-manager, I'll be certain to choose to use the VG as the pool and create an LV sized for my needs for that specific virtual machine.  For desktops, I'd typically provide 35-50G. For servers, it depends, but anywhere from 1G to 15G, depending on how much data it will hold. This desktop is a VM and has 40G of storage allocated.  Inside the VM, it boots from ZFS.
```
$ sudo zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   401M  1.48G        -         -     0%    20%  1.00x    ONLINE  -
rpool  35.5G  18.0G  17.5G        -         -    49%    50%  1.00x    ONLINE  -
```
But outside, as you can look up in my prior post, it is 
```
  &#9500;&#9472;vg00-Mint21.1                   lvm  zfs_member     40G                rpool      
```
The hostOS doesn't mount it to any directory. There is no qcow2 file for the VM.

---

### Post by Quarkrad on 2023-09-29
Wow - that cracked it; using LVM Volume Pool and no qcow2 file.   Also helped my understanding of storage devices and mounting - thank you very much.  One last question (a bit of $64K question) - what typical size would you use for a ubuntu 22.04 vm that is used for testing apps/scripts mainly.  I have used 40G as the lv size for this test but get the impression 40G is way over-kill.

note:  my df -h shows root is back to 33% :P

---

### Post by TheFu on 2023-09-29
> **Quarkrad said:**
> Wow - that cracked it; using LVM Volume Pool and no qcow2 file.   Also helped my understanding of storage devices and mounting - thank you very much.  One last question (a bit of $64K question) - what typical size would you use for a ubuntu 22.04 vm that is used for testing apps/scripts mainly.  I have used 40G as the lv size for this test but get the impression 40G is way over-kill.

note:  my df -h shows root is back to 33% :P

Well, that depends on the specific release and bloat and how long I think it will be around.  Anywhere from 1G to 50G. It is a bit of a judgement call.  And as for 22.04, I'm not the guy to ask. Too new for my use, in general.  Let me check all my systems real quick (ansible rocks for that!).

Ok, the summary is 
[LIST]
[*]4 systems based on 22.04, 1 desktop, but the other 3 are in LXC containers. The containers are for extremely specific 1 web-app, requirements.
[*]5 systems running 20.04.6. 2 physical servers (VM hosts), 2 LXC containers and 2 VMs.
[*]3 systems running older Ubuntu server releases ... er ... for specific reasons. 2 of those should be upgraded, but the upgrades are ugly and likely will take multiple weeks to accomplish if they are possible. 1 of those will likely need to be completely re-implemented.  The 3rd system is around just to provide backup software for the other too, so when the other two are handled, it will go away.
[/LIST]

Of the 22.04-based systems ... 
```
# Wallabag
$ dft
Filesystem              Type  Size  Used Avail Use% Mounted on
lxd/containers/wallabag zfs    31G **1019M**   30G   4% /

# Pihole2 (pihole1 is on 20.04 still)
$ dft
Filesystem             Type           Size  Used Avail Use% Mounted on
lxd/containers/pihole2 zfs             32G  **2.5G**   30G   8% /

# Nextcloud
$ dft
Filesystem                           Type  Size  Used Avail Use% Mounted on
lxd/containers/nextcloud-lxd         zfs    41G   **11G**   30G  27% /  
/dev/mapper/WDBLK_8T-lv_d7           ext4  3.6T  953G  2.5T  28% /media/Music  # mapped from external-to-container storage
hadar:/d/rom/export/gallery          nfs   196G  120G   67G  65% /media/Photos  # mapped from external-to-container storage
/dev/mapper/istar--vg-lv_media       ext4  3.5T  3.4T  146G  96% /media/ebooks  # mapped from external-to-container storage

```
It should be noted that because those are containers managed by lxd, that all the storage is shared on a per physical host basis, so the real sizes of the allocation per instance isn't clearly visible. I can see the total storage pool for lxd is 
```
  space used: 18.57GiB
  total space: 47.97GiB
```
Is that useful?
I think the **df -Th** output "Used" column is just as helpful.  Containers are much more efficient on storage than VMs.  Plus they run 10x faster, approximately.  I'm at the point where I use containers by default and full VMs when I need stuff with kernel drivers, like a firewall.  To have a firewall that works inside a container requires using a privileged container, which is 95% of why containers are secure. They run without privileges.  That's sorta the entire point!  Breaking that means breaking the container, in my book.

The Linux Mint 21.2 Victoria desktop has ZFS and appears to be 40G total. You tell me:
```
$ sudo zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   401M  1.48G        -         -     0%    20%  1.00x    ONLINE  -
rpool  35.5G  18.0G  17.5G        -         -    49%    50%  1.00x    ONLINE  -
```
It is a stripped down desktop. I don't really use DEs. Plus Mint doesn't have snaps (which is why I switched), so there isn't any multi-GB snap-bloat.

---

### Post by Quarkrad on 2023-09-29
Again, thank you for your detailed reply.  You  got me onto rdiff-backup, then qemu/virtual machines and now  LVM.  Now I need to look at *Containers*.  I'm going to have to ask you to stop supporting on this forum soon!

---

### Post by TheFu on 2023-09-29
> **Quarkrad said:**
> Again, thank you for your detailed reply.  You  got me onto rdiff-backup, then qemu/virtual machines and now  LVM.  Now I need to look at *Containers*.  I'm going to have to ask you to stop supporting on this forum soon!

Do you run enterprise email servers yet?  That can be fun too! <beg>

---

### Post by Quarkrad on 2023-10-12
I'm back again!!!  Root full again

```
dad@dadubuntu:~$ df -h
Filesystem             Size  Used Avail Use% Mounted on
tmpfs                  1.6G  2.0M  1.6G   1% /run
/dev/mapper/vg01-root   40G   38G     0 100% /
tmpfs                  7.7G  4.0K  7.7G   1% /dev/shm
tmpfs                  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1         197M  8.6M  189M   5% /boot/efi
tmpfs                  7.7G     0  7.7G   0% /run/qemu
/dev/mapper/vg01-home   49G   15G   33G  31% /home
tmpfs                  1.6G  152K  1.6G   1% /run/user/1000

```

```
dad@dadubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg01/root
  LV Name                root
  VG Name                vg01
  LV UUID                Q9V1MZ-K1yj-KyPB-Ax2Q-Cehr-yrxK-L9uVH3
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:48:57 +0000
  LV Status              available
  # open                 1
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0

```

One thing I do not understand - that might help me solve this - is that root is on /dev/vg01/root which is 40G.  However, when I launch *Disk Usage Analyser* and scan the file system it tells me that root is at 100% and has a Size of 19.7GB.  (There is insufficient space on my 'system' to take a screen shot!).  If df is telling me */vg01/root *is 40GB and 38GB is being used where does 19.7GB come from reported by Disk Analyser?

At the moment I have nothing mounted under */media* and all my other hard disks are commented out in fstab.  The only LV's I have in fstab are /, /home and swap

---

### Post by TheFu on 2023-10-12
swap file?
/var/

There's little reason to use lvdisplay.  Use **lvs** instead.
Is it possible that you extended the root LV, but forgot to resize the file system too?  Always, always, always, use the **-r** option when using **lvextend**.   ALWAYS.[*]

* certain assumptions exist, like it should only be used with ext4 file systems.

---

### Post by Quarkrad on 2023-10-12
As far as I'm aware both the filesystem and size of my root LV is 40G. I've also created a 50G /home lv.

```
dad@dadubuntu:~$ df -h /
Filesystem             Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root   40G   38G     0 100% /
dad@dadubuntu:~$ df -h /home
Filesystem             Size  Used Avail Use% Mounted on
/dev/mapper/vg01-home   49G   15G   33G  31% /home

```

My swap lv looks OK

```
dad@dadubuntu:~$ sudo swapon -s
Filename				Type		Size		Used	Priority
/dev/dm-3                               partition	8388604		0	-2

```

---

### Post by Quarkrad on 2023-10-12
I'm still perplexed why *Disk Analyser* reports **/** as 19.8GB when df shows it as 40GB

---

### Post by Quarkrad on 2023-10-12
Solved - root trash was, well, full of trash.  One never stops learning!!

---

### Post by TheFu on 2023-10-12
> **Quarkrad said:**
> Solved - root trash was, well, full of trash.  One never stops learning!!

Why would **anyone** enable trash?  It just gets in the way.  Especially with a root account?  You aren't using a file manager as root, are you?  Bad. Bad. Bad.

Additionally, never trust GUI tools that provide important data.  Always drop to a shell and use those tools if there is any question.

---

### Post by Quarkrad on 2023-10-13
Thank you @TheFu.   99.9% of the time I do no use a file manager as root, but during researching my problem came across the possibility of the 'root trash' being my problem.  Only at that point I did use a file manager as root to navigate to and empty the trash.  For my own education .... what do mean by "... enable trash...."?   I am not aware I have changed anything from the standard install.

---

### Post by TheFu on 2023-10-13
> **Quarkrad said:**
>  For my own education .... what do mean by "... enable trash...."?   I am not aware I have changed anything from the standard install.

I know nothing of a standard install ... since around 12.04.  There must be settings somewhere, perhaps inside the file manager, to enable/disable the use of Trash.  As part of my backups, I run 
```
        if [[ -f /usr/bin/gio ]] ; then
           echo "INFO: Empty GIO trash"
           /usr/bin/gio trash --empty
        fi

```

I consider gio and gvfs to be abominations, but Gnome keeps pre-installing them. Sickening.  That's why we make daily, automatic, versioned, backups.

Just yesterday, I was trying to delete some time-stamped files from August  And used 
```
rm 2023-08 *
``` by mistake. I wanted
```
rm 2023-08* 
```
Fortunately, my daily overnight backups had all the files. 10 seconds later and they were all back. I got side tracked. Whenever I setup timestamped files, I also make a process/method to clean them up, but that didn't work (if it had, I wouldn't have be using the rm command). Ok... think it is fixed now. Next week when it works I'll know if that's true.  It was a compound 'find -delete' command with OR and AND combinations that I slapped together. Simplified now.

Anyways, backups rock.  Trash is a waste for people like us.  It just leaves crap in odd places that we don't expect, especially if we have lots of different file systems.

---

