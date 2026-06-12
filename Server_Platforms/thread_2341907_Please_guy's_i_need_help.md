---
title: "Please guy's i need help???"
date: 2016-11-02
forum: Server Platforms
---

### Post by amsar on 2016-11-02
after i finish install squid with mikrotik and i do every thing wright i  still can't have any data from my squid so if i download winrar.exe   and remove it from my PC and re-downloaded it started from begin

some PHO

[https://s14.postimg.org/uqu3nmic1/image.jpg](https://s14.postimg.org/uqu3nmic1/image.jpg)

[https://s14.postimg.org/idh9gpsnl/image.jpg](https://s14.postimg.org/idh9gpsnl/image.jpg)

[https://s14.postimg.org/o2xi10ytt/image.jpg](https://s14.postimg.org/o2xi10ytt/image.jpg)

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.50$
route add -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.50.254 dev eth1


exit 0

```

**pleases pleases any one have any idea where the problem**

---

### Post by mörgæs on 2016-11-02
A thread title like this is not likely to bring many answers. People just skip it.

Better to write a short and exact description of your problem.
[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by ajgreeny on 2016-11-02
And please do not use large inline images in your post as you originally did.
Either add images from your hard disk as attachments using the paperclip icon in the "Reply to Thread" window or use links as I have now done; attachments preferred.

---

