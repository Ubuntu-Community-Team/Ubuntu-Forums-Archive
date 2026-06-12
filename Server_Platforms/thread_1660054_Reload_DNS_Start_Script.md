---
title: "Reload DNS Start Script"
date: 2011-01-04
forum: Server Platforms
---

### Post by unemployment on 2011-01-04
One of my developers set up my server.  My site just went down and he is telling me to reload the dsn start script.  Any ideas how to do this using putty via ssh?

---

### Post by James78 on 2011-01-04
Reload DNS start script? Maybe he meant reload the DNS server. In which case you could do something like:
```
sudo service bind9 restart
```

---

### Post by unemployment on 2011-01-05
> **James78 said:**
> Reload DNS start script? Maybe he meant reload the DNS server. In which case you could do something like:
```
sudo service bind9 restart
```

I tried your suggestions and get this error.

rndc: connect failed 127.0.0.1#953: connection refused
-bash aquota.group: command not found

---

### Post by James78 on 2011-01-05
There's an error in your configuration. You should talk to your developer about that. Tell him to make sure rdnc is setup, and is setup correctly. As for aquota.group, that's completely unrelated, but you should refer that to him as well.

---

