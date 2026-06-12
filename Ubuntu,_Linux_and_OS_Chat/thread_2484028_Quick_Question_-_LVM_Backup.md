---
title: "Quick Question - LVM Backup"
date: 2023-02-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-02-15
Considering LVM.  Is it the case that Backups are done via snapshots?  I have been using rdiff-backup and rsync to date on my non-lvm installs.  I have yet to read anything re lvm snapshots and the rdiff-backup capability of versioning and deleting previous backups (e.g. delete backups older than x days).

---

### Post by TheFu on 2023-02-15
[https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)   - it isn't specific to any backup tool, though their example used tar, which nobody should be using for system backups.

---

### Post by Quarkrad on 2023-02-16
What backup tool(s) would you advise I look at for LVM based on the following:

[LIST]
[*]
[*]Using a stand-alone Desktop pc
[*]Basic understanding, and currently using, rdiff-backup (mainly because of versioning and ability to delete 'old backups')
[/LIST]


note: For my purposes/workflow I have a script that mounts un-mounted discs for my Backups and runs rdiff-backup when I shutdown the machine.  Over the past 12 months I have migrated to the versioning/restore testing Backup philosophy and very happy with rdiff-backup.  Currently I'm wondering/researching if moving to lvm is a step too far for me.

---

### Post by TheFu on 2023-02-16
I use rdiff-backup.  Using it with LVM snapshots isn't hard.  How much more script commands are needed depends on the number of LVs that need snapshots created, mounts, umounts, and snapshots deleted .... along with error checking to ensure things worked.

Always remember the power and flexibility with LVM comes from NOT allocating all the VG to LVs.  Here's an SSD layout with LVM:
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
  &#9492;&#9472;vg00-Mint21.1                      40G lvm  zfs_member  rpool
```
If the 465G partition, it uses only about 230G, so around 50% used.  The unmounted storage at the bottom is managed by libvirt for KVM VMs. Libvirt understands LVM.  BTW, that system has plenty of storage.
```
$ inxi -d
Drives:    Local Storage: total: 37.13 TiB used: 22.42 TiB (60.4%) 
....

```
cough ... lots of storage, all under LVM management currently. No RAID.

---

### Post by Quarkrad on 2023-02-16
Thank you - very interesting. If one was to use rdiff-backup to backup **vg00 - home** and also take a snapshot of **vg00 - home** are we not doing the same thing?  Or is that the rdiff-backup just contains the data-set within a specific logical volume whereas a snapshot contains the data-set but also info about the logical volume itself in the context of the whole lvm environment?  (If this was the case I can see the benefit of having both a rdiff-backup and snapshot of the same logical volume).

---

### Post by TheFu on 2023-02-16
> **Quarkrad said:**
> Thank you - very interesting. If one was to use rdiff-backup to backup **vg00 - home** and also take a snapshot of **vg00 - home** are we not doing the same thing?  Or is that the rdiff-backup just contains the data-set within a specific logical volume whereas a snapshot contains the data-set but also info about the logical volume itself in the context of the whole lvm environment?  (If this was the case I can see the benefit of having both a rdiff-backup and snapshot of the same logical volume).

Read this: [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

Only backup the snapshots. They are frozen blocks, so backups won't become corrupted with files being modified in the middle of rdiff-backup.  Also, don't loop over each individual LV, creating a snapshot, then mount it, then run rdiff-backup, then umounting the snapshot, then deleting the snapshot.  Do them all at once so all the data being backups is consistent.

Snapshots are named.  Snapshots are never a backup, since they are just frozen blocks - immutable.  This is why we need to remove them when we are done.

Play with them inside a VM.  Do something simple, like take a snapshot, then do lots of package management work, then roll back to that point.  It will change many things in how you do risky things when it only takes an instant to get back where you were.  This is part of the reason that ZFS and BTRFS have proper volume management snapshots.  Don't confuse what other backup tools call "snapshots" with what LVM, ZFS and BTRFS call snapshots. They are completely different.

Ponder this.  Why would you mount a snapshot read-only?

---

### Post by Quarkrad on 2023-02-17
I cannot create a vm that has lvm to play with.  My limited knowledge/experience of qemu vm is to create a vm by installing an iso file.  The ubuntu installer only allows the whole vm to be a logical volume and you cannot shrink it without using a liveCD - which I can't see how that is done on a vm.  Perhaps other distributions allow configurable lvm during their install(?).

---

### Post by TheFu on 2023-02-17
> **Quarkrad said:**
> I cannot create a vm that has lvm to play with.  My limited knowledge/experience of qemu vm is to create a vm by installing an iso file.  The ubuntu installer only allows the whole vm to be a logical volume and you cannot shrink it without using a liveCD - which I can't see how that is done on a vm.  Perhaps other distributions allow configurable lvm during their install(?).

VMs work the same as physical machines.  If you want to boot from an Ubuntu Installler ISO, connect that to the VM using the CDROM option and swap the boot order so that gets used first.  Bam. You are booting from an ISO, but have the virtual storage available.  

To test backups, add another virtual storage drive to the VM.  Treat it just like you would a physical storage device.

So, Ubuntu does allow configuring LVM under the terrible "Do Something Else" part of the installer.  CentOS had a fairly intuitive way years ago. I haven't looked at CentOS in about 7 yrs and won't touch it as an alpha rolling release that Redhat has converted it into to have their community be alpha testers.  Perhaps check out Rocky Linux?  IDK.  Or just setup the LVM PV, VG, and LVs on the storage **before** connecting it to a physical machine if you don't like switching to a different, text-only, tty, while the installers runs, but before the storage parts. 

Lots of options.

---

### Post by Quarkrad on 2023-02-18
TheFu - once again thank you.  Successfully got lvm environment within vm so I can have a play and get more experience before implementing on my new hd.  Currently looking at having 2nd storage disk attached to vm so I can get my head around the backup methodology.  Initially confusing reading about snapshots and the amount of space they take up.  Having a vm environment now will hopefully let me answer my own questions.

---

### Post by TheFu on 2023-02-18
Congratulations.  Actual experience can answer most questions faster and easier with greater depth of knowledge than just reading thoughts from others. How much storage snapshots use is an "it depends" question, so there isn't any real answer.  

Sorta like how how much backup storage rdiff-backup needs to have 30, 60, 180, days of versioned backups.  "It depends."  I use 110% of the total as a rule of thumb for every 30 days worth, but sometimes I'll do something accidentally where the backup size is 2x for many months as a large file that I accidentally left in my HOME overnight slowly expires through the backup versions.  

The same applies for snapshots. If you upgrade the entire OS, don't be surprised if the snapshot created used 50% of the storage, right?  OTOH, if the system is mostly idle, then a snapshot probably won't use very much storage at all, since frozen blocks that don't get updated can be shared with the snapshot AND the running system.

---

