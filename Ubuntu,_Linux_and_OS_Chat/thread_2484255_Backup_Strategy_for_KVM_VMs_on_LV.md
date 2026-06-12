---
title: "Backup Strategy for KVM VMs on LV"
date: 2023-02-21
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-02-21
I've been experimenting with lvm prior to building a new Desktop on a new HD. I have, and am happy with, using rdiff-backup for things like **/home** that has it's own lv.  I plan to create another lv to be used solely for kvm virtual machines.  At the moment, on my 'old' Desktop, I use rsync to backup my kvm machines as they tend not to change much (they are all in a separate folder/mount point).   Anyway .... when I migrate to logical volumes, and have one dedicated to my  kvm virtual machines, I'm not sure what to do in terms of backup up the lv.  Is rdiff-backup an appropriate tool for this kvm lv? (Note:  I know in the lvm world snapshots are used and I'm trying to get my head around these re a Desktop machine. Having successfully used rdiff-backup for my **/home** lv I feel comfortable using rdiff-backup rather than a snapshot.  For things like /home I cannot see, at the moment, the advantage of a snapshot over rdiff-backup).

---

### Post by TheFu on 2023-02-21
> **Quarkrad said:**
> I've been experimenting with lvm prior to building a new Desktop on a new HD. I have, and am happy with, using rdiff-backup for things like **/home** that has it's own lv.  I plan to create another lv to be used solely for kvm virtual machines.  At the moment, on my 'old' Desktop, I use rsync to backup my kvm machines as they tend not to change much (they are all in a separate folder/mount point).   Anyway .... when I migrate to logical volumes, and have one dedicated to my  kvm virtual machines, I'm not sure what to do in terms of backup up the lv.  Is rdiff-backup an appropriate tool for this kvm lv? (Note:  I know in the lvm world snapshots are used and I'm trying to get my head around these re a Desktop machine. Having successfully used rdiff-backup for my **/home** lv I feel comfortable using rdiff-backup rather than a snapshot.  For things like /home I cannot see, at the moment, the advantage of a snapshot over rdiff-backup).

I use 1 LV per VM. That's how libvirt seems to prefer it.  There is somethings called "thin provisioning", but that just seems too scary to me, so I've only dabbled with it.

I used to use rsync with VMs, but soon it was clear that the 45min each backup period per VM wasn't going to let the backups finish in the allowed backup window I had.  With rdiff-backup, most VM backups take 1-3 minutes and a few with 100reds of thousands of tiny files take about 20 minutes.  That's still better than 45-90 minutes each which is what rsync provided.  Plus, with rdiff-backup, I have the ability to move to completely different hardware, file systems, and even different hypervisor types, because the backups aren't tied to any hypervisor.

Seems you are still confusing what a snapshot is, vs what a backup is. They are not the same.

For VMs, I treat them exactly like physical machines when it comes to backups.  If there is LVM, then I'll create a snapshot for each LV inside the VM, mount the snapshots readonly, then use rdiff-backup to pull them.  For almost all my systems, my backup server "pulls" the backups for security reasons.  If we say that "local backups" are 80% good, then "pushed" backups are 90% good, "pulled" backups are 100% good.

[LIST]
[*]Local backup = the backup storage is locally connected (this can also include any network mounted storage, say NFS or CIFS) If the client can fully access to the storage using a file manager, it is "local"
[*]Pushed backups = the client pushes the files to a backup server. The backup storage on the server cannot be accessed except through rdiff-backup, never by using a file manager or mounted storage on the client.
[*]Pulled backups = the server pulls the files from a client to the server storage.  The backup storage is only available to the backup server, no client systems.
[/LIST]

2-3 yrs ago, I helped someone setup their LVM + snapshot + rdiff-backup backups in these forums with a script.  The only issue I had when we were done is that he didn't create the LVM snapshots at the same time, which meant the backup data wasn't homogeneic/consistent to the exact same instant of time.  Each LV being frozen at a different time was the issue. That could be very important for some applications.

---

### Post by Quarkrad on 2023-02-28
Thank you - really helpful.  I'm a little confused about *then I'll create a snapshot for each LV inside the VM* - is the vm not inside the LV?  My 'wrong' thinking is I have a LV of say 50G, inside that 50G I'm going to have a qcow2 file*  but I also need space inside the LV for the snapshot (I'm guessing it does not work like that).  Also, in another thread ([https://ubuntuforums.org/showthread.php?t=2484455](https://ubuntuforums.org/showthread.php?t=2484455)) Dennis N has suggested I use the whole LV disc for the vm rather than creating a qcow2 file - I quite like that idea but it adds more confusion for me re backup.

---

### Post by TheFu on 2023-02-28
duplicate ... somehow.  ?

---

### Post by TheFu on 2023-02-28
> **Quarkrad said:**
> Thank you - really helpful.  I'm a little confused about *then I'll create a snapshot for each LV inside the VM* - is the vm not inside the LV?  My 'wrong' thinking is I have a LV of say 50G, inside that 50G I'm going to have a qcow2 file*  but I also need space inside the LV for the snapshot (I'm guessing it does not work like that).  Also, in another thread ([https://ubuntuforums.org/showthread.php?t=2484455](https://ubuntuforums.org/showthread.php?t=2484455)) Dennis N has suggested I use the whole LV disc for the vm rather than creating a qcow2 file - I quite like that idea but it adds more confusion for me re backup.

The LV provided to the guest VM from the host is a block device, unformatted.  Inside the VM, it sees that block device as a whole HDD that can be used with partitioning or however you like.  I would never use qcow2 inside a VM or for a VM that I didn't think needed to be handed over to someone else.

For example, I brought up a new desktop running the latest Linux Mint a few weeks ago.  I chose ZFS for the file system during install.  From inside the VM, storage looks like this:
```
$ lsblkt
NAME    SIZE TYPE FSTYPE     MOUNTPOINT
vda      40G disk            
&#9500;&#9472;vda1    1M part            
&#9500;&#9472;vda2  513M part vfat       /boot/efi
&#9500;&#9472;vda3  1.8G part swap       [SWAP]
&#9500;&#9472;vda4    2G part zfs_member 
&#9492;&#9472;vda5 35.7G part zfs_member 
```
You'll recognize the 'vda' as a virtio disk device.  2 ZFS pools are setup - rpool and bpool - for root and boot.  Because ZFS lies about **df** use, that command isn't really useful.  Ok, it isn't lying, but it isn't the truth either because ZFS storage is 'different'.

From outside the VM, on the host, it looks like this:
```
nvme0n1                             465.8G disk                        
&#9500;&#9472;nvme0n1p1                            50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                           600M part ext4        boot       /boot
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9500;&#9472;vg00-swap                         4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                      35G lvm  ext4        root       /
  &#9500;&#9472;vg00-var                           55G lvm  ext4        var        /var
  &#9500;&#9472;vg00-home                          26G lvm  ext4        home       /home
  &#9500;&#9472;vg00-ubuntu2204--srv               15G lvm                         
  &#9500;&#9472;vg00-ubuntu22.04--srv--2           15G lvm                         
  &#9500;&#9472;vg00-xubuntu22.04--backup          10G lvm                         
  &#9500;&#9472;vg00-xubuntu22.04                  15G lvm                         
  &#9500;&#9472;vg00-xubu--22.10                   10G lvm                         
**  &#9500;&#9472;vg00-Mint21.1                      40G lvm  zfs_member  rpool      **
  &#9492;&#9472;vg00-lxd                           50G lvm        
```
As you can see, a few other 22.04 and 22.10 systems are using separate LVs under the host OS.  I'm using ZFS to learn more about it, so don't worry about that.  It could be straight LVM too. As you can see, 7 of the LVs aren't actually mounted to the hostOS.  What you don't see is that inside the lxd LV, there are a few linux containers sharing that 50G of space.  Here's a relatively new nextcloud LXC container (perhaps 2 weeks old) ... using 3.6G of storage:
```
$ dft
Filesystem                                   Type           Size  Used Avail Use% Mounted on
lxd/containers/nextcloud-lxd                 zfs             48G  **3.6G**   44G   8% /
```
Most of the data available inside nextcloud is stored outside it, via read-only storage access.  I've never lost and data inside nextcloud by accident or stupidity and I've been running a NC server for 3-5 yrs (I don't really remember - it was on an 18.04 VM originally).  

lxd really wants us to use ZFS. Learned that over the last few years managing lxc containers with lxd.  I've removed some other storage from all the posts, to avoid cluttering up things.  Simple to show points is my goal, though I fear sometimes my simplification is still too much. ;)

Headed off-topic ... sorry.

I treat my VMs like they are physical hosts when it comes to backups.  The trick is to find the way to backup each system in an efficient (space, speed) and secure way.  There are no wrong answers, provided it works.  Also, just because there's a "backup" tool provided, that doesn't mean it does what's needed.  The nextcloud snap backup (nextcloud.export) is less than great, for example.  It does versioning with different directories for each backup (20230228-110921/ 20230228-110920/), which doesn't work well with backup tools that handle their own versioning efficiently.  I don't want 120 copies of the DBMS data and applications saved. I'd rather have the backups wipe all prior files and let rdiff-backup handle versioning.
Plus, it isn't capturing snap settings - I've added removable media and limit snap updates to Saturdays. That would be lost, even if it got all the data (which it doesn't).
Here's the backup storage:
```
# du -sh /var/snap/nextcloud/common/backups
503M    /var/snap/nextcloud/common/backups
```

There's well over 400G in the system.  There aren't any options to the nextcloud.export tool, so I don't see how to know what's included or not.

---

### Post by Quarkrad on 2023-02-28
Thanks for your detailed response. I'm enjoying my latest lvm journey - your host structure is also very interesting and giving me new things to think about.

---

### Post by TheFu on 2023-02-28
> **Quarkrad said:**
> Thanks for your detailed response. I'm enjoying my latest lvm journey - your host structure is also very interesting and giving me new things to think about.

There are some choices in my host LVs that aren't necessary (/boot/) and I wouldn't have done.  There are others that were named different, root-00, to avoid conflicts from a disk/LVM setup not shown.
The size of var LV is much larger than I'd normally do, but that's because I was lazy and expected to have directory-based lxc containers there and some snap packages are very, very, bloated.  YMMV.

---

