---
title: "Bind9, postfix, mysql not starting on boot after update"
date: 2011-03-04
forum: Server Platforms
---

### Post by Neil Smith on 2011-03-04
Ubuntu Server 10.04.2 LTS.

Yesterday, everything was working fine, with lots of services running.

This morning, I updated the latest security patches and rebooted the server.

After the reboot, apache2, cupsd, dovecot, and sshd started normally.

However, bind9, postfix, mysql, git-daemon, and my homebrew iptables did not start automatically.

Manually starting the services brings them up perfectly fine.

Any suggestions? And any ideas what other services should be running that I've not explicitly configured?

---

### Post by Neo@Matrix on 2011-03-04
Try to see in update log what has been changed , but most likely it ain't in question.
Updates not supposed to have affect on your server settings.
If you're in position (or already gave a shot) try another reboot , just to make sure 
that it is still the situation. 

In webmin you have the opportunity to manually set all the services you need to have running at startup, and an overview of services running.

---

### Post by Neil Smith on 2011-03-04
Thanks for the reply. I know updates aren't supposed to affect server settings, which is why I was surprised that it did.

I've rebooted the server a couple of times to check the effect was real: it is.

I don't use webmin. But I'm concerned about the services that should be running that I've not needed to fiddle with. 

Is there anything I should be looking for in the init system that may have become broken?


In case it helps, here's my last couple of updates. I can't remember when I last rebooted the server before today's update.

Aptitude 0.4.11.11: log report
Wed, Mar  2 2011 12:56:36 +0000

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 25 packages, and remove 0 packages.
99.5MB of disk space will be used
===============================================================================
[INSTALL] linux-image-2.6.32-29-generic-pae
[UPGRADE] clamav 0.96.5+dfsg-1ubuntu1.10.04.1 -> 0.96.5+dfsg-1ubuntu1.10.04.2
[UPGRADE] clamav-base 0.96.5+dfsg-1ubuntu1.10.04.1 -> 0.96.5+dfsg-1ubuntu1.10.04.2
[UPGRADE] clamav-daemon 0.96.5+dfsg-1ubuntu1.10.04.1 -> 0.96.5+dfsg-1ubuntu1.10.04.2
[UPGRADE] clamav-freshclam 0.96.5+dfsg-1ubuntu1.10.04.1 -> 0.96.5+dfsg-1ubuntu1.10.04.2
[UPGRADE] fuse-utils 2.8.1-1.1ubuntu3 -> 2.8.1-1.1ubuntu3.1
[UPGRADE] libclamav6 0.96.5+dfsg-1ubuntu1.10.04.1 -> 0.96.5+dfsg-1ubuntu1.10.04.2
[UPGRADE] libfuse2 2.8.1-1.1ubuntu3 -> 2.8.1-1.1ubuntu3.1
[UPGRADE] libmysqlclient16 5.1.41-3ubuntu12.9 -> 5.1.41-3ubuntu12.10
[UPGRADE] libwbclient0 2:3.4.7~dfsg-1ubuntu3.3 -> 2:3.4.7~dfsg-1ubuntu3.4
[UPGRADE] linux-generic-pae 2.6.32.28.32 -> 2.6.32.29.35
[UPGRADE] linux-image-generic-pae 2.6.32.28.32 -> 2.6.32.29.35
[UPGRADE] linux-image-server 2.6.32.28.32 -> 2.6.32.29.35
[UPGRADE] linux-libc-dev 2.6.32-28.55 -> 2.6.32-29.58
[UPGRADE] linux-server 2.6.32.28.32 -> 2.6.32.29.35
[UPGRADE] mysql-client-5.1 5.1.41-3ubuntu12.9 -> 5.1.41-3ubuntu12.10
[UPGRADE] mysql-client-core-5.1 5.1.41-3ubuntu12.9 -> 5.1.41-3ubuntu12.10
[UPGRADE] mysql-common 5.1.41-3ubuntu12.9 -> 5.1.41-3ubuntu12.10
[UPGRADE] mysql-server 5.1.41-3ubuntu12.9 -> 5.1.41-3ubuntu12.10
[UPGRADE] mysql-server-5.1 5.1.41-3ubuntu12.9 -> 5.1.41-3ubuntu12.10
[UPGRADE] mysql-server-core-5.1 5.1.41-3ubuntu12.9 -> 5.1.41-3ubuntu12.10
[UPGRADE] samba-common 2:3.4.7~dfsg-1ubuntu3.3 -> 2:3.4.7~dfsg-1ubuntu3.4
[UPGRADE] samba-common-bin 2:3.4.7~dfsg-1ubuntu3.3 -> 2:3.4.7~dfsg-1ubuntu3.4
[UPGRADE] smbclient 2:3.4.7~dfsg-1ubuntu3.3 -> 2:3.4.7~dfsg-1ubuntu3.4
[UPGRADE] xkb-data 1.8-1ubuntu8 -> 1.8-1ubuntu8.1~10.04.1
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Mar  4 2011 06:57:43 +0000

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 3 packages, and remove 0 packages.
===============================================================================
[UPGRADE] libpango1.0-0 1.28.0-0ubuntu2.1 -> 1.28.0-0ubuntu2.2
[UPGRADE] libpango1.0-common 1.28.0-0ubuntu2.1 -> 1.28.0-0ubuntu2.2
[UPGRADE] linux-firmware 1.34.3 -> 1.34.4
===============================================================================

Log complete.

---

### Post by GnuDragon on 2011-03-29
I experienced the similar issue today. 

I updated 10.04 LTS to 10.04.02 and **ssh**, **mysql** and **samba** did not come up on reboot. Starting them manually works.

my /var/log/apt/history.log

Start-Date: 2011-03-28  06:31:33
Upgrade: smbclient (3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg-1ubuntu3.5), libdbus-1-3 (
1.2.16-2ubuntu4.1, 1.2.16-2ubuntu4.2), smbfs (3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg-
1ubuntu3.5), openssh-client (5.3p1-3ubuntu5, 5.3p1-3ubuntu6), samba-common-bin (
3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg-1ubuntu3.5), samba-doc (3.4.7~dfsg-1ubuntu3.4,
 3.4.7~dfsg-1ubuntu3.5), samba (3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg-1ubuntu3.5), l
ibwbclient0 (3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg-1ubuntu3.5), tzdata (2011c-0ubunt
u0.10.04, 2011d-0ubuntu0.10.04), samba-common (3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg
-1ubuntu3.5), winbind (3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg-1ubuntu3.5), libpam-smb
pass (3.4.7~dfsg-1ubuntu3.4, 3.4.7~dfsg-1ubuntu3.5), openssh-server (5.3p1-3ubun
tu5, 5.3p1-3ubuntu6)
End-Date: 2011-03-28  06:32:13

---

### Post by GnuDragon on 2011-03-29
I fixed it for me.

If relevant:

I had a lady on site to examine the server.

She noticed that when it restarts it does not restart the hardware i.e. cold boot. It logs everyone out then drops to a root prompt in the boot loader, then relaunches the OS. So it wasn't fully rebooting.

I told her to try issuing the shutdown command from the root prompt, and the same thing happened. So I told her to ctrl-alt-del, and it hung on 'restarting system'. OK I know the power management/acpi logic is a bit old on this machine's ancient motherboard, so that didn't surprise me.

 I told her to cycle the power, and it works fine now after the cold boot.

edit: i don't even understand how this is even possible.

edit2: was it possible that wasn't the boot loader? i didn't see the screen myself.

---

### Post by Neil Smith on 2011-03-29
Sorry, I should have revisited this thread.

It turns out I had the same problem as GnuDragon. A reboot ('shutdown -r') was just switching the machine to runlevel 6 and doing nothing else. A power-cycling hard reboot fixed the problem.

---

### Post by GnuDragon on 2011-04-01
Ahh... run levels. I better read up on those. Thanks. I only know the one that puts it into single user mode.

---

