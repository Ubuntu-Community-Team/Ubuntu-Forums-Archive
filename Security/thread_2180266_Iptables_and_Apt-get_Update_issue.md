---
title: "Iptables and Apt-get Update issue"
date: 2013-10-12
forum: Security
---

### Post by jackbrennan2008 on 2013-10-12
Hi people.

I've had my webserver behind a NAT router for a long time and never really spent any time configuring the firewall (iptables) on the actual server. 
As i'm starting to use more and more Linux based servers i thought it was time i gave it a go.

So far everything is working extremely well except Apt-get Update which gets stuck at Security.Ubuntu.Com on either 99 or 100%, so i'm hoping someone can see the flaw in my IPtalbes rules and give me a leg up :).

Removing the ruleset will allow Apt-get Update to work properly again, so i must be missing a rule or have done something silly.

Thanks for any tips or help :)

Required ports:
HTTP:80
HTTPS:443
DNS:53
SMTP:25

```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [39:4968]
:fail2ban-ssh - [0:0]
-A INPUT -p tcp -m multiport --dports 22 -j fail2ban-ssh
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p udp -m udp --sport 53 -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 0 -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --sport 25 -m state --state ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

-A OUTPUT -o eth0 -p tcp -m tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT
-A OUTPUT -o eth0 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
-A OUTPUT -o eth0 -p tcp -m tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT
-A OUTPUT -o eth0 -p udp -m udp --dport 53 -j ACCEPT
-A OUTPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A OUTPUT -o eth0 -p tcp -m tcp --dport 25 -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
-A fail2ban-ssh -j RETURN
COMMIT
# Completed on Wed Oct  9 16:28:16 2013

```
[IMG]http://i24.photobucket.com/albums/c11/smakme7757/aptgetupdate_zps7fdc2780.png[/IMG]

---

### Post by Doug S on 2013-10-12
It seems likely to me that you need this line added to your OUTPUT rules set:```
-A OUTPUT -o eth0 -p tcp -m tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
```If that does not work, then I suggest to add a logging line as your last OUTPUT rule so that you can see the details of those 39 dropped packets. Here is my OUTPUT catch line, which if I have done my rule set properly, never gets hit:```
sudo iptables -A OUTPUT -s 0.0.0.0/0 -d 0.0.0.0/0 -j LOG --log-prefix "OCATCH:" --log-level info
```

---

### Post by jackbrennan2008 on 2013-10-12
Thanks very much :). We solved the problem!

It turned out it was a DNS problem. I had allowed DNS over UDP, but not TCP. Before i tried your HTTPS rule i enabled logging as you mentioned and it returned the following:

Sample:
```
Oct 12 17:15:16 webserver kernel: [13368.429600] OCATCH:IN= OUT=eth0 SRC=172.16.7.14 **DST=172.16.7.10** LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=26967 DF PROTO=TCP SPT=59199 DPT=53 WINDOW=14600 RES=0x00 SYN URGP=0
```

172.16.7.10 is my DNS, so it was clear that there was a problem with DNS. After a bit of pondering i looked at my ruleset and added the following:
```
iptables -A OUTPUT -p tcp -o eth0 --dport 53 -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --sport 53 -j ACCEPT
```

Essentially the same as i had for UDP, but with TCP and now everything seems to be in order.

Again thank you for pointing me in the right direction.

---

### Post by The Cog on 2013-10-12
I don't like this:
```
iptables -A OUTPUT -p tcp -o eth0 --dport 53 -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --sport 53 -j ACCEPT
```
It means that anyone can connect to any port on your server provided that they call from port 53 (or 22 or 80). 
Your server is wide open. Same is true for UDP.

I think I would ignore the source port on incoming rules, and only allow ESTABLISHED (i.e. responses to outgoing requests). 
Then allow incoming connections to specific destination ports for services that I want to make public.

---

### Post by Doug S on 2013-10-12
Glad you got it working. Adding logging can sure help with debugging issues.

Edit: Oh, and yes, The Cog is right. Although I think you mentioned that your server is behind NAT, so a little less of a worry, I suppose.

---

### Post by jackbrennan2008 on 2013-10-12
> **The Cog said:**
> I don't like this:
```
iptables -A OUTPUT -p tcp -o eth0 --dport 53 -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --sport 53 -j ACCEPT
```
It means that anyone can connect to any port on your server provided that they call from port 53 (or 22 or 80). 
Your server is wide open. Same is true for UDP.

I think I would ignore the source port on incoming rules, and only allow ESTABLISHED (i.e. responses to outgoing requests). 
Then allow incoming connections to specific destination ports for services that I want to make public.
Good points,

Like i mentioned above, I'm really just starting out, so bare with me :smile:.

With regards to your statement:
> I think I would ignore the  source port on incoming rules, and only allow ESTABLISHED (i.e.  responses to outgoing requests). 
Then allow incoming connections to specific destination ports for services that I want to make public.
Do you mean to create a single input rule which allows all established connections?

For example I would have the following input rule:
```
**iptables -A INPUT -p tcp -i eth0 -m state --state ESTABLISHED -j ACCEPT**
```

Then i could define output rules for ports i need to make contact with outside the server, like so:
```
iptables -A OUTPUT -p tcp -o eth0 --dport 53 -j ACCEPT
```

And then i would allow specific incoming ports on my webserver, HTTP, like so:
```
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
```


So that input rule (marked with stars) would be a generic rule for all incoming connections that have already been initiated from the server machine?

---

### Post by Doug S on 2013-10-12
yes, exactly. For example here is mine:```
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
```but note that I also allow RELATED and do not discriminate by protocol.
Just a small point. For this line:```
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
```it really only needs to be this:```
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW -j ACCEPT
```because your previous rule allows the established path.

---

### Post by CharlesA on 2013-10-12
I think Doug covered the majority of the iptables stuff, but I'll just leave this here...
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by jackbrennan2008 on 2013-10-12
> **Doug S said:**
> yes, exactly. For example here is mine:```
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
```but note that I also allow RELATED and do not discriminate by protocol.
Just a small point. For this line:```
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
```it really only needs to be this:```
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW -j ACCEPT
```because your previous rule allows the established path.
Ok, thanks for the feedback.

I'll fix up my rules tomorrow and see what else i can optimize. I really appreciate your feedback, you have been most helpful!

> **CharlesA said:**
> I think Doug covered the majority of the iptables stuff, but I'll just leave this here...
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)
Bookmarked. From a quick skim i'm pretty sure reading that will be worth my time :)

---

### Post by The Cog on 2013-10-13
Just a quick point. As far as I can tell, "--state NEW" simply means a connection the connection tracking engine hasn't seen before. For TCP, this could be any type of TCP packet, not necessarily the SYN that TCP uses to initiate a new connection. 
If you are being particular, iptables supports "-m tcp --syn" clause that specifically picks out packets that start a new TCP connection.

---

### Post by Doug S on 2013-10-13
> **The Cog said:**
> Just a quick point. As far as I can tell, "--state NEW" simply means a connection the connection tracking engine hasn't seen before. For TCP, this could be any type of TCP packet, not necessarily the SYN that TCP uses to initiate a new connection. 
If you are being particular, iptables supports "-m tcp --syn" clause that specifically picks out packets that start a new TCP connection.Another very good point. Additionally, and very often due to the half duplex close nature of TCP termination used in linux, "NEW" criteria also includes ones the connection tracking engine has seen before, but has forgotten about. Any good and complete rule set should check for a proper "NEW" connection. Below is a segment from my rule set:```
# A NEW TCP connection requires SYN bit set and FIN,RST,ACK reset.
# V1.02: Many packets here are due to forgotten connections. Try REJECT instead of DROP.
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level info
#$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j REJECT
```

---

### Post by jackbrennan2008 on 2013-10-13
> **The Cog said:**
> Just a quick point. As far as I can tell, "--state NEW" simply means a connection the connection tracking engine hasn't seen before. For TCP, this could be any type of TCP packet, not necessarily the SYN that TCP uses to initiate a new connection. 
If you are being particular, iptables supports "-m tcp --syn" clause that specifically picks out packets that start a new TCP connection.
I'm actually reading [Linux Firewalls]("http://www.amazon.com/Linux-Firewalls-Detection-Response-iptables/dp/1593271417/ref=sr_1_1?ie=UTF8&qid=1381686620&sr=8-1&keywords=Linux+Firewall") and they have just started touching on exactly this. I'm definitely going to look at implementing this into my rule set. So thank you for bringing that up. I must admit that i thought NEW was specifying the start of a completely new connection. However it seems that's not the case.

> **Doug S said:**
> Another very good point. Additionally, and very often due to the half duplex close nature of TCP termination used in linux, "NEW" criteria also includes ones the connection tracking engine has seen before, but has forgotten about. Any good and complete rule set should check for a proper "NEW" connection. Below is a segment from my rule set:```
# A NEW TCP connection requires SYN bit set and FIN,RST,ACK reset.
# V1.02: Many packets here are due to forgotten connections. Try REJECT instead of DROP.
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level info
#$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j REJECT
```

Thank you so much. I've made a copy of that and I'll have a look at it sometime during the week. My rule set is slowly getting better, but all good things take time and patience I guess :). Here i wasthinking i could fix it all in a single night...

 As mentioned above the book I'm reading is starting to get into this, so I'm going to have to use some time to digest it all, but I'll be sure to come back here if I have any more questions :)

All the help is truly appreciated!

---

