---
title: "quirky iptables setup"
date: 2009-02-25
forum: Security
---

### Post by jonallport on 2009-02-25
Hi all,

I didn't know whether this was 'security' or 'networking', but here goes.

I have a chillispot captive portal setup with ubuntu (8.04 server).  The 'external' interface is on the 'office' network and 'guests' connect via wifi APs on the 'internal' interface.

Obviously, once authenticated, the guests can see the office network and I need to stop this.  Can iptables deny access to an address range (say 192.168.1.0/24) on the external interface but permit routing via (say) 192.168.1.1 (the router to the real world).

If so, how?  I'm afraid this may be a big ask, but I'm not too familiar with iptables rules other than 'allow/deny incoming/outgoing on port xx'

Unfortunately, at the moment, physically separating the networks is not possible although that would be my preferred solution.

Many, many thanks in advance.
Jon :^)

---

### Post by bodhi.zazen on 2009-02-25
iptables -A INPUT -s 192.168.1.0/16 -d 192.168.1.1 -j DROP

iptables -A OUTPUT -s 192.168.1.1 -d 192.168.1.0 -j DROP

Of course order counts , so you may need to insert those rules earlier.

Your other option is to use Shorewall or guarddog, both should be able to do this for you.

---

### Post by jonallport on 2009-03-04
Thanks to bodhi.zazen for the quick reply.

I finally got around to trying it.  What I ended up with was the following, 90% standard chilli.iptables, one rule added:

```

#!/bin/sh
#
# Firewall script for ChilliSpot
# A Wireless LAN Access Point Controller
#
# Uses $EXTIF (eth0) as the external interface (Internet or intranet) and
# $INTIF (eth1) as the internal interface (access points).
#
#
# SUMMARY
# * All connections originating from chilli are allowed.
# * Only ssh is allowed in on external interface.
# * Nothing is allowed in on internal interface.
# * Forwarding is allowed to and from the external interface, but disallowed
#   to and from the internal interface.
# * NAT is enabled on the external interface.

IPTABLES="/sbin/iptables"
EXTIF="eth0"
INTIF="eth1"

$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT

#Allow related and established on all interfaces (input)
$IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

#Allow releated, established and ssh on $EXTIF. Reject everything else.
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 --syn -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -j REJECT

#Drop connections for network 'just outside'
$IPTABLES -A OUTPUT -s 192.168.182.0/24 -d 80.213.74.168/29 -j DROP
$IPTABLES -A INPUT -s 80.213.74.168/29 -d 192.168.182.0/24 -j DROP

#Allow related and established from $INTIF. Drop everything else.
$IPTABLES -A INPUT -i $INTIF -j DROP

#Allow http and https on other interfaces (input).
#This is only needed if authentication server is on same server as chilli
$IPTABLES -A INPUT -p tcp -m tcp --dport 80 --syn -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 443 --syn -j ACCEPT

#Allow 3990 on other interfaces (input).
$IPTABLES -A INPUT -p tcp -m tcp --dport 3990 --syn -j ACCEPT

#Allow everything on loopback interface.
$IPTABLES -A INPUT -i lo -j ACCEPT

# Drop everything to and from $INTIF (forward)
# This means that access points can only be managed from ChilliSpot
$IPTABLES -A FORWARD -i $INTIF -j DROP
$IPTABLES -A FORWARD -o $INTIF -j DROP

#Enable NAT on output device
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

```

You'll see that I want to drop connections from the network 'behind' the gateway bound for the network 'just in front of' it but not those heading for the internet via the router at 80.213.74.169, i.e. Internet access but no access to peers of the gateway.  I also want to allow incoming to the gateway for ssh management.

My addled brain can't get around it - please help.

Thanks

---

### Post by bodhi.zazen on 2009-03-04
I do not see any obvious mistakes either.

I find this command helps :

```
sudo iptables -L -v
```The -v flag is verbose, and shows "counts" or where packets are going (accepted or dropped).

You can reset the counters with -Z and watch your network traffic .

My guess would be the masquerade rule.

---

### Post by koenn on 2009-03-04
I'm having some trouble visualizing your network layout and have no idea what a chilispot is, but if I understand correctly, the WLAN hosts connect through the INTIF and need forwarding towards the internet (through the office network ?). Yet you're blocking exactly that, with
```
$IPTABLES -A FORWARD -i $INTIF -j DROP
$IPTABLES -A FORWARD -o $INTIF -j DROP
```

You probably have to split that up in a number of src/dest combinations, each with the appropriate -j target.



edit: It's also unclear to me why you need a masquerade rule.

---

### Post by HermanAB on 2009-03-04
Hmmm, iptables is always a puzzler.

Since the default rule for INPUT is DROP, I don't think this rule does anything:
$IPTABLES -A INPUT -s 80.213.74.168/29 -d 192.168.182.0/24 -j DROP

Cheers,

Herman

---

### Post by lensman3 on 2009-03-04
Change this line:

$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 --syn -j ACCEPT

TO:

$IPTABLES -A INPUT -m state --state NEW -p tcp --dport 22 -j ACCEPT

That way only "NEW" connections will be accepted and processed.  The "ESTABLISHED" line will take care of everything else.  I think that syn is the same as NEW in a TCP connection that is being established.

The other lines with --syn can be changed to "NEW".  They are new connections.  Let the ESTABLISHED line take care of the connection after that.

---

### Post by jonallport on 2009-03-09
OK,

Chiilispot ([www.chillispot.info](www.chillispot.info)) is a hotspot/captive portal gateway.  $EXTIF is on a public/internet facing network, $INTIF is the hotspot network.  Under normal circumstances a user will connect to the network on $INTIF (via switch or wifi AP), the first time they request a web-page (http or https) they are redirected to a login page and must enter a username/password / accept T&Cs etc. before anything other that their DNS requests will be allowed out of $EXTIF.  If the default policy was ACCEPT then thie captive portal would be of no value.

In the example I gave above, &EXTIF is a public interface, hence NAT.

What I want to do is drop any and all connections from the hostspot network (192.168.182.0/24) bound for peers of $EXTIF (80.213.74.168/29).

Thanks in advance

Jon

---

### Post by jonallport on 2009-03-09
Sorted!

I added:
$IPTABLES -A FORWARD -s 192.168.182.0/24 -d 80.213.74.168/29 -j DROP
to the FORWARD chain and all seems to be as I want it.

Thanks to those who looked, and especially those who replied.

Jon

---

