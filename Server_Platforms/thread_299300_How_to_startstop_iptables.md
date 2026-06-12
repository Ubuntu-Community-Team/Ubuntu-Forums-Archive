---
title: "How to start/stop iptables"
date: 2006-11-13
forum: Server Platforms
---

### Post by satimis on 2006-11-13
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64


How to start/stop/restart iptables?

ls /etc/init.d/ | grep iptables
No printout

It has been compiled in the kernel as modules;

$ cat /boot/config-2.6.15-26-amd64-server | grep -i "CONFIG_IP_NF"```

CONFIG_IP_NF_CONNTRACK=m
CONFIG_IP_NF_CT_ACCT=y
CONFIG_IP_NF_CONNTRACK_MARK=y
# CONFIG_IP_NF_CONNTRACK_EVENTS is not set
CONFIG_IP_NF_CONNTRACK_NETLINK=m
CONFIG_IP_NF_CT_PROTO_SCTP=m
CONFIG_IP_NF_FTP=m
CONFIG_IP_NF_IRC=m
CONFIG_IP_NF_NETBIOS_NS=m
CONFIG_IP_NF_TFTP=m
CONFIG_IP_NF_AMANDA=m
CONFIG_IP_NF_PPTP=m
CONFIG_IP_NF_QUEUE=m
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_LIMIT=m
CONFIG_IP_NF_MATCH_IPRANGE=m
CONFIG_IP_NF_MATCH_MAC=m
CONFIG_IP_NF_MATCH_PKTTYPE=m
CONFIG_IP_NF_MATCH_MARK=m
CONFIG_IP_NF_MATCH_MULTIPORT=m
CONFIG_IP_NF_MATCH_TOS=m
CONFIG_IP_NF_MATCH_RECENT=m
CONFIG_IP_NF_MATCH_ECN=m
CONFIG_IP_NF_MATCH_DSCP=m
CONFIG_IP_NF_MATCH_AH_ESP=m
CONFIG_IP_NF_MATCH_LENGTH=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_TCPMSS=m
CONFIG_IP_NF_MATCH_HELPER=m
CONFIG_IP_NF_MATCH_STATE=m
CONFIG_IP_NF_MATCH_CONNTRACK=m
CONFIG_IP_NF_MATCH_OWNER=m
CONFIG_IP_NF_MATCH_PHYSDEV=m
CONFIG_IP_NF_MATCH_ADDRTYPE=m
CONFIG_IP_NF_MATCH_REALM=m
CONFIG_IP_NF_MATCH_SCTP=m
CONFIG_IP_NF_MATCH_DCCP=m
CONFIG_IP_NF_MATCH_COMMENT=m
CONFIG_IP_NF_MATCH_CONNMARK=m
CONFIG_IP_NF_MATCH_CONNBYTES=m
CONFIG_IP_NF_MATCH_HASHLIMIT=m
CONFIG_IP_NF_MATCH_STRING=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_IP_NF_TARGET_TCPMSS=m
CONFIG_IP_NF_TARGET_NFQUEUE=m
CONFIG_IP_NF_NAT=m
CONFIG_IP_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
CONFIG_IP_NF_TARGET_NETMAP=m
CONFIG_IP_NF_TARGET_SAME=m
CONFIG_IP_NF_NAT_SNMP_BASIC=m
CONFIG_IP_NF_NAT_IRC=m
CONFIG_IP_NF_NAT_FTP=m
CONFIG_IP_NF_NAT_TFTP=m
CONFIG_IP_NF_NAT_AMANDA=m
CONFIG_IP_NF_NAT_PPTP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_TOS=m
CONFIG_IP_NF_TARGET_ECN=m
CONFIG_IP_NF_TARGET_DSCP=m
CONFIG_IP_NF_TARGET_MARK=m
CONFIG_IP_NF_TARGET_CLASSIFY=m
CONFIG_IP_NF_TARGET_TTL=m
CONFIG_IP_NF_TARGET_CONNMARK=m
CONFIG_IP_NF_TARGET_CLUSTERIP=m
CONFIG_IP_NF_RAW=m
CONFIG_IP_NF_TARGET_NOTRACK=m
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
CONFIG_IP_NF_ARP_MANGLE=m

```

Where is its config file for changing policy?

TIA

B.R.
satimis

---

### Post by harrysales on 2006-11-14
Not sure if I'm telling 'me granny how to suck eggs' but if you issue
sudo iptables -L 
and the service is running you will get an out put similar to this

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

which is the output for having no rules defined 

Harry

---

### Post by frodon on 2006-11-14
Here is a guide i wrote which will give you some basis :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

### Post by satimis on 2006-11-14
Hi frodon,

It is a nice guide.  Tks.

Now I have the 3 scripts created and activated.

Before I was looking around on /etc/init.d/iptables start/stop/restart etc. and couldn't find it.

I need to stop iptables to check whether it blocks port 80 disallowing me to run "127.0.0.1/localhost" on firefox to popup Apache2 default page.  After stopping iptables I found it is not the cause of firewall.

Tks again.

B.R.
satimis

---

### Post by krisvloeberghs on 2007-12-14
Hey Frodon,

I too have to thank you for this great HOWTO.  I simply copied your scripts and changed the name of the network interface.  This now all seems to work fine, in the sence that indeed I can access the internet, and that incoming requests are blocked.
However, it seems to be blocking a bit too much.

I for instance cannot ping to my Ubuntu machine anymore, which appears to be because of security reasons.  This though is not relevant for my situation, since my LAN is protected by means of the firewall on my D-Link router (128 bit wpa encryption).  Internally I need to be able to ping, since the wireless network card of my Ubuntu machine is sometimes experiencing connection problems.  Pinging allows me to verify whether that connection is working or not.  How can I fix this?

On top of that, and this is actually what itsis all about, I also cannot access my Ubuntu machine through NX client ([www.nomachine.com](www.nomachine.com)) anymore.
I use NX to remotely connect to my Ubuntu machine from my Windows laptop (it's a company laptop, so I unfortunately have to run Windows on it).  I'm trying to use port 443 for NX, so that I can access my home Linux system from work, where I'm working behind a firewall.

Thanks a lot already!

Best regard,
Kris

---

