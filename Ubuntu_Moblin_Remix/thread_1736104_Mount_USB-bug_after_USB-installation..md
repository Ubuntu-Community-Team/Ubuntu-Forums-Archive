---
title: "Mount USB-bug after USB-installation."
date: 2011-04-22
forum: Ubuntu Moblin Remix
---

### Post by JorisSpekreijse on 2011-04-22
Hello,

I have noticed that my Ubuntu 11.04 is facing a bug that is not uncommon when searching on the internet.
My laptop is unable to mount a USB-stick. It seems that something during installation made the following fstab.

[PHP]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5e009437-78b5-4129-b6a4-585e5882104b none            swap    sw              0       0
[/PHP]

Nice, my USB should be mounted to root. O_o
Seeing the line that was added during installation about swap, it should be possible to alter the fstab to a proper fstab.

Is this already reported to Ubuntu?

---

### Post by Clyssus on 2011-05-01
I'm having problems with USB storage devices also, although I installed from a Live CD. I have been trying to transfer mp3 / .flac files from an external HD to the music file. Sometimes the transfer is dropped before it is complete (the only way to get Ubuntu to mount the HD again, is to turn the power off on the external drive and then turn it back on again). Some of the transfers seem to be complete, but when I look in the transfered folder some or all of the files are missing. When I plug a new USB storage device in it takes forever for Ubuntu to mount it. Quite annoying, considering I have roughly 10,000 songs to transfer. I've found that if I transfer one folder at a time it works relatively well, although Ubuntu still unmounts the HD and drops the transfer from time to time. When I tried to transfer every thing at once it dropped the transfer and only completed a small fraction of the transfer. This is a nightmare!!!! It's driving me crazy!!!!

---

### Post by lagerratrobe on 2011-05-06
I'm having problems with mounting USB devices since upgrading from 10.10 to 11.04.  In some cases it will mount a smaller Kingston USB stick, but fail to recognize a larger SATA hard drive enclosure. Booting into "Previous Linux" version allows all USB devices to show up, so it looks like a regression in 11.04.

dmesg shows
```

[ 4711.300113] sd 9:0:0:0: sense urb submission failure
[ 4711.320025] sd 9:0:0:0: sense urb submission failure
[ 4711.340043] sd 9:0:0:0: sense urb submission failure

```

If I can't find a solution, I'll probably drop back down to 10.10.

---

