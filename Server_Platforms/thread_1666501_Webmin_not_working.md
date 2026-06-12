---
title: "Webmin not working"
date: 2011-01-13
forum: Server Platforms
---

### Post by Nimbu on 2011-01-13
I have installed ubuntu server 10.04 on a virtualhost. I have installed webmin fine.
When I try to access the webpage from my web browser the webpage cant be displayed.
I have attached the output of ifconfig. Please help!

---

### Post by wongo888 on 2011-01-13
Are you running a bridged adapter?

[http://www.virtualbox.org/manual/ch06.html#id489067](http://www.virtualbox.org/manual/ch06.html#id489067)

In your Virtual Box VM machine menu (Devices | Network adapters...), ensure your network adapter is enabled and attached to: "bridged adapter", name "en0: ethernet". Under advanced, adapter type is greyed out as is MAC address and "cable connected" is checked.

---

### Post by sj1410 on 2011-01-14
are you able to ping you server. webmin default port is 10000

---

### Post by Nimbu on 2011-01-16
I think I had a problem when I set the local ip to a static one on my router. This was not properly configured on the server. However after I have fixed that issue when I try to connect to webmin it takes too long to respond. Any suggestions??? I am using https://

---

