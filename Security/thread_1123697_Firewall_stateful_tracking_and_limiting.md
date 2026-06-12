---
title: "Firewall: stateful tracking and limiting"
date: 2009-04-12
forum: Security
---

### Post by gor on 2009-04-12
Hello,

I have a problem that i couldn't solve yet. One of my servers with Ubuntu OS was affected by TCP connection flood attack targeted to apache service. After reviewing the system i have discovered that attacker opened large number of TCP connections to tcp port 80 without sending any data. The httpd service ran out of connections and stoped responding. Netstat says:
```
# netstat -atn
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):2780     ESTABLISHED
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):4841     ESTABLISHED
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):4498     ESTABLISHED
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):4551     ESTABLISHED
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):1505     ESTABLISHED
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):4186     ESTABLISHED
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):4037     ESTABLISHED
tcp        0      1 (MY-SERVER-IP):80        (ATTACKER-IP):2530     ESTABLISHED
... (more than hundered identical lines) ...

```
I know that is not a bug, but i could not find the way to prevent such kind of attack so i had to block the whole IP range of attacker's ISP. Im not a newbie in Linux and UNIX, but am not really familiar with Linux iptables stuff.
Some of my servers running OpenBSD with PF. BSD's PF allows you to limit the maximum number of simultaneous states per source IP: [http://openbsd.org/faq/pf/filter.html#stateopts]("http://openbsd.org/faq/pf/filter.html#stateopts")

I have found some infos regarding iptables connlimit feature, unfortunately it won't work on my server:
```
# iptables -I INPUT -p tcp -m connlimit --connlimit-above 10 -j REJECT
iptables v1.3.8: Couldn't load match `connlimit':/lib/iptables/libipt_connlimit.so: cannot open shared object file: No such file or directory
```
It seems that 'connlimit' module is broken. I remember similar issue years ago on other linux distribution (SuSE) where i tried to compile it manually, with no success.

I have wrote a simple proof-of-concept PHP script that demonstrates an attack:
```
<?php
/**
 * Proof of concept script: TCP connection flooding.
 * THIS SCRIPT WAS WRITTEN FOR INTERNAL TEST PURPOSES ONLY!!!
 *
 * The script is not functional; you need to repair it in order to get it to work (script kiddie protection).
 *
 */

$target_host='192.168.2.200';
$target_port=80;

$conn=array();

for ($i=0; $i<500; $i++) {
  if ($conn[$i]=@ffsockopen($target_host, $target_port)) {
    echo "Connection #$i opened\n";
    flush();
    fwrite($conn[$i], "GET / HTTP/1.1\r\n"); // lets send the first line and grab an apache process
  }
}
sleep(30); // The server must be blocked until the script exits

?>
```


Well, here is my question: is there a way to get connlimit to work, or are there any other tools for source tracking/limiting on Linux? This problem isn't really new; however it hurts alot unless you have professional firewall/gateway appliance that protects your server.

Thank you in advance.

---

### Post by HermanAB on 2009-04-12
Here you go:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

---

### Post by gor on 2009-04-13
Thank you for reply.
I have added the rule and executed the script from my post above. Same result - the server remains unavailable during the test...

Unfortunately, this rule seems to affect all clients, so if attacker "grabs" all free connections/states within the limit all "good" clients must wait.

---

### Post by kevdog on 2009-04-13
Sounds like you need to block the source ip

iptables -I INPUT -p TCP --src <src IP> -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

---

### Post by bodhi.zazen on 2009-04-13
I suggest 2 things :

1. First, I do not know about others, but posting the script you use to configure iptables is not so helpful when debugging iptables problems.

Please post the output of :

```
sudo iptables -L -v
```

Once you get your rules configures, you can simply 

```
sudo iptable-save > /etc/iptables.rulse
```

And restore

```
iptables-restore < /etc/iptables.rules
```

in /etc/rc.local

No real need for fancy scripts, IMO.


2. I would encourage you to file a bug report against Apache.

---

### Post by gor on 2009-04-13
Hello,
Thank you for replies.

> **kevdog said:**
> Sounds like you need to block the source ip
The attacker has dynamic DSL account so he just needs to reconnect in order to continue flooding. Unfortunately, his ISP has large IP ranges; the only one possibility i've seen was to block huge IP address areas. Thats evil, but the smallest one: customers from other countries can access their applications now. I used following command to block IP ranges:
# iptables -A INPUT -s xx.xx.xx.xx/yy -j DROP
As you can see from iptables output below, there are lot of dropped packets most of them are assumed not to come from attacker.

> **bodhi.zazen said:**
> 1. First, I do not know about others, but posting the script you use to configure iptables is not so helpful when debugging iptables problems.
The script from my post above is not iptables config script; it demonstrates the flood attack. We have tested that scripts against some Linux (CentOS, Ubuntu) servers in our office network. All of them went offline after a short time. Our network gateway/firewall is an OpenBSD with PF. PF provides state limits for every source IP address, eg every client can have maximum 'N' simultaneous connection states. The server affected by the attack i've describe here is located outside our network and not protected by any firewall appliances so i have to find the way to secure it.

Edit the script and test it against your Linux machines and you will see what i mean. The script is not functional, you need to repair it before you run it (script kiddie protection). If you are not familiar with PHP then send me a PM and i will provide you a functional version.

> **bodhi.zazen said:**
> Please post the output of iptables -L -v

```
# iptables -L -v -n
Chain INPUT (policy ACCEPT 15M packets, 13G bytes)
 pkts bytes target     prot opt in     out     source               destination
 5612  302K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW limit: avg 10/min burst 5
 7610  398K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW limit: avg 30/min burst 5
  298 58432 DROP       all  --  *      *       88.xxx.0.0/17        0.0.0.0/0
 913K   44M DROP       all  --  *      *       88.xxx.xxx.0/17      0.0.0.0/0
 529K   25M DROP       all  --  *      *       85.xx.xxx.0/17       0.0.0.0/0
 515K   25M DROP       all  --  *      *       88.xxx.xxx.0/24      0.0.0.0/0
 232K   11M DROP       all  --  *      *       78.xxx.xxx.0/24      0.0.0.0/0
 131K 6292K DROP       all  --  *      *       88.xxx.xxx.0/24      0.0.0.0/0
 892K   43M DROP       all  --  *      *       88.xxx.xxx.0/24      0.0.0.0/0
 227K 9976K DROP       all  --  *      *       88.xxx.xxx.0/24      0.0.0.0/0

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 17M packets, 15G bytes)
 pkts bytes target     prot opt in     out     source               destination

```

> **kevdog said:**
> 2. I would encourage you to file a bug report against Apache.
Yes, i will to do that. But, sorry for repeating my last question; is there a way to limit simultaneous connection states for every source IP on Linux? Beside possible Apache weakness it would be useful to be able to protect running services on the machine.

Thank you.

---

### Post by gor on 2009-04-14
Anyone??

---

### Post by bodhi.zazen on 2009-04-14
This is how I do it :

[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

The rules for ssh i use are tighter then the rules for http (ie number of new connections allowed).

---

### Post by The Cog on 2009-04-14
+1 for bodhi.zazens solution. Works a treat for me.

---

### Post by gor on 2009-04-14
> **bodhi.zazen said:**
> This is how I do it :

[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

The rules for ssh i use are tighter then the rules for http (ie number of new connections allowed).

```
iptables -I INPUT -p tcp --dport 80 -i eth0 -m state --state NEW -m recent --set
iptables -I INPUT -p tcp --dport 80 -i eth0 -m state --state NEW -m recent --update --seconds 10 --hitcount 10 -j DROP
iptables -I INPUT -p tcp --dport 80 -i eth0 -m state --state INVALID -m recent --set
iptables -I INPUT -p tcp --dport 80 -i eth0 -m state --state INVALID -m recent --update --seconds 10 --hitcount 10 -j DROP

```

Phew, the server can breathe again. Many thanks!

---

