---
title: "Patch for 's' file attribute in ext4 filesystem?"
date: 2010-06-22
forum: Security
---

### Post by WinstonChurchill on 2010-06-22
The manpage for 'chattr' command includes the following:> When a file with the 's' attribute set is deleted, its blocks are zeroed and written back to the disk.  Note: please make sure to read the bugs and limitations section at the end of this document.... which seems pretty slick, but in the aforementioned "bugs and limitations" section, it says this:> The 'c', 's',  and 'u' attributes are not honored by the ext2 and ext3 filesystems as implemented in the current mainline Linux kernels. These attributes may be implemented in future versions of the ext2 and ext3 filesystems. This attribute isn't supported in ext4 either (see below). This seems like an incredibly convenient way to securely overwrite files - does anybody know of a patch to allow this? A little light google-ing didn't turn anything up...

The attribute not working: (and shred working as expected)
```
root@Linux:/# mount /dev/sdb1 /mnt
root@Linux:/# echo "JJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJ" > /mnt/thing.txt
root@Linux:/# umount /mnt
root@Linux:/# hexdump -C /dev/sdb1 | grep "JJJJJJJJJJJJJJJJ"
00840c00  4a 4a 4a 4a 4a 4a 4a 4a  4a 4a 4a 4a 4a 4a 4a 4a  |JJJJJJJJJJJJJJJJ|
root@Linux:/# mount /dev/sdb1 /mnt
root@Linux:/# rm -rf /mnt/thing.txt
root@Linux:/# umount /mnt
root@Linux:/# hexdump -C /dev/sdb1 | grep "JJJJJJJJJJJJJJJJ"
00840c00  4a 4a 4a 4a 4a 4a 4a 4a  4a 4a 4a 4a 4a 4a 4a 4a  |JJJJJJJJJJJJJJJJ|
root@Linux:/# mount /dev/sdb1 /mnt
root@Linux:/# echo "KKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK" > /mnt/thing2.txt
root@Linux:/# chattr +s /mnt/thing2.txt
root@Linux:/# umount /mnt
root@Linux:/# hexdump -C /dev/sdb1 | grep "KKKKKKKKKKKKKKKK"
00840c00  4b 4b 4b 4b 4b 4b 4b 4b  4b 4b 4b 4b 4b 4b 4b 4b  |KKKKKKKKKKKKKKKK|
root@Linux:/# mount /dev/sdb1 /mnt
root@Linux:/# lsattr /mnt
s----------------e- /mnt/thing2.txt
root@Linux:/# rm -rf /mnt/thing2.txt
root@Linux:/# umount /mnt
root@Linux:/# hexdump -C /dev/sdb1 | grep "KKKKKKKKKKKKKKKK"
00840c00  4b 4b 4b 4b 4b 4b 4b 4b  4b 4b 4b 4b 4b 4b 4b 4b  |KKKKKKKKKKKKKKKK|
root@Linux:/# mount /dev/sdb1 /mnt
root@Linux:/# shred /mnt/thing2.txt
root@Linux:/# umount /mnt
root@Linux:/# hexdump -C /dev/sdb1 | grep "KKKKKKKKKKKKKKKK"
root@Linux:/# exit
```

---

