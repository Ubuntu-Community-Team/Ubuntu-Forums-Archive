---
title: "System will not boot"
date: 2009-11-10
forum: Server Platforms
---

### Post by mrdaze0 on 2009-11-10
Hi, I rebooted my system this morning after attempting an upgrade to the newest release....when rebooting the system will not go past mountall it stops on mount: /media/sdb waiting for /dev/sdb1

What can i do to fix this?

---

### Post by prshah on 2009-11-10
> **mrdaze0 said:**
> Hi, I rebooted my system this morning after attempting an upgrade to the newest release....when rebooting the system will not go past mountall it stops on mount: /media/sdb waiting for /dev/sdb1

I had the same problem on my laptop (I had completed the upgrade successfully). The only way I could solve it was by commenting out the offending UUID in /etc/fstab; fortunately it referred to my fat32 Windows partition and not "/" or "/home". I still have to leave it commented out; everytime I enable it I land up with the same error as you.

This means that my Windows partition is now not automatically mounted; I have to doubleclick it in Nautilus to mount it. This also means that my documents created in that partition are not indexed by Google Desktop.

I suggest you try to comment out the stated partition ID (/dev/sdb1) from your /etc/fstab, if it does not refer to a linux partition. To access the file, you will need a live CD; boot off it, open a terminal (Applications-Accessories-Terminal), then use the following commands:```
sudo mount /dev/sdX9 /mnt -o defaults,rw
sudo pico /mnt/etc/fstab
#comment out the relevant UUIDs / partition (/dev/sdb1)
#by placing a "#" at the beginning of the relevant lines
#Ctrl-X to quit pico; save when prompted
sudo umount /mnt
sudo reboot

```

Important: replace /dev/sdX9 with the linux partition ID that contains the "/" (root) filesystem.

Post back if you need more help, or with feedback.

---

