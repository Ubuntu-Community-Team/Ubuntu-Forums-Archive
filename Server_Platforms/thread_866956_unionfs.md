---
title: "unionfs"
date: 2008-07-22
forum: Server Platforms
---

### Post by Necromantis on 2008-07-22
Hello,

This is a 2 part problem:

1st I'm using usb drives who have hardware standby. I have placed the UUID in the fstab but; it seems to me that the usb drives takes too long to respond on boot up and they aren't mounted; a simple sudo mount -a after boot up works. Is there a way to make the fstab wait few second for the seagate usb drives to warm up?

2nd
I had for a short period of time unionfs working but after few days it just died and I can't get it to work again.. I remove + install it back which didn't solve the problem.

I get a [Fail] message on boot up with: mount: special device unionfs does not exist.
with a dmesg | grep unionfs I get:
Registering unionfs 1.4
unionfs debugging is not enable
unionfs: error accessing hidden directory 'usb1=r'

my fstab reads:
unionfs /mergeusb unionfs dirs=/usb1=r:/usb2=r 0 0

I have no idea why this stop working :( Anyone ?

---

