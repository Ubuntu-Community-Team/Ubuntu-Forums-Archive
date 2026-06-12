---
title: "iptables connections per port"
date: 2012-11-03
forum: Security
---

### Post by dudi4155 on 2012-11-03
I am trying to limit the number of connections to UDP port 19567, but unfortunately, the following command:

```
iptables -A INPUT -p udp --dport 19567 -m connlimit --connlimit-above 20 -j DROP
```

Returns the following error:

```
iptables: No chain/target/match by that name.
```

What I'm trying to achieve, is to allow only up to 20 unique IP's to be connected through that port at one time. Multiple connections from the same IP should be allowed.

Could anyone help me, please?

---

### Post by SeijiSensei on 2012-11-03
You need to run the iptables command as root with sudo, e.g., "sudo iptables -A INPUT ...".  Did you do that?

---

### Post by dudi4155 on 2012-11-03
Yes, I'm executing this as root

---

### Post by Doug S on 2012-11-03
The command works for me:```
doug@s15:~/sguide-1204/sguide-footnote$ sudo iptables -A INPUT -p udp --dport 19567 -m connlimit --connlimit-above 20 -j DROP
doug@s15:~/sguide-1204/sguide-footnote$ sudo iptables -v -x -n -L
Chain INPUT (policy ACCEPT 5 packets, 356 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:19567 #conn src/32 > 20
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain OUTPUT (policy ACCEPT 4 packets, 704 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```(Note: my s15 computer is isolated, so I don't normally have an iptables rule set running on it.)
 
I wonder if, perhaps, you don't have the connlimit module. I am not sure of the proper way to check.```
doug@s15:~/sguide-1204/sguide-footnote$ ls -l /lib/modules/3.2.0-32-generic/kernel/net/netfilter/xt_connlimit.ko
-rw-r--r-- 1 root root 9968 Sep 26 15:16 /lib/modules/3.2.0-32-generic/kernel/net/netfilter/xt_connlimit.ko

```I also see the module declaration in my config file:```
doug@s15:~/sguide-1204/sguide-footnote$ ls -l /boot/config-3.2.0-32-generic
-rw-r--r-- 1 root root 140488 Sep 26 15:14 /boot/config-3.2.0-32-generic
```contains:```
CONFIG_NETFILTER_XT_MATCH_CONNLIMIT=m
```By the way, I am running 3.2.0-32

---

### Post by theogeo on 2012-11-03
> **dudi4155 said:**
> I am trying to limit the number of connections to UDP port 19567, but unfortunately, the following command:

```
iptables -A INPUT -p udp --dport 19567 -m connlimit --connlimit-above 20 -j DROP
```

Returns the following error:

```
iptables: No chain/target/match by that name.
```

What I'm trying to achieve, is to allow only up to 20 unique IP's to be connected through that port at one time. Multiple connections from the same IP should be allowed.

Could anyone help me, please?


[http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#COMMONPROBLEMS]("http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#COMMONPROBLEMS")


"Another error that you may get when running iptables is the following error.

iptables: No chain/target/match by that name
   
This error tells us that there is no such chain, target or match. This could depend upon a huge set of factors, the most common being that you have misspelled the chain, target or match in question. Also, this could be generated in case you are trying to use a match that is not available, either because you did not load the proper module, it was not compiled into the kernel, or iptables failed to automatically load the module. In general, you should look for all of the above solutions but also look for misspelled targets of some sort or another in your rule."


Use the command: 
```
lsmod |less  or lsmod |grep -i "connlimit" 
``` to check if the connlimit module is loaded, if not use the ```
modprobe 
```  command to load it

---

### Post by dudi4155 on 2012-11-04
Oh, I didn't know that I need an extra module for this to work. It doesn't appear to be installed on the system, though. 

Since I am running Ubuntu on OpenVZ based VPS, there is no way I can install it myself, without contacting the support, right?

---

