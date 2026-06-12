---
title: "Firestarter start-up at log-in"
date: 2008-10-02
forum: Security
---

### Post by Nuu on 2008-10-02
At the moment, I'm on a laptop which is constantly connected to the wired A.D.S.L. Ethernet network. When I log-in I manually start up Firestarter. I have ticked all three boxes in the 'Firewall Startup and Persistence', but it doesn't seem to make any difference (although I'm not sure that it was supposed to). Is there a 'start-up' folder in which you can just put a shortcut in and it will run the programme, like in Windows XP, perhaps?

---

### Post by citro_cell on 2008-10-02
Short Answer: By installing Firestarter and running the wizard you are protected.  Once configured, you don't need it "running in the background"

According to "Beginning Ubuntu Linux" by Keir Thomas (great book btw)- "Firestarter is used only to configure the built-in firewall and doesn't need to be running for the firewall to work.  Once you've finished configuration, you can quit the program.  You'll need to use it again only if you wish to reconfigure the firewall."  

One preference Keir suggests editing is under Preferences-ICMP Filtering, enable ICMP filtering.  This will disable all of the packet types listed below it - "if you don't know what ping and traceroute are, your won't miss them, so there will be no harm in disallowing them."

Good Luck

---

### Post by hyper_ch on 2008-10-02
(1) Firestarter is no firewall
(2) Firestarter is merely a GUI for iptables, the actual firewall
(3) Are you sure you need to mess around with iptables? In most cases there's no need for that

---

### Post by Nuu on 2008-10-02
Cheers.

---

