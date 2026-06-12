---
title: "ETHOS (ubuntu 14.04 based) ethernet adapter driver install problems RTL8111 RTL8168"
date: 2018-04-18
forum: Ubuntu/Debian BASED
---

### Post by daniloadur on 2018-04-18
Hi Friends, 

I have a motherboard with onboard RTL8111 / RTL8168 ethernet controller, it is used for ethereum mining and OS is ubuntu based called ETHOS. Ubuntu versionis 14.04 and kernel is 4.

When I boot the OS the network adapter is not being recognized by OS that is loading RTL8169 driver.

I take a look on this thread: [https://ubuntuforums.org/showthread.php?t=1022411](https://ubuntuforums.org/showthread.php?t=1022411) and tried to fix the issue but with no positive result.

I´m trying to use the latest driver 8.045: [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Conn=4&DownTypeID=3&Langid=1&Level=5&PFid=5&PNid=13#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Conn=4&DownTypeID=3&Langid=1&Level=5&PFid=5&PNid=13#2)

When making clean modules and install system is returning errors

Would be possible someone with more experice on this help me? (let me pay you a coffe).

Cheers

---

### Post by wildmanne39 on 2018-04-18
*Thread moved to **Ubuntu/Debian BASED for a more appropriate fit**.*

---

### Post by daniloadur on 2018-04-19
[ATTACH=CONFIG]279355[/ATTACH]

This is the condition, ethernet controller  is different than driver loaded.

---

### Post by praseodym on 2018-04-19
Just run
```

sudo apt-get install r8168-dkms dkms build-essential
```

---

