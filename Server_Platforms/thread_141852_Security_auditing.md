---
title: "Security auditing"
date: 2006-03-09
forum: Server Platforms
---

### Post by bailey_ca on 2006-03-09
Just out of curiosity, is there an equivalent of [msec]("http://mandriva.vmlinuz.ca/index.php/SysAdmin/Security/msec") for Ubuntu? I'm specifically interested in the permissions checks it runs, eg, making sure that nothing in /etc is world-readable.

---

### Post by mlind on 2006-03-09
I'm actually interested this myself too. Nessus looks like some sort of security
audition framework, but I haven't tried it out yet.

---

### Post by bailey_ca on 2006-03-10
I'll admit, I haven't spent that much time on the Nessus site, but it strikes me as more remote-based. I.e., it's checking if libbuggy-dev is actually buggy. Though I like the sounds of Nessus as well, I still need a local permissions checker.

With msec, I could easily control local file permissions. For example, if I decided all folders under /home were 700, except for /home/shared at 775, and everything under /etc was 750, I could do so, even if my users tried otherwise.

Ubuntu server is lacking this ability. The sheer number of world-readable stuff in /etc bugs me. (Yes, I know I could change it myself. I don't want to!)

I would love to see the server installation offer some sort of local security checks.

---

### Post by mlind on 2006-03-10
well, it looks like there's already effort for porting msec
to ubuntu [https://wiki.ubuntu.com/SecurityLevels](https://wiki.ubuntu.com/SecurityLevels)

---

