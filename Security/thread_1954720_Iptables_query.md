---
title: "Iptables query"
date: 2012-04-08
forum: Security
---

### Post by karan1337 on 2012-04-08
I was learning iptables and came across a tutorial.

Initially all rules are flushed using iptables -F

next, a rule:

iptables -A INPUT -p tcp --dport 80 -j ACCEPT was added to allow communication from port 80 via the tcp protocol 

The default policies for output is accept and for input and forward is drop.

Why isn't this enough for browsing the internet? My browser is able to make a request to any website, but keeps waiting for replies.


Whereas, i'm able to browse if i execute:-  iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


Why is the second command required even if the default output policy is set to accept?

Thanks in advance.

---

### Post by CharlesA on 2012-04-08
You shouldn't need that rule on the default configuration of iptables - it is set to allow everything in input, forwarding and output.

In any case, the input rule you posted, would allow access to whatever is running on port 80 on the machine in question, which is usually a web server.

---

### Post by darkod on 2012-04-08
I am no expert in web traffic, but I think your computer doesn't communicate only on port 80 for web. The traffic arrives to the web server at 80 but it doesn't mean it leaves your computer on 80 or that it comes back to 80.

I believe that is why it doesn't work until you ACCEPT the traffic established from your computer. Since you are establishing the www session from your computer, it accepts the reply regardless to what ever port it arrives to.

If you want to, setup logging for iptables and check the logs to confirm at what port(s) the traffic comes back at.

---

### Post by CharlesA on 2012-04-08
> **darkod said:**
> I am no expert in web traffic, but I think your computer doesn't communicate only on port 80 for web. The traffic arrives to the web server at 80 but it doesn't mean it leaves your computer on 80 or that it comes back to 80.

I believe that is why it doesn't work until you ACCEPT the traffic established from your computer. Since you are establishing the www session from your computer, it accepts the reply regardless to what ever port it arrives to.

If you want to, setup logging for iptables and check the logs to confirm at what port(s) the traffic comes back at.
Basically the OS sends packets from a random high-numbered port to the destination port of another machine - port 80 in this case, but it could be port 22 (ssh server) or port 443 (https).

In other words, your explanation is correct. ;)

The computer is trying to connect on port 80 and cannot.

---

### Post by darkod on 2012-04-08
I might be reading this wrong, but I don't understand your last sentence.
> The computer is trying to connect on port 80 and cannot.If I understand it right, the OP did:
1. Activated iptables.
2. Set the INPUT and FORWARD chains to DROP, the OUTPUT to ACCEPT.
3. Set only one single rule for the INPUT chain to accept port 80.

We are talking about his desktop computer. So the question is, why can't he browse unless he adds the rule about established traffic too. But we are talking here about the desktop computer, not the server side firewall.

The port 80 is for www sessions but on the server side, not on the client side.

So, from your desktop, you would establish a session with source port of 12345 for example, to destination port 80. Because your OUTPUT is allowed, the packet leaves. It reaches the web server at 80. But when the server sends the reply back to port 12345, you yourself are blocking this packet because you have DROP in your INPUT chain and only allow packets on port 80.

But adding the established traffic rule solves this because it will accept back any packets from your originating session.

Makes sense?

---

### Post by CharlesA on 2012-04-08
Aye, an established/related rule would fix the problem, for exactly the reason you said - the input table is blocking the returning traffic.

---

### Post by dontquoteme on 2012-04-08
I hope these help.  It's a guide to the top 25 rules to use with IPtables - to get you started in a safe manner.   We all start with copy and paste. :)

**[SIZE=2]25 Most Frequently Used Linux IPTables Rules Examples[/SIZE]**

[http://www.thegeekstuff.com/2011/06/iptables-rules-examples/](http://www.thegeekstuff.com/2011/06/iptables-rules-examples/)

In this article, I’ve given 25 practical IPTables rules that you can copy/paste.

Rule 6 applies:
**Allow Incoming HTTP and HTTPS**

iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

iptables -A INPUT -i eth0 -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT 

iptables -A OUTPUT -o eth0 -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT

---

### Post by darkod on 2012-04-08
> **dontquoteme said:**
> I hope these help.  It's a guide to the top 25 rules to use with IPtables - to get you started in a safe manner.   We all start with copy and paste. :)

**[SIZE=2]25 Most Frequently Used Linux IPTables Rules Examples[/SIZE]**

[http://www.thegeekstuff.com/2011/06/iptables-rules-examples/](http://www.thegeekstuff.com/2011/06/iptables-rules-examples/)

In this article, I’ve given 25 practical IPTables rules that you can copy/paste.

Rule 6 applies:
**Allow Incoming HTTP and HTTPS**

iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

iptables -A INPUT -i eth0 -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT 

iptables -A OUTPUT -o eth0 -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT

Are you sure these are not rules for the server side and not the client side?

As already mentioned, simply adding the established/related rule solves your problem for a desktop system.

---

### Post by CharlesA on 2012-04-08
> **darkod said:**
> Are you sure these are not rules for the server side and not the client side?

As already mentioned, simply adding the established/related rule solves your problem for a desktop system.
Yeah, those look like server-side rules to me.

---

### Post by dfreer on 2012-04-08
> **karan1337 said:**
> I was learning iptables and came across a tutorial.

Initially all rules are flushed using iptables -F


Note that the default policies for each chain is not reset using just this command. To set them you will want to run the following (replace ACCEPT with DROP as needed):
```
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
```

> **karan1337 said:**
> 
next, a rule:

iptables -A INPUT -p tcp --dport 80 -j ACCEPT was added to allow communication from port 80 via the tcp protocol 

The default policies for output is accept and for input and forward is drop.

Why isn't this enough for browsing the internet? My browser is able to make a request to any website, but keeps waiting for replies.


The rule you have listed only applies to incoming requests to port 80. This would be a rule you would use if you are allowing inbound traffic to your web server. Since you mentioned just being able to browse other webservers, this rule does absolutely nothing.

The key here is that you have the INPUT chain set to DROP, and OUTPUT chain set to ACCEPT. You are able to send out the initial packet to your DNS server, but are unable to receive a reply from it telling you the IP address of the webpage you have asked for. Same thing would apply if you manually navigated to an IP address, your outgoing packet would successfully hit their web server, but their replies would be dropped by your firewall. As you have mentioned:

> **karan1337 said:**
> 
Whereas, i'm able to browse if i execute:-  iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


Why is the second command required even if the default output policy is set to accept?

This command says to only accept incoming packets that have been "associated" with your outgoing packets. Specifically this is a stateful packet inspecting rule, that relies on a table that stores all of your ingoing/outgoing packet states.

This should be all you need for a basic workstation firewall, as you have no doubt discovered. It only allows incoming requests that are part of an outgoing request you have initiated. Since it only blocks incoming traffic, it is an ingress stateful firewall. 

A more complicated firewall would be an ingress/egress stateful firewall. Here's an example of one for a workstation:

```

#!/bin/bash

## I like to clear my firewall at the beginning of scripts.
## Setting default policies
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

## Clearing all rules
iptables -F

## Allowing loopback connections
iptables -P INPUT -i lo -j ACCEPT # -i for incoming interface
iptables -P OUTPUT -o lo -j ACCEPT # -o for outgoing interface

## Allow outgoing DNS requests.
## Most of your requests will be UDP. I doubt you will ever need TCP, but it's possible.
iptables -P OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
#iptables -P OUTPUT -p tcp --dport 53 --syn -m state --state NEW -j ACCEPT

## Allow outgoing HTTP and HTTPS requests.
iptables -P OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
iptables -P OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT

## Allow Pings outbound, but deny pings to us
iptables -P OUTPUT -p icmp --icmp-type echo-request -m state --state NEW -j ACCEPT

## Drop Invalid packets In/Out
iptables -P INPUT -m state --state INVALID -j DROP
iptables -P OUTPUT -m state --state INVALID -j DROP

## Allow subsequent established and related packets In/OUT
iptables -P INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -P OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Set Default Policy
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

```

---

### Post by karan1337 on 2012-04-09
@darkod @dfreer @CharlesA Thanks, it's a lot more clear to me now :)

@dontquoteme Thanks, i'll bookmark the link for use on servers.

---

### Post by bodhi.zazen on 2012-04-09
your web browser, firefox, uses a random port > 1024 to connect to port 80 on the server.

See [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

