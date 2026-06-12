---
title: "Add raid5 to fstab - can't get syntax"
date: 2014-03-28
forum: Server Platforms
---

### Post by m0rph3us0306 on 2014-03-28
Trying to setup a plexserver (actually that part is running), but I have an external ICY DOC with (4) 750G disks in a raid5.  The disk mounts fine, can share via samba, but the plexserver can't add and from my reading, it seems the mask is wrong (basically a permission issue).   So I want to add it to the fstab file, but I can't figure out the FS type (made this a while back).

The disk is mounted, works fine, and an *fdisk -l* shows;
[SIZE=1]Disk /dev/md0: 2250.5 GB, 2250460102656 bytes
2 heads, 4 sectors/track, 549428736 cylinders, total 4395429888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000
Disk /dev/md0 doesn't contain a valid partition table[/SIZE]

Not sure how that's possible as df -h shows it fine (and as I said I can use it fine).
[SIZE=1]/dev/md0        2.1T  1.4T  568G  72% /home/user/data
[/SIZE]
So in short, I need to see how to basically auto mount this external disk in the fstab.  The fix from the forum has the user enter the following;
LABEL[COLOR=#666600]=[/COLOR]DATA  [COLOR=#666600]/[/COLOR]media[COLOR=#666600]/[/COLOR]data  ntfs[COLOR=#666600]-[/COLOR][COLOR=#006666]3g[/COLOR]  defaults[COLOR=#666600],[/COLOR]umask[COLOR=#666600]=[/COLOR][COLOR=#006666]0022[/COLOR][COLOR=#666600],[/COLOR]fmask[COLOR=#666600]=[/COLOR][COLOR=#006666]0133[/COLOR]  [COLOR=#006666]0[/COLOR]  [COLOR=#006666]0.
[/COLOR]
But I know I don't have the partition set as ntfs, and an fdisk /dev/disk1, etc. all have invalid partition table.

Thanks for all read/replies.

---

### Post by bab1 on 2014-03-29
> **Lace said:**
> Trying to setup a plexserver (actually that part is running), but I have an external ICY DOC with (4) 750G disks in a raid5.  The disk mounts fine, can share via samba, but the plexserver can't add and from my reading, it seems the mask is wrong (basically a permission issue).   So I want to add it to the fstab file, but I can't figure out the FS type (made this a while back).

The disk is mounted, works fine, and an *fdisk -l* shows;
[SIZE=1]Disk /dev/md0: 2250.5 GB, 2250460102656 bytes
2 heads, 4 sectors/track, 549428736 cylinders, total 4395429888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000
Disk /dev/md0 doesn't contain a valid partition table[/SIZE]

Not sure how that's possible as df -h shows it fine (and as I said I can use it fine).
[SIZE=1]/dev/md0        2.1T  1.4T  568G  72% /home/user/data
[/SIZE]
So in short, I need to see how to basically auto mount this external disk in the fstab.  The fix from the forum has the user enter the following;
LABEL[COLOR=#666600]=[/COLOR]DATA  [COLOR=#666600]/[/COLOR]media[COLOR=#666600]/[/COLOR]data  ntfs[COLOR=#666600]-[/COLOR][COLOR=#006666]3g[/COLOR]  defaults[COLOR=#666600],[/COLOR]umask[COLOR=#666600]=[/COLOR][COLOR=#006666]0022[/COLOR][COLOR=#666600],[/COLOR]fmask[COLOR=#666600]=[/COLOR][COLOR=#006666]0133[/COLOR]  [COLOR=#006666]0[/COLOR]  [COLOR=#006666]0.
[/COLOR]
But I know I don't have the partition set as ntfs, and an fdisk /dev/disk1, etc. all have invalid partition table.

Thanks for all read/replies.
I think you can mount the array with a UUID instead of a LABEL.  Post the output of this```

sudo blkid -c /dev/null -o list

```...if this works you should see the array and the FS on it.

If the FS is NTFS,  you will need to set the ownership and permissions at mount time.  NTFS doesn't understand chmod or chown.

---

### Post by m0rph3us0306 on 2014-03-29
Thanks.   That did confirm;

/dev/md0                                        ext4            data             (not mounted)                                       998bc24c-fcd5-4abe-996e-9f38270a8cdf

So, I have posted a comment/question on the plex forums, as the disk is mounted, works local and from samba on remote machines now, plex server just won't show anything in the add media section.  In an old post they suggested adding [COLOR=#000000]defaults[/COLOR][COLOR=#666600],[/COLOR][COLOR=#000000]umask[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]0022[/COLOR][COLOR=#666600],[/COLOR][COLOR=#000000]fmask[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]0133[/COLOR][COLOR=#000000] [/COLOR][COLOR=#006666]0[/COLOR][COLOR=#000000] [/COLOR][COLOR=#006666]0 to the end of the fstab but mounting was throwing errors (both umask/fmask) which I wasn't sure if you could do.

So I will see what they say as things are mounted and confirmed on the server side.

Thanks.[/COLOR]

---

### Post by bab1 on 2014-03-29
> **Lace said:**
> Thanks.   That did confirm;

/dev/md0                                        ext4            data             (not mounted)                                       998bc24c-fcd5-4abe-996e-9f38270a8cdf

So, I have posted a comment/question on the plex forums, as the disk is mounted, works local and from samba on remote machines now, plex server just won't show anything in the add media section.  In an old post they suggested adding [COLOR=#000000]defaults[/COLOR][COLOR=#666600],[/COLOR][COLOR=#000000]umask[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]0022[/COLOR][COLOR=#666600],[/COLOR][COLOR=#000000]fmask[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]0133[/COLOR][COLOR=#000000] [/COLOR][COLOR=#006666]0[/COLOR][COLOR=#000000] [/COLOR][COLOR=#006666]0 to the end of the fstab but mounting was throwing errors (both umask/fmask) which I wasn't sure if you could do.

So I will see what they say as things are mounted and confirmed on the server side.

Thanks.[/COLOR]

There is no *fmask=013300* The files should never be more than 0000 and not less than 0666.  When a file is created it is with permissions of 666 and the mask removes permissions.  Since this is ext the default umask of 0022 or 0002 is fine.  Since this is the default you don't really need to declare it.

---

