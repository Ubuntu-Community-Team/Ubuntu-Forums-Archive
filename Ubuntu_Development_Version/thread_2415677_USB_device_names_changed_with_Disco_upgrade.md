---
title: "USB device names changed with Disco upgrade"
date: 2019-03-29
forum: Ubuntu Development Version
---

### Post by dbarron on 2019-03-29
It only took me about five minutes to figure it out, but my two usb storage drives (/dev/sdc and /dev/sdb) apparently switched order.  Being as one is formatted ntfs and one is ext4, it was pretty easy to tell something was different wrong and just change device names in /etc/fstab.
I assume this is kernel related...just wanted to post in case it helps someone else upgrading.

---

### Post by jeremy31 on 2019-03-29
Disco has not been released yet, so moved to Ubuntu Development

---

### Post by rbmorse on 2019-03-29
I've always found the way Linux enumerates attached storage to be somewhat capricious.  For me, using UUID= in fstab is the most reliable way of ensuring required/desired partitions get mounted during the IPL.

---

### Post by TheFu on 2019-03-29
> **dbarron said:**
> It only took me about five minutes to figure it out, but my two usb storage drives (/dev/sdc and /dev/sdb) apparently switched order.  Being as one is formatted ntfs and one is ext4, it was pretty easy to tell something was different wrong and just change device names in /etc/fstab.
I assume this is kernel related...just wanted to post in case it helps someone else upgrading.

Device names haven't been guaranteed in Linux for over a decade. Use LABEL, UUID, or by-path/ names, if you need to point to the same partitions consistently.  The by-path/ method assumes that no physical connections are changed.  UUIDs and LABELs can be duplicated by accident and cause issues.  by-path/ won't.

I doubt this is specific to 19.04 alpha.

---

### Post by dbarron on 2019-03-30
I should have realized that...I'm old school and it shows sometimes ;)  Thank you.

---

