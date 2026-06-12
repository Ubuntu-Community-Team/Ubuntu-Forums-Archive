---
title: "[ubuntu] How to commision nodes on MAAS 2.0 ?"
date: 2016-06-20
forum: Ubuntu Cloud and Juju
---

### Post by GiFos on 2016-06-20
[FONT=Ubuntu]Hi,

I have a problem about how to commision nodes on MAAS 2.0.  The nodes succesfully registered on MAAS as "New". I choose "commisioning" for the nodes and also choose "Manual" for Power Type for each nodes. After that i'm powering up nodes manually by a power button on the nodes case. After half a minute booting from PXE, the nodes automatically shutting down itself. This behave like a first time registering nodes on MAAS. The status on the MAAS still "commisioning" until time out. What's going wrong or what step that i forgot? The guide on the internet only for MAAS 1.9 and below, not 2.0. Also there is no "wake on lan" for the Power Type in MAAS 2.0. How do i remotely power on nodes when i don't have other Power Type except Wake on Lan? 

The nodes and server i'm using are ordinary/consumer computer without brand, not a server grade. The OS for the server is uBuntu Server 16.04 LTS.

I'm very grateful if anyone can help me, and i'm sorry for my english as i'm not an english native speaker.

Thank you.[/FONT]

---

### Post by Fire_Chief on 2016-06-21
Do you have the option to use IPMI instead of WOL (wake on lan)?

---

### Post by GiFos on 2016-06-22
Thanks for the suggestion, Fire_Chief. As i stated above, my nodes and server hardware are (old, Core 2 Duo era) consumer grade, not a server grade. It doesn't have a fancy option like IPMI or AMT. The only option is Wake on Lan (WoL), but on MAAS 2.0 there is no option for WoL. 

So what is your suggestion? Do i must downgrade to MAAS 1.9 or below, or switch to another cloud server option like Eucalyptus?

---

