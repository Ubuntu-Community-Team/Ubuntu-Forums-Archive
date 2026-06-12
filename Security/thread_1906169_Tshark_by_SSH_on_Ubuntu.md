---
title: "Tshark by SSH on Ubuntu"
date: 2012-01-08
forum: Security
---

### Post by Borg6of9 on 2012-01-08
Hi,
 
I'm sniffing packets with Tshark on a distant Ubuntu Laptop with SSH connected on a Cisco Switch.
 
So if i logon by SSH and start the tshark session, when i start the span session on the port of the Laptop on the Cisco switch, i lose my connection because the Laptop's port becomes on Monitoring status.
 
How can i recover the process when i "no" the monitoring port and get the connection back when i reconnect by ssh ? 
 
V

---

### Post by Dangertux on 2012-01-08
> **Borg6of9 said:**
> Hi,
 
I'm sniffing packets with Tshark on a distant Ubuntu Laptop with SSH connected on a Cisco Switch.
 
So if i logon by SSH and start the tshark session, when i start the span session on the port of the Laptop on the Cisco switch, i lose my connection because the Laptop's port becomes on Monitoring status.
 
How can i recover the process when i "no" the monitoring port and get the connection back when i reconnect by ssh ? 
 
V

Run the process in a screen session, then just screen -x to reattach once you reconnect.

---

