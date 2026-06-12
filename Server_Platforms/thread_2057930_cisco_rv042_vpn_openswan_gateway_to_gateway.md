---
title: "cisco rv042 vpn openswan gateway to gateway"
date: 2012-09-14
forum: Server Platforms
---

### Post by razvanis on 2012-09-14
[IMG]http://oi46.tinypic.com/vq5f2b.jpg[/IMG]

config setup
    protostack=netkey
    klipsdebug=none
    plutodebug=none
    interfaces=%defaultroute
    oe=no
    nhelpers=0
    nat_traversal=yes

conn %default
    authby=secret
    type=tunnel
    left=%defaultroute
    left=Ip Server linux (unbutu)
    leftid=[EMAIL="user2@vpn2.arena.net"]user2@vpn2.arena.net[/EMAIL]
    leftsubnet=192.168.1.0/24      # or whatever your ClearOS LAN subnet is
    leftsourceip=192.168.1.1      # or whatever your ClearOS LAN IP is

conn router.arena.net
    auto=add
 #   leftnexthop=eth0        #uncomment this line if both ends of the VPN are in the same WAN subnet
    right= IP Router cisco rv042
    rightsubnet=10.206.103.0/24
    rightsourceip=10.206.103.1
    rightid=[EMAIL="user1@vpn1.arena.net"]user1@vpn1.arena.net[/EMAIL]
    dpdtimeout=120
    dpddelay=30
    dpdaction=hold  # alternatves: restart_by_peer, restart, clear, hold
    rekey=no
    auth=esp
    esp=3des-md5
    ike=3des-md5
    keyexchange=ike
    pfs=yes
 #   keyingtries=1
 #   aggrmode=yes

[IMG]http://oi49.tinypic.com/2a5x45u.jpg[/IMG]

[IMG]http://oi49.tinypic.com/ddz900.jpg[/IMG]

[IMG]http://oi45.tinypic.com/2zho012.jpg[/IMG]

[IMG]http://oi49.tinypic.com/v4qn2p.jpg[/IMG]

---

### Post by razvanis on 2012-09-14
i give you the logs please can you look it ??
cat /var/log/auth.log | grep pluto

Sep 14 18:09:05 Arena pluto[29856]: packet from 117.217.238.179:500:  sending notification PAYLOAD_MALFORMED to 117.217.238.179:500
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500:  next payload type of ISAKMP Message has an unknown value: 133
Sep 14 18:09:10 Arena pluto[29856]: | payload malformed after IV
Sep 14 18:09:10 Arena pluto[29856]: |
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500:  sending notification PAYLOAD_MALFORMED to 117.217.238.179:500
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500: ignoring Vendor ID payload [MS-MamieExists]
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500: received Vendor ID payload [RFC 3947] method set to=109
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500:  received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106,  but already using method 109
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500: ignoring Vendor ID payload [FRAGMENTATION]
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500:  ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500: ignoring Vendor ID payload [IKE CGA version 1]
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500:  af+type of ISAKMP Oakley attribute has an unknown value: 16384
Sep 14 18:09:10 Arena pluto[29856]: packet from 117.217.238.179:500:  initial Main Mode message received on 86.124.166.134:500 but no  connection has been authorized
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #20: the peer proposed: 192.168.1.0/24:0/0 -> 10.206.103.0/24:0/0
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22: responding to Quick Mode proposal {msgid:a27835be}
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22:     us:  192.168.1.0/24===86.124.166.134<86.124.166.134>[user2@vpn2.arena.net,+S=C]
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22:   them:  79.112.28.98<79.112.28.98>[user1@vpn1.arena.net,+S=C]===10.206.103.0/24
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22: keeping refhim=4294901761 during rekey
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22: Dead Peer Detection (RFC 3706): enabled
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Sep 14 18:43:40 Arena pluto[29856]: "router.arena.net" #22:  STATE_QUICK_R2: IPsec SA established tunnel mode {ESP=>0x3a884b85  <0xb0a59665 xfrm=3DES_0-HMAC_MD5 NATOA=none NATD=none DPD=enabled}
Sep 14 18:44:35 Arena pluto[29856]: "router.arena.net" #20: received Delete SA(0xf7c83068) payload: deleting IPSEC State #21
Sep 14 18:44:35 Arena pluto[29856]: "router.arena.net" #20: received and ignored informational message

root@Arena:~# service ipsec status
IPsec running  - pluto pid: 29856
pluto pid 29856
1 tunnels up
some eroutes exist

root@Arena:~# ipsec auto --status
000 using kernel interface: netkey
000 interface lo/lo ::1
000 interface lo/lo 127.0.0.1
000 interface lo/lo 127.0.0.1
000 interface eth0/eth0 xx.xxx.xxx.134
000 interface eth0/eth0 xx.xxx.xxx.134
000 interface eth0/eth0 192.168.1.100
000 interface eth0/eth0 192.168.1.100
000 interface eth1/eth1 192.168.1.1
000 interface eth1/eth1 192.168.1.1
000 %myid = (none)
000 debug none
000
000 virtual_private (%priv):
000 - allowed 0 subnets:
000 - disallowed 0 subnets:
000 WARNING: Either virtual_private= was not specified, or there was a syntax
000          error in that line. 'left/rightsubnet=%priv' will not work!
000
000 algorithm ESP encrypt: id=2, name=ESP_DES, ivlen=8, keysizemin=64, keysizemax=64
000 algorithm ESP encrypt: id=3, name=ESP_3DES, ivlen=8, keysizemin=192, keysizemax=192
000 algorithm ESP encrypt: id=6, name=ESP_CAST, ivlen=8, keysizemin=40, keysizemax=128
000 algorithm ESP encrypt: id=7, name=ESP_BLOWFISH, ivlen=8, keysizemin=40, keysizemax=448
000 algorithm ESP encrypt: id=11, name=ESP_NULL, ivlen=0, keysizemin=0, keysizemax=0
000 algorithm ESP encrypt: id=12, name=ESP_AES, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=14, name=ESP_AES_CCM_A, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=15, name=ESP_AES_CCM_B, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=16, name=ESP_AES_CCM_C, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=18, name=ESP_AES_GCM_A, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=19, name=ESP_AES_GCM_B, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=20, name=ESP_AES_GCM_C, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=252, name=ESP_SERPENT, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=253, name=ESP_TWOFISH, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP auth attr: id=1, name=AUTH_ALGORITHM_HMAC_MD5, keysizemin=128, keysizemax=128
000 algorithm ESP auth attr: id=2, name=AUTH_ALGORITHM_HMAC_SHA1, keysizemin=160, keysizemax=160
000 algorithm ESP auth attr: id=5, name=AUTH_ALGORITHM_HMAC_SHA2_256, keysizemin=256, keysizemax=256
000 algorithm ESP auth attr: id=6, name=AUTH_ALGORITHM_HMAC_SHA2_384, keysizemin=384, keysizemax=384
000 algorithm ESP auth attr: id=7, name=AUTH_ALGORITHM_HMAC_SHA2_512, keysizemin=512, keysizemax=512
000 algorithm ESP auth attr: id=251, name=(null), keysizemin=0, keysizemax=0
000
000 algorithm IKE encrypt: id=0, name=(null), blocksize=16, keydeflen=131
000 algorithm IKE encrypt: id=3, name=OAKLEY_BLOWFISH_CBC, blocksize=8, keydeflen=128
000 algorithm IKE encrypt: id=5, name=OAKLEY_3DES_CBC, blocksize=8, keydeflen=192
000 algorithm IKE encrypt: id=7, name=OAKLEY_AES_CBC, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: id=65004, name=OAKLEY_SERPENT_CBC, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: id=65005, name=OAKLEY_TWOFISH_CBC, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: id=65289, name=OAKLEY_TWOFISH_CBC_SSH, blocksize=16, keydeflen=128
000 algorithm IKE hash: id=1, name=OAKLEY_MD5, hashsize=16
000 algorithm IKE hash: id=2, name=OAKLEY_SHA1, hashsize=20
000 algorithm IKE hash: id=4, name=OAKLEY_SHA2_256, hashsize=32
000 algorithm IKE hash: id=6, name=OAKLEY_SHA2_512, hashsize=64
000 algorithm IKE dh group: id=2, name=OAKLEY_GROUP_MODP1024, bits=1024
000 algorithm IKE dh group: id=5, name=OAKLEY_GROUP_MODP1536, bits=1536
000 algorithm IKE dh group: id=14, name=OAKLEY_GROUP_MODP2048, bits=2048
000 algorithm IKE dh group: id=15, name=OAKLEY_GROUP_MODP3072, bits=3072
000 algorithm IKE dh group: id=16, name=OAKLEY_GROUP_MODP4096, bits=4096
000 algorithm IKE dh group: id=17, name=OAKLEY_GROUP_MODP6144, bits=6144
000 algorithm IKE dh group: id=18, name=OAKLEY_GROUP_MODP8192, bits=8192
000
000 stats db_ops: {curr_cnt, total_cnt, maxsz} :context={0,0,0} trans={0,0,0} attrs={0,0,0}
000
000 "router.arena.net":  192.168.1.0/24===86.124.166.134<86.124.166.134>[user2@vpn2.arena.net,+S=C]...79.112.28.98<79.112.28.98>[user1@vpn1.arena.net,+S=C]===10.206.103.0/24;  erouted; eroute owner: #22
000 "router.arena.net":     myip=192.168.1.100; hisip=10.206.103.2;
000 "router.arena.net":   ike_life: 3600s; ipsec_life: 28800s; rekey_margin: 540s; rekey_fuzz: 100%; keyingtries: 0
000 "router.arena.net":   policy: PSK+ENCRYPT+TUNNEL+PFS+DONTREKEY+IKEv2ALLOW+lKOD+rKOD; prio: 24,24; interface: eth0;
000 "router.arena.net":   dpd: action:hold; delay:30; timeout:120;
000 "router.arena.net":   newest ISAKMP SA: #20; newest IPsec SA: #22;
000 "router.arena.net":   IKE algorithms wanted:  3DES_CBC(5)_000-MD5(1)_000-MODP1536(5),  3DES_CBC(5)_000-MD5(1)_000-MODP1024(2); flags=-strict
000 "router.arena.net":   IKE algorithms found:  3DES_CBC(5)_192-MD5(1)_128-MODP1536(5), 3DES_CBC(5)_192-MD5(1)_128-MODP1024(2)
000 "router.arena.net":   IKE algorithm newest: 3DES_CBC_192-MD5-MODP1536
000 "router.arena.net":   ESP algorithms wanted: 3DES(3)_000-MD5(1)_000; flags=-strict
000 "router.arena.net":   ESP algorithms loaded: 3DES(3)_192-MD5(1)_128
000 "router.arena.net":   ESP algorithm newest: 3DES_000-HMAC_MD5; pfsgroup=<Phase1>
000
000 #22: "router.arena.net":500 STATE_QUICK_R2 (IPsec SA established);  EVENT_SA_EXPIRE in 866s; newest IPSEC; eroute owner; isakmp#20; idle;  import:not set
000 #22: "router.arena.net" esp.3a884b85@79.112.28.98  esp.b0a59665@86.124.166.134 tun.0@79.112.28.98 tun.0@86.124.166.134  ref=0 refhim=4294901761
000 #20: "router.arena.net":500 STATE_MAIN_R3 (sent MR3, ISAKMP SA  established); EVENT_SA_EXPIRE in 20021s; newest ISAKMP; lastdpd=5s(seq  in:0 out:0); idle; import:not set
000

root@Arena:~# ipsec auto --up router.arena.net
117 "router.arena.net" #23: STATE_QUICK_I1: initiate
004 "router.arena.net" #23: STATE_QUICK_I2: sent QI2, IPsec SA  established tunnel mode {ESP=>0x5d0b4ef0 <0x6ffc00da  xfrm=3DES_0-HMAC_MD5 NATOA=none NATD=none DPD=enabled}

root@Arena:~# ipsec verify
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.26/K2.6.35 (netkey)
Checking for IPsec support in kernel                            [OK]
NETKEY detected, testing for disabled ICMP send_redirects       [OK]
NETKEY detected, testing for disabled ICMP accept_redirects     [OK]
Checking for RSA private key (/etc/ipsec.secrets)               [OK]
Checking that pluto is running                                  [OK]
Pluto listening for IKE on udp 500                              [OK]
Pluto listening for NAT-T on udp 4500                           [OK]
Two or more interfaces found, checking IP forwarding            [OK]
Checking NAT and MASQUERADEing
Checking for 'ip' command                                       [OK]
Checking for 'iptables' command                                 [OK]

Opportunistic Encryption DNS checks:
   Looking for TXT in forward dns zone: Arena.net               [MISSING]
   Does the machine have at least one non-private address?      [OK]
   Looking for TXT in reverse dns zone: 134.166.124.86.in-addr.arpa.    [MISSING]

---

### Post by razvanis on 2012-09-14
Hello I managed to pick rv042 vpn between cisco router and linux server  unbutu  and it goes ping between the two locations.  I have a question  to you sir. How can i get net from location A and give net to the  location B?  More exactly in location B it is a computer that has linux  (unbutu) and this computer gives net to others  4 computers. In this  computer (server linux unbutu) that gives net to other it is installed  openswan.   To improve the banda from location B I want to achieve on  this plan:  I want to get internet banda metropolitan from location A  and send to the location B with the help of VPN.I want that Computer  from location B to receive net from location A all this is designed to  provide internet to others 4 computers that exist in location B. All  this process would increase the banda for all 4 computers with help of  location A by location B.
    If you dont understand what I mean I can make you a diagram with all proces.

I need to take internet from location A and i give to location B,   because this location ( B ) has more clients and need Internet banda  increased ( the banda that it is in location B for this moment it is not  enough , more exactly wen all the clients from location B start in the  same time to used internet the banda strangle and clients cant used  internet in normale- webpages they are loading very difficult or dont  works at all ). I do this plane because is the only way to have more  internet banda for clients in this location B. My city offers two bands  provider in Internet use. one is underground(metropolitan) and the  second is for internet use.

Both locations are in the same city from the same provider (ISP) and  between the two locations I have 100 MB of traffic (this is not internet  traffic it is Metropolitan). From location A with help of metropolitan I  want to take internet and give to location B.Because of this needs I  make a VPN to "transport" Internet traffic.And a part of this I resolved  more exacly I have ping from server linux to the router cisco rv042.Now  I need to make this staps: router cisco to give internet to the server  linux and this give internet to the clients(I think this process is  called- VPN gateway  to gateway).

 My city offers two bands provider ( ISP ) in Internet use. one is underground(metropolitan) and the second is for internet use.

yes but not working it block Server-linux and I have a question when I  give ping to the clients ( from location B ) to the cisco router it does  responding to ping, but wen I give ping from Linux to the cisco router  it responds to the ping do you think you can help me ??

---

