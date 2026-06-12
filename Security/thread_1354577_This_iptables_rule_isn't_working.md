---
title: "This iptables rule isn't working"
date: 2009-12-14
forum: Security
---

### Post by FuturePilot on 2009-12-14
So someone keeps hitting my server quite frequently with what appears to be at best a suspicious request. 
```
88.80.10.1 - - [14/Dec/2009:00:40:46 -0500] "GET http://spam-chaos.com/pp/set-cookie.php HTTP/1.1" 400 469 "-" "-"
```

I adjusted some fail2ban settings and it caught it and banned the IP address. The ban was working as I wasn't getting any more of those requests. But I figured since fail2ban will end up unbanning it after the ban time expires I should make it permanent. So I used the exact same command that fail2ban used except I appended it to the INPUT chain and then removed the rule from fail2ban.
```
 sudo iptables -A INPUT -s 88.80.10.1/32 -j DROP
```

After I did this though I started getting that same request again! I've used a very similar rule for other IP address and it worked fine, so I don't understand what's going on here. I even went so far as to put that rule in my router but that didn't even work. So why isn't this blocking that IP address and why does it only work if fail2ban blocks it?

---

### Post by cdenley on 2009-12-14
1. Since the request results in a 400 error, it is probably harmless. They are trying to use you as a proxy, but they are sending an HTTP/1.1 request, and probably aren't providing a "Host" header.

2. Fail2ban only bans for a certain period of time for a reason. IP addresses aren't always static. It is possible, though very unlikely, that a legitimate user may end up with that IP and fail to connect to your site at some point in the future. Besides, if you are being targeted, the attacker would probably move on to a different proxy or compromised system to attack you from with a fresh IP. Are you sure the requests are coming from the same IP?

3. We can't help you with your iptables rules until you post them. You must be accepting the requests before it reaches that rule.
```

sudo iptables -L -n

```

---

### Post by bodhi.zazen on 2009-12-14
Keep in mind, order of your rules is critical. So my guess is that an earlier rule is accepting traffic.

post the output of ```
sudo iptables -L -v
```

---

### Post by FuturePilot on 2009-12-14
> **bodhi.zazen said:**
> Keep in mind, order of your rules is critical. So my guess is that an earlier rule is accepting traffic.


This appears to be exactly what was happening. Actually it wasn't specific to this particular rule as I just noticed that some others weren't working either. I knew that iptables was specific about the order of rules but I didn't quite understand how it worked. After doing some reading on that I understand it better now.

So I figure that it was matching one of the rules at the beginning of the INPUT chain (the fail2ban and ufw rules) and therefore never checked it against my custom rule since I was just appending it to the end of INPUT. This would make sense seeing as how it worked when fail2ban added the rule, but not when I added it manually. So as a test I inserted my custom rule as the first rule in the INPUT chain and it appears to have worked. So now I'm guessing the best way to make this work is to create a custom chain and link it up in the number 1 slot in the INPUT chain?

```
Chain INPUT (policy DROP)
target     prot opt source               destination               
fail2ban-ModSec  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 80,443 
fail2ban-ssh  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports <snip> 
fail2ban-ssh-ddos  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports <snip>
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           
TARPIT     tcp  --  122.227.164.96       0.0.0.0/0           
DROP       udp  --  122.227.164.96       0.0.0.0/0           
DROP       udp  --  216.129.119.12       0.0.0.0/0           
TARPIT     tcp  --  64.34.172.135        0.0.0.0/0                  
DROP       udp  --  213.92.8.7           0.0.0.0/0           
TARPIT     tcp  --  213.92.8.7           0.0.0.0/0           
<snip> just a bunch more IPs

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-ModSec (1 references)
target     prot opt source               destination         
DROP       all  --  69.62.203.41         0.0.0.0/0           
DROP       all  --  216.129.119.12       0.0.0.0/0           
DROP       all  --  61.139.105.163       0.0.0.0/0
DROP       all  --  88.80.10.1           0.0.0.0/0           
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-SSH (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-apache-badbots (0 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         

Chain fail2ban-ssh-ddos (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:138 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:68 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 4 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  224.0.0.0/4          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            224.0.0.0/4         
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:<snip> 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:<snip>
ACCEPT     all  --  192.168.1.0/24       192.168.1.4         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
```

---

### Post by bodhi.zazen on 2009-12-14
> **FuturePilot said:**
> So now I'm guessing the best way to make this work is to create a custom chain and link it up in the number 1 slot in the INPUT chain?

That is how I do it, add a custom chain for blacklisting. I do not run it first in my INPUT as I reject a few things first, such as invalid packets, but close to the top.

Also I advise either you configure your firewall with ufw or iptables, but not both. This is because ufw adds a layer of complexity and it is difficult to read through the custom chains.

---

### Post by cdenley on 2009-12-14
Well, ideally, you would either configure iptables manually, or you would allow UFW to configure it for you. Stick with one configuration method to avoid conflicts.
```

sudo ufw deny from 88.80.10.1

```

---

### Post by bodhi.zazen on 2009-12-14
> **cdenley said:**
> Well, ideally, you would either configure iptables manually, or you would allow UFW to configure it for you. Stick with one configuration method to avoid conflicts.
```

sudo ufw deny from 88.80.10.1

```

Well, same problem, order of the rules applies, so you need to insert the rule early in your rules :

```
sudo ufw insert 1 deny from 88.80.10.1
```

---

### Post by FuturePilot on 2009-12-14
> **bodhi.zazen said:**
> That is how I do it, add a custom chain for blacklisting. I do not run it first in my INPUT as I reject a few things first, such as invalid packets, but close to the top.
Great! That's what I'll do then.

> **bodhi.zazen said:**
> Also I advise either you configure your firewall with ufw or iptables, but not both. This is because ufw adds a layer of complexity and it is difficult to read through the custom chains.


> **cdenley said:**
> Well, ideally, you would either configure iptables manually, or you would allow UFW to configure it for you. Stick with one configuration method to avoid conflicts.
```

sudo ufw deny from 88.80.10.1

```

That thought did cross my mind and now I kind of see why. I'll stick with only one from now on.

Thanks for the help guys! :)

---

### Post by bodhi.zazen on 2009-12-14
One more small tip ...

When working with remote servers, it is easy to lock yourself out if you set the default policy as drop.

Better, IMO, to keep the default policy as ACCEPT and as the last rule in a chain,

iptables -A INPUT -j DROP

---

