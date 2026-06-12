---
title: "Ubuntu 10.04 minimal, login info warning"
date: 2010-09-30
forum: Server Platforms
---

### Post by dragos2 on 2010-09-30
I installed Ubuntu 10.04.1 Server x86_64 minimal, updated, upgraded, then
I blacklisted all not used modules in /etc/modprobe.d/blacklist.conf:
```

# Custom
blacklist snd_intel8x0
blacklist ppdev
blacklist joydev
#blacklist lp
blacklist parport_pc
blacklist psmouse
blacklist serio_raw
blacklist i2c_piix4
#blacklist usbhid
#blacklist e1000

```

and after reboot I had this after login:

```

System information disabled due to load higher than 1.

```

What caused that ? It is a test system in VirtualBox.

---

### Post by CharlesA on 2010-09-30
It's fine. It's trying to run landscape-sysinfo, but is set to run it if the system load is not higher then 1.

You run find the system load by running top, htop, w, who, uptime, etc.

I run into the same thing on my VMs using VirtualBox.

---

### Post by dragos2 on 2010-09-30
> **CharlesA said:**
> It's fine. It's trying to run landscape-sysinfo, but is set to run it if the system load is not higher then 1.

You run find the system load by running top, htop, w, who, uptime, etc.

I run into the same thing on my VMs using VirtualBox.

I wonder why the load increases when I blacklist those modules.
The system has nothing else installed besides Ubuntu 10.04.1 minimal.

---

### Post by CharlesA on 2010-09-30
Happens to me on clean installs. I suppose it's just the way VirtualBox emulates the hardware or something. *shrugs*

---

### Post by dragos2 on 2010-09-30
> **CharlesA said:**
> Happens to me on clean installs. I suppose it's just the way VirtualBox emulates the hardware or something. *shrugs*

Possibly, but we can only know for sure on real hardware.

---

### Post by CharlesA on 2010-09-30
> **dragos2 said:**
> Possibly, but we can only know for sure on real hardware.

Indeed. For all I know, it could be coming up since I blacklist these two kernel modules right after doing a clean install:

fbcon
vga16fb

---

### Post by buntolith on 2010-09-30
I just did a new install of 10.04 using an atom motherboard and a couple of hdd in raid 5. I got the same message when I logged in for the first couple of times and when I did landscape-sysinfo I got a system load of approximately 1.8. I thought it was the motherboard but after leaving the server on for a few hours the system load dropped down to below 1. Right now it is down to 0.0. This problem just fixed itself for me.

---

### Post by ubuking on 2011-01-30
> **buntolith said:**
> I just did a new install of 10.04 using an atom motherboard and a couple of hdd in raid 5. I got the same message when I logged in for the first couple of times and when I did landscape-sysinfo I got a system load of approximately 1.8. I thought it was the motherboard but after leaving the server on for a few hours the system load dropped down to below 1. Right now it is down to 0.0. This problem just fixed itself for me.
I have got the same experience, just a matter of waiting, and apparently in the meantime nothing goes wrong

---

### Post by warfie on 2013-04-13
> **CharlesA said:**
> It's fine. It's trying to run landscape-sysinfo, but is set to run it if the system load is not higher then 1.

You run find the system load by running top, htop, w, who, uptime, etc.

I run into the same thing on my VMs using VirtualBox.

Is it possible to modify this behaviour? make it ignore the system load and display sysinfo anyway?

---

### Post by sandyd on 2013-04-14
**Necromancing - Thread closed**
Please do not post in threads more than one year old as many things change between Ubuntu releases and the solutions provided in the thread may not be pertinent to your installation.

Thanks!

---

