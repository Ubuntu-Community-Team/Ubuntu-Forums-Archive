---
title: "NEWB server installation questions."
date: 2008-07-29
forum: Server Platforms
---

### Post by brad8266 on 2008-07-29
I will be deploying a Ubuntu server for a client that has an office with around 5 desktop machines running Windows OS. Currently they are all setup in a workgroup in order for all the machines to share files.

The objective is to have centralized file sharing between all the computers and that is basically all that needs to be done. The idea is that everyone can share files such as Quick Book records. The client has internet access for the desktops via a regular router connected to a cable modem so IP addressing is already taken care of. All I need is to have samba running and we will probably also setup the server as a print server also. Raid will also be implemented.

Can you guys give me any tips or suggestions on the best way to go about this. This is my first Linux Server deployment although i have worked with enterprise Linux in the past and used it as a samba server. I appreciate any insight.

---

### Post by tuxxy on 2008-07-29
You could try the documentation,

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by brad8266 on 2008-07-29
> **tuxxy said:**
> You could try the documentation,

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Yes I've read through most of it already. I just wanted to hear from actual people that are running it.

---

### Post by cariboo on 2008-07-30
Here is another good link:

[http://us1.samba.org/samba/docs/man/Samba-Guide/](http://us1.samba.org/samba/docs/man/Samba-Guide/)

Jim

---

### Post by jonabyte on 2008-07-30
I am running it...pm me if you want.

---

### Post by ChumleyEX on 2008-07-30
dude look up webmin, it's a webpage wizard. Makes life easier, and you can tunnel into the computer remotely (ssh) and pull it up to make changes.

---

