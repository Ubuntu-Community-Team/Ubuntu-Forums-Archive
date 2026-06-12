---
title: "automounting usb device in virtualbox environment"
date: 2011-03-09
forum: Server Platforms
---

### Post by fro1269 on 2011-03-09
Hello

I am running Ubuntu Server 10.04.2 LTS Inside a Virtualbox 3.2.12 environment running on a Windows Server 2003 x64 R2 SP2 host environment.

I am trying to figure out how I can have it so my usb devices automatically mount into a specified directory after I "Save the state" and then "Resume the state"

I currently have my fstab setup to look like this

```

UUID=BCE8F628E8F5E096  /media/thumb1    ntfs  defaults,nobootwait 0 0


```

So with that being said the USB device is successfully mounted in the /media/thumb1 directory on startup; however, when I resume from a saved state the device changes from /dev/sdb1 to /dev/sdc1, thus making the usb device unavailable to the OS unless I unmount and remount manually. I have been reading into this and I think that I need to add something to the /etc/udev/rules.d directory but I am not sure what I need to put in there to get this to work. Any help is appreciated

---

### Post by fro1269 on 2011-03-10
OK so I think I have made some progress but I'm not there yet.

I did a 
```
udevadm info -a -p $(udevadm info -q path -n /dev/sdb)
```

And I was able to get a serialnumber of 0876500C8092243B from the device, so I wrote a rule called

/etc/udev/rules.d/10-usbname.rules

The contents are
```
KERNEL=="sd*", SUBSYSTEMS=="scsi", ATTRS{serial}=="0876500C8092243B", SYMLINK+="thumba%n"
```

I have restarted the udev service, unattached the usb device and re-attached, but it still comes up as /dev/sdb as opposed to /dev/thumba. I have also restarted the VM to no avail

---

### Post by fro1269 on 2011-03-10
OK so I got it to work by correcting my syntax to 

```
BUS=="usb", ATTRS{serial}=="0876500C8092243B", KERNEL=="sd?1", SYMLINK+="thumba%n", GROUP="storage"

```
 ; however, what I think I need to do is force the kernel to name it /dev/sdX instead of a symlink, and then make it stay with /dev/sdX after i save/restore the VM

---

### Post by fro1269 on 2011-03-10
So I got this resolved. It turns out it was never an issue with device naming, but an issue with the drive not being accessible after the restore , I would get an I/O error. A workaround I found is to run a 
```
mount -a
```

After I restore from a saved state, at that point the drive is now accessible. WHen I run the mount -a comment, or for that matter mount any drive that is connected via usb filter to the guest I get the error

"The disk contains an unclean filesystem (0,1).
The filesystem wasnt safely closed on Windows. Fixing"

After I let that run everything works fine. Is there a way I can resolve that issue?

---

