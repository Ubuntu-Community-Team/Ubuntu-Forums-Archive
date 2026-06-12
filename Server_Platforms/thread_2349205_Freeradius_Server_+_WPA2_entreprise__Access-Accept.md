---
title: "Freeradius Server + WPA2 entreprise : Access-Accept but not connected"
date: 2017-01-12
forum: Server Platforms
---

### Post by knoxys on 2017-01-12
Hi,

First I'm sorry for my bad English...

I just install Freeradius ([using this tutorial]("https://blog.fenrir.fr/2013/09/07/655/")), everything work (I get a access-accept when I try the radtest command) but when I try connect to the AP using WPA2 Entreprise, my devise (I use an Iphone but with a Laptop I get the same problem) don't connect.

I don't have any error message, and after few try the device "give up" I mean without any error message it just stop.

On the Freeradius server when I use the Freeradius -X command I can see the Access-Accept but my device re-try a connection.

I have no idea where the problem come from...

Here the log :

```

rad_recv: Access-Request packet from host 192.168.11.122 port 55831, id=21, length=166
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        EAP-Message = 0x0276000d01612e74617270696e
        Message-Authenticator = 0xb482c3828728d8da3c17525c676fd015
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+group authorize {
++[preprocess] = ok
++[chap] = noop
++[mschap] = noop
++[digest] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
[eap] EAP packet type response id 118 length 13
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] = updated
++[files] = noop
++[expiration] = noop
++[logintime] = noop
[pap] WARNING! No "known good" password found for the user.  Authentication may fail because of this.
++[pap] = noop
+} # group authorize = updated
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/default
+group authenticate {
[eap] EAP Identity
[eap] processing type tls
[tls] Initiate
[tls] Start returned 1
++[eap] = handled
+} # group authenticate = handled
Sending Access-Challenge of id 21 to 192.168.11.122 port 55831
        EAP-Message = 0x017700061520
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa03d9759a04a8245fd2c6df765db38ab
Finished request 21.
Going to the next request
Waking up in 0.4 seconds.
rad_recv: Access-Request packet from host 192.168.11.122 port 55831, id=22, length=302
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        EAP-Message = 0x02770083158000000079160301007401000070030158765ace5ef18faad8307cbb0cb6e1fee9808dee2aba37a3bb2a535985894cf900002800ffc024c023c00ac009c008c028c027c014c013c012003d003c0035002f000ac007c011000500040100001f000a00080006001700180019000b0002010000050005010000000000120000
        State = 0xa03d9759a04a8245fd2c6df765db38ab
        Message-Authenticator = 0x884818949d3791fb2181464655b473bf
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+group authorize {
++[preprocess] = ok
++[chap] = noop
++[mschap] = noop
++[digest] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
[eap] EAP packet type response id 119 length 131
[eap] Continuing tunnel setup.
++[eap] = ok
+} # group authorize = ok
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/default
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/ttls
[eap] processing type ttls
[ttls] Authenticate
[ttls] processing EAP-TLS
  TLS Length 121
[ttls] Length Included
[ttls] eaptls_verify returned 11
[ttls]     (other): before/accept initialization
[ttls]     TLS_accept: before/accept initialization
[ttls] <<< Unknown TLS version [length 0005]
[ttls] <<< TLS 1.0 Handshake [length 0074], ClientHello
[ttls]     TLS_accept: unknown state
[ttls] >>> Unknown TLS version [length 0005]
[ttls] >>> TLS 1.0 Handshake [length 0039], ServerHello
[ttls]     TLS_accept: unknown state
[ttls] >>> Unknown TLS version [length 0005]
[ttls] >>> TLS 1.0 Handshake [length 02ce], Certificate
[ttls]     TLS_accept: unknown state
[ttls] >>> Unknown TLS version [length 0005]
[ttls] >>> TLS 1.0 Handshake [length 014b], ServerKeyExchange
[ttls]     TLS_accept: unknown state
[ttls] >>> Unknown TLS version [length 0005]
[ttls] >>> TLS 1.0 Handshake [length 0004], ServerHelloDone
[ttls]     TLS_accept: unknown state
[ttls]     TLS_accept: unknown state
[ttls]     TLS_accept: unknown state
[ttls]     TLS_accept: Need to read more data: unknown state
[ttls]     TLS_accept: Need to read more data: unknown state
In SSL Handshake Phase
In SSL Accept mode
[ttls] eaptls_process returned 13
++[eap] = handled
+} # group authenticate = handled
Sending Access-Challenge of id 22 to 192.168.11.122 port 55831
        EAP-Message = 0x0178040015c00000046a1603010039020000350301b0b0c4309fe9e28baac03c379994a03c43c17edabf896adbe77d7c50ba92312e00c01400000dff01000100000b00040300010216030102ce0b0002ca0002c70002c4308202c0308201a8a003020102020900f20ccd35f5be79e0300d06092a864886f70d01010b050030183116301406035504030c0d7562756e74752d726164697573301e170d3137303131313133343430315a170d3237303130393133343430315a30183116301406035504030c0d7562756e74752d72616469757330820122300d06092a864886f70d01010105000382010f003082010a0282010100bae84393e78ab8117a34
        EAP-Message = 0x76a096a31a3e72a0687854fdb31f9471d7f73fc8b9efa43b5a4e7d5d98d6c7a86e55bcbd389e1ca26c8b5437f42f576c433fd19e8c3e5643d6066213a5383637a2bed3647057955d01ff33529b81cf41d72e6b6b27afd6aeec77fa1cf9b12017dbe1e0a4dbcf9edb451d764f54c441d1673f843c54cf01077a7298d9db84271628e244913e33d189625134fe482979915758b6d3b037fa255f2f52d8ba4d7fabf0ce4f0f2d769d81bee74047a97337568ea22fb52a14976ead23a3cadad2025a33a6c82e86de4fbe4d7d72ed5ecfbf2ed17e7e0473194f4e256a3059c0602f7ff48e011506a6b1377d2e231eff0230e4b705f08d83ef0203010001a30d
        EAP-Message = 0x300b30090603551d1304023000300d06092a864886f70d01010b0500038201010054ac44d1f29e6edd1a0acc5a17366b78f30aa398f650f9adc659ff1c13b83e1755cb79bf6f7b67a9181eeda92656503673b7ab6868d0630930c84393dbee3e22740dbcf6bffaacb2e1256a0a6bc55f733fc7f760b14ed6cbdcf3077f28b6f4a555f9bac811e1b2e8a9e63ef90dd3790754d3feadc8f63c178e23279e9b3478c5d129ccc71c97776489b93a7e83599e180289509cdb671acf4ad68c79f6af0745b71ac8268e5fa864155e722da3293764c4123466d6937963361207c883a4678695c8f222db95a74bc779a63e6520e2e41ab3fe0239bf4afe388e6acb
        EAP-Message = 0x893f42b934b7aadd295ba4a5ce95b63ce8626c77ff63e860adc0ed611a13fa690ea22af5160301014b0c000147030017410432ca055c5c5b05b16674f7d9d1e9d004ecf2f103149134845196166fb05a30c237ce8006f620452d5e894a537e1a2a36dffbe42b1f822469a6e149d1be40f7f5010085ded0a16cf16c029409d4736e8771de33c73fe160dd5736ad16d16c8cc901aa8183289209c2182b6d4ca9e0904956c29f48249490ef3105dfa033ed72dc0ac415f517acd6274012814a997668ebd64a8b274b3b080cb19e88efec06fac54b27eaf8af80ad7b6c880428cd7b178c638d465504a75588ab9ac2dc7eb549cf21f4144da59dc52a80639b
        EAP-Message = 0x4898b9179a8a4cbd1c3e8e02
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa03d9759a1458245fd2c6df765db38ab
Finished request 22.
Going to the next request
Waking up in 0.4 seconds.
rad_recv: Access-Request packet from host 192.168.11.122 port 55831, id=23, length=177
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        EAP-Message = 0x027800061500
        State = 0xa03d9759a1458245fd2c6df765db38ab
        Message-Authenticator = 0xb74d4f399f88faa2dc6ecab5a7c59ef5
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+group authorize {
++[preprocess] = ok
++[chap] = noop
++[mschap] = noop
++[digest] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
[eap] EAP packet type response id 120 length 6
[eap] Continuing tunnel setup.
++[eap] = ok
+} # group authorize = ok
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/default
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/ttls
[eap] processing type ttls
[ttls] Authenticate
[ttls] processing EAP-TLS
[ttls] Received TLS ACK
[ttls] ACK handshake fragment handler
[ttls] eaptls_verify returned 1
[ttls] eaptls_process returned 13
++[eap] = handled
+} # group authenticate = handled
Sending Access-Challenge of id 23 to 192.168.11.122 port 55831
        EAP-Message = 0x0179007e15800000046a27736e313a9c94129d2e20ff6d830a5a4453100de43302a99f64c039ff4ebeb6346b5a970651e82c6675b58711f87aabbe0ce6b517e6748c9b8d875de71e1358910b6444b7768d9892592f05d8394b46a0d8c69569cbdcb3b705993cf58dbcfeecac447d0016d0c3a0849016030100040e000000
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa03d9759a2448245fd2c6df765db38ab
Finished request 23.
Going to the next request
Waking up in 0.4 seconds.
rad_recv: Access-Request packet from host 192.168.11.122 port 55831, id=24, length=315
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        EAP-Message = 0x027900901580000000861603010046100000424104337e617747f33b002b76e435dc1a015dd8f2ce5bd23637e098b5d2b4b1d322c45359672ed0cdf5606884847fce6c20bb6df07d7447a8efc2eb4a3327f73f9e561403010001011603010030c10b7ec571ea0d94355fc52ccc65e4fe8de14af82d6513d0ba6c2789dbb20ea51c2ab948d5eb88ee83d48b0618a118a6
        State = 0xa03d9759a2448245fd2c6df765db38ab
        Message-Authenticator = 0x3f77a4fc48400fd15e67f53d2ed27281
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+group authorize {
++[preprocess] = ok
++[chap] = noop
++[mschap] = noop
++[digest] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
[eap] EAP packet type response id 121 length 144
[eap] Continuing tunnel setup.
++[eap] = ok
+} # group authorize = ok
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/default
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/ttls
[eap] processing type ttls
[ttls] Authenticate
[ttls] processing EAP-TLS
  TLS Length 134
[ttls] Length Included
[ttls] eaptls_verify returned 11
[ttls] <<< Unknown TLS version [length 0005]
[ttls] <<< TLS 1.0 Handshake [length 0046], ClientKeyExchange
[ttls]     TLS_accept: unknown state
[ttls]     TLS_accept: unknown state
[ttls] <<< Unknown TLS version [length 0005]
[ttls] <<< TLS 1.0 ChangeCipherSpec [length 0001]
[ttls] <<< Unknown TLS version [length 0005]
[ttls] <<< TLS 1.0 Handshake [length 0010], Finished
[ttls]     TLS_accept: unknown state
[ttls] >>> Unknown TLS version [length 0005]
[ttls] >>> TLS 1.0 ChangeCipherSpec [length 0001]
[ttls]     TLS_accept: unknown state
[ttls] >>> Unknown TLS version [length 0005]
[ttls] >>> TLS 1.0 Handshake [length 0010], Finished
[ttls]     TLS_accept: unknown state
[ttls]     TLS_accept: unknown state
[ttls]     (other): SSL negotiation finished successfully
SSL Connection Established
[ttls] eaptls_process returned 13
++[eap] = handled
+} # group authenticate = handled
Sending Access-Challenge of id 24 to 192.168.11.122 port 55831
        EAP-Message = 0x017a004515800000003b140301000101160301003067d24b1e24d98dd8358608a799d2d98a6c803b22a1ea02edd2876c83bce05478c4d42863ba281bde613fcd93746b5db4
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa03d9759a3478245fd2c6df765db38ab
Finished request 24.
Going to the next request
Waking up in 0.4 seconds.
rad_recv: Access-Request packet from host 192.168.11.122 port 55831, id=25, length=234
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        EAP-Message = 0x027a003f1580000000351703010030d90dc3c6217fad6c4a190dbcc710ce24952e5590ddf783a118ed33f2dd37cc8448a64e6283bd5e897d7205b56f5d3885
        State = 0xa03d9759a3478245fd2c6df765db38ab
        Message-Authenticator = 0xe5d71870121582e829028705cfaffddc
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+group authorize {
++[preprocess] = ok
++[chap] = noop
++[mschap] = noop
++[digest] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
[eap] EAP packet type response id 122 length 63
[eap] Continuing tunnel setup.
++[eap] = ok
+} # group authorize = ok
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/default
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/ttls
[eap] processing type ttls
[ttls] Authenticate
[ttls] processing EAP-TLS
  TLS Length 53
[ttls] Length Included
[ttls] eaptls_verify returned 11
[ttls] <<< Unknown TLS version [length 0005]
[ttls] eaptls_process returned 7
[ttls] Session established.  Proceeding to decode tunneled attributes.
[ttls] Got tunneled request
        EAP-Message = 0x0200000d01612e74617270696e
        FreeRADIUS-Proxied-To = 127.0.0.1
[ttls] Got tunneled identity of a.tarpin
[ttls] Setting default EAP type for tunneled EAP session.
[ttls] Sending tunneled request
        EAP-Message = 0x0200000d01612e74617270696e
        FreeRADIUS-Proxied-To = 127.0.0.1
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        NAS-IP-Address = 192.168.11.122
server inner-tunnel {
# Executing section authorize from file /etc/freeradius/sites-enabled/inner-tunnel
+group authorize {
++[chap] = noop
++[mschap] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
++update control {
++} # update control = noop
[eap] EAP packet type response id 0 length 13
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] = updated
++[files] = noop
++[expiration] = noop
++[logintime] = noop
++[pap] = noop
+} # group authorize = updated
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/inner-tunnel
+group authenticate {
[eap] EAP Identity
[eap] processing type mschapv2
rlm_eap_mschapv2: Issuing Challenge
++[eap] = handled
+} # group authenticate = handled
} # server inner-tunnel
[ttls] Got tunneled reply code Access-Challenge
        EAP-Message = 0x010100221a0101001d1038372371be1aa9ef32ee8866de250ed1612e74617270696e
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa27a3a04a27b208a9cc215a0320ce53e
[ttls] Got tunneled Access-Challenge
[ttls] >>> Unknown TLS version [length 0005]
++[eap] = handled
+} # group authenticate = handled
Sending Access-Challenge of id 25 to 192.168.11.122 port 55831
        EAP-Message = 0x017b005f158000000055170301005013cfcfbb5f2326d02ad8a21f00b79de7f7f9440febe577f655b77b7bea4f7eff27da9be6db7afb7ed3b6033d7fafe0b02395320aaf8d37e9c1c0e2d3330887789e21a7b6b1960a7cff3c197313824851
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa03d9759a4468245fd2c6df765db38ab
Finished request 25.
Going to the next request
Waking up in 0.3 seconds.
rad_recv: Access-Request packet from host 192.168.11.122 port 55831, id=26, length=298
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        EAP-Message = 0x027b007f158000000075170301007011784dd9efc131615186767a7cb5c3b78df7760875fc18dda10bdbd1459549d53e678135a681fee2fd6871fb8ac703b9b32e689df31ca3d86a662dc31dbb2d9629c135b8bd69c8a2cf9d94c97b6eff528d64f8165292d61a32ab595c8b71111147a082a4821e1b8f9a537822e9ad2dd4
        State = 0xa03d9759a4468245fd2c6df765db38ab
        Message-Authenticator = 0x4bb694e9e82fd6e061f4e9659a2da866
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+group authorize {
++[preprocess] = ok
++[chap] = noop
++[mschap] = noop
++[digest] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
[eap] EAP packet type response id 123 length 127
[eap] Continuing tunnel setup.
++[eap] = ok
+} # group authorize = ok
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/default
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/ttls
[eap] processing type ttls
[ttls] Authenticate
[ttls] processing EAP-TLS
  TLS Length 117
[ttls] Length Included
[ttls] eaptls_verify returned 11
[ttls] <<< Unknown TLS version [length 0005]
[ttls] eaptls_process returned 7
[ttls] Session established.  Proceeding to decode tunneled attributes.
[ttls] Got tunneled request
        EAP-Message = 0x020100431a0201003e31c10dfb638800e1500de9b56668cb74060000000000000000c88722ab37ce3585bfd3682bf02b02a4387b3766229aac2f00612e74617270696e
        FreeRADIUS-Proxied-To = 127.0.0.1
[ttls] Sending tunneled request
        EAP-Message = 0x020100431a0201003e31c10dfb638800e1500de9b56668cb74060000000000000000c88722ab37ce3585bfd3682bf02b02a4387b3766229aac2f00612e74617270696e
        FreeRADIUS-Proxied-To = 127.0.0.1
        User-Name = "a.tarpin"
        State = 0xa27a3a04a27b208a9cc215a0320ce53e
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        NAS-IP-Address = 192.168.11.122
server inner-tunnel {
# Executing section authorize from file /etc/freeradius/sites-enabled/inner-tunnel
+group authorize {
++[chap] = noop
++[mschap] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
++update control {
++} # update control = noop
[eap] EAP packet type response id 1 length 67
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] = updated
++[files] = noop
++[expiration] = noop
++[logintime] = noop
++[pap] = noop
+} # group authorize = updated
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/inner-tunnel
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/mschapv2
[eap] processing type mschapv2
[mschapv2] # Executing group from file /etc/freeradius/sites-enabled/inner-tunnel
[mschapv2] +group MS-CHAP {
[mschap] Creating challenge hash with username: a.tarpin
[mschap] Client is using MS-CHAPv2 for a.tarpin, we need NT-Password
[mschap]        expand: %{Stripped-User-Name} ->
[mschap]        ... expanding second conditional
[mschap]        expand: %{User-Name} -> a.tarpin
[mschap]        expand: %{%{User-Name}:-None} -> a.tarpin
[mschap]        expand: --username=%{%{Stripped-User-Name}:-%{%{User-Name}:-None}} -> --username=a.tarpin
[mschap] Creating challenge hash with username: a.tarpin
[mschap]        expand: %{mschap:Challenge} -> f8edaa904e9fa6d1
[mschap]        expand: --challenge=%{%{mschap:Challenge}:-00} -> --challenge=f8edaa904e9fa6d1
[mschap]        expand: %{mschap:NT-Response} -> c88722ab37ce3585bfd3682bf02b02a4387b3766229aac2f
[mschap]        expand: --nt-response=%{%{mschap:NT-Response}:-00} -> --nt-response=c88722ab37ce3585bfd3682bf02b02a4387b3766229aac2f
Exec output: NT_KEY: 01DAD29C6673DE9BAEBBE44D48C51144
Exec plaintext: NT_KEY: 01DAD29C6673DE9BAEBBE44D48C51144
[mschap] Exec: program returned: 0
[mschap] adding MS-CHAPv2 MPPE keys
++[mschap] = ok
+} # group MS-CHAP = ok
MSCHAP Success
++[eap] = handled
+} # group authenticate = handled
} # server inner-tunnel
[ttls] Got tunneled reply code Access-Challenge
        EAP-Message = 0x010200331a0301002e533d46353045323446453334373645323837353836313433443338443736343831443244314142353734
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa27a3a04a378208a9cc215a0320ce53e
[ttls] Got tunneled Access-Challenge
[ttls] >>> Unknown TLS version [length 0005]
++[eap] = handled
+} # group authenticate = handled
Sending Access-Challenge of id 26 to 192.168.11.122 port 55831
        EAP-Message = 0x017c006f158000000065170301006011761203ff7caf21dd10aade0c2611d83e6360a822eb7d36687dac99645d9934600d20c5bdd07bebc121d18e4eb9d4e2d9be9eb5471af9f49ae21c6e3a216102250ba19cd5893b42233397d0517c56256d48859513f388ba2f714c54b7131ea3
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0xa03d9759a5418245fd2c6df765db38ab
Finished request 26.
Going to the next request
Waking up in 0.3 seconds.
rad_recv: Access-Request packet from host 192.168.11.122 port 55831, id=27, length=234
        User-Name = "a.tarpin"
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        EAP-Message = 0x027c003f1580000000351703010030cb530b6a02511df7bf36a2fa6d3d5bc5f0a6441a155f462cbb00b4d2d0cbd4542d2c5f9040487cc2c483a970575d6161
        State = 0xa03d9759a5418245fd2c6df765db38ab
        Message-Authenticator = 0x7be49a2ae9d9f035ab78cc30ed8d0397
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+group authorize {
++[preprocess] = ok
++[chap] = noop
++[mschap] = noop
++[digest] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
[eap] EAP packet type response id 124 length 63
[eap] Continuing tunnel setup.
++[eap] = ok
+} # group authorize = ok
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/default
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/ttls
[eap] processing type ttls
[ttls] Authenticate
[ttls] processing EAP-TLS
  TLS Length 53
[ttls] Length Included
[ttls] eaptls_verify returned 11
[ttls] <<< Unknown TLS version [length 0005]
[ttls] eaptls_process returned 7
[ttls] Session established.  Proceeding to decode tunneled attributes.
[ttls] Got tunneled request
        EAP-Message = 0x020200061a03
        FreeRADIUS-Proxied-To = 127.0.0.1
[ttls] Sending tunneled request
        EAP-Message = 0x020200061a03
        FreeRADIUS-Proxied-To = 127.0.0.1
        User-Name = "a.tarpin"
        State = 0xa27a3a04a378208a9cc215a0320ce53e
        NAS-Identifier = "802aa89673dd"
        NAS-Port = 0
        Called-Station-Id = "82-2A-A8-98-73-DD:wifi-test"
        Calling-Station-Id = "04-4B-ED-1A-3B-6C"
        Framed-MTU = 1400
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 0Mbps 802.11b"
        NAS-IP-Address = 192.168.11.122
server inner-tunnel {
# Executing section authorize from file /etc/freeradius/sites-enabled/inner-tunnel
+group authorize {
++[chap] = noop
++[mschap] = noop
[suffix] No '@' in User-Name = "a.tarpin", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] = noop
++update control {
++} # update control = noop
[eap] EAP packet type response id 2 length 6
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] = updated
++[files] = noop
++[expiration] = noop
++[logintime] = noop
++[pap] = noop
+} # group authorize = updated
Found Auth-Type = EAP
# Executing group from file /etc/freeradius/sites-enabled/inner-tunnel
+group authenticate {
[eap] Request found, released from the list
[eap] EAP/mschapv2
[eap] processing type mschapv2
[eap] Freeing handler
++[eap] = ok
+} # group authenticate = ok
  WARNING: Empty post-auth section.  Using default return values.
# Executing section post-auth from file /etc/freeradius/sites-enabled/inner-tunnel
} # server inner-tunnel
[ttls] Got tunneled reply code Access-Accept
        MS-MPPE-Encryption-Policy = 0x00000002
        MS-MPPE-Encryption-Types = 0x00000004
        MS-MPPE-Send-Key = 0xd2945975ecf1a221e1ee1d070d2891dd
        MS-MPPE-Recv-Key = 0x834f4d25d1269b7014c27c5140b1f898
        EAP-Message = 0x03020004
        Message-Authenticator = 0x00000000000000000000000000000000
        User-Name = "a.tarpin"
[ttls] Got tunneled Access-Accept
[eap] Freeing handler
rlm_eap_ttls: Freeing handler for user a.tarpin
++[eap] = ok
+} # group authenticate = ok
# Executing section post-auth from file /etc/freeradius/sites-enabled/default
+group post-auth {
++[exec] = noop
+} # group post-auth = noop
Sending Access-Accept of id 27 to 192.168.11.122 port 55831
        MS-MPPE-Encryption-Policy = 0x00000002
        MS-MPPE-Encryption-Types = 0x00000004
        MS-MPPE-Send-Key = 0xd2945975ecf1a221e1ee1d070d2891dd
        MS-MPPE-Recv-Key = 0x834f4d25d1269b7014c27c5140b1f898
        Message-Authenticator = 0x00000000000000000000000000000000
        User-Name = "a.tarpin"
        MS-MPPE-Recv-Key = 0xe27cfc4aeaf04ba460adf86811d3c2a068b52bbe4e30d0e79c48a1d801de5bbc
        MS-MPPE-Send-Key = 0x4e3c07e4df836b2af32406a60a1ba337d035d39c2608723f6c43a54c636db116
        EAP-Message = 0x037c0004
Finished request 27.
Going to the next request
Waking up in 0.3 seconds.
Cleaning up request 14 ID 14 with timestamp +17
Cleaning up request 15 ID 15 with timestamp +17
Cleaning up request 16 ID 16 with timestamp +17
Cleaning up request 17 ID 17 with timestamp +17
Cleaning up request 18 ID 18 with timestamp +17
Cleaning up request 19 ID 19 with timestamp +17
Cleaning up request 20 ID 20 with timestamp +17
Waking up in 4.3 seconds.
Cleaning up request 21 ID 21 with timestamp +22
Cleaning up request 22 ID 22 with timestamp +22
Cleaning up request 23 ID 23 with timestamp +22
Cleaning up request 24 ID 24 with timestamp +22
Cleaning up request 25 ID 25 with timestamp +22
Cleaning up request 26 ID 26 with timestamp +22
Cleaning up request 27 ID 27 with timestamp +22
Ready to process requests.



```

---

