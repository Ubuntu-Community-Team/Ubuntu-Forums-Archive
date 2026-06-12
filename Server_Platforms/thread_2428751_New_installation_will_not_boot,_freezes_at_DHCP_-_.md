---
title: "New installation will not boot, freezes at DHCP - Ubuntu 18.04.3 LTS"
date: 2019-10-08
forum: Server Platforms
---

### Post by woolyguy on 2019-10-08
Sorry for the beginner question.  So I just did a fresh install of Ubuntu 18.04.3 LTS.  When I try and start  the OS, it never boots up.  It hangs at loading DHCP.  I don't know  why.  I know the hardware works, because my buddy already installed 18.04.3 LTS on the same comp and gave it to me.   It was wiped clean, and now I  am installing it fresh myself.  The only difference is that my install  was at my house on my network, BTW the comp is hardwired to my router.

**I wonder if this is the problem:**


The Ubuntu Tutorial shows this:
[IMG]https://i.imgur.com/1fu5soK.png[/IMG]





However, during my install, this is my actual option:
[img]https://i.imgur.com/AKRsNO0.png[/img]



Do I just have to change the address?  Is that the problem?

---

### Post by Skaperen on 2019-10-08
it seems you do have ethernet but your computer isn't getting any answers on it.  maybe that is the wrong type of cable.  do you have an ethernet hub or switch and a 2nd cable?

---

### Post by woolyguy on 2019-10-09
> **Skaperen said:**
> it seems you do have ethernet but your computer isn't getting any answers on it.  maybe that is the wrong type of cable.  do you have an ethernet hub or switch and a 2nd cable?

Thanks for the reply.  I swapped cables just to check, and it's not that.  I plugged directly into my router too, no extra access point or switch in between.  The comp is a Lenovo ThinkCentre M72e, mobo is LEVONO MAHOBAY 0B98405 STD.  This machine was used by a large company recently, and then they replaced all their machines so the old ones were given away to employees, so I know the machine works well.  It also was working well when my friend gave it to me.  I really doubt it is the hardware, but then again, I don't know what is wrong.

---

### Post by woolyguy on 2019-10-11
Anyone else have any idea how I can get my install right.  I am brand new to Ubuntu, and I have not even gotten the installation finished.

---

### Post by Bashing-om on 2019-10-11
woolyguy; Hello; Welcome to the forum.

A thought - bad install medium?

Did you verify the download of the .iso ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you verify the copy ?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

And as a check when booting the installer to "Try Ubuntu" mode;
Does networking work here ?
what shows:
```

ip link ls
ls /sys/class/net
ip route show

```

Let's see here if you can talk to the router.

[INDENT]gots to be a reason
[/INDENT]

---

