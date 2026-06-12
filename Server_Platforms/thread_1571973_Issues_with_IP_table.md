---
title: "Issues with IP table"
date: 2010-09-10
forum: Server Platforms
---

### Post by djanie78 on 2010-09-10
I got two NICs on a server am working on. One to the LAN and the other to the WAN. The WAN is there so users can PPTP onto the server and user server resources. The LAN is there so i can get onto the server via the LAN. 

I dont want PPTP user who have come from the WAN to be able to go onto the LAN so i thought IP tables....

How can i configure it such that us going onto the server from the LAN can go anywhere but the bad guys who PPTP from the WAN can only stay on the server and not break into the LAN

The pptp server is on the server

Help please

thanks

---

### Post by bprins on 2010-10-10
ehm, why don't you just go for your first solution (which seems to work?) and install a decent firewall on your server system?

---

### Post by BkkBonanza on 2010-10-10
```

-A FORWARD -i $WANIF -o $LANIF -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i $WANIF -o $LANIF -j DROP
-A FORWARD -i $LANIF -o $WANIF -j ACCEPT

```

New connections are dropped but established are allowed thru for replies to LAN users. You don't need that DROP rule if the FORWARD chain policy is set to DROP.

---

