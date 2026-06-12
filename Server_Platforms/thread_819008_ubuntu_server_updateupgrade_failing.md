---
title: "ubuntu server update/upgrade failing"
date: 2008-06-04
forum: Server Platforms
---

### Post by kshuck2 on 2008-06-04
Hello,

I am currently running a webserver with Ubuntu Server 7.10.  
Everytime I try to do an update or upgrade (example: sudo apt-get update) it returns failure errors.

I have saved the errors in a txt file and you can view it here:
[http://shuckwebdesign.com/failure.txt](http://shuckwebdesign.com/failure.txt)

The only thing I can think is that my Firewall program is blocking it from connecting. (shuckwebdesign.com/firewall.txt)

I really need to do the updates so that I can be re-assured it is as secure as I am capable of. 

any help as to what i need to do is much appreciated! 

Thanks

---

### Post by uncannybuzzard on 2008-06-05
looks more like a DNS thing. can you resolve other FQDNs? also, what's the output of ```
iptables -L
```

---

### Post by kshuck2 on 2008-06-05
> **uncannybuzzard said:**
> looks more like a DNS thing. can you resolve other FQDNs? also, what's the output of ```
iptables -L
```

Thanks for the fast reply uncannybuzzard

here is what that the iptables -L returned:

```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
DROP       tcp  --  anywhere             anywhere            tcp dpt:ldap
DROP       tcp  --  anywhere             anywhere            tcp dpt:1002
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin
ACCEPT     0    --  anywhere             anywhere            state NEW
LOG        0    --  anywhere             anywhere            limit: avg 30/min burst 5 LOG level warning prefix `Dropping: '

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```





thanks

---

### Post by quelx on 2008-06-05
You need to open your firewall to allow DNS requests (and responses) and HTTP requests (and responses).  There is probably a more elegant way to do the HTTP(80) bit but this should get you started.  Change **xxx.xxx.xxx.xxx** with one of your known dns servers.

```

DNS="*xxx.xxx.xxx.xxx*"
$IPTABLES -A OUTPUT -d $DNS --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPTABLES -A INPUT -s $DNS --sport 53 -m state --state ESTABLISHED -j ACCEPT
$IPTABLES -A OUTPUT -p tcp -d $ANYWHERE --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPTABLES -A INPUT -s $ANYWHERE -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
```

---

### Post by kshuck2 on 2008-06-05
I forgot to mention the Firewall controls the iptables, the code for the firewall is in a txt file at:
[http://shuckwebdesign.com/firewall.txt](http://shuckwebdesign.com/firewall.txt)

a friend help me set up this firewall, but im not sure what i would need to change (possibly temporarily) to let me do the updates

---

### Post by kshuck2 on 2008-06-05
Thanks for your quick reply

how do i specify to allow more than one DNS

as far as i can tell technically it is looking in four different spots that i would need to allow:

[http://security.ubuntu.com](http://security.ubuntu.com)
[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 
security.ubuntu.com
us.archive.ubuntu.com 


thanks

---

### Post by kshuck2 on 2008-06-05
> **quelx said:**
> You need to open your firewall to allow DNS requests (and responses) and HTTP requests (and responses).  There is probably a more elegant way to do the HTTP(80) bit but this should get you started.  Change **xxx.xxx.xxx.xxx** with one of your known dns servers.

```

DNS="*xxx.xxx.xxx.xxx*"
$IPTABLES -A OUTPUT -d $DNS --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPTABLES -A INPUT -s $DNS --sport 53 -m state --state ESTABLISHED -j ACCEPT
$IPTABLES -A OUTPUT -p tcp -d $ANYWHERE --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPTABLES -A INPUT -s $ANYWHERE -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
```


actually I think i missread/missunderstood what you said
what would typically be used for DNS

---

### Post by quelx on 2008-06-05
> **kshuck2 said:**
> actually I think i missread/missunderstood what you said
what would typically be used for DNS

```
cat /etc/resolv.conf
``` on the server, use the ip address from one of the lines that read **nameserver xxx.xxx.xxx.xxx**

---

### Post by kshuck2 on 2008-06-05
I tried that and I'm still getting "failed to fetch" errors

I tried to disable my firewall, and the I restarted apache2
i tried iptables -L and it showed that all the "rules" were still enabled
I'm stumped.  Any more suggestions?

> **quelx said:**
> ```
cat /etc/resolv.conf
``` on the server, use the ip address from one of the lines that read **nameserver xxx.xxx.xxx.xxx**

---

### Post by quelx on 2008-06-05
This is quick and dirty, as I am not a firewall expert, if it were me I'd just trial and error, but I'll leave that to you (or some other helpful soul on the forum who can actually get DNS and HTTP working with your current set).

[COLOR="Red"]NOTE:[/COLOR]This will drop your firewall completely while you do you updates.

Backup your current rule set, make sure they are safe, and flush all the current rules
```
sudo iptables-save > /etc/iptables.20080605
sudo cat /etc/iptables.20080605
sudo iptables -F
``` 

do your updates

restore your rule set and check they are back in place
```
sudo iptables-restore < /etc/iptables.20080605
sudo iptables -L
```

---

### Post by kshuck2 on 2008-06-05
I tried doing this from my remote ssh
as soon as i commanded iptables -F  i was locked out completely
it defaulted to drop every connection.

although thats not what i wanted i found it amusing
i just rebooted and everything was back to normal.

> **quelx said:**
> This is quick and dirty, as I am not a firewall expert, if it were me I'd just trial and error, but I'll leave that to you (or some other helpful soul on the forum who can actually get DNS and HTTP working with your current set).

[COLOR="Red"]NOTE:[/COLOR]This will drop your firewall completely while you do you updates.

Backup your current rule set, make sure they are safe, and flush all the current rules
```
sudo iptables-save > /etc/iptables.20080605
sudo cat /etc/iptables.20080605
sudo iptables -F
``` 

do your updates

restore your rule set and check they are back in place
```
sudo iptables-restore < /etc/iptables.20080605
sudo iptables -L
```

---

### Post by kshuck2 on 2008-06-06
for now I cannot think of anything else to try,  tomorrow I'm going to setup a backup server using hardy, so i can take the gutsy server offline and play around with it more as to why it won't update. 

as for now, thanks for all the suggestions thus far

---

### Post by quelx on 2008-06-06
> I tried doing this from my remote ssh
as soon as i commanded iptables -F i was locked out completely
it defaulted to drop every connection.

That wasn't intentional :) .

Were you able to do the updates from the server console itself (headless?)?

I found this, [http://www.cyberciti.biz/faq/turn-on-turn-off-firewall-in-linux/](http://www.cyberciti.biz/faq/turn-on-turn-off-firewall-in-linux/), which may help with removing all the rules and allow completely open access.

If you put it all in a script and then ran it as root, you should be able to get it all done in one fell swoop.

```
#!/bin/bash
iptables-save > /etc/iptables.20080605
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
apt-get update
apt-get upgrade
iptables-restore < /etc/iptables.20080605
iptables -L
```

EDIT: actually this won't work, as soon as ssh disconnects the script will die too...  You don't happen to have **screen** already installed on the server?

---

### Post by kamaji792 on 2008-06-06
I am a noob when it comes to iptables but it is what I am playing with at the moment and I have the same problem.

You could remove all the rules one by one
```
iptables -D INPUT <num>
```
Where <num> is the number of the rule you want to remove.  The first rule is 1 (as listed by iptables -L).

I'd leave the first rule and the one for ssh and see if you can do the update then.

Now I show my noob credentials.  Apart form "ldap" and "1002" what is the firewall blocking.  Which then leaves the questing why is it stopping apt-get update.

Sorry this is a bit rambling - just done the iptables -F directly on my ubuntu box and apt-get update then worked fine.

As you were kind enough to show your set up - here is mine
```

# Generated by iptables-save v1.3.8 on Fri Jun  6 07:57:05 2008
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [348:45725]
-A INPUT -i lo -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p udp -m udp --dport 138 -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p udp -m udp --dport 137 -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 445 -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 139 -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 80 -j ACCEPT 
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7 
-A INPUT -j DROP 
COMMIT
# Completed on Fri Jun  6 07:57:05 2008

```
The above the output from "sudo iptables-save" and this does block apt-get.  I have not yet tried quelx's solutions.

All the best

---

### Post by kshuck2 on 2008-06-11
> **quelx said:**
> That wasn't intentional :) .

Were you able to do the updates from the server console itself (headless?)?

I found this, [http://www.cyberciti.biz/faq/turn-on-turn-off-firewall-in-linux/](http://www.cyberciti.biz/faq/turn-on-turn-off-firewall-in-linux/), which may help with removing all the rules and allow completely open access.

If you put it all in a script and then ran it as root, you should be able to get it all done in one fell swoop.

```
#!/bin/bash
iptables-save > /etc/iptables.20080605
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
apt-get update
apt-get upgrade
iptables-restore < /etc/iptables.20080605
iptables -L
```

EDIT: actually this won't work, as soon as ssh disconnects the script will die too...  You don't happen to have **screen** already installed on the server?




Due to lack of time I wont be able to try this until sometime this weekend,  but i have a thought. 
When I shutdown the iptables before, it defaulted to disable all connection requests.  I remember coming across something, maybe in a config file, that set the default to drop everything if nothing is specified to accept.

Whill this script still work?

---

### Post by kshuck2 on 2008-06-11
UPDATE:   ok, so I was playing around with my new hardy server, and came across the culpret to my update failure.  

I was able to do this by documenting ever step that I did.  The problem was the nameserver in the */etc/resolv.conf* file, I misunderstood how it works, and still dont understand.

I keep reading guides that say change the nameserver to the server's ip

nameserver xxx.xxx.xxx.xxx

so i was doing this, but as soon as i did this it blocked my outgoing connection, so i changed it back to the router ip and all is well, i also changed it on my gutsy server and was able to perform the update.

Could anyone explain what the nameserver actually does/is.

---

### Post by quelx on 2008-06-11
> **kshuck2 said:**
> 
Could anyone explain what the nameserver actually does/is.

It's akin to a phone book that translates common names (eg [www.ubuntu.com](www.ubuntu.com)) into ip addresses (91.189.94.249) which network hardware understands (routers, switches and the like) so your server wasn't able to get the IP of the update servers.

[http://people.csa.iisc.ernet.in/gaurav/np/rfcs/dns.html#section1](http://people.csa.iisc.ernet.in/gaurav/np/rfcs/dns.html#section1)

try ```
dig google.com
``` from the command line and then try ```
dig garbageaddress.garbage
``` and notice the **ANSWER:** bit.  Your server was getting no answer for it's requests.

PS. sorry for trying to break your firewall :)

---

### Post by kshuck2 on 2008-06-12
no harm done.

Thanks for helping me learn more, and realize I dont know it all yet....  ;)   lol

---

### Post by molotov00 on 2008-06-12
I have to clarify something. Entering the wrong nameserver doesn't "block" anything.

Nameservers resolve hostnames to IP addresses. It converts google.com to an IP, for example.

When you enter the wrong nameserver then your server is unable to determine IP addresses for all sites that are not stored in /etc/hosts

What you should take away from this is to no edit things unless you know what they are... I'm surprised it took you this long to realize that your server had virtually no access to the outside world.3

---

### Post by kshuck2 on 2008-06-12
> **molotov00 said:**
> I'm surprised it took you this long to realize that your server had virtually no access to the outside world.3

it never really mattered to me, i didnt try hitting the outside world unless doing updates (which failed, lol).  All I really cared about was that people could hit my server, and see my website.

thanks for the clarification though

> **molotov00 said:**
> What you should take away from this is to no edit things unless you know what they are... 

good advice, but screwing things up is half the fun in learning how to fix them ;)

---

