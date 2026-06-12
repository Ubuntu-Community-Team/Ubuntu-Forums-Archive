---
title: "IPSec L2TP Ubuntu 14.04 - How to get it running"
date: 2014-08-09
forum: Security
---

### Post by Dominic--- on 2014-08-09
Hello guys,

Let me start with the saying that I have followed 4 tutorials online on how to install a VPN IPsec server on a Ubuntu server.
When I follow the steps 1:1 it just doesn't work and my logs are full with errors where I cannot find a solution for.
Frustation point is very high at this moment...

Right now I have Ubuntu 14.04 running with this tutorial followed: [https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_14.04.html](https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_14.04.html)

Now my logs are full with these errors:
Aug  9 16:50:45 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: responding to Main Mode from unknown peer 62.45.140.54
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: Can't authenticate: no preshared key found for `149.210.135.175' and `%any'.  Attribute OAKLEY_AUTHENTICATION_METHOD
Aug  9 16:50:45 test-facility pluto[1539]: message repeated 3 times: [ "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: Can't authenticate: no preshared key found for `149.210.135.175' and `%any'.  Attribute OAKLEY_AUTHENTICATION_METHOD]
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: OAKLEY_DES_CBC is not supported.  Attribute OAKLEY_ENCRYPTION_ALGORITHM
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: OAKLEY_DES_CBC is not supported.  Attribute OAKLEY_ENCRYPTION_ALGORITHM
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: no acceptable Oakley Transform
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54 #1: sending notification NO_PROPOSAL_CHOSEN to 62.45.140.54:4
Aug  9 16:50:45 test-facility pluto[1539]: "L2TP-PSK-noNAT"[1] 62.45.140.54: deleting connection "L2TP-PSK-noNAT" instance with peer 62.45.140.54 {isakmp=#0/ipsec=#0}
Aug  9 16:50:46 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Aug  9 16:50:46 test-facility pluto[1539]: packet from 62.45.140.54:4: received Vendor ID payload [RFC 3947] meth=115, but port floating is off
Aug  9 16:50:46 test-facility pluto[1539]: packet from 62.45.140.54:4: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but port floating is off
Aug  9 16:50:46 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 16:50:46 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 16:50:46 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 16:50:46 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: responding to Main Mode from unknown peer 62.45.140.54
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: Can't authenticate: no preshared key found for `149.210.135.175' and `%any'.  Attribute OAKLEY_AUTHENTICATION_METHOD
Aug  9 16:50:46 test-facility pluto[1539]: message repeated 3 times: [ "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: Can't authenticate: no preshared key found for `149.210.135.175' and `%any'.  Attribute OAKLEY_AUTHENTICATION_METHOD]
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: OAKLEY_DES_CBC is not supported.  Attribute OAKLEY_ENCRYPTION_ALGORITHM
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: OAKLEY_DES_CBC is not supported.  Attribute OAKLEY_ENCRYPTION_ALGORITHM
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: no acceptable Oakley Transform
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54 #2: sending notification NO_PROPOSAL_CHOSEN to 62.45.140.54:4
Aug  9 16:50:46 test-facility pluto[1539]: "L2TP-PSK-noNAT"[2] 62.45.140.54: deleting connection "L2TP-PSK-noNAT" instance with peer 62.45.140.54 {isakmp=#0/ipsec=#0}
Aug  9 16:50:48 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Aug  9 16:50:48 test-facility pluto[1539]: packet from 62.45.140.54:4: received Vendor ID payload [RFC 3947] meth=115, but port floating is off
Aug  9 16:50:48 test-facility pluto[1539]: packet from 62.45.140.54:4: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but port floating is off
Aug  9 16:50:48 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 16:50:48 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 16:50:48 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 16:50:48 test-facility pluto[1539]: packet from 62.45.140.54:4: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: responding to Main Mode from unknown peer 62.45.140.54
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: Can't authenticate: no preshared key found for `149.210.135.175' and `%any'.  Attribute OAKLEY_AUTHENTICATION_METHOD
Aug  9 16:50:48 test-facility pluto[1539]: message repeated 3 times: [ "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: Can't authenticate: no preshared key found for `149.210.135.175' and `%any'.  Attribute OAKLEY_AUTHENTICATION_METHOD]
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: OAKLEY_DES_CBC is not supported.  Attribute OAKLEY_ENCRYPTION_ALGORITHM
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: OAKLEY_DES_CBC is not supported.  Attribute OAKLEY_ENCRYPTION_ALGORITHM
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: no acceptable Oakley Transform
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #3: sending notification NO_PROPOSAL_CHOSEN to 62.45.140.54:4
Aug  9 16:50:48 test-facility pluto[1539]: "L2TP-PSK-noNAT"[3] 62.45.140.54: deleting connection "L2TP-PSK-noNAT" instance with peer 62.45.140.54 {isakmp=#0/ipsec=#0}
root@test-facility:/etc/ipsec.d# 

So it is bitching about OAKLEY and there cannot be a PSK found for %any....

Here are my config files:

root@test-facility:/etc/ipsec.d# cat road-warrior.conf
conn L2TP-PSK-noNAT
  authby=secret
  pfs=no
  auto=add
  keyingtries=3
  rekey=no
  ikelifetime=8h
  keylife=1h
  type=transport
  left=149.210.135.175 
  leftprotoport=17/1701
  right=%any
  rightprotoport=17/%any

conn L2TP-PSK-NAT
  rightsubnet=vhost:%priv
  also=L2TP-PSK-noNAT

---------------------------------

root@test-facility:/etc/ipsec.d# cat road-warrior.secrets 
149.210.135.175 %any: PSK "***"

---------------------------------

root@test-facility:/etc/ipsec.d# cat /etc/ipsec.conf
version 2.0

config setup
  dumpdir=/var/run/pluto/
  nat_traversal=no
  virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
  oe=off
  protostack=netkey
  keep_alive=10

include /etc/ipsec.d/*.conf

---------------------------------

root@test-facility:/etc/xl2tpd# cat xl2tpd.conf
[global]
ipsec saref = yes

[lns default]
ip range = 10.10.10.2-10.10.10.200  
local ip = 10.10.10.1
refuse chap = no
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

-----------------------------------

Can someone point me in the right direction?

Thanks in advance!

---

### Post by Dominic--- on 2014-08-09
First I removed this line in /etc/ipsec.conf
include /etc/ipsec.d/*.conf

Then I got returned other errors so since that didn't provide a solutation I reversed that action and restarted ipsec.
Now I got this message:

Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: Main mode peer ID is ID_IPV4_ADDR: '192.168.0.105'
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[5] 62.45.140.54 #5: switched from "L2TP-PSK-noNAT" to "L2TP-PSK-noNAT"
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[6] 62.45.140.54 #5: deleting connection "L2TP-PSK-noNAT" instance with peer 62.45.140.54 {isakmp=#0/ipsec=#0}
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[6] 62.45.140.54 #5: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[6] 62.45.140.54 #5: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-noNAT"[6] 62.45.140.54 #5: the peer proposed: 149.210.135.175/32:17/1701 -> 192.168.0.105/32:17/0
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-NAT"[3] 62.45.140.54 #6: responding to Quick Mode proposal {msgid:01000000}
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-NAT"[3] 62.45.140.54 #6:     us: 149.210.135.175<149.210.135.175>:17/1701
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-NAT"[3] 62.45.140.54 #6:   them: 62.45.140.54[192.168.0.105]:17/1701===192.168.0.105/32
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-NAT"[3] 62.45.140.54 #6: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-NAT"[3] 62.45.140.54 #6: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-NAT"[3] 62.45.140.54 #6: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 18:15:41 test-facility pluto[1587]: "L2TP-PSK-NAT"[3] 62.45.140.54 #6: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xa31a9bbe <0x36fc282d xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=none DPD=none}
Aug  9 18:16:16 test-facility pluto[1587]: "L2TP-PSK-noNAT"[6] 62.45.140.54 #5: received Delete SA(0xa31a9bbe) payload: deleting IPSEC State #6
Aug  9 18:16:16 test-facility pluto[1587]: "L2TP-PSK-noNAT"[6] 62.45.140.54 #5: **ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory**
Aug  9 18:16:16 test-facility pluto[1587]: "L2TP-PSK-noNAT"[6] 62.45.140.54 #5: deleting connection "L2TP-PSK-NAT" instance with peer 62.45.140.54 {isakmp=#0/ipsec=#0}

So that was an improvement, somehow...

Then added a key in my register of Windows 7 and rebooted... ([http://support.microsoft.com/kb/310109](http://support.microsoft.com/kb/310109))
And guess what...connected in a few seconds to my VPN server via L2TP with IPsec encryption.

There really should be a tutorial of troubleshooting the top 20 error messages when configuring IPsec on Linux, from what I read on the net I am not  the only one with this issue.
(that is why i posted the solution, hope someone benefits from it)

---

### Post by Dominic--- on 2014-08-09
Never mind. VPN connects though but when I sniif with Wireshark the line isn't encrypted.
Still investigating further.

---

### Post by Dominic--- on 2014-08-10
Fixed. My server doesnt NAT, so this piece is not needed so removed it:
conn L2TP-PSK-NAT
  rightsubnet=vhost:%priv
  also=L2TP-PSK-noNAT

And when that's done NAT Traversel must be set to yes.
nat_traversal=yes

Now I have a working connection with the packets in ESP encapsulation.
Modified the iptables and allowed ipv4 forwarding and now it fucntions as my gateway.

Hope this helpes someone out there sometime.

---

### Post by Vadim_Bogatov on 2014-08-11
You can find UBUNTU IPSec/L2TP VPN configuration right here [https://www.youtube.com/watch?v=DoYVkapRUno](https://www.youtube.com/watch?v=DoYVkapRUno)

---

