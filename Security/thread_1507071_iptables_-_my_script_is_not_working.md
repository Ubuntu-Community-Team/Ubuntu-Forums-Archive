---
title: "iptables - my script is not working"
date: 2010-06-11
forum: Security
---

### Post by chihwahli on 2010-06-11
I see many threads / websites about how to configure iptables. They say if you use these
rules it will allow http traffic. But they don't work. I like to deny all then allow specific ports open for traffic.

So far I tried the script to flush and update my iptables rules, trying to open port 80 and 53 for http and DNS  traffic:
(I made the script executable, with $ iptables -L -v I can see that the rules are changed after I run the script. )

```

#! /bin/bash

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

iptables -A INPUT -p tcp --sport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --sport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

``` What is the minimal required  to let me use port 80 and 53. I still like to use the drop all policy and specify what to allow  :confused:

---

### Post by The Cog on 2010-06-11
Almost there. But DNS uses UDP, not TCP. I think that's your problem.

It might be better to only allow incoming packets on existing connections rather than allow any connection coming from port 80, like this:> iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPTOtherwise someone can make new incoming connections to any service on your PC by using a source port of 80.

I would also have the script clear any existing rules before entering the new ones. 

And you should let the computer talk to itself or strange things (like printing) break. So maybe something like this:
```
! /bin/sh
iptables -F
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -d localhost -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables  -A INPUT -i lo -j ACCEPT

```

---

### Post by chihwahli on 2010-06-11
Thanks!  That helped! I did not know I had to specify UDP instead of TCP, I thought
TCP would cover everthing. I can internet now.

I added a few extra lines to drop anything I did not got ACCEPTED. This should drop all packets that I do not like to go out and in.

! /bin/sh
iptables -F
iptables -X
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -d localhost -j ACCEPT
iptables  -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


iptables -A INPUT -j DROP
iptables -A OUTPUT -jDROP
iptables -A FORWARD -j DROP

But the funny thing is, an online scanner said my port 23 is open (responding). 
How can this be?

---

### Post by The Cog on 2010-06-11
Aargh! I missed out setting the policies to DROP! Stupid stupid stupid! Well spotted you.

Do you have a router? If so, it's probably the router that has port 23 open. That's not clever and you should investigate further.

The command **netstat -lnt** will show what TCP ports your PC is listening on. 23 should **not** be listed.

---

### Post by technick on 2010-06-11
Just to make sure I understand your request, you want to filter both inbound (to your machine) and outbound (from your machine to the network and internet) traffic?

---

### Post by chihwahli on 2010-06-12
@ The Cog: Humans do make small mistakes now and then. Perfection is not found in us. 
    We learn every day. Still thanks for helping out! 

@ Technick: I am trying to make it more and more secure

I made an improvement, by not allowing every incoming request at a port. Now it will check if I made an outgoing request already --> established, related, etc
I added ports for pop email, https, ftp passive ability.
I found a script line about allowing passive FTP traffic, after that I copied the line towards my other lines (http, etc) worksd with most , some don't...slowly understanding what everythin means. If anyone know another improvement. Let me know..
I am reading some iptables html..... lot's of pages!!! 


#! /bin/bash
# Flush chains en delete non-standaard chains.
iptables -F
iptables -X
# Drop well known port scans
iptables -A INPUT -p tcp --tcp-flag ALL NONE -j DROP
iptables -A INPUT -p tcp --tcp-flag ALL ALL -j DROP
iptables -A INPUT -p tcp --tcp-flag SYN,FIN SYN,FIN -j DROP
# Allow HTTP traffic
iptables -A INPUT -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --sport 80 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
# Allow DNS traffic
iptables -A INPUT -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
#iptables -A OUTPUT -p tcp --dport 53 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
# Allow FTP @ port 21
iptables -A INPUT  -p tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
# Allow Passive FTP connection
iptables -A INPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow Pop / SMTP traffic
iptables -A INPUT -p tcp --sport 110 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 110 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --sport 25 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 25 -m state --state NEW,ESTABLISHED -j ACCEPT
# Allow https traffic
iptables -A INPUT -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
# Allow Local communication
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
# Policy: Drop any remaining traffic that is not defined in my allow list.
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP
iptables -A OUTPUT -j DROP

# After updating the UFW rules, show the rules on screen, and any errors.
iptables -n -L

---

