---
title: "Out of the box &amp; ssh not working to another machine — why?"
date: 2017-12-27
forum: Server Platforms
---

### Post by gary64 on 2017-12-27
Hi,

just installed a new 16.04 server, set up ssh, but when I try to connect from the new server to another server, nothing happens:

```
ssh account@myoldserver
```

But:
• Connecting to the new server with any other server works just fine (using the stored public keys)
• Connecting to the old server with *any* other server works fine as well!

What can possibly prevent the connection?


Thanks a lot for any help!

Gary

---

### Post by howefield on 2017-12-27
Thread moved to the "*Server Platforms*" forum.

---

### Post by The Cog on 2017-12-27
Try addiing a -v flag to get more info: ssh -v  account@myoldserver

Also, "nothing happens" is unlikely. SSH has quite a long timeout (2 minutes) if it doesn't get an answer - maybe you didn't wait long enough to get the "Connection timed out" message?

---

### Post by gary64 on 2017-12-27
You’re right. After waiting long enough, I get a connection timeout:

```
ssh -v account@myoldserver
OpenSSH_7.2p2 Ubuntu-4ubuntu2.2, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to myoldserver [11.11.11.11] port 22.
debug1: connect to address 11.11.11.11 port 22: Connection timed out
ssh: connect to host myoldserver port 22: Connection timed out
```

I have no idea, why. Doing this from another machine, I get this result:

```
ssh -v account@myoldserverOpenSSH_6.9p1, LibreSSL 2.1.8
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug1: Connecting to myoldserver [11.11.11.11] port 22.
debug1: Connection established.
debug1: identity file /Users/mac/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mac/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mac/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mac/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mac/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mac/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mac/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mac/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.9
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.4
debug1: match: OpenSSH_7.4 pat OpenSSH* compat 0x04000000
debug1: Authenticating to myoldserver:22 as 'account'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client chacha20-poly1305@openssh.com <implicit> none
debug1: kex: client->server chacha20-poly1305@openssh.com <implicit> none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:dEF1CxmlXS1vJ+4WgTj/Qy7pIr3JDKDovSJrb+mx7js
debug1: Host 'myoldserver' is known and matches the ECDSA host key.
debug1: Found key in /Users/mac/.ssh/known_hosts:5
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /Users/mac/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Trying private key: /Users/mac/.ssh/id_dsa
debug1: Trying private key: /Users/mac/.ssh/id_ecdsa
debug1: Trying private key: /Users/mac/.ssh/id_ed25519
debug1: Next authentication method: keyboard-interactive
Password:
debug1: Authentication succeeded (keyboard-interactive).
Authenticated to myoldserver ([11.11.11.11]:22).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug1: Sending environment.
debug1: Sending env LANG = de_DE.UTF-8
Last login: Wed Dec 27 13:21:02 2017 from 12.12.12.12
```

---

### Post by The Cog on 2017-12-27
OK, so we are looking at a stratighforward networking or firewall issue. 
Try temporarily disabling firewalls to see if it works then.

Can you confirm that these servers (let's call them oldserver, newserver and otherserver) are all on the same network, and that they all have different IP addresses?
If they are all on the same subnet, do they all have the same subnet mask ((e.g. "/24", use **ip addr list** to see these)
After a failed connect request, ue the command **ip neigh list** and see what the entry for the failed looks like.
Are they able to ping each other?

---

### Post by SeijiSensei on 2017-12-27
Do you work for the US Department of Defense?  If not, you shouldn't be using the 11/8 subnet which belongs to DOD.  Use the address ranges set aside for private networks:  10/8, 172.16.0.0-172.31.0.0, and 192.168.0.0/16.

```

$ whois 11.0.0.0@whois.arin.net
[Querying whois.arin.net]
[whois.arin.net]

NetRange:       11.0.0.0 - 11.255.255.255
CIDR:           11.0.0.0/8
NetName:        DODIIS
NetHandle:      NET-11-0-0-0-1
Parent:          ()

NetType:        Direct Allocation
OriginAS:
Organization:   DoD Network Information Center (DNIC)
RegDate:        1984-01-19
Updated:        2007-08-22
Ref:            https://whois.arin.net/rest/net/NET-11-0-0-0-1

```

---

### Post by The Cog on 2017-12-27
Chuckle. I assume he was hiding his real address.

---

### Post by gary64 on 2017-12-27
DOD? :-)  I just changed the IP&#8217;s to arbitrary numbers :-)

All three servers are in different countries with different IP&#8217;s and different LAN IP's.

---

### Post by The Cog on 2017-12-27
So they are all on different routed subnets. Let's go to basics.
Can they ping each other by name?
If not, can they ping each other by IP address?

---

### Post by LHammonds on 2017-12-27
Sounds like a firewall issue.  Most-likely you have iptables/ufw blocking port 22 for anything but certain IP addresses.  Check the rules and add port 22 and your new server's IP...but the IP your old server sees when it is coming in...not the new server's local LAN IP.

LHammonds

---

### Post by gary64 on 2017-12-27
OK, the domains get resolved fine.
It seems ping is disabled on "oldserver"

ping OK from oldserver to newserver
ssh OK from oldserver to newserver

ping is LOST from otherserver to oldserver
ssh OK from otherserver to oldserver

ping is LOST from newserver to oldserver
ssh timeout from newserver to oldserver

---

### Post by gary64 on 2017-12-27
No ip&#8217;s are blocked from oldserver

I can ssh to "oldserver" from just about everything, but not from "newserver".

---

### Post by The Cog on 2017-12-27
The next step I woud take woudl be to use traceroute or tracepath from newserver to oldserver, to see how far the packets are getting. But you probably need a network diagram to make sense of the output.

---

### Post by gary64 on 2017-12-27
```
traceroute to myoldserver (11.11.11.11), 30 hops max, 60 byte packets 1  * * *
 2  ae0-0-25.m20-2a6.united.net.ua (176.111.48.2)  0.749 ms  0.846 ms  1.012 ms
 3  ae11-221.RT1.NTL.KIV.UA.retn.net (87.245.237.26)  0.813 ms  0.897 ms  0.797 ms
 4  ae3-4.RT.IRX.FKT.DE.retn.net (87.245.232.234)  33.216 ms et302-6.RT.IRX.FKT.DE.retn.net (87.245.234.49)  33.199 ms ae3-4.RT.IRX.FKT.DE.retn.net (87.245.232.234)  33.448 ms
 5  213.198.77.213 (213.198.77.213)  32.540 ms  32.485 ms  33.440 ms
 6  62.157.249.185 (62.157.249.185)  30.459 ms  29.546 ms  29.566 ms
 7  d-eb6-i.D.DE.NET.DTAG.DE (62.154.43.74)  33.749 ms  32.804 ms  33.443 ms
 8  80.150.170.166 (80.150.170.166)  34.001 ms  33.655 ms  33.900 ms
 9  10.255.184.138 (10.255.184.138)  33.635 ms  33.016 ms  33.082 ms
10  * * *
11  * * *
12  * * *
13  * * *
```

The newserver’s internet provider is united.net.ua. My oldserver’s internet provider is dtag.de, I can follow it to that point. Within dtag.de, there are two more hops, but not myoldserver. Is it possible that dtag.de blocks the connection to myoldserver from .ua?

---

### Post by The Cog on 2017-12-27
I don't know. I don't see why an ISP would choose to block certain addresses though. The path to oldserver from newserver ends at 10.255.184.138 which is a provate address. Try comparing that with a traceroute to oldserver from otherserver, to see if they reach a common point. I.e. is 10.255.184.138 the last router before oldserver itself? If so then is is probably an issue with oldserver itself. Did you try disabling any firewalling in oldserver?

---

### Post by gary64 on 2017-12-27
This is the traceroute from otherserver to oldserver:
```
...
 7  equinix-zurich.ch.net.dtag.de (194.42.48.56)  1.833 ms  1.821 ms  5.491 ms 8  d-eb6-i.D.DE.NET.DTAG.DE (62.154.1.106)  18.199 ms  18.060 ms  18.076 ms
 9  80.150.170.166 (80.150.170.166)  22.540 ms  22.451 ms  22.397 ms
10  * * *
11  * * *
12  * * *
```

It stops with 80.150.170.166, which is also present in the traceroute from newserver to oldserver. It doesn't make sense.

I checked firewall and there is no IP blocked. In my router I am redirecting port 22 to oldserver in my LAN. I can’t think of anything else.

---

### Post by LHammonds on 2017-12-27
> **gary64 said:**
> I checked firewall and there is no IP blocked. In my router I am redirecting port 22 to oldserver in my LAN. I can&#8217;t think of anything else.
Just so you know, the firewall (the operating system's software firewall) is most-likely set to block ALL rather than block specific IPs which is normal.
If the firewall is enabled, then you need to specifically allow port 22 in from the new server.

LHammonds

---

### Post by gary64 on 2017-12-31
Solution to the riddle:

Well, I contacted the support of the server provider and eventually they explained that ssh to other machines was blocked for security reasons... !

Thank y’all so much for your suggestions!

Gary

---

