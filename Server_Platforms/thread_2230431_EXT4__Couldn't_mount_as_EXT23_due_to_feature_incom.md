---
title: "EXT4  Couldn't mount as EXT2/3 due to feature incompatibilities + KVM VCPU error"
date: 2014-06-19
forum: Server Platforms
---

### Post by Revenger on 2014-06-19
I installed ubuntu server on my Microserver N36l using normal partitioning setup webmin/virtualmin/cloudmin for server stuff.

I have been updating apps etc normally using apt-get or webmin and I'm noticing errors on the system despite not doing anything else or changing anything.

[ATTACH=CONFIG]254061[/ATTACH]

I have never ever touched anything with the mounting of the partitions since the install a couple weeks back.

I don't know if this is called by the virtio driver in KVM that I have been using on cloudmin with systems such as Fedora etc but at the time of those errors the vm's were shut down I believe.

The other is a VCPU error I have no idea about.

Did a update on apt-get break the hdd partition thats the only thing I can think of with the newer headers over the last few days.

Here is a output of a couple commands.

```
server@server:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b6b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   471621631   235809792   83  Linux
/dev/sda2       471623678   488396799     8386561    5  Extended
/dev/sda5       471623680   488396799     8386560   82  Linux swap / Solaris
server@server:~$ df -T
Filesystem     Type     1K-blocks     Used Available Use% Mounted on
/dev/sda1      ext4     231976960 44102244 176067844  21% /
none           tmpfs            4        0         4   0% /sys/fs/cgroup
udev           devtmpfs   4044628        4   4044624   1% /dev
tmpfs          tmpfs       817688      756    816932   1% /run
none           tmpfs         5120        0      5120   0% /run/lock
none           tmpfs      4088424        0   4088424   0% /run/shm
none           tmpfs       102400        0    102400   0% /run/user
server@server:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,relatime,hugetlb)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
server@server:~$

```

I presume this is due to KVM and the 'VrtualIO' driver with Fedora as I get these errors in cloudmin a KVM web virtualser 

```
Checking filesystem on first disk ..
.. not possible for the first disk

Mounting KVM instance filesystem ..
.. failed : None of the partions in the disk image /kvm/fedora-lxde.drguild.noip.me.img could be mounted and contained the /etc directory. This may be due to the use of RAID or LVM.
```

For now I am going to remove the VM's and see if that clears it.

Update removing the vm's I am getting no messages but I'll keep an eye on it.

---

### Post by Vegan on 2014-06-19
unfortunately i run across this once in while too

I use Hyper-V but the same issues surface with other Linux distros too

---

