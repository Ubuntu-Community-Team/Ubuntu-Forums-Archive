---
title: "UFW blocks all outbound traffic on VPS"
date: 2010-02-18
forum: Security
---

### Post by JakeWins on 2010-02-18
I recently purchased a couple of Virtual Private Servers, and installed Ubuntu 9.10 server edition on them. I downloaded and installed the UFW firewall, something I've done without any problems many times before on non-virtual servers.

After setting up a few rules to allow VPN and SSH ports to be open, I enable the firewall, and get a message saying:

```
ERROR: problem running ufw-init
```

I can't find any logs for UFW, but running ufw status looks fine:

```

root@wally:~# ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
1194                       ALLOW       Anywhere

```

However, the firewall now also blocks any outbound connection. Ping times out, nslookup times out. Disabling UFW resolves the problem (but, of course, leaves me without a firewall).

I've never seen UFW block outbound connections by default before. I tried explicitly enabling outbound connections on the main network interface:

```

root@wally:~# ufw allow out on venet0
Rule added
root@wally:~# ufw reload
ERROR: problem running ufw-init
root@wally:~# ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
1194                       ALLOW       Anywhere

Anywhere                   ALLOW OUT   Anywhere on venet0

```

But this does not work, all outbound connections are dropped.

Does anyone have any tips for how to debug this?

---

### Post by gaspo100 on 2010-02-18
I have exactly the same problem with 9.10 server on VPS running under SolusVM. I tried 
```
ufw default allow outgoing
```iptables -L shows correct setting for the outgoing connections, but it still nothing gets out.

---

### Post by JakeWins on 2010-02-18
I'm playing around with this now. It appears that the iptable chain OUTPUT has no effect on outgoing connections, however, if I allow full pass through the INPUT chain, outgoing connections are let through.

Case in point:

```
root@wally:/var/log# nslookup google.com
;; connection timed out; no servers could be reached

root@wally:/var/log# iptables -P INPUT ACCEPT
root@wally:/var/log# nslookup google.com
Server:		4.2.2.1
Address:	4.2.2.1#53

Non-authoritative answer:
Name:	google.com
Address: 72.14.204.103
Name:	google.com
Address: 72.14.204.104
Name:	google.com
Address: 72.14.204.147
Name:	google.com
Address: 72.14.204.99

root@wally:/var/log#
```

---

### Post by JakeWins on 2010-02-18
I think I solved it. It appears that UFW does not properly add rules to accept incoming connections that were intitated by the local server.

To resolve:

```

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# UFW seems to neglect adding rules allowing local connections to:
iptables -A INPUT -i lo -j ACCEPT

```

This will, I believe, be undone anytime UFW is run. I have no clue why it behaves like this, but assume the error that it prints every now and then, "ERROR: problem running ufw-init" has something to do with it.

Edit: Nevermind, it seems restarting UFW does not undo these rules. I guess UFW only tampers with it's own chains, and since this is added straight into the INPUT chain, UFW leaves it be :)

---

### Post by bodhi.zazen on 2010-02-18
IMO, if you are running Virtualization, it is best to learn to use iptables directly.

GUFW, UFW, Firestarter, all will either fail or need to be reconfigured. By the time you re configure the tool you could be up and running with iptables.

You should also learn NAT ;)

---

### Post by JakeWins on 2010-02-18
> **bodhi.zazen said:**
> IMO, if you are running Virtualization, it is best to learn to use iptables directly.

GUFW, UFW, Firestarter, all will either fail or need to be reconfigured. By the time you re configure the tool you could be up and running with iptables.

You should also learn NAT ;)

I have had a very rude awakening today as to the differences in real vs. virtual servers, both in this area as well as in memory/swap/virtual memory kinks. 

At least I finally got myself started using iptables :)

---

### Post by bodhi.zazen on 2010-02-18
> **JakeWins said:**
> At least I finally got myself started using iptables :)

That will pay off for you in spades =)

---

### Post by myna on 2011-04-12
Where exactly do you put those commands so that they happen on every boot? i ask because i am assuming that there is no point in putting them in ufw-before, right?

---

### Post by bodhi.zazen on 2011-04-12
Assuming you are using iptables, you first set up your rules, then you use iptables-save and iptables-restore

You can use any number of techniques to activate the rules at boot, anything from calling iptables-restore in /etc/rc.local to adding it to your network scripts (see "post-up" ).

---

### Post by dfreer on 2011-04-12
BTW, if you ever do want to play with iptables directly, this script has a great beginning ingress/egress stateful firewall.

```
#!/bin/bash

## Clean out current iptables rules
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F

## DNS Outgoing (needed to access websites)
iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT

## HTTP Outgoing (needed to access websites)
iptables -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT

## Let all related connections in
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Let all related connections out
iptables -A OUTPUT -m state --state INVALID -j DROP
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Set Default Policy
iptables -P INPUT DROP
iptables -P OUTPUT DROP
```

Basically locks your machine down completely, only allows outgoing DNS lookups and HTTP requests.

---

### Post by bodhi.zazen on 2011-04-12
> **dfreer said:**
> Basically locks your machine down completely, only allows outgoing DNS lookups and HTTP requests.

Well, port 80 at least, which by default is http, but in theory one could just at well run a ssh server on port 80 ;)

---

