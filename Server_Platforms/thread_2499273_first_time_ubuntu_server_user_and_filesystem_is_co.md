---
title: "first time ubuntu server user and filesystem is confusing me"
date: 2024-07-21
forum: Server Platforms
---

### Post by simtaalo on 2024-07-21
Hi all, it's the first time I've used Ubuntu Server. When setting up the hard drive I chose the standard option. But now that I'm looking at the file system I'm quite confused about how it's setup.

This is the result of **lsblk** command

```
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0                       7:0    0  63.9M  1 loop /snap/core20/2318
loop1                       7:1    0  63.9M  1 loop /snap/core20/2105
loop2                       7:2    0  40.4M  1 loop /snap/snapd/20671
loop3                       7:3    0  74.2M  1 loop /snap/core22/1380
loop4                       7:4    0    87M  1 loop /snap/lxd/28373
loop5                       7:5    0  38.8M  1 loop /snap/snapd/21759
loop6                       7:6    0    87M  1 loop /snap/lxd/29351
loop7                       7:7    0     4K  1 loop /snap/bare/5
loop9                       7:9    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop10                      7:10   0 505.1M  1 loop /snap/gnome-42-2204/176
sda                         8:0    0 476.9G  0 disk
&#9500;&#9472;sda1                      8:1    0     1G  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0     2G  0 part /boot
&#9492;&#9472;sda3                      8:3    0 473.9G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 252:0    0   100G  0 lvm  /
```

So **ubuntu--vg-ubuntu--lv** is 100gb inside SDA3 and it has / there, but what I don't understand is how I would be able to use the rest of the space on sda3. This makes me think that anything I install is taking away from the 100gb and not affecting the remaining space on sda3, is that correct?

---

### Post by currentshaft on 2024-07-21
AFAIK the server installation uses less disk space for the primary partition to give you more flexibility later on.

You can change the default sizes in the installer or after installation with lvextend. Let us know if you need help doing so.

---

### Post by TheFu on 2024-07-21
There's a bunch of "fake" storage mounts listed in that output.  You can use a few aliases to hide those, since they have ZERO, NADA, Nothing, to do with actual storage used.  I'll assume you know how to use aliases.

```
alias lsblkt='lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

Somehow, you have LVM, which isn't a bad thing, but beginners usually don't choose it because it adds complexity that you many not want to learn.  OTOH, LVM is very flexible and has been enterprise-grade over 25 yrs on Linux.  It provides some volume manager features that standard partition+file systems don't.

If you want to see the overview of the 3 different LVM objects, use these commands:
```
sudo pvs
sudo vgs
sudo lvs
```

There are many personal choices for storage layouts. Some have security implications that you may want to consider enabling for high risk servers.  For a home server, most people don't.   For example, I'd never all / to be over 35GB in size.  I just wouldn't.  When I'm laying out storage, I'm also designing the backup method to be used and I want different file systems, perhaps with different mount options, to help with my goals.

There are lots of opinions for how to setup LVM. Ask if you are interested, but it doesn't hurt to learn and make less great, difficult-to-fix, choices.  Next time, you'll do better, if it ever matters to you at all.

---

### Post by simtaalo on 2024-07-21
> **currentshaft said:**
> AFAIK the server installation uses less disk space for the primary partition to give you more flexibility later on.

You can change the default sizes in the installer or after installation with lvextend. Let us know if you need help doing so.

Yeah I was wondering if it could be extended. I think the bit I'm confused about is if the main / file system is all in that one partition, how can I install stuff to a different one.


> **TheFu said:**
> There's a bunch of "fake" storage mounts listed in that output.  You can use a few aliases to hide those, since they have ZERO, NADA, Nothing, to do with actual storage used.  I'll assume you know how to use aliases.

```
alias lsblkt='lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```


nice tip

> **TheFu said:**
> 

Somehow, you have LVM, which isn't a bad thing, but beginners usually don't choose it because it adds complexity that you many not want to learn.  OTOH, LVM is very flexible and has been enterprise-grade over 25 yrs on Linux.  It provides some volume manager features that standard partition+file systems don't.

If you want to see the overview of the 3 different LVM objects, use these commands:
```
sudo pvs
sudo vgs
sudo lvs
```

There are many personal choices for storage layouts. Some have security implications that you may want to consider enabling for high risk servers.  For a home server, most people don't.   For example, I'd never all / to be over 35GB in size.  I just wouldn't.  When I'm laying out storage, I'm also designing the backup method to be used and I want different file systems, perhaps with different mount options, to help with my goals.

There are lots of opinions for how to setup LVM. Ask if you are interested, but it doesn't hurt to learn and make less great, difficult-to-fix, choices.  Next time, you'll do better, if it ever matters to you at all.

Whilst it's the first time I've used Ubuntu Server, I've been using Linux off-and-on for years, back to Ubuntu 7 or 8 maybe so using LVM is something I've used before. But previously when it's been setup it's moved things like home into a diff section, I think it being all in one bit has confused me. Although tbf I haven't installed Ubuntu with LVM for many years so I guess it's no surprise things are different.

Output of those commands

```
sudo pvs
  PV         VG        Fmt  Attr PSize    PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <473.89g <373.89g
```

```
sudo vgs
  VG        #PV #LV #SN Attr   VSize    VFree
  ubuntu-vg   1   1   0 wz--n- <473.89g <373.89g
```

```
sudo lvs
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 100.00g
```

So if I'm understanding correctly, there is the volume group ubuntu-vg that contains the logical volume ubuntu-lv where / lives. 

One of the functions I'm planning to use this server for is a self-hosted instance of mattermost so that a local community group can use it. I wanna make sure that couldn't somehow suck away all my space of the main filesystem.

---

### Post by TheFu on 2024-07-22
Seems like you know what you need to do now.
If it were me, I'd reduce the size of ubuntu-lv to 35G, add LVs for swap, home, var and tmp, then boot off an ISO and move the existing files inside ubuntu-lv  to those new LVs and mount them where needed using the fstab.  Reboot back into the main OS, verify all is good, clean up the swapfile (if you didn't do that already), and see how everything is working.  Then you can create a mattersmost-lv, if you like.  Remember, the power in LVM is how easy it is to make an LV larger, but only if the VG has free space.  Also, that VG free space is important for use for snapshops for a number of reasons. For example, here's how I do it:
```
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL       MOUNTPOINT
nvme0n1                          disk                    931.5G                            
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                            
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%             /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M    314M    46%             /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                            
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                            [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 35G   24.7G    23%             /
  &#9500;&#9472;vg01-var01                   lvm   ext4                 20G     14G    23%             /var
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    3.6G     2% tmp01       /tmp
  &#9500;&#9472;vg01-home01                  lvm   ext4                 20G    9.1G    49% home01      /home
  &#9500;&#9472;vg01-libvirt--01             lvm   ext4                137G    2.8G    98% libvirt--01 /var/lib/libvirt
  &#9500;&#9472;vg01-lxd--containers--01     lvm                        30G                            
  &#9492;&#9472;vg01-usrv2404                lvm                        15G
```
The last two in the list are used for LXC containers and KVM/QEMU VMs.  The block storage is provided directly to the VMs.    If you add up all the LVs, you can see I'm using less than 50% of the storage for the SSD.  During backup processing, snapshots are created to hold the change data for the 10 minutes the backups need to get copied off to other storage.  You might note how little storage is used for / and /var.  35GB is overkill for /.
And a different view:```

$ dft
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01                  ext4   35G  7.8G   25G  24% /
/dev/nvme0n1p3                           ext4  672M  309M  314M  50% /boot
/dev/mapper/vg01-home01                  ext4   20G  9.6G  9.1G  52% /home
/dev/mapper/vg01-tmp01                   ext4  3.9G   91M  3.6G   3% /tmp
/dev/mapper/vg01-var01                   ext4   20G  4.5G   15G  25% /var
/dev/nvme0n1p2                           vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-libvirt--01             ext4  134G  131G  2.8G  98% /var/lib/libvirt

```
Of course, storage that isn't mounted doesn't show up.

BTW, this system has about 25 TB of raw storage, but I've not listed the other parts to limit complexities. They also use LVM.

---

### Post by simtaalo on 2024-07-22
> **TheFu said:**
> Seems like you know what you need to do now.
If it were me, I'd reduce the size of ubuntu-lv to 35G, add LVs for swap, home, var and tmp, then boot off an ISO and move the existing files inside ubuntu-lv  to those new LVs and mount them where needed using the fstab.  Reboot back into the main OS, verify all is good, clean up the swapfile (if you didn't do that already), and see how everything is working.  Then you can create a mattersmost-lv, if you like.  Remember, the power in LVM is how easy it is to make an LV larger, but only if the VG has free space.  Also, that VG free space is important for use for snapshops for a number of reasons.


Thanks for that, I had a vague idea but that's helped to order it more &#128077;&#127997;

So the lazy spirit inside me thinks that I could just make a LV for mattermost and still get the safety I need from that being separate but also wouldn't need to do the additional work separating off swap, home, var and tmp. I know it's not super hard work, but it's an extra level of hassle I could sidestep without issue unless I'm missing something.

---

### Post by TheFu on 2024-07-22
> **simtaalo said:**
> Thanks for that, I had a vague idea but that's helped to order it more &#128077;&#127997;

So the lazy spirit inside me thinks that I could just make a LV for mattermost and still get the safety I need from that being separate but also wouldn't need to do the additional work separating off swap, home, var and tmp. I know it's not super hard work, but it's an extra level of hassle I could sidestep without issue unless I'm missing something.

Yep.  Don't know how much safety it provides. Linux doesn't like a full file system and having different LVs mounted with different, defensive, options, can be important. Only you can decide.  As you know, don't let /var fill up.

For backups and snapshots ....  [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html) and a longer version: [https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/](https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/)

---

