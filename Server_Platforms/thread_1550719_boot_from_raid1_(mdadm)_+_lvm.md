---
title: "boot from raid1 (mdadm) + lvm"
date: 2010-08-11
forum: Server Platforms
---

### Post by Ztoragefool on 2010-08-11
hello - i am new in here, hopefully to find enlightenment regarding my problem...

intending to set up an all-in-one server, i threw in the ubuntu server 10.04 (amd64) cd. 

during the text-install, i set up the device-topology below, and it worked. 

```


            LVM           mdadm       part

 sys  --                           -- sda1
        \                         /
 swap ------ VG --- PD --- md0 ---
        /                         \
 data --                           -- sdb1


```then i tested my raid by hot-pulling off the sda wire (ouch).  worked fine, system still worked, and it also managed rebooting from the  left sdb (which of course showed up being sda, lacking the first  drive). 

now i am trying to recover this pre-crash state. adding the first disk  (showing up as sdb), i can add it to md0 and let it start syncronizing  for 2 hours. but... i can´t boot anymore with the recovered first disk  being sda...

at first, booting got stuck in an initrd-prompt after complaining it couldn´t find my sys-logical volume. 

after a lot of trial and error i don´t even get any complaints, just a  black screen which would let me wait for a boot for weeks...

so, my system does not boot from my first disk, whether i plug in the  second or not. my second disk still boots. my last attempt to get  booting fine again has been:

[LIST]
[*]zero sda´s first and last gigabyte to kill any ids
[*]duplicate sdb´s first cylinder to sda to make it bootable
[*]reinitialize sdb´s part.table using command o in fdisk for a new disk-id
[*]recreate sda1 partition
[*]add sda1 to md0
[/LIST]
:popcorn:
ok, hope you enjoyed the show. now who can tell me what the heck is wrong?

thanks!

---

### Post by Ztoragefool on 2010-08-12
ok, 

it´s been nice talking about it. error turned out to reside right in front of the screen... again.

to compare both disk´s bootsector, i used the dd command to dump them into files, then i used cmp -l command to find that the mbr of sda has been zeroed - althoug i already copied it from sdb. so i guess it´s been the o command in fdisk which did not just initialize the partition table including a new disk id, but destroy the bootcode. 

copied once again, now both disks boot and i am happy. 

this does not explain my first symptom where initrd couldn´t proceed booting, but doing it all again i must have corrected whichever mistake i´ve made before. doesn´t matter anymore. 

have a nice day!

---

