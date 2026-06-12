---
title: "Unable to start OS after install"
date: 2017-06-21
forum: Ubuntu/Debian BASED
---

### Post by jesus-freak on 2017-06-21
I've tried to install many different distros. Most of them are debian/ubuntu based distros but I have even tried some Arch distros and I have the same problem. The Distros goes through the installation process without any problems or errors. When it is finished installing and I restart the system, I get this screen: [http://i47.photobucket.com/albums/f167/hendrix4000/P1860084.jpg](http://i47.photobucket.com/albums/f167/hendrix4000/P1860084.jpg)

 I've never had trouble with Linux on this computer before so this seems really weird to me.

---

### Post by lisati on 2017-06-21
The first thing to check, and probably easiest, is that your BIOS/UEFI is set to boot from the HDD first. Failing that, there are one or two other things we can check.

---

### Post by jesus-freak on 2017-06-21
Of course I set the bios to boot from the HDD first. I've been installing and trying Linux Os's for several years now and in the last 6 months or so I started getting this problem with most distros.

---

### Post by jesus-freak on 2017-06-24
No ideas on this?

---

### Post by howefield on 2017-06-24
Anything interesting in your /etc/network/interfaces file ?

```
cat /etc/network/interfaces
```

---

### Post by jesus-freak on 2017-06-26
Well I can't run this command on any of the systems that I am having problems with because as the title says I can't log into the OS after installing it. That being said, Linux Mint is one of the very few that installed and allowed me to log in and use the OS. So I ran that command on my Linux Mint system and got this 

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by jesus-freak on 2017-06-28
Okay, I've figured out what the problem is, I just don't understand what is causing it. The problem is that the usb is installing the system fine, it's just not flagging the HD to boot. So to get around this I have to install the OS, then reboot into the live CD, open gparted and flag the HD to boot. Then I can restart into the new system. I have tried making the usb with unetbootin, disks, startup disk creator, and image writer and I have the same results each time. The system is installed but the drive is not flagged to boot.

---

