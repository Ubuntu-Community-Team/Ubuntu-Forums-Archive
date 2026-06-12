---
title: "How to decrypt CD encryptes with loopback/eas256?"
date: 2013-03-14
forum: Security
---

### Post by lduperval on 2013-03-14
Hi,

I have a CD that was encrypted with loopback and eas256. The last time I decrypted it, I used this command:

sudo mount -t iso9660 /dev/dvd /mnt/dvd -o loop,encryption=aes

and it worked fine. Now, using the sme command, I get this:

> mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


When I look in syslog, the only thing I see is:

> [37935.023276] Intel AES-NI instructions are not detected.


However, I am using the same machine I used when I did the encryption. Right now, I think the problem is that I don't have loop-eas-utils installed, but if I try to install it, I get a meessage saying that it will uninstall fuse, fuse-utils, gfs-fuse, and other packages. So I'm thinking that's not a good idea.

How can I read this CD now? Can it be read using a different approach, while still recognizing my original password?

Thanks,

L

---

### Post by jasondean on 2013-06-13
Hello, i had a similar problem with it wanting to uninstall fuse, this website showed how to compile a loop-aes-utils that doesn't conflict with fuse, i also had to use this site to build loop-aes-utils for my computers that use Raring, for some reason loop-aes-utils was removed from that version.

> **Temporary debianized loop-aes-utils not conflicting with fuse**
Since beginning of the year 2011 fuse package is in conflict with loop-aes-utils. It has been reported many times and finally somewhere in October 2011 someone wrote a patch for mount and umount which solves the problem.

Unfortunately I need both on daily basis so I could either: downgrade fuse and wait until someone changes "conflict" line to something version-dependent and not just absolute: loop-aes-utils. or do compile my own loop-aes-utils and use it under different name.
[http://code.opoki.com/loop-aes-utils-debian/](http://code.opoki.com/loop-aes-utils-debian/)

---

