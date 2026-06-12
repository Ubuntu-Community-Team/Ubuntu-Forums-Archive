---
title: "Keep Losing LVM Snapshot"
date: 2023-10-24
forum: Virtualisation
---

### Post by Quarkrad on 2023-10-24
I have just started to take snapshots of my VMs - specifically creating snapshot of a test VM to get use to the whole snapshot 'thing'.  So far I have twice created a snapshot, tested it by making changes to the VM and then reverting back via the snapshot -  and it works!  Problem is the snapshot then disappears!  I have some confusion where the snapshot(s) is/are located but from what I have gleaned so far the snapshot is created in the volume group where the LV is.  Here are my LVs

 ```
dad@dadubuntu:~$ sudo lvs
  LV        VG   Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home      vg01 -wi-ao----  50.00g                                                    
  root      vg01 -wi-ao----  40.00g                                                    
  swap      vg01 -wi-ao----   8.00g                                                    
  ubuntuvm  vg01 -wi-a-----  40.00g                                                    
  win10     vg01 -wi-a-----  50.00g                                                    
  workspace vg01 -wi-a----- 250.00g 
```

The two LVs I am using for testing are ubuntuvm and win10.  All the other LVs are part of my live system.  Yesterday I created a snapshot of ubuntuvm called ubuntuvm_snap - it was stored in **/dev/vg01** (I have no other Volume Groups on this machine).  Indeed, yesterday I tested the snapshot using the command **sudo lvconvert –-merge /dev/vg01/ubuntuvm_snap** and everything worked fine.   Today I have made some changes to ubuntuvm and messed things up a bit so want to go back to when I took the snapshot yesterday.   But, to me at least, the snapshot is no longer there

```
dad@dadubuntu:~$ cd /dev/vg01
dad@dadubuntu:/dev/vg01$ ls
home  root  swap  ubuntuvm  win10  workspace
dad@dadubuntu:/dev/vg01$ 

```

Seems to me I'm doing something fundamentally wrong in my snapshot creating process.   (To create the snapshot I used sudo lvcreate -L 5G -s -n ubuntuvm_snap /dev/vg01/ubuntuvm).

---

### Post by #&amp;thj^% on 2023-10-24
You did it right, but when the merge finishes, the merged snapshot is removed.

---

### Post by Quarkrad on 2023-10-24
Thank you - that explains a lot of what has been happening to me.  So a snapshot isn't like a separate 'thing' that can be used independent of the base data in the LV - it relies on the LV internal data for it's existence.  So, if you reformat a LV to ext4 for a clean install, then the snapshot will have disappeared because the base data that was in the LV is no longer there(?).  I think this is what I have done - hence the disappearance.  So .... in my case, leave the messed up LV and just use lvconvert to put the snapshot back in place.  (And hence, take another snapshot if I want to keep a 'day 1' copy).

---

### Post by #&amp;thj^% on 2023-10-24
> **Quarkrad said:**
>  So a snapshot isn't like a separate 'thing'
Well it is, but when used with the restore, it feels it's no longer needed since it is now used. (hope that makes sense) 
There is a way to keep the snapshot after restoring but it is very complicated, and space consuming.

I keep 3 daily and remove most the following day.
```
sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vglinux/root
  LV Name                root
  VG Name                vglinux
  LV UUID                B6gtk8-thJg-TwxK-Qd4e-2Hv2-fgi9-lRDd3P
  LV Write Access        read/write
  LV Creation host, time linux, 2023-10-12 11:25:04 -0600
  LV Status              available
  # open                 1
  LV Size                <463.29 GiB
  Current LE             118601
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     131064
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vglinux/swap_1
  LV Name                swap_1
  VG Name                vglinux
  LV UUID                QTBZID-WjNH-w0vd-JqIp-Qn3a-svsw-MLc2wX
  LV Write Access        read/write
  LV Creation host, time linux, 2023-10-12 11:25:04 -0600
  LV Status              available
  # open                 2
  LV Size                <1.91 GiB
  Current LE             488
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     131064
  Block device           253:1
   

```
Dang I keep forgetting Timeshift will also help, and maybe easier for you visually:
```
*timeshift --list
Mounted '/dev/dm-0 (sdc2)' at '/run/timeshift/48453/backup'
Device : /dev/dm-0 (sdc2)
UUID   : 7b3ea96f-ccc1-42d2-87de-4398db10de44
Path   : /run/timeshift/48453/backup
Mode   : RSYNC
Status : OK
1 snapshots, 396.8 GB free

Num     Name                 Tags  Description  
------------------------------------------------------------------------------
0    >  2023-10-23_08-00-01  D                  


```

---

### Post by Quarkrad on 2023-10-24
Thank you

---

### Post by MAFoElffen on 2023-10-24
Wow. What yuo asked in 4 lines could take volumes to explain. But I will try to keep that short.

For [COLOR=#ff0000]LVM2[/COLOR] snapshots (specifically):
> *"Snapshots can’t be used as a backup option. Backups are Primary Copies of some data, so we cant use snapshots as a backup option."*
This is not like snapshots of other volume managers in that respect. Let me explain why the is true, specifically for LVM2...

LVM2 snapshots are sort of a special type of Logical Volume (LV), that just tracks "transaction changes". since it was create for the origin pool (LV). If you use the command 'lvs', that will show snapshots and there pool they were made from. They are created in the same VG of the LV you created them in.

When you first create a snapshot, it is empty in size, because there are no changes yet. With every change you make, it adds that change to the snapshot. The default max size of a snapshot is 1GiB. When you create it with lvcreate, you can make that limit bigger or smaller. You can use lvextend to resize it. If that gets over the size of the limit, then the snapshot will adapt to that , by merging that change into the snapshot... So if that snapshot is important to you, you want to keep an eye on the stats of that. SO, like your example, when you formatted an LV, you created more than 1GiB of changes, so it most likely committed those changes to the snapshot. It isn't a backup. It isn't fool-proof. You still need to do "backup's" for data in LVM2. 

In LVM2- If you roll back a snapshot, it rolls back those changes and automatically deletes the snapshot. In fact, it is considered a BUG if it doesn't. Why? Because it is back at Point 0, and none of those tracked changes exist anymore. A work-around for that is to, before rolling back a snapshot, if you are not certain that is what you want to do, that another snapshot... To use that snapshot to roll-back the roll-back, back to the future, re-applying all those changes again.

LVM2 snapshots are r/w. So are vulnerable to corruption and from viruses. They are not 'copies of data'. They rare meant to be temporary and small in size. But they are great for rolling back "changes" to a point in time... They are considered as a type Copy-on-write snapshots, but more tied to the meta-data and changes, rather than the actual data.

Copy-on-write snapshots take a copy of the metadata of the target volume into the snapshot pool. Then, depending on which mode of COW they are using, they copy data that would be overwritten by new writes to the snapshot pool before writing the new data. It is tied to the source LV and the VG it resides in. That varies a bit from ZFS snapshots.

ZFS and BTRFS have full-snapshot capabilities, which is useful for moving onto separate media, which in turn is very handy for backup systems using removable media. ZFS refers to those as "snapshot" datasets, and leverage ZFS's ability to use zfs send and zfs recv to copy volumes and snapshots over the network to a remote host or another local array/pool. BTRFS has something similar.

Sorry, I tried to keep it short.

---

### Post by Quarkrad on 2023-10-24
Thank you - that explains a lot of muddle in my head.  Bearing in mind I use ext4 for everything what would you suggest is the best method (for me) to backup one of the 'test' VMs I create?  I have a number of physical HDs in my machine.  The only one that has LVM on it is my 1T nvme ssd that contains a number of LVs including ones for **/ **and **/home**.  I also create additional LVs on this ssd that contain 'test' kvm VMs.  For my critical/personal data on this lvm ssd I use rdiff-backup to backup to a physically different HD.  This methodology works well for me.  I guess what I'm after is the ability to backup a 'day1' install of a test VM (that is in a LV) so that if things get messed up I can re-install back to 'day 1' quickly rather than re-install from fresh.  I though snapshot was my answer but perhaps it is not.

---

### Post by TheFu on 2023-10-24
When an LVM snapshot is created, the old LV blocks are frozen (unchangeable) and the new created area is where all changes go. 
I looked for a 5 step image to show this more clearly, but didn't find any. Sorry.

---

### Post by #&amp;thj^% on 2023-10-24
I was hoping TheFu would come in, it is rather hard to relay what and we do to other users, to fit their plan or concept.
If I tried to explain mine, >>>mine, yours, and visitors minds would just reel and spin.
I try to keep it simple and in small steps.

---

### Post by MAFoElffen on 2023-10-24
I know it is "not efficient" but this works for me.

I create a library of installs of certain types of VM templates. They have updates done to them and are current, but they are static examples of different config types and releases. I can quickly clone one of these VM Templates and spin it up to use as something temporary. They do not need to have large storage. VM Images can be resized quickly.

I do a lot of testing. Especially for "here", working out problems  for users. I spin up an instance, break it like they did to recreate a  problem, then see if I can fix it. That way I know something will work  before I recommend doing something. And doing it that way, I can take screenshots of how it is done, to help new users who need that something "extra" to help them along.

I also use these to try or learn new things. If I think I'm going to frag something and I want to get back to that point in a hurry, I'll make a copy of the VM image file, for the just in case. Remove/delete the old image. Add/attach to the backup image. Takes less than 20 seconds.

Doing "that" saves me a lot of time. VM Guest (along with it's image) is just files.  Some things just make sense to me to do for something temporary. Other's that are going to be around for a while, I spend more time and thought on.

---

