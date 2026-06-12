---
title: "Tunnel Apache Around Firewall"
date: 2010-08-02
forum: Server Platforms
---

### Post by paragonconcept on 2010-08-02
I'm traveling, and i need to make some stuff on my local web server available to folks at the office. However, the network im on here doesn't allow port forwarding, so i can open up for 80. 

I have  Ubuntu 9.10 on my Laptop, and on a Server back at my home office. I'd like to forward tunnel it through SSH. I've been using the following command with no luck. 

> ssh -N -f -R 8000:localhost:80 [email]username@homeoffice.no-ip.org[/email]

---

### Post by paragonconcept on 2010-08-02
So i'm using 

> sudo ssh -R 8001:localhost:80 [email]user@mydomain.no-ip.org[/email]

when i  then ssh into my home box - i can use lynx to navogate to the site on my laptop, however, i cant seem to access it @ [http://mydomain.no-ip.org:8001](http://mydomain.no-ip.org:8001)

---

### Post by cdenley on 2010-08-02
First, you need to configure sshd to allow ssh to bind to external interfaces for port forwards.

/etc/ssh/sshd_config
```

GatewayPorts clientspecified

```

Then, when connecting, you need to specify a bind address, or leave it blank to bind to all interfaces.
```

sudo ssh -R **[COLOR="Red"]:[/COLOR]**8001:localhost:80 user@mydomain.no-ip.org  

```

---

