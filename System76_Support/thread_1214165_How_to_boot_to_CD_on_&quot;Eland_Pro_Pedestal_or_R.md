---
title: "How to boot to CD on &quot;Eland Pro Pedestal or Rack&quot;"
date: 2009-07-15
forum: System76 Support
---

### Post by jcrn on 2009-07-15
Hello,

Brand new "Eland Pro Pedestal or Rack" server, I tried booting to the cdrom and couldn't find such an option in the BIOS.  How do I boot from a CD?  The only three options the BIOS gives me are boot to 3ware, net boot, and some sort of management shell.

Also, suppose I were to reinstall Ubuntu 8.04, are there other system76 things that should be put on there, like cooling daemons, etc.?

jrc

---

### Post by thomasaaron on 2009-07-16
> Also, suppose I were to reinstall Ubuntu 8.04, are there other system76 things that should be put on there, like cooling daemons, etc.?

No, just install Ubuntu on it.

> Brand new "Eland Pro Pedestal or Rack" server, I tried booting to the cdrom and couldn't find such an option in the BIOS. How do I boot from a CD?

I've imaged many Eland's from a CD, so it will definitely boot from one. Have you tried to insert a bootable CD and just restart the machine? It may be set up to boot from a CD by default, although I'd be seriously surprised if there wasn't something in the BIOS for it.

---

### Post by jcrn on 2009-07-16
Hmmmmmm, there's a cd/dvdrom physically installed in the server, but as far as I can tell it's not being recognized:

root@goldlake:~# find /dev | grep cdrom
root@goldlake:~# find /dev | grep dvd
root@goldlake:~# find /dev | grep rw

Will it void my warranty if I open up the box and make sure somebody plugged the thing into the motherboard before shipping it?

jrc

---

### Post by thomasaaron on 2009-07-16
No, that wont' void your warranty. 

Run...

```
lspci
```

---

### Post by jcrn on 2009-07-16
Okay, I fixed it.  The SATA cable for the cdrom wasn't plugged into the motherboard.  Plugged it in and now it works.

Thanks!

---

