---
title: "Postgres 8.3 on Ubuntu 9.04 with Remote connections"
date: 2009-11-26
forum: Server Platforms
---

### Post by pazzorilancio on 2009-11-26
Hey guys.

So on an Ubuntu 9.04 server I did an apt-get install postgres which installed postgres 8.3.

In the conf files I've allowed the host 0.0.0.0/0 for postgres user with ident sameuser. I've also edited the main postgres.conf file to listen on *.

When I try connecting remotely to the server using PGAdmin I get a server unexpectedly closed error after about 30 seconds. Below is a packet trace (SuggyServer is the server and the IP is the PGAdmin host):

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
12:43:29.093918 IP 82.109.203.178.nessus > SuggysServer.5000: S 1641206390:1641206390(0) win 8192 <mss 1460,nop,wscale 2,nop,nop,sackOK>
12:43:29.093918 IP SuggysServer.5000 > 82.109.203.178.nessus: S 1829310476:1829310476(0) ack 1641206391 win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 6>
12:43:29.243914 IP 82.109.203.178.nessus > SuggysServer.5000: . ack 1 win 16425
12:43:29.243914 IP 82.109.203.178.nessus > SuggysServer.5000: P 1:9(8) ack 1 win 16425
12:43:29.243914 IP SuggysServer.5000 > 82.109.203.178.nessus: . ack 9 win 92
12:43:29.243914 IP SuggysServer.5000 > 82.109.203.178.nessus: P 1:2(1) ack 9 win 92
12:43:29.413917 IP 82.109.203.178.nessus > SuggysServer.5000: P 9:97(88) ack 2 win 16424
12:43:29.413917 IP SuggysServer.5000 > 82.109.203.178.nessus: P 2:932(930) ack 97 win 92
12:43:29.643915 IP 82.109.203.178.nessus > SuggysServer.5000: P 97:295(198) ack 932 win 16192
12:43:29.643915 IP SuggysServer.5000 > 82.109.203.178.nessus: P 932:991(59) ack 295 win 108
12:43:29.773918 IP 82.109.203.178.nessus > SuggysServer.5000: P 295:401(106) ack 991 win 16177
12:43:29.813918 IP SuggysServer.5000 > 82.109.203.178.nessus: . ack 401 win 108

(It shows nessus for local port though thats a coincidence. I set the server to use port 5000 but I get the same issue on the default 5432 port)

The above shows its not a firewall issue as the 2 machines can talk to each other on port 5000.

Does anyone have any ideas? It's driving me insane :)

Cheers

---

### Post by pazzorilancio on 2009-11-26
root@SuggysServer:/var/log/postgresql# tcpdump port 5000 -s0 -X
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
13:04:40.593917 IP 82.109.203.178.19755 > SuggysServer.5000: S 245857580:245857580(0) win 8192 <mss 1460,nop,wscale 2,nop,nop,sackOK>
        0x0000:  4500 0034 0fee 4000 7306 9854 526d cbb2  E..4..@.s..TRm..
        0x0010:  ae8f 92d2 4d2b 1388 0ea7 7d2c 0000 0000  ....M+....},....
        0x0020:  8002 2000 030e 0000 0204 05b4 0103 0302  ................
        0x0030:  0101 0402                                ....
13:04:40.593917 IP SuggysServer.5000 > 82.109.203.178.19755: S 295842069:295842069(0) ack 245857581 win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 6>
        0x0000:  4500 0034 0000 4000 4006 db42 ae8f 92d2  E..4..@.@..B....
        0x0010:  526d cbb2 1388 4d2b 11a2 3115 0ea7 7d2d  Rm....M+..1...}-
        0x0020:  8012 16d0 c971 0000 0204 05b4 0101 0402  .....q..........
        0x0030:  0103 0306                                ....
13:04:40.713915 IP 82.109.203.178.19755 > SuggysServer.5000: . ack 1 win 16425
        0x0000:  4500 0028 0fef 4000 7306 985f 526d cbb2  E..(..@.s.._Rm..
        0x0010:  ae8f 92d2 4d2b 1388 0ea7 7d2d 11a2 3116  ....M+....}-..1.
        0x0020:  5010 4029 e0e9 0000                      P.@)....
13:04:40.723915 IP 82.109.203.178.19755 > SuggysServer.5000: P 1:9(8) ack 1 win 16425
        0x0000:  4500 0030 0ff0 4000 7306 9856 526d cbb2  E..0..@.s..VRm..
        0x0010:  ae8f 92d2 4d2b 1388 0ea7 7d2d 11a2 3116  ....M+....}-..1.
        0x0020:  5018 4029 c5d0 0000 0000 0008 04d2 162f  P.@).........../
13:04:40.723915 IP SuggysServer.5000 > 82.109.203.178.19755: . ack 9 win 92
        0x0000:  4500 0028 2783 4000 4006 b3cb ae8f 92d2  E..('.@.@.......
        0x0010:  526d cbb2 1388 4d2b 11a2 3116 0ea7 7d35  Rm....M+..1...}5
        0x0020:  5010 005c 20af 0000                      P..\....
13:04:40.723915 IP SuggysServer.5000 > 82.109.203.178.19755: P 1:2(1) ack 9 win 92
        0x0000:  4500 0029 2784 4000 4006 b3c9 ae8f 92d2  E..)'.@.@.......
        0x0010:  526d cbb2 1388 4d2b 11a2 3116 0ea7 7d35  Rm....M+..1...}5
        0x0020:  5018 005c 5f9d 0000 53                   P..\_...S
13:04:40.843918 IP 82.109.203.178.19755 > SuggysServer.5000: P 9:97(88) ack 2 win 16424
        0x0000:  4500 0080 0ff3 4000 7306 9803 526d cbb2  E.....@.s...Rm..
        0x0010:  ae8f 92d2 4d2b 1388 0ea7 7d35 11a2 3117  ....M+....}5..1.
        0x0020:  5018 4028 4550 0000 1603 0100 5301 0000  P.@(EP......S...
        0x0030:  4f03 014b 0e7c e98c c673 9da2 ad15 2c70  O..K.|...s....,p
        0x0040:  d9ec 94eb 1c4e 884d 0537 6096 0b4c a0f7  .....N.M.7`..L..
        0x0050:  4fa9 3300 0028 0039 0038 0035 0016 0013  O.3..(.9.8.5....
        0x0060:  000a 0033 0032 002f 0007 0005 0004 0015  ...3.2./........
        0x0070:  0012 0009 0014 0011 0008 0006 0003 0100  ................
13:04:40.843918 IP SuggysServer.5000 > 82.109.203.178.19755: P 2:932(930) ack 97 win 92
        0x0000:  4500 03ca 2785 4000 4006 b027 ae8f 92d2  E...'.@.@..'....
        0x0010:  526d cbb2 1388 4d2b 11a2 3117 0ea7 7d8d  Rm....M+..1...}.
        0x0020:  5018 005c 633e 0000 1603 0100 4a02 0000  P..\c>......J...
        0x0030:  4603 014b 0e7c e896 84a5 7031 9d62 9d38  F..K.|....p1.b.8
        0x0040:  357f 4677 cfa5 e02d 3c16 bfc7 eca7 ca99  5.Fw...-<.......
        0x0050:  96ab 4720 00dc 5f1f 5831 1e17 3af8 cb3f  ..G..._.X1..:..?
        0x0060:  b958 ed1d 4e45 914f 15bb 97a1 8546 e005  .X..NE.O.....F..
        0x0070:  bdcf 90c4 0039 0016 0301 01b3 0b00 01af  .....9..........
        0x0080:  0001 ac00 01a9 3082 01a5 3082 010e 0209  ......0...0.....
        0x0090:  00dc 6101 123d 7304 cc30 0d06 092a 8648  ..a..=s..0...*.H
        0x00a0:  86f7 0d01 0105 0500 3017 3115 3013 0603  ........0.1.0...
        0x00b0:  5504 0313 0c53 7567 6779 7353 6572 7665  U....SuggysServe
        0x00c0:  7230 1e17 0d30 3931 3132 3630 3934 3632  r0...09112609462
        0x00d0:  375a 170d 3139 3131 3234 3039 3436 3237  7Z..191124094627
        0x00e0:  5a30 1731 1530 1306 0355 0403 130c 5375  Z0.1.0...U....Su
        0x00f0:  6767 7973 5365 7276 6572 3081 9f30 0d06  ggysServer0..0..
        0x0100:  092a 8648 86f7 0d01 0101 0500 0381 8d00  .*.H............
        0x0110:  3081 8902 8181 00cc 3ff4 0cb4 d5c4 71f5  0.......?.....q.
        0x0120:  b21b b7eb 7b64 fa64 fc4e 7ce6 88a1 9fdf  ....{d.d.N|.....
        0x0130:  47a1 8abe 595b c60e 1243 8e73 55d7 6ca4  G...Y[...C.sU.l.
        0x0140:  42ab 9d5a c319 2a4c 5d86 2a5d 8129 7304  B..Z..*L].*].)s.
        0x0150:  528e 771d 571e 67a1 9a8e 8e23 cb55 32b6  R.w.W.g....#.U2.
        0x0160:  f400 53c4 3af8 54a9 2984 edc8 3b99 cb63  ..S.:.T.)...;..c
        0x0170:  164b 81fc 0f73 055d ddb4 2f9f 9a20 60e2  .K...s.]../...`.
        0x0180:  4a11 ad34 a1f9 507b 3032 253f 8df8 f510  J..4..P{02%?....
        0x0190:  8d4e f3b3 6269 1302 0301 0001 300d 0609  .N..bi......0...
        0x01a0:  2a86 4886 f70d 0101 0505 0003 8181 0037  *.H............7
        0x01b0:  9fae d2dd cdb5 7452 e007 68dd 6bd4 776f  ......tR..h.k.wo
        0x01c0:  799b ee27 1861 be68 4d8f a0f9 29cd 6ec4  y..'.a.hM...).n.
        0x01d0:  5a2f e80c 8f4f 2fe6 51c1 023b c3a0 2ea1  Z/...O/.Q..;....
        0x01e0:  3cb8 5d8e 1b35 a4f5 dce5 5236 74b3 b1d2  <.]..5....R6t...
        0x01f0:  ce3b 82dc d65a ba47 e09e a6a9 65bc 54c0  .;...Z.G....e.T.
        0x0200:  f793 f07e 8de0 1e45 1199 ca30 1b08 d0fe  ...~...E...0....
        0x0210:  86b4 9b5a 9c10 3539 6100 b101 62b6 b49e  ...Z..59a...b...
        0x0220:  64d6 aaa9 29e4 a332 b73a b1ca 3e13 e016  d...)..2.:..>...
        0x0230:  0301 018d 0c00 0189 0080 f488 fd58 4e49  .............XNI
        0x0240:  dbcd 20b4 9de4 9107 366b 336c 380d 451d  ........6k3l8.E.
        0x0250:  0f7c 88b3 1c7c 5b2d 8ef6 f3c9 23c0 43f0  .|...|[-....#.C.
        0x0260:  a55b 188d 8ebb 558c b85d 38d3 34fd 7c17  .[....U..]8.4.|.
        0x0270:  5743 a31d 186c de33 212c b52a ff3c e1b1  WC...l.3!,.*.<..
        0x0280:  2940 1811 8d7c 84a7 0a72 d686 c403 19c8  )@...|...r......
        0x0290:  0729 7aca 950c d996 9fab d00a 509b 0246  .)z.........P..F
        0x02a0:  d308 3d66 a45d 419f 9c7c bd89 4b22 1926  ..=f.]A..|..K".&
        0x02b0:  baab a25e c355 e92f 78c7 0001 0200 8080  ...^.U./x.......
        0x02c0:  5dc5 486f 50e2 1c4f a956 2740 cf38 e550  ].HoP..O.V'@.8.P
        0x02d0:  989c 1cc5 f319 23b4 4972 847d 9e21 9f82  ......#.Ir.}.!..
        0x02e0:  2d34 1d46 20c9 da38 f1f0 9134 bf97 cffe  -4.F...8...4....
        0x02f0:  67fd 092d da4a c31e 9dde 06c5 15e8 a385  g..-.J..........
        0x0300:  b50d c669 84da fc51 c848 46c7 a48a 17bc  ...i...Q.HF.....
        0x0310:  abcb 9115 0ebc 5460 7371 4635 26bb 53e9  ......T`sqF5&.S.
        0x0320:  d608 4ada 3b33 1f07 54cb 9831 bead 0a69  ..J.;3..T..1...i
        0x0330:  bd0d 24b2 f148 f136 d4cd 972c 350b 0e00  ..$..H.6...,5...
        0x0340:  80ad c55b 646e b6b8 c87c 28c3 02cb ee7e  ...[dn...|(....~
        0x0350:  6ea9 7c0f 966f bd27 ed4d a27f 5bfc 826a  n.|..o.'.M..[..j
        0x0360:  8382 563d df9f 4696 da2b ffc3 9d3c a174  ..V=..F..+...<.t
        0x0370:  8a96 bd2e c2de 2ecc 4718 5666 5495 d764  ........G.VfT..d
        0x0380:  7fe8 1067 d3a6 94d4 d61c 5806 ed7c c1d0  ...g......X..|..
        0x0390:  71c5 b18a bb8f 73af f0e1 4ee0 29b7 107b  q.....s...N.)..{
        0x03a0:  738b c108 19a8 262b f9ce 6ac1 0cc6 2e26  s.....&+..j....&
        0x03b0:  01e0 26c1 8303 eeee c0d7 cb2d cecd 1d39  ..&........-...9
        0x03c0:  f816 0301 0004 0e00 0000                 ..........
13:04:41.033915 IP 82.109.203.178.19755 > SuggysServer.5000: P 97:295(198) ack 932 win 16192
        0x0000:  4500 00ee 0ff6 4000 7306 9792 526d cbb2  E.....@.s...Rm..
        0x0010:  ae8f 92d2 4d2b 1388 0ea7 7d8d 11a2 34b9  ....M+....}...4.
        0x0020:  5018 3f40 12dc 0000 1603 0100 8610 0000  P.?@............
        0x0030:  8200 80cf 6a2b dd9e 77e1 cfee af3d 84e6  ....j+..w....=..
        0x0040:  3043 9c5c 8b49 f87d af95 e729 2261 dc19  0C.\.I.}...)"a..
        0x0050:  098f 8919 758a 989b 26df 9645 f645 6e06  ....u...&..E.En.
        0x0060:  166e 0e32 2ff3 277f d908 5552 4114 aaad  .n.2/.'...URA...
        0x0070:  fc78 46a7 4211 a88a 8fec 8164 19fd 2dde  .xF.B......d..-.
        0x0080:  8e57 3c72 07d4 5c1c a629 ec14 3b3d 1d01  .W<r..\..)..;=..
        0x0090:  6061 c1a5 7490 4ee4 68e8 1bdc 2f63 3870  `a..t.N.h.../c8p
        0x00a0:  486f 7bdb b387 7828 fcbf e2a2 ec4b d3c9  Ho{...x(.....K..
        0x00b0:  9e8d aa14 0301 0001 0116 0301 0030 7fa9  .............0..
        0x00c0:  b667 33ed dbd9 ff34 e463 0b49 079c e766  .g3....4.c.I...f
        0x00d0:  3093 7c4a 3fd4 4d75 2df4 067a 6778 f293  0.|J?.Mu-..zgx..
        0x00e0:  d911 2a2f a15b 6de5 6f8c 0f0a 5968       ..*/.[m.o...Yh
13:04:41.033915 IP SuggysServer.5000 > 82.109.203.178.19755: P 932:991(59) ack 295 win 108
        0x0000:  4500 0063 2786 4000 4006 b38d ae8f 92d2  E..c'.@.@.......
        0x0010:  526d cbb2 1388 4d2b 11a2 34b9 0ea7 7e53  Rm....M+..4...~S
        0x0020:  5018 006c 5fd7 0000 1403 0100 0101 1603  P..l_...........
        0x0030:  0100 306f 0a04 bd26 45ea ad24 ef78 c004  ..0o...&E..$.x..
        0x0040:  9bb5 d50d 6f35 71e4 10b2 219d 01db 10c1  ....o5q...!.....
        0x0050:  ea98 db6c 8eca fd11 8089 f613 6a29 de0b  ...l........j)..
        0x0060:  9a29 e2                                  .).
13:04:41.163916 IP 82.109.203.178.19755 > SuggysServer.5000: P 295:401(106) ack 991 win 16177
        0x0000:  4500 0092 0ff8 4000 7306 97ec 526d cbb2  E.....@.s...Rm..
        0x0010:  ae8f 92d2 4d2b 1388 0ea7 7e53 11a2 34f4  ....M+....~S..4.
        0x0020:  5018 3f31 1bc3 0000 1703 0100 20c2 2449  P.?1..........$I
        0x0030:  a4aa 7479 5665 a914 d035 2011 1091 7152  ..tyVe...5....qR
        0x0040:  2a88 154a 8310 3e7c 1d36 b9f7 2217 0301  *..J..>|.6.."...
        0x0050:  0040 8413 b525 3a80 e3a8 b25c 359d 597b  .@...%:....\5.Y{
        0x0060:  ded4 d055 f179 a6c2 bc29 f928 ccbe 2b4c  ...U.y...).(..+L
        0x0070:  07bb 37c0 c807 bce1 ed7b e70c 557a 5009  ..7......{..UzP.
        0x0080:  89e9 9b0c 8b56 5df4 1685 eb70 3194 1e6a  .....V]....p1..j
        0x0090:  aea9                                     ..
13:04:41.203916 IP SuggysServer.5000 > 82.109.203.178.19755: . ack 401 win 108
        0x0000:  4500 0028 2787 4000 4006 b3c7 ae8f 92d2  E..('.@.@.......
        0x0010:  526d cbb2 1388 4d2b 11a2 34f4 0ea7 7ebd  Rm....M+..4...~.
        0x0020:  5010 006c 1b39 0000                      P..l.9..

---

### Post by masux594 on 2009-11-26
what about pg_hba.conf? 
Postgres read from pg_hba.conf the configurations of what accept, and what refuse..

Sysc, A

---

