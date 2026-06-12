---
title: "No reboot after reboot command"
date: 2011-09-04
forum: Server Platforms
---

### Post by Johnny-Gear on 2011-09-04
Hi All,

Running Ubuntu Server 11.04; Main duties are running a Headless VirtualBox environment, Bacula Server(currently not running any jobs) and a couple of video cards which do some hashing(curently no running though).

Disk setup is all mdadm:
- RAID1 - /boot
- RAID10 - /
- RAID6 - /mnt/md1

This server is a new creation for the office here and hasn't been a priority, but I have noticed this issue a number of times when working on it.

I run a reboot command as root and I get the following:
>>
# reboot

Broadcast message from <user>@<host>
    (/dev/pts/1) at 8:52 ...

The system is going down for reboot NOW!
>>

The system does not reboot though. 

I have confirmed each time this has happened as well that the VirtualBox guest is not running as I thought this may have some affect.

I have also confirmed each time that there are no zombie processes.

Any help would be appreciated as I would like to confirm the stability and reliability of this system before it goes into production.

Thanks,

Johnny

---

