---
title: "How to Use VPN Without Network Manager?"
date: 2013-03-24
forum: Server Platforms
---

### Post by daz1uk on 2013-03-24
Hi,

I have an Ubuntu Server setup as a home server for streaming media for the family and KVM Dev environments for my development work. I have manually editied /etc/network/interfaces to setup the bridge for the KVM machines so I no longer have a working Network Manager utility. How can I setup this server to use a VPN connection please?

Thanks

---

### Post by matt_symes on 2013-03-24
I think this thread may get better responses in the **server platforms **sub forum.

Thread moved.

---

### Post by daz1uk on 2013-03-24
OK, Cheers.

---

### Post by sandyd on 2013-03-25
> **daz1uk said:**
> Hi,

I have an Ubuntu Server setup as a home server for streaming media for the family and KVM Dev environments for my development work. I have manually editied /etc/network/interfaces to setup the bridge for the KVM machines so I no longer have a working Network Manager utility. How can I setup this server to use a VPN connection please?

Thanks

You will want to install openvpn, and place the configuration in /etc/openvpn.
A sample configuration is provided at /usr/share/doc/openvpn/sample/examples/sample-config-files/

---

