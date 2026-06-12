---
title: "error while getting interface flags"
date: 2008-12-31
forum: Server Platforms
---

### Post by dtone on 2008-12-31
I'm quite new to Linux. 
I encountered a network problem after I moved a virtualbox based vm to another PC.

it displayed as following when I input '/etc/init.d/networking restar't in terminal

 * Reconfiguring network interfaces...
eth0: ERROR while getting interface flags: No such device
SIOSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0

I think there was something wrong with LAN driver druing my moving the vm to another PC.

Could you tell me how to correct this error.
Thank you very much.

---

### Post by windependence on 2008-12-31
Check that your card is properly seated in the slot on your new box. This message can appear when the card is partially inserted and it can be seen my the machine but can't be configged because all the pins aren't making contact. 

-Tim

---

