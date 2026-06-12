---
title: "noatime has no effect"
date: 2011-10-04
forum: Server Platforms
---

### Post by ugh_bough on 2011-10-04
Hi,

I am setting up a 10.04-64bit-server that has three SATA backup disks. I want to save power when idling so I **spin down the drives** using an /etc/init.d script and hdparm like this:

# backupMaster 20 min
hdparm -S240 /dev/disk/by-id/ata-SAMSUNG_HD204UI_S2H7J1CB900152
# backupSlave1 5 min
hdparm -S60 /dev/disk/by-id/ata-SAMSUNG_HD204UI_S2H7J1CB900150
# backupSlave2 5 min
hdparm -S60 /dev/disk/by-id/ata-SAMSUNG_HD204UI_S2H7J1CB900151

I want a sync to **only spin up** those drives that have **files written** to it. The problem: Linux writes access times for files to disk. This is also the case for reads from the cache during the time a disk is spun down. As a result a sync spins the disks up to write these changes. So I configured the drives in the /etc/fstab like so using the noatime option that should prevent the recording of access times:

UUID=f0b94725-2d6f-4055-907a-85b8340974e5 /home/backuper/master ext2 defaults**,noatime** 0 0
UUID=6462d347-1174-496a-9a6a-718698eadf8c /home/backuper/slave1 ext2 defaults**,noatime** 0 0
UUID=a45010cf-5b9c-43e3-8d97-7c06f174d516 /home/backuper/slave2 ext2 defaults**,noatime** 0 0

But when I wait until slave1 and slave2 are spun down and e.g.

% touch slave1/test # no spin up yet since write cache is used
% sync # now spin up

then **both** slaves are spinning up again although I haven't even read from slave2.

Can you guys/gals teach me what I'm missing to get the desired behavior, i.e. slave2 stays spun down? Do you know ways to inspect the problem to find out the reasons for current (mis-)behavior?

Thx,
ugh_bough

---

### Post by ugh_bough on 2011-10-05
bump: I edited the post to make the question clearer.

---

### Post by CharlesA on 2011-10-05
Thread moved to Server Platforms per OP request.

---

### Post by ThePol1 on 2011-10-05
I had a similar problem. My post may help you:
[http://ubuntuforums.org/showthread.php?t=1725263](http://ubuntuforums.org/showthread.php?t=1725263)

---

### Post by ugh_bough on 2011-10-06
somewhere i read about some daemon that cares about atime updates of filesystems. it was called **nosyncd **or something. does any one of you know that exact name (nosyncd is wrong).

---

