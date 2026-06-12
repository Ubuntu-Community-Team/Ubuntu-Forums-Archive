---
title: "disk encryption without passphrase"
date: 2010-07-07
forum: Server Platforms
---

### Post by BarryDocks on 2010-07-07
I would like to encrypt one of the RAID arrays on my server.  The filesystem and swap do not need encryption just the data on a mounted RAID array.  Is it possible to achieve this without having to use a passphrase that has to be input at boot?

I am using 10.04 LTS server edition

Thanks

---

### Post by stlsaint on 2010-07-07
Im not sure if your able to encrypt only certain portions of a lvm without encrypted all of it. You may want to consider seperating whatever data you want encrypted onto another partition and just encrypting that.

---

### Post by HermanAB on 2010-07-08
Howdy,

You could use LUKS and put the key on a USB memory stick.  Then of course, the stick should be plugged in at boot time, but it may suffice for your situation.

---

### Post by BarryDocks on 2010-07-08
Thanks for the replies.

> **stlsaint said:**
> Im not sure if your able to encrypt only certain portions of a lvm without encrypted all of it. You may want to consider seperating whatever data you want encrypted onto another partition and just encrypting that.
I am not using LVM.  I have the OS and swap on one drive and data on a completely separate drive that is mounted in the filesystem.  I don't need LVM as by the time this drive is full the system will be obsolete!!  I just want to encrypt the data drive in the event the server was nicked (we recently has a break in and some computer hardware was in the process of being stolen when the fuzz turned up)

> **HermanAB said:**
> Howdy,

You could use LUKS and put the key on a USB memory stick.  Then of course, the stick should be plugged in at boot time, but it may suffice for your situation.
I have seen reference to this and it seems a good idea, do you know of any straight forward how-to's?

---

### Post by gurgelsmurf on 2011-06-15
Resurrecting this pretty old thread since it describes exactly the same scenario as I want to achieve.
I have played around a bit with it in a vbox environment.
I have come so far as the raid array is up and encrypted with the passphrase stored on a usb pendrive.
The problem is that in 10.04 server usb drives will not be automounted when they are inserted.
I want it to be automounted and then to automatically launch some magic script that uses the key from it and decrypts the raid array.
Does anyone know how to achieve this?

---

