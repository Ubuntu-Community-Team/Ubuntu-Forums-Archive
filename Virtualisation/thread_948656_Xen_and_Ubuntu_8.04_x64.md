---
title: "Xen and Ubuntu 8.04 x64"
date: 2008-10-15
forum: Virtualisation
---

### Post by DavidBer on 2008-10-15
Please bear with my lack of knowledge.  I am not new by any means, just new to Ubuntu and Xen :)  Most of my work is done on CentOS boxes.

I have a need to install Xen.  I am trying to get Eucalyptus ([http://eucalyptus.cs.ucsb.edu/](http://eucalyptus.cs.ucsb.edu/)) installed and Xen as well as Java JDK > 1.5 are requirements.

I have a Ubuntu 8.04 x64 box that I dual boot with Vista 64.  I figured what better place to do this!

Ubuntu works fine.  I did a apt-get install xen-server.  It did a bunch of installs, modified grub and suggested a reboot.  I rebooted.

Now what happens is that I get no access to any network devices.  I did an ifconfig and it no longer shows eth0, it shows peth0 with the ip address from the DHCP server.

I looked at the config file and made sure that the network-bridge was uncommented.  I did a xend restart and I get a peth0 not configured.

I went into system administration and noticed that the interface was set to roaming.  I unlocked it and set it to DHCP.  I then did a xend restart and get the same errors, but now I get something more interesting!  I can see my local network but can not get past my router.

Does anyone have an idea what I need to do to configure this Ubuntu box so that I can get Xen working on it and have net access?

Thanks.

dave

---

### Post by louvros10 on 2008-10-18
Maybe this will help you:
[http://mediakey.dk/~cc/ubuntu-howto-install-xen/](http://mediakey.dk/~cc/ubuntu-howto-install-xen/)

---

