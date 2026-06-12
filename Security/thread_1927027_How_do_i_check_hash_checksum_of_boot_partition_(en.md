---
title: "How do i check hash checksum of boot partition? (encryption security)"
date: 2012-02-17
forum: Security
---

### Post by maloki on 2012-02-17
Hi.
For those of you who use full system encryption, you may or may not have heard of a small program called "evil maid" which in minutes can install itself from a usb to the MBR, then works as a key logger, which then results in a worthless encryption.

One solution would be to install the boot partition to a usb and booting from it every time, a second solution would be to check md5 hash checksum of the boot partition, before (live cd?) or after login.

My question is: how do I check the hash of my boot partition?
Any ideas on how to render a hardware attack useless (powered of computer) would also be appreciated

---

### Post by unspawn on 2012-02-18
> **maloki said:**
> how do I check the hash of my boot partition?
Regular partitions can be checked with md5sum, sha1sum etc, etc as in
```
sha512sum /dev/devicename
```
and the same goes for partitions saved to a file with say 'dd'. If you want just n bytes you could use say ```
od /dev/devicename -N *n*|sha1sum
```. 
* Note checking hashes is not a "solution" but a means of detection change.

---

### Post by maloki on 2012-02-18
> **unspawn said:**
> Regular partitions can be checked with md5sum, sha1sum etc, etc as in
```
sha512sum /dev/devicename
```
and the same goes for partitions saved to a file with say 'dd'. If you want just n bytes you could use say ```
od /dev/devicename -N *n*|sha1sum
```. 
* Note checking hashes is not a "solution" but a means of detection change.

Thank you for the info.

I am aware that it isn't a solution, but a way to see if the boot partition have have been compromised.
My solution which I have devised is as follow: seperate boot partition on SD card and keyfiles on a USB-stick, if ever the USB-stick or SD card ware ever to leave my side, a hash checksum would ensure if any tampering have been made to them. Another solution would be to restore the USB and SD from a encrypted backup.

The only security risk left with the above mentioned solution would be hardware malware, hardware keylogger or me leaving the computer on.

---

