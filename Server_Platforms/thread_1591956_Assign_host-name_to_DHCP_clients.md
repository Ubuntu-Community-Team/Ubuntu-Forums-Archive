---
title: "Assign host-name to DHCP clients"
date: 2010-10-10
forum: Server Platforms
---

### Post by ruinas on 2010-10-10
Hello,

I'm trying to assign host names to clients from the DHCP server. I tell you:

    * Server: **dhcpd3-server** from Ubuntu Server 10.04

    * Clients: (**dhclient**) Ubuntu Desktop 10.04 and Ubuntu Server Edition 10.04

    *  To set-up the network information: "**host**" sentence in the  **dhcpd.conf** file, which included this line: [B]option host-name [I]client-name
[/I][/B]
    * Checking file **dhclient.eth0.leases** verify that the information reaches the client

    * I'm doing tests with VirtualBox

But [COLOR=#000000]it does not work[/COLOR], the client maintains its original name. Would appreciate any help or suggestions.

Thank you very much,


Ruinas !!

---

