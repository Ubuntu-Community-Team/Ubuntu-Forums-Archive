---
title: "ubuntu-9.10-server-i386 ISO seems to be corrupted on HTTP"
date: 2010-02-03
forum: Server Platforms
---

### Post by mikymike on 2010-02-03
Hello,

I'd like to report an issue I've had with Ubuntu server ISO.
I downloaded ubuntu-9.10-server-i386.iso by HTTP on ubuntu's website and burned it on a CD. It doesn't work well. I got an error in udevadm sys/devices/pci0000 etc...
First I thank that it was a problem with the hardware, but it seems that it's the ISO that is corrupted.
I checked the MD5 checksum and it's not good.
Then I download the same ISO a second time (by HTTP) and same problem.
Finally, I download it through BitTorrent, MD5 is OK and installer works fine!

So it seems to me that the ubuntu-9.10-server-i386.iso that we can download by HTTP is not the same as the torrent one.
Maybe I'm wrong. Anyway, if I'm right I hope this information will be useful for administrators.

Regards,

Michaël

---

### Post by cdenley on 2010-02-03
Looks fine to me.
```

cdenley@ubuntu:~$ md5sum ubuntu-9.10-server-i386.iso
55618ad5f180692f9dac20cbff352634  ubuntu-9.10-server-i386.iso

```
Which mirror were you downloading from?

---

