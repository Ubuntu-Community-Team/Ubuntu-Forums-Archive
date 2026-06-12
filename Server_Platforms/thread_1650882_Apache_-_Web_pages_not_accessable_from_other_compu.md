---
title: "Apache - Web pages not accessable from other computers on LAN"
date: 2010-12-22
forum: Server Platforms
---

### Post by Guruprasad on 2010-12-22
I have two computers. I have installed Apache on one of them. I can access webpages from local computer ([http://localhost/bc](http://localhost/bc)). But I can not access them from other computer on network.

Computer A (192.168.100.9) with Apache is connected to internet. It shares the internet with computer B (192.168.100.5) on network. Default gateway for computer B is 192.168.100.9 . I am trying to access the webpages from computer B ([http://192.168.100.9/bc](http://192.168.100.9/bc)) but can not connect.

---

### Post by arrrghhh on 2010-12-22
Does computer B have any issues accessing the internet thru that shared connection you have...?  Also, can you ping computer A/the gateway from computer B?

Might also be good to check firewall rules - if you have UFW enabled, you'll need to allow port 80 to that IP.  I allow all local traffic to my server, you may or may not want to do that... It is a security loophole if a lot of people get on your LAN.

---

### Post by CharlesA on 2010-12-22
First thing I would check would be firewall rules.

Also post the output of this, when run from the machine running apache:

```
ifconfig
```

---

### Post by Guruprasad on 2010-12-22
Thank you very much...

Computer B can access internet.

The problem was with firewall rules. I allowed port 80 for just 192.168.100.5

---

### Post by arrrghhh on 2010-12-22
> **Guruprasad said:**
> The problem was with firewall rules. I allowed port 80 for just 192.168.100.5

Glad to hear it :D

---

