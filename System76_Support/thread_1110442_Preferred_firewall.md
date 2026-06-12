---
title: "Preferred firewall?"
date: 2009-03-29
forum: System76 Support
---

### Post by andrewdied on 2009-03-29
Just wondering if System 76 or someone in the group had a preferred firewall in ubuntu.  Basically I'm not interested in crafting my own iptables scripts.  

I did see [http://knowledge76.com/index.php/Firestarter_Firewall_Guide]("http://knowledge76.com/index.php/Firestarter_Firewall_Guide") in the howtos, but other than how to make it go I don't know anything about it.

---

### Post by nerdboy4200 on 2009-03-29
I've used Firestarter ever since I've had my machine. (Gazelle Performance V1 - ~2.5 yrs) It works reliably and logs any major incoming things. But there is one thing that I don't like about it's setup:

* Going from Wired->Wireless does not work - firestarter doesn't handle that well - it acts like there is no firewall until I switch it from the wired interface to the wireless interface. This also occurs if I go onto a VPN.

I am currently trying out a different system: ufw. It is just as easy to configure even. It may also work better over both VPN's and over wireless...

-Josh

---

