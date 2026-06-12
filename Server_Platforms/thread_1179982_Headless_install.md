---
title: "Headless install"
date: 2009-06-06
forum: Server Platforms
---

### Post by John_5 on 2009-06-06
I have a computer without a video card that I want to install Ubuntu server 9.04 on. Is it possible to install Ubuntu server without a monitor, maybe by via SSH?

---

### Post by tad1073 on 2009-06-06
how can you ssh w/o ssh on server?

---

### Post by iponeverything on 2009-06-06
Found this:

[http://blog.nominet.org.uk/tech/2005/09/19/building-a-redhat-enterprise-linux-serial-console-boot-dvd/](http://blog.nominet.org.uk/tech/2005/09/19/building-a-redhat-enterprise-linux-serial-console-boot-dvd/)

This would be fun thing to try, if you do and works let me know!

mount the iso via loopback:

```
mount -o loop ubuntu-8.04.1-server-i386.iso /mnt

```
Modify this file:

```
/mnt/isolinux/isolinux.cfg

```



Add these lines to top of file:

```

serial 0 9600
default serial
prompt 1
timeout 60
display isolinux.txt
label serial
kernel /install/vmlinuz
append initrd

LABEL serial
kernel /install/vmlinuz
append file=/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz console=ttyS0
```

remove the duplicate lines like "timeout" and "default"

umount the iso, burn it. Plug in a serial null modem cable from the server you are going to install on to the machine that you're going to ssh to.

ssh into the other machine setup and start minicom and boot off CD and see what happens..

BTW -- I have no idea if it will work, but it would be cool if it did.

---

### Post by v3xtra on 2009-06-06
Do you have a computer that has a video card in it right now?  The best / easiest thing to do would be to either switch the video card out into the actual server and use it to install / set up ssh with and then remove it so that it will be working.  The other option is to just put the hard drive into the working computer with the video card, install the server onto the new hard drive and set everything up for it, although I don't know if the settings may need to be changed once it switches computers, so the first option might be your best.

---

### Post by Serangan on 2009-06-07
Or maybe have a automatic install?
As outlined here: [https://help.ubuntu.com/9.04/installation-guide/i386/automatic-install.html](https://help.ubuntu.com/9.04/installation-guide/i386/automatic-install.html)

Never tried this myself. But it should work

---

### Post by Vegan on 2009-06-07
Try installing it with a video card like I did. Then when you have remote access working, yank the card.

If you motherboard has a built-in one like new boards have, they draw so little power its no big deal.

---

