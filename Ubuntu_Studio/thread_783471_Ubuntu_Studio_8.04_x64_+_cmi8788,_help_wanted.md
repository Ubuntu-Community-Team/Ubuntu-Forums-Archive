---
title: "Ubuntu Studio 8.04 x64 + cmi8788, help wanted"
date: 2008-05-05
forum: Ubuntu Studio
---

### Post by more10 on 2008-05-05
I have successfully installed Ubuntu Studio 8.04, 64 bit version. Its an old 939 system with an X2 cpu.

My sound card is a Razer Barracuda AC-1. [ALSA's snd-oxygen For C-Media CMI8788 APUs]("http://www.phoronix.com/scan.php?page=article&item=939&num=1") says it should work.

I have downloaded the beta 2008-04-15 driver from [http://www.alsa-project.org/main/index.php/User:ClemensLadisch]("http://www.alsa-project.org/main/index.php/User:ClemensLadisch").

I followed the guide [http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen]("http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen"), adding some packages in order to compile.

I had to run configure with a switch:
```
./configure --with-kernel /usr/src/linux-headers-2.6.24-16-generic/
```
Have no idea if this is correct.

This is where I get stuck:
```
#alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
```
Googling this error I found this [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg13874.html]("http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg13874.html"). So I typed:
```
#strace -eopen alsamixer
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/libm.so.6", O_RDONLY)        = 3
open("/lib/libdl.so.2", O_RDONLY)       = 3
open("/lib/libpthread.so.0", O_RDONLY)  = 3
open("/lib/libc.so.6", O_RDONLY)        = 3
open("/lib/librt.so.1", O_RDONLY)       = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/root/.asoundrc", O_RDONLY)       = 3
open("/root/.asoundrc.asoundconf", O_RDONLY) = 4
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENODEV (No such device)
open("/dev/aloadC0", O_RDONLY)          = -1 ENODEV (No such device)
open("/dev/snd/controlC1", O_RDONLY)    = -1 ENODEV (No such device)
.......more error lines

```
Then
```
#ls -al /dev/snd/controlC0
crw-rw---- 1 root audio 116, 0 2008-05-05 22:58 /dev/snd/controlC0
#ls -al /dev/aloadC1
crw-rw---- 1 root audio 116, 32 2008-05-05 22:58 /dev/aloadC1

```

Any help appreciated.

Mårten

---

