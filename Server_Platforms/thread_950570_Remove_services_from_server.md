---
title: "Remove services from server"
date: 2008-10-17
forum: Server Platforms
---

### Post by devonps on 2008-10-17
Hi,

I have an Ubuntu 8.04 server currently running a LAMP installation and an email server.

I wish to remove the AMP services and leave only the email server running, after some googling I found the following:

```
#apt-get remove --purge package
#apt-get clean
```

Would people recommend the above commands?

Thanks in advance.
Steve.

---

### Post by sisco311 on 2008-10-17
the above command will uninstall the package.
it's save and you can reinstall the package later with:
```
sudo apt-get install *package*
```
(replace the *package* with the name of the package)

if you don't want uninstall the package, just turn off
the service permanently, then try:
```
sudo update-rc.d -f *service-name* remove
```

to start/stop/restart the service:
```
sudo invoke-rc.d *service-name* start
sudo invoke-rc.d *service-name* stop
sudo invoke-rc.d *service-name* restart
```

to turn it back on  permanently:
```
sudo update-rc.d -f *service-name* defaults
```

---

### Post by cdenley on 2008-10-17
I believe if you want to remove the LAMP packages, you can uncheck it in this menu
```

sudo tasksel

```

---

