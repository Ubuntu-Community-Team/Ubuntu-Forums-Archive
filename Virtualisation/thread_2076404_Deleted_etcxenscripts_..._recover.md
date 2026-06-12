---
title: "Deleted /etc/xen/scripts ... recover?"
date: 2012-10-25
forum: Virtualisation
---

### Post by bryogenic on 2012-10-25
I made a bonehead mistake and rm'd [FONT="Courier New"]/etc/xen/scripts[/FONT].  I tried [FONT="Courier New"]apt-get install xen-hypervisor --reinstall[/FONT] with no success.  Any other ideas?  Any help is greatly appreciated!

-bryogenic

---

### Post by vandorjw on 2012-10-25
[http://packages.ubuntu.com/lucid/amd64/xen-hypervisor-3.3/filelist](http://packages.ubuntu.com/lucid/amd64/xen-hypervisor-3.3/filelist)

Take a close look at that filelist.
I don't know what version of Ubuntu or Debian you are using, but the xen-hypervisor package most certainly does not contain any configuration files.

/etc/whatever usually contains configuration files for "whatever"

If you did this in a production enviroment, then I wish you best of luck.

(what I would do is check your backup files.)

---

### Post by bryogenic on 2012-10-25
It definitely isn't production.  Mostly I was curious what I rm'd and where it came from, which might lead to easily repairing it.  The few google's I tried were not very informative of what the scripts were for so I figured it might be worth asking here.  Thanks again!

---

