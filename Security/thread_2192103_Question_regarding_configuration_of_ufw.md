---
title: "Question regarding configuration of ufw"
date: 2013-12-05
forum: Security
---

### Post by linuxyogi on 2013-12-05
Hi,  I have installed gufw and enabled it. I see that by default gufw sets all incoming traffic to deny but in this video  [https://www.youtube.com/watch?v=zp0tg6popQ0](https://www.youtube.com/watch?v=zp0tg6popQ0)  the guy is adding all these rules for incoming traffic.  Is this necessary ?

---

### Post by sammiev on 2013-12-05
I have set incoming and out going to Deny but add rules for out going only. This [thread]("http://ubuntuforums.org/showthread.php?t=1876124") should help you a lot. :)

---

### Post by bashiergui on 2013-12-06
No. You only need to open ports if you have services running that need to accept incoming connections. If you don't have any services (and if you don't know if you have any services), then you don't need any rules for incoming traffic except for "deny".

---

