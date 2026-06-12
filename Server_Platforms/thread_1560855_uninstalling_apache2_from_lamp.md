---
title: "uninstalling apache2 from lamp"
date: 2010-08-25
forum: Server Platforms
---

### Post by chippanfat on 2010-08-25
Hello everyone, yet another problem again !

Basically I've made a right **** up of my apache2 configuration and I just want to un-install apache2 and re-install so I can start again.

I've done research on this but the guides have always been for people installing using "apt-get" or "rpm" packages. I've tried these methods but nothing has worked.

The way I installed lamp was from selecting it in the different options when installing ubuntu-server from disk.

Is there any way I can do this through the terminal and not through synaptic, only reason being is that I'm ssh'ing across a local network.

Cheers Guys :)

---

### Post by stlsaint on 2010-08-25
have you tried:

```
sudo aptitude purge apache2
```

or

```
sudo aptitude autoremove apache2
```

If so what errors are you getting that is not making them work?

---

### Post by arubislander on 2010-08-25
> **chippanfat said:**
> I've done research on this but the guides have always been for people installing using "apt-get" or "rpm" packages. I've tried these methods but nothing has worked.

I think you mean "deb" and "rpm" packages. The reason the guides probably did not work is that you were only uninstalling the packages, not the configuration files.

Try this in a terminal```
~$ sudo apt-get --purge autoremove apache2
```

This will remove apache2 and all the dependencies automatically installed with it, including each and every configuration file associated with these packages that isn't in your /home directory.

---

