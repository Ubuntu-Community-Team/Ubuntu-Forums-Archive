---
title: "Samba Server"
date: 2006-02-07
forum: Server Platforms
---

### Post by ruth on 2006-02-07
Hi everybody,
i just started using Ubuntu as a Samba PDC.
i did not change the default /etc/apt/sources.list for that.
Now, i have some errors in my network.
Searching for bugs, i found, that these bugs are resolved upstream in samba > 3.0.14.
Unfortunately, this is the version, that is currently marked stable in Ubuntu 5.10
So my Question is:
there's a 
samba/samba-common_3.0.21a-1ubuntu1_i386.deb
and a
samba/samba_3.0.21a-1ubuntu1_i386.deb
in
[http://de.archive.ubuntu.com/ubuntu/pool/main/s/samba/](http://de.archive.ubuntu.com/ubuntu/pool/main/s/samba/)
for example
How do i manage to install this version?
I guess, that this is called mixing...
What do i have to write into my sources.list, so that apt can update my samba installation?
basically, all i want to to is something like having a stable  base system and have the latest samba packages installed...
i already have searched about this issue on google, but did not find something useful...
maybe someone can push me into the right direction?

best regards,
ruth

---

### Post by eudoxos on 2006-02-07
The easiest is to download required .debs manually and install them by `dpkg -i *.deb`. That will work if dependencies of samba from dapper are satisfied by packages from breezy.

In the more complex case, you will add dapper to your sources (in /etc/apt/sources.list) and will use **pinning** to prefer breezy. This way, only the packages you really want to upgrade will be upgraded, the rest will be kept at the preffered (breezy) version. You will have to force the version of samba (in synaptic Package -> Force version, in aptitude by selecting it from package details, from command line by saying samba=3.0.21a).

See [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html) for nice intro and HOWTO. The preference file is /etc/apt/preferences, google for it if in doubt.

Regards,

Eudoxos

---

