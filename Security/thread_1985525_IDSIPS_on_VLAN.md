---
title: "IDS/IPS on VLAN"
date: 2012-05-23
forum: Security
---

### Post by FuriousRage on 2012-05-23
Hi, at my company we're sitting here and discussing 
on maybe setting up IDS/IPS and what we gathered, the IDS part
can just be hooked up to the VLAN and listen with snort and using acidbase to monitor the lan,


But however, with IPS, would we have to rout all VLAN traffic thru the (linux) server or can we just "hook it up" on the vlan?

(internet and/or other vlans)
................|
[IDS/IPS]--+
................|
[-------VLAN------]

Like this?

--

We're not looking for a ready made solution, more like pointers
"you need this and that"-solution so we can build it up our selves.


Or do we need to build the vlan like i suspect:


(internet and/or other vlans)
......|
..[IDS/IPS]
......|
[-------VLAN------]


--

with the first solution, route thru the ids possible even if a "shorter way" is available is present?

---

