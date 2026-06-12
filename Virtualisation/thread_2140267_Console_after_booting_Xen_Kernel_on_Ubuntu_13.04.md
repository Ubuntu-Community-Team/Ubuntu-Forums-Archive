---
title: "Console after booting Xen Kernel on Ubuntu 13.04"
date: 2013-04-29
forum: Virtualisation
---

### Post by TurboBee on 2013-04-29
I installed Xen using the recommended procedure on Ubuntu's site using motherboard Supermicro X7SBL-LN2 and Ubuntu 13.04 amd64.  After the installing it and rebooting my console looks like this: [https://www.youtube.com/watch?v=-UbZt7Gix2Q](https://www.youtube.com/watch?v=-UbZt7Gix2Q) I've had this happen also with CentOS 6 as well.  Everything on the server works fine but the console is unusable.  If I switch back to the stock kernel it goes back to normal and I can use the console again but then I can't use Xen.  This is a fresh install of Ubuntu 13.04.  Any help troubleshooting this problem is appreciated.

Thanks!

---

### Post by TurboBee on 2013-08-06
I contacted Supermicro about the problem and they gave me a beta BIOS for the motherboard to try.  Surprisingly it actually fixed the problem.  Since the BIOS isn't posted on their site I'll just leave a link here to it in case anyone else is having this problem.  Use BIOS at your own risk as it is a beta BIOS.

[http://geo.animounted.net/X7SBL1.113.zip](http://geo.animounted.net/X7SBL1.113.zip)

---

