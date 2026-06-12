---
title: "OpenLDAP SSL certificate not working"
date: 2009-03-07
forum: Server Platforms
---

### Post by beniwtv on 2009-03-07
Hi all,

I'm trying to set-up OpenLDAP with a self-signed certificate, but it seems it won't play nice :(

I have generated the certificate as follows:

```

openssl genrsa -out /etc/ssl/private/secure-server.key 1024
openssl req -new -key /etc/ssl/private/secure-server.key -out /etc/ssl/certs/csr/secure-server.csr
openssl x509 -req -days 365 -in /etc/ssl/certs/csr/secure-server.csr -signkey /etc/ssl/private/secure-server.key -out /etc/ssl/certs/secure-server.crt

```

Apache seems to be working fine with this certficate.
And slapd.conf reads as follows:

```

TLSCertificateFile /etc/ssl/certs/secure-server.crt
TLSCertificateKeyFile /etc/ssl/private/secure-server.key
TLSVerifyClient try

```

OpenLDAP starts OK and listens on port 636 as expected, but I get the following error if I try to ldapsearch -x:

```
ldap_create
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP opserv.private.wwbs-online.net:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 127.0.1.1:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
tls_write: want=82, written=82
  0000:  16 03 02 00 4d 01 00 00  49 03 02 49 b2 67 2e b5   ....M...I..I.g..  
  0010:  c4 33 f4 99 9e 5f 74 2c  19 b4 a1 65 64 80 a6 6c   .3..._t,...ed..l  
  0020:  fe 17 03 60 e6 dd 2a d6  3b a3 a3 00 00 18 00 39   ...`..*.;......9  
  0030:  00 33 00 16 00 38 00 32  00 13 00 66 00 35 00 2f   .3...8.2...f.5./  
  0040:  00 0a 00 05 00 04 02 01  00 00 07 00 09 00 03 02   ................  
  0050:  00 01                                              ..                
tls_read: want=5, got=5
  0000:  16 03 02 00 4a                                     ....J             
tls_read: want=74, got=74
  0000:  02 00 00 46 03 02 49 b2  67 2e 0e 67 da b8 a8 f3   ...F..I.g..g....  
  0010:  c4 7b f5 f7 17 56 43 88  c4 9e f0 c2 90 cf 90 17   .{...VC.........  
  0020:  66 74 d6 2a 9d b9 20 97  18 e5 28 80 d7 1a 30 7d   ft.*.. ...(...0}  
  0030:  71 c8 69 77 fa a4 a0 ec  51 4e ef e6 1d 0e 82 a9   q.iw....QN......  
  0040:  97 b7 f5 db 0c f4 ed 00  35 01                     ........5.        
tls_read: want=5, got=5
  0000:  16 03 02 03 35                                     ....5             
tls_read: want=821, got=821
  0000:  0b 00 03 31 00 03 2e 00  03 2b 30 82 03 27 30 82   ...1.....+0..'0.  
  0010:  02 90 02 09 00 a0 68 21  ad 1f 8c 5c 93 30 0d 06   ......h!...\.0..  
  0020:  09 2a 86 48 86 f7 0d 01  01 05 05 00 30 81 d7 31   .*.H........0..1  
  0030:  0b 30 09 06 03 55 04 06  13 02 45 53 31 10 30 0e   .0...U....ES1.0.  
  0040:  06 03 55 04 08 14 07 4d  c3 a1 6c 61 67 61 31 1d   ..U....M..laga1.  
  0050:  30 1b 06 03 55 04 07 14  14 53 61 6e 20 50 65 64   0...U....San Ped  
  0060:  72 6f 20 41 6c 63 c3 a1  6e 74 61 72 61 31 2c 30   ro Alc..ntara1,0  
  0070:  2a 06 03 55 04 0a 13 23  57 57 42 53 20 2d 20 57   *..U...#WWBS - W  
  0080:  6f 72 6c 64 77 69 64 65  20 42 75 73 69 6e 65 73   orldwide Busines  
  0090:  73 20 53 6f 6c 75 74 69  6f 6e 73 31 16 30 14 06   s Solutions1.0..  
  00a0:  03 55 04 0b 13 0d 53 65  63 75 72 65 20 73 65 72   .U....Secure ser  
  00b0:  76 65 72 31 27 30 25 06  03 55 04 03 13 1e 6f 70   ver1'0%..U....op  
  00c0:  73 65 72 76 2e 70 72 69  76 61 74 65 2e 77 77 62   serv.private.wwb  
  00d0:  73 2d 6f 6e 6c 69 6e 65  2e 6e 65 74 31 28 30 26   s-online.net1(0&  
  00e0:  06 09 2a 86 48 86 f7 0d  01 09 01 16 19 77 65 62   ..*.H........web  
  00f0:  6d 61 73 74 65 72 40 77  77 62 73 2d 6f 6e 6c 69   master@wwbs-onli  
  0100:  6e 65 2e 6e 65 74 30 1e  17 0d 30 39 30 33 30 37   ne.net0...090307  
  0110:  31 31 35 38 35 30 5a 17  0d 31 30 30 33 30 37 31   115850Z..1003071  
  0120:  31 35 38 35 30 5a 30 81  d7 31 0b 30 09 06 03 55   15850Z0..1.0...U  
  0130:  04 06 13 02 45 53 31 10  30 0e 06 03 55 04 08 14   ....ES1.0...U...  
  0140:  07 4d c3 a1 6c 61 67 61  31 1d 30 1b 06 03 55 04   .M..laga1.0...U.  
  0150:  07 14 14 53 61 6e 20 50  65 64 72 6f 20 41 6c 63   ...San Pedro Alc  
  0160:  c3 a1 6e 74 61 72 61 31  2c 30 2a 06 03 55 04 0a   ..ntara1,0*..U..  
  0170:  13 23 57 57 42 53 20 2d  20 57 6f 72 6c 64 77 69   .#WWBS - Worldwi  
  0180:  64 65 20 42 75 73 69 6e  65 73 73 20 53 6f 6c 75   de Business Solu  
  0190:  74 69 6f 6e 73 31 16 30  14 06 03 55 04 0b 13 0d   tions1.0...U....  
  01a0:  53 65 63 75 72 65 20 73  65 72 76 65 72 31 27 30   Secure server1'0  
  01b0:  25 06 03 55 04 03 13 1e  6f 70 73 65 72 76 2e 70   %..U....opserv.p  
  01c0:  72 69 76 61 74 65 2e 77  77 62 73 2d 6f 6e 6c 69   rivate.wwbs-onli  
  01d0:  6e 65 2e 6e 65 74 31 28  30 26 06 09 2a 86 48 86   ne.net1(0&..*.H.  
  01e0:  f7 0d 01 09 01 16 19 77  65 62 6d 61 73 74 65 72   .......webmaster  
  01f0:  40 77 77 62 73 2d 6f 6e  6c 69 6e 65 2e 6e 65 74   @wwbs-online.net  
  0200:  30 81 9f 30 0d 06 09 2a  86 48 86 f7 0d 01 01 01   0..0...*.H......  
  0210:  05 00 03 81 8d 00 30 81  89 02 81 81 00 db 95 26   ......0........&  
  0220:  fa 1c 0d 28 24 41 fa ed  a3 70 1b b3 03 4c 02 97   ...($A...p...L..  
  0230:  4c 6f cc f6 47 fc ad de  e3 61 7b 33 5c f5 c2 59   Lo..G....a{3\..Y  
  0240:  83 85 e9 d0 0b 02 7a 33  94 ca f5 15 1a 2f b4 a4   ......z3...../..  
  0250:  72 f1 98 b3 e7 a5 f3 8e  a3 69 e4 bf 8a e3 23 53   r........i....#S  
  0260:  f9 4d 83 9d 5b 4d 8c 82  c0 b1 e5 80 83 b4 bf ea   .M..[M..........  
  0270:  39 2b 5a 72 30 3d 64 8d  d1 8a bf c6 6b fd ee 40   9+Zr0=d.....k..@  
  0280:  7c ca 62 33 90 54 d0 19  95 19 c4 de 20 bf b0 30   |.b3.T...... ..0  
  0290:  19 a9 35 85 7d f7 4d f5  cd 22 39 3c 1f 02 03 01   ..5.}.M.."9<....  
  02a0:  00 01 30 0d 06 09 2a 86  48 86 f7 0d 01 01 05 05   ..0...*.H.......  
  02b0:  00 03 81 81 00 19 54 a8  15 0d 3c ff 15 b5 f0 f6   ......T...<.....  
  02c0:  eb 29 97 b6 93 59 af 2c  71 76 28 59 f6 30 9b e3   .)...Y.,qv(Y.0..  
  02d0:  8c be cc d3 49 06 f5 16  2c f9 97 d9 a0 68 f1 b6   ....I...,....h..  
  02e0:  68 0b f4 6f 30 bb 4a 14  aa c2 ea 91 f2 85 41 2f   h..o0.J.......A/  
  02f0:  8a ac 2c 33 e1 f0 63 1a  bb 5f 12 50 e3 fd 2c 7f   ..,3..c.._.P..,.  
  0300:  3f 76 d2 0c e5 8a ca 1c  2c 39 10 82 85 9c 1a 36   ?v......,9.....6  
  0310:  69 cb 5d be 7f ca 80 6e  97 cf 69 95 ce cf b1 0f   i.]....n..i.....  
  0320:  db ea 84 84 d6 f1 e6 de  83 85 40 52 b4 b1 fc 64   ..........@R...d  
  0330:  4d 45 d5 5b 71                                     ME.[q             
tls_read: want=5, got=5
  0000:  16 03 02 00 09                                     .....             
tls_read: want=9, got=9
  0000:  0d 00 00 05 02 01 02 00  00                        .........         
tls_read: want=5, got=5
  0000:  16 03 02 00 04                                     .....             
tls_read: want=4, got=4
  0000:  0e 00 00 00                                        ....              
tls_write: want=12, written=12
  0000:  16 03 02 00 07 0b 00 00  03 00 00 00               ............      
tls_write: want=139, written=139
  0000:  16 03 02 00 86 10 00 00  82 00 80 cc 31 be 57 9e   ............1.W.  
  0010:  66 ba 3f 86 c9 e2 4e e0  7d f2 0c 01 06 04 2a bf   f.?...N.}.....*.  
  0020:  9d e9 64 8e e1 f9 c7 c1  b4 7e 07 e5 02 5c c4 a1   ..d......~...\..  
  0030:  cd 4d 66 ea 88 a9 b9 d0  a6 6b 74 8a ed 1c 10 9b   .Mf......kt.....  
  0040:  72 f3 63 54 71 1d e8 95  88 3d 49 0c cb 16 3d 64   r.cTq....=I...=d  
  0050:  d6 f7 f6 3e e8 23 d4 56  15 72 e9 a2 07 3b a6 e4   ...>.#.V.r...;..  
  0060:  a1 c2 ec 3c b4 15 00 08  39 db 5d ad 11 6b ca 4b   ...<....9.]..k.K  
  0070:  d3 e8 cc 47 6c 80 7d a2  3f c0 f8 35 28 65 9e b8   ...Gl.}.?..5(e..  
  0080:  cf 55 56 1c 5d db d6 97  52 76 e0                  .UV.]...Rv.       
tls_write: want=6, written=6
  0000:  14 03 02 00 01 01                                  ......            
tls_write: want=85, written=85
  0000:  16 03 02 00 50 8c 94 52  63 27 94 4e ee fd eb 15   ....P..Rc'.N....  
  0010:  d3 88 21 3e 68 ff 3f cb  3f e9 df 4e 05 d4 6e 95   ..!>h.?.?..N..n.  
  0020:  f5 44 3d a4 1a 53 75 43  12 4a 4f 9a 40 c6 32 25   .D=..SuC.JO.@.2%  
  0030:  8f 86 b1 d9 10 4d 17 8f  a3 3f 56 6e c3 fe 45 be   .....M...?Vn..E.  
  0040:  4e 0f b0 bf aa 36 ee c6  04 cb 45 aa 9c af 0f ac   N....6....E.....  
  0050:  13 47 ec 8c 72                                     .G..r             
tls_read: want=5, got=5
  0000:  14 03 02 00 01                                     .....             
tls_read: want=1, got=1
  0000:  01                                                 .                 
tls_read: want=5, got=5
  0000:  16 03 02 00 70                                     ....p             
tls_read: want=112, got=112
  0000:  30 cb f9 a6 5e 79 48 87  d5 bd 81 04 9e 28 72 56   0...^yH......(rV  
  0010:  b8 c4 dd 6b 06 32 6a 56  00 ef 90 f7 f6 40 bf 15   ...k.2jV.....@..  
  0020:  69 56 bc d0 7b d2 21 65  f2 47 1c 29 2a c0 f0 69   iV..{.!e.G.)*..i  
  0030:  f2 9a e6 cd e1 86 4e 1d  00 4e 17 a8 dc 21 f2 a1   ......N..N...!..  
  0040:  62 04 d6 58 28 61 78 7f  dc f7 d3 de 13 d9 1c 36   b..X(ax........6  
  0050:  68 c0 52 fb 7f a9 95 1c  ec 5d d8 11 a7 fa eb 44   h.R......].....D  
  0060:  ea 33 9a 63 78 75 67 e0  dd 3c fa 4b 72 25 da 26   .3.cxug..<.Kr%.&  
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 14 bytes to sd 3
  0000:  30 0c 02 01 01 60 07 02  01 03 04 00 80 00         0....`........    
tls_write: want=213, written=213
  0000:  17 03 02 00 d0 13 bc 15  12 cd 20 55 97 7a 1a 42   .......... U.z.B  
  0010:  b2 b6 74 85 a1 22 eb 89  a0 ed 7c b9 d7 d4 16 44   ..t.."....|....D  
  0020:  78 59 96 09 2a 81 56 10  d3 8a e6 ac d1 92 00 fc   xY..*.V.........  
  0030:  cd 00 93 a1 aa 03 27 31  59 8c 15 dd 28 69 d8 14   ......'1Y...(i..  
  0040:  e7 37 37 ee 8a 6a 37 44  60 ba 05 a7 4c 48 ae dd   .77..j7D`...LH..  
  0050:  c4 83 3b 2d 48 9c 40 48  09 16 3f 67 c2 ee 71 56   ..;-H.@H..?g..qV  
  0060:  e2 88 57 f5 11 42 fa 56  8b 83 07 66 62 6e aa 1a   ..W..B.V...fbn..  
  0070:  e6 3f 32 43 87 7d 3e 73  95 fb a8 67 c4 6e e9 9c   .?2C.}>s...g.n..  
  0080:  2d f6 58 30 b0 2b d7 c1  68 1f 78 24 58 9a 9a 60   -.X0.+..h.x$X..`  
  0090:  a4 bb 4c a3 e5 b1 65 c5  89 ce 40 4e 53 a4 91 bb   ..L...e...@NS...  
  00a0:  c3 93 01 be d8 a9 e1 fa  d4 f4 88 0b 5b 2e c0 5d   ............[..]  
  00b0:  15 b2 c9 d0 3c 99 b5 0f  04 8b f9 fc ff 24 cf 46   ....<........$.F  
  00c0:  f7 8f a4 d0 7c d5 af 6f  93 89 24 bb 24 52 b5 b6   ....|..o..$.$R..  
  00d0:  e2 71 0a 17 75                                     .q..u             
ldap_write: want=14, written=14
  0000:  30 0c 02 01 01 60 07 02  01 03 04 00 80 00         0....`........    
ldap_result ld 0x6120a0 msgid 1
wait4msg ld 0x6120a0 msgid 1 (infinite timeout)
wait4msg continue ld 0x6120a0 msgid 1 all 1
** ld 0x6120a0 Connections:
* host: opserv.private.wwbs-online.net  port: 636  (default)
  refcnt: 2  status: Connected
  last used: Sat Mar  7 13:23:10 2009


** ld 0x6120a0 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x6120a0 request count 1 (abandoned 0)
** ld 0x6120a0 Response Queue:
   Empty
  ld 0x6120a0 response count 0
ldap_chkResponseList ld 0x6120a0 msgid 1 all 1
ldap_chkResponseList returns ld 0x6120a0 NULL
ldap_int_select
read1msg: ld 0x6120a0 msgid 1 all 1
ber_get_next
tls_read: want=5, got=5
  0000:  15 03 02 00 90                                     .....             
tls_read: want=144, got=144
  0000:  d5 e4 4d 60 41 35 d6 e9  8d 4d a7 c3 6f 73 45 92   ..M`A5...M..osE.  
  0010:  55 05 2c a7 80 8a 40 31  1f eb 41 d0 38 72 4d 2b   U.,...@1..A.8rM+  
  0020:  7b 22 c3 62 b7 73 45 43  d6 f3 3a e4 84 e4 f8 fa   {".b.sEC..:.....  
  0030:  a8 f3 d6 3b 6d 19 81 c8  3a 18 c3 06 0d 02 e5 32   ...;m...:......2  
  0040:  73 ee f5 aa 57 37 71 e8  6f cc 28 8c 7b f3 eb 09   s...W7q.o.(.{...  
  0050:  a0 82 8a 6b 70 e0 da cb  5f a6 40 44 65 af f2 b1   ...kp..._.@De...  
  0060:  f8 db 17 e5 71 df e0 86  3b 22 77 af 0a 9f d2 46   ....q...;"w....F  
  0070:  2e 45 b0 a6 21 22 e6 93  dd f1 dd 5c b3 e9 39 2d   .E..!".....\..9-  
  0080:  b7 aa f7 7d 61 3f e1 a7  8e 1b 34 d2 cf 61 95 65   ...}a?....4..a.e  
ldap_read: want=8, got=0

ldap_free_connection 1 0
tls_write: want=213 error=Broken pipe
ldap_free_connection: actually freed
ldap_err2string
ldap_result: Can't contact LDAP server (-1)

```

[https://help.ubuntu.com/community/SecuringOpenLDAPConnections](https://help.ubuntu.com/community/SecuringOpenLDAPConnections) lists the generation commands different as apache, but I would like to use the same certificate.

Any ideas if I need to convert this certificate? 

Cheers,

---

