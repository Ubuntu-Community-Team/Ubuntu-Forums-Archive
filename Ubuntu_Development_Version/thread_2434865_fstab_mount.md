---
title: "fstab mount"
date: 2020-01-12
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-01-12
I think this update removed the ability to mount NFS folders from fstab
```
Start-Date: 2020-01-12  07:32:53
Commandline: aptdaemon role='role-commit-packages' sender=':1.729'
Upgrade: gir1.2-nm-1.0:amd64 (1.20.4-2ubuntu3, 1.20.8-1ubuntu2), python3-mako:amd64 (1.1.0+ds1-1, 1.1.0+ds1-1ubuntu1), python3-xkit:amd64 (0.5.0ubuntu2, 0.5.0ubuntu4), libnm0:amd64 (1.20.4-2ubuntu3, 1.20.8-1ubuntu2), network-manager:amd64 (1.20.4-2ubuntu3, 1.20.8-1ubuntu2), network-manager-config-connectivity-ubuntu:amd64 (1.20.4-2ubuntu3, 1.20.8-1ubuntu2), python-gobject-2:amd64 (2.28.6-12ubuntu4, 2.28.6-12ubuntu5)
End-Date: 2020-01-12  07:33:01

```

---

### Post by oldfred on 2020-01-12
Doubtful.

More likely your Windows did an update & turned fast start up back on. Then hibernation flag is set on all NTFS partition and Ubuntu NTFS driver will not mount normally read/write to prevent damage.
Make sure fast start up is off in Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by TheFu on 2020-01-12
NFS or NTFS?

---

### Post by P-I H on 2020-01-13
The servers are Ubuntu server 16.04.
Can't find any fast boot settings in this BIOS.
The NFS mount in Kodi works fine
No problem to activate with
**sudo mount TV-server**
fstab look like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=57faf406-c853-438e-bae8-cc3b1dce9626 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=021B-414D  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
ip.address.to.server1:/srv/Media /home/p-i/ServerMedia nfs tcp,rsize=8192,wsize=8192,timeo=14,intr 0 0
ip.address.to.server1:/srv/Anvandare/p-i/NASDokument /home/p-i/ServerDokument nfs tcp,rsize=8192,wsize=8192,timeo=14,intr 0 0
ip.address.to.server2:/srv/Media /home/p-i/TV-server nfs tcp,rsize=8192,wsize=8192,timeo=14,intr 0 0
```

---

### Post by SeijiSensei on 2020-01-13
What if you remove "tcp" from the options and let it use the default UDP connection?

I'm on 19.10 and fstab entries with "defaults,noauto,x-systemd.automount" work just fine.  ("x-systemd-automount" is the systemd successor to autofs.)

---

### Post by TheFu on 2020-01-13
In autofs, the tcp option is "**proto=tcp**" and all other options are the same as in fstab, at least on 16.04.  On a GigE network, tcp is recommended for NFS.  I use these options for server-to-server NFS:
```
proto=tcp,intr,rw,async,vers=3
```

BTW, specifying rsize=8192,wsize=8192 prevents the client and server from negotiating the best sized automatically which has been part of nfsv4 servers since the beginning.

---

### Post by P-I H on 2020-01-13
Thanks for the proposals.
This set up worked at least some days back.
I will connect my main PC and se if it works on 19.10.
I have had problems earlier with this config and used a autfs instead, but in that case you have to do more settings.

---

### Post by P-I H on 2020-01-13
Connected my main computer. I have installed both 19.10 and 20.04 on separate disks on this computer. NFS mounts worked fine both before and after updates.
Perhaps the problem is connected to the dual boot with W10 as suggested by oldfred.

---

### Post by SeijiSensei on 2020-01-13
> **TheFu said:**
> BTW, specifying rsize=8192,wsize=8192 prevents the client and server from negotiating the best sized automatically which has been part of nfsv4 servers since the beginning.
Indeed. On my systems rsize and wsize are auto-negotiated to run at 524288, even on wireless N.

---

### Post by TheFu on 2020-01-13
Raspberry Pi, USB-to-GigE adaptor and between Intel NICs all negotiated rsize=1048576,wsize=1048576 for multiple mounts on multiple different NFS servers according to *nfsstat -m*.

---

