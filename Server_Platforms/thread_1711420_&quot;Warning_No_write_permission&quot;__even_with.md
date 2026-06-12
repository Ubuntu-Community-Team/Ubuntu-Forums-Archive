---
title: "&quot;Warning: No write permission&quot;  even with root"
date: 2011-03-21
forum: Server Platforms
---

### Post by mkhurram92 on 2011-03-21
hello all,

i am using Ubuntu 10.10 and login using root on terminal
but when i want to edit any file i get this error

"Warning: No write permission"

Also see the result of dhcp restart

root@webmin:~# /etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail]
* Starting DHCP server dhcpd3 chown: changing ownership of `/var/lib/dhcp3': Read-only file system
chown: changing ownership of `/var/lib/dhcp3/dhcpd.leases': Read-only file system
chown: changing ownership of `/var/lib/dhcp3/dhcpd.leases~': Read-only file system
* check syslog for diagnostics.


My System was working fine in the morning...
what happened i dont know and i m very confused about this situation 

Pls Help

Best Regards

---

### Post by BkkBonanza on 2011-03-21
Have a look at your logs, /var/boot.log, /var/log/messages
You may see that the root filesystem was mounted read only. This happens when a problem is detected at boot. 

Probably you should run a fsck on the root partition. You should reboot and from the grub boot menu choose recovery/rescue mode and run the fsck.

eg.

fsck /dev/sda

Another way is to do **touch /forcefsck** and reboot. BUt if the filesystem is read-only this may not work. Or perhaps **shutdown -rF now** may tag the drive for fsck after starting next time.

---

### Post by SeijiSensei on 2011-03-21
> **BkkBonanza said:**
> fsck /dev/sda

You need to specify the partition on which the filesystem is stored, e.g., "fsck /dev/sda**1**".  Otherwise, I'm sure BKKBonanza is correct that the filesystem has errors so Linux refuses to mount it read/write.  That's usually the problem behind "read-only filesystem" errors.

---

### Post by BkkBonanza on 2011-03-21
Yes. My mistake - don't know why I left off the number.

---

### Post by SeijiSensei on 2011-03-21
> **BkkBonanza said:**
> Yes. My mistake - don't know why I left off the number.

We're all busy and distracted.  We all make mistakes.  Don't sweat it!

---

### Post by cipherboy_loc on 2011-03-21
If you get the error again (after the fsck), try running:

```

mount

```

to tell you if the directory is read write (rw) or read only (ro).



Cipherboy

---

### Post by mkhurram92 on 2011-03-22
hi guys 

thanks all for help 

my problem has been resolved... I just restart my system and its working fine now... ;)

coz shutdown -rF now was now working on it then


Best Regards
Jazaib Hussain

---

