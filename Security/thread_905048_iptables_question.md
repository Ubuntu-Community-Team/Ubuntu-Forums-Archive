---
title: "iptables question"
date: 2008-08-29
forum: Security
---

### Post by hey2222 on 2008-08-29
Hi, I'm working on iptables and I can't seem to get myself going. I've dropped everything, and enabled web traffic for mozilla.

#1 is this right?
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

#2 or is this right?
iptables -A INPUT -i eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

#3 or is all I have to do is this
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

Im not sure because Ive tryed all 3 and I cant access the web. Another question is once i flush what I have I still can't seem to get back on. I have to restart the computer each time to get back on. Is there anything I can do about that?

---

### Post by cariboo on 2008-08-30
Firefox doesn't use port 80 for outgoing connections have a look at this output:

```
tcp        0      0 intrepid.local:53463    cg-in-f99.google.co:www ESTABLISHED 6959/firefox 
```

As you can see from the above output of:

```
sudo netstat -put
```

There is no mention of port 80.

Jim

---

### Post by koenn on 2008-08-30
> **hey2222 said:**
> Hi, I'm working on iptables and I can't seem to get myself going. I've dropped everything, and enabled web traffic for mozilla.

#1 is this right?
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

#2 or is this right?
iptables -A INPUT -i eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

#3 or is all I have to do is this
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

Im not sure because Ive tryed all 3 and I cant access the web. Another question is once i flush what I have I still can't seem to get back on. I have to restart the computer each time to get back on. Is there anything I can do about that?

#2 is the right one, but you don't really have to match state on the OUTPUT, i.e. you can leave out '-m state --state NEW,ESTABLISHED'

you also have to allow DNS, and probably dhcp, for web access to work.
Probably, you also need to allow traffic on the loopback interface

flushing the rules doesn't change your default policies, i think. You probably set a default of reject or drop, so that's blocking your web access when you flush the rules

---

### Post by update_manager on 2008-08-31
> **hey2222 said:**
> Hi, I'm working on iptables and I can't seem to get myself going. I've dropped everything, and enabled web traffic for mozilla.

#1 is this right?
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

#2 or is this right?
iptables -A INPUT -i eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

#3 or is all I have to do is this
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

Im not sure because Ive tryed all 3 and I cant access the web. Another question is once i flush what I have I still can't seem to get back on. I have to restart the computer each time to get back on. Is there anything I can do about that?

You aren't letting out DNS. ;-)

I'd get rid of the port 80 restriction as some websites use other ports and instead use:


iptables -A OUTPUT -p udp -j ACCEPT

iptables -A OUTPUT -o eth0 -p tcp -m string --algo bm --string "<your user-agent-string>" -j ACCEPT

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


This assumes that your policies are
iptables -P INPUT DROP
iptables -P OUTPUT DROP


setting the policies from drop to accept will also keep from having you to reboot.

---

### Post by kevdog on 2008-09-02
Just a quick clarification


Do you only want to open the outbound firewall for programs with a source port destination of port 80 or port 443 (https)?  Do you need any other outgoing ports open??

Just for the record you might want to configure iptables similar to the following:

#!/bin/sh

IPTABLES=/sbin/iptables

$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT

$IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

exit
### EOF ### 

Just a suggestion -- If you are more clear on what you want, I can be more specific.  Notice however how the destination chain (OUTPUT) is being filter by the destination port.

---

