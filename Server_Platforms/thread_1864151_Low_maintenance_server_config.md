---
title: "Low maintenance server config"
date: 2011-10-18
forum: Server Platforms
---

### Post by Rob_H on 2011-10-18
I'm setting up a workgroup server for a friend's small business. Just doing basic file serving and backup tasks. I want to make it as "hands-off" as possible including automatically installing security patches and the like. How can I set up Ubuntu Server to do this? Also, any other routine maintenance tasks that I should consider automating?

---

### Post by karlson on 2011-10-18
> **Rob_H said:**
> I'm setting up a workgroup server for a friend's small business. Just doing basic file serving and backup tasks. I want to make it as "hands-off" as possible including automatically installing security patches and the like. How can I set up Ubuntu Server to do this? Also, any other routine maintenance tasks that I should consider automating?

Installation of security updates or any other kinds of updates should not be done automatically.  If you need to reboot the server for updates to Kernel or OpenSSL you want to keep an eye on the server because if this blows up you want to find out right then and there rather then tomorrow of Monday morning when everything is down.

User creation/lock/deletion can certainly be automated.  Beyond that I can't think of anything.

---

### Post by collisionystm on 2011-10-18
> **Rob_H said:**
> I'm setting up a workgroup server for a friend's small business. Just doing basic file serving and backup tasks. I want to make it as "hands-off" as possible including automatically installing security patches and the like. How can I set up Ubuntu Server to do this? Also, any other routine maintenance tasks that I should consider automating?

Use Zentyal. I tell that to everyone and everyone says, well hey thats not exactly what I am looking for! It is 10.04 Ubuntu sever with a web interface and lxde gui. It can be configured to do ANYTHING all with the click of a button. Not to mention it has the option to get paid support or training if your friend ever needs it in the future. You can manage the server with the zentyal cloud.
[https://cloud.zentyal.com/login/](https://cloud.zentyal.com/login/)

[www.zentyal.com](www.zentyal.com)

---

### Post by drdos2006 on 2011-10-18
zentyal 1+


regards

---

