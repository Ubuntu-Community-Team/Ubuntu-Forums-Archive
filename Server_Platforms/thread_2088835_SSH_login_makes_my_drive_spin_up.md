---
title: "SSH login makes my drive spin up"
date: 2012-11-27
forum: Server Platforms
---

### Post by xeerf on 2012-11-27
Hi,

I have Ubuntu Server installed on SSD disk with one classic rotating magnetic disk attached. It is configured by hdparm on every boot to spin down after few hours of idle time. Also, there are some folders shared over SMB and FTP on magnetic drive. It's working flawlessly, every time I access the server using SMB or FTP it spins up and after some time it spin down again.
But when I login through SSH, it also spins up the magnetic drive. That's wrong. There are no system files located on the drive (not even home directory of course) neither the drive is referred in login script. Can you help me please?

---

### Post by lykwydchykyn on 2012-11-27
Not sure, but one theory is that update-motd is doing something that accesses this disk.  Update-motd runs on every ssh or terminal login to update that system status info you see when you log in.  Maybe check out the scripts in /etc/update-motd.d and see if any of them is doing something that might require files on the disk.

---

### Post by xeerf on 2012-11-27
Thanks for the helpful advise, I will try to put some debug messages to see if any of these scripts is waiting for drive to spin up.

---

### Post by CharlesA on 2012-11-27
> **lykwydchykyn said:**
> Not sure, but one theory is that update-motd is doing something that accesses this disk.  Update-motd runs on every ssh or terminal login to update that system status info you see when you log in.  Maybe check out the scripts in /etc/update-motd.d and see if any of them is doing something that might require files on the disk.
That's probably it. I remember getting a message saying / is 90% full when logging in via ssh before. I assume the same goes for any drives that are mounted.

---

### Post by markbl on 2012-11-27
I'll throw this in although it may not be relevant.

This exact problem was happening to me on a Solaris server once and it was due to file quota checking. When a user logs in his usage quota is checked across all disks. The solution was to turn off quota checking for the specific partition in /etc/fstab.

---

### Post by xeerf on 2012-11-29
I have tried to put some debug scripts into /etc/update-motd.d and I can confirm that it wasn't the problem. Drive is spun on before any of these script writes anything on the screen. I tried to turn off quotas in fstab, but attribute *quotaoff* that I have found is not working for EXT4 filesystem. Maybe it will be working at least for bound folders in fstab.

---

