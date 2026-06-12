---
title: "Error installing Ubuntu Server 13.04 on VMware"
date: 2013-09-25
forum: Virtualisation
---

### Post by Santiago_Alvarez on 2013-09-25
[SIZE=3]Hello. I'm trying to install the 64-bit version of Ubuntu Server 13.04 on a VMware virtual machine, and things seem to run ok, but after I finish disk partitioning and the installer starts to copy kernel images to disk, I get the following error message:
[/SIZE]
[FONT=lucida console][SIZE=2][SIZE=2]Unable to install the selected kernel
An error was returned while trying to install the kernel into the target system

Kernel package: 'linux-generic'

Check /var/log/syslog or see virtual console 4 for the details[/SIZE]
[/SIZE][/FONT]
[SIZE=3]I then check the log, and the last line says this:[/SIZE] [FONT=lucida console]"base-installer: error: exiting on error base-installer/kernel/failed-install"
[/FONT][FONT=lucida console][SIZE=2]
[/SIZE][/FONT]

---

### Post by CharlesA on 2013-09-26
If you are installing from an ISO, did you verify the md5sum/sha1sum of it before trying to do the install?

As far as running 13.04 as a server, is there a reason for running the latest and not a LTS version?

---

### Post by Santiago_Alvarez on 2013-09-29
Yeah, I did check the md5sum, and it was fine. I also tried installing the LTS version, and got the same error.
Another thing, in my partitioning scheme I had /boot, /, /home and /var, all in separate partitions. After I made this post, I tried installing the server, but now without a dedicated partition for /boot, and that way no error was thrown. Any clue on what's happening?

By the way, my interests on running Ubuntu server are purely academic, so both the latest version and LTS are OK with me.

Thanks!

---

### Post by CharlesA on 2013-09-30
Huh. I've not run into that before. Maybe it was a VMware thing?

---

### Post by Santiago_Alvarez on 2013-10-11
It seems like it's a VMware bug. I retried installation and somehow I ran into the same error again.
I did it on VirtualBox and it got installed perfectly. Thanks anyway!

---

