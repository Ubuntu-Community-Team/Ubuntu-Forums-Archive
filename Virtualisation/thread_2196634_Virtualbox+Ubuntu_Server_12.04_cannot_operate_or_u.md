---
title: "Virtualbox+Ubuntu Server 12.04: cannot operate or use openvpn"
date: 2013-12-30
forum: Virtualisation
---

### Post by jsms on 2013-12-30
I am trying to use openvpn with Ubuntu server 12.04 via virtualbox, and have been unsuccessful so far.
I have gotten various different error messages, this is the one I am currently getting: 
> 
[COLOR=#29F914][FONT=Andale Mono]tma@SGFS:/etc/openvpn$ sudo openvpn --config "vpn-at4_ovpn065.conff"[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]Mon Dec 30 15:26:40 2013 OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Feb 27 2013[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]Mon Dec 30 15:26:40 2013 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]Mon Dec 30 15:26:40 2013 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]Mon Dec 30 15:26:40 2013 WARNING: file 'vpn-at4_ovpn065.key' is group or others accessible[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]Mon Dec 30 15:26:40 2013 LZO compression initialized[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]Mon Dec 30 15:26:40 2013 failed to find GID for group nobody[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]Mon Dec 30 15:26:40 2013 Exiting[/FONT][/COLOR]


---

