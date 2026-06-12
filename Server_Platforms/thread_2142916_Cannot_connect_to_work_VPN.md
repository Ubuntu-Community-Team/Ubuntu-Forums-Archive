---
title: "Cannot connect to work VPN"
date: 2013-05-07
forum: Server Platforms
---

### Post by jimmyhart on 2013-05-07
Hi all. I've recently got 13.04 installed on my work machine and have everything set up and working like a dream (for work tasks Ubuntu is a revelation compared to Windows 7!), but I can't connect to VPN. I'm using L2TP IPsec VPN Manager 1.0.9.

I have entered the ip address, secret key, username and password exactly as I have on my Windows VPN connection, but it doesn't work. I've had various error logs and below is the latest. If anyone can provide any advice, it would be much appreciated.

```

[COLOR=#000000]May 07 09:25:44.312 ipsec_setup: Starting Openswan IPsec U2.6.38/K3.8.0-19-generic...[/COLOR]
[COLOR=#000000]May 07 09:25:44.483 ipsec__plutorun: Starting Pluto subsystem...[/COLOR]
[COLOR=#000000]May 07 09:25:44.496 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d[/COLOR]
[COLOR=#000000]May 07 09:25:44.497 recvref[30]: Protocol not available[/COLOR]
[COLOR=#000000]May 07 09:25:44.497 xl2tpd[4439]: This binary does not support kernel L2TP.[/COLOR]
[COLOR=#000000]May 07 09:25:44.497 xl2tpd[4450]: xl2tpd version xl2tpd-1.3.1 started on jameshart-Precision-M6700 PID:4450[/COLOR]
[COLOR=#000000]May 07 09:25:44.498 xl2tpd[4450]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.[/COLOR]
[COLOR=#000000]May 07 09:25:44.498 xl2tpd[4450]: Forked by Scott Balmos and David Stipp, (C) 2001[/COLOR]
[COLOR=#000000]May 07 09:25:44.500 xl2tpd[4450]: Inherited by Jeff McAdams, (C) 2002[/COLOR]
[COLOR=#000000]May 07 09:25:44.501 xl2tpd[4450]: Forked again by Xelerance ([www.xelerance.com]("http://www.xelerance.com")) (C) 2006[/COLOR]
[COLOR=#000000]May 07 09:25:44.501 xl2tpd[4450]: Listening on IP address 0.0.0.0, port 1701[/COLOR]
[COLOR=#000000]May 07 09:25:44.502 Starting xl2tpd: xl2tpd.[/COLOR]
[COLOR=#000000]May 07 09:25:44.525 ipsec__plutorun: 002 added connection description "valtech"[/COLOR]
[COLOR=#000000]May 07 09:25:44.803 104 "valtech" #1: STATE_MAIN_I1: initiate[/COLOR]
[COLOR=#000000]May 07 09:25:44.803 003 "valtech" #1: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000004][/COLOR]
[COLOR=#000000]May 07 09:25:44.804 003 "valtech" #1: ignoring Vendor ID payload [FRAGMENTATION][/COLOR]
[COLOR=#000000]May 07 09:25:44.804 003 "valtech" #1: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] method set to=106 [/COLOR]
[COLOR=#000000]May 07 09:25:44.804 106 "valtech" #1: STATE_MAIN_I2: sent MI2, expecting MR2[/COLOR]
[COLOR=#000000]May 07 09:25:44.804 003 "valtech" #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: i am NATed[/COLOR]
[COLOR=#000000]May 07 09:25:44.805 108 "valtech" #1: STATE_MAIN_I3: sent MI3, expecting MR3[/COLOR]
[COLOR=#000000]May 07 09:25:44.805 004 "valtech" #1: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=oakley_3des_cbc_192 prf=oakley_sha group=modp1024}[/COLOR]
[COLOR=#000000]May 07 09:25:44.805 117 "valtech" #2: STATE_QUICK_I1: initiate[/COLOR]
[COLOR=#000000]May 07 09:25:44.806 003 "valtech" #2: ignoring informational payload, type IPSEC_RESPONDER_LIFETIME msgid=5fbb2b57[/COLOR]
[COLOR=#000000]May 07 09:25:44.806 003 "valtech" #2: our client subnet returned doesn't match my proposal - us:192.168.1.69/32 vs them:86.185.58.201/32[/COLOR]
[COLOR=#000000]May 07 09:25:44.806 003 "valtech" #2: Allowing questionable proposal anyway [ALLOW_MICROSOFT_BAD_PROPOSAL][/COLOR]
[COLOR=#000000]May 07 09:25:44.807 000 "valtech" #2: peer client type is FQDN[/COLOR]
[COLOR=#000000]May 07 09:25:44.807 003 "valtech" #2: peer client subnet returned doesn't match my proposal - us:80.169.55.100/32 vs them:86.185.58.201/32[/COLOR]
[COLOR=#000000]May 07 09:25:44.807 003 "valtech" #2: Allowing questionable proposal anyway [ALLOW_MICROSOFT_BAD_PROPOSAL][/COLOR]
[COLOR=#000000]May 07 09:25:44.807 003 "valtech" #2: IDcr was FQDN: vtlonvpn01.UK.valtech.com, using NAT_OA=0.0.0.0/32 as IDcr[/COLOR]
[COLOR=#000000]May 07 09:25:44.808 004 "valtech" #2: STATE_QUICK_I2: sent QI2, IPsec SA established transport mode {ESP=>0x9677b464 <0x698cfe95 xfrm=3DES_0-HMAC_SHA1 NATOA=none NATD=none DPD=none}[/COLOR]
[COLOR=#000000]May 07 09:25:45.809 xl2tpd[4450]: Connecting to host 80.169.55.100, port 1701[/COLOR]
[COLOR=#000000]May 07 09:25:50.815 xl2tpd[4450]: Maximum retries exceeded for tunnel 54766.  Closing.[/COLOR]
[COLOR=#ff0000]May 07 09:25:50.816 [ERROR  410]   Connection attempt to 'valtech' timed out[/COLOR]
[COLOR=#000000]May 07 09:25:50.819 xl2tpd[4450]: Connection 0 closed to 80.169.55.100, port 1701 (Timeout)[/COLOR]
[COLOR=#000000]May 07 09:25:50.827 xl2tpd[4450]: death_handler: Fatal signal 15 received[/COLOR]
[COLOR=#000000]May 07 09:25:50.828 Stopping xl2tpd: xl2tpd.[/COLOR]
[COLOR=#000000]May 07 09:25:50.839 ipsec_setup: Stopping Openswan IPsec...[/COLOR]
```
[COLOR=#000000]
[/COLOR]

---

### Post by matt_symes on 2013-05-07
Thread moved to **Server Platforms**.

This may be a better sub forum for an answer.

---

### Post by darkod on 2013-05-07
> **jimmyhart said:**
> Hi all. I've recently got 13.04 installed on my work machine and have everything set up and working like a dream (for work tasks Ubuntu is a revelation compared to Windows 7!), but I can't connect to VPN. I'm using L2TP IPsec VPN Manager 1.0.9.

I have entered the ip address, secret key, username and password exactly as I have on my Windows VPN connection, but it doesn't work. I've had various error logs and below is the latest. If anyone can provide any advice, it would be much appreciated.

```

[COLOR=#000000]May 07 09:25:44.312 ipsec_setup: Starting Openswan IPsec U2.6.38/K3.8.0-19-generic...[/COLOR]
[COLOR=#000000]May 07 09:25:44.483 ipsec__plutorun: Starting Pluto subsystem...[/COLOR]
[COLOR=#000000]May 07 09:25:44.496 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d[/COLOR]
[COLOR=#000000]May 07 09:25:44.497 recvref[30]: Protocol not available[/COLOR]
[COLOR=#000000]May 07 09:25:44.497 xl2tpd[4439]: [/COLOR][COLOR=#ff0000]This binary does not support kernel L2TP.[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]May 07 09:25:44.497 xl2tpd[4450]: xl2tpd version xl2tpd-1.3.1 started on jameshart-Precision-M6700 PID:4450[/COLOR]
[COLOR=#000000]May 07 09:25:44.498 xl2tpd[4450]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.[/COLOR]
[COLOR=#000000]May 07 09:25:44.498 xl2tpd[4450]: Forked by Scott Balmos and David Stipp, (C) 2001[/COLOR]
[COLOR=#000000]May 07 09:25:44.500 xl2tpd[4450]: Inherited by Jeff McAdams, (C) 2002[/COLOR]
[COLOR=#000000]May 07 09:25:44.501 xl2tpd[4450]: Forked again by Xelerance ([www.xelerance.com]("http://www.xelerance.com")) (C) 2006[/COLOR]
[COLOR=#000000]May 07 09:25:44.501 xl2tpd[4450]: Listening on IP address 0.0.0.0, port 1701[/COLOR]
[COLOR=#000000]May 07 09:25:44.502 Starting xl2tpd: xl2tpd.[/COLOR]
[COLOR=#000000]May 07 09:25:44.525 ipsec__plutorun: 002 added connection description "valtech"[/COLOR]
[COLOR=#000000]May 07 09:25:44.803 104 "valtech" #1: STATE_MAIN_I1: initiate[/COLOR]
[COLOR=#000000]May 07 09:25:44.803 003 "valtech" #1: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000004][/COLOR]
[COLOR=#000000]May 07 09:25:44.804 003 "valtech" #1: ignoring Vendor ID payload [FRAGMENTATION][/COLOR]
[COLOR=#000000]May 07 09:25:44.804 003 "valtech" #1: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] method set to=106 [/COLOR]
[COLOR=#000000]May 07 09:25:44.804 106 "valtech" #1: [/COLOR][COLOR=#ff0000]STATE_MAIN_I2: sent MI2, expecting MR2[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]May 07 09:25:44.804 003 "valtech" #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: i am NATed[/COLOR]
[COLOR=#000000]May 07 09:25:44.805 108 "valtech" #1: [/COLOR][COLOR=#ff0000]STATE_MAIN_I3: sent MI3, expecting MR3[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]May 07 09:25:44.805 004 "valtech" #1: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=oakley_3des_cbc_192 prf=oakley_sha group=modp1024}[/COLOR]
[COLOR=#000000]May 07 09:25:44.805 117 "valtech" #2: STATE_QUICK_I1: initiate[/COLOR]
[COLOR=#000000]May 07 09:25:44.806 003 "valtech" #2: ignoring informational payload, type IPSEC_RESPONDER_LIFETIME msgid=5fbb2b57[/COLOR]
[COLOR=#000000]May 07 09:25:44.806 003 "valtech" #2: [/COLOR][COLOR=#ff0000]our client subnet returned doesn't match my proposal - us:192.168.1.69/32 vs them:86.185.58.201/32[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]May 07 09:25:44.806 003 "valtech" #2: Allowing questionable proposal anyway [ALLOW_MICROSOFT_BAD_PROPOSAL][/COLOR]
[COLOR=#000000]May 07 09:25:44.807 000 "valtech" #2: peer client type is FQDN[/COLOR]
[COLOR=#000000]May 07 09:25:44.807 003 "valtech" #2: [/COLOR][COLOR=#ff0000]peer client subnet returned doesn't match my proposal - us:80.169.55.100/32 vs them:86.185.58.201/32[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]May 07 09:25:44.807 003 "valtech" #2: Allowing questionable proposal anyway [ALLOW_MICROSOFT_BAD_PROPOSAL][/COLOR]
[COLOR=#000000]May 07 09:25:44.807 003 "valtech" #2: IDcr was FQDN: vtlonvpn01.UK.valtech.com, using NAT_OA=0.0.0.0/32 as IDcr[/COLOR]
[COLOR=#000000]May 07 09:25:44.808 004 "valtech" #2: STATE_QUICK_I2: sent QI2, IPsec SA established transport mode {ESP=>0x9677b464 <0x698cfe95 xfrm=3DES_0-HMAC_SHA1 NATOA=none NATD=none DPD=none}[/COLOR]
[COLOR=#000000]May 07 09:25:45.809 xl2tpd[4450]: Connecting to host 80.169.55.100, port 1701[/COLOR]
[COLOR=#000000]May 07 09:25:50.815 xl2tpd[4450]: Maximum retries exceeded for tunnel 54766.  Closing.[/COLOR]
[COLOR=#ff0000]May 07 09:25:50.816 [ERROR  410]   Connection attempt to 'valtech' timed out[/COLOR]
[COLOR=#000000]May 07 09:25:50.819 xl2tpd[4450]: Connection 0 closed to 80.169.55.100, port 1701 (Timeout)[/COLOR]
[COLOR=#000000]May 07 09:25:50.827 xl2tpd[4450]: death_handler: Fatal signal 15 received[/COLOR]
[COLOR=#000000]May 07 09:25:50.828 Stopping xl2tpd: xl2tpd.[/COLOR]
[COLOR=#000000]May 07 09:25:50.839 ipsec_setup: Stopping Openswan IPsec...[/COLOR]
```
[COLOR=#000000]
[/COLOR]

I don't know this program but you have loads of suspicious errors in the log. Are you sure you can do this L2TP connection with this client? Are you sure all settings are set up correctly? It also complains about subnets not matching, you might need to set the remote subnet yourself in this ubuntu client.

I have highlighted few entries in the log above although I can't say I understand them fully.

Have you tried any other vpn client? Or do you need a client at all?

Once as a test, I connected to our work VPN with my ubuntu desktop at home, and I simply used the VPN section in Network Manager, without any special clients. Note that I think the connection was PPTP, not L2TP over IPsec, but I would look into Network Manager options too.

---

### Post by jimmyhart on 2013-05-07
When I connect via Windows (it's the same with the people who have Macs), I have to specify a secret key/shared passphrase, I don't think the default Ubuntu manager allows for that. That's why I gave this tool a go. I tried the Cisco client and I had even less luck than with this client.

I believe I have everything set up correctly, I will post some screenshots when I am next booted into Ubuntu.

---

### Post by darkod on 2013-05-07
I can't check right now also, and I don't remember all the options in Network Manager.
But the fields it offers will depend on the type of connection. If you select PPTP, there will be no field for the IPsec shared key because it's not Ipsec connection.
If the NM offers L2TP over Ipsec as type of connection, then there should be a field for the IPsec shared key, on top of the L2TP username and password. But I have no idea if you can set that type of connection with NM at all. :) I won't be able to check until tonight too. :)

---

### Post by jimmyhart on 2013-05-07
No problem, thanks for your help so far. I've temporarily screwed up my install by trying to install nvidia drivers (can't get the panels and unity up now), so need to sort that out. When I finish work in an hour or so, I'll try and sort that out then post you some VPN info.

---

### Post by koenn on 2013-05-07
I agree with  darkod : that log suggests your side is not configured correctly, or not set up at all

I've had a quick look : default NM assumes you want  PPTP (what everybody on windows is using)
Most other VPN docu out there assumes you want OpenVPN (what everybody on Linux is using)

here's someone who figured out how to do L2PT IPsec : [http://bailey.st/blog/2011/07/14/connecting-to-a-l2tpipsec-vpn-from-ubuntu-desktop/](http://bailey.st/blog/2011/07/14/connecting-to-a-l2tpipsec-vpn-from-ubuntu-desktop/)
more here : [http://wiki.l2tpipsecvpn.tuxfamily.org/wiki/index.php?title=Main_Page](http://wiki.l2tpipsecvpn.tuxfamily.org/wiki/index.php?title=Main_Page)
looks doable.

---

### Post by d4m1r on 2013-05-08
I would Google each of those bad looking lines of the output you posted. If you solve them 1 by 1, it is bound to work.

Other than that, I have no experience dealing with L2PT IPsec unfortunately.

---

### Post by jimmyhart on 2013-05-09
Hi guys, sorry I haven't posted anything recently, I didn't have time Tuesday evening and was away all day yesterday. I'll have a look at koenn's links as well as my errors and post some information once I have it.

---

### Post by jimmyhart on 2013-05-09
Have tried to find solutions to the errors but not found anything yet. Since setting up my system again, I've installed it directly from the Ubuntu repositories rather than from ppa werner. I've got a very slightly different log which I've put below as well as the screenshots, in case they are any help. Have also put the output from sudo ipsec verify.

```
[COLOR=#000000]May 09 20:09:33.858 ipsec_setup: Stopping Openswan IPsec...[/COLOR][COLOR=#000000]May 09 20:09:35.284 Stopping xl2tpd: xl2tpd.[/COLOR]
[COLOR=#000000]May 09 20:09:35.311 ipsec_setup: Starting Openswan IPsec U2.6.38/K3.8.0-19-generic...[/COLOR]
[COLOR=#000000]May 09 20:09:35.489 Starting xl2tpd: xl2tpd.[/COLOR]
[COLOR=#ff0000]May 09 20:10:53.846 Last command timed out[/COLOR]
[COLOR=#000000]May 09 20:10:55.047 104 "vtlondon" #1: STATE_MAIN_I1: initiate[/COLOR]
[COLOR=#000000]May 09 20:10:55.047 003 "vtlondon" #1: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000004][/COLOR]
[COLOR=#000000]May 09 20:10:55.047 003 "vtlondon" #1: ignoring Vendor ID payload [FRAGMENTATION][/COLOR]
[COLOR=#000000]May 09 20:10:55.048 003 "vtlondon" #1: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] method set to=106 [/COLOR]
[COLOR=#000000]May 09 20:10:55.048 106 "vtlondon" #1: STATE_MAIN_I2: sent MI2, expecting MR2[/COLOR]
[COLOR=#000000]May 09 20:10:55.050 003 "vtlondon" #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: i am NATed[/COLOR]
[COLOR=#000000]May 09 20:10:55.050 108 "vtlondon" #1: STATE_MAIN_I3: sent MI3, expecting MR3[/COLOR]
[COLOR=#000000]May 09 20:10:55.051 004 "vtlondon" #1: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=oakley_3des_cbc_192 prf=oakley_sha group=modp1024}[/COLOR]
[COLOR=#000000]May 09 20:10:55.051 117 "vtlondon" #2: STATE_QUICK_I1: initiate[/COLOR]
[COLOR=#000000]May 09 20:10:55.051 003 "vtlondon" #2: ignoring informational payload, type IPSEC_RESPONDER_LIFETIME msgid=39e67670[/COLOR]
[COLOR=#000000]May 09 20:10:55.051 003 "vtlondon" #2: our client subnet returned doesn't match my proposal - us:192.168.1.69/32 vs them:86.146.7.169/32[/COLOR]
[COLOR=#000000]May 09 20:10:55.052 003 "vtlondon" #2: Allowing questionable proposal anyway [ALLOW_MICROSOFT_BAD_PROPOSAL][/COLOR]
[COLOR=#000000]May 09 20:10:55.052 000 "vtlondon" #2: peer client type is FQDN[/COLOR]
[COLOR=#000000]May 09 20:10:55.052 003 "vtlondon" #2: peer client subnet returned doesn't match my proposal - us:80.169.55.100/32 vs them:86.146.7.169/32[/COLOR]
[COLOR=#000000]May 09 20:10:55.052 003 "vtlondon" #2: Allowing questionable proposal anyway [ALLOW_MICROSOFT_BAD_PROPOSAL][/COLOR]
[COLOR=#000000]May 09 20:10:55.053 003 "vtlondon" #2: IDcr was FQDN: vtlonvpn01.UK.valtech.com, using NAT_OA=0.0.0.0/32 as IDcr[/COLOR]
[COLOR=#000000]May 09 20:10:55.053 004 "vtlondon" #2: STATE_QUICK_I2: sent QI2, IPsec SA established transport mode {ESP=>0x9ed1f3ba <0x5f1fcd7e xfrm=3DES_0-HMAC_SHA1 NATOA=none NATD=none DPD=none}[/COLOR]

```

```
Checking your system to see if IPsec got installed and started correctly:Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.38/K3.8.0-19-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [FAILED]


  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!


    [FAILED]


  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!


    [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [OK]
Two or more interfaces found, checking IP forwarding        Checking NAT and MASQUERADEing                                  [OK]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                               [WARNING]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]



```

---

### Post by d4m1r on 2013-05-09
Sounds like it's pointing to specific problem, have you tried doing what it says?


```
NETKEY:  Testing XFRM related proc values                      [FAILED]     Please disable /proc/sys/net/ipv4/conf/*/send_redirects   or NETKEY will cause the sending of bogus ICMP redirects!       [FAILED]     Please disable /proc/sys/net/ipv4/conf/*/accept_redirects   or NETKEY will accept bogus ICMP redirects!
```

---

### Post by jimmyhart on 2013-05-14
Not had time to look at this recently. Had another try now and I'm getting the same error as originally and running ipsec verify is now giving a different output, which is below. There's definitely something wrong with my local machine but it's difficult to pinpoint as there doesn't seem to be a consistency in the errors.

```
Checking your system to see if IPsec got installed and started correctly:Version check and ipsec on-path                             	[OK]
Linux Openswan U2.6.38/K(no kernel code presently loaded)
Checking for IPsec support in kernel                        	[FAILED]
 SAref kernel support                                       	[N/A]
Checking that pluto is running                              	[FAILED]
  whack: Pluto is not running (no "/var/run/pluto/pluto.ctl")
Two or more interfaces found, checking IP forwarding        Checking NAT and MASQUERADEing                              	[OK]
Checking for 'ip' command                                   	[OK]
Checking /bin/sh is not /bin/dash                           	[WARNING]
Checking for 'iptables' command                             	[OK]
Opportunistic Encryption Support                            	[DISABLED]

```

---

