---
title: "Cannot Start Kubuntu Desktop on Ubuntu Server"
date: 2010-09-20
forum: Server Platforms
---

### Post by jcole208 on 2010-09-20
I have Ubuntu Server running with Webmin, but I wanted a GUI to work with so I installed kubuntu-desktop.  I cannot get it to start.  

When I type *start kdm* I get the following error:

*Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory*

Can anyone help me?

---

### Post by CharlesA on 2010-09-20
Try this:

```
sudo service start kdm
```

---

