---
title: "ubuntu web server tutorial"
date: 2010-03-16
forum: Server Platforms
---

### Post by nate8033 on 2010-03-16
could any one tell me to find a good lamp web server tutorial or a book. i want one that will tell me how to get it working over the internet not just a localhost.

---

### Post by dudumomo on 2010-03-16
It depends on what you are looking for, but i wrote an easy tutorial about LAMP on my self hosted blog: [www.freelydifferent.com](www.freelydifferent.com)

Check the part "Webserver"

Let me know if it answers some of your questions.

---

### Post by wojox on 2010-03-16
[ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

As far as working over the internet you need to set up port forwarding on your router.


Also you can also just ask us questions. We'd be more than glad to help you.

---

### Post by nate8033 on 2010-03-17
ok so i got my server to work on my local network. do i need to set a static ip and if so how d oi do this?

---

### Post by shizakapayou on 2010-03-17
On your local LAN, setting a static IP is done in /etc/network/interfaces - there should be something similar to 

```
auto eth0
iface bond0 inet dhcp
```

You'll want to make it
```
auto eth0
iface eth0 inet static
     address xxx.xxx.xxx.xxx
     netmask 255.255.255.0
     gateway yyy.yyy.yyy.yyy
```

Obviously make your addresses something that'll work with your existing address scheme, likely 192.168.1.x.  I always set static IP's on my server just so I know it'll always be there.  The DHCP server will usually keep giving devices the same address, but not always (especially if it's a consumer router that gets rebooted).

Note this doesn't do anything for making it available to the world - we can help there too.

---

