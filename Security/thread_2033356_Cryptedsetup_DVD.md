---
title: "Cryptedsetup DVD"
date: 2012-07-26
forum: Security
---

### Post by Werewolf6851 on 2012-07-26
I have a few crypto bottles I set up with cryptsetup sized to fit on a DVD-R
when burned to dvd (ie growisofs -dvd-compat -speed=4 -Z /dev/sr0=crypt.vol)
then reinserted and giving the password I get
"Error unlocking device: cryptsetup exited with exit code 1: device-mapper: reload ioctl failed: Invalid argument"
Guessing the "-r" option not getting applied by the auto mounter.
Since forgetting the -r in
cryptsetup luksOpen /dev/dvd dvd
get the message
"device-mapper: reload ioctl failed: Invalid argument"

Any Ideas?

I'd like it to get it mounted to /media/"file system label"
like encrypted usb drives do
Wolf

---

