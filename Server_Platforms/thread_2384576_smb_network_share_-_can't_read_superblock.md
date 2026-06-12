---
title: "smb network share - can't read superblock"
date: 2018-02-08
forum: Server Platforms
---

### Post by jamarsh123 on 2018-02-08
Desktop computer with Ubuntu 16.04 has been connecting to ubuntu server 14.04 samba with no issues. Now, the shares cannot be mounted. Message says "can't read superblock." Other desktops with similar setup are able to connect.

---

### Post by wildmanne39 on 2018-02-08
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by LHammonds on 2018-02-08
> **jamarsh123 said:**
> Desktop computer with Ubuntu 16.04 has been connecting to ubuntu server 14.04 samba with no issues. Now, the shares cannot be mounted. Message says "can't read superblock." Other desktops with similar setup are able to connect.
What format is the file system of the share?  EXT4?  NTFS?  FAT32?  I've heard of intermittent issues with NTFS-formatted filesystems on Linux.

LHammonds

---

### Post by jamarsh123 on 2018-02-08
The server is Ubuntu 14.04
sda1 is ext2
sda5 is crypto_LUKS
/dev/mapper/ubuntu--vg-root TYPE="ext4"

---

### Post by jamarsh123 on 2018-02-08
Just found out that a second computer, laptop, is experiencing the same issue. So, 3 computers are fine, and 2 are unable to connect to the server, and are displaying the same message: can't read superblock.

---

### Post by LHammonds on 2018-02-09
I'm not familiar with that encryption but I have to wonder if there is some corruption messing with you.

---

### Post by jamarsh123 on 2018-02-09
Thanks for you replies. Not sure how, but I've managed to solve the problem. I've posted my solution to the main thread.

---

### Post by QIII on 2018-02-09
Which "main thread" is that?

---

### Post by jamarsh123 on 2018-02-09
Well, I've managed to solve the problem. Every time I rebooted a workstation, it lost connection to the server. This confirmed that the server was the problem and not the workstations.

I booted with live CD and ran some fsck commands to repair the superblock. This did not work. I was considering restoring a full backup restore of the server. In a last ditch effort, I ran these 2 voodoo commands on the server, which, inexplicably, restored server connectivity for all workstations.

sudo apt-get update
sudo apt-get dist-upgrade

It came to mind because I recently had a laptop that suddenly lost drivers for the modem. The commands above restored the modem.

At any rate, I don't understand how, but we can consider the issue solved.

---

