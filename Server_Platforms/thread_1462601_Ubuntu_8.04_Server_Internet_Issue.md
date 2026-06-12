---
title: "Ubuntu 8.04 Server Internet Issue"
date: 2010-04-25
forum: Server Platforms
---

### Post by axellerate on 2010-04-25
Alright, basically decided to make a pentium 4 useful, and I installed the server on it. Long story short, my only access to internet on it is a trendnet USB wifi stick. Alright, so I did reading and Ive basically found that I need ndiswrapper installed. So I got the 3 required drivers, put them on a usb and thats where I am now.


What do I do?

---

### Post by tgalati4 on 2010-04-26
man ndiswrapper

sudo ndiswrapper -l

---

### Post by cariboo on 2010-04-26
Have a look [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for an ndiswrapper howto.

---

