---
title: "Request assistance or guide on how to use freeradius on Mac address authentication"
date: 2016-03-07
forum: Security
---

### Post by stevekk0430 on 2016-03-07
[FONT=Verdana]

Dear All,

Any one has the experience of implementing the RADIUS server to authenticate PC Nodes MAC address ? IEEE 802.1x ? i would need to guidance on how to set up a radius server with store all the pc mac address and reject those unauthenticated machine. (Linux server ).

thank you [/FONT]

---

### Post by SeijiSensei on 2016-03-07
Do you just want to allow or deny clients based on their MAC addresses, or do you need to authenticate the users' credentials as well?  If the former, you can use isc-dhcp-server instead.  You can give the server a list of authorized MAC addresses and tell it to deny any other connections.

---

