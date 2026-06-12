---
title: "Quick freebsd install question"
date: 2010-04-29
forum: The Cafe
---

### Post by PurposeOfReason on 2010-04-29
Getting to the network screen (doing a ftp install), I use dhcp which fills in all by the hostname and domain. I put whatever in as they shouldn't really be important but when I hit enter it says it cannot resolve hostname '<ftp site>'. Windows and linux both connect fine.

---

### Post by drreed on 2010-04-29
> **PurposeOfReason said:**
> Getting to the network screen (doing a ftp install), I use dhcp which fills in all by the hostname and domain. I put whatever in as they shouldn't really be important but when I hit enter it says it cannot resolve hostname '<ftp site>'. Windows and linux both connect fine.

I've installed FreeBSD about 6 times in the last month and don't recall any difficulties related to networking.
I do seem to recall it asking me whether I wanted ipv6 support, and I answered no. Do you have more than one adapter? I think it asked me which one it should use as the default connection.

If you haven't solved it and want me to, I can run an install to step through that part and see what happens exactly. My CD is version 8.

---

### Post by DeadSuperHero on 2010-04-29
My best advice is to consult the FreeBSD handbook and [see if it has anything on FTP connections]("http://www.freebsd.org/doc/en/books/handbook/network-ftp.html").

Alternatively, just [check the table of contents]("http://www.freebsd.org/doc/en/books/handbook/"). There's loads of good stuff when it comes to networking.

---

### Post by PurposeOfReason on 2010-04-29
Turns out it is a common problem with usb/ftp installs. I had to ghetto hack it by "installing" from usb, then getting into the nes install and mounting the usb and copying all I needed off. Stupid, but it works.

---

### Post by drreed on 2010-04-29
> **PurposeOfReason said:**
> Turns out it is a common problem with usb/ftp installs. I had to ghetto hack it by "installing" from usb, then getting into the nes install and mounting the usb and copying all I needed off. Stupid, but it works.


Cool. My only problem with it is as a desktop. It's probably my hardware, but I got a lot of lockups and core dumps. Frustrated, I re-installed without all that fluff. As a server, it hasn't given me any problems, but it doesn't do much but sit there.:P

---

### Post by PurposeOfReason on 2010-04-29
I've never used it before so we'll find out. Is there a flag I can put for ports to not prompt me for things and just install with the default options? I just want to go into dwm, run make and let it grab xorg and everything for me and not ask questions.

---

### Post by kk0sse54 on 2010-04-29
> **PurposeOfReason said:**
> I've never used it before so we'll find out. Is there a flag I can put for ports to not prompt me for things and just install with the default options? I just want to go into dwm, run make and let it grab xorg and everything for me and not ask questions.

Perhaps you might want to check out the command "make config-recursive" or just use portmaster which recursively goes into the config menu before installation

---

### Post by PurposeOfReason on 2010-04-29
Thanks. Just feels weird coming from a gentoo background to how freebsd thinks.

---

### Post by Bachstelze on 2010-04-30
> **PurposeOfReason said:**
> Getting to the network screen (doing a ftp install), I use dhcp which fills in all by the hostname and domain. I put whatever in as they shouldn't really be important but when I hit enter it says it cannot resolve hostname '<ftp site>'. Windows and linux both connect fine.

It's a known bug in sysinstall. Some people reported that answering "yes" to "Try IPv6 configuration?" fixed it for them (even if they don't have IPv6), but it didn't work for me either. What I do is that I just install the base and kernels dist from the CD, and then install the others after rebooting in the installed system.

---

