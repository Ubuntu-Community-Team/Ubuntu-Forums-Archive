---
title: "Access to Dl-Link 1210-28ME"
date: 2018-10-18
forum: Ubuntu Development Version
---

### Post by imorphey on 2018-10-18
After updating on ubuntu 18.10 can't access to D-link switches (1210-28ME) via telnet or web. Telnet saying "connection refused". Other D-link switches accessible via telnet or web.  How can I solve this problem, it's very important!

---

### Post by dino99 on 2018-10-18
Are you using a recent kernel ?  Need to know if that hardware is well listed by lshw and matching with journalctl output.
Also be sure about the connection' s cords; maybe test with those on the other working switches.

---

### Post by imorphey on 2018-10-18
Yes, I'm using recent kernel. Hardware is well listed. Cord is also good. The problem causes only with D-Link 120-28/ME. Other switches(Cisco, Quidway, D-link) works fine. Can't access only D-link 1210-28/ME.

---

### Post by dino99 on 2018-10-18
If you are using a 4.18 kernel for example, and journalctl does list warning/error about that hardware, then apparmor is a possible restriction (might be logged too) or the bios/uefi settings need some tweaks.
Do that switche have its own closed driver and/or its own bios ?

[https://support.dlink.com/list.aspx?type=1&model=1210-28me](https://support.dlink.com/list.aspx?type=1&model=1210-28me)

---

### Post by imorphey on 2018-10-21
> **dino99 said:**
> If you are using a 4.18 kernel for example, and journalctl does list warning/error about that hardware, then apparmor is a possible restriction (might be logged too) or the bios/uefi settings need some tweaks.
Do that switche have its own closed driver and/or its own bios ?

[https://support.dlink.com/list.aspx?type=1&model=1210-28me](https://support.dlink.com/list.aspx?type=1&model=1210-28me)

It doesn't depend on switch firmware and it doesn't need special driver. It's accessible through telnet doesn't work. I haven't found any restriction in apparmor. Tried clean ubuntu 18.10 from liveCD, it has the same problem. Can't access D-Link 1210-28/ME via telnet other D-Link switches works fine. I have no errors about hardware on my PC.

---

### Post by dino99 on 2018-10-21
then open a bug report for devs knowing about that issue. You can also ask devs via askubuntu to get quicker answer

---

### Post by imorphey on 2018-10-21
Thanks for help

---

