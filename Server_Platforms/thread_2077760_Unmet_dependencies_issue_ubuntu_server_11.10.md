---
title: "Unmet dependencies issue ubuntu server 11.10"
date: 2012-10-29
forum: Server Platforms
---

### Post by infiniteoddity on 2012-10-29
Im running Server 11.10
I currently have an issue where I can not install anything without getting the following error
Unmet dependencies. Try 'apt-get -f install' with no packages

However when I do run the apt-get install -f
It attempts to install the missing dependencies for linux-image-3.0.0-26-server and comes up with the following error

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-26-server_3.0.0-26.43_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now on doing a further investigation my /boot is also full (which I assume is why I cant installlinux-image-3.0.0-26-server)  however I can not remove old packages due to the issue above. 

Also after doing a uname -r I get 3.0.0-25-server

Does anyone have any suggestions?

---

### Post by drmrgd on 2012-10-29
If you run:

```
sudo apt-get autoremove
```

Does it ask to remove the old Kernel versions?  If not, then you might have a look at this to remove them manually:

Note:  I've not completely read or followed this in the past!
[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)
[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

---

### Post by dniMretsaM on 2012-10-29
If you have old packages (that you're sure you can safely remove), I believe you can remove them with dpkg like so:
```
dpkc --remove [pkgname]
```

---

### Post by infiniteoddity on 2012-10-29
Thanks for the assist guys.
This worked perfectly:
```
dpkg --remove
``` 
I was then able to clear enough space on the /boot to allow for the apt-get install -f to work

---

