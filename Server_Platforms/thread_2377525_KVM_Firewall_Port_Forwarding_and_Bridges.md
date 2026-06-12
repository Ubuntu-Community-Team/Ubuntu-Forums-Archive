---
title: "KVM Firewall Port Forwarding and Bridges"
date: 2017-11-14
forum: Server Platforms
---

### Post by naisanza on 2017-11-14
I'm having a issue with something simple, I hope. I did this with Proxmox, and everything worked, but I've moved off Proxmox to use Ubuntu instead. And Untangled port forwards the traffic, but the SSH server doesn't respond.

+ The setup is a vanilla 16.04 server install + updates + bridge-utils + zfsutils-linux
+ 2 physical NICS, enp6s0 and enp7s0
+ 2 bridges, "outer" and "inner"
+ 1 KVM running Untangled Firewall (with both bridges attached)
+ Configuration Ansible Playbook - [https://github.com/TheShellLand/antsable/blob/master/playbooks/ubuntu-hypervisor.yml](https://github.com/TheShellLand/antsable/blob/master/playbooks/ubuntu-hypervisor.yml)
+ The service trying to be accessed is the SSH server on the host

KVM has bridges: "outer", "inner"
KVM address is 192.168.1.4 on "outer", and 10.0.0.3 on "inner"
KVM is configured to port forward only SSH connections incoming from "outer" to address 10.0.0.2


The original working design with Proxmox was:
[Internet] ==> [router: 192.168.1.0/24] ==DMZ to KVM Firewall IP==> [192.168.1.4/24] ==port forward 22==> [10.0.0.2]


Iptables are flushed and empty
Default policy is accept on all chains in filter, nat, and mangle.


So this works:
+ clients on "inner" can SSH to 10.0.0.2

This doesn't work:
+ clients not in "inner" can't access the SSH server
+ however, tcpdump (see below) shows traffic incoming to the KVM, and also traffic port forwarded to 10.0.0.2
+ But there is no returning traffic from 10.0.0.2 to the client


Host /etc/network/interfaces:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


# grey  ==> external router
iface enp6s0 inet manual


# white ==> internal router
iface enp7s0 inet manual


auto outer
iface outer inet static
        address 192.168.1.10
        broadcast 192.168.1.255
        netmask 255.255.255.0
        gateway 192.168.1.1
        network 192.168.0.0
        dns-nameservers 8.8.8.8 8.8.4.4
        bridge_ports enp6s0
        bridge_stp on
        bridge_fd 0


auto inner
iface inner inet static
        address 10.0.0.2
        broadcast 10.0.0.255
        netmask 255.255.255.0
        #gateway 10.0.0.3
        network 10.0.0.0
        bridge_ports enp7s0
        bridge_stp on
        bridge_fd 0



```

KVM (Untagled Firewall) routes:
```

 = IPv4 Table main = 
10.0.0.0/24 dev eth1  proto kernel  scope link  src 10.0.0.3 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.4 
192.168.1.1 dev eth0  scope link 

```

Host tcpdump for port 22 on "outer":
```

IP 172.217.13.xxx > 192.168.1.4.ssh [S]
IP 172.217.13.xxx > 192.168.1.4.ssh [S]
IP 172.217.13.xxx > 192.168.1.4.ssh [S]

```

Host tcpdump for port 22 on "inner":
```

IP 172.217.13.xxx > 10.0.0.2.ssh [S]
IP 172.217.13.xxx > 10.0.0.2.ssh [S]
IP 172.217.13.xxx > 10.0.0.2.ssh [S]

```

---

### Post by darkod on 2017-11-14
On the kvm host did you enable ipv4 forwarding in /etc/sysctl.conf?

And also I think you will need a MASQUERADE rule in the nat table of iptables on the host (if that is the machine routing traffic from 192.168.1.0/24 to 10.0.0.0/24 and back). Don't forget that any subnet change is actually routing, so without ipv4 forwarding and a MASQUERADE rule I don't think it will work. Even if iptables is not blocking anything (all policies to ACCEPT) that doesn't mean traffic knows to find its way back when travelling over different subnets. The MASQUERADE does that.

---

### Post by naisanza on 2017-11-14
> **darkod said:**
> On the kvm host did you enable ipv4 forwarding in /etc/sysctl.conf?

And also I think you will need a MASQUERADE rule in the nat table of iptables on the host (if that is the machine routing traffic from 192.168.1.0/24 to 10.0.0.0/24 and back). Don't forget that any subnet change is actually routing, so without ipv4 forwarding and a MASQUERADE rule I don't think it will work. Even if iptables is not blocking anything (all policies to ACCEPT) that doesn't mean traffic knows to find its way back when travelling over different subnets. The MASQUERADE does that.

I knew it had to be something with routing, but when I checked Proxmox, it didn't have any iptable rules. So I mimicked the same thing to try and narrow down the troubleshooting

The KVM is running Untangled Firewall, it has ipv4 forwarding set

In any case, I'd like to figure out the iptable rules I'll need to set.

Which iptables chain/tables do I need to change? Is it just FORWARD chain, and NAT POSTROUTING MASQUERADE that are needed?

To check if I understood you correctly, is this what I need?

```

iptables -F
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -A FORWARD -i outer -o outer -j ACCEPT    # allow outer <==> outer  (do I need this?)
iptables -A FORWARD -i inner -o inner -j ACCEPT    # allow inner <==> inner  (do I need this?)
iptables -A FORWARD -i outer -o inner -j ACCEPT    # allow outer <==> inner
iptables -A FORWARD -i inner -o outer -j ACCEPT    # allow inner <==> outer
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 ! -d 192.168.1.0/24 -j MASQUERADE    # masquerade anything leaving outer
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 ! -d 10.0.0.0/24 -j MASQUERADE          # masquerade anything leaving inner

```

---

### Post by darkod on 2017-11-15
1. If the FORWARD policy is ACCEPT like in your post, no need for any specific forward rules. All will be accepted by default with the policy.

2. Yes, those POSTROUTING rules should work, but you can also modify them to include source range and outgoing interface, I usually use it like that. For example something like:
```
iptables -t nat -A POSTROUTING -o enp7s0 -s 192.168.1.0/24 -j MASQUERADE
```

Do some testing and see what works best for you. But basically that is what you need to get the traffic flowing correctly in my opinion...

PS. Don't forget that outgoing interface is the interface used for the traffic to leave the KVM host. If I understood your setup correctly, for example the traffic from 192.168.1.0/24 enters the KVM host on enp6s0 and leaves it on enp7s0. So the outgoing interface would be enp7s0. I have a small dilemma whether you should use the bridge interfaces in MASQUERADE or the physical interface names, but you will figure it out with few tests. I haven't had this situation so I can't be sure if it's one or the other.

---

### Post by naisanza on 2017-11-15
> **darkod said:**
> ```
iptables -t nat -A POSTROUTING -o enp7s0 -s 192.168.1.0/24 -j MASQUERADE
```Do you mean `enp6s0` instead of `enp7s0`, since `enp6s0` is the interface connected to the internet?:```
iptables -t nat -A POSTROUTING -o enp6s0 -s 192.168.1.0/24 -j MASQUERADE
```

I've gone through and created rules in all the chains in filter and nat, looking for which table catches a packet with destination of 10.0.0.2/32

So far, only nat-PREROUTING is the only table that sees it. None of the other tables in filter and nat sees it.

I can create a PREROUTING rule to DNAT to 10.0.0.2/32, but that defeats the purpose of the KVM firewall.

This doesn't work, because enp6s0 is set to "iface enp6s0 inet manual", and also enp6s0 isn't used except as a bridge port:```
iptables -t nat -A POSTROUTING -o enp6s0 -s 192.168.1.0/24 -j MASQUERADE
```This is getting hits in "iptable -v -t nat -L", but it's still not showing outbound traffic from 10.0.0.2:22 ==> internet client```
iptables -t nat -A POSTROUTING -o outer -s 192.168.1.0/24 -j MASQUERADE
```

The only thing that has worked is enabling NAT'ing in the KVM firewall rule. However, then everything is seen as coming from the KVM IP, and not the public address of the client.

---

### Post by darkod on 2017-11-15
Did you look at my comments in the PS in my last post or they escaped you?

Try with the bridge interface instead. And don't forget that calling "public address" is far from correct, because both subnets you are using are private. What for you is external or internal traffic is another thing but don't forget we don't have as many details as you...

---

### Post by darkod on 2017-11-15
Like I said in the previous post, and after rerading everything again, the situation seems to be this:

Traffic is coming from the 192.168.1.0/24 subnet using the outer BrA and the destination is the KVM host 10.0.0.2 (the inner bridge BrB). In such case the masquerade rule would be:
```
iptables -t nat -A POSTROUTING -o inner -s 192.168.1.0/24 -j MASQUERADE
```

Try with that and let us know.

---

### Post by naisanza on 2017-11-15
> **darkod said:**
> Like I said in the previous post, and after rerading everything again, the situation seems to be this:

Traffic is coming from the 192.168.1.0/24 subnet using the outer BrA and the destination is the KVM host 10.0.0.2 (the inner bridge BrB). In such case the masquerade rule would be:
```
iptables -t nat -A POSTROUTING -o inner -s 192.168.1.0/24 -j MASQUERADE
```

Try with that and let us know.


I did try your other suggestions as well, it seems like the only rule that fires is:
```

iptables -t nat -I POSTROUTING 0 -o outer -s 192.168.1.0/24 -j MASQUERADE

```

I hope I had enough details, but I've added more details to the original post. And changed BrA and BrB to their respective bridge names, "outer" and "inner".

The KVM has the addresses
```

192.168.1.4
10.0.0.3

```

The original working design with Proxmox was:
```

[Internet] ==> [router: 192.168.1.0/24] ==DMZ to KVM Firewall IP==> [192.168.1.4/24] ==port forward 22==> [10.0.0.2]

```

"outer" is bridged with 192.168.1.0/24 
"inner" is 10.0.0.0/24

Host is 192.168.1.10/24 on "outer"
Host is 10.0.0.2/24 on "inner"
Host bridges: "outer", "inner"

KVM is 192.168.1.4/24 on "outer"
KVM is 10.0.0.3/24 on "inner"

[COLOR=#000000]tcpdump on "outer":[/COLOR]
[COLOR=#000000]```

IP 172.217.13.xxx > 192.168.1.4.ssh [S]
IP 172.217.13.xxx > 192.168.1.4.ssh [S]
IP 172.217.13.xxx > 192.168.1.4.ssh [S]

```

[/COLOR]tcpdump on "inner":
```

IP 172.217.13.xxx > 10.0.0.2.ssh [S]
IP 172.217.13.xxx > 10.0.0.2.ssh [S]
IP 172.217.13.xxx > 10.0.0.2.ssh [S]

```

iptables - t nat -L POSTROUTING -v:
```

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 MASQUERADE  all  --  any    inner  192.168.1.0/24       anywhere            
   12   840 MASQUERADE  all  --  any    outer   192.168.1.0/24       anywhere            

```

---

### Post by darkod on 2017-11-16
Hmmm, I thought it should be inner in the rule but I might be wrong. Like i said, I haven't had this situation with bridges. I have done quite a lot vpn servers and their routing though, but they didn't have bridges. Great, if it works for you with outer then that is the correct answer.

You can remove the inner rule by using the same command to create it, only using -D instead of the -A. It will delete the rule from iptables chain.

You can also mark this as Solved if it is. You can find the option in Thread Tools above the first post.

---

### Post by naisanza on 2017-11-16
> **darkod said:**
> Hmmm, I thought it should be inner in the rule but I might be wrong. Like i said, I haven't had this situation with bridges. I have done quite a lot vpn servers and their routing though, but they didn't have bridges. Great, if it works for you with outer then that is the correct answer.

You can remove the inner rule by using the same command to create it, only using -D instead of the -A. It will delete the rule from iptables chain.

You can also mark this as Solved if it is. You can find the option in Thread Tools above the first post.

That one rule that fires also doesn't work :(

In the tcpdump capture, it still just shows traffic inbound, but no outbound packets from 10.0.0.2.

Also, the only thing that has worked is enabling NAT'ing in the KVM firewall software. However, then everything is seen as coming from 10.0.0.3

---

### Post by darkod on 2017-11-16
Well, maybe you need that rule otherwise the return traffic doesn't know its way back...

Plus, are you trying this from public internet or the 192.168.1.0/24 subnet? Because your tcpdumps are from public IP. I think the header keeps the source IP information so the masquerade rule using -s 192.168.1.0/24 will not work.

As temporary test what if you try not limiting to any source IP (so it can work for the public IPs too):
```
iptables -t nat -A POSTROUTING -o inner -j MASQUERADE
```

See if that helps and in case it does you can try limiting it to specific range of public IPs if possible.

---

