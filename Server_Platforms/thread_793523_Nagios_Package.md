---
title: "Nagios Package?"
date: 2008-05-13
forum: Server Platforms
---

### Post by t8sht3r on 2008-05-13
I was trying to install nagios tonight using the apt-get command, is there not a package for Ubuntu that I can use apt-get for? All I can find when searching is "download the latest tarball", etc. I want to use the package manager if possible.

---

### Post by PseudoOne on 2008-05-13
Plenty: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nagios](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nagios)

---

### Post by Monicker on 2008-05-13
> **t8sht3r said:**
> I was trying to install nagios tonight using the apt-get command, is there not a package for Ubuntu that I can use apt-get for? All I can find when searching is "download the latest tarball", etc. I want to use the package manager if possible.

If you look at the link that PseudoOne gave, you will see that nagios is in the Universe repository.  You can enable that via the settings in Synaptic, or by editing /etc/apt/sourceslist; afterwards you will need to run an apt-get update before trying apt-get install.

---

