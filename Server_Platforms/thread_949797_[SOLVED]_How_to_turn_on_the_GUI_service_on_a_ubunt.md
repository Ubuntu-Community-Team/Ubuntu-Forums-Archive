---
title: "[SOLVED] How to turn on the GUI service on a ubuntu server to make users login using"
date: 2008-10-16
forum: Server Platforms
---

### Post by Diana Rogger on 2008-10-16
Hi everybody,

3 or 4 months ago I downloaded and installed ubuntu desktop using the command: sudo apt-get install ubuntu-desktop or something like that.

Yesterday I was busy to disable or turn off unnecessary services on my ubuntu server. 

accidentally I select a service which is causing me to not see the GUI to log in anymore.

I also installed Webmin. When I turned of the service I was connected on an other computer using webmin.

Question:

Can anybody tell me how to start this service again using the terminal or using webmin?

Thank you in advanced,

Diana Rogger

---

### Post by lykwydchykyn on 2008-10-16
the terminal command is:
```

sudo invoke-rc.d gdm start

```

To turn it back on permanently when booting:
```

sudo update-rc.d -f gdm remove
sudo update-rc.d gdm start 99 2 3 4 5 . stop 20 1 .

```

---

### Post by Diana Rogger on 2008-10-16
Thank for your help.

It is working now.

Regards,

Diana Rogger

---

### Post by sisco311 on 2008-10-16
Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

