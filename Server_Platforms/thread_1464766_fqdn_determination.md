---
title: "fqdn determination"
date: 2010-04-28
forum: Server Platforms
---

### Post by blakep2 on 2010-04-28
when i start apache this comes up

 Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I have the namevirtualhost set and my site configuration has the Servername, and VirtualHost as well.

---

### Post by wojox on 2010-04-28
Try:

```
sudo nano /etc/apache2/apache2.conf
```

And add:

ServerName "192.168.1.123" 

or whatever your ip address is.

---

### Post by cdenley on 2010-04-28
That is a harmless warning, but if it annoys you, run this command.
```

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

```

---

### Post by blakep2 on 2010-04-28
if i wanted to add a subdomain to this site would it recognize it.  My A record is my home's ip address.  My router is set to forward the 80 port to the local ip that is currently running the main site.  How would i configure the subdomain.

---

### Post by cdenley on 2010-04-28
> **blakep2 said:**
> if i wanted to add a subdomain to this site would it recognize it.  My A record is my home's ip address.  My router is set to forward the 80 port to the local ip that is currently running the main site.  How would i configure the subdomain.

That question is not related to this thread. You already have a thread for that topic, though the title isn't very descriptive.

---

