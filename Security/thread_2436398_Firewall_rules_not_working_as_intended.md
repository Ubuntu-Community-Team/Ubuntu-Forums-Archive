---
title: "Firewall rules not working as intended"
date: 2020-02-05
forum: Security
---

### Post by localgeek2 on 2020-02-05
I'm trying to use only UFW from now on, but I think that there may be some remnant rules in IPTABLES which are causing issues. Ideally, I'd like to reset those to default, but that didn't seem to work when I tried it, so if someone has a good help doc for that, I'd appreciate it.

Ubuntu 18.04

Below are my UFW and IPTABLES rules.


Here's the issue:
Although UFW explicitly DENIES port 943 traffic in, I can still access a web page on that port.


Any ideas?


ps- anything else you see in there which could come out, please feel free to point out.

```
[ UFW ] 
root@localhost:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
943                        DENY IN     Anywhere


************************************************************************


[ IPTABLES ] 
root@localhost:~# sudo iptables -S | less
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -j ufw-not-local
-A ufw-before-input -d 224.0.0.251/32 -p udp -m udp --dport 5353 -j ACCEPT
-A ufw-before-input -d 239.255.255.250/32 -p udp -m udp --dport 1900 -j ACCEPT
-A ufw-before-input -j ufw-user-input
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -j ufw-user-output
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] "
-A ufw-logging-deny -m conntrack --ctstate INVALID -m limit --limit 3/min --limit-burst 10 -j RETURN
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
-A ufw-skip-to-policy-forward -j DROP
-A ufw-skip-to-policy-input -j DROP
-A ufw-skip-to-policy-output -j ACCEPT
-A ufw-track-output -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-user-input -p tcp -m tcp --dport 22 -j ACCEPT
-A ufw-user-input -p udp -m udp --dport 22 -j ACCEPT
-A ufw-user-input -p udp -m udp --dport 80 -j ACCEPT
-A ufw-user-input -p udp -m udp --dport 443 -j ACCEPT
-A ufw-user-input -p tcp -m tcp --dport 943 -j DROP
-A ufw-user-input -p udp -m udp --dport 943 -j DROP
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable
-A ufw-user-limit-accept -j ACCEPT
```

---

### Post by wildmanne39 on 2020-02-05
Hello and welcome to the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by TheFu on 2020-02-06
I don't see any left over iptable rules.

The default rule is to deny all inbound new connections.   The specific rule for 943 isn't needed.  If the intent is also to block all outbound access, unless specifically allowed, you'll need more rules for that.

However, inbound rules don't impact when a program on the system accesses another system.  That opens a connection and allows the response.  That's kinda the entire point of connection tracking firewalls.

Not too important, but using sudo when already root is a waste.

---

### Post by Doug S on 2020-02-06
Your iptables rules listing seems incomplete, therefore we can not answer your question. Do this: "sudo iptables -v -x -n -L" and post it all, although I find ufw generated rule sets difficult to follow.

---

### Post by EuclideanCoffee on 2020-02-12
Whenever I have a problem with ufw rules, it is likely due to order. If you could please post your rules from the ufw stdout, that would be helpful in checking the order of your rules. Essentially, if you have a "accept all" rule at the bottom, it overrides rules at the top.

---

### Post by kevdog on 2020-02-13
> **Doug S said:**
> Your iptables rules listing seems incomplete, therefore we can not answer your question. Do this: "sudo iptables -v -x -n -L" and post it all, although I find ufw generated rule sets difficult to follow.

Second that.  ufw is usually easy to use, however if you ever have to do some serious debugging its a royal PITA to manually debug the iptables rulesets.

---

