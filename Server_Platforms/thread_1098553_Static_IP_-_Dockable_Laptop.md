---
title: "Static IP - Dockable Laptop"
date: 2009-03-17
forum: Server Platforms
---

### Post by MrWES on 2009-03-17
I'm currently assigning static IP address via my router and the card's MAC address. Can I assign the same IP, say 192.168.1.114 to my wife's docked laptop and the same IP when it's not docked? It's running hardwired when docked and wireless when not, so the MAC addresses would be different.

Bill

---

### Post by albandy on 2009-03-17
> **MrWES said:**
> I'm currently assigning static IP address via my router and the card's MAC address. Can I assign the same IP, say 192.168.1.114 to my wife's docked laptop and the same IP when it's not docked? It's running hardwired when docked and wireless when not, so the MAC addresses would be different.

Bill

if you set the 2 interfaces with the same MAC the router will set the same IP to the 2 interfaces but ensure you don't have both enabled at the same time.

---

### Post by MrWES on 2009-03-17
> **albandy said:**
> if you set the 2 interfaces with the same MAC the router will set the same IP to the 2 interfaces but ensure you don't have both enabled at the same time.

Right --that's what I was thinking. The wireless card is disabled in the docked hardware profile. Should work right?

---

### Post by volkswagner on 2009-03-17
If the above does not work, I would use the router/mac to assign the wireless as static.  I would then use the Ubuntu LAN manager to set a static ip on the wired interface.  This would allow roaming on the wireless interface.  Again you would still want the interfaces on one at a time.

---

### Post by MrWES on 2009-03-17
> **volkswagner said:**
> If the above does not work, I would use the router/mac to assign the wireless as static.  I would then use the Ubuntu LAN manager to set a static ip on the wired interface.  This would allow roaming on the wireless interface.  Again you would still want the interfaces on one at a time.

Ok..I think that card is wlan0, so I'd edit the network interface for that and hard assign the IP. Got it.

BTW, still have a lot of snow up in Kingston? :)

Bill

---

### Post by volkswagner on 2009-03-17
> **MrWES said:**
> Ok..

BTW, still have a lot of snow up in Kingston? :)

Bill

Just the disgusting piles in parking lots.  ;)

---

