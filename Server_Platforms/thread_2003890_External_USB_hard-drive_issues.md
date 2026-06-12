---
title: "External USB hard-drive issues"
date: 2012-06-14
forum: Server Platforms
---

### Post by dustinmarc on 2012-06-14
Hi everyone, I recently took an old computer that wasn't being used and made it into a server using ubuntu server 12.  I got samba and mediatomb set up yesterday, and everything was working perfectly!  I was streaming movies to my ps3 from the server, and couldn't be happier.

Unfortunately, today when I tried to access some files on an external hard drive attached to the server, they were all gone.  The drive had unmounted itself.  Due to lack of storage space on the old comp, this external drive holds ALL my information, so you can imagine my disappointment.  Well, I tried to reboot and found that the boot was hanging due to an entry in fstab telling it to mount my external drive.  Then I skipped the mount and continued booting, and tried to manually mount.  Still no luck.  Next, I plugged the external drive into my main PC to see if it would work there - Nope!  After getting really scared of a hardware problem, I did some research and decided to power cycle it.  Success - It's still alive!  So I figured it was just a freak accident and plugged it back into the server after another power cycle, and rebooted to the same problem.  So I have it plugged back into my main comp. to make sure that it's not a hardware issue, and it works fine - which tells me it is something up with the server and how it is dealing with it.  

I know I should post the error messages I am getting at startup on the server with the external drive attached, but I am such a newbie that I am not sure of the best way to do this!  I only have one monitor with one input, so it would be the biggest pain in the world to keep plugging/unplugging monitors to copy the output manually.  So, what's the best way to do that, and what information do you all need?  

I fear I may have messed too many things up in getting the server going (I didn't know what I was doing, and just copied a ton of code from how-to websites), and that may have led to this issue.  Yet it was working fine last night, and I haven't changed anything that I can think of.  Sorry for the lengthly post, and uninformed nature of said post.  Any help would be GREATLY appreciated.

---

### Post by matt_symes on 2012-06-14
Hi

To get around the computer hanging when you bootup use the flag **nobootwait** in /etc/fstab.

Below is only an example.

```
UUID=<device_uuid> <mount_point> ext4 defaults,**nobootwait** 0 0
```

To post from your server i would use pastebin

```
sudo apt-get install pastebinit
```

Enter your password. It will not be echoed to the screen. You will need the universe repository enabled on you server.

```
cat <log_file_name> | pastebinit
```

This will supply a url you can post in your next post.

If the log file is large consider using the tail command.

```
tail -n 100 <log_file_name> | pastebinit
```

The log file i would look in to start with would be ```
/var/log/syslog
```

Kind regards

---

### Post by dustinmarc on 2012-06-14
Thanks so much for the quick reply!  I wasn't sure about the order you wanted me to do things, so I unplugged the external from my main computer (fully working), plugged it into my server, and then rebooted.  I am not sure if all the information you will need is in the file, but here it is:

[http://paste.ubuntu.com/1041718](http://paste.ubuntu.com/1041718)

edit: I didn't realize all the info that would be in there.  Looks like the problems start around 4437.

---

### Post by dustinmarc on 2012-06-14
Anyone know if that is the right information?  Anything else needed?

---

### Post by dustinmarc on 2012-06-15
I'm still stuck.  Anyone?

---

### Post by matt_symes on 2012-06-17
Hi

This is not good.

```
Jun 14 18:10:20 server kernel: [90531.712023] usb 1-1: reset high-speed USB device number 2 using ehci_hcd
Jun 14 18:10:20 server kernel: [90531.836018] usb 1-1: device descriptor read/64, error -71
Jun 14 18:10:21 server kernel: [90532.064016] usb 1-1: device descriptor read/64, error -71
Jun 14 18:10:21 server kernel: [90532.280017] usb 1-1: reset high-speed USB device number 2 using ehci_hcd
Jun 14 18:10:21 server kernel: [90532.404019] usb 1-1: device descriptor read/64, error -71
Jun 14 18:10:21 server kernel: [90532.632016] usb 1-1: device descriptor read/64, error -71
Jun 14 18:10:21 server kernel: [90532.848016] usb 1-1: reset high-speed USB device number 2 using ehci_hcd
Jun 14 18:10:22 server kernel: [90533.264011] usb 1-1: device not accepting address 2, error -71
Jun 14 18:10:22 server kernel: [90533.376019] usb 1-1: reset high-speed USB device number 2 using ehci_hcd
Jun 14 18:10:22 server kernel: [90533.792013] usb 1-1: device not accepting address 2, error -71
Jun 14 18:10:22 server kernel: [90533.792060] usb 1-1: USB disconnect, device number 2
Jun 14 18:10:22 server ntfs-3g[638]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jun 14 18:10:22 server ntfs-3g[638]: Failed to read of MFT, mft=7672 count=1 br=-1: Input/output error
Jun 14 18:10:22 server ntfs-3g[638]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jun 14 18:10:22 server kernel: [90533.804094] sd 2:0:0:0: [sdb] Unhandled error code
Jun 14 18:10:22 server kernel: [90533.804100] sd 2:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun 14 18:10:22 server kernel: [90533.804105] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 12 19 81 37 00 00 08 00
Jun 14 18:10:22 server kernel: [90533.804118] end_request: I/O error, dev sdb, sector 303661367
Jun 14 18:10:22 server kernel: [90533.804413] Buffer I/O error on device sdb1, logical block 37957663
Jun 14 18:10:22 server ntfs-3g[638]: Failed to read of MFT, mft=7672 count=1 br=-1: Input/output error
Jun 14 18:10:22 server ntfs-3g[638]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jun 14 18:10:22 server ntfs-3g[638]: Failed to read of MFT, mft=2609 count=1 br=-1: Input/output error
Jun 14 18:10:22 server ntfs-3g[638]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jun 14 18:10:22 server ntfs-3g[638]: Failed to read of MFT, mft=93 count=1 br=-1: Input/output error
Jun 14 18:10:22 server ntfs-3g[638]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
```

Have you tried a different USB port ? 

Is the external drive powered from the USB power bus or does it have its own power supply ?

Are you using an external USB hub ?

EDIT: Error -71 is a protocol error.

> #define EPROTO          71      /* Protocol error */

Kind regards

---

### Post by dustinmarc on 2012-06-18
matt,

I just gave in and reinstalled the whole OS.  As I was doing that, I realized it was plugged in to the main USB grouping on the mother board, and not the USB2.0 card installed lower down.  I had forgotten this old comp had regular USB ports, lol.  I never did just try plugging in to the USB2.0 card before reinstalling, I do not have an external USB hub, and it is powered through its' own power supply.  

Either way, after reinstalling and moving to the USB2 card, everything works (and faster too!)  Thank you so much for your help.  Sorry this thread is basically useless, as my fix was to just start back over.

---

