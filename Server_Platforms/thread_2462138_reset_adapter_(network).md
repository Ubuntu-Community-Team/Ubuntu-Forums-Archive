---
title: "reset adapter (network)"
date: 2021-05-14
forum: Server Platforms
---

### Post by smokeybr on 2021-05-14
i woke up this morning to find i could not ssh into my server, when looking at the physical machine i saw lights were turned off on the network card and also i had multiple messages with

[ATTACH=CONFIG]288470[/ATTACH]
i tried to boot the system and network starts working fine after a few mins (10 tops) but then network is turned off
i could retrieve a log that shows up exactly when network goes down
[ATTACH=CONFIG]288469[/ATTACH]

netplan
[ATTACH=CONFIG]288471[/ATTACH]


this goes to the extent of logs i know to get if i can do more to figure it out please let me know
ps:sorry for the pics i have no way to ssh into the server right now

---

### Post by LHammonds on 2021-05-14
Can you swap the NIC with a different one?

---

### Post by smokeybr on 2021-05-14
I can... however i dont believe the NIC or PCI is the problem, i have now set up the same NIC,port,IP on a different router and its working so far however i do have a bunch of services turned off.

The reason i changed router was because i was using pfsense as a virtual machine
any thoughts ?

---

### Post by smokeybr on 2021-05-14
nevermind just happened again as soon as i started rtorrent


EDIT: i am now testing with a different NIC

---

### Post by smokeybr on 2021-05-14
same problem different NIC, rtorrent was not on
[ATTACH=CONFIG]288472[/ATTACH]

---

### Post by LHammonds on 2021-05-14
The "no carrier" message was making me think it was the NIC...however, it could be the cable or the port it is plugged in to.

LHammonds

---

### Post by smokeybr on 2021-05-16
it seems your guess was right, i had 2 different NIC however they were the same make and model both would result in the problems, when i finally used the onboard network port problem did not occur, it seems to have started after an ubuntu update.
The NIC is an intel PRO/100 MT Dual Port how would i go about checking support for it ?

---

