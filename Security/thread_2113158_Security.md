---
title: "Security"
date: 2013-02-06
forum: Security
---

### Post by gordie69 on 2013-02-06
Hey guys it's gordie69 again to be a pain but I dual booted W7 64 Bit and Ubuntu 12.10 32 bit and when I went through the install of ubuntu, I incryted the home folders aswell now I'm I secure dual booting like this or should install Ubuntu on a second drive and switch from drive to drive in cmos when booting up.
I love Ubuntu and I'm only using Windows for gaming but I use Ubuntu for my home banking and finance no downloading just facebook, twitter and browsing the web on my forums. The only downloading I do is on Windows.

Thanks you

---

### Post by Hungry Man on 2013-02-06
Ah, I see. Yeah, that's fine.

---

### Post by gordie69 on 2013-02-06
thanks hungry man ubuntu is safer then windows sorry but I really starting hate windows love the ubuntu but some say you need a firewall but I thought the kernel had it but in built in

---

### Post by cariboo on 2013-02-06
> **gordie69 said:**
> thanks hungry man ubuntu is safer then windows sorry but I really starting hate windows love the ubuntu but some say you need a firewall but I thought the kernel had it but in built in

The firewall is built in, but it isn't enabled by default, to enable it use the following command:

```
sudo ufw enable
```

To check the status:

```
sudo ufw status
```

to turn it off:

```
sudo ufw disable
```

---

### Post by gordie69 on 2013-02-07
Thanks Cariboo907 just trying to make myself safe I'm tired of Windows crashing or not responding boot everytime you do anything crap I love the ubuntu been with since ubuntu 7 and lot of improvments keep up the great work.
I wish I could get the 64 bit 12.10 to work on my system I get it installed and drivers done and it would go to the desktop stops at the desktop screen but no icons and love the new kernel for 13.04 3.8 thats great also

---

### Post by Ms. Daisy on 2013-02-09
Check out this document, it addresses a lot of basic security questions.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

