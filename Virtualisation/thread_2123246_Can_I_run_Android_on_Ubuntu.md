---
title: "Can I run Android on Ubuntu"
date: 2013-03-07
forum: Virtualisation
---

### Post by dr-kart on 2013-03-07
I used either eee*.iso or latest 4.2 Android isos from [https://code.google.com/p/android-x86/downloads/list](https://code.google.com/p/android-x86/downloads/list) on virtualbox (ubuntu 12.10x64). No success yet. System reboots while virtual machine running :confused: (The same result with latest virtualbox.deb version from developer's site) Or should I change some parameters on VBox since I have Intel Ivy Bridge cpu and B75 chipset?

---

### Post by sanderj on 2013-03-07
Worth a try: [http://www.cnx-software.com/2013/03/01/how-to-run-android-apps-in-linux-with-androvm/](http://www.cnx-software.com/2013/03/01/how-to-run-android-apps-in-linux-with-androvm/)

---

### Post by ibjsb4 on 2013-03-07
x86-4.2 loaded on the second try.  First try was ext4, no good.  Second try was fat32 and it booted :)

[ATTACH=CONFIG]239870[/ATTACH]

---

### Post by dr-kart on 2013-03-08
> **sanderj said:**
> Worth a try: [http://www.cnx-software.com/2013/03/01/how-to-run-android-apps-in-linux-with-androvm/](http://www.cnx-software.com/2013/03/01/how-to-run-android-apps-in-linux-with-androvm/)

Thanks! It works!.

---

