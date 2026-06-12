---
title: "Problems with Feisty commandline install on Compatc Flash"
date: 2007-09-14
forum: Server Platforms
---

### Post by Swiss2K on 2007-09-14
I'm running into strange problems with my commandline feisty install on a Compact Flash card.

The card is in a CF to IDE adapter. It's a clean Feisty commandline install. Additional installed software are SSH and ProFTPD. The only change I have made to to default install is add 'noatime' to hda1 in the fstab, to minimize writing to the CF card.

The problem is that after a few hours after boot, hda1 suddenly becomes read only, I can't start vim and other applications.

I.e.When running Crontab -e - I get ' Read-only file system
Creation of temporary crontab file failed - aborting'
Running vim an others i get - 'input/output error'

This is the output from mount:
/dev/hda1 on / type ext3 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)

What can be the problem??

---

