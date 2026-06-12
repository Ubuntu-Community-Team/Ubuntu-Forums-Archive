---
title: "Encrypt Live USB?"
date: 2009-06-07
forum: Security
---

### Post by Jekshadow on 2009-06-07
Just wondering, is there any way to encrypt a external 100GB drive, similar to the way the Ubuntu Alternate CD does it for normal installs?

---

### Post by sgosnell on 2009-06-07
Why do you want to encrypt a live CD?  

It should be possible to encrypt any drive, regardless of what is on it, but being able to mount it is another matter.  If the drive is encrypted, how would you boot from it, when an OS is necessary to decrypt it for use?

---

### Post by Jekshadow on 2009-06-08
The way the Alternate CD works is it puts /boot on a separate, unencrypted partition. That partition contains a kernel, which when detecting the other, encrypted partition, asks you for the password and then unencrypts the partition, allowing Ubuntu to run normally. I want to set something similar up.

---

### Post by Jekshadow on 2009-06-08
Found my answer here:

[http://www.linux.com/archive/feature/125625](http://www.linux.com/archive/feature/125625)

It's for debian, but it should be very simple to tweak it (if it needs tweaking at all) for Ubuntu.

---

### Post by R()_K()_H() on 2012-05-08
@Jekshadow did you actually get it working? I'm performing the format and install right now for Ubuntu 12.04 LTS and will report back with my experience. 

If anyone else has installed Ubuntu from a Live CD to a USB Drive using encryption for the filesystem (save the grub) please help out and post your findings.

Thanks!

---

### Post by oldos2er on 2012-05-09
Old thread closed. Please start a new thread.

---

