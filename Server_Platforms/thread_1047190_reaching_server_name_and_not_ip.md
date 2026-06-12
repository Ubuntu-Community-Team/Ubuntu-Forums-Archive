---
title: "reaching server name and not ip"
date: 2009-01-22
forum: Server Platforms
---

### Post by av76 on 2009-01-22
Hi all,

I have ubuntu running apache2, mysql and php that I want to be reachable via the server's name. For now it is working on m$ systems, but when I am trying the same thing on other ubuntu system I get an online server.

On m$ it looks like: [http://riser](http://riser)
And I see all my www content ... how to do this on ubuntu?

Thanks,
A

---

### Post by volkswagner on 2009-01-22
If riser is the host name of your server, add it along with the internal ip to your /etc/hosts file.  You do this on the client machines.  It also will allow you to ssh into the server with the host name.

---

### Post by av76 on 2009-01-22
I added: 127.0.0.1 riser to the file and now it looks like:

127.0.0.1 localhost
127.0.0.1 riser

but it still does not work. My ubuntu app server is getting an automated ip address and I thnk I need to set it to a static one. Did it before, but it is bugy ... it disables my other network connections if it is static.

Any ideas?

---

### Post by cdenley on 2009-01-22
If windows computers are resolving the computer name "riser" to an IP, then you must be running samba on the web server. I think ubuntu can resolve the hostname using zeroconf if you install avahi on the server.
```

sudo apt-get install avahi-daemon

```
You could also install and configure winbind on each client so they can resolve netbios names. You could also take volkswagner's advice and configure the hosts file **on each CLIENT**, but that would require a static IP.

---

### Post by av76 on 2009-01-22
I have avahi and winbind installed :-)
I would really want to avoid setting a static ip address.

---

### Post by cdenley on 2009-01-22
> **av76 said:**
> I have avahi and winbind installed :-)
I would really want to avoid setting a static ip address.

Is it working? Did you install **and configure** winbind **on the clients**? Did you install avahi-daemon on the server? You only need avahi or winbind. Do you want to use a zeroconf hostname, or a netbios hostname?

---

### Post by av76 on 2009-01-22
> **cdenley said:**
> Is it working? Did you install **and configure** winbind **on the clients**? Did you install avahi-daemon on the server? You only need avahi or winbind. Do you want to use a zeroconf hostname, or a netbios hostname?

Since the app server is ubuntu and clients may differ (ms and lin) I think that it would e wise to use avahi (as said before ms can access via server's name).

I think that I understand the differences between zeroconf and netbios and I would choose zeroconf. How do I configure avahi on the server and on clients?

---

### Post by cdenley on 2009-01-22
I forgot that with zeroconf, you have to append ".local" to the hostname.
```

ping riser.local

```

---

### Post by av76 on 2009-01-22
> **cdenley said:**
> I forgot that with zeroconf, you have to append ".local" to the hostname.
```

ping riser.local

```

Cool that works!!!
I type [http://riser.local](http://riser.local) and I get what I want :-)

Many thanks,
A

P.S
What a relieve

---

### Post by Iowan on 2009-01-22
> **av76 said:**
> 127.0.0.1 localhost
127.0.0.1 riser
A moot poiint if you've already got it working, but it seems like "standard" configuration would be ```
127.0.0.1 localhost
127.0.1.1 riser.local riser
```

---

