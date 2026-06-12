---
title: "The best security feature in Ubuntu: apt-get?"
date: 2008-03-24
forum: Security Discussions
---

### Post by phrostbyte on 2008-03-24
It occurred to me that the Debain package manager is not just a excellent way to manage software, it may very well be the biggest security enhancement in Ubuntu.

Systems seem to be comprised in one of the following ways:

(1) A evil piece of code is executed on the system
(2) A trusted program with a security hole is exploited

apt-get greatly helps with (1) and also enchances the protection against (2). When you install a program from the Ubuntu repositories, those are uploaded by trusted members of the community or Canonical employees, and peer reviewed to a certain extent, so the chances of malware leaking in are highly unlikely, especially compared to the completely wide open, non-accountable way Windows packages are distributed. And on top of this they are all signed as to ensure they have not been tampered with. This is HUGE for security. It almost removes (1) from the equasion.

(2) is helped because of the reliable update system apt-get offers, fixes to security vulnerabilities can be issued quickly. This is less likely if apt-get didn't exist. 

So I must conclude from a security standpoint, the most important things to Ubuntu:
apt-get > SELinux >= AppArmor > sudo

:popcorn:

---

### Post by erginemr on 2008-03-24
Well said bro. I am also fond of the Debian way of package handling. =D>

---

### Post by bhavi on 2008-03-24
> **erginemr said:**
> Well said bro. I am also fond of the Debian way of package handling. =D>
Yes its the most simplest of all the linux distros....

---

