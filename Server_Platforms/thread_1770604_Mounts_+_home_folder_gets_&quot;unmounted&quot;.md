---
title: "Mounts + home folder gets &quot;unmounted&quot;"
date: 2011-05-29
forum: Server Platforms
---

### Post by Elaro on 2011-05-29
Hello everyone!

I'm having a rather strange issue with my 11.04 32-bit server install.

The problem is the MDADM raid (/dev/md0) and my home folder (used the home folder encryption - could live without it) seems to be unavailable sometimes.

Normally my df -h looks like this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  1.6G   67G   3% /
none                  995M  216K  995M   1% /dev
none                 1002M  4.0K 1002M   1% /dev/shm
none                 1002M  1.1M 1001M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
/home/lars/.Private    72G  1.6G   67G   3% /home/lars
/dev/md0              4.1T  1.8T  2.1T  47% /home/lars/data

```

but after the a while it changes to this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  1.6G   67G   3% /
none                  995M  216K  995M   1% /dev
none                 1002M  4.0K 1002M   1% /dev/shm
none                 1002M  1.1M 1001M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
/home/lars/.Private    72G  1.6G   67G   3% /home/lars
/dev/md0               72G  1.6G   67G   3% /home/lars/data

```

And the data folder is just blank. If I remount md0 it works fine.

When i notice this problem my user cron jobs also start complaining about not find config files and scripts in my homefolder

I've been looking around in the logs and the only mentions of md0 I can find in at boot up.

The has been running fine from since natty came out to around a week ago and about 6 months before that on an early ubuntu.

Hoped you all might have a some ideas, very interested in how one would troubleshoot on a issue like this :)

---

