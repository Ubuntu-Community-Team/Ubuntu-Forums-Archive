---
title: "UPnP packages in ubuntu 12.04"
date: 2013-08-08
forum: Security
---

### Post by jsvidyad on 2013-08-08
Hello,

   I use ubuntu 12.04. I know that from a security point of view, it is a bad idea to enable UPnP on a router. But, it seems some UPnP related packages are installed on my system. I don't know how they got there as I definitely did not install them.
Running the command 
dpkg -l | grep -i upnp
on my system gives the output:

ii  libgupnp-1.0-4                               0.18.1-2                                         GObject-based library for UPnP
ii  libgupnp-igd-1.0-4                           0.2.1-2                                          library to handle UPnP IGD port mapping
ii  libminiupnpc8                                1.6-3ubuntu1                                     UPnP IGD client lightweight library
ii  libupnp3                                     1:1.6.6-5.1ubuntu0.12.04.1                       Portable SDK for UPnP Devices, version 1.6 (shared libraries)

Why are these packages there on my system? Are any of the above four UPnP related packages present on my ubuntu 12.04 system a security threat to my ubuntu 12.04 system?

---

### Post by Cheesemill on 2013-08-08
Those packages are almost certainly dependencies of programs that can ask for a UPnP request. This is nothing to worry about as you have switched off the UPnP capability of your router.

You can find out why these packages are on your system using the following command...
```
apt-cache rdepends libgupnp
```

---

### Post by jsvidyad on 2013-08-09
So, the presence of any of those four UPnP related packages is not a security threat for my ubuntu 12.04 system?

---

### Post by jsvidyad on 2013-08-14
Can someone please help me here?

---

### Post by cariboo on 2013-08-15
Did you run the command that Cheesemill gave you, and what were the results, we can't help, if we don't know what packages you installed that added the Upnp libraries.

---

### Post by MrSteve on 2013-08-17
i have just done a check and have the same UPnP files on my 12.04.2 system but have disabled UPnP on the router 

i believe that the UPnP files are installed by default as using 'apt-cache rdepends libgupnp' brings back no installed packages
but this result could be due to me emptying the cache on a regular basis 

i have also checked un-installing the files in synaptic but find many other programs would have to be un-installed with these files
as UPnP is disabled on the router i don't believe they are a security issue for the system ...

---

