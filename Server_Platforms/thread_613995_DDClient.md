---
title: "DDClient"
date: 2007-11-15
forum: Server Platforms
---

### Post by mattc908 on 2007-11-15
Hey basically I use  DYNDNS.org to help my hosting problems, only problem is DDClient use's my local IP 192.168.1.103 as its host I have to manually go in an change that........Any way I can make it so it broadcasts the actull server IP so other can access it.

---

### Post by mattc908 on 2007-11-17
Bump

---

### Post by mattc908 on 2007-11-18
Bump

---

### Post by Zeosa on 2007-11-18
What router are you using....?


You can either get the ip from the router itself by changing the 'use' statement in the ddclient.conf

to get the ip from the router you need to know which page in the routers configuration shows the external ip...
```

use=fw, fw=http://router.ip.address/page/with/ip, fw-login=username, fw-password=routerpassword, fw-skip='text'

```

Replace username with your router username, replace fw-password with your router password replace 'text' with the text on the page which comes directly before the ip address on the page ....For instance, my router shows "PPP    xxx.xxx.xxx.xxx" ...so I'll have fw-skip='PPP'


The second way of doing it is to not get the IP from the router at all, but use an external site such as checkip.dyndns.org....the statement would go like this:

```

use=web, web=checkip.dyndns.org/, web-skip='IP Address'

```

After modifying the configuration, test with 'ddclient -daemon 0 -debug' to see what (if anything it'll report) to dyndns.

---

### Post by mattc908 on 2007-11-20
What is the config file for DDClient under? /home/username/?

---

### Post by Gouki on 2007-11-20
> **mattc908 said:**
> What is the config file for DDClient under? /home/username/?

/etc/ddclient.conf

---

### Post by kinemagician on 2007-11-20
It works!!!!
Thank you!:):)

---

### Post by mattc908 on 2007-11-22
Yes works perfectly thank you.

---

