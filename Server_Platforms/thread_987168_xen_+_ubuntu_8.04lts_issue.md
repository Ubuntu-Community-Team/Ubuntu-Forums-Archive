---
title: "xen + ubuntu 8.04lts issue"
date: 2008-11-19
forum: Server Platforms
---

### Post by Scarby on 2008-11-19
Hi
i'm having an issue with xen under ubuntu.

After installing the ubuntu-xen-server package through apt-get along with some config changes (ensure networking operational), i then reboot the system into the xen kernel however at this point i have no networking at all, doing ifconfig i am able to see my network adaptors however both fail to receive a DHCP lease (either when both connected or singularly), i have tried assigning eth0 (the default) a static ip and this still does not work ip's shown but am unable to send or receive anything. When booting back to the standard kernel and making no changes to config files the networking works flawlessly.

Any ideas?

Thanks
Scarby

---

