---
title: "Firestarter blocking loads of connections"
date: 2006-06-22
forum: Server Platforms
---

### Post by akudewan on 2006-06-22
I installed firestarter recently. Its working fine. But I see loads and loads of connections being blocked in the "Events" tab. The list just gets bigger and bigger. Is this normal? Why is this happening ?

Attached: Screenshot
[[IMG]http://img208.imageshack.us/img208/391/firestarterblocking6wy.th.png[/IMG]](http://img208.imageshack.us/my.php?image=firestarterblocking6wy.png)

---

### Post by Xecuter on 2006-06-22
You should be glad its blocking it. I don't know what most of it is, but that's what a firewall does; blocks incoming packets.

---

### Post by Azrael on 2006-06-22
[SIZE=-1]32459 is the default port ****used  by the bittorrent client uTorrent I believe. Ever use(d) that?
[/SIZE]

---

### Post by akudewan on 2006-06-22
Never used uTorrent. I usually use azureus, and I haven't started it since I booted today.

---

### Post by akudewan on 2006-06-22
The same thing is happening in Windows. (I dual boot). I have the windows firewall enabled, and its dropping loads of UDP packets. Port 32459 seems to be the favourite.

In firestarter, there is an option called "Lookup Hostname". I did that on a few blocked connections, and here's some of the hostnames that I got:
c-69-180-244-220.hsd1.tn.comcast.net
207.173.176.60.broad.hz.zj.dynamic.cndata.com
vyk-cti.zno.skynet.cz
cpe-72-179-135-252.satx.res.rr.com
pc62.broad.dynamic.qz.fj.cn.cndata.com
[[IMG]http://img71.imageshack.us/img71/7690/resolip1tu.th.png[/IMG]](http://img71.imageshack.us/my.php?image=resolip1tu.png)
Many of the hostnames didn't show up.

The hosts look totally random to me.

Could there be a virus on my local network thats causing this?

---

### Post by Ride Jib on 2006-06-22
Typical peer to peer traffic. Virus on your local network? No. That is inbound traffic getting dropped, not outbound. If it were virus traffic (which it's not) the infected host would be outside your network.

---

### Post by Oceola on 2006-06-25
If you do a little searching you can find some fairly complete lists of the port designations and where the packets could possibly be from. 
**Here's a few of what you're most likely to see: **
compressnet         2/udp   Management Utility
compressnet         2/tcp   Management Utility
ftp-data           20/udp   File Transfer [Default Data]
ftp-data           20/tcp   File Transfer [Default Data]
ftp                21/udp   File Transfer [Control]
ftp                21/tcp   File Transfer [Control]
audiogalaxy        21/tcp   
ssh                22/udp   SSH Remote Login Protocol
ssh                22/tcp   SSH Remote Login Protocol
pcanywhere         22/udp   
epmap             135/tcp   DCE endpoint resolution
epmap             135/udp   DCE endpoint resolution
windows-messenger   135/udp   
microsoft-rpc     135/tcp  
profile           136/tcp   PROFILE Naming System           
profile           136/udp   PROFILE Naming System           
netbios-ns        137/udp   NETBIOS Name Service    
netbios-ns        137/tcp   NETBIOS Name Service    
netbios-dgm       138/udp   NETBIOS Datagram Service
netbios-dgm       138/tcp   NETBIOS Datagram Service
netbios-ssn       139/udp   NETBIOS Session Service
netbios-ssn       139/tcp   NETBIOS Session Service
kdm              1024/tcp
blackjack        1025/udp   network blackjack
blackjack        1025/tcp   network blackjack
cap              1026/udp   Calender Access Protocol
cap              1026/tcp   Calender Access Protocol
weathercast      1026/udp   
windows-messenger-service  1026/udp  
windows-messenger-service  1026/udp   
windows-messenger-service  1027/udp
solid-mux        1029/tcp   Solid Mux Server
solid-mux        1029/udp   Solid Mux Server
## BBN IAD(Bolt, Beranek and Newman)Interface Access Device, operates as a bridge/router between IP, X.25,asynch links, etc."
iad1             1030/udp  
iad1             1030/tcp   BBN IAD
iad2             1031/udp   BBN IAD
iad2             1031/tcp   BBN IAD
iad3             1032/tcp   BBN IAD
iad3             1032/udp   BBN IAD
netinfo-local    1033/tcp   local netinfo port
netinfo-local    1033/udp   local netinfo port
netspy           1033/tcp

Looking in the /etc/services file may have a small listing and then there's a more complete list with nmap. Numbers above a certain point are not registered with Iana.
If you use iptraf in conjunction with the Firewall and allow the reverse look-up you can see where the packets came from and sometimes you can use nettools to find out who the url number is assigned to if there's no name, you can also take the name, if no url number and place it in "Lookup and it will either return a url at the top of the list or a series of servers. In some cases all you'll get is the network(isp) they're on and in some cases the url won't be recognized. In a number of cases I've found reversing the url will give the owner. This may be like a bidi function like locale for right or left reading or a privacy mask function. 

;)

---

### Post by akudewan on 2006-06-25
Oceola: You are 133t!!!! :-D 

Over the past 2 days, the frequency of these packets has reduced drastically. Yesterday, I was getting just one or two every 30 minutes, and today I'm getting 4-5 every 15 minutes. The ports have also been different, not the usual.

Oceola: I looked up some of these ports, and most of them seem to be unassigned. One of them is an radmin-port and one is Sun-RPC Portmap. A couple of ports are also used by Trojans. So I don't know what to conclude.

I also tried reverse look-up on iptraf, its very helpful, but I'm sure my ISP doesn't like me doing that, (as it may put a lot of load  on their nameservers).

I've never used nettools and nmap. I'm installing them right now and checking them out.

I'm glad that the number of packets has reduced now. Don't know how and why. ;)

---

### Post by Ride Jib on 2006-06-25
[QUOTE=akudewan]Oceola: You are 133t!!!! :-D 
I looked up some of these ports, and most of them seem to be unassigned. One of them is an radmin-port and one is Sun-RPC Portmap. A couple of ports are also used by Trojans. So I don't know what to conclude.

I also tried reverse look-up on iptraf, its very helpful, but I'm sure my ISP doesn't like me doing that, (as it may put a lot of load  on their nameservers).

I've never used nettools and nmap. I'm installing them right now and checking them out.

I'm glad that the number of packets has reduced now. Don't know how and why. ;)[/QUOTE]

You're just wasting your time. I've already said this is typical peer to peer traffic. And just because a port is 'associated with a trojan' means absolutely nothing in regards to the traffic that you are seeing. If the traffic you were seeing was strictly on the 'trojan' port it might be something to look at, but it's not the case.

---

### Post by akudewan on 2006-06-26
[QUOTE=Ride Jib]You're just wasting your time. I've already said this is typical peer to peer traffic. And just because a port is 'associated with a trojan' means absolutely nothing in regards to the traffic that you are seeing. If the traffic you were seeing was strictly on the 'trojan' port it might be something to look at, but it's not the case.[/QUOTE]

And why in blazes am I receiving packets even though I'm not running any p2p client/daemon/program ?

(Edit: I realize that my tone was slightly rude, I apologise for this.)

---

### Post by Azrael on 2006-06-26
[quote=akudewan]And why in blazes am I receiving packets even though I'm not running any p2p client/daemon/program ?[/quote]
Maybe these packets are not meant for you, but are routed wrongly somewhere. Maybe someone is trying to bypass the MAC address filtering on your wireless network by spoofing your MAC address thus causing a mess. Maybe some remote  piece of bittorrent software has a corrupted list of peers. It could be anything like that.

But if you want to know instead of speculate, then use Ethereal already (which really isn't that complicated at all). It will tell you exactly what the contents of these 'rogue' packets is.

---

### Post by Oceola on 2006-06-27
Another possible answer is revolving url's which are employed by some ISPs if you do not have a fixed URL. Although you may be on a different URL everytime, the spam packet or maybe ICMP signal is directed at the URL not specifically you.

Figure an ISP has a range of 25.230.20.0 to 25.230.20.10. Each time you login, remember there's other folks connecting as well, you get a different URL in the range. The sites which record the activity of the URL, which may be all they see, may send ICMP packets or spam, depending on the site and it's functions to the URL which it recorded from a previous user of that URL or they may just assault the range, indiscriminantly. There's also a security consideration where packets sent to a pre-defined sequence of ports is in actuality an access code but this is in some form of development, unless I read wrong and it may be some folks have decided to see if it's employed as of yet.

If you're curious about the site, using Nettools will give you their ISP in some cases but not the actual site unless they have a fixed ID, just a range. In some cases if you track who the packet came from it may signal the site. Best to let the packets drop silently and just pay attention. It does get annoying sometimes.

---

### Post by akudewan on 2006-06-28
Oceola: What you say does make sense. And I think I have done enough digging on this matter. One final thing that I'd like to show:

Here is the data from one of these packets, that I got from ethereal:

```

0000  00 10 b5 12 bb f7 00 c0  69 0c 3b 68 08 00 45 00   ........ i.;h..E.
0010  00 5a 2d 18 00 00 6c 11  af 25 55 4c ff 67 0a 0a   .Z-...l. .%UL.g..
0020  13 98 4b 99 7e cb 00 46  b7 50 64 31 3a 61 64 32   ..K.~..F .Pd1:ad2
0030  3a 69 64 32 30 3a 38 d8  b5 96 d4 a1 39 05 40 4d   :id20:8. ....9.@M
0040  d3 2a ba e2 b4 8f 70 8e  85 64 65 31 3a 71 34 3a   .*....p. .de1:q4:
0050  70 69 6e 67 31 3a 74 38  3a 55 0b 65 43 7b 80 28   ping1:t8 :U.eC{.(
0060  86 31 3a 79 31 3a 71 65                            .1:y1:qe         

```

And here is another one: (They look quite similar, both contain "ping1:t8" and some other things):

```

0000  00 10 b5 12 bb f7 00 c0  69 0c 3b 68 08 00 45 00   ........ i.;h..E.
0010  00 5a 1f e8 00 00 68 11  59 c6 cb df ef 63 0a 0a   .Z....h. Y....c..
0020  13 98 33 23 7e cb 00 46  7b 93 64 31 3a 61 64 32   ..3#~..F {.d1:ad2
0030  3a 69 64 32 30 3a ec 68  ba 0c b1 16 48 f4 6c ec   :id20:.h ....H.l.
0040  90 3d 70 fc 74 d5 fb 0e  21 54 65 31 3a 71 34 3a   .=p.t... !Te1:q4:
0050  70 69 6e 67 31 3a 74 38  3a 6f 73 3c a2 22 c4 47   ping1:t8 :os<.".G
0060  3e 31 3a 79 31 3a 71 65                            >1:y1:qe         

```

This is mostly greek and latin to me, but does anyone know what this means?

---

### Post by Oceola on 2006-06-28
A lot would depend on the url where the packets came from as well as the size and which port. Like if the packet was aimed at your 22 port it maybe the signal is looking for an open 22 port (remote login) Frankly I can make out the ping but it's in hex and coded text other than the ping I can't tell what it's doing. If on 445 it's a MS directory lookup on 135 some other type of identifier. There may be some kind of library which provides descriptions for standard signals.

---

### Post by Azrael on 2006-06-28
akudewan, doesn't ethereal give you application layer protocol information on the packets? I could look it up manually I guess, but I don't feel like going through the hassle of decyphering.

---

### Post by akudewan on 2006-06-29
Here's another one of these packets, with more details:

```

No.     Time        Source                Destination           Protocol Info
    497 440.062465  80.224.99.212         10.10.19.152          UDP      Source
port: 9005  Destination port: 16574

Frame 497 (104 bytes on wire, 104 bytes captured)
    Arrival Time: Jun 29, 2006 13:48:14.105903000
    Time delta from previous packet: 56.930218000 seconds
    Time since reference or first frame: 440.062465000 seconds
    Frame Number: 497
    Packet Length: 104 bytes
    Capture Length: 104 bytes
    Protocols in frame: eth:ip:udp:data
    Coloring Rule Name: UDP
    Coloring Rule String: udp
Ethernet II, Src: Axxceler_0c:3b:68 (00:c0:69:0c:3b:68), Dst: AcctonTe_12:bb:f7
(00:10:b5:12:bb:f7)
    Destination: AcctonTe_12:bb:f7 (00:10:b5:12:bb:f7)
        Address: AcctonTe_12:bb:f7 (00:10:b5:12:bb:f7)
        .... ...0 .... .... .... .... = Multicast: This is a UNICAST frame
        .... ..0. .... .... .... .... = Locally Administrated Address: This is a
 FACTORY DEFAULT address
    Source: Axxceler_0c:3b:68 (00:c0:69:0c:3b:68)
        Address: Axxceler_0c:3b:68 (00:c0:69:0c:3b:68)
        .... ...0 .... .... .... .... = Multicast: This is a UNICAST frame
        .... ..0. .... .... .... .... = Locally Administrated Address: This is a
 FACTORY DEFAULT address
    Type: IP (0x0800)
Internet Protocol, Src: 80.224.99.212 (80.224.99.212), Dst: 10.10.19.152 (10.10.
19.152)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 90
    Identification: 0xee20 (60960)
    Flags: 0x00
        0... = Reserved bit: Not set
        .0.. = Don't fragment: Not set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 102
    Protocol: UDP (0x11)
    Header checksum: 0x941c [correct]
        Good: True
        Bad : False
    Source: 80.224.99.212 (80.224.99.212)
    Destination: 10.10.19.152 (10.10.19.152)
User Datagram Protocol, Src Port: 9005 (9005), Dst Port: 16574 (16574)
    Source port: 9005 (9005)
    Destination port: 16574 (16574)
    Length: 70
    Checksum: 0x7d66 [correct]
Data (62 bytes)

0000  64 31 3a 61 64 32 3a 69 64 32 30 3a c2 d4 8b 2b   d1:ad2:id20:...+
0010  7a 29 43 74 80 1a a3 e2 ef 52 0e 8c 17 67 3b 52   z)Ct.....R...g;R
0020  65 31 3a 71 34 3a 70 69 6e 67 31 3a 74 38 3a 79   e1:q4:ping1:t8:y
0030  af 49 00 63 de 5a fc 31 3a 79 31 3a 71 65         .I.c.Z.1:y1:qe

```

Any ideas?

---

### Post by akudewan on 2006-06-29
Another interesting development. It seems there's a bigger LAN outside my LAN, and someone with the IP address 10.10.18.187 is trying to access my samba shares! This IP doesn't come under my LAN, here's what tracepath gives:

```

$ tracepath 10.10.18.187
 1:  ranjan404 (10.10.19.152)                               0.454ms pmtu 1500
 1:  10.10.19.129 (10.10.19.129)                          asymm 35   2.459ms
 2:  192.168.100.1 (192.168.100.1)                        asymm 36   4.649ms
 3:  dialpool-210-214-35-8.maa.sify.net (210.214.35.8)      8.226ms !H
     Resume: pmtu 1500

```

sify.net is my ISP.

Btw, thanks to all the people who have been helping me out. You've been really patient with me :)

---

### Post by Ride Jib on 2006-06-29
Ok, to clarify.... just because the payload of these packets say 'ping' does not mean the packets themselves are pings or ICMP (like someone previously mentioned). ICMP (aka ping) does not have a port associated with it (unlike UDP and TCP) thus these firewall drops you are seeing are not pings. You stated the traffic is UDP which is completely synonymous with peer to peer traffic, especially running on random high ports. Looking at the payload of those two items you posted, this is typical of BitTorrent traffic. You may also see payloads with contents of "peer announce" in them as well as things like "find node".

---

### Post by MJN on 2006-06-30
Ping is a user-interface to the ICMP protocol and uses the registered port number 7.
 
You're right in that the 'ping' you see in the packets above is just conincidence of letters - the ping tool doesn't send an ASCII 'ping' character but rather an echo-request flag.
 
Back to the question in hand, I agree with the above that's it's likely to be Torrent traffic due to either you now using an IP address once used by someone else and thus other torrent clients trying to get in touch with you.
 
Mathew

---

### Post by akudewan on 2006-06-30
Hi guys,

I have kept an eye on my IP address every time I logon to the internet. I noticed that whenever I am assigned a particular IP address, I keep getting loads and loads of packets. If I simply logout and login, then my IP address changes, and these packets either stop, or reduce, and/or the ports change.

There are p2p software, especially bittorrent clients, that remember IP addresses of peers. Since my IP address is dynamic, my IP address was probably someone else's IP address sometime back, and I'm simply receiving packets meant for that person.

Oceola, Ride Jib: You had suggested this earlier, and now I have reason to believe that you are right.

Lets wrap up this case. Thanks for all the help guys.

---

