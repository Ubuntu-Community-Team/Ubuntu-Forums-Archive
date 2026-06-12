---
title: "HELP: Filtering internet connection sharing"
date: 2008-06-26
forum: Security
---

### Post by cjtjamandra on 2008-06-26
Iam using my Ubuntu box to share my internet connection through LAN using dnsmasq and ipmasq, a PC can have internet connection by just specifying my server's ip as their gateway. But i dont want all of the PC in my LAN to be able to use or share with my connection, i just want to specify certain IP who will be able to connect or share with my connection.

Is there any resolution to this problem? thanks.

---

### Post by kevdog on 2008-06-27
I'm taking a wild guess, but Im guessing that you are going to have to alter the iptables ruleset on the machine sharing the internet.  I'm also willing to bet you have a script file that sets up your iptables with the following line:

iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE


Hopefully you have first a default drop policy in your script, something like (this would be near the top of the script):

iptables -P FORWARD DROP

Then you want to filter by ip address, specific ip addresses that can forward through your machine (please note this is an example, and you would place this statement before the POSTROUTING statement):

iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A FORWARD -s <IPADDRESS> --syn -m state --state NEW -j ACCEPT

Now the <IPADDRESS> parameter can be an individual ip address (if you use multiple ip addresses that are not contiguous you would have to repeat this line for each ip address.  To avoid this, you could use nomenclature like 192.168.0.1/24 or could specify a range of contigous addresses you would like to accept like this:

iptables -t filter -A FORWARD -m iprange --src-range 192.168.0.13-192.168.0.19 --syn -m state --state NEW -j ACCEPT 

Of course you could do the reverse of the range with the following:

iptables -t filter -A FORWARD -m iprange ! --src-range 192.168.0.13-192.168.0.19 --syn -m state --state NEW -j ACCEPT 

Does this help at all?

---

### Post by cjtjamandra on 2008-06-27
Thank you very much for the reply.

I don't have the script :

```
iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
```

Because iam using ipmasq and dnsmasq in sharing my connection.

But can i still use the lines:

```
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A FORWARD -s <IPADDRESS> --syn -m state --state NEW -j ACCEPT
```

even if iam using ipmasq and dnsmasq?

or is there a utility under dnsmasq or ipmasq that i can use?

thanks in advance

---

### Post by kevdog on 2008-06-27
Are you telling me you are using Firestarter?  Just wondering. Im a little confused with your setup.


And just b/c I'm curious, can you list:

sudo iptables -L

---

### Post by cjtjamandra on 2008-06-27
Iam not using firestarter because my ubuntu is server edition, no GUI

iam executing this to enable internet sharing:

```
sudo /etc/init.d/dnsmasq restart
sudo /etc/init.d/ipmasq restart
```


iptables -L results:

```
Chain INPUT (policy DROP)
target     prot opt source               destination
DROP       0    --  192.168.10.106       anywhere
ACCEPT     0    --  192.168.10.0/24      192.168.24.0/24
ACCEPT     0    --  192.168.24.0/24      192.168.10.0/24
ACCEPT     0    --  192.168.10.0/24      192.168.21.0/24
ACCEPT     0    --  192.168.21.0/24      192.168.10.0/24
ACCEPT     0    --  anywhere             anywhere
LOG        0    --  loopback/8           anywhere            LOG level warning
DROP       0    --  loopback/8           anywhere
ACCEPT     0    --  anywhere             255.255.255.255
ACCEPT     0    --  192.168.10.0/24      anywhere
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4
LOG        0    --  192.168.10.0/24      anywhere            LOG level warning
DROP       0    --  192.168.10.0/24      anywhere
ACCEPT     0    --  anywhere             255.255.255.255
ACCEPT     0    --  anywhere             webserver.9.5.117.mozcom.net
ACCEPT     0    --  anywhere             61.9.5.255
DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET
LOG        0    --  anywhere             anywhere            LOG level warning
DROP       0    --  anywhere             anywhere
           tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: SET name: DEFAULT side: source
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: UPDATE seconds: 60 hit_count: 2 name: DEFAULT side: source

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  192.168.10.0/24      192.168.24.0/24
ACCEPT     0    --  192.168.24.0/24      192.168.10.0/24
ACCEPT     0    --  192.168.10.0/24      192.168.21.0/24
ACCEPT     0    --  192.168.21.0/24      192.168.10.0/24
ACCEPT     0    --  192.168.10.0/24      anywhere
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED
LOG        0    --  anywhere             192.168.10.0/24     LOG level warning
DROP       0    --  anywhere             192.168.10.0/24
DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET
LOG        0    --  anywhere             anywhere            LOG level warning
DROP       0    --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  192.168.10.0/24      192.168.24.0/24
ACCEPT     0    --  192.168.24.0/24      192.168.10.0/24
ACCEPT     0    --  192.168.10.0/24      192.168.21.0/24
ACCEPT     0    --  192.168.21.0/24      192.168.10.0/24
ACCEPT     0    --  anywhere             anywhere
ACCEPT     0    --  anywhere             255.255.255.255
ACCEPT     0    --  anywhere             192.168.10.0/24
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4
LOG        0    --  anywhere             192.168.10.0/24     LOG level warning
DROP       0    --  anywhere             192.168.10.0/24
ACCEPT     0    --  anywhere             255.255.255.255
ACCEPT     0    --  webserver.9.5.117.mozcom.net  anywhere
ACCEPT     0    --  61.9.5.255           anywhere
DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET
LOG        0    --  anywhere             anywhere            LOG level warning
DROP       0    --  anywhere             anywhere

```

---

### Post by kevdog on 2008-06-27
dnsmasq is not the issue -- this is a light dns server.

ipmasq is acting as your firewall -- in actuality its indirectly modifying your iptables.

Hmm interesting.  That doesn't seem the way I would do, rather just skip the ipmasq and modify your iptables directly.  

I looked at the documentation at the ipmasq website and it was very skant.  It looks like there are some rules files that you could alter using this file(s).

A lot of rules in your iptables?  Do ipmasq add all of these, or was there another process?

---

### Post by kevdog on 2008-06-27
After thinking about it for a while I suppose its possible to just insert the filter rules into the table directly at the right spot (that is going to be the tricky part -- but definitely doable).  This might be the easiest solution. 


Can you post the following

iptable -L FORWARD --line-numbers

---

### Post by cjtjamandra on 2008-06-27
No, the other rules are added by me. because iam forwarding my other PC(whose gateway is my server) to other segments of the network and also blocking certain IPs in my LAN, that's why i need to filter my Internet sharing so that certain IPs only can use my internet sharing, but all i want to block from the other is my internet sharing, i still want others to access my apache server.

Is it possible? How can i do these using iptables? is it too complex?

---

### Post by kevdog on 2008-06-27
Maybe I'm a little confused, but a diagram from you would definitely clear things up.  From your iptables, you have a lot of subnets going on.  As far as the internet connection sharing, you are telling me the computers you want blocked you want to be able to access an internal http server, but not have access to the internet?  Its definitely possible to filter on the basis of either destination/source ports and ip addresses, and combinations, so I think it would be do able.

I'm no iptables expert, but I'm thinking we could probably figure this one out!

---

### Post by cjtjamandra on 2008-06-27
Thanks.. iam glad you could get what i mean after those very vague explanation of mine. :)


All i want is to have an iptables rule that will:

First, Allow all other connections from my LAN to my apache socket 443 (SSL).

Second, drop all internet sharing attempts except for certain IPs i want.


That's all i want to do. :)

---

### Post by kevdog on 2008-06-28
Sorry for the long reply, but this is definitely possible.

Lets just start off with ICS.  Then we will limit ICS (by setting up some limits within iptables).  

Then allowing http access -- that is easy within the lan.  No Problem there.

Can you post:
iptables -L FORWARD --line-numbers

---

### Post by cjtjamandra on 2008-06-29
This is the result of iptables -L FORWARD --line-numbers:

```
Chain FORWARD (policy DROP)
num  target     prot opt source               destination
1    ACCEPT     0    --  192.168.10.0/24      192.168.24.0/24
2    ACCEPT     0    --  192.168.24.0/24      192.168.10.0/24
3    ACCEPT     0    --  192.168.10.0/24      192.168.21.0/24
4    ACCEPT     0    --  192.168.21.0/24      192.168.10.0/24
5    ACCEPT     0    --  192.168.10.0/24      anywhere
6    ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED
7    LOG        0    --  anywhere             192.168.10.0/24     LOG level warning
8    DROP       0    --  anywhere             192.168.10.0/24
9    DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET
10   LOG        0    --  anywhere             anywhere            LOG level warning
11   DROP       0    --  anywhere             anywhere

```

For my analyzation, it is sharing internet connection to all, am i right?

But I just want to share my internet connection to specific IPs only.:popcorn:

---

### Post by kevdog on 2008-06-29
You have three separate subnets.  How is your network arranged?

---

### Post by cjtjamandra on 2008-06-29
We have several segments. my server and client PCs are in segment 10, my gateway(server PC) is forwarding segment 21 and 24 so that my client PCs can connect to them (21 and 24).

---

