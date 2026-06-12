---
title: "How do I see the encrypted packets sent through ssh?"
date: 2008-03-17
forum: Security Discussions
---

### Post by kevdog on 2008-03-17
Couple of questions?

Once I establish an ssh connection, how do I confirm the packets sent are really encrypted?  Can I examine the packets?  (Isnt wireshark only for wireless devices??)

Is it possible to use ssh to transmit data using no-encryption??  

Just some random thoughts?

---

### Post by The Tronyx on 2008-03-17
> **kevdog said:**
> Couple of questions?

Once I establish an ssh connection, how do I confirm the packets sent are really encrypted?  Can I examine the packets?  (Isnt wireshark only for wireless devices??)

Is it possible to use ssh to transmit data using no-encryption??  

Just some random thoughts?

1) SSH is what it is, a secure connection.  If you want information transmitted in plain text you can use telnet.

2) Wireshark is not for wireless only, it is a network protocol analyzer and a very powerful tool.  Depending on the interface you are looking for packets on, you will most likely only see the plaintext information since wireshark will read it before it is encrypted.  In this scenario, you can refer to yourself as the first party.  The first party knows what's going on and as a result, nothing needs to be hidden from this person (like yourself, you know what you are typing in, right?).  The third party, e.g., a hacker, is the person you need to be worried about.  If you are on a network and I am sniffing network traffic at the router or gateway, the information would show up as encrypted.

Hope that helps.

---

### Post by kevdog on 2008-03-18
How can I sniff my own network traffic at the router or otherwise?

---

### Post by The Tronyx on 2008-03-18
> **kevdog said:**
> How can I sniff my own network traffic at the router or otherwise?

I'm not trying to be difficult, but just so I can help more clearly, what is it you are trying to test?

---

### Post by kevdog on 2008-03-18
I want to see the encrypted packets to prove to myself the data is indeed encrypted.

---

### Post by cdenley on 2008-03-18
If you are sending data with a SSH client on your computer, wireshark should show you the encrypted packets. Have you tried it?

> 
How can I sniff my own network traffic at the router or otherwise?

Run wireshark on the router if it's running ubuntu desktop. If it's running ubuntu server, use tcpdump.

---

### Post by Dr Small on 2008-03-18
Install wireshark, sniff your interface, and connect to a SSH server.
You can then apply a ssh filter so you only see SSH packets.

Sorry, let me clarify:

Install Wireshark:
```
sudo apt-get install wireshark
```

Then run Wireshark:
```
gksudo wireshark
```

Click the second button over on the bottom row (this is why I hate GUI instructions :p).
It should say "Show the capture options...."

Select your interface. For Display Options I have "Update List of packets in real time" and "Hide Capture Info Dialog" checked.

You can set a filter in these options too, and any other options you wish. Then click start. The packets should show up on the screen. The rest is fairly simple to figure out on how to view the packets and whatnot.


Dr Small

---

### Post by wieman01 on 2008-03-19
Install wireshark on 3rd computer and sniff your own network while SSH client & server communicate with each other. That should do.

---

### Post by p_quarles on 2008-03-19
I believe you would also need to configure the interface on the scanning machine to capture all packets. Assuming eth0, it would be:
```
sudo ifconfig eth0 promisc
```
Replace "promisc" with "-promisc" to change it back.

---

### Post by The Tronyx on 2008-03-19
The scanning machine, assuming it is being used as a third party and not the same computer that the ssh is being used to connect with, would need to be in between computer 1 and the gateway.  The easiest way to do this, would be to add an ARP entry in the "sniffing" third party computer and add the LAN IP of the SSH connection you want to test (this is actually called ARP poisoning, Ettergap does a great job of executing MITM attacks).  When you are done, either reboot the 'attacking' machine or flush the ARP cache.

To be honest, the amount of things that people are telling you to seem to be over complicating this post.  If you want to know if your SSH is secure, you could always look up the RFC info [http://www.ietf.org/rfc/rfc4251.txt](http://www.ietf.org/rfc/rfc4251.txt).  But to make a long story short, SSH won't work if it isn't 'acting' securely, such as encrypting data.  Secondly, in the event that someone did hijack your SSH connection, there wouldn't be much you could do other than to pay attention to key changes.

---

### Post by Athelstan101 on 2008-03-19
Try the following, then send some data (assuming the ssh connection is on the eth0 interface):

```
$ sudo tcpdump -i eth0 -vv -X
```

---

### Post by The Tronyx on 2008-03-19
You guys...why is this so difficult?

When you use SSH, traffic is masked upon exiting the interface.  When it arrives at the destination, it is DELIVERED in plain text.  In transit, it is encrypted and unreadable unless a proper man-in-the-middle attack is executed.  Thus, sniffing at the source and/or the destination will not provide accurate results.  The source and destination are the only 2 parties authorized to view that data, why would it be delivered in a way that it cannot be read?  The packets are decoded at the point of interception which just happens to be where your packet sniffer would be sniffing.

The only real way to determine if your SSH is being handled correctly, assuming you suspect that it isn't encrypted, it to execute third party data interception, e.g. ARP poison your own setup.

If you want accurate results, do not sniff on the sending/receiving machine, it is not an accurate reflection of data transmission.  Running TCP dump on the your own NIC and filtering SSH traffic is kind of a waste of time as far as validity of secrecy is concerned.

---

### Post by cdenley on 2008-03-20
> **2point0 said:**
> You guys...why is this so difficult?

When you use SSH, traffic is masked upon exiting the interface.  When it arrives at the destination, it is DELIVERED in plain text.  In transit, it is encrypted and unreadable unless a proper man-in-the-middle attack is executed.  Thus, sniffing at the source and/or the destination will not provide accurate results.  The source and destination are the only 2 parties authorized to view that data, why would it be delivered in a way that it cannot be read?  The packets are decoded at the point of interception which just happens to be where your packet sniffer would be sniffing.

The only real way to determine if your SSH is being handled correctly, assuming you suspect that it isn't encrypted, it to execute third party data interception, e.g. ARP poison your own setup.

If you want accurate results, do not sniff on the sending/receiving machine, it is not an accurate reflection of data transmission.  Running TCP dump on the your own NIC and filtering SSH traffic is kind of a waste of time as far as validity of secrecy is concerned.

Are you sure about that? As I understood, the ssh client encrypts the data, then sends it. The ssh server listens for connections on port 22, then decodes them as they are received. If you capture packets from the device, then all you will see is packets with encrypted data. The encryption is done by the software. Anything you see in a packet capture is what is being sent or received from the device.

If I am mistaken, I would be very interested in seeing a reference. If you were sniffing a virtual device such as a VPN tunnel, then you would see unencrypted data, but I don't think that is the case with a physical device.

I just sent a text file over SSH while capturing the network traffic. I used the strings command to grab any plaintext in the captured data. There wasn't any text from my text file. The captured data must be encrypted.

---

### Post by The Tronyx on 2008-03-20
@cdenley

No, I haven't tried but I will tonight.  I've been on vacation and I'm probably an *** for making that statement without testing it.  I'll fool around with it when I get back home tonight and let you know.

I may very well be wrong too.  Since I can't test it right now, I was looking at it like various other things that can be captured in plain text on localhost that you shouldn't be able to be read in plain text en route to its destination such as various authentications on numerous protocols and some other data transmissions.

Edit:  Ahhh foiled again!  You are very correct cdenley =D>.  I just bothered to install wireshark on this machine and use it with PuTTY.  That's what I get for coming off so over confident on vacation.

---

### Post by kevdog on 2008-03-20
Here is what I got from a captured ssh transmission attempting a login to the server (which I was denied for some reason).  I captured the output using wireshark at the client:

```
SSH-2.0-WeOnlyDo 2.0.0

SSH-2.0-OpenSSH_4.7
.......v....J....?v.
....6diffie-hellman-group1-sha1,diffie-hellman-group14-sha1....ssh-rsa,ssh-dss....blowfish-cbc....blowfish-cbc....hmac-sha1,hmac-md5,none....hmac-sha1,hmac-md5,none....zlib,none....zlib,none...........................J(.{.8!.*......#...~diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1....ssh-rsa,ssh-dss....aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr....aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr...ihmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96...ihmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96....zlib@openssh.com,zlib,none....zlib@openssh.com,zlib,none...............................5.Y.`..RL...
...M...H..Xp....I...j.....A....%/.....H.}j...!.....h...n...
..$.
..@h
...x]..g-....Y.__... 7..L...2..P.4x..?~.[.....v..U......).....&.?..V......z.j
.e1v........;..._Fp.X^...n.....l..p.3."*...{&r(.m...4....
..%.>F.>L........:|.X:3.F.\z.@..v.xvZ.........<..........ssh-rsa....#.........!.$.-J...5.\....Ol..>.....r2..=.W...p7j........*..n+d.^q-..K....\....Xd..?.-.m..
.h.|..|hG.Q{.2.'I.]tk.j.G..J|.G..G.`...J.V.......("!._.
......*vX=3.:]L7......e..
.i... ..6..j..p.v.:..i0).=._Wb..\.RX.#.*.c..F.......1L+.....?...O5..@0e...*.w...N.0...m...h.....^..'7.|..TR.....-....0BY..-4Be.....Ia....Z......@.....Z..|.t,-&..#2...........[@.g}..!.B.z7
l..._pmt.C...%...Bbn....u.
.k....J........ssh-rsa.....t.K....p...\.....S
.2.k.9*Ex...Q....?X.=..$.r.si..rG...YO....la&..A..-..t&m@._j.........,P..].....6k..R.t,t.!w..O.
.....!t;..I..............
...............
..F..
j...].......s.|W[......D.?.......Z.j.....'Yq.|...../.....HF.J...Bf.7[C....
%.=.g...Qs.D............?..V.a....<@..D|.......I../J@..r.k;J....%{'fC...Lp.$.{.a.....A".VS.eH..~...h.7.......%G&Z.....~.....E.E..*3.>/.4..)...M....pf.j..j....c.....s....g..L.....%.e<QD"V.YFJ#.6.{.\!.!..i.J..~.....|L!.b.c......M..s^T..J..G...8U....|.......2....!...Jk..Z..p_..3........:.....@(_..B..m!.z~0...w....FFx.........C'.........f.8...4.....F...m.........z,.#^....m...i..r>.P.k..!..N2.S+.......A]..e.,t..h.Q-...^..[..D41.#3........P.*..x......W..5y....u.........[L3|...\.<.n
.64..\...v\.y..a,p....p*..*n..?.`...s.)..H......L..cI#.3
..o63q.U........|..}...O`....@.KG......C.qY.DPW.J}.@I.K.e....K.
Y'.........p.......j.Dy.....\.M!.e@..z..+...r..&E.~._
..!..."Z..~........a.. E
.nF."..........n......]..N..f6`......p..v..Ew......j.x..]$...5/.....l.}?h<n..?.H.h.......:..6...?4..0{..{.....^...J..h6Ez-....=...I...0.*.QV.CX)..y.
.{cC.nx.t...21..S....XMu?.p.w1*..0G*.._.>.....5..0.7<....t8L.z.1....\d.TIy.w....Co..=...0.........K$:.hf..Y.u....?..._;..(.V$m2..2...
....I...j.N
%.~.=...$..j.z....7....6O...A.;.._p..b.rbs.P..Z.H.[.......[dtm.../.z.i..@.6Q.5.M...!|p:."..UDV.CFJ......y...b.x...3U.5....mi..[..q.O9...a......'..=.V..w.....a7n.+@E...SM...@..Ln..:..6...P
.....Y.&...?.i....2.6.8...A.DxI.Wr....R...b5....T...H0M{P._...v?..z..SQZvV.......'d..Kx.:.F..WR{..HQ.:|h..X...!.?.!.....7<M.K...m.\
..{~.......KE..;Z....[....n..n.....q..^.....?..l(.j<.[.....Q....{^.....9$4.?_k......4
.8.MAB....4...
.<..r.4....9.....E@9..s&......x....q.w......D..o.o"...j..h#..Y...y}....5{...0R.r\.W.
.._....q)....K.&v.......{Wl)..Y1.AjMcG
1.s...;Ul,...w.^9..lYW..M.0MR.f...^.....&..$.\.cZ..o.5......H...oH..q.lE.d.iR.../(8.]pU...sb-!.jM..i...._E.....
0..7.&..r.m....C...y.;.zp:v%...rz..P.Gt../....|#.!.g<Y.D.....S.`....C../...v..9...L......,U....z-y..'......bO..F....<.f:(..QA/.<........s..L............=....YB_M...4+...g.....x..K...'.|...t.>Y&w>U..l'.......
]......h..%.lDz...q..`.P...@Q...4.d
....[.^..5....&....T.........&..7,I^lEP;![.V`..x..k...(...EF.......~..W.Q...O.V-......C....<....'.S/?.;Z..K....;s.....,|.o4..XD................>.x>.U.x....w.^h&.l.n.`.k..v
.=.-X.....l...b.P..@
._I...M.RD.`.....U..C...i,Zq....ib+AQTdi.y..7...Mp.z........O......0..O;.Ly.....q.
......P..F]...........W..4.c..YJ.......}..
.........M...........{.....[....dj....H*CSg...d.
z....z.
|.....s...?....y.......i2.v&.p@...
z*..N...f....M..?...e......'.......kN..u.*....I...._I.;..B.2...^.?..[Y@9......F.
Q...{..C.f. n.....F:
..L9;...lu.j..Y...._.{.......}N.C...*/.`.....$...R....b.u>..\8.....3...p...D.d.I....aW.Y......%d..uP.E..,N/;.]....W
...c.Oz...E*....}
.iT......]..Qv.c...{S.........O.Q.p?...v0E.X../.....R....L.....Dw..eq..S..~..W..$...`.J...4#7.!...uH+./..%..:^H.S...j...U@.AF..Z`.8.

```

Im going to assume this is ciphertext?  Can anyone else confirm this?

---

### Post by p_quarles on 2008-03-20
> **kevdog said:**
> Im going to assume this is ciphertext?  Can anyone else confirm this?
Well, I certainly can't read it. :D

While I'm not a cryptography expert, I can say that this is very similar to the output I get when attempting to view unmounted encrypted loop devices on my own machine. That kind of output is what I would expect to see, that is. 

Perhaps someone else can offer more expert confirmation.

---

### Post by kevdog on 2008-03-20
I only know that gpg encrypted cipher text looks much different.

---

### Post by The Tronyx on 2008-03-20
> **kevdog said:**
> 
Im going to assume this is ciphertext?  Can anyone else confirm this?

That is indeed ciphertext.

---

### Post by Dr Small on 2008-03-20
I can confirm that it is ciphertext also.
If you read the SSH manual, you will see a list of ciphers under -c

Dr Small

---

### Post by The Cog on 2008-03-22
Wireshark captures packets pretty-much as they are passed to/from the network adapter, I guess as they pass to-from the driver. This means that SSH packets that are software encrypted before handing to the network card show up in wireshark as encrypted and unreadable. One exception appears to be WEP/WPA wireless encryption which wirehark captures in plain text - I assume that the encryption is performed as a MAC layer process inside the driver itself (or even on the card).

---

### Post by wieman01 on 2008-03-22
> **The Cog said:**
> Wireshark captures packets pretty-much as they are passed to/from the network adapter, I guess as they pass to-from the driver. This means that SSH packets that are software encrypted before handing to the network card show up in wireshark as encrypted and unreadable. One exception appears to be WEP/WPA wireless encryption which wirehark captures in plain text - I assume that the encryption is performed as a MAC layer process inside the driver itself (or even on the card).
Encryption is performed by a supplicant program... wpa-supplicant. It sits on top of the driver/interface and is in charge of encrypting/decrypting data. The driver, however, must be able to understand WPA and implement a certain interface that wpa-supplicant can communicate with.

---

### Post by kevdog on 2008-03-22
Anyway from the ciphertext I posted can you identify the cipher algorithm that produced the result?

---

