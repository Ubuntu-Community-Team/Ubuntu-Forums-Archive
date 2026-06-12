---
title: "bind trouble. Need a little help."
date: 2012-03-10
forum: Server Platforms
---

### Post by Drenriza on 2012-03-10
Hi guys. I have tried to setup an dhcp with a dns (bind) solution. From what i understand i have added a line in the dhcp conf that should allow the dns service, to add the client with an A record, when the client get a dhcp address. So you dynamic can say ping host1, from any other machine on the local network without manually edit the /etc/hosts file.
 
But this function is not quite working and im wondering where i have gone wrong.
The configuration is as follows.

---

### Post by Drenriza on 2012-03-10
Pictures #2

---

### Post by Drenriza on 2012-03-10
No one who have an idea i can use to solve my issue with dhcp3 and bind, to add the clients to the bind file when they get a dhcp address. So you can ping a client from a different client based on the client-name??

---

### Post by Doug S on 2012-03-10
Forum readers need time to see your post and respond. No need to bump so quickly.
 
Shouldn't your option domain-name be "h4" instead of "intranet"?
 
What you are wanting to do works on one of my computers but not the rest, and I am trying to figure out why. (I do not know yet if it is the root issue, but the one it works on is new and still gets it's IP address from the pool, while the rest get their IP address based on MAC). I'll post back if I figure it out.

---

### Post by Doug S on 2012-03-11
I made my new computer get IP address based on MAC, and it still is able to do DNS lookups by just host name, not needing FQDN. One of the computers from yesterday now works by just host name also. I don't know what is different, but I did re-start eveything and I did delete my /var/lib/dhcp3/dhcpd.leases and leases~ files because they had legacy stuff that I wanted to get rid of. 
 
So now, it seems that only my main server itself, the one running dhcpd and dns, can not ping by abbreviated host name. The rest of the computers (includes two Ubuntu linux servers and some windows computers) can.
 
I do notice, via tcpdump, that the main server is forwarding the abbreviated name to upstream name servers, which of course doesn't work. I also notice that the other computers are sending a DNS request, but have filled out the FQDN in that request.

---

### Post by Drenriza on 2012-03-16
Hi Doug.
 
Thanks for your time. I have figured out how to dynamically update my forward and reversed lookup zones, and everything is working handy dandy.

---

