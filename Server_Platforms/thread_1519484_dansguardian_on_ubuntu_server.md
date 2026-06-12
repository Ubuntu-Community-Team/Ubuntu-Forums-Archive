---
title: "dansguardian on ubuntu server"
date: 2010-06-28
forum: Server Platforms
---

### Post by fabiomc on 2010-06-28
hi i have installed dansguardian 2.10.1.1 on ubuntu server 9.1.0 (with apt-get install dansguardian)
 
the daemon doesnt start automatically on reboot of server
 
i must launch it manually and it runs
 
what can i do?
 
thanks
Fabio

---

### Post by upbeat.linux on 2010-07-01
You'll want to add it to startup:

```
sudo update-rc.d dansguardian defaults
```

Check out the man page for [update-rc.d]("http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d"). Also worthwhile 

[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

