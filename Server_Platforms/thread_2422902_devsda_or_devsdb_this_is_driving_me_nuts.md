---
title: "/dev/sda or /dev/sdb this is driving me nuts"
date: 2019-07-14
forum: Server Platforms
---

### Post by David_Partridge on 2019-07-14
I have two "drives" in my system: A SATA SSD and a SAS RAID array

When the system starts up sometimes the SATA drive is assigned /dev/sda and the RAID array /dev/sdb, but other times it comes out the other way round :(

This means that my entries in smartd.conf are incorrect quite often!   The lastest boot came up with the RAID array as /dev/sda so I needed to change smartd.conf AGAIN :(

```
/dev/sdb -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
#
/dev/sda -d aacraid,0,0,0 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d aacraid,0,0,1 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d aacraid,0,0,2 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d aacraid,0,0,3 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d aacraid,0,0,4 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d aacraid,0,0,5 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d aacraid,0,0,6 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d aacraid,0,0,7 -n standby -W 0,0,55 -m david.partridge@xxx -M exec /usr/share/smartmontools/smartd-runner
```

Is there any way I can get this to behave consistently?

Thanks
David

---

### Post by oldfred on 2019-07-14
Do not know RAID and will move post to server sub-forum where those who know RAID may be able to help.

Linux stopped using device for mounting many years ago, for the reasons you post. Drive order depending on BIOS/UEFI startup order of drives. Generally standard SATA drives come up in SATA port order, but other drives may not depending on time to spin up or be seen by system.
My flash drives at sdf on reboot become sda. So not uncommon issue.
I have changed to use labels so I can control device & has a useful id not long UUID, Linux uses UUID normally which only changes if you reformat a partition.

Post these:
lsblk -f
cat /etc/fstab

If RAID does not come up to speed as fast as SSD boots, you may need to not use fstab to mount, but have script at end of boot process. 
Or change settings in fstab

       [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections
use noauto if mount issues
[https://askubuntu.com/questions/1047109/how-can-i-delay-mount-of-secondary-internal-hard-drive-on-boot?noredirect=1#comment1710066_1047109](https://askubuntu.com/questions/1047109/how-can-i-delay-mount-of-secondary-internal-hard-drive-on-boot?noredirect=1#comment1710066_1047109)

---

### Post by David_Partridge on 2019-07-14
There's no chance the RAID comes ready after the boot process has started.  The RAID card has the RAID array ready for use before the BIOS is given control to boot the system.

```

root@Charon:/home/amonra# lsblk -f
NAME                  FSTYPE      LABEL  UUID                                   MOUNTPOINT
sda                                                                             
&#9492;&#9472;sda1                btrfs       Shared cf914647-a613-4ced-b3d8-cda423c48ac5   /shared
sdb                                                                             
&#9500;&#9472;sdb2                                                                          
&#9500;&#9472;sdb5                LVM2_member        QEmshk-WXVY-JJjh-eEDj-KRq1-FnGa-D2MyHc 
&#9474; &#9500;&#9472;Charon--vg-root   btrfs              dbe7f6e2-81d3-4097-8b35-eace3e125d41   /home
&#9474; &#9492;&#9472;Charon--vg-swap_1 swap               ece2e724-3fc3-48af-aab9-5672000bd436   
&#9492;&#9472;sdb6                LVM2_member        z72BfN-lwcN-K9IJ-gY9D-tRuF-4Y9c-1iFe89 
  &#9492;&#9472;Charon--vg-root   btrfs              dbe7f6e2-81d3-4097-8b35-eace3e125d41   /home
sr0                                                                             
root@Charon:/home/amonra# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>         <type>   <options>                    <dump>  <pass>
/dev/mapper/Charon--vg-root /          btrfs   defaults,subvol=@             0       1
/dev/mapper/Charon--vg-root /home      btrfs   defaults,subvol=@home         0       2
# UUID=1ed72a7b-093b-4e88-a3b5-19c02a0eee5f /boot defaults                     0       0
#
UUID=cf914647-a613-4ced-b3d8-cda423c48ac5 /shared btrfs    defaults,subvol=@    0       1

root@Charon:/home/amonra#
```

Cheers
David

---

### Post by sisco311 on 2019-07-14
Instead of /dev/sdX use the symlink(s) from /dev/disk/by-id

---

### Post by David_Partridge on 2019-07-14
Thank you,

/dev/disk/by-path/pci-0000:00:17.0-ata-1
/dev/disk/by-path/pci-0000:01:00.0-scsi-0:0:0:0
 
Saved the day, though I'm sure I could use the /dev/disk/by-id links instead.

Thanks again

---

### Post by wildmanne39 on 2019-07-14
Moved to the server sub-forum as we believe you will have better opportunity to have your issue resolved here.

---

