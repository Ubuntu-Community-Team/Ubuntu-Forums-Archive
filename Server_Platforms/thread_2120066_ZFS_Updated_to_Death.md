---
title: "ZFS Updated to Death"
date: 2013-02-25
forum: Server Platforms
---

### Post by person6billion on 2013-02-25
I am running ZFS on Linux version 0.6.0.97 which supports version 23 zpools. Recently after an update whenever I would run "zpool status" it would show my pool working fine with a comment that said I should use zpool upgrade to be able to use tags.

I ran the upgrade command and after it finished my first que that something was wrong was that samba wasn't working. About 3 hours of investigating later showed ZFS was the issue. zpool status commands found that the zpool was unavailable due to the pool being an unsupported version.

I have a few ideas as to what to do next, but I am not sure if they will work or how to do them. 

My first thought was to use the unstable version, but I don't know the commands to issues to achieve this.

My second thought was to destroy the pool and copy it all back from a backup, which being over 1TB takes a while to do. Only issue is that I exported the pool and it won't allow me to destroy it without mounting it and I cant mount it unless it becomes a supported version.

Any other thoughts welcome.

---

### Post by achianese on 2013-03-02
Just an amateur here, so don't take me too seriously. Are you using the ZFS on Linux ppa for a recent version of Ubuntu?  The current version is 0.6.0-rc14, which supports zpools through version 31, including feature flags (past version 31 they stopped using version numbers apparently).

---

### Post by person6billion on 2013-03-03
After a bit of searching turns out that 0.6.0.97 and 0.6.0 rc14 are both the same version. I am running Ubuntu 12.10. Both zfs and spl are showing that version so it should be able to mount the pool, but it pops up with the error "cannot import 'name of pool' pool is formatted using a newer zfs version" I used the zpool upgrade command on this system to update the pool.

---

### Post by person6billion on 2013-03-08
update:
I installed an update to zfs. No change other volumes still mount this one doesn't.

---

### Post by person6billion on 2013-03-08
Just put in a gigabit switch. Will be testing just how fast my disks are by using gparted to remove zfs from the disks and recovering from a backup disk.

---

### Post by Cheesemill on 2013-03-08
A ZFS array should easily saturate a gigabit link at around 100MB/s.

Your backup drive might well do too if it's a modern disk doing sequential reads.

---

### Post by thnewguy on 2013-03-08
Are there snapshots of the existing ZFS pool? My thought would be to try to mount (or clone) one of the old snapshots? Not sure if the snapshots are all updated with the active ZFS fiel system, but perhaps the newer version can be clones back to an older version?

---

### Post by person6billion on 2013-03-09
Cheesemill:
The disks I was coping from managed about 400Mbps and only did that for a bit over an hour, not sure if it was the source or destination disks that are the holdup though. (source disks 2* 1TB WD green)(destination disks 2* 3TB WD red) 
Update: tested the read speed after coping everything over. I couldn't get an accurate result because they copied faster than my SSD could write (~550Mbps) Anyone know of an application to test read that would work in this case?

Thnewguy:
The only backups I have for the array are from a windows soft-raid, wish I did still have a snapshot though, would have been neat to try.

---

