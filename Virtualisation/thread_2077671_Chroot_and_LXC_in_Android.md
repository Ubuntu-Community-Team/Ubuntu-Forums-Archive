---
title: "Chroot and LXC in Android"
date: 2012-10-29
forum: Virtualisation
---

### Post by narcisgarcia on 2012-10-29
I'm trying to run Ubuntu inside an LXC container, and this inside a Chroot container with Ubuntu to have LXC userspace tools:
1. Copy an Ubuntu's debootstrap to an Android system (tried with Linux 3.0.15)
2. Chroot into it.
3. Run an LXC container inside.

I don't know if the lack of a LXC port to bionic component is the cause of my problem.
My procedure:

Create a debootstrap directory in a system running Ubuntu (v12.04 seems to host right LXC containers, not v12.10)
```
sudo debootstrap --verbose --arch=armhf --foreign precise precise-armhf
```

Copy the directory "precise-armhf" to an Ext partition in the Android/ARM device (rooted). Open a root session in the device:
```
su
```

(Supposing that the new path is /data/precise-armhf)
Check if there are ro/nodev/noexec/nosuid restrictions:
```
mount
```
> /dev/block/mmcblk0p12 /data ext4 ro,nosuid,nodev,noatime,barrier=1,journal_async_commit,data=ordered,noauto_da_alloc,discard 0 0

If necessary, remount the target with same options but removing rw/nodev/noexec/nosuid:
```
mount -o remount,rw,noatime,barrier=1,journal_async_commit,data=ordered,noauto_da_alloc,discard /data
```

Let's mount the common resources for a chroot:
```

RootPoint="/data/precise-armhf"
mount -o bind "/dev" "$RootPoint/dev"
mount -o bind "/dev/pts" "$RootPoint/dev/pts"
mount -o bind "/sys" "$RootPoint/sys"
mount -o bind "/proc" "$RootPoint/proc"
```

Find the cgroup independent resources in the Android host:
```
mount | sed -e "/ cgroup /!d"
```
> none /acct cgroup rw,relatime,cpuacct 0 0
none /dev/cpuctl cgroup rw,relatime,cpu 0 0

Make them available to chroot environment:
```
mkdir -p "$RootPoint/acct"
mount -o bind /acct "$RootPoint/acct"
mount -o bind /dev/cpuctl "$RootPoint/dev/cpuctl"
```

Enter to the first container, mount anything specific, and one more directory to sure programs see something mounted:
```
chroot "$RootPoint" /bin/su
mount -a
if [ "$(mount)" = "" ] ; then mount -o bind /selinux /selinux ; fi
```

Complete debootstrap in the target architecture:
```
/debootstrap/debootstrap --second-stage
```

Patch to avoid Upstart errors:
```
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
```

Configure network:
```
echo "nameserver 4.2.2.2" > /etc/resolv.conf
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
echo "nameserver 8.8.4.4" >> /etc/resolv.conf
echo "127.0.0.1 localhost" > /etc/hosts
```

Look for repositories already set, and/or set them:
```
cat /etc/apt/sources.list
echo "deb http://ports.ubuntu.com/ precise main universe" >> /etc/apt/sources.list
echo "# deb-src http://ports.ubuntu.com/ precise main universe" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "deb http://ports.ubuntu.com/ precise-updates main universe" >> /etc/apt/sources.list
echo "# deb-src http://ports.ubuntu.com/ precise-updates main universe" >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list
echo "deb http://ports.ubuntu.com/ precise-security main universe" >> /etc/apt/sources.list
echo "# deb-src http://ports.ubuntu.com/ precise-security main universe" >> /etc/apt/sources.list
```

Update repositories, install LXC and create a new container:```

apt-get update
apt-get install lxctl
lxc-create -t ubuntu --name quantal -- --release quantal
```
(some error messages):
> Can not write log, openpty() failed (/dev/pts not mounted?)
invoke-rc.d: policy-rc.d denied execution of start.

The fact is that LXC container doesn't start:
```
lxc-start --name quantal
```
> lxc-start: failed to create veth4lBZQS-vethe2nGyB : Operation not supported
lxc-start: failed to create netdev
lxc-start: failed to create the network
lxc-start: failed to spawn 'quantal'
lxc-start: No such file or directory - failed to remove cgroup '/acct//lxc/quantal'

(also tested with precise)

---

### Post by narcisgarcia on 2012-10-29
(remove me)

---

