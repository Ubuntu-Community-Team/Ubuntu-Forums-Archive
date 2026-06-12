---
title: "[SOLVED] VirtualBox: Compact VDI file in Ubuntu-Linux 8.04 guest"
date: 2008-09-02
forum: Virtualisation
---

### Post by abcuser on 2008-09-02
Hi,

Instructions for:
- Sun xVM Virtual Box 1.6.4
- Windows XP SP3 as VM_host
- Ubuntu 8.04 as VM_guest

According to following HOW-TOs I have adapted document instructions to work under Ubuntu 8.04:
[http://forums.virtualbox.org/viewtopic.php?p=29272#29272](http://forums.virtualbox.org/viewtopic.php?p=29272#29272)
[http://giornaledisistema.blogspot.com/2007/11/virtualbox-compattare-dischi-virtuali.html](http://giornaledisistema.blogspot.com/2007/11/virtualbox-compattare-dischi-virtuali.html)

1. Download file [http://intgat.tigress.co.uk/rmy/uml/zerofree-1.0.1.tgz](http://intgat.tigress.co.uk/rmy/uml/zerofree-1.0.1.tgz)
2. Untar file:
```
tar -xvzf zerofree-1.0.1.tgz
```
3. Change directory to zerofree dir:
```
cd zerofree-1.0.1
```
4. Install required gcc libraries and ext2fs library:
```
sudo apt-get install build-essential
sudo apt-get install e2fslibs-dev
```
5. Compile c-code:
```
make
```
6. Copy executible file to /root dir:
```
sudo cp zerofree /root
```
6. Start runlevel 1:
```
sudo telinit 1
```
7. Select "root" from Recovery menu.
8. Check to see disk names:
```
df
```
9. From previous command in left corner there are /dev/... devices in my case /dev/sda1. Mount this disk as read only:
```
mount -n -o remount,ro -t ext2 /dev/sda1 /
```
10. Check if everything is ok with file system
```
fsck -f /dev/sda1
```
11. Make zeros:
```
zerofree /dev/sda1
```
11. Check again if everything is ok with file system
```
fsck -f /dev/sda1
```
12. Shutdown linux:
```
halt
```
13. from Windows host execute:
"C:\Program Files\Sun\xVM VirtualBox\VBoxManage" modifyvdi vdi_file.vdi compact

Regards,
Abcuser

---

