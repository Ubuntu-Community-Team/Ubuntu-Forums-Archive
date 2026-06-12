---
title: "Can't access root (/)"
date: 2008-11-24
forum: Server Platforms
---

### Post by any.linux12 on 2008-11-24
Hey everybody!

I've ubuntu 8.10 and on the root (/) I have 2 folder mounted when the system loads. One is mounted by fstab (it's the server of the network) and the other is a ftp-server mounted by a script.

The problem is that if I unplug the network cable I can't access the (/) folder...what should I do???

Help please

---

### Post by Sef on 2008-11-24
moved to server platforms.

---

### Post by Walter_Crankite on 2008-11-24
You are doing something wrong. When the server and the TFTP are local resources, it is independent of the network configuration. 

When you mount something on the local machine that is a network resource, it will not work when you unplug the cable.

Mounting is not the same as copying all data to local HDD. 
It is more like a gate to the resource. 

Walter

---

### Post by any.linux12 on 2008-11-24
Ok that's all true

But how do you explain that I just lose access to my / dir when I unplug the cable??
Should be something about permissions??

---

### Post by bogdan.veringioiu on 2008-11-24
Hi.

The problem is that you loose connectivity and the listing of the / filesystem hangs while trying to list the broken folders (the one with the mounts).

To be able to browse your / filesystem after you unplug the network, try:

edit /etc/mtab (as root)

comment your network mount entries, and save.

You should be able to browse you / filesystem, after this.

You can try to umount (lazy umount) the filesystems with:

umount -l /network_mounted_folder (as root)

Let me know if it works for you.

Bogdan

---

### Post by any.linux12 on 2008-11-24
Sorry! But didn't work with me.

More ideas please

---

### Post by bogdan.veringioiu on 2008-11-24
How do you access the filesystem?

Nautilus, or terminal?

are you able to issue ls -l / (after you umount the folders)?

Bogdan

---

### Post by abhilashm86 on 2008-11-24
actually root is all related with permission,use 
sudo su
then try accessing root

---

### Post by any.linux12 on 2008-11-24
The server is mounted by the FSTAB and the FTP server is by script that is load on startup by sessions.

And no I can ls the / dir

---

### Post by any.linux12 on 2008-11-24
abhilashm86 you are also wrong. Even with root user I can't access /.
I think that  bogdan.veringioiu is more close to the answer

---

### Post by bogdan.veringioiu on 2008-11-24
Hm.

The solution that I gave was working...but on redhat server 4, and nfs mounts...

Could you post your /etc/mtab, /etc/fstab entries?

Thanks.

---

### Post by any.linux12 on 2008-11-24
proc            /proc           proc    defaults        0       0
UUID=69f12ad1-fa75-4175-ab15-62260db043c1 /               ext3    relatime,errors=remount-ro 0       1
UUID=fee295a1-03a0-47de-a1de-02e5b92d8cbe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
itserver:/server /server nfs defaults 0 0
usbfs /proc/bus/usb usbfs auto 0 0


the itserver line is the line that mounts the server

sorry about late response

---

### Post by bogdan.veringioiu on 2008-11-24
Ok.

What about /etc/mtab?

Could you post the contents?

Bogdan

---

### Post by any.linux12 on 2008-11-24
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
itserver:/server /server nfs rw,addr=192.168.1.3 0 0
gvfs-fuse-daemon /home/itadmin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=itadmin 0 0
curlftpfs#[ftp://192.168.1.42/](ftp://192.168.1.42/) /esp-ftp fuse rw,nosuid,nodev,user=itadmin 0 0

---

### Post by bogdan.veringioiu on 2008-11-24
Ok.

Now, try this after you unplug the cable:

-open gnome terminal, and type (before you list the / filesystem and lock the terminal):

sudo umount -l /server
sudo umount -l /esp-ftp

then ls -l /

Bogdan

---

### Post by any.linux12 on 2008-11-24
And how should I mount after that?

---

### Post by any.linux12 on 2008-11-24
Sorry but doesn't work couse when I tipe that the terminal crashes

---

### Post by bogdan.veringioiu on 2008-11-24
You have to mount manually after you plug the cable.

sudo mount -t nfs host:/server /server

The same for ftp.

But I suggest the following thing:
Try not to mount the network share directly on / filesystem.

Create a folder in root filesystem:

sudo mkdir /network_share

and create inside your mount folders (server and esp-ftp), and modify fstab and the script for mounting to the new folders.

I think in this way you will be able to see / filesystem.
The filesystem probably will lock when you will access /network_share with cable unplugged.

Bogdan

---

### Post by any.linux12 on 2008-11-25
Thank you very much!
Was a good idea

---

