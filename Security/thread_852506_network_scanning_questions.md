---
title: "network scanning questions"
date: 2008-07-07
forum: Security
---

### Post by Red-Shield on 2008-07-07
i want to scan my network to see if there are other users talking to my router or using my connection i think the mac filtering is no longer working on my router i limit the router to hand out ony 3 ip address/dhcp users and something is a foot i dont lock my network other then that so can any one tell me if there is a way to scan the network to see if there any other mac address using my access point/router using the terminal of course??????????.............. here are the periods you thought i forgot put them where you see fit

---

### Post by Dizzle7677 on 2008-07-07
[NMAP]("http://nmap.org")

---

### Post by sp0nge on 2008-07-07
NMAP is awesome!

---

### Post by Dr Small on 2008-07-07
> **Red-Shield said:**
> i want to scan my network to see if there are other users talking to my router or using my connection i think the mac filtering is no longer working on my router i limit the router to hand out ony 3 ip address/dhcp users and something is a foot i dont lock my network other then that so can any one tell me if there is a way to scan the network to see if there any other mac address using my access point/router using the terminal of course??????????.............. here are the periods you thought i forgot put them where you see fit
You could use Wireshark to do some packet sniffing.

---

### Post by The Cog on 2008-07-08
It might be easiest just to ask the router for its ARP table (if that's possible). The ARP table is a list of IP address -> MAC address lookups.

---

### Post by lisati on 2008-07-08
My router has an "Attached Devices" option on it's administration screen.

---

### Post by Dr Small on 2008-07-08
Or you could use ettercap to scan for all hosts that are connected to the router, and it will give you a list.

---

### Post by timcredible on 2008-07-08
> **Dr Small said:**
> Or you could use ettercap to scan for all hosts that are connected to the router, and it will give you a list.

small typo - ethercap

---

### Post by Dr Small on 2008-07-08
> **timcredible said:**
> small typo - ethercap
No, there is no typo. I ment "ettercap".

---

