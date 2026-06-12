---
title: "Edubuntu - install in existing network?"
date: 2012-09-02
forum: Server Platforms
---

### Post by Sternfan on 2012-09-02
Hi all,
I am testing Edubuntu and will be installing it in an existing network (at work) that already has a DHCP server.  

As I understand it, Edubuntu automatically configures and starts DHCP when doing the install.

How do I insure that Edubuntu won't install or enable DHCP during the install?

Thanks,
Rob

---

### Post by kgatan on 2012-09-02
It will only install the dhcp service if you use the LTSP package.

---

### Post by Sternfan on 2012-09-03
Ok - but I need the LTSP package to run Edubuntu - correct?  In short - I want to set up a Edubuntu server and some clients and use the existing DHCP server.  

Rob

---

### Post by kgatan on 2012-09-03
You only need the LTSP package if you want your clients to network boot from your Edubuntu server.

I think the typical set-up for a small ltsp environment is to have two nic's in your server, one for your main network and DHCP on the second for the LTSP network.

However, when I tried it in my small home network with just a single nic it still worked with two dhcp's as the edubuntu dhcp regonised the main dhcp and setup as a slave.
But I don't think it's recommended.

---

### Post by racnor on 2012-09-25
try "echo manual > /etc/init/isc-dhcp-server.override"

---

