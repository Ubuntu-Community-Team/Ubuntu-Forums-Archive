---
title: "Firestarter: Inbound Traffic Rule I Did Not Create"
date: 2008-09-25
forum: Security
---

### Post by ajacx on 2008-09-25
Hi,

As a new Linux user I decided to install Firestarter and went through all the shields up tests successfully when I first installed Ubuntu a few months ago. Today I had a look at my Firestarter rules and found a rule had been created to allow inbound traffic from 92.81.150.208, I'm quite certain that I personally did not create that rule.

I'm worried about whether some has gained access to my desktop. Can you please tell if it is possible for me to find out when this rule was created, who created it and steps I can take to make my computer secure?

I don't know if this is important, but I'm a home user and I installed the LAMP package to learn a little about web development. I've followed the instructions to make sure the server is only used locally and no inbound traffic is allowed.

Thanks

---

### Post by lisati on 2008-09-25
1) I don't know how the rule got created. 
2) According to the ["What is my IP address?" website]("http://whatismyipaddress.com/"), the IP address 92.81.150.208 belongs to someone in Romania.

---

### Post by ajacx on 2008-09-27
Thanks, I did check to see where the ip address belonged, and when I searched for 92.81.150 I found a fwe references to spam bots.
I'm not sure if I asked right, I would like to know if there are any log files that can show me when a rule was created or modified in firestarter [or probably iptables]. The only reason I'm asking is so that I can find out when (or if) my desktop was compromised and check to see if other important programs were modified immediately afterwards. Does anyone know?
Also as a general question, how secure is firestarter's default configuration (with ICMP filtering)?

---

