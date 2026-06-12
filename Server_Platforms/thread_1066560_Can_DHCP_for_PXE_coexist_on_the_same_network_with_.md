---
title: "Can DHCP for PXE coexist on the same network with another DHCP server?"
date: 2009-02-11
forum: Server Platforms
---

### Post by ThaddeusW on 2009-02-11
I am in the process of setting up a PXE boot server on an Ubuntu 8.04 server install. I currently have a m0n0wall router on my network which handles DHCP and I would like to know if it can co-exist with a DHCP server for the PXE clients. I don't know if this setup will work but I have read that it is possible to setup a second DHCP server to only listen for PXE clients.

Is this setup possible? If so can someone tell me how to configure the DHCP server or point me to a tutorial. I can set the "hidden" m0n0wall PXE feature but its not well documented and I would like to leave the PXE boot stuff to the Ubuntu system and keep it simple.

---

### Post by jimv on 2009-02-11
You don't need to set up a 2nd DHCP server.  You simply edit the config file for your current DHCP server to point PXE clients at your PXE server.

Add these two options to your subnet in the config file for DHCPD:

```
filename "pxelinux.0";
next-server ip.of.pxe.server;

```

---

### Post by ThaddeusW on 2009-02-11
> **jimv said:**
> You don't need to set up a 2nd DHCP server.  You simply edit the config file for your current DHCP server to point PXE clients at your PXE server.

I understand what you are saying but what if I had a router that was unable to handle PXE clients? I do not want to keep a power hungry computer running to provide DHCP. What if I wanted to create a portable PXE server to connect to a network and not have to worry about modifying the local DHCP server. Or if the local DHCP server is unable to handle PXE clients like a home router. For now I will setup my m0n0wall router to handle PXE clients.  

The point of my question was to find out if DHCPd is able to co-exist with another DHCP server but only handle PXE clients.

---

### Post by jimv on 2009-02-11
Just curious, are you thinking about using a PXE server to do Ubuntu installs for your clients' computers or something like that?

---

### Post by ThaddeusW on 2009-02-12
> **jimv said:**
> Just curious, are you thinking about using a PXE server to do Ubuntu installs for your clients' computers or something like that?

Yes that is the purpose, but not only Ubuntu. I want to also host a few other distros as well. It keeps me from having to burn new cd's and keep track of them for testing other distros, installing etc.

---

### Post by HDave on 2009-06-27
Did you ever solve this?  I am interested in the same thing.

---

### Post by kixome on 2009-06-27
Yes you can have 2 dhcp servers on the same network, you should point your clients to one for main and the second as alternative, also make the dhcp servers see each other as main and the opposing as alternative. You could also make this work using subnetting(different subnets), but I am not going to get into that.

---

### Post by kixome on 2009-06-27
Jimv's way is probably the best route to go with minimal effort, I was just saying the answer to your question is Yes

---

### Post by HDave on 2009-06-28
My problem is that my DHCP server is also my network router.  While I can turn that DHCP server off, I would really prefer not to as my PXE server can't be on all the time.

---

### Post by netztier on 2009-06-29
> **HDave said:**
> While I can turn that DHCP server off, I would really prefer not to as my PXE server can't be on all the time.

A normal PC booting shouldn't issue a PXE request, should it? It will just boot and use DHCP to ask for an address. If it (accidentally) sends PXE request, it will get redirected to the PXE server. If the PXE server is offline and the request will timeout - just as well...

So I think you can modify the m0n0wall's DHCP server to redirect PXE requests to the PXE server - regardless of the server's availability, without impacting the rest of the DHCP service it provides to other clients on the subnet.


regards

Marc

---

### Post by netztier on 2009-06-29
> **kixome said:**
> You could also make this work using subnetting(different subnets), but I am not going to get into that.

You wouldn't even have to go as far as having different/multiple subnets in a single broadcast domain.

You can configure non-overlapping DHCP ranges *within the same subnet*, where one server doles out addresses from 192.168.0.10-99, while the second server gives addresses from 192.168.0.110-199 (for example). 

Each client gets two DHCPOFFERs to it's DHCPDISCOVER, and it picks one of the offers, it'll broadcast it's DHCPREQUEST and the "losing" DHCP server will see that it's offer was not accepted and will free up the preliminarily reserved address.

regards

Marc

---

### Post by HDave on 2009-06-30
> **netztier said:**
> So I think you can modify the m0n0wall's DHCP server to redirect PXE requests to the PXE server - regardless of the server's availability, without impacting the rest of the DHCP service it provides to other clients on the subnet.

My Linksys/Cisco router has no such setting on the DHCP server to redirect PXE requests.  I can give the two DHCP servers different and non-overlapping IP ranges, but unless the router's DHCP server is smart enough to ignore PXE boot requests there will still be confusion.  It's a real pickle!

---

### Post by floomby on 2009-10-25
I came across this **old **thread on google.

But for the benefit of other people searching, I think what the OP wants to do is possible using the proxydhcp feature of dnsmasq, so you only have one DHCP server, in my case, a home router. The dnsmasq server just responds to any pxe boot requests. I followed this guide [https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP](https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP)
I cannot get it to work in Virtualbox, however I did manage to boot another physical computer with method.

---

