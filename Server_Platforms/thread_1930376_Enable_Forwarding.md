---
title: "Enable Forwarding"
date: 2012-02-23
forum: Server Platforms
---

### Post by Desann243 on 2012-02-23
How do i enable forwarding of information from network card to network card?

---

### Post by kevinthecomputerguy on 2012-02-23
edit the file /etc/sysctl.conf

add or un-comment the following line

net.ipv4.ip_forward=1


save and reboot

here is a screen shot. [http://woodel.com/page5_files/p5_image074.jpg](http://woodel.com/page5_files/p5_image074.jpg)
-Kev

---

