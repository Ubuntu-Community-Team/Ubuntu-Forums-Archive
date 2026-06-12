---
title: "Urgent!!   Machine blocking connections"
date: 2008-10-06
forum: Server Platforms
---

### Post by sysfix on 2008-10-06
Hello, in need of an expert here. 
I have an ubuntu 8.04 server running a few services on a range of different ports but for some reason the server is blocking connections....

Server is on a 192.168.1.x netowrk, so are local machines
I can use http fine (port 80)

But cannot access Remote desktop or FTP (on alternative port)



I do not have a firewall enabled.
However if i go into a shell and type
# ufw disable

I can access everything.
A message appears saying firewall is turned off, and will be disabled on boot.


BUT 
Everytime I reboot, I get the same problem...
Unable to connect to the ports...

also, issuing 
#iptables -F
#/etc/init.d/networking restart

also allows me access
UNTIL I reboot

Please help):P):P):P

---

### Post by oneloveamaru on 2008-10-06
Then something is starting up that is blocking those ports. There are many firewall programs out there. Try removing iptables and reboot. Usually a firewall program like shorewall, etc uses iptables but if it's not there, it can't start.

apt-get remove iptables

Let me know how it goes after a reboot.

---

### Post by Vegan on 2008-10-06
Are you using a router such as one of those Linksys WRT54G like I use, if so you need to manually open ports as Linux is not UPNP capable.

---

### Post by oneloveamaru on 2008-10-06
on second thought, do a "ufw status" after a reboot and see what it says.

---

### Post by cdenley on 2008-10-06
What iptables front-end were you previously using? You sometimes have to purge them to prevent their rules from being loaded at startup.
```

sudo dpkg -P firestarter
sudo dpkg -P guarddog

```

To see what iptables rules are active
```

sudo iptables -L -n

```

---

### Post by sysfix on 2008-10-06
Thank-You all for your comments, I'm going to try these suggestions now.
However - the issues appear internally and externally on the lan so this is not a router issue (also tested this by direct cable connection)

No other firewall has been installed, brand new server installation and ran through the [Perfect Ubuntu Server Install]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p1")

OK.. here we go....

SERVER REBOOT:

```
server1:~$ sudo iptables -L -n
[sudo] password for xxx:
Chain INPUT (policy DROP)
target     prot opt source               destination
DROP       tcp  --  0.0.0.0/0            127.0.0.0/8
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTAB                            LISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  224.0.0.0/4          0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTAB                            LISHED
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0

Chain INT_IN (0 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain INT_OUT (0 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain PAROLE (10 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain PUB_IN (4 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 0
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:21
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:25
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:110
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8080
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:10000
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
DROP       icmp --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain PUB_OUT (4 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0



```





server1:~$ sudo ufw status
Firewall not loaded

---

### Post by cdenley on 2008-10-06
> **sysfix said:**
> Thank-You all for your comments, I'm going to try these suggestions now.
However - the issues appear internally and externally on the lan so this is not a router issue (also tested this by direct cable connection)

No other firewall has been installed, brand new server installation and ran through the [Perfect Ubuntu Server Install]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p1")

OK.. here we go....

SERVER REBOOT:

```
server1:~$ sudo iptables -L -n
[sudo] password for xxx:
Chain INPUT (policy DROP)
target     prot opt source               destination
DROP       tcp  --  0.0.0.0/0            127.0.0.0/8
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTAB                            LISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  224.0.0.0/4          0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
PUB_IN     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTAB                            LISHED
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0
PUB_OUT    all  --  0.0.0.0/0            0.0.0.0/0

Chain INT_IN (0 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain INT_OUT (0 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain PAROLE (10 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain PUB_IN (4 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 0
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:21
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:25
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:110
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8080
PAROLE     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:10000
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
DROP       icmp --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain PUB_OUT (4 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0



```





server1:~$ sudo ufw status
Firewall not loaded

There is obviously something loading iptables rules at startup. The output you posted should look like
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
to clear it, run
```

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F

```

---

### Post by sysfix on 2008-10-06
hmm im stumped from here then , im a windows guru , this is my first linux build

What I dont get is even if something dies load rules into iptables, when you check the status , it says firewall isnt running , so you'd expect anything in there to not be processed.




OMG!!!!!!!
Where the &^$^$&^*&%(   has this come from???

bastille-firewall 	Yes 	Load/unload ipchains rulesets at startup





IM WORKING NOW
THANKS SO MUCH TO EVERYONE FOR YOUR KIND HELP

---

### Post by cdenley on 2008-10-06
> **sysfix said:**
> hmm im stumped from here then , im a windows guru , this is my first linux build

What I dont get is even if something dies load rules into iptables, when you check the status , it says firewall isnt running , so you'd expect anything in there to not be processed.




OMG!!!!!!!
Where the &^$^$&^*&%(   has this come from???

bastille-firewall 	Yes 	Load/unload ipchains rulesets at startup





IM WORKING NOW
THANKS SO MUCH TO EVERYONE FOR YOUR KIND HELP

IM WORKING NOW = it's working now?

UFW is a frontend for iptables. Disabling the UFW rules does not prevent another script from loading its own iptables rules. You could possibly have two frontends with their individual filter chains processed concurrently.

---

