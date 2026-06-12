---
title: "Will not start up"
date: 2010-06-22
forum: Server Platforms
---

### Post by happyhacker on 2010-06-22
After working OK for months my Ubuntu will not boot. I have connected a terminal, the BIOS seems to say the hda is there OK but I get the following at end of screen on boot:

mount: mounting /root/dev on dev/.static/dev failed No such file...
mount: mounting /sys on root/sys failed No such file...
mount: mounting /proc on /root/proc failed No such file...

Target filesystem does not have /sbin/init.
No init found try passing init= bootarg.

ends with (initramfs) in the command line.

There is other stuff before that like "I/O error, dev sda, sector (n). Looks as if here is a sda fail somewhere. The unit is not being issued an IP address on the network. PS I know my hdb is full but that has not caused a problem before. I have done no updates recently. Appreciate assistance.

---

### Post by wilee-nilee on 2010-06-22
> **cantthinkofanickname said:**
> After working OK for months my Ubuntu will not boot. I have connected a terminal, the BIOS seems to say the hda is there OK but I get the following at end of screen on boot:

mount: mounting /root/dev on dev/.static/dev failed No such file...
mount: mounting /sys on root/sys failed No such file...
mount: mounting /proc on /root/proc failed No such file...

Target filesystem does not have /sbin/init.
No init found try passing init= bootarg.

ends with (initramfs) in the command line.

There is other stuff before that like "I/O error, dev sda, sector (n). Looks as if here is a sda fail somewhere. The unit is not being issued an IP address on the network. PS I know my hdb is full but that has not caused a problem before. I have done no updates recently. Appreciate assistance.

If your HD is full already log files will max it out possibly. What distro are you using.

---

### Post by happyhacker on 2010-06-22
I think it's Ubuntu server 8.3. I ahve not upgraded it to the latest yet.

---

### Post by happyhacker on 2010-06-22
I am downloading Knoppix in case I need to boot from that to resolve.

Assuming it's a log overrun, how do I deal given the above (my first entry above) state. Is there a command line available?

---

### Post by happyhacker on 2010-06-22
I have blown a new Ubuntu live CD and booted from that and done a check in GParted and this has allowed a boot to a logon request which I did and got in BUT during booting there were many [[COLOR="Red"]FAIL[/COLOR]} errors but some things started like SAMBA but I still have a corrupt system (no ethernet dhcp assigned) and some programs did not start. Some directories reported as missing!

Any ideas what to do next appreciated.

---

