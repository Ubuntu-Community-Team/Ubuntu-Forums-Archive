---
title: "Failed To Stop Firewall..."
date: 2007-02-11
forum: Server Platforms
---

### Post by play0r on 2007-02-11
after i upgraded to kernel image 2.6.20 firestarter fails to stop.
if anyone has made a custom kernel image of 2.6.20 & uses firestarter, it would be greatly appreciated if someone could give me some insight on which module needs to be enabled within the netfilter values to allow firestarter to stop.

thanks in advance,
play0r

---

### Post by maciu on 2007-02-12
same problem here, firestarter refuses to stop... NEED HELP ! anyone ?

---

### Post by play0r on 2007-02-12
i fixed it in the worst way imaginable...
i compiled everything within netfilter. this is by no means a good solution, but it works. :-# 
if anyone knows what specific module(s) need to be selected it would be greatly appreciated if you would post a follow-up. i honestly do not want to go through a process of elimination with the netfilter modules. :roll: 

ez,
play0r

---

### Post by maciu on 2007-02-12
god damn lucky you i network cant live without netfilter, still any ideas what modules are conflicting woth firestarter ?
:(

---

### Post by LaLLi on 2007-02-13
My Firestarter is acting crazy. After a fresh none of my internet wielding programs work(Firefox, Gaim, Evolution. If I start Firestarter it reports some "incidents" with unfamiliar ports. When I try to stop Firestarter it won't stop but my applications can access the internet like they should. Firestarter doesnt like my custom compiled 2.6.20 kernel :P

---

### Post by Hav0k on 2007-02-15
Anyone found any solutions? I have the same exact problem. If you start Firestarter, you can't connect to anything. You can stop Firestarter (either GUI or command line) and it says failed to stop, but I'm pretty sure it does because you can suddenly connect to the internet again.

(This is also with kernel 2.6.20 - had to update so hibernate would work)

As stated above, recompiled including everything Netfilter and it seems to work. Still have the "Failed to stop firewall" issue when doing Firestarter -p, but it does stop it, and Firestarter -s starts it again. Guess this works for now! :)

---

### Post by raffytaffy on 2007-02-16
im also having odd behavior with 2.6.20 on kubuntu 2.6.20. When i open firestarter and add rule, my firewall starts blocking everything. i have to reboot my machine.  i get some sort of error message about network during boot...but the screen goes by too fast for me to make note of it. is there any place i can view such logs to post and study them better?

---

### Post by edubbler on 2007-02-17
Just looking at the config file for the kernel...

It has

# CONFIG_NETFILTER_XT_MATCH_SCTP is not set
# CONFIG_NETFILTER_XT_MATCH_STATISTIC is not set

It *should* have

# CONFIG_NETFILTER_XT_MATCH_SCTP is not set
CONFIG_NETFILTER_XT_MATCH_STATE=m
# CONFIG_NETFILTER_XT_MATCH_STATISTIC is not set

I'm using the same .config file I used for 2.6.19, but once it starts compiling that line disappears. weird.

---

### Post by play0r on 2007-02-17
the guys at netfilter reworked the naming scheme of ip_conntrack to nf_conntrack, there is proc support for ip_conntrack built-in if you select it.
i just selected & built all the modules within the netfilter section. now everything is fully functional, but as i said this is by no means a good solution.

ez,
play0r

---

### Post by maulattu on 2007-02-17
The same for me...
Now it's the 4 time i'm trying to recompile the kernel (2.6.20-ck1). now i checked all the options under the netfilter section, _except_ those specified here:
[http://www.fs-security.com/docs/kernel.php](http://www.fs-security.com/docs/kernel.php)
that is "raw table support" (I disabled also the ipv6 netfilter since I don't need ipv6 support, I disabled it).
now it's recompiling, let's wait ](*,)
anyway, when firestarter is up, i can ping any address (e.g. [www.google.it)](www.google.it)), but i can't use any program (firefox, konqueror, apt-get...). when i stop the firewall, it said "fail", but the iptable tables are empty (sudo iptables -L) and i can surf the net...

---

### Post by maulattu on 2007-02-17
> **play0r said:**
> there is proc support for ip_conntrack built-in if you select it.

precisely, where is it?
using "make xconfig", it maybe in "networking, networking options, networking packet filtering framework, core netfilter configuration", right?:confused:

---

### Post by edubbler on 2007-02-17
I got it to work!  Here is the relevant excerpt from my .config file:

```
CONFIG_NETFILTER=y
CONFIG_NETFILTER_DEBUG=y

#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_NETLINK=y
# CONFIG_NETFILTER_NETLINK_QUEUE is not set
# CONFIG_NETFILTER_NETLINK_LOG is not set
CONFIG_NF_CONNTRACK_ENABLED=m
CONFIG_NF_CONNTRACK_SUPPORT=y
# CONFIG_IP_NF_CONNTRACK_SUPPORT is not set
CONFIG_NF_CONNTRACK=m
# CONFIG_NF_CT_ACCT is not set
# CONFIG_NF_CONNTRACK_MARK is not set
# CONFIG_NF_CONNTRACK_SECMARK is not set
# CONFIG_NF_CONNTRACK_EVENTS is not set
# CONFIG_NF_CT_PROTO_SCTP is not set
# CONFIG_NF_CONNTRACK_AMANDA is not set
CONFIG_NF_CONNTRACK_FTP=m
# CONFIG_NF_CONNTRACK_H323 is not set
CONFIG_NF_CONNTRACK_IRC=m
# CONFIG_NF_CONNTRACK_NETBIOS_NS is not set
# CONFIG_NF_CONNTRACK_PPTP is not set
# CONFIG_NF_CONNTRACK_SIP is not set
# CONFIG_NF_CONNTRACK_TFTP is not set
# CONFIG_NF_CT_NETLINK is not set
CONFIG_NETFILTER_XTABLES=m
# CONFIG_NETFILTER_XT_TARGET_CLASSIFY is not set
# CONFIG_NETFILTER_XT_TARGET_DSCP is not set
CONFIG_NETFILTER_XT_TARGET_MARK=m
# CONFIG_NETFILTER_XT_TARGET_NFQUEUE is not set
# CONFIG_NETFILTER_XT_TARGET_NFLOG is not set
# CONFIG_NETFILTER_XT_TARGET_SECMARK is not set
# CONFIG_NETFILTER_XT_MATCH_COMMENT is not set
# CONFIG_NETFILTER_XT_MATCH_CONNTRACK is not set
# CONFIG_NETFILTER_XT_MATCH_DCCP is not set
# CONFIG_NETFILTER_XT_MATCH_DSCP is not set
# CONFIG_NETFILTER_XT_MATCH_ESP is not set
# CONFIG_NETFILTER_XT_MATCH_HELPER is not set
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
# CONFIG_NETFILTER_XT_MATCH_POLICY is not set
# CONFIG_NETFILTER_XT_MATCH_MULTIPORT is not set
# CONFIG_NETFILTER_XT_MATCH_PKTTYPE is not set
# CONFIG_NETFILTER_XT_MATCH_QUOTA is not set
# CONFIG_NETFILTER_XT_MATCH_REALM is not set
# CONFIG_NETFILTER_XT_MATCH_SCTP is not set
CONFIG_NETFILTER_XT_MATCH_STATE=m
# CONFIG_NETFILTER_XT_MATCH_STATISTIC is not set
# CONFIG_NETFILTER_XT_MATCH_STRING is not set
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m
# CONFIG_NETFILTER_XT_MATCH_HASHLIMIT is not set

#
# IP: Netfilter Configuration
#
CONFIG_NF_CONNTRACK_IPV4=m
CONFIG_NF_CONNTRACK_PROC_COMPAT=y
CONFIG_IP_NF_QUEUE=y
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_IPRANGE=m
CONFIG_IP_NF_MATCH_TOS=m
# CONFIG_IP_NF_MATCH_RECENT is not set
# CONFIG_IP_NF_MATCH_ECN is not set
# CONFIG_IP_NF_MATCH_AH is not set
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_OWNER=m
CONFIG_IP_NF_MATCH_ADDRTYPE=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_IP_NF_TARGET_TCPMSS=m
CONFIG_NF_NAT=m
CONFIG_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
# CONFIG_IP_NF_TARGET_REDIRECT is not set
# CONFIG_IP_NF_TARGET_NETMAP is not set
# CONFIG_IP_NF_TARGET_SAME is not set
# CONFIG_NF_NAT_SNMP_BASIC is not set
CONFIG_NF_NAT_FTP=m
CONFIG_NF_NAT_IRC=m
# CONFIG_NF_NAT_TFTP is not set
# CONFIG_NF_NAT_AMANDA is not set
# CONFIG_NF_NAT_PPTP is not set
# CONFIG_NF_NAT_H323 is not set
# CONFIG_NF_NAT_SIP is not set
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_TOS=m
# CONFIG_IP_NF_TARGET_ECN is not set
# CONFIG_IP_NF_TARGET_TTL is not set
# CONFIG_IP_NF_RAW is not set
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m

```

Regarding my initial question: conn tracking needs to be enabled for xt_state to show up.

---

### Post by play0r on 2007-02-17
> **maulattu said:**
> precisely, where is it?
using "make xconfig", it maybe in "networking, networking options, networking packet filtering framework, core netfilter configuration", right?:confused:

it is in:
```
Networking -> Networking Options -> Networking Packet Filtering Framework -> IP: Netfilter Configuration -> <M> IPv4 connection tracking support (required for NAT) -> <*> proc/sysctl compatibility with old connection tracking
```

ez,
play0r

p.s.
thanks for the post of your config edubbler, i'll get around to removing the unneeded modules next time i compile a 2.6.20.* kernel.

---

### Post by maulattu on 2007-02-18
> **play0r said:**
> it is in:
```
Networking -> Networking Options -> Networking Packet Filtering Framework -> IP: Netfilter Configuration -> <M> IPv4 connection tracking support (required for NAT) -> <*> proc/sysctl compatibility with old connection tracking
```

ez,
play0r

p.s.
thanks for the post of your config edubbler, i'll get around to removing the unneeded modules next time i compile a 2.6.20.* kernel.

thank you ;)
anyway, i recompiled the kernel with all the netfilter options selected (M) and now it works :popcorn:

---

