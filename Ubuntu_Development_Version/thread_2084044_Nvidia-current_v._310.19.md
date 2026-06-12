---
title: "Nvidia-current v. 310.19"
date: 2012-11-14
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-11-14
There is a new nvidia-current beta version available from xorg-edgers PPA (RR branch).
The version is 310.19.

Working fine here.

---

### Post by dino99 on 2012-11-14
hm, still get the same known error:

```
update-initramfs: Generating /boot/initrd.img-3.7.0-030700rc5-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted (core dumped)
WARNING: could not open /tmp/mkinitramfs_iuhZhv/lib/modules/3.7.0-030700rc5-generic/modules.builtin: No such file or directory

```

---

### Post by zika on 2012-11-14
> **dino99 said:**
> hm, still get the same known error:

```
update-initramfs: Generating /boot/initrd.img-3.7.0-030700rc5-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted (core dumped)
WARNING: could not open /tmp/mkinitramfs_iuhZhv/lib/modules/3.7.0-030700rc5-generic/modules.builtin: No such file or directory

```It's just warning... No harm produced as far as I can tell...
Lot of bugs are filed against this and elsewhere...
[http://bit.ly/TGOiWG](http://bit.ly/TGOiWG)

---

### Post by dino99 on 2012-11-14
> **zika said:**
> It's just warning... No harm produced as far as I can tell...
Lot of bugs are filed against this and elsewhere...
[http://bit.ly/TGOiWG](http://bit.ly/TGOiWG)

I can run it but only on low graphic mode (800x600), so i switch back to nouveau again  :(

---

### Post by NikTh on 2012-11-14
An observation here , that might help others. 

I downloaded (2 days ago) 310.14 beta driver from Nvidia's site 
[http://www.nvidia.com/object/linux-display-amd64-310.14-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.14-driver.html)

To test it with my Nvidia GT430. What I observed is when I installed the .run file , during installation asked me to blacklist nouveau. Installation failed due to nouveau loaded module. 
I blacklisted nouveau and booted with vesa (low graphics) and then installation completed successfully and the driver working good since then.
Until this time I thought the only requirement was to stop the X , but seems a new requirement now is to have nouveau module unloaded. 
So , try to install with nouveau blacklisted. (manual by you). 

Thanks

---

### Post by zika on 2012-11-14
> **dino99 said:**
> I can run it but only on low graphic mode (800x600), so i switch back to nouveau again  :(Then I stand corrected. My (ATI/Asus) machine does not produce any harm due to this warning...

---

### Post by Harry33 on 2012-11-14
Well if one just upgrades from the previous nvidia-current version, then nouveau driver is blacklisted.
That is, installing nvidia-current will automatically blacklist nouveau driver.

---

### Post by dino99 on 2012-11-14
i cant beleive what have happened:
- due to previous comment, i've purged the "nouveau" driver (installed: vesa, fbdev, modesetting)
- then did a cold reboot
- was expecting a low graphic, but got a normal definition :P :confused:
- then i've checked the active video driver : "nouveau"
   :confused::confused: its really purged, but still active after a reboot :confused::confused::confused:

- well going ahead: activate edgers ppa and install nvidia 310.19
- got the kmod error
- then i've rebooted: surprisingly i got alot of art-deco before getting lightdm
- and everything seems ok: jockey show me nvidia activated that time  :P

---

### Post by toobuntu on 2012-11-15
Is your /tmp mounted [FONT="Courier New"]noexec[/FONT]? If so, the [FONT="Courier New"]update-initramfs[/FONT] issue might be related to Debian Bug #[576678]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576678"); at least it seems familiar. 

> /tmp: [exec] needs to be mounted [FONT="Courier New"]exec[/FONT] at package configuration time, or there could be problems with the maintainer scripts, e.g. see Bug#576678: [FONT="Courier New"]initramfs-tools[/FONT]: breaks but continues if /tmp is mounted with [FONT="Courier New"]noexec[/FONT] option (fixed on 08-Jun-2010 in v0.96.1).

Does ```
grep \ /tmp /etc/mtab
``` show [FONT="Courier New"]noexec[/FONT] as a mount option? If so, try remounting [FONT="Courier New"]exec[/FONT] before running [FONT="Courier New"]update-initramfs[/FONT] (or [FONT="Courier New"]apt-get[/FONT], which will call it when appropriate). You can do that with:
```
sudo mount /tmp -o remount,exec
```

---

### Post by dino99 on 2012-11-15
hm, get no output, and /tmp is not mounted at all

oem@oem-desktop:~$ grep \ /tmp /etc/mtab
oem@oem-desktop:~$ sudo grep \ /tmp /etc/mtab
[sudo] password for oem: 
oem@oem-desktop:~$ sudo mount /tmp -o remount,exec
mount: /tmp not mounted or bad option

---

### Post by toobuntu on 2012-11-15
Interesting. First of all, know that if it's the bug I mentioned above, then this is a non-fatal error so your program should work. Nevertheless, you may be curious to find out what's going on. Let's see what filesystems you have mounted and what the mount options are. Can you post the output of the following commands?
```
mount
```
and
```
cat /etc/fstab
```

Also, there is a space between the \ and /tmp, but it doesn't look like you entered it that way. Another way to run that command is ```
grep " /tmp" /etc/mtab
```

---

### Post by dino99 on 2012-11-15
well, its a default installation, and dont see why /tmp should be mounted on its own as the / partition is already mounted (single home desktop)

the related bug is confirmed by devs leaders:
 [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1075422](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1075422)

```
oem@oem-desktop:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
cgroup on /sys/fs/cgroup type tmpfs (rw,relatime,mode=755)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,relatime,hugetlb)
/dev/sda3 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/oem/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=oem)
```

```
oem@oem-desktop:~$ grep " /tmp" /etc/mtab
```

```
oem@oem-desktop:~$ cat /etc/fstab
proc                                       /proc  proc  nodev,noexec,nosuid 0 0 
# sda1  Dev32
UUID=9e61e83e-bca9-43cf-aa90-5a68892213fa  /      ext3  errors=remount-ro  0  1 
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523  /home  ext3  defaults,relatime  0  2  
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16  none   swap  sw                 0  0 
```

---

### Post by Harry33 on 2012-11-16
So this initramfs-tools bug will perhaps be fixed by the next update.

---

### Post by dino99 on 2012-11-16
What surprise me is that it seems that other nvidia users are not affected, as no one have reported dupes or write comments on that report. But as devs are aware, i hope to see a fix soon indeed.

---

### Post by zika on 2012-11-16
From [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576678:](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576678:)
> I regard it as bug with severity minor or wishlist.ROFL...

---

### Post by dino99 on 2012-11-16
merging request to get the latest fixes:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1079605](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1079605)

---

### Post by Harry33 on 2012-11-16
> **dino99 said:**
> What surprise me is that it seems that other nvidia users are not affected, as no one have reported dupes or write comments on that report. But as devs are aware, i hope to see a fix soon indeed.

Well I would not count on that one.
I see the same warning message each time, but it does not harm my setup in anyway:

```

WARNING: could not open /tmp/mkinitramfs_iuhZhv/lib/modules/3.7.0-*-generic/modules.builtin: No such file or directory

```

---

### Post by dino99 on 2012-11-16
> **Harry33 said:**
> 
I see the same warning message each time, but it does not harm my setup in anyway

you are lucky :P i only get low resolution if i use nvidia driver. :(

Have you installed additional edgers packages ? (like xorg or mesa)

---

### Post by Harry33 on 2012-11-17
> **dino99 said:**
> you are lucky :P i only get low resolution if i use nvidia driver. :(

Have you installed additional edgers packages ? (like xorg or mesa)

Nope, for xserver, mesa and drm I use RR packages.

---

### Post by HansKisaragi on 2012-11-17
failed to install , had to use 304..

running Elementary Luna (based on 12.04)

---

### Post by Harry33 on 2012-11-17
> **Viiral said:**
> failed to install , had to use 304..

running Elementary Luna (based on 12.04)

Why did it fail?
Error messages?

---

