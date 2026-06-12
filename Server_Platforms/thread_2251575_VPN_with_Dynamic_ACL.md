---
title: "VPN with Dynamic ACL"
date: 2014-11-05
forum: Server Platforms
---

### Post by povlhp on 2014-11-05
Is there any way to setup an Ubuntu Server as a VPN server with dynamic ACL ?
I would like to have the user authentication passed on to Windows, and use Windows groups to determine which ACL to apply, and if not in any of the relevant groups, disconnect the user (or give him a deny any rule, and he will get tired of the VPN).

As I see it, it could be done by having a VPN-up script creating iptables rules, and tearing them down again when the VPN connection breaks. There will be some housekeeping of course. Like cleaning up lingering rules when a new connection starts.

So it is technically possible. Is there a solution out there already what will do this for me ? I know the Cisco AnyConnect will do as I want, but I am looking for an OSS alternative.

---

### Post by bashiergui on 2014-11-08
It seems you could probably have the VPN server check ldap or samba which would integrate with windows. But I have no experience with such things. 

The links I found in my 2 minutes of Googling are old (2010). So it is theoretically possible at least. 
[https://code.google.com/p/openvpn-auth-ldap/wiki/Configuration](https://code.google.com/p/openvpn-auth-ldap/wiki/Configuration)


There's also samba auth for vpn:
[https://wiki.samba.org/index.php/VPN_Single_SignOn_with_Samba_AD](https://wiki.samba.org/index.php/VPN_Single_SignOn_with_Samba_AD)

Again, I've got no experience with it but maybe it's someplace to start.

---

### Post by howefield on 2014-11-08
Thread moved to the "*Server Platforms*" forum.

---

