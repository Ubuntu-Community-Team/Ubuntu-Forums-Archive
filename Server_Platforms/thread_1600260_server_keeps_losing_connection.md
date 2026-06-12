---
title: "server keeps losing connection"
date: 2010-10-18
forum: Server Platforms
---

### Post by cbarron on 2010-10-18
So i have my server running and now it will randomly loose its internet connection I can not put my finger on why or what is causing it to "shut off" the internet connection......I am using Ubuntu Server 10.04

Any thoughts or ideas would be great

Thanks,
Chris

---

### Post by oregonbob on 2010-10-18
Look at /var/log/messages and other recent log files for a possible reason. Is it wireless?

---

### Post by cbarron on 2010-10-18
no it is a wired connection.........and thanks for the first lead i will look at those....anything particular i should look for?

---

### Post by HermanAB on 2010-10-19
Howdy,

Are you perhaps running DHCP?  If dhclient connects to a badly configured DHCP server then that will explain it.

---

