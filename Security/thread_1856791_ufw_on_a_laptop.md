---
title: "ufw on a laptop"
date: 2011-10-09
forum: Security
---

### Post by jsvidyad on 2011-10-09
Hello,

  This post is a follow up to another post I recently made regarding ufw. But, that was for a desktop with a wired ethernet connection. The situation for a laptop is somewhat different. So, I have a few questions regarding that.

  My first question is regarding a laptop with a wireless connection to the net. The net connection is made only after I log into a user account and connect to the net using network manager. Now, ufw is activated at system startup. How can ufw then load the appropriate iptables rules if it doesn't have any information regarding the networking set up when it starts?

   The second question is regarding a computer with the wireless card turned off using the wireless switch on the laptop. If the wireless switch is then turned on after logging into one of the user accounts and then a connection to the net is made using the wireless card, will ufw then load the appropriate iptables rules in this case at the correct time? I guess this question is closely connected to the first question.

  Thanks in advance for your help. I am just trying to understand how ufw and iptables work. Though this has a practical dimension too since I use ubuntu both on desktops and laptops.

---

### Post by mikewhatever on 2011-10-09
> **jsvidyad said:**
> 

  My first question is regarding a laptop with a wireless connection to the net. The net connection is made only after I log into a user account and connect to the net using network manager. Now, ufw is activated at system startup. How can ufw then load the appropriate iptables rules if it doesn't have any information regarding the networking set up when it starts?


The firewall activates rules the system administrator defines, and if that's you, presumably you know all there is to know about your networking setup. There aren't any automated rules.

>    The second question is regarding a computer with the wireless card turned off using the wireless switch on the laptop. If the wireless switch is then turned on after logging into one of the user accounts and then a connection to the net is made using the wireless card, will ufw then load the appropriate iptables rules in this case at the correct time? I guess this question is closely connected to the first question.


Same as above. Firewall rules are activated regardless of who logs in and what interface is used.

---

### Post by The Cog on 2011-10-09
My understanding from reading here (I haven't tried ufw) is that its default setting is to allow all outgoing connections but to block all incoming connections. Such a configuration would still be applicable regardless of which interfaces or IP addresses were in use, so changing interfaces, bringing wireless up and down shouldn't matter.

Ufw is a front end to iptables. You can view how it has configured iptables with the command```
sudo iptables -nvL
```but don't try to configure iptables directly if you are using ufw because they will conflict.

---

