---
title: "creating iptable rule for web site"
date: 2018-02-24
forum: Security
---

### Post by sniper8752 on 2018-02-24
I am trying to access the pi hole admin page on my lan ip.  In iptables, I've tried both:

```
sudo iptables -I INPUT -p tcp -i eth0 -m multiport --dports 80,443 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT

sudo iptables -I INPUT -p tcp -s 192.168.0.0/24 -m multiport --dports 80,443 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```

Both will give me access when I hit the internal ip in my browser.  But when I go to my wan ip, I am also able to view it, which is not what I want.  Are these rules allowing the external ip to connect to the service, or could it be another rule enabling that?

---

### Post by TheFu on 2018-02-25
Do you have a separate router?  Just don't forward any ports internally.  Never trust just 1 system for your security. Always use 2 methods, so if 1 fails for any reason (logical, physical, or config failure), the other catches it.

Some routers don't pass internal requests through their WAN port if the request comes from an internal IP on an internal ethernet port.

If there is a web server involved, you can use the web server allow/deny rules for stuff like this.

nginx works this way:
```
    allow 172.22.22.0/24; # Internal LAN
```

apache 2.4 works this way:
```
    <RequireAny>
               Require ip 172.22.22
     </RequireAny>
```

---

### Post by sniper8752 on 2018-02-25
The ubuntu server does everything.  I do have a wap, but that is to only connect wireless clients to the server.  It doesn't even hand out IPs. 
Do you mean that if my server fails, that then my wap/clients would be vulnerable?
And isn't there a way to do this in iptables?

---

### Post by The Cog on 2018-02-25
The rules you posted allow both anything connecting in via eth0 and anything calling from 192.168.0.* to access the services. Without more information I can't be sure what effect this has. If your server only has one interface (eth0) then the 192 address rules are entirely redundant because you are allowing anything from anywhere in anyway. The rules will allow external IP addresses to connect to the server if they are reaching it by coming in through eth0.

---

### Post by sniper8752 on 2018-02-25
Here are iptables rules:

```
Chain INPUT (policy DROP 0 packets, 0 bytes) pkts bytes target     prot opt in     out     source               destination
   x  x ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
   x  x ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED <-- Commenting this out breaks http/s connections 
   x  x DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
   x  x ACCEPT     all  --  eth0   eth1    192.168.0.0/24       0.0.0.0/0            ctstate NEW <-- Commenting this out breaks http/s connections 
   x  x ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED <-- Commenting this out breaks http/s connections 


Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
   x  x ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate ESTABLISHED
   x  x ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
   x  x DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

I have no clue how or why http/s is working when I have not put in rules for it.

---

### Post by Doug S on 2018-02-27
We still do not have enough information about your system to be able to try to help. Please post your entire iptables rule set and describe your system.

---

### Post by sniper8752 on 2018-02-27
Setup: Ubutnu 16 server: wan interface/lan interface -> wap -> wireless clients.

---

