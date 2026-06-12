---
title: "Recovering data from recovery mode"
date: 2010-03-12
forum: Server Platforms
---

### Post by majestiknl on 2010-03-12
Hello Ubuntu fellows,

Today I wanted to make a backup of my Ubuntu server. Since the program wasn't working for me, I rebooted my computer and right now it wont boot.

Now I entered recovery mode and I'm trying to recover my /var/www and /etc/mrtg folders.

I want to copy them to my USB-Stick but Ubuntu wont do this.

The command I tried:
```
cp -r /var/www /dev/sdg1/www
```

I already created the folder via a other system.

I also tried to mount the USB stick:
```
mount /dev/sdg1 /mnt/usbe
```

But im getting the following error: error while loading shared libraries: /lib/libsepol.so.1: Invalid ELF header.

Please help me to recover/save my data!

Thanks in advance,

Tristan

---

### Post by cdenley on 2010-03-12
Use a livecd to recover any files. If you can't even run the "mount" command, then there is something seriously wrong with your install. You might want to verify your memory and hard are working correctly before reinstalling.

---

### Post by BobVila on 2010-03-12
> **cdenley said:**
> Use a livecd to recover any files. If you can't even run the "mount" command, then there is something seriously wrong with your install. You might want to verify your memory and hard are working correctly before reinstalling.

+1 for the livecd. The ubuntu install disc should work fine for you, although there are some livecds more specifically tailored to this kind of work.

---

