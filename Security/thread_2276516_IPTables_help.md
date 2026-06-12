---
title: "IPTables help"
date: 2015-05-03
forum: Security
---

### Post by samer4 on 2015-05-03
Hi guys, this my first time using iptables and I already have the rules that I will use but I am trying to put those rules in a table for a presentation. 

An example of the table is

[https://www.usenix.org/legacy/event/lisa07/tech/full_papers/tran/tran_html/=01.ehab.figure7.gif](https://www.usenix.org/legacy/event/lisa07/tech/full_papers/tran/tran_html/=01.ehab.figure7.gif)

My rules are

 
iptables –F                            
           
**Whitelisting**
iptables -P INPUT DROP                  
iptables -P FORWARD DROP
iptables –P OUTPUT DROP
 
 
iptables –L –n           
 
**Allow HTTP & SSH**
iptables –A INPUT –p tcp --dport ssh –j ACCEPT
 
iptables _A INPUT  -p tcp  --dport 80 –j ACCEPT    new, established
src webserver sport 80 established 
 
**Allow Ping from Inside to Outside**
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT        
iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -s 10.1.10.0/24 --dport 3306 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 3306 -m state --state ESTABLISHED -j ACCEPT
 
source webserver and pool ip addresses 
 
**Allow DNS**
iptables -A OUTPUT -p udp -o eth0 --dport 53 -j ACCEPT     
iptables -A INPUT -p udp -i eth0 --sport 53 -j ACCEPT
 
**Prevent DOS attack/ Password guessing**
iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT
 
**To prevent port scanning **
iptables -N port-scan
 
**Allow traffic for established connections**
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
 
**iptables-save > /etc/sysconfig/iptables**
 
And I have this so far

[TABLE]
[TR]
[TD]Order
[/TD]
[TD]Protocol
[/TD]
[TD]SrcIP
[/TD]
[TD]SrcPort
[/TD]
[TD]DestIP
[/TD]
[TD]DestPort
[/TD]
[TD]Action
[/TD]
[/TR]
[TR]
[TD]1
[/TD]
[TD]TCP
[/TD]
[TD] 
[/TD]
[TD]*
[/TD]
[TD] 
[/TD]
[TD]SSH
[/TD]
[TD]Accept
[/TD]
[/TR]
[TR]
[TD]2
[/TD]
[TD]TCP
[/TD]
[TD]*
[/TD]
[TD]*
[/TD]
[TD]webserver
[/TD]
[TD]80
[/TD]
[TD]Accept
[/TD]
[/TR]
[TR]
[TD]3
[/TD]
[TD]ICMP
[/TD]
[TD] 
[/TD]
[TD]*
[/TD]
[TD]Webserver
[/TD]
[TD] 
[/TD]
[TD]Accept
[/TD]
[/TR]
[TR]
[TD]4
[/TD]
[TD]ICMP
[/TD]
[TD] 
[/TD]
[TD]*
[/TD]
[TD] 
[/TD]
[TD] 
[/TD]
[TD]Accept
[/TD]
[/TR]
[TR]
[TD]5
[/TD]
[TD]UDP
[/TD]
[TD]Eth0
[/TD]
[TD]*
[/TD]
[TD] 
[/TD]
[TD]53
[/TD]
[TD]Accept
[/TD]
[/TR]
[TR]
[TD]6
[/TD]
[TD]UDP
[/TD]
[TD]Eth0
[/TD]
[TD]*
[/TD]
[TD] 
[/TD]
[TD]53
[/TD]
[TD]Accept
[/TD]
[/TR]
[TR]
[TD]7
[/TD]
[TD]TCP
[/TD]
[TD] 
[/TD]
[TD]*
[/TD]
[TD] 
[/TD]
[TD]80
[/TD]
[TD]Accept
[/TD]
[/TR]
[/TABLE]
 
Am I on the right track or not even close?

---

### Post by SeijiSensei on 2015-05-03
A couple of quick observations:

1) Add this rule above the SSH rule
```
/sbin/iptables -A INPUT -i lo -j ACCEPT
```
and move the ESTABLISHED,RELATED rule right below it.  Traffic on the localhost interface and reply traffic should be accepted ahead of any further rules.

2) As far I as know, this rule does nothing other than defining another table called "port-scan:"
```
iptables -N port-scan
```
Normally you would have rules that forward traffic along to the ruleset contained in port-scan.  For instance, I have a table called SPAM which is the target of another rule handling inbound SMTP connections.  The SPAM table consists of IP addresses I wish to block because of repeated spamming.  This arrangement lets me update the SPAM table's address list independently of the rest of the iptables ruleset.  So you would need a set of rules in the port-scan table to block scanning activity.  Frankly I don't care about being scanned.  I only permit traffic to the services I offer and block everything else.

---

### Post by samer4 on 2015-05-03
> **SeijiSensei said:**
> A couple of quick observations:

1) Add this rule above the SSH rule
```
/sbin/iptables -A INPUT -i lo -j ACCEPT
```
and move the ESTABLISHED,RELATED rule right below it.  Traffic on the localhost interface and reply traffic should be accepted ahead of any further rules.

2) As far I as know, this rule does nothing other than defining another table called "port-scan:"
```
iptables -N port-scan
```
Normally you would have rules that forward traffic along to the ruleset contained in port-scan.  For instance, I have a table called SPAM which is the target of another rule handling inbound SMTP connections.  The SPAM table consists of IP addresses I wish to block because of repeated spamming.  This arrangement lets me update the SPAM table's address list independently of the rest of the iptables ruleset.  So you would need a set of rules in the port-scan table to block scanning activity.  Frankly I don't care about being scanned.  I only permit traffic to the services I offer and block everything else.

Thanks for the reply I will add this to my rules but what about the table?

I need to put my rules into a table just like this one -->> [https://www.usenix.org/legacy/event/lisa07/tech/full_papers/tran/tran_html/=01.ehab.figure7.gif](https://www.usenix.org/legacy/event/lisa07/tech/full_papers/tran/tran_html/=01.ehab.figure7.gif)

---

### Post by SeijiSensei on 2015-05-03
> **samer4 said:**
> I need to put my rules into a table just like this one -->> [https://www.usenix.org/legacy/event/lisa07/tech/full_papers/tran/tran_html/=01.ehab.figure7.gif](https://www.usenix.org/legacy/event/lisa07/tech/full_papers/tran/tran_html/=01.ehab.figure7.gif)

That looks to be the result of manually entering the rules into a spreadsheet.  Maybe there's some GUI interface to iptables that will do that.  I only use the command-line for iptables.

---

