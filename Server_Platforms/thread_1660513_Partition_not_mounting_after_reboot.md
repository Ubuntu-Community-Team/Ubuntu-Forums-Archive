---
title: "Partition not mounting after reboot"
date: 2011-01-05
forum: Server Platforms
---

### Post by nunojpg on 2011-01-05
The partition /dev/cciss/c0d0p4 refuses to mount after a reboot.

How can I check what is happening?

Regards,
Nuno

root@segal:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p2     9.2G  7.4G  1.4G  85% /
udev                  4.0G  196K  4.0G   1% /dev
none                  4.0G  164K  4.0G   1% /dev/shm
none                  4.0G  104K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
root@segal:/# mount
/dev/cciss/c0d0p2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev
)
root@segal:/# mount -a
mount: /dev/cciss/c0d0p4 already mounted or /ui busy
root@segal:/#

---

### Post by nunojpg on 2011-01-19
The partition was undergoing a disk check that lasted more than 2 hours. That was why it didn't look mounted neither it allowed to be mounted(again).
When the disk check ended, the partition appeared mounted as expected.

---

