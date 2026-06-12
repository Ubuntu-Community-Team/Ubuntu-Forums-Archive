---
title: "iptables and dhcp"
date: 2009-07-11
forum: Security
---

### Post by ooobooontooo on 2009-07-11
Hi,

I have a box which is configured with iptables and gets its ip dynamically from a dhcp. Do I need to explicitly allow dhcp in my iptables script? So far, it's been working despite the fact that all unspecified incoming connections should be dropped and logged (I saw no trace of it in the logs). I read somewhere that dhcp operates with 'raw packets' which iptables can't detect...is this the case and is it true for all dhcp servers? Stranger still, I seem to be getting traces of other people's dhcp requests on my logs (because all dhcp requests go to broadcast). How come it picks up other people's requests and not the DHCPOFFER packets if dhcp interaction is done in raw packets?

P.S. If you recommend that I explicitly allow dhcp in iptables, could you please give reference as to how? Right now, I have:
```
iptables -A INPUT -i eth0 -p udp --dport 68 --sport 67 -j ACCEPT
```
That doesn't seem restrictive enough...doesn't that accept the dhcp requests of other people on my network as well?

Thanks in advance. Please let me know if any part seems unclear.

---

### Post by gombadi on 2009-07-11
> 
So far, it's been working despite the fact that all unspecified incoming connections should be dropped and logged (I saw no trace of it in the logs)


I would guess the reason it is working is because of timing. Your machine comes up, asks for an ip address from the dhcp server and then loads the firewall. Do you know when the firewall is loaded relative to the interface coming up?

> 
I read somewhere that dhcp operates with 'raw packets' which iptables can't detect


Do you have a reference for this information? I have trouble believing it :-)

> 
That doesn't seem restrictive enough...doesn't that accept the dhcp requests of other people on my network as well?


Yes it will accept packets from any source. If you want to take it a step further then you could find out the ip address and/or mac address of the dhcp server and add clauses so you only accept packets from that machine. Depends on how restrictive you want to be.

---

### Post by ooobooontooo on 2009-07-11
> I would guess the reason it is working is because of timing. Your machine comes up, asks for an ip address from the dhcp server and then loads the firewall. Do you know when the firewall is loaded relative to the interface coming up?
My firewall script is /etc/network/if-pre-up.d/00-firewall

> Do you have a reference for this information? I have trouble believing it
These links prove the existence of raw sockets and that they do bypass iptables:
[http://en.wikipedia.org/wiki/Raw_socket]("http://en.wikipedia.org/wiki/Raw_socket")
[http://www.linuxchix.org/content/courses/security/raw_sockets]("http://www.linuxchix.org/content/courses/security/raw_sockets")
This link is to show that dhcp uses raw sockets:
[http://www.mail-archive.com/netfilter@lists.samba.org/msg03189.html]("http://www.mail-archive.com/netfilter@lists.samba.org/msg03189.html")

> Yes it will accept packets from any source. If you want to take it a step further then you could find out the ip address and/or mac address of the dhcp server and add clauses so you only accept packets from that machine. Depends on how restrictive you want to be.
Thanks I wasn't thinking straight on that one...

Anyway, I talked to a couple of people today, and it does seem that dhcp uses raw sockets to communicate so that's why my iptables script wasn't blocking it..,but it is still strange that my log records other people's dhcp requests and it seems that there was one case where the dhcp server contacted my box directly (with source port 67 and dest port 68)...I don't know what that's about....

EDIT: Fixed one of the links.

---

### Post by The Cog on 2009-07-12
Very early on in your iptables INPUT rules should be a rule that allows packets that are RELATED,ESTABLISHED. This allows incoming respones to outgoing connections/requests back in. Such a rule will of course than allow in replies to your DHCP requests.

---

### Post by ooobooontooo on 2009-07-12
> **The Cog said:**
> Very early on in your iptables INPUT rules should be a rule that allows packets that are RELATED,ESTABLISHED. This allows incoming respones to outgoing connections/requests back in. Such a rule will of course than allow in replies to your DHCP requests.

Yes I do have that rule (although I don't have the RELATED state included), but dhcp first works by broadcasting the DHCPOFFER no? Also, the DHCPREQUEST is broadcasted as well right? I find it hard to believe iptables will count a udp packet that is broadcasted in response to a broadcast as ESTABLISHED....

---

### Post by The Cog on 2009-07-12
> **ooobooontooo said:**
> I find it hard to believe iptables will count a udp packet that is broadcasted in response to a broadcast as ESTABLISHED....Use of a broadcast response was noted in [http://www.faqs.org/rfcs/rfc1542.html](http://www.faqs.org/rfcs/rfc1542.html) section 4.1.2 sixteen years ago as only being for supporting "older implementations".  And I am sure that the writers of iptables are able to understand BOOTP/DHCP protocol quite well.

Without the RELATED rule, you may find that FTP data transfers time out - they happen on a different port to the control messages that initiate them, and I think the RELATED rule is to cover that kind of situation.

---

### Post by ooobooontooo on 2009-07-12
> **The Cog said:**
> Use of a broadcast response was noted in [http://www.faqs.org/rfcs/rfc1542.html](http://www.faqs.org/rfcs/rfc1542.html) section 4.1.2 sixteen years ago as only being for supporting "older implementations".  And I am sure that the writers of iptables are able to understand BOOTP/DHCP protocol quite well.

Without the RELATED rule, you may find that FTP data transfers time out - they happen on a different port to the control messages that initiate them, and I think the RELATED rule is to cover that kind of situation.

Excellent link. Thank you. I look forward to reading it. So are you saying that it is the ESTABLISHED rule which allows dhcp traffic rather than raw sockets?

Regarding the RELATED rule, I don't really use ftp, and I can always use passive mode if I wanted to. The only use for the RELATED state that I have is for icmp and I take care of that in a different chain. Thank you for your suggestion though.:D

---

### Post by The Cog on 2009-07-13
> **ooobooontooo said:**
> So are you saying that it is the ESTABLISHED rule which allows dhcp traffic rather than raw sockets?
I have never found a need to configure iptables to permit packets in to port 68 explicitly. I *assume* this is because iptables sees the outgoing broadcast and knows to allow replies back in. I also *assume* this is part of the ESTABLISHED rule. It might be interesting to try DHCP with and without that rule in place to see the difference, but I haven't done so.

---

### Post by HermanAB on 2009-07-13
Just to chip in on FTP:
Netfilter has a special FTP tracking module that allows it to make FTP work despite the port changes.  There is a similar tracker for RPC used with NFS.

---

### Post by koenn on 2009-07-13
I was going to call  'bovine excrement' on most of this thread (dhcp uses udp ports 67 and 68 - that'd be udp sockets, not raw sockets; ESTABLISHED and RELATED don't mean a thing in a stateless protocol such as udp ... ; you need to explicitely allow traffic out to udp/67 and in from udp/67 for dhcp to work across a firewall ; .... ) ...
when I thought I'd better check before running my mouth of

so, i released my dhcp lease, brought down my eth0 
, including IPv6, setup iptables to DROP everything anywhere, (at some point, I even added explicit DROP rules for DHCP ...)  and run dhclient to try and get an IP address. guess what ...

```

Listening on LPF/eth0/00:50:04:35:38:32
Sending on   LPF/eth0/00:50:04:35:38:32
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Operation not permitted

root@knix:~# ifconfig eth0 inet6 down
root@knix:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:04:35:38:32 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10620603 (10.1 MB)  TX bytes:927036 (905.3 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          <snip>


root@knix:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
DROP       udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
DROP       udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 

root@knix:~# dhclient
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:04:35:38:32
Sending on   LPF/eth0/00:50:04:35:38:32
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.251 from 192.168.1.1
DHCPREQUEST of 192.168.1.251 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.251 from 192.168.1.1
bound to 192.168.1.251 -- renewal in 16968 seconds.
root@knix:~# 


```

so, did I miss something ? what exactly is happening here ?

---

### Post by koenn on 2009-07-13
> **ooobooontooo said:**
> 
P.S. If you recommend that I explicitly allow dhcp in iptables, could you please give reference as to how? Right now, I have:
```
iptables -A INPUT -i eth0 -p udp --dport 68 --sport 67 -j ACCEPT
```
That doesn't seem restrictive enough...doesn't that accept the dhcp requests of other people on my network as well?

You can't filter on addresses because the whole point of dhcp is that it assigns an address. At best you can try to limit some of it to the broadcast-address in stead on any address, but what's the point, really ?

It's in the nature of dhcp that it has to work network-wide so i don't really see what you mean with 'not restrictive enough'. 
Are you talking about a firewall on a dhcp client or a dhcp server ?

---

### Post by The Cog on 2009-07-14
> **koenn said:**
> 
so, did I miss something ? what exactly is happening here ?
You are dropping everything. It can't even get the packets out because of the output DROP (hence the send_packet permission denied messages). You would be better off using an output polict that permits anything, and just fiddling with the input policies.

You are wrong about UDP being stateless. Although a single packet doesn't contain flags indicating the overall connection state, it is perfectly possible to infer the state of a UDP connection by looking at a sequence of packets and remembering what has gone before. It makes sense for a firewall that sees an outgoing DHCP request packet to expect an incoming response in the near future. Although the UDP datagram is stateless, its contents certainly are not. And firewalls are not limited to considering only the TCP/UDP headers - they are allowed to (and often do) examine content. Even if they don't understand the UDP content, they are well capable of figuring out associations by address:port pairs talking to each other.

---

### Post by koenn on 2009-07-14
> **The Cog said:**
> You are dropping everything. It can't even get the packets out because of the output DROP (hence the send_packet permission denied messages). You would be better off using an output polict that permits anything, and just fiddling with the input policies.

never mind the send_packet perm denied, I"m only doing that the drop my dhcp lease and leave my NIC completely unconfigured.

you're missing the point. I do drop everything (**on purpose**) yet dhclient manages to do the full dhcp dialogue of discover, offer, request, acknowledge and configure my network card. Kinda weird, no ?

---

### Post by koenn on 2009-07-14
> **The Cog said:**
> 
You are wrong about UDP being stateless. Although a single packet doesn't contain flags indicating the overall connection state, it is perfectly possible to infer the state of a UDP connection by looking at a sequence of packets and remembering what has gone before. It makes sense for a firewall that sees an outgoing DHCP request packet to expect an incoming response in the near future. Although the UDP datagram is stateless, its contents certainly are not. And firewalls are not limited to considering only the TCP/UDP headers - they are allowed to (and often do) examine content. Even if they don't understand the UDP content, they are well capable of figuring out associations by address:port pairs talking to each other.
but we're discussing iptables here, not firewalls in general, and iptables 'state' and contrack 'cstate' define 
```
ESTABLISHED meaning that
the  packet is associated with a connection which has seen pack&#8208;
ets in both directions, NEW meaning that the packet has  started
a  new  connection,  or  otherwise  associated with a connection
 which has not seen packets in both directions, and RELATED mean&#8208;
ing that the packet is starting a new connection, but is associ&#8208;
ated with an existing connection,
```
it's going to be pretty difficult to apply that to a *connectionless* protocol.

I'll give you that one could infer state from the datagrams' payloads, and that some firewalls do inspect payload. I don't know of any that actually try to track dhcp dialogs, and I'm not convinced iptables tries to match a state "RELATED" to dhcp broadcast packets. 

In fact, I was going to test if it does - i.e. check if I needed a match on RELATED for dhcp to work, hence the DROP policies. turns out the test produced the unexpected results posted earlier.

---

### Post by The Cog on 2009-07-15
> **koenn said:**
> never mind the send_packet perm denied, I"m only doing that the drop my dhcp lease and leave my NIC completely unconfigured.

you're missing the point. I do drop everything (**on purpose**) yet dhclient manages to do the full dhcp dialogue of discover, offer, request, acknowledge and configure my network card. Kinda weird, no ?

Interesting point. I wonder if DHCP bypasses iptables. It may be necessary to do that because the IP stack isn't fully functional until it has an IP address.

---

### Post by The Cog on 2009-07-15
> 
it's going to be pretty difficult to apply that to a *connectionless* protocol.

I'll give you that one could infer state from the datagrams' payloads, and that some firewalls do inspect payload. I don't know of any that actually try to track dhcp dialogs, and I'm not convinced iptables tries to match a state "RELATED" to dhcp broadcast packets. 


It may be connectionless at the IP layer, but many UDP connections are far from connectionless. Voice over IP VOIP, several other streaming protocols, TFTP file transfer, OpenVPN are all examples of connection oriented protocols that use UDP for transport. And there is generally no need to examine hte payload either. If you see a UDP packet going from 1.2.3.4-999 to 5.6.7.8-7000, is is reasonable to infer that a UDP packet a short time later from 5.6.7.8-7000 to 1.2.3.4-999 is part of a "connection". The only difficulty is in knowing when the connection has been broken because UDP doesn't of itself indicate the connection state. Most firewalls (and I guess conntrack is included in this) implement an inactivity timeout for these connections.

Try this command:
**sudo cat /proc/net/ip_conntrack**
You need to have an iptables rule that causes connection tracking for the file to exist. Mine even includes "connections" to my subnet broadcast destination.

---

### Post by koenn on 2009-07-15
> **The Cog said:**
> It may be connectionless at the IP layer, but many UDP connections are far from connectionless. Voice over IP VOIP, several other streaming protocols, TFTP file transfer, OpenVPN are all examples of connection oriented protocols that use UDP for transport
.
it's connectionless at the *transport* layer. The examples you give are *applications*, all of which implement their own, application-level mechanism to deal with the stateless nature of UDP, i.e. the applications have state, the transport protocol, udp,  doesn't.
eg. VOIP implements sessions, tftp sends numbered data paclets and numbered ACK packets to keep track of the file transfer, and openvpn makes client and server authenticate and sends its packets as payload of other packets, so if a (tcp) connection over openvpn exist, it only exists when udp payload is delivered, the udp itself is still as stateless as ever.
> **Iptables tutorial, chapter on contrack]UDP connections are in them selves not stateful connections, but rather stateless. There are several reasons why, mainly because they don't contain any connection establishment or connection closing said:**
> 

-----


[QUOTE=The Cog;7619758] And there is generally no need to examine hte payload either. If you see a UDP packet going from 1.2.3.4-999 to 5.6.7.8-7000, is is reasonable to infer that a UDP packet a short time later from 5.6.7.8-7000 to 1.2.3.4-999 is part of a "connection". 
.
Ok, that would be a reasonable assumption - but still an assumption. As it happens (I looked it up :) ), this is apparently how iptables contrack tracks udp "connections" . 

I find this assumption less reasonable when it concerns broadcasts, as in the case of dhcp, which started this discussion : how are you going to match replies to requests if replies have dest=255.255.255.2555 and could be intended for any host on the subnet ?

---

