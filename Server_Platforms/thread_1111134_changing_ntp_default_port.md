---
title: "changing ntp default port"
date: 2009-03-30
forum: Server Platforms
---

### Post by yamahammer on 2009-03-30
Is it possible to change the default port for ntp sync? I would like to sync clients through a vpn and using custom port, but i'm having trouble find resources to help me learn how. Can anyone provide some insight or suggest a resource to accomplish this?

---

### Post by BkkBonanza on 2009-03-30
I don't think you can change the ntp port. However, I expect you could add an iptables comand to redirect it through a vpn port. I found this link which has some info that may help you,

[http://openvpn.net/archive/openvpn-users/2007-11/msg00223.html](http://openvpn.net/archive/openvpn-users/2007-11/msg00223.html)

---

### Post by yamahammer on 2009-03-30
Awesome, thank you for your quick reply! That thread addresses a very similar situation we are trying to work around.
Thanks again!

---

