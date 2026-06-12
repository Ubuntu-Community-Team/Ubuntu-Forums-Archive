---
title: "usb drive performance in kvm"
date: 2010-01-02
forum: Virtualisation
---

### Post by paweljasinski on 2010-01-02
hi,

host: karmic
guest: Linux sysrescuecd 2.6.29.06-sd123 #1 SMP ...

I have connected external usb drive and the performance in guest is way below expectations. hdparm -t reports 2MB in 5 sec.
The same drive connected to host is reports: 90 MB in 3.05 seconds = 29.49 MB/sec

I start the kvm with:
sudo kvm -enable-kvm -boot d -vga vmware -hda disk0 -cdrom ~/download/iso/systemrescuecd-x86-1.2.3.iso -usb -usbdevice host:1058:0704


Do I have to do anything extra on the host? Until now I simply unmounted whatever got mounted in /media before starting the kvm

--pawel

---

### Post by hob on 2010-01-10
I have the exact same problem. I'm running 9.10 64-bit server on a Dell tower, Core2 Duo E8400 at 3 GHz, 4 Gigs RAM.

External drive is a Western Digital My Book 1110, a single 500gig drive. This drive has the "feature" of the built-in fake CD drive with a bunch of Western Digital drivers/manuals/etc.

```

user@server:~$ sudo hdparm -t /dev/sdb1

/dev/sdb1:
 Timing buffered disk reads:    2 MB in  4.94 seconds = 414.92 kB/sec
```

As far as I can tell, the external drive is connected to the Guest VM at USB 2.0 speeds, but the measured speed is USB 1.1. Definitely not what I'm looking for.

Maybe this has something to do with apparmor?

---

### Post by hob on 2010-01-10
Digging a little bit deeper, it does seem that the external USB drive is connected to a USB 1.1 hub only within the Guest.

For the Guest, it is on a USB 1.1 bus:
```
user@server:~$ lsusb
Bus 001 Device 002: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

But looking at the Host, the external harddrive is connected to a USB 2.0 bus. All the ports on this machine are USB 2.0, but there isn't anything else plugged into those other ports, so they default to 1.1:
```
user@server:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I already tried plugging the harddrive into another physical USB port on the computer, to no effect.

Does the USB 2.0 hub need to be added to the guest's XML file as an item in the hostdev section?

I also installed the "hald" program as described in [http://ubuntuforums.org/showthread.php?t=1300952](http://ubuntuforums.org/showthread.php?t=1300952). Since it has been running for several months without hald, I guess it's not that important.

---

### Post by hob on 2010-01-10
Well, adding the USB 2.0 hub does not seem to fix the problem.

```
user@server:~$ lsusb
Bus 001 Device 004: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 0000:0000  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
user@server:~$ sudo hdparm -t /dev/sdb1

/dev/sdb1:
 Timing buffered disk reads:    2 MB in  4.29 seconds = 476.84 kB/sec
```

I just added 1d6b:0002 to the QEMU xml definitions file, then had to Undefine the VM and Define it again.

---

