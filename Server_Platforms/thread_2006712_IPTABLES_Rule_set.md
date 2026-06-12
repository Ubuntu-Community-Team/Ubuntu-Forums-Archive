---
title: "IPTABLES Rule set"
date: 2012-06-19
forum: Server Platforms
---

### Post by brent1975 on 2012-06-19
Hello, I have a question, This is probably an easy one for someone who works with IPtables all the time. Here is the rules that I currently have in place. If I want to add a rule set above the one marked in Red how would I go about doing so? I want to allow port 3128 to the server.  How would I trigger the location  on -A INPUT -p tcp -m tcp --dport 3128 -j ACCEPT

-Also Does my rule set look okay? I was wondering about the first rule set should that be in there?

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
[COLOR=Red]ACCEPT     all  --  anywhere             anywhere[/COLOR]
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:4444
ACCEPT     tcp  --  anywhere             anywhere             tcp dpts:netbios-ns:netbios-ssn
ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-ns
ACCEPT     udp  --  anywhere             anywhere             udp dpt:9987
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:10011
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:30033
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:49152
[COLOR=Red]DROP       all  --  anywhere             anywhere[/COLOR]

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by darkod on 2012-06-19
If I am not mistaken, that first rule marked in red, ACCEPT all would allow all traffic regardless if the other rules. The rules are executed one by one, top to bottom, until one is fulfilled.

Since the ACCEPT All will allow all packets, the other rules are not even queried.

Also, if you look at the policies for both the INPUT and FORWARD chains, they are both ACCEPT. It's like you don't even have a firewall, you allow everything right now!

As for the order of the rules, how are you loading them at boot, using iptables-restore for example or another method?

---

### Post by The Cog on 2012-06-19
You can use -I (insert) rather than -A (append) to insert a rule at the start:
```
iptables -I INPUT -p tcp -m tcp --dport 3128 -j ACCEPT
```
The line that looks like it allows everything almost certainly only does so for the loopback port, so that applications on loclhost can commuicate with each other. Without this clause, lots of things (like printing) break. Use the -v flag to get the in/out interface listed as well:
```
iptables -n -v -L
```

---

### Post by SeijiSensei on 2012-06-19
> **darkod said:**
> If I am not mistaken, that first rule marked in red, ACCEPT all would allow all traffic regardless if the other rules.

We can't know that for sure unless he lists the rules with "iptables -nv -L" as The Cog suggests.  Without the verbose switch turned on, we don't see the interfaces to which the rules apply.  Suppose, for instance, the first rule is the common:

```
/sbin/iptables -A INPUT -i lo -j ACCEPT
```

allowing all traffic on the localhost interface.  That rule won't match traffic arriving on, say, eth0, so later rules would apply.  However you'll see that rule listed as 

```
ACCEPT all -- anywhere anywhere
```

if you don't use "iptables -L -v".  (The -n switch reports IP addresses instead of hostnames.  It's faster than running without -n since the application won't have to do DNS lookups to resolve all the IP addresses into names.)

---

### Post by darkod on 2012-06-19
> **SeijiSensei said:**
> We can't know that for sure unless he lists the rules with "iptables -nv -L" as The Cog suggests.  Without the verbose switch turned on, we don't see the interfaces to which the rules apply.  Suppose, for instance, the first rule is the common:

```
/sbin/iptables -A INPUT -i lo -j ACCEPT
```allowing all traffic on the localhost interface.  That rule won't match traffic arriving on, say, eth0, so later rules would apply.  However you'll see that rule listed as 

```
ACCEPT all -- anywhere anywhere
```if you don't use "iptables -L -v".  (The -n switch reports IP addresses instead of hostnames.  It's faster than running without -n since the application won't have to do DNS lookups to resolve all the IP addresses into names.)

Point taken and learned, thanks.

---

### Post by brent1975 on 2012-06-19
> **darkod said:**
> If I am not mistaken, that first rule marked in red, ACCEPT all would allow all traffic regardless if the other rules. The rules are executed one by one, top to bottom, until one is fulfilled.

Since the ACCEPT All will allow all packets, the other rules are not even queried.

Also, if you look at the policies for both the INPUT and FORWARD chains, they are both ACCEPT. It's like you don't even have a firewall, you allow everything right now!

As for the order of the rules, how are you loading them at boot, using iptables-restore for example or another method?


under /etc/network/interfaces I have

pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules

---

### Post by brent1975 on 2012-06-19
> **The Cog said:**
> You can use -I (insert) rather than -A (append) to insert a rule at the start:
```
iptables -I INPUT -p tcp -m tcp --dport 3128 -j ACCEPT
```The line that looks like it allows everything almost certainly only does so for the loopback port, so that applications on loclhost can commuicate with each other. Without this clause, lots of things (like printing) break. Use the -v flag to get the in/out interface listed as well:
```
iptables -n -v -L
```

iptables -n -v -L

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
   24  1200 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0   
10937   15M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    3   180 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:4444
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpts:137:139
  141 12114 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:9987
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:10011
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:30033
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:49152
  135 18402 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0   

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 6171 packets, 431K bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by darkod on 2012-06-19
It depends how you want to set up your firewall, but if I'm not mistaken the general rule is that you set DROP policy to both INPUT and FORWARD, and then only allow the traffic you want to.

In your /etc/iptables.rules you seem to have ACCEPT for both of them.

It should look something like:
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

That would block all packages in the INPUT and FORWARD chains except the ones you explicitly allow in /etc/iptables.rules.

---

### Post by brent1975 on 2012-06-19
> **SeijiSensei said:**
> We can't know that for sure unless he lists the rules with "iptables -nv -L" as The Cog suggests.  Without the verbose switch turned on, we don't see the interfaces to which the rules apply.  Suppose, for instance, the first rule is the common:

```
/sbin/iptables -A INPUT -i lo -j ACCEPT
```allowing all traffic on the localhost interface.  That rule won't match traffic arriving on, say, eth0, so later rules would apply.  However you'll see that rule listed as 

```
ACCEPT all -- anywhere anywhere
```if you don't use "iptables -L -v".  (The -n switch reports IP addresses instead of hostnames.  It's faster than running without -n since the application won't have to do DNS lookups to resolve all the IP addresses into names.)

here is iptables -nv -L 

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
   28  1400 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0   
11205   15M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    3   180 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:4444
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpts:137:139
  152 13020 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:9987
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:10011
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:30033
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:49152
  151 20378 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0   

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 7096 packets, 565K bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by The Cog on 2012-06-20
> **brent1975 said:**
> under /etc/network/interfaces I have

pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules

This is saving the current iptables rules as the machine shuts down, and reloading them as the machine starts up again.

Another way of editing the rules is to edit the file /etc/iptables.rules (the syntax is quite easy) and then use this command to load the revised rules:```
iptables-restore < /etc/iptables.rules
```

Does that answer everything, or are there outstanding questions? Somehow I get the feeling you're still looking for an answer to something but I can't tell what.

---

### Post by brent1975 on 2012-06-20
> **The Cog said:**
> This is saving the current iptables rules as the machine shuts down, and reloading them as the machine starts up again.

Another way of editing the rules is to edit the file /etc/iptables.rules (the syntax is quite easy) and then use this command to load the revised rules:```
iptables-restore < /etc/iptables.rules
```Does that answer everything, or are there outstanding questions? Somehow I get the feeling you're still looking for an answer to something but I can't tell what.

Thanks The Cog, So are my tables good? Do I need to remove the first entry that is in red?

Thanks

---

### Post by spynappels on 2012-06-20
> **darkod said:**
> It depends how you want to set up your firewall, but if I'm not mistaken the general rule is that you set DROP policy to both INPUT and FORWARD, and then only allow the traffic you want to.

In your /etc/iptables.rules you seem to have ACCEPT for both of them.

It should look something like:
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

That would block all packages in the INPUT and FORWARD chains except the ones you explicitly allow in /etc/iptables.rules.

This is fine for a server you have local access to and the option of connecting a keyboard and monitor to, but for a remote server, there is a chance that messing with the rules might completely lock you out.

For a remote server, or one which it is difficult to connect a keyboard and mouse to, it is normally better to leave the defaults to ACCEPT and put the last rule in the chain to drop everything, which the OP has. 


To the OP:  Your rules look fine, but you have not added the port 3128 (proxy server?) rule, did you still want to?

---

### Post by darkod on 2012-06-20
> **spynappels said:**
> This is fine for a server you have local access to and the option of connecting a keyboard and monitor to, but for a remote server, there is a chance that messing with the rules might completely lock you out.

For a remote server, or one which it is difficult to connect a keyboard and mouse to, it is normally better to leave the defaults to ACCEPT and put the last rule in the chain to drop everything, which the OP has. 


And what is the difference with this? I thought the DROP is the norm.

If you have a correct rule for your SSH access, it would allow you in.
If you don't have a correct rule for the SSH, it would still kick you out with the DROP All rule at the end.

So, having the policy at ACCEPT on first look looks only as security risk, not as any help since without correct SSH rule you get kicked out anyway.

---

### Post by spynappels on 2012-06-20
> **darkod said:**
> And what is the difference with this? I thought the DROP is the norm.

If you have a correct rule for your SSH access, it would allow you in.
If you don't have a correct rule for the SSH, it would still kick you out with the DROP All rule at the end.

So, having the policy at ACCEPT on first look looks only as security risk, not as any help since without correct SSH rule you get kicked out anyway.

At first sight, yes, but the problem occurs when the rule set is not loaded correctly during a configuration or for some other reason and the rules are flushed and the only rule which applies is the default DROP. Then you're locked out and without some Out-of-Band access you cannot get back in.

It has happened to many of us on here, and with a default ALLOW policy, this is avoided.

---

### Post by brent1975 on 2012-06-20
So is my current config good then?

---

### Post by SeijiSensei on 2012-06-20
> **brent1975 said:**
> So is my current config good then?

Well, it's hard to say since I don't know what those services are that are listening on high ports like 4444 or 30333.  I presume you know what they are and that they should be permitted.  Otherwise it looks fine.  Just add that squid rule for port 3128 somewhere above the default DENY rule at the bottom of the INPUT chain.

[quote=spynappels]It has happened to many of us on here, and with a default ALLOW policy, this is avoided.[/quote]

Yup, been there, done that.  It's no fun.  I avoid the problem of being locked out by having rules that grant unlimited access from my client IP addresses right after the ESTABLISHED rule.

---

### Post by brent1975 on 2012-06-20
> **SeijiSensei said:**
> Well, it's hard to say since I don't know what those services are that are listening on high ports like 4444 or 30333.  I presume you know what they are and that they should be permitted.  Otherwise it looks fine.  Just add that squid rule for port 3128 somewhere above the default DENY rule at the bottom of the INPUT chain.



Yup, been there, done that.  It's no fun.  I avoid the problem of being locked out by having rules that grant unlimited access from my client IP addresses right after the ESTABLISHED rule.

4444 is for the sockso media streaming server. 
30333 is for my sons Team Speak Server for a game he plays.

Thank you very much.

---

