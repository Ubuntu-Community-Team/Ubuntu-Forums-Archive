---
title: "Is it possible to request a 'certificate' to remote users?"
date: 2009-02-11
forum: Security
---

### Post by ruipedroca on 2009-02-11
Hi,

Is it possible to configure a server to request a 'certificate' to remote users (webmail, samba, http)?

I have a site wich I wanted to grant access only to people in my house and my office. 
In both locations I have a draytek router which has the ability import a certificates (x.509 and others). 

I would prefer the certificate to be installed in the router and not in the browser because of security: (in the browser, users could eventually copy it to an usb pen; the router is password protected)

Regards,

---

### Post by ruipedroca on 2009-02-12
Come on guys, shed some light in here, please! I'm a newbye in this matter!

Regards,

---

### Post by Dr Small on 2009-02-12
> **ruipedroca said:**
> Come on guys, shed some light in here, please! I'm a newbye in this matter!

Regards,
I am too, that's why I am just watching your thread ;)

---

### Post by e1mer on 2009-02-12
It actually is more appropriate to the router, you can just drop any
connection to your host that does not come from your subnet.

If your router is open, then you could add a rule for each host that
is allowed to connect to the server.

Finally, if you are so inclined, you can use iptables to only accept
connections from your network.

look over the iptables man page and see if that is where
you are trying to get.

---

### Post by ruipedroca on 2009-02-19
Any mores ideas?

---

