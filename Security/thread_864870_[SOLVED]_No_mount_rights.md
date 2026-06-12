---
title: "[SOLVED] No mount rights"
date: 2008-07-20
forum: Security
---

### Post by bogdanbiv on 2008-07-20
When I try to mount my USB stick or my NTFS partition I get this error:

A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")

It did work previously.

My system is Kubuntu 8.04, 32bits
$ uname -a
Linux bog-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux 

Screenshot:
[IMG]http://farm4.static.flickr.com/3113/2684901910_6ce78d8aa1_o.png[/IMG]

---

### Post by bogdanbiv on 2008-07-29
My user is a member of

```
bog@bog-desktop:~$ groups
bog adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin vboxusers mythtv
```

Root can mount/read/write the usb device
Users (bog too) can also read from the device.



Did I accidentally remove my user from the relevant group ?
How can I learn what does each group mean?

I learnt that admin group members can change the config of the system, what about other groups adm, lpadmin...?
Is there a tool such as whatis/whereis for system groups?

---

### Post by bogdanbiv on 2008-07-29
It seems that I have accidentally changed the mount rights and I did not notice this!
Here's how I did it:
checked that my disk (CORSAIR) is not in /etc/mtab:
```
$ cat /etc/mtab
/dev/sda2 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda3 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

then I removed the mount point - I thought there could be 'leftovers' remaining from a dirty removal of device:
OLD /media directory:
```
$ ls -lt /media
total 12
drwxr-xr-x 2 root root 4096 2008-07-22 07:09 CORSAIR
lrwxrwxrwx 1 root  999    6 2008-06-20 10:00 cdrom -> cdrom0
drwxr-xr-x 2 root  999 4096 2008-06-20 10:00 cdrom0
lrwxrwxrwx 1 root  999    7 2008-06-20 10:00 floppy -> floppy0
drwxr-xr-x 2 root  999 4096 2008-06-20 10:00 floppy0
```

New /media directory:
```
/media$ sudo rmdir CORSAIR/
[sudo] password for bog:
bog@bog-desktop:/media$ ls
cdrom  cdrom0  floppy  floppy0
```

I plugged in the usb flash disk and I get the friendly error message you can see in the previous posts.

Then I went to the Main menu, selected the System settings option (if you don't see the option in the main menu you can also type "systemsettings" in a console). Then I choose "Disk & File systems" on the Advanced tab (use the search tool to find it). Then I enabled administrator mode.

I select the partition on the device (/dev/sdb1) and I chose "Modify".
Which gets me here:
[[IMG]http://farm4.static.flickr.com/3238/2725543976_c8d8cd7ab5.jpg[/IMG]]("http://www.flickr.com/photos/53454265@N00/2725543976/sizes/o/")  click to see it on flickr.

---

