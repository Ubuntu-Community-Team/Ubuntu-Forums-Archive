---
title: "SELinux"
date: 2012-05-11
forum: Security
---

### Post by choppyfireballs on 2012-05-11
I currently have an active and working fileshare using samba i can successfully connect to the machine through any pc on the network that I need to. I need to install SELinux and I have been messing with this on a test computer to no avail does anyone have any ideas suggestions.

---

### Post by bodhi.zazen on 2012-05-11
Ubuntu uses apparmor. If you want selinux I highly suggest you use Fedora, RHEL, Centos, or Scientific.

Selinux support on Ubuntu is marginal at best.

What makes you think you need selinux for Samba ?

---

### Post by choppyfireballs on 2012-05-11
Thanks, and boss was mandating it.

---

### Post by bodhi.zazen on 2012-05-11
> **choppyfireballs said:**
> Thanks, and boss was mandating it.

Ah, well, the problem with selinux on Ubuntu is the selinux policies are not well maintained, you would have to debug them yourself.

If you want selinux, and this is a work environment, I highly advise RHEL, Centos, or Scientific.

If you want to use Ubuntu, use apparmor.

---

### Post by CharlesA on 2012-05-11
> **bodhi.zazen said:**
> Ah, well, the problem with selinux on Ubuntu is the selinux policies are not well maintained, you would have to debug them yourself.

If you want selinux, and this is a work environment, I highly advise RHEL, Centos, or Scientific.

If you want to use Ubuntu, use apparmor.
+1 to RH/CentOS for a work environment.

---

### Post by choppyfireballs on 2012-05-14
> **bodhi.zazen said:**
> Ah, well, the problem with selinux on Ubuntu is the selinux policies are not well maintained, you would have to debug them yourself.

If you want selinux, and this is a work environment, I highly advise RHEL, Centos, or Scientific.

If you want to use Ubuntu, use apparmor.


Ok thank you I will take it for a spin

I would assume sudo apt-get install apparmor not that i'm not going to try it in 30 seconds anyway lawl

---

### Post by CharlesA on 2012-05-14
> **choppyfireballs said:**
> Ok thank you I will take it for a spin

I would assume sudo apt-get install apparmor not that i'm not going to try it in 30 seconds anyway lawl
If you are going to go with Apparmor: Read this:
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by bodhi.zazen on 2012-05-14
> **choppyfireballs said:**
> Ok thank you I will take it for a spin

I would assume sudo apt-get install apparmor not that i'm not going to try it in 30 seconds anyway lawl

Apparmor is already installed.

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by choppyfireballs on 2012-05-15
> **bodhi.zazen said:**
> Apparmor is already installed.

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

I saw that.

---

