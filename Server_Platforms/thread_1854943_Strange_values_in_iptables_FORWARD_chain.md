---
title: "Strange values in iptables FORWARD chain"
date: 2011-10-05
forum: Server Platforms
---

### Post by DavidBeijer on 2011-10-05
Hi,

I recently installed my first server with ubuntu server. Through the installation procedure a SSH, FTP, SAMBA and LAMP were pre-configured. I have modified things to my liking and now am working on firewall settings. For this I use IP-tables and thusfar I understand everything and it works. However, when I list the rules with iptables -L (-v), I see some rules I do not fully understand in the FORWARD chain. I have not put those rules there myself, and as I do not use this server as a gateway for internet acces I do not get why these rules are here. Can I safely remove them? Will some services stop working if I do?

The rules:
```


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  any    virbr0  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  virbr0 any     192.168.122.0/24     anywhere
    0     0 ACCEPT     all  --  virbr0 virbr0  anywhere             anywhere
    0     0 REJECT     all  --  any    virbr0  anywhere             anywhere            reject-with icmp-port-unreachable
    0     0 REJECT     all  --  virbr0 any     anywhere             anywhere            reject-with icmp-port-unreachable


```


Any ideas?

Oh, and one additional question: at the moment I control this server remotely, and I notice that rules that have a specified source or target IP take very long to get printed in a terminal. And with very long I mean seconds, whereas lines that have "anywhere" as source or destination get printed with no time delay whatsoever. Any ideas what may cause this?

---

### Post by Dangertux on 2011-10-05
> **DavidBeijer said:**
> Hi,

I recently installed my first server with ubuntu server. Through the installation procedure a SSH, FTP, SAMBA and LAMP were pre-configured. I have modified things to my liking and now am working on firewall settings. For this I use IP-tables and thusfar I understand everything and it works. However, when I list the rules with iptables -L (-v), I see some rules I do not fully understand in the FORWARD chain. I have not put those rules there myself, and as I do not use this server as a gateway for internet acces I do not get why these rules are here. Can I safely remove them? Will some services stop working if I do?

The rules:
```


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  any    virbr0  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  virbr0 any     192.168.122.0/24     anywhere
    0     0 ACCEPT     all  --  virbr0 virbr0  anywhere             anywhere
    0     0 REJECT     all  --  any    virbr0  anywhere             anywhere            reject-with icmp-port-unreachable
    0     0 REJECT     all  --  virbr0 any     anywhere             anywhere            reject-with icmp-port-unreachable


```
Any ideas?

Oh, and one additional question: at the moment I control this server remotely, and I notice that rules that have a specified source or target IP take very long to get printed in a terminal. And with very long I mean seconds, whereas lines that have "anywhere" as source or destination get printed with no time delay whatsoever. Any ideas what may cause this?


The virbr0 interfaces are virtual interfaces usually added either by something like Xen or KVM are you using virtualization or is this a VPS host?

In any case they are normal if you are using a virtualized instance.

---

### Post by DavidBeijer on 2011-10-06
I'm not using any virtualisation, it is also not a VPS. It's just an old laptop I'm using here locally for multimedia purposes.

If I just remove these rules, will that screw up things badly? Or can I safely do some "trial and error" without having to do a complete reinstall?

---

### Post by Dangertux on 2011-10-06
You can do trial and error they may just be left over from vmware or something like that they probably even doing anything if you're not using virtualization.

---

### Post by DavidBeijer on 2011-10-06
I tried it and everything seems to be working just fine. Thanks!

Any ideas as to why entries containing specific IP-adresses or ranges are printed MUCH slower (both on a remote terminal and locally)? After "sudo iptables -L" all lines print instantaneously, except the lines containing specific IP-adresses, such as the open ports for samba that are only accessible from my local network range.

---

### Post by DavidBeijer on 2011-10-10
ok, apparently something is still wrong with my firewall configuration. Regardless of whether I have the "unknown" values in the FORWARD chain, some things start malfunctioning with these iptables settings.

Logging in remotely over SSH is much slower when I activate my rules in iptables, and apt-get will just not work when it is on. Also, when listing iptables, each line that has a spacified ip-adress as source or destination takes a couple of seconds to be printed. When I restart the server (and iptables is restored to default) everything works just fine. Can anyone point at a reason why this configuration slows down (or breaks) certain stuff?

A dump from iptables-save:
```

# Generated by iptables-save v1.4.10 on Mon Oct 10 14:50:57 2011
*nat
:PREROUTING ACCEPT [597:76705]
:INPUT ACCEPT [32:3894]
:OUTPUT ACCEPT [39:4388]
:POSTROUTING ACCEPT [39:4388]
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE
COMMIT
# Completed on Mon Oct 10 14:50:57 2011
# Generated by iptables-save v1.4.10 on Mon Oct 10 14:50:57 2011
*mangle
:PREROUTING ACCEPT [1210:148094]
:INPUT ACCEPT [1210:148094]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [545:80399]
:POSTROUTING ACCEPT [549:81389]
-A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill
COMMIT
# Completed on Mon Oct 10 14:50:57 2011
# Generated by iptables-save v1.4.10 on Mon Oct 10 14:50:57 2011
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 445 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 139 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 138 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 137 -j ACCEPT
-A INPUT -p udp -m udp --dport 20630 -j ACCEPT
-A INPUT -p udp -m udp --dport 20500:20599 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20500:20599 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20630 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 9091 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT
-A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT
-A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT
-A INPUT -j DROP
-A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT
-A FORWARD -i virbr0 -o virbr0 -j ACCEPT
-A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -j DROP
-A OUTPUT -j ACCEPT
COMMIT
# Completed on Mon Oct 10 14:50:57 2011

```

---

### Post by SeijiSensei on 2011-10-10
The delays arise because you don't have reverse DNS configured for the numerical addresses.  The simplest solution is to create entries for these addresses in /etc/hosts, or use "iptables -L -n".

You also have rules for those virbr0 interfaces.  Just get rid of the "-i virbr0" and "-o virbr0" parameters for now and see if that fixes things.  

Did you write these rules yourself, or did you get them from somewhere else?  As others have said, if you're not using a virtual machine, there shouldn't be any virbrX interfaces.

---

### Post by DavidBeijer on 2011-10-11
ah, the -n option helps a lot :). Tnx!

So now I eliminated all the lines from iptables dealing with virbr0. I also eliminated all lines dealing with the 192.168.122.* range, as I do not have anything on my network in that range. I certainly did not add them, but when I restart ubuntu the virbr0 stuff is back in iptables. Can it have something to do with the fact that I enabled the option for virtual machines during installation? I'm not using any VM's right now, but I might want to experiment with that in the future.

In any case: "sudo apt-get update" still won't work. iptables -L -n now looks like:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     tcp  --  192.168.0.0/24       0.0.0.0/0           tcp dpt:445
ACCEPT     tcp  --  192.168.0.0/24       0.0.0.0/0           tcp dpt:139
ACCEPT     udp  --  192.168.0.0/24       0.0.0.0/0           udp dpt:138
ACCEPT     udp  --  192.168.0.0/24       0.0.0.0/0           udp dpt:137
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:20630
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:20500:20599
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:20500:20599
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20630
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:9091
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

```

and the result of "sudo iptables-save" looks like
```

# Generated by iptables-save v1.4.10 on Tue Oct 11 15:15:38 2011
*nat
:PREROUTING ACCEPT [6:650]
:INPUT ACCEPT [6:650]
:OUTPUT ACCEPT [20:2096]
:POSTROUTING ACCEPT [20:2096]
COMMIT
# Completed on Tue Oct 11 15:15:38 2011
# Generated by iptables-save v1.4.10 on Tue Oct 11 15:15:38 2011
*mangle
:PREROUTING ACCEPT [614:43206]
:INPUT ACCEPT [614:43206]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [511:75082]
:POSTROUTING ACCEPT [519:77062]
COMMIT
# Completed on Tue Oct 11 15:15:38 2011
# Generated by iptables-save v1.4.10 on Tue Oct 11 15:15:38 2011
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 445 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 139 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 138 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 137 -j ACCEPT
-A INPUT -p udp -m udp --dport 20630 -j ACCEPT
-A INPUT -p udp -m udp --dport 20500:20599 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20500:20599 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20630 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 9091 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -j DROP
-A OUTPUT -j ACCEPT
COMMIT
# Completed on Tue Oct 11 15:15:38 2011

```

It should also be noted that when I restart ubuntu, apt works exactly as it is supposed to. The only thing that has changed is iptables. Just after rebooting iptables-save looks like this:
```

# Generated by iptables-save v1.4.10 on Tue Oct 11 15:19:48 2011
*nat
:PREROUTING ACCEPT [5:620]
:INPUT ACCEPT [5:620]
:OUTPUT ACCEPT [31:2972]
:POSTROUTING ACCEPT [31:2972]
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE
COMMIT
# Completed on Tue Oct 11 15:19:48 2011
# Generated by iptables-save v1.4.10 on Tue Oct 11 15:19:48 2011
*mangle
:PREROUTING ACCEPT [125:13579]
:INPUT ACCEPT [125:13579]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [126:16771]
:POSTROUTING ACCEPT [156:20593]
-A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill
COMMIT
# Completed on Tue Oct 11 15:19:48 2011
# Generated by iptables-save v1.4.10 on Tue Oct 11 15:19:48 2011
*filter
:INPUT ACCEPT [125:13579]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [125:16685]
-A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT
-A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT
-A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT
-A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT
-A FORWARD -i virbr0 -o virbr0 -j ACCEPT
-A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable
COMMIT
# Completed on Tue Oct 11 15:19:48 2011


```

Is there some ports I need to open in order for apt to work? As far as I understand ports and networks that should not be the case. Have I overlooked something?


PS: Before I also had a -j DROP on everything in FORWARD, but the presence or absence of that line does not seem to make a difference

---

### Post by SeijiSensei on 2011-10-11
I didn't mean you should remove all the rules that had vibr0 in them.  As I said, remove the "-i vibr0" and "-o vibr0" entries to leave the interfaces unspecified (meaning "all").  

BTW, there are still vibr0 references in the FORWARD chain.

---

### Post by DavidBeijer on 2011-10-12
Oh I'm sorry I misuderstood.

I did now as you said, and it doesn't seem to make a difference. The result of all these operations:
```

~$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     tcp  --  192.168.0.0/24       0.0.0.0/0           tcp dpt:445
ACCEPT     tcp  --  192.168.0.0/24       0.0.0.0/0           tcp dpt:139
ACCEPT     udp  --  192.168.0.0/24       0.0.0.0/0           udp dpt:138
ACCEPT     udp  --  192.168.0.0/24       0.0.0.0/0           udp dpt:137
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:20630
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:20500:20599
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:20500:20599
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20630
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:9091
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:67
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            192.168.122.0/24    state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

```
and:
```

~$ sudo iptables-save
# Generated by iptables-save v1.4.10 on Wed Oct 12 12:10:19 2011
*nat
:PREROUTING ACCEPT [21:1923]
:INPUT ACCEPT [5:815]
:OUTPUT ACCEPT [38:2592]
:POSTROUTING ACCEPT [38:2592]
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE
COMMIT
# Completed on Wed Oct 12 12:10:19 2011
# Generated by iptables-save v1.4.10 on Wed Oct 12 12:10:19 2011
*mangle
:PREROUTING ACCEPT [1260:428323]
:INPUT ACCEPT [1258:428223]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [883:263470]
:POSTROUTING ACCEPT [883:263470]
-A POSTROUTING -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill
COMMIT
# Completed on Wed Oct 12 12:10:19 2011
# Generated by iptables-save v1.4.10 on Wed Oct 12 12:10:19 2011
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 445 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 139 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 138 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 137 -j ACCEPT
-A INPUT -p udp -m udp --dport 20630 -j ACCEPT
-A INPUT -p udp -m udp --dport 20500:20599 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20500:20599 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20630 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 9091 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 53 -j ACCEPT
-A INPUT -p udp -m udp --dport 67 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 67 -j ACCEPT
-A INPUT -j DROP
-A FORWARD -d 192.168.122.0/24 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 192.168.122.0/24 -j ACCEPT
-A FORWARD -j ACCEPT
-A FORWARD -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -j DROP
-A OUTPUT -j ACCEPT
COMMIT
# Completed on Wed Oct 12 12:10:19 2011

```

I have a feeling now that the FORWARD chain looks a bit silly, as first basically everything gets accepted, then rejected and then dropped. 

In any case: apt still won't update. Just to be sure, here is its output:
```

~$ sudo apt-get update
Err http://us.archive.ubuntu.com natty InRelease

Err http://security.ubuntu.com natty-security InRelease

Err http://us.archive.ubuntu.com natty-updates InRelease

Err http://security.ubuntu.com natty-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://us.archive.ubuntu.com natty Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com natty-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

```
When I reboot Ubuntu and the firewall settings are back to "default" (still the same as given some posts ago) apt will update just fine. Since these firewall settings are currently the only thing I am changing around, this must be the source of problems. Any ideas?

---

### Post by SeijiSensei on 2011-10-12
You don't appear to have a rule that permits return traffic.  Add this to the top of the ruleset:

```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

You have a rule like this for the FORWARD chain, but none for the INPUT chain.

---

### Post by DavidBeijer on 2011-10-12
Yeah, that was the issue! It makes sense that peers will have to be able to respond, and that that traffic is not discarded by some other rules. 

Thanks heaps for all your time! I learned a lot again :).

---

