---
title: "Locking Down Apache &amp; MySQL"
date: 2008-07-07
forum: Security
---

### Post by oxsyn on 2008-07-07
Just installed Apache & MySQL on my laptop.  Using them for local apps only.  Is there a way (I'm 100% sure there is, i just don't know how) to lock them down, so they'll only respond to local queries?

---

### Post by brian_p on 2008-07-07
> **F4RR4R said:**
> Just installed Apache & MySQL on my laptop.  Using them for local apps only.  Is there a way (I'm 100% sure there is, i just don't know how) to lock them down, so they'll only respond to local queries?

I'm almost sure mysql only listens on localhost by default so that's that taken care of. Check the config file in /etc to be sure.

Apache probably listens on all interfaces but can be configured with the Listen directive to listen to only specific IP addresses.

---

### Post by cdenley on 2008-07-07
For mysql, make sure you have a line like this in /etc/mysql/my.cnf in the "mysqld" section. (this is the default)
```

bind-address = 127.0.0.1

```

For Apache, edit /etc/apache2/ports.conf
```

Listen 127.0.0.1:80

<IfModule mod_ssl.c>
    Listen 127.0.0.1:443
</IfModule>

```

After you restart the servers, you will see from this output that you are only listening for connections on the local loopback device.
```

netstat -tnl

```

---

### Post by hyper_ch on 2008-07-08
or if you are behind a router and you trust your lan, then just don't forward the according ports from the router to your box.

---

