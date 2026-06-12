---
title: "Possible security breach trough Intel ME / IPMI on Servers ?"
date: 2021-01-23
forum: Server Platforms
---

### Post by Anquietas on 2021-01-23
Hello,

I have 2 server that I installed with Ubuntu Server and I monitor them.

Suffice to say that I didn't configure the BIOSes initially. Somebody else was in charge of this operation.

Let's call these servers: Server1 and Server2.

Server1 is a Lenovo ThinkCentre M92P - This one has Intel Management Engine with AMT
Server2 is a HP Proliant DL160 G6 - This one has IPMI (to my surprise, it doesn't have ILO).

I was in charge of the OS Section.
I installed Ubuntu 20.04 on both of them, I secured them, firewall, VPN, and so on....

But I dind't pay attention to one single thing: the possibility of external access, independent of OS, via Intel ME/AMT and IPMI.

I disabled them both (Intel ME/AMT and IPMI) on both servers so I can have a good night sleep. And no, I do not need them. OS with Linux is enough, I don't need remote management features.

My questions are (I ASK THAT ONLY PEOPLE WHO KNOW THESE THINGS LIKE 100% TO ANSWER ME, OK ?)

1. CAN SOMEBODY HACK INTO MY SYSTEM USING THESE AND ACCESS THE CONTENTS OF MY HDD WHILE LINUX IS RUNNING ?
(I am ONLY interested in information theft or virus/info writing on HDD).
I don't care about CPU temperature, auto-reboots and sensors. Nothing happened that I should have noticed.
I am only interested in remote exploits.

Is it possible ? Does Intel ME/AMT or IPMI allow for this ? (for externals to enter my system and read the HDD) ?

I also mention the following facts:

1st server (Intel ME/AMP):
- I think it only runs on the on-board NIC. I don't use the onboard LAN Card. Only PCIe LAN Cards.
Does Intel ME/AMPT run only on on-board NIC ? If that is the case, I can stay relaxed.
- It looks like AMP had DHCP active, but my Card doesn't get DHCP, so I believe this is also a good point.
- Even configuring a local address, I wasn't able to access Intel ME/AMP from Linux or from on an external computer via the real IPs. Port scans reveal no open ports, aside from those opened by Linux

2nd server (IPMI):
- IMPI is set on BIOS to run on DEDICATED NIC. Not on Shared Onboard NIC. (but I don't saw a dedicated RJ-45 Port on the back of the server)
- Also, NO IP address is obtained via DHCP.
- I wasn't able to access Intel ME/AMP from Linux or from on an external computer via the real IPs. Port scans reveal no open ports, aside from those opened by Linux

I disabled the services now.
I am interested if UNTIL NOW, could anyone have entered in some form or another to access my HDD ?
I believe that in order to enter, an IP address must be configured. Intel ME/AMP and IPMI both used DHCP on an interface on which I didn't have an IP. But in my Internal LAN, I had an IP on a PCIe card. Could that have been a problem ?

If someone can help, please help me with these security concerns....

Thank you !

---

