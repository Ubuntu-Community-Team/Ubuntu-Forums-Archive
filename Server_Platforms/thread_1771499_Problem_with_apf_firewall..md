---
title: "Problem with apf firewall."
date: 2011-05-30
forum: Server Platforms
---

### Post by cheater99 on 2011-05-30
Hi,

I've got my server running ubuntu 10.10. I installed apf-firewall two  nights ago (28th may) and set it up with the ports i needed etc, fine.  Was all working. I go to ssh in this morning, to find that my connection  is refused. I try pinging the server, no response. 

I asked a friend to test the pinging, and it responds fine for him.  Tunneling through him, I managed to get connected to the server and  stopped apf (i ran 'apf -f'). 

Lo and behold, I could now connect over my connection again. I read some  other issues people had had, and added my IP to allow_hosts.rules.  Started apf again, no luck.

I've checked deny_hosts.rules and it's empty, as well as  glob_allow.rules and glob_deny.rules. I've tried rebooting the server  multiple times. I also read it could be iptables, but running "iptables  -L" only returns this (below) so i assume there's nothing in there.
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```Is anyone able to help me? Any help will be highly appreciated :smile:

Thanks in advance.

---

### Post by ablake on 2012-03-21
I have a script that sends mail via the gmail SMTP on port 587. When apf  is turned off it sends, but when apf is turned on it can't connect. I  have added 587 to both IG_TCP_CPORTS and EG_TCP_CPORTS, and have tried  with EGF set to "0" and set to "1". EG_ICMP_TYPES is set to "All". But  nothing works -- the only way the script can send is with apf-firewall  turned off.

I would have liked to post this as a new post, but I just can't see how to post anything.

---

