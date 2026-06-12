---
title: "Problems writing to the host file system from a (kvm) guest instance"
date: 2012-09-06
forum: Virtualisation
---

### Post by jgaa on 2012-09-06
I recently installed Ubuntu Precise Server on my home server. This machine is sliced up in a number of VM's for different tasks. In the past I have used Debian with Vserver, VmWare and VirtualBox. My plan was to use Zen this time, but after some reading, I realized that kvm was the currently recommended technology for Ubuntu.

So I created a few virtual machines, and after a late evenings work, I had the most important functions up and running. The one thing that I failed to figure out was how to access the local host file system from the guest. Today I picked up that thread.

From "virt-manager" I created a "filesystem", pointing to a directory on the host machine with permissions 0777. At first, mount on the guest refused to deal with the "9p" file system type at all. After some goggling, I resolved that by installing the package "linux-image-extra-virtual" on the guest. It still refused to load the 9p kernel module, but after an "apt-get update && apt-get upgrade" and a reboot, the module loaded, and I could mount the share. However, I could not write to it. In the hosts syslog, I found some "apparmor="DENIED" operation="open"" messages. I have not dealt with apparmor before, so in stead of spending the next few hours getting familiar with the thing, I disabled it and rebooted the host. I also run into a few minor bugs on the guest. If I added the 9p mount point to “/etc/fstab”, the boot would halt, awaiting manual input after the mount failed. If I mounted it manually from the command-line, it was mounted, but the "df" command would not list it. So, as I usually use "df" to see what file sytems that are available, it was kind of hidden. (I think df should enumerate what's actually mounted). These annoyances went away when I added "9p" and "9pnet_virtio" to "/etc/modules" on the guest.

Now, after four hours, the 9p thing is still not working as expected. Reading and listing files works fine. But if I try to write to an existing file on the host file system, I get "Permission denied". If I try to create a new file, I get "Operation not supported". And unlike earlier today, I can't find anything in any logs about why. So I'm kind of lost. I don't even know if the problem is on the guest or host side. I could solve this by using nfs in stead – but I don't like nfs. Also, I don't think nfs is appropriate in a scenario like this, where I don't want another guest to be able to hijack the share.

On the guest:
~# mount
/dev/sda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
backup on /mnt/backup type 9p (rw,trans=virtio,version=9p2000.L)

~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.6G 1013M  6.2G  14% /
udev            241M  4.0K  241M   1% /dev
tmpfs           100M  200K   99M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            248M     0  248M   0% /run/shm
backup          1.8T  1.4T  343G  81% /mnt/backup

So I would appreciate if someone could shed some light on this, or suggest were to continue to search for the actual problem.

Jgaa

---

