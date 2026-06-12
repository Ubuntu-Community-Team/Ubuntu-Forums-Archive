---
title: "How do I change the default folder for publically viewable html documents"
date: 2017-07-24
forum: Server Platforms
---

### Post by jaytelford on 2017-07-24
Hi, I don't know if this has anything to do with the fact that my service provider is still running on Ubuntu 15.10 (have no actual user experience with the later builds) but the folder that houses publically available html documents is located at: ```
../../../var/www/html
```.  This is okay for the most part but it makes life more difficult when uploading directly from Dreamweaver.

Consequently, I would like to change the folder that houses publically available html documents to ```
/home/httpdocs/public_html
```.  How can I direct all web traffic to this directory rather than ```
../../../var/www/html
```?

---

### Post by mastablasta on 2017-07-25
/home is folder from user not a public one. having docs in /var/www is normal and common practice.

they really should upgrade the server to 16.04.

also regarding Apache web server: [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

---

