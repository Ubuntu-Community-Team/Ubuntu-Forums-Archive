---
title: "PXE boot Ubuntu Server install image"
date: 2008-09-11
forum: Server Platforms
---

### Post by Cocoabean on 2008-09-11
Well, I stayed up late into the night getting PXE to boot several live CDs from my 2nd Ubuntu server. The first one easily boots Kubuntu and Ubuntu live CDs useing pxelinux, atftp, and NFS. However, I cannot get the server install CD to boot so I can install server of the LOCAL network. I know how to use the netboot image to install from a remote server, but I would like to boot it just as if I had the CD in the drive. The kernel loads, and I get into the Ubuntu Server keyboard setup, but then when it goes to find the CDROM, it of course cannot find it because the root is an NFS share. Here is my config for pxelinux specifically for the ubuntu server option, does anyone have idea on how i can get it to look for the NFS share instead of the CD. Thanks!
```
LABEL hardy-server
        MENU LABEL Ubuntu Server Hardy Heron
        kernel hardyserver/vmlinuz
        append root=/dev/nfs  boot=install netboot=nfs nfsroot=192.168.0.105:/netboot/ubuntuserver804/mnt initrd=hardyserver/initrd.gz --
                    
```

---

### Post by Sef on 2008-09-12
Moved to server platform.

---

### Post by promodus on 2008-09-12
[http://ubuntuforums.org/showthread.php?t=829482](http://ubuntuforums.org/showthread.php?t=829482)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Cocoabean on 2008-09-12
Thanks,

Looks like step 5 of [http://ubuntuforums.org/showthread.php?t=829482]("http://ubuntuforums.org/showthread.php?t=829482") is the magic bullet. I'll try it when I get home from work and post findings for anyone else who may be having this problem

---

