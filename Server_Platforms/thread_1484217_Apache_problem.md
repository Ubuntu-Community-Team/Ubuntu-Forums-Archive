---
title: "Apache problem"
date: 2010-05-15
forum: Server Platforms
---

### Post by BreatheInMyVoid on 2010-05-15
I have installed LAMP using "sudo tasksel install lamp-server". localhost said to me that It Works. I have created my Virtual host and tried to restart apache. It wrote to me [Fail]. I have trying to check status of apache using "sudo /etc/init.d/apache2 status" but it tells to me that Apache is NOT running:shock:. But lolcalhost works. Whats wrong?

---

### Post by NullHead on 2010-05-15
Sounds like your virtual host is misconfigured. Double check the config where you setup the virtual host and restart apache again.

---

