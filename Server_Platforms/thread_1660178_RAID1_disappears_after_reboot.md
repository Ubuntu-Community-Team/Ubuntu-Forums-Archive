---
title: "RAID1 disappears after reboot?"
date: 2011-01-05
forum: Server Platforms
---

### Post by HimeNoHogosha on 2011-01-05
I had a thread earlier asking for help installing Ubuntu Server to my homemade atom based NAS, but I gave up on that (GUI's are more helpful to me :P) and so now I'm running Ubuntu 10.10 Desktop 64bit edition.

Last night I was finally able to get mdadm set up. I have two 1TB disks set up in RAID1 config. I used ```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
``` to create the array, and then waited until it finished assembling. Then I used System>Administration>Disk Utility to create a ext4 partition on the /dev/md0p1 device.

Finally, I modified /etc/fstab in the following manner ```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0


UUID=a58e62e0-e3b5-438c-98d5-23268689ea84 /media/galaxy ext4 defaults 0 0
``` to try and automount the raid partition.

After rebooting however, Ubuntu said it was waiting for /media/galaxy to be mounted. After a few minutes I decided to skip it, and noticed that /dev/md0 was no longer available. I ran ```
ls -l /dev/disk/by-uuid
``` but there was no listing of my raid device. I tried to click my way around. In Disk Utility again, I could see a 0.0Kb raid array, clicked 'Stop RAID Array', then 'Start RAID Array', and suddenly my 1TB /dev/md0 array reappeared! 

I'm not sure what I just did, but I'm hoping somebody can tell me what step I might have missed. Do I need to do something to have mdadm properly load the raid array upon bootup?

---

### Post by HimeNoHogosha on 2011-01-07
Searched more carefully again and solved my own problem with this thread : [http://ubuntuforums.org/showthread.php?t=1225334&highlight=mdadm]("http://ubuntuforums.org/showthread.php?t=1225334&highlight=mdadm")

Yay forums!

---

