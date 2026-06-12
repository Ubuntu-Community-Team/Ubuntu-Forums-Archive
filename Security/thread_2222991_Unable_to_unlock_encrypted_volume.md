---
title: "Unable to unlock encrypted volume"
date: 2014-05-09
forum: Security
---

### Post by raincityrunner on 2014-05-09
Volume set up in 12.04, now unable to access in 14.04.

Error as follows:
```
Error unlocking /dev/sdl1: Error spawning command-line `cryptsetup luksOpen "/dev/sdl1" "luks-b5479205-958b-43ad-9b73-06cd96ce7cf0" ': Failed to execute child process "cryptsetup" (No such file or directory) (g-exec-error-quark, 8)
```

---

### Post by darthpbal on 2014-05-09
I've got literally the same issue. I installed from a live USB. The drive I'm trying to access is a 32 GB SD card that's password protected, and when I try to access it, I type in my password and I get this message. I was able to access the drive fine before installing 14.04 this morning.

---

### Post by bashiergui on 2014-05-10
Perhaps this will help
[http://askubuntu.com/questions/213537/cannot-mount-luks-encrypted-usb-on-boot-after-12-10-upgrade](http://askubuntu.com/questions/213537/cannot-mount-luks-encrypted-usb-on-boot-after-12-10-upgrade)

---

### Post by shinyblue on 2014-05-14
Fix: sudo apt-get install cryptsetup

Bug: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1310174](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1310174)

---

