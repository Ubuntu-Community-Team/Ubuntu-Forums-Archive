---
title: "Does this mean someone is scanning my computer?"
date: 2012-10-30
forum: Security
---

### Post by kanadanoobie on 2012-10-30
Hello if someone could explain to me what the ufw keeps blocking ... Is it outbound traffic or incoming?  Sorry I fully intend to read up more however this is related to a business lan and if someone could share some light quicker before I can sit down and learn ufw logs better myself.

Any help would be appreciated!!

I noticed ipv6, is there a way to turn that off and since I am not utilizing it wouldn't it be more secure to turn it off?

[112240.134286] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112240.136123] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112365.567258] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112365.569171] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112491.000171] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112491.002081] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112616.433122] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112616.434889] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112741.865809] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112741.867583] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0

---

### Post by jerrrys on 2012-10-30
Look here

[http://ubuntuforums.org/showthread.php?p=12327224#post12327224](http://ubuntuforums.org/showthread.php?p=12327224#post12327224)

---

### Post by dannyboy79 on 2012-10-30
> **kanadanoobie said:**
> Hello if someone could explain to me what the ufw keeps blocking ... Is it outbound traffic or incoming?  Sorry I fully intend to read up more however this is related to a business lan and if someone could share some light quicker before I can sit down and learn ufw logs better myself.

Any help would be appreciated!!

I noticed ipv6, is there a way to turn that off and since I am not utilizing it wouldn't it be more secure to turn it off?

[112240.134286] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112240.136123] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112365.567258] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112365.569171] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112491.000171] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112491.002081] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112616.433122] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112616.434889] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[112741.865809] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1f:bc:0d:ca:43:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[112741.867583] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:00:1f:bc:0d:ca:43:86:dd SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0
any place you see SRC (that's source) which is 0.0.0.0, that's YOUR computer being the source. DST (that's the destination).
SO when I read the first log line, I see, **SRC=0.0.0.0 DST=224.0.0.1**
which means that UFW blocked "outgoing" traffic, not an issue IMO. Good luck

---

### Post by localhost8080 on 2012-10-30
this:

SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 
means its coming from you


and this:
DST=ff02:0000:0000:0000:0000:0000:0000:0001

means its a multicast packet looking for all your neighbours.

this:
[http://en.wikipedia.org/wiki/Neighbor_Discovery_Protocol](http://en.wikipedia.org/wiki/Neighbor_Discovery_Protocol)
explains why :)

---

### Post by kanadanoobie on 2012-10-30
> **localhost8080 said:**
> this:

SRC=fe80:0000:0000:0000:021f:bcff:fe0d:ca43 
means its coming from you


and this:
DST=ff02:0000:0000:0000:0000:0000:0000:0001

means its a multicast packet looking for all your neighbours.

this:
[http://en.wikipedia.org/wiki/Neighbor_Discovery_Protocol](http://en.wikipedia.org/wiki/Neighbor_Discovery_Protocol)
explains why :)

Okay well I know most ISP do these multicast to up date their routing usually in intervals of a mintue or so however what has me a little concerned is this is coming from my lan side not my wan side and I have a nat router...... I have taken steps such as static arp tables on all machines by scripts upon bootup, all my machines have static ips and ufw to accept nothing but on ssh and coming for only one machine that I use to maintain my servers.... via keys... Regardless these multicast are being directed at a machine behind my nat or they are being sent out on my lan... If its from my provider and it is routeable and can get on my lan okay... however if it is being sent from within my lan ..... Argh I am so busy right now I dont have time to or wanted to avoid breaking out wireshark....... Anyhow if anyone has anything further please help :)

---

### Post by dannyboy79 on 2012-10-31
i don't know what you're so paranoid about, you being behind a NAT Router is enough and as long as there are no ports open there's really no need to run UFW on each machine. Unless of course you're worried about internal LAN intrusion. Is this a home network or a work network?

the traffic is clearly from YOUR own machine (0.0.0.0) and it's trying to make it to 224.0.0.1 which is The All Hosts multicast group which addresses all hosts on the same network segment.

IMO, if you're behind a NAT Router there's no need for running ANY firewalls within an internal network but that's just my opinion.

---

