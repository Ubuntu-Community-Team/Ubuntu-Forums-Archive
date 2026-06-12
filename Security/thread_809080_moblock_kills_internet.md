---
title: "moblock kills internet"
date: 2008-05-27
forum: Security
---

### Post by demonskier on 2008-05-27
I'm not sure how or why or what to do but anytime I try and use moblock (with mobloquer as well) Firefox is unable to get to any website.  I've even tried to allow http and https connections (a few of the options) but to no avail

---

### Post by jre on 2008-05-28
Edit your /etc/default/moblock:
```
gksudo gedit /etc/default/moblock
```

You need the following entries:
```
WHITE_TCP_OUT="http https"
WHITE_IP_IN="YOUR_LAN/24"
WHITE_IP_OUT="YOUR_LAN/24"
```

Replace YOUR_LAN/24 with your LAN/subnet mask:

If you don't know your local IP check it with "sudo ifconfig". It's the value after  "inet addr:" of the interface that you use for networking. For wired connections that might be "eth0", for wireless connections "wlan0".

Example: You found out that your IP is 192.168.0.39. Then your LAN will most probably cover the IP range 192.168.0.1-192.168.0.255. Then whitelist this range with the following value:
  192.168.0.0/24

---

### Post by demonskier on 2008-05-29
hey thanks a lot that fixed it

---

### Post by rzrgenesys187 on 2008-06-27
Thanks worked great for me as well

---

### Post by rasungod_7 on 2009-11-05
Thank you that worked

---

