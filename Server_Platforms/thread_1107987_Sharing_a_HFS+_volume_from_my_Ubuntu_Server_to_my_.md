---
title: "Sharing a HFS+ volume from my Ubuntu Server to my MacBook Pro via NFS."
date: 2009-03-27
forum: Server Platforms
---

### Post by peppiotr on 2009-03-27
Hi guys!
This is my first post here at the Ubuntu Forums. I'm totally new to ubuntu and unix, as I have just set up my first ubuntu server here at home. So if you'll help me step by step on everything, I'll be very thankful :)

My server runs with the IP 192.168.2.200 which is outside the routers DHCP range. I have connected to the server via SaMBa from my MacBook Pro as I had a friend help me configure it. Now, SaMBa works okay I guess, but it is a bit slow. So I have decided to change protocols to the NFS. 

I have a WD My Passport Studio HFS+ drive mounted to the server with full read/write accsess from all users(I think).
Anyways, here's the /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c1ac2ef9-f236-4daf-bb4e-1def6abe7c1d /               ext3    relatime,erro$
# /dev/sda5
UUID=b42d1faf-4615-482b-9d14-55410a87b4e3 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb         /mnt/usbdisk    hfsplus           rw,noauto,users,exec,noatime,umask=000 0 0
```

This works pretty well, and I can write to the disc(/mnt/usbdisk) both from my server and through SaMBa.

When installing NFS I have used this guide:
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs)
in addition to some other forum posts. 

My portmap has not been binded as the guid says.
Now... The /etc/exports looks like this on my server now. (I have tried a variety of versions that doesn't work.)
```

/mnt/usbdisk 192.168.2.1/24(rw,sync,no_subtree_check,insecure)
```

However, afterwards when i run the following, the following happens:
```
mats@irontown:~$ sudo exportfs -a
exportfs: Warning: /mnt/usbdisk does not support NFS export.
```
 
How do I fix this?

In addition, I've heard talk abou my userID's having to be equal on my Mac and my server. On My Mac it looks like this:
```
uid=501(matsolsen) gid=20(staff) groups=20(staff),98(_lpadmin),81(_appserveradm),
79(_appserverusr),80(admin),101(com.apple.sharepoint.group.1)

```
and on my ubuntu server it's like this:
```
uid=1000(mats) gid=1000(mats) groups=4(adm),20(dialout),24(cdrom),46(plugdev),
112(lpadmin),113(sambashare),114(admin),1000(mats)

```

In the /etc/exports it's possible to add userids like anonid and anongid.. But I don't know if this should be done.. 

Can anyone please,please give me a hand.
I have been struggeling with this for days.

---

### Post by ktrnka on 2009-03-27
I was looking through google and it appears that the most simple solution is to avoid NFS with HFS+ and use Samba.

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by peppiotr on 2009-03-28
I have Samba working. But I want NFS because of the speed. Mounting the HFS+ was no trouble at all. It works fine. But as you see, I am having trouble exporting it through NFS. Any words on this?

---

### Post by ktrnka on 2009-04-12
Doing a little more research, I found that HFS+ needs to be compiled into the kernel to be exported via nfs-kernel-server. The other option is to export it via nfs-user-server. It is not as efficient as the nfs-kernel-server because it is in user space but at least you should be able to export your HFS+ partition without having to recompile your kernel.

Hope that helps.

---

