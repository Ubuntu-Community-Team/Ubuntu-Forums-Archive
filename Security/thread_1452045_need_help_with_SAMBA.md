---
title: "need help with SAMBA"
date: 2010-04-11
forum: Security
---

### Post by MARK5 on 2010-04-11
I am new in SAMBA and I need some help.
 
[FONT=Arial]from an administration and security perspective [FONT=Arial]I need answer with those Q as practical examples[/FONT][/FONT]


[FONT=Arial]
[LIST]
[*][FONT=Arial]What security features does SAMBA support?[/FONT][FONT=Arial]
[*][FONT=Arial]How is it possible to implement an access control list on a SAMBA server?[/FONT]
[*][FONT=Arial]What security auditing features does SAMBA support and is it possible to detect brute forcing attacks (such as NAT) against a SAMBA server?[/FONT][/FONT]
[/LIST][/FONT]

---

### Post by cariboo on 2010-04-11
The first thing you should do is check out the [Samba]("http://samba.org/") web site. The one big thing to remember is not to leave samba open to the rest of the world, it is for internal networking only.

---

### Post by alexm1971 on 2010-04-13
The Samba.org website has a lot of valuable data.  They also highlight approved commercial support options here:  [http://www.samba.org/samba/support/us.html](http://www.samba.org/samba/support/us.html)

---

### Post by HermanAB on 2010-04-14
The main thing to remember is that Samba is essentially just as insecure as ordinary Microsoft Windows networking.  It is designed for use on a LAN.  If you want real security, then you need to apply other mechanisms e.g. VLANs and VPNs.

---

### Post by Jive Turkey on 2010-04-14
By default SAMBA server in ubuntu is set to have its users/passwords synced with PAM but you can change that to LDAP or maybe something else.  Each share can have valid and invalid users specified in the share directives in /etc/samba/smb.conf You can also allow guests.  I have seen examples of allowed hosts specified there as well.  I think you can add samba users separate from the system users in addition to the synced PAM users.  UFW makes it pretty easy to firewall it to only allow connections from your LAN.  It uses pretty light encryption for the traffic itself.

---

