---
title: "restricting PPTP users"
date: 2013-02-18
forum: Server Platforms
---

### Post by sbdcunha on 2013-02-18
Dear All,
I have a Ubuntu PPTP vpn server and its working fine
I have about 8 users that are using vpn.
each user should be able to access their own server or servers

now the issues I am having is how do I restrict a particular user to access only his server and not even able to ping or reach the other server

is it possible on the VPN server that if the user logs in a userA he is allowed to access only server1 and server2 and not server 3 and similarly userB allowed to access server 2 and server 3 but not server 1

appreciate your kind help

regards

simon

---

### Post by MrKaliman on 2013-02-18
Using pptp is not a good choice anymore.
Please read the following article: 
[http://www.zdnet.com/blog/ou/pptp-vpn-authentication-protocol-proven-very-susceptible-to-attack/21](http://www.zdnet.com/blog/ou/pptp-vpn-authentication-protocol-proven-very-susceptible-to-attack/21)


Maybe it is better to choose ltp or ipsec?

About the security case. Make sure that only the user account of a particular user is enabledon the server where he/her is allowed to logon.

---

### Post by sbdcunha on 2013-02-20
dear mr kaliman,

thanks and apprecite your quick reply..
by the way I just wanted to ask you if on he same current pptp server can be coverted to ltp/ipsec server


thanks once again and god bless you


regards

simon

---

### Post by sbdcunha on 2013-02-20
dear mr kaliman

sorry to mention earlier 
any goods link that can help me to setup ltp/ipsec server...


thanks in advance

regards

simon

---

### Post by jonobr on 2013-02-20
Hello



Whether your using PPTP or L2TP or some other method, I still think your stuck with limiting network access to servers based on who the user is.

I would recommend reading [bodhizazen's]("http://bodhizazen.net/Tutorials/iptables#Using_iptables_for_Filtering") (staff emeritus at the UF) excellent blog


I figure your best bet is to set up users in groups.
This way you can control the groups access using iptables or ufw
Go to the part in the blog which discusses limiting network access based on groups

---

### Post by sbdcunha on 2013-02-20
thanks you guys for the wise replies..
i really appreciate.


thanks and regards


simon

---

