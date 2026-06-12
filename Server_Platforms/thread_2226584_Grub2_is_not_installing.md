---
title: "Grub2 is not installing"
date: 2014-05-28
forum: Server Platforms
---

### Post by joshua31 on 2014-05-28
I am a new linux user who desires to create a home server. I followed every instruction i could think of which is relevant on how to do so using ubuntu server 14.04. I am using an HP compaq that has 2 ghz of processing power, 2 GB random access memory, and an 80 GB HDD. I am able to fully install everything that is available, with exception to the grub2 bootloader. I get up to where it asks if it wants me to make grub2 my bootloader our of the MBR. I say yes, then it tells me that it can't install grub2 to harddisk, or on any other drive i try to set it up on. I finally lost patience and downloaded LILO, hoping it'd work. Initially, it could not find /dev/sdb1 (somehow not created according to the system), so i re-installed it. I have been installing it with a 4GB flash drive that i installed the ubuntu server software into so that i could take one of the computers i have lying around and create a server. After i re-installed, i tried to boot with no bootloader instead. It then came out with a message that read: LILO keytable/ checksum error. I tried to re-install after that (again) and it continues to give me that same error. If i could get some help, i would be very appreciative.

---

### Post by Bucky Ball on 2014-05-28
Any reason you are attempting to install it on sdb??? Generally sda is where you'd put it, although this is probably not the issue ...

---

### Post by joshua31 on 2014-05-28
I had not known the difference between the various sdb, sda, etc. It was a default of sort. As far as i can determine as of now.

---

### Post by Bucky Ball on 2014-05-28
Well, as this machine sounds like it has one 80Gb hard drive in it, sdb would be a usb stick or another device (do you have an external drive or USB dongle plugged in?). The local hard drive (in the machine) is sda. You just want to install it to sda, not sda1 or anything else. Give that a try.

And welcome to the forums, BTW. ;)

---

### Post by joshua31 on 2014-05-28
Will do, I'll let you know if that works.

Oh yeah, thanks!

---

### Post by joshua31 on 2014-05-28
Is it normal for the computer to mark the first partition as sdb?

---

### Post by sudodus on 2014-05-28
No, but it can happen that the internal disk is called sdb. Normally the internal disk is sda.

The first partition in the first disk is sda1, the first partition in the second disk is sdb1, ...
 
The best identification of partitions is via the UUID, that is normally used in the configuration file /etc/fstab.

See the output of the following commands
```

cat /etc/fstab
```

```
sudo blkid
```

---

### Post by joshua31 on 2014-05-28
I will do so when it finishes installing the software

---

### Post by joshua31 on 2014-05-28
hey. thank you for the suggestion. I was able to correctly install grub2 with no errors at all.

---

### Post by Bucky Ball on 2014-05-28
Glad it all worked out. ;)

To help future travelers, how did you do it exactly?

---

### Post by joshua31 on 2014-05-30
It worked out when I went through the install again, and this time as i was creating partitions, made sure i found what i was supposed to allow grub 2 to be loaded out of. For me (for some reason) it was sdb. When it asked me if i wanted to write into the MBR, i said no and specified /dev/sdb as where i desired it to be written to. It worked out perfectly with no bugs after that.

---

