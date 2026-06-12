---
title: "raid / grub configuration issue"
date: 2009-04-26
forum: Server Platforms
---

### Post by maclenin on 2009-04-26
With reference to this earlier post re: my _[raid / lvm configuration]("http://ubuntuforums.org/showpost.php?p=7134682&postcount=4")_ and eventual installation...

...I am trying to resolve what seems to be a grub-related wrinkle:  

a. I have discovered that the system does **not** boot from the bootable md0 array, consisting of...
```
sda1 - RAID1 - (md0) - ext3 - /boot (500mb)
sdb1 - RAID1 - (md0) - ext3 - /boot (500mb)
```
b. The system boots, instead, from the "plain vanilla" (non-RAID and non-LVM) sdc1 partition...
```
sdc1 - ext3 - /boot (500mb)
```
c. grub> find /grub/stage1 indicates...
```
(hd2,0)
```
d. /dev/sdc1 **does** show up in fstab with /boot as it's mount point.

e. /dev/md0 (the bootable RAID1 array) does **not** show up in fstab.

All else seems to be in good order:

f. The md0 array shows up as it should when I run mdadm diagnostics.

g. fdisk -l shows all partitions (sda1, sdb1, sdc1) configured as bootable ("*").

Questions:

1. How can I make the md0 array bootable (as I had originally intended) and what do I need to do with regard to grub and fstab to fix the wrinkle?

2. Could it be that when the partition tables were being finalized during install - that the /dev/sdc1 /boot partition was somehow given priority to the /dev/md0 /boot "array" - and, therefore, added to fstab (and assigned some grub) by the installer while /dev/md0 was not?

3. Might it just be a "simple" matter of making certain that grub is properly installed or configured on the /dev/md0 array?

4. How can I tell whether things are (already) set up properly - grub-wise?

5. Might it just be a "simple" matter of adding the /dev/md0 array to fstab?

6. Any thoughts as to why /dev/md0 would not have been added to fstab during install?

7. Can multiple /boot partitions share a single fstab file?

Thanks for any insights....

---

### Post by maclenin on 2009-04-27
Following-up on my original post (and with reference to [_this configuration_]("http://ubuntuforums.org/showpost.php?p=7134682&postcount=4")):

8. According to blkid -L, the bootable md0 array (consisting of bootable partitions sda1 and sdb1) is not mounted. Could this be a reason that (hd0,0) and (hd1,0) don't show up when I run ">grub find /grub/stage1"?

9. How can I find out whether grub is properly installed on the unmounted md0 array?

9.a. Could I temporarily mount (and then umount) the md0 raid array into a random "/findtest" directory for the purposes of having ">grub find" take a look to see if the grub files are present within the array?

10. Might a simple commenting out or replacement of sdc1 in fstab with /dev/md0 be the solution to getting the system to boot from md0?

10.a. I would like to use a uuid for /dev/md0 in fstab - would the uuid I enter for "/dev/md0" be that of "md0"? Or would the uuid of "/dev/md0" be that of "sda1" - which is the "primary" bootable partition of the md0 array? Should I not use a uuid for /dev/md0 in fstab?

11. Does "dev/sdc1" need to be removed or commented out of fstab - or can it be re-assigned to another mount point - rendering it accessible (at boot) - if need be (see 12. and 13.)?

NOTE: **Before** I revise fstab and reboot:

12. I'd like to set up a [_fallback_]("http://www.gnu.org/software/grub/manual/grub.html#Booting-fallback-systems") situation - where if the md0 array won't boot (as I now try to configure it properly - or sometime in the future) the system could be directed to boot from sdc1 - which I know works. The issue is how do I make sdc1 "bootable" without adding it to /boot in fstab? Would grub be able to boot from sdc1 if sdc1 (or it's uuid) were present in menu.lst, but not in fstab?

13. Can I just set up a situation where the grub menu (at boot via ESC) gives me the option to boot from either the raid array (md0) or the vanilla partition (sdc1)?

Thanks for any guidance!

---

### Post by maclenin on 2009-04-28
...with the aid of large swaths of google, I feel I might finally be approaching a practical resolution to this grub issue.

Here's a preliminary framework:

h. Create a [_grub-bootable "rescue" cd-rom (stage2_eltorito)_]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html")

i. Test the rescue cd-rom to see whether it works as I think it should - i.e. boots into my system exactly the way it would if I were booting from my hard drive.... 

j. Reboot the system without the rescue cd-rom

k. Add the active/bootable /dev/md0 (sda1 and sdb1) array to fstab at the mount point /boot

l. Keep the active/bootable /dev/sdc1 parition in fstab at the mount point /boot

m. Modify menu.lst to set /dev/md0 as the default boot entry.

n. Modify menu.lst to set /dev/sdc1 as the fallback boot entry.

o. Reboot and be done (with this task)....

Questions:

14. Given that the active partitions /dev/md0 and /dev/sdc1 are ("legally") on separate drives, why then was /dev/md0 NOT automatically added to fstab during install? Can two arrays or partitions (even though on separate disks) not share the same mount point "title" (e.g. /boot)?

15. Restated: Is it possible for /dev/md0 and /dev/sdc1 to share the same mount point in fstab?

16. Will I need to "update-grub" menu.lst, somehow, in order for my manually-entered menu.lst changes to take effect? Or, should this "update-grub" happen, automatically, at reboot?

17. Is there anything I am missing?

Thanks for any knowledge....

---

### Post by maclenin on 2009-05-01
Any comments?

---

### Post by maclenin on 2009-05-03
... _ _ _ ...
... _ _ _ ...
... _ _ _ ...

---

