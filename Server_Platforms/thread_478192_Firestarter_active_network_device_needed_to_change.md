---
title: "Firestarter: active network device needed to change automatically"
date: 2007-06-19
forum: Server Platforms
---

### Post by Badovic on 2007-06-19
Hi,

Could you help me with my problem. At home I am using wireless and at university ethernet connection. After Ubuntu starts up, followed error assage occurs "failed to start firewall". Probably the firewall can't recognize which of the type of the connections is actually using (wireless or ethernet), then only manually reconfiguration at the firewall's GUI helps me (needed to manually change the network device). Is there any
way how to do it automatically.

Laptop: Ibm Thinkpad R05e
Operation system: Ubuntu: 7.04
Firewall: Firestarter 1.03
Installation's way: Synaptic manager 

tnx
Bado

---

### Post by JanvL on 2007-06-19
Hi

just a hint.

Firestarter is afrontend for IPtables.
So you must be able to make two working sets of tables
and change between them with a simple bash-script.

Just lookup where the tables are, I did that once but do not remember at the
moment where exactly they are.

Lots of success,

Jan

---

### Post by LeChacal on 2007-06-25
Hi, I am having this same problem but can someone give me a little bit more help with the IPtables   I don't fully understand how they work or how i would go about doing what JanvL has suggested I understand the theory but don't have any idea of what do. Can someone help me more please.

---

