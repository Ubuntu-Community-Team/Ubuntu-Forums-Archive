---
title: "Mdadm software raid 1 out of sync but no error. How to check and fix?"
date: 2013-03-04
forum: Server Platforms
---

### Post by chris112233 on 2013-03-04
Hello,

I’ve created a raid 1 with two external usb drives (first test case with two usb-sticks) with the following command:

mdadm --create --verbose /dev/md0 --metadata 1.0 --level=1 --raid-devices=2 /dev/sde1 /dev/sdf1 
I’ve used --metadata 1.0 because with this superblock version I can mount the raid 1 partitions separately with ‘mount –t ext4 … ‘ and with a ext windows driver to access the files if my Ubuntu fileserver has failed.
 
Everything works great but if I mount one partition of the raid 1 separately (‘mount –t ext4 … ‘) and modify the content at the partition (I’ve deleted one file, copied one file, and renamed one file) I expect that the raid is out of sync. 
But I can assemble the raid without any warning or error and mount the file system:

mdadm --assemble –scan
mount /media/md0 
If I now I try to open the files I have modified. The file I’ve deleted at one side is displayed but I can’t open it.
Now I start a raid check:
/usr/share/mdadm/checkarray --cron --fast –quiet /dev/md0

The checkarray does not output any errors or warnings (I’ve checks the syslog).
fsck.ext4 -f /dev/md0 also does not display any errors

Now I mount the two partitions of the raid 1 separately. The displayed files (ls -l ) are equal at both sides (the deleted file is displayed at both side, the copied file is not displayed and the renamed file has the original filename) (How merge mdadm the two sides?)
But I still can open the deleted file only at one side! This mean the raid 1 still must be out of sync.
 
What does /usr/share/mdadm/checkarray exactly do? And how can I sync the array correctly?

Thanks for your answers.

---

### Post by chris112233 on 2013-03-04
I don't have see the following lines in the syslog. But I still can open the deleted file only at one side!

Mar  4 13:47:25 ubuntu3 kernel: [317443.034085] md/raid1:md0: not clean -- starting background reconstruction
Mar  4 13:47:25 ubuntu3 kernel: [317443.034098] md/raid1:md0: active with 2 out of 2 mirrors
Mar  4 13:47:25 ubuntu3 kernel: [317443.034191] md0: detected capacity change from 0 to 3798925312
Mar  4 13:47:25 ubuntu3 kernel: [317443.041943]  md0: unknown partition table
Mar  4 13:47:25 ubuntu3 kernel: [317443.047957] md: resync of RAID array md0
Mar  4 13:47:25 ubuntu3 kernel: [317443.047967] md: minimum _guaranteed_  speed: 100000 KB/sec/disk.
Mar  4 13:47:25 ubuntu3 kernel: [317443.047976] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Mar  4 13:47:25 ubuntu3 kernel: [317443.047987] md: using 128k window, over a total of 3709888k.
Mar  4 13:49:52 ubuntu3 kernel: [317589.571733] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
Mar  4 13:58:16 ubuntu3 kernel: [318094.020171] md: md0: resync done.

If I assemble and mount the raid, one time a can open the file, one time I can't.
I' don't unterstand this behavior ...

---

