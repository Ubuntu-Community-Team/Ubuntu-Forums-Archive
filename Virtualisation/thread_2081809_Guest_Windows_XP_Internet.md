---
title: "Guest Windows XP Internet"
date: 2012-11-07
forum: Virtualisation
---

### Post by Joon Lee on 2012-11-07
My host computer (Xubuntu) is connected to the internet via an ethernet cable (no password needed). When I run my XP machine, through VirtualBox, I can't use the internet or any applications that require the internet. Fixes?

---

### Post by jerome1232 on 2012-11-07
Check what your network settings for the Machine are, Open virtualboxes main window, highlight the xp machine without opening it, right click it and click settings, in the left hand pane click network. Make sure the adapter is enabled and set to NAT (other settings may work, I use bridged)

Click advanced and make sure "cable is connected" is checked.

---

### Post by |{urse on 2012-11-07
Yep, switch it to bridged.

---

### Post by coldraven on 2012-11-07
For some good info about networking in Virtualbox  g[I]o here and click on the image of issue 61 to download it 
[http://fullcirclemagazine.org/issue-61/](http://fullcirclemagazine.org/issue-61/) 
Then read from page 15 [/I]onwards.

---

### Post by Joon Lee on 2012-11-11
Thank you all. I switched it from NAT to Bridged Adapter and it worked!

---

