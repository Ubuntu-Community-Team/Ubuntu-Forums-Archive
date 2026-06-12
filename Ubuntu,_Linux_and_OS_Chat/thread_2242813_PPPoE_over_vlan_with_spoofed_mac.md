---
title: "PPPoE over vlan with spoofed mac"
date: 2014-09-04
forum: Ubuntu, Linux and OS Chat
---

### Post by charlvv2 on 2014-09-04
Hi,

This might not be the appropriate forum to post this in but I thought I would just try to get some feedback first.

I have an ubuntu server 12.04 machine connected to 4 ADSL modems via a managed switch with a vlan interface for each modem. Connections are made to various ISPs over each of the lines.

This setup works perfectly well in 1 location but not in another. The problem with the second environment it seems is that the access concentrator is limiting the number of lines an initiator (single hardware address) can connect from.

My attempt at a workaround was to spoof the vlan mac addresses. Without changing the mac address of the third vlan pppoe discovery fails. Setting a different mac address allows pppoe discovery to complete but authentication fails. Using tcpdump I discovered that the mac address used during discovery is the spoofed address. The problem then comes with LCP. Incoming frames from the responder uses the spoofed address but outgoing frames have the address of the underlying ethernet interface.

Is this behavior to be expected?

Thanks in advance for any assistance.

---

