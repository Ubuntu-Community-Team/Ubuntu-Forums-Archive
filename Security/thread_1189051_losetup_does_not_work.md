---
title: "losetup does not work"
date: 2009-06-16
forum: Security
---

### Post by yogg on 2009-06-16
Hi

I have the following Problem:
losetup -e aes256 /dev/loop0 /cdrom/casper/filesystem.squashfs
ioctl: loop_set_status: invalid argument, requested cipher or key length (256 bits) not supported by kernel

But that can't be.
```

modprobe loop
modprobe cryptoloop
modprobe aes-i586

cat /proc/modules | grep loop
cryptoloop 10880 0 - Live 0xf96eb000
loop 23052 1 cryptoloop, Live 0xf96f9000

cat /proc/modules | grep aes
aes_i586 15744 0 - Live 0xf9788000
aes_generic 35880 1 aes_i586, Live 0xf98bf000

losetup -e aes256 /dev/loop0 /cdrom/casper/filesystem.squashfs
ioctl: loop_set_status: invalid argument, requested cipher or key length (256 bits) not supported by kernel

```The needed modules are loaded. Make I something wrong? This should run in initramfs. If I try the same on my Ubuntu desktop it works perfectly (it also runs in an debian initramfs :/).

By the way.
Is there a workaround for more?
cat /proc/modules | more
does not work :(

---

### Post by HermanAB on 2009-06-16
Howdy,

Cryptoloop is insecure and is deprecated.  Use LUKS instead.

This may help:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by myob01 on 2010-06-14
> **HermanAB said:**
> Howdy,

Cryptoloop is insecure and is deprecated.  Use LUKS instead.

This may help:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)


I had the same problem and while I understand that cryptoloop is  deprecated, and intend to use better methods in future, I have a  cryptoloop encrypted file which I need to access before I do. I also  have legacy backups encrypted with cryptoloop which I may need at some  time. just to say 'use LUKS instead' is not very helpful - I need to  access these files!


Yogg:

solution - use 'AES256' instead of 'aes256' - the case of the crypto module has changed. thats all. (you may need to install losetup-aes  package and possibly modprobe cryptoloop and aes. I did these things  before noticing the change of case but after that it worked

---

