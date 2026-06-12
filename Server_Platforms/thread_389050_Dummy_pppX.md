---
title: "Dummy pppX ?"
date: 2007-03-20
forum: Server Platforms
---

### Post by hachaboob on 2007-03-20
Is it possible to create a dummy deviced called ppp0 or ppp1 etc?

I have setup shorewall (3.4.1) with 2 (eth0, eth1) internal and 2 external interfaces (ppp0, ppp1). the 2 externals are managed by rp-pppoe to connection to adsl. because i use shorewall to route from eth0 to ppp0 and from eth1 to ppp1 both external interfaces must be up for shorewall to load and everything to work. ideally i would like to be able to handle fallover of one of the internet connections. i was thinking creating a dummy ppp interface so at least shorewall can start and modify routing manually when it happens...

---

