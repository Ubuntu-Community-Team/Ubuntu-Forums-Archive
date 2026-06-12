---
title: "Pureftpd-mysql on mutiple ports"
date: 2020-09-11
forum: Server Platforms
---

### Post by math492m on 2020-09-11
hi im running Ubuntu server 18.04
My firewall is ufw and is open on the ports i need and want 

and the problem im having is that i dont know how to have pureftpd listen on multiple ports

can anyone help please

---

### Post by darkod on 2020-09-11
I don't understand. You don't need pureftpd to listen on multiple ports.

But what you do need is to set up pasive port range and passive IP when you use it behind a firewall. You have instructions here how to do it:
[https://www.faqforge.com/linux/controlpanels/ispconfig3/how-to-set-the-passiveportrange-in-pure-ftpd-on-denian-and-ubuntu-linux/](https://www.faqforge.com/linux/controlpanels/ispconfig3/how-to-set-the-passiveportrange-in-pure-ftpd-on-denian-and-ubuntu-linux/)

In general I would try to avoid using FTP. It is very unsecure. Use SFTP or SCP instead. In such case you also have less firewall problems because they run over the standard SSH port.

---

