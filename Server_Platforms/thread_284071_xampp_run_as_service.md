---
title: "xampp run as service?"
date: 2006-10-25
forum: Server Platforms
---

### Post by LoclynGrey on 2006-10-25
I'm not running a external website, instead i'm using xampp to run some development websites and a crm system on my work laptop.
I've used xampp in the past on webservers that never get turned off, however my laptop gets shut down daily.

Anyone have any insight on how to run xampp as a system service under dapper or know how to auto run this command @ start up?

sudo /opt/lampp/lampp start

<<of which i need to then input my password>>

Thanks in advance

---

### Post by hockalees on 2006-10-27
Look at Secion #3, step 3 on this page:

[http://www.apachefriends.org/en/faq-xampp-linux.html](http://www.apachefriends.org/en/faq-xampp-linux.html)

For ubuntu, the directory is rc2.d

---

