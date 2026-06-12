---
title: "A simple iptables setup won't work. Complains no route..."
date: 2017-05-08
forum: Server Platforms
---

### Post by cb951303 on 2017-05-08
I have server running 16.04 and I've set it up so that the public interface is removed. It only has a private network interface (ens3). /etc/network/interfaces looks like this:

```

auto lo
iface lo inet loopback

auto ens7
iface ens7 inet static
    address 10.99.0.12
    netmask 255.255.0.0
    mtu 1450"

```

Up to this point everything works. Then I've decided to add a line to the above file to load my iptables rules before the network is setup
```

pre-up iptables-restore < /path/to/my/iptables.rules

```

Where my rules look like this
```

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
:TCP - [0:0]
:UDP - [0:0]
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate INVALID -j DROP
-A INPUT -p icmp -m icmp --icmp-type 8 -m conntrack --ctstate NEW -j ACCEPT
-A INPUT -p udp -m conntrack --ctstate NEW -j UDP
-A INPUT -p tcp --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j TCP
-A INPUT -p udp -j REJECT --reject-with icmp-port-unreachable
-A INPUT -p tcp -j REJECT --reject-with tcp-reset
-A INPUT -j REJECT --reject-with icmp-proto-unreachable
-A TCP -p tcp --dport 22 -j ACCEPT
-A TCP -p tcp --dport 7777 -j ACCEPT
COMMIT

```

As it can bee seen from the rules I only want ping, SSH and 7777 (my rest server) to be accessible.

But when I try to ping I get time out and when I try to ssh into the machine I get "no route to host" error.

Any ideas?

Thanks

---

### Post by darkod on 2017-05-08
I don't see ens3 in your /etc/network/interfaces. Did you cut it out or the file is as posted? Because if it is as posted you don't even have a gateway defined.

---

### Post by cb951303 on 2017-05-09
> **darkod said:**
> I don't see ens3 in your /etc/network/interfaces. Did you cut it out or the file is as posted? Because if it is as posted you don't even have a gateway defined.
I have removed it completely so that the computer is not connected to the outside at all. 
I only want to access to machine via ssh and http through private network (ens7) and it works when iptables is set to ACCEPT all. So my guess there is something wrong with my iptables setup

---

### Post by darkod on 2017-05-09
No, there is something wrong with your networking setup. It needs a gateway to communicate correctly. It can be a gw for the local LAN, doesn't need to be public access. But it does need one. For ens7 try adding something like 'gateway 10.99.0.1' or depending what the gw is for that subnet.

You can also try using port-up instead of pre-up. It doesn't make much difference because it will be run right after the interface is brought online, no one will have time to misuse it. The pre-up might complain because there is still no interface up, while when using post-up the interface is already up.

---

### Post by cb951303 on 2017-05-09
I'll try but as I said, it works without gateway. I tried it just now. When the iptables is set to allow every packet there is no problem connecting to the machine via ssh.
Also I now switched to ufw and there it works too.

EDIT: Gateway didn't help with the iptables setup. I've also learned that it's not needed because when the machines are on the same LAN (which what my private network is I think) you only need netmask and not gateway: [https://askubuntu.com/questions/432506/when-are-network-broadcast-and-gateway-required-for-configuring-a-network-inter](https://askubuntu.com/questions/432506/when-are-network-broadcast-and-gateway-required-for-configuring-a-network-inter)
But thanks, I think I'm going to use ufw. It's just easier to setup

---

### Post by Doug S on 2017-05-09
> **cb951303 said:**
> But thanks, I think I'm going to use ufw. It's just easier to setupToo bad. Myself, I much prefer iptables. I am very curious why your rules are not working for you. I looked and looked and looked at them and could not see anything wrong. I loaded your exact iptables rules into one of my test computers and it seems to be working fine.
```
doug@cyd-hp2:~$ [COLOR="#FF0000"]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    5281   228244 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    4881   292884 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
       [COLOR="#FF0000"]7[/COLOR]      588 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8 ctstate NEW
     108    12730 UDP        udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
       [COLOR="#FF0000"]2[/COLOR]      104 TCP        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp flags:0x17/0x02 ctstate NEW
     108    12730 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable
       0        0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with tcp-reset
      36     2592 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-proto-unreachable

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 10190 packets, 567422 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain TCP (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       [COLOR="#FF0000"]2[/COLOR]      104 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:7777

Chain UDP (1 references)
    pkts      bytes target     prot opt in     out     source               destination

```Although, your UDP chain seems incomplete.

---

