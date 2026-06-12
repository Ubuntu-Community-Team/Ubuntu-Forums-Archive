---
title: "Offering MS-CHAPv2 in pppd causes Windows error 778"
date: 2010-07-08
forum: Server Platforms
---

### Post by MidSpeck on 2010-07-08
I previously had an Openswan-based IPsec/L2TP solution that was working marvelously on Ubuntu 8.04 LTS.  I upgraded to Ubuntu 10.04 LTS and cannot seem to get it working again.

First, Ubuntu's version of Openswan (2.6.23) does not work with NATted transport mode [1].  Since an L2TP connection is in transport mode, I downloaded Openswan 2.6.27 to /usr/src/, and ran "make programs" and "make install".

This allowed my IPsec and xl2tpd configuration that I previously had to work again like they were supposed to.  (Aren't you relieved this isn't an IPsec question?) :p

Anyway, xl2tpd starts up an instance of pppd for the new incoming connection using /etc/ppp/options.xl2tpd.  But for some reason my previous configuration was not working.  After hours of searching and tracking things down, I've narrowed it down to the following lines in my options.xl2tpd file:
```
require-mschap-v2
plugin winbind.so
ntlm_auth-helper '/usr/bin/ntlm_auth --helper-protocol=ntlm-server-1 --require-membership-of="EXAMPLEDOM\\VPN Users"'
```

The winbind.so plugin adds the ntlm_auth-helper functionality to pppd and calls ntlm_auth (which I believe is part of the samba/winbind package) to authenticate against a Windows server.  All my testing with ntlm_auth and wbinfo seems to work fine.  It can properly detect an incorrect username and/or password and seemingly responds appropriately. [2]

When running ntlm_auth (3.4.7) inside of pppd (2.4.5) however, my Windows clients do not like the response they get and error out with an error 778 (both XP and Vista).

Two things that work:
**a) Connecting to the same setup on the older version of Ubuntu works fine (ntlm_auth 3.0.28a and pppd 2.4.4).**
OR:
**b) Changing my ppp options file to say "require-mschap" instead of "require-mschap-v2" also works... but obviously uses MS-CHAP instead of MS-CHAPv2.**

So I'm not sure whether it's the Samba suite or the ppp daemon that is messing up here.

Do you have any thoughts?










Additional notes:

[1] [http://lists.openswan.org/pipermail/users/2009-November/017815.html](http://lists.openswan.org/pipermail/users/2009-November/017815.html)

[2] Below are 4 debug log snippets from pppd.
1) MS-CHAPv2 required, valid credentials (doesn't work!)
2) MS-CHAP required, valid credentials (works)
3) MS-CHAPv2 required, bad password (expected behavior)
4) MS-CHAPv2 required, bad username (expected behavior)

1) The first is a connection attempt with MS-CHAPv2 required:
```
sent [LCP ConfReq id=0x1 <mru 1280> <asyncmap 0x0> <auth chap MS-v2> <magic 0x6bf2894f> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <mru 1280> <asyncmap 0x0> <auth chap MS-v2> <magic 0x6bf2894f> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x74cd45cf> <pcomp> <accomp> <callback CBCP>]
sent [LCP ConfRej id=0x1 <callback CBCP>]
rcvd [LCP ConfReq id=0x2 <mru 1400> <magic 0x74cd45cf> <pcomp> <accomp>]
sent [LCP ConfAck id=0x2 <mru 1400> <magic 0x74cd45cf> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x6bf2894f]
sent [CHAP Challenge id=0x3d <2677994165a303743af14a1d2416d00c>, name = "l2tpd"]
rcvd [LCP Ident id=0x3 magic=0x74cd45cf "MSRASV5.10"]
rcvd [LCP Ident id=0x4 magic=0x74cd45cf "MSRAS-0-COMPTECH2"]
rcvd [LCP EchoRep id=0x0 magic=0x74cd45cf]
rcvd [CHAP Response id=0x3d <f5b7143b992c6ee198f917ec6aa0d29a00000000000000005dde9a89837a1ea4b4a11028dc0d6531ee5802f20475034700>, name = "shop"]
sent [CHAP Success id=0x3d "S=A8AF459F80A874EF4060C265AFA0E7065746982A M=Access granted"]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.1.1>]
rcvd [LCP TermReq id=0x5 "t\37777777715E\37777777717\000<\37777777715t\000\000\003\n"]
sent [LCP TermAck id=0x5]
```
Notice that we have "CHAP Success" and "Access granted" for the "auth chap MS-v2" method.  It's at this point that the Windows machine decides it's done with us and sends a Termination Request.

2) The next snippet is from just a minute later when I had require-mschap instead.  It's pretty much the same except for that it finishes LCP negotiations and actually works:
```
sent [LCP ConfReq id=0x1 <mru 1280> <asyncmap 0x0> <auth chap MS> <magic 0x9c583f20> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <mru 1280> <asyncmap 0x0> <auth chap MS> <magic 0x9c583f20> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x4fa614b1> <pcomp> <accomp> <callback CBCP>]
sent [LCP ConfRej id=0x1 <callback CBCP>]
rcvd [LCP ConfReq id=0x2 <mru 1400> <magic 0x4fa614b1> <pcomp> <accomp>]
sent [LCP ConfAck id=0x2 <mru 1400> <magic 0x4fa614b1> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x9c583f20]
sent [CHAP Challenge id=0x14 <1bf5f5a691098292>, name = "l2tpd"]
rcvd [LCP Ident id=0x3 magic=0x4fa614b1 "MSRASV5.10"]
rcvd [LCP Ident id=0x4 magic=0x4fa614b1 "MSRAS-0-COMPTECH2"]
rcvd [LCP EchoRep id=0x0 magic=0x4fa614b1]
rcvd [CHAP Response id=0x14 <0000000000000000000000000000000000000000000000006ccf61cf357b9068cd243bdf21ffd8e796038a49124816bc01>, name = "shop"]
sent [CHAP Success id=0x14 "Access granted"]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.1.1>]
rcvd [CCP ConfReq id=0x5 <mppe +H -M -S -L -D +C>]
sent [CCP ConfRej id=0x5 <mppe +H -M -S -L -D +C>]
rcvd [IPCP ConfReq id=0x6 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
sent [IPCP ConfRej id=0x6 <ms-wins 0.0.0.0> <ms-wins 0.0.0.0>]
rcvd [CCP ConfRej id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [CCP ConfReq id=0x2]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 192.168.1.1>]
rcvd [CCP TermReq id=0x7"O\37777777646\024\37777777661\000<\37777777715t\000\000\002\37777777734"]
sent [CCP TermAck id=0x7]
rcvd [IPCP ConfReq id=0x8 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfNak id=0x8 <addr 192.168.1.10> <ms-dns1 192.168.1.3> <ms-dns2 192.168.1.3>]
rcvd [IPCP ConfAck id=0x2 <addr 192.168.1.1>]
rcvd [IPCP ConfReq id=0x9 <addr 192.168.1.10> <ms-dns1 192.168.1.3> <ms-dns2 192.168.1.3>]
sent [IPCP ConfAck id=0x9 <addr 192.168.1.10> <ms-dns1 192.168.1.3> <ms-dns2 192.168.1.3>]
Script /etc/ppp/ip-up started (pid 8281)
Script /etc/ppp/ip-up finished (pid 8281), status = 0x0
sent [CCP ConfReq id=0x2]
rcvd [CCP TermAck id=0x2]
sent [CCP TermReq id=0x3"No compression negotiated"]
rcvd [CCP TermAck id=0x3"No compression negotiated"]
rcvd [LCP TermReq id=0xa "O\37777777646\024\37777777661\000<\37777777715t\000\000\000\000"]
Script /etc/ppp/ip-down started (pid 8306)
sent [LCP TermAck id=0xa]
```

3) Invalid password with MS-CHAPv2 (I've snipped most of the log, which is otherwise the same):
```
rcvd [CHAP Response id=0x2 <fa230d341cb67a273f099319657b0fb800000000000000009d4e88afdde17ef2af34bba3ae98d90d72e6955e34ce30a500>, name = "shop"]
sent [CHAP Failure id=0x2 "E=691 R=1 C=c9fd54b06ad08bebadeefdd879e8dc85 V=0 M=Wrong Password"]
sent [LCP TermReq id=0x2 "Authentication failed"]
rcvd [LCP TermAck id=0x2 "Authentication failed"]
```

4) Invalid user with MS-CHAPv2:
```
rcvd [CHAP Response id=0xaa <b5e024432d616fa0f0de958c65b6e12a0000000000000000f70b2e6876460f118fa9d0298176c82d822fc58b3cb1b4ad00>, name = "asdf"]
sent [CHAP Failure id=0xaa "E=691 R=1 C=3290114afa2b436f20af5db4ff5bb085 V=0 M=No such user"]
sent [LCP TermReq id=0x2 "Authentication failed"]
rcvd [LCP TermAck id=0x2 "Authentication failed"]
```

---

### Post by jhohm on 2010-08-17
I can confirm this happens in Lucid (10.04) but not in Hardy (8.04), fortunately for me it was on a new virtual machine so it was relatively easy to rebuild it in a functioning state with Hardy.

The Windows 7 RAS client has pretty decent tracing features, I began to suspect something was funny -- eventually found this thread -- when I uncovered this in the RASCHAP.LOG:

[5368] 08-16 23:53:26:206: ChapBegin(fS=0,bA=0x81)
[5368] 08-16 23:53:26:206: StoreCredentials
[5368] 08-16 23:53:26:207: ChapBegin done.
[5368] 08-16 23:53:26:207: ChapMakeMessage,RBuf=00000000
[5368] 08-16 23:53:26:207: ChapCMakeMessage...
[5368] 08-16 23:53:26:207: CS_Initial
[5368] 08-16 23:53:26:224: ChapMakeMessage,RBuf=02E8086A
[5368] 08-16 23:53:26:224: ChapCMakeMessage...
[5368] 08-16 23:53:26:224: CS_WaitForChallenge
[5368] 08-16 23:53:26:224: MakeResponseMessage...
[5368] 08-16 23:53:26:225: Generating Challenge
[5368] 08-16 23:53:26:225: GetChallenge.
[5368] 08-16 23:53:26:225: GetChallenge: LsaCallAuthenticationPackage succeeded
[5368] 08-16 23:53:26:225: GetChallenge.
[5368] 08-16 23:53:26:225: GetChallenge: LsaCallAuthenticationPackage succeeded
[5368] 08-16 23:53:26:225: GetChallengeResponse
[5368] 08-16 23:53:26:225: GetDESChallengeResponse
[5368] 08-16 23:53:26:225: GetDESChallengeResponse Success
[5368] 08-16 23:53:26:225: GetMD5ChallengeResponse Success
[5368] 08-16 23:53:26:225: GetMD5ChallengeResponse Success
[5368] 08-16 23:53:26:225: GetChallengeResponse Success
[5368] 08-16 23:53:26:225: GetChallengeResponse=0
...a message dump with the username etc...
[5368] 08-16 23:53:26:264: ChapMakeMessage,RBuf=03521F22
[5368] 08-16 23:53:26:264: ChapCMakeMessage...
[5368] 08-16 23:53:26:264: CS_ResponseSent
[5368] 08-16 23:53:26:264: Message received...
...a message dump with Access granted etc...
[5368] 08-16 23:53:26:264: Success received...
[5368] 08-16 23:53:26:264: CHAP: Signature received...
...a message dump...
[5368] 08-16 23:53:26:264: CHAP: Signature should be...
...a different message dump...
[5368] 08-16 23:53:26:267: ChapEnd

---

### Post by moblongata on 2010-09-15
I experienced this same problem that is caused by [https://bugzilla.samba.org/show_bug.cgi?id=6563](https://bugzilla.samba.org/show_bug.cgi?id=6563).   

I worked around it by downloading Samba 3.5.5 source, applying this patch ([https://bugzilla.samba.org/attachment.cgi?id=5882&action=view](https://bugzilla.samba.org/attachment.cgi?id=5882&action=view)) and adding this to the global section of smb.conf:

winbind:forcesamlogon = True

Note, the patch is written for Samba 3.5.4 but you can also apply it to 3.5.5 by changing replacing 3.5.4 with 3.5.5 at the top of the diff.

Problem solved.

---

### Post by moblongata on 2010-09-16
If you want to confirm that Samba bug 6563 is what's causing your problem before going through the trouble of recompiling, download the Python script from [https://bugzilla.samba.org/attachment.cgi?id=5015&action=view](https://bugzilla.samba.org/attachment.cgi?id=5015&action=view) and run it with your domain username and password.  Compare the resulting NT_KEY with the output from ntlm_auth when envoked by pppd or radius.  If the NT_KEY's do not match chances are you're being hit by Samba bug 6563. 

Here's what FreeRadius debug logs showed from ntlm_auth:
Exec-Program output: NT_KEY: 9E911AE4F9C62D1564545B81B7E8FEBE
Exec-Program-Wait: plaintext: NT_KEY: 9E911AE4F9C62D1564545B81B7E8FEBE

but 
$ ./ntlm_gen.py sameusername samepassword
Challenge :  82b2e5a708775263
Response  :  21d9a49f9605363cad07edaa4361227787a2fae67ffa7523
NT_KEY    :  14B4DBA3C39EAB4FA47BA79C9AA2E99D

As you can see, the NT_KEYs did not match and confirmed that Samba bug 6563 was my problem.  

In summary, patched Samba 5.5.5 fixed the problem for me.

Thanks to Midspeck and jhohm for sharing helpful troubleshooting details.

---

