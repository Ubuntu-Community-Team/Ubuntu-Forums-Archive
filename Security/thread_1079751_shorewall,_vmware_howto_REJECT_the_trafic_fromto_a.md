---
title: "shorewall, vmware: howto REJECT the trafic from/to a virtual host"
date: 2009-02-24
forum: Security
---

### Post by azzamite on 2009-02-24
Hi everyone
I'm messing with shorewall, I want to block all trafic from/to my virtual hosts, but I can't, so I was wondering if you could help me.

The virtual host is... you guessed, windows!, the virtual network connection is **NAT**ed, so I have vmnet1 and vmnet8.

Both vmnets are in the zone *_vir_*, from the wich all packages **must be** dropped (for now).

So far, the **virtual host can ping** wlan0, vmnet1 and google **while it shouldn't**. The only one it can't ping is vmnet8 (same subnet as the host). I can ping vmnet8 from the host while shorewall isn't running.

So far this is my comfiguration

zones
```
fw firewall
net ipv4
#dmz ipv4
vir ipv4

```

interfaces
```
net wlan0 detect dhcp,routefilter,tcpflags
net eth0  detect dhcp,routefilter,tcpflags
vir vmnet8 detect dhcp
vir vmnet1 detect dhcp

```

policy
```
net all DROP
#dmz all REJECT
vir all DROP
fw all ACCEPT #ACCEPT BY DEFAULT
all all REJECT

```

I'm trying [this]("http://wiki.debian.org/HowTo/shorewall") tutorial 
And some more output

```
shorewall check
Checking...
Initializing...
Determining Zones...
   IPv4 Zones: net vir
   Firewall Zone: fw
Validating interfaces file...
Validating hosts file...
Pre-processing Actions...
   Pre-processing /usr/share/shorewall/action.Drop...
   Pre-processing /usr/share/shorewall/action.Reject...
Validating Policy file...
Determining Hosts in Zones...
   net Zone: wlan0:0.0.0.0/0 eth0:0.0.0.0/0
   vir Zone: vmnet8:0.0.0.0/0 vmnet1:0.0.0.0/0
Deleting user chains...
Checking /etc/shorewall/routestopped ...
Creating Interface Chains...
Checking Common Rules
Adding rules for DHCP
Checking TCP Flags checking...
Checking Kernel Route Filtering...
Checking Martian Logging...
Checking /etc/shorewall/rules...
Checking Actions...
Checking /usr/share/shorewall/action.Drop for Chain Drop...
Checking /usr/share/shorewall/action.Reject for Chain Reject...
Checking /etc/shorewall/policy...
Checking Traffic Control Rules...
Checking Rule Activation...
Compiling IP Forwarding...
Shorewall configuration verified

```

---

### Post by bodhi.zazen on 2009-02-24
A few simple rules in iptables should do the job :

```
sudo iptables -A INPUT -i vmnet1 -j DROP
sudo iptables -A INPUT -i vmnet8 -j DROP

sudo iptables -A OUTPUT -o vmnet1 -j DROP
sudo iptables -A OUTPUT -o vmnet8 -j DROP
```

---

### Post by azzamite on 2009-02-24
> **bodhi.zazen said:**
> A few simple rules in iptables should do the job :

```
sudo iptables -A _INPTUT_ -i vmnet1 -j DROP
sudo iptables -A _INPTUT_ -i vmnet8 -j DROP

sudo iptables -A OUTPUT -o vmnet1 -j DROP
sudo iptables -A OUTPUT -o vmnet8 -j DROP
```

mmm, the idea is no to use iptables directly, since those changes won't be applied on every system reboot, unless I add'em in rc.local or something.

And, after correcting the little typo, those rules didn't work either, the host still make the same pings.

The only way I've been able to block the trafic is blocking **fw** but the whole system is left without internet...

I think it's got something to do with the fact that the host gets internet using NAT, I'll try using host-only.

Meanwhile, any more ideas?

---

### Post by bodhi.zazen on 2009-02-24
Interesting ...

You can save and restore iptables via iptables-save and iptables-restore or if you prefer ufw.

Now I am interested in why those rules did not work, will have to fire up vmware ...

Why not disable your network on your host ?

My guess is that shorewall (and perhaps iptables) will not work because your vmware interfaces are bridged, just a guess though.

---

### Post by azzamite on 2009-02-24
> **bodhi.zazen said:**
> You can save and restore iptables via iptables-save and iptables-restore or if you prefer ufw.

Good to know it, but still, iptables is for hardcore users (or so I think).


> **bodhi.zazen said:**
> Why not disable your network on your host ?

As I said, I'm messing with shorewall.
Actually, I want to learn how to configure it, so I'm practicing with my virtual hosts.

The idea is to block ALL trafic, and then open ports as required: http, ftp, dns, etc.

And then after that configure port fordwarding and so on...

---

### Post by bodhi.zazen on 2009-02-24
Good luck with shorewall.

I found it difficult to learn and IMO in the time it takes you to learn shorewall you can learn iptables (IMHO).

May I suggest Guarddog or UFW ?

Edit: Guarddog has built in help which describes your options.

I wrote a (nice) overview of iptables here : 

[http://bodhizazen.net/beginners/Firewall](http://bodhizazen.net/beginners/Firewall)

Although my server is down at the moment :( (should be back up in a few hours, although I am having issues ... )

In addition the site (including css) is still a work in progress, so excuse the eyesore.

All the way at the bottom of the page is a link for how to NAT which is what you are wanting to do.

---

### Post by azzamite on 2009-02-24
I shall read your overview of iptables.

AFAIK, shorewall and mabe Guarddog and UFW, are front ends to netfilter's iptables (the only firewall of linux (since ipchains is discontinued)).

Anyway, I'll check'em out.

Tanks for your help.

):P

---

### Post by bodhi.zazen on 2009-02-24
OK, first my server is back up (FYI) 

Second, the reason those rules did not work is that the order of the rules is important. 

List your rules with :

```
sudo iptables -L -v
```

Early in your rules you are accepting the traffic ...

So ...

You will need to start by flushing your rules.

```
sudo iptables -F
```

the rules I gave you  will then work.

You can then allow traffic by inserting earlier rules.

---

### Post by phones604 on 2009-02-25
[chinese cell phones](http://www.chinese-cell-phones.com) [img]http://www.chinese-cell-phones.com/uploadfile/UploadFileimages/2009177364091959b.jpg[/img]

---

