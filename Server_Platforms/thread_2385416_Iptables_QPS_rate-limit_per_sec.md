---
title: "Iptables QPS rate-limit per sec"
date: 2018-02-20
forum: Server Platforms
---

### Post by thekingshark on 2018-02-20
Hi.
I have nginx server that i want to limit the QPS rate limit per second.
For example, after 10 connections (of any type) per 1 minutes,  the server will drop all the next connections until the end of the 1 minutes.  

The port that i want to limit is 80 (http)
*I don't care about limit per IP, i want to limit the number of requests for all incoming traffic per 1 min. 
Any help how to do it?

Thanks in advanced.

---

### Post by slickymaster on 2018-02-20
Thread moved to **Server Platforms** for a better fit

---

### Post by Doug S on 2018-02-20
The standard rate limiting iptables rules should do what you want (assuming no other rules):

```

sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -m state --state NEW -m limit --limit 10/m -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j DROP

```
However, for an ngix server I do not know, but please note that the default settings for an apache server allow multiple requests per connection, so that needs to be changed:
```
#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
#KeepAlive On
KeepAlive Off

```

---

### Post by thekingshark on 2018-02-25
Thanks for your help.
I tried to use that rules, but looks like http requests still accepted and the page is shown..

---

### Post by Doug S on 2018-02-25
> **thekingshark said:**
> I tried to use that rules, but looks like http requests still accepted and the page is shown..It doesn't DROP any packets at all? After you think it should have dropped some packets, show us the output of:```
sudo iptables -v -x -n -L
```Example:```
$ [COLOR="#FF0000"]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy ACCEPT 13 packets, 2169 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     241    17962 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
      18     1080 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 state NEW limit: avg 10/min burst 5
      [COLOR="#FF0000"]38     2280 DROP[/COLOR]       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 state NEW

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 169 packets, 217649 bytes)
    pkts      bytes target     prot opt in     out     source               destination

```

---

