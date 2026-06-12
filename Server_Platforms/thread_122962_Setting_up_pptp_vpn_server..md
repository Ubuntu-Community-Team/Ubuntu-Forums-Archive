---
title: "Setting up pptp vpn server."
date: 2006-01-28
forum: Server Platforms
---

### Post by HondaDirtBiker on 2006-01-28
I am setting up my computer as a PPTP VPN server. I installed the PPTPD package from synaptic.
I don't know where to go, to setup the server on my computer with this package.
I also am hoping my server will be win32 compatible.

Has anyone tried this package or another PPTP VPN package?
Thanks in advance.

---

### Post by bluemax on 2006-03-09
Hi, I know it's been a while since you posted it but how did this go? Because I'm planning on trying the same thing in the next few days.

Has anyone else had any luck in using Ubuntu as a VPN+authentication server to a Windows Active Directory domain?

I found this article on the poptop (pptpd) web site about joining a linux machine to an AD domain and setting up pptpd:
[http://poptop.sourceforge.net/dox/replacing-windows-pptp-with-linux-howto.phtml]("http://poptop.sourceforge.net/dox/replacing-windows-pptp-with-linux-howto.phtml")

I would just like to know what is involved for AD users to authenticate and VPN through an Ubuntu server into an Active Directory domain. Is there more to it than just kerberos+samba+pptpd?

---

### Post by ttallos on 2006-03-10
Yes I have done this for a while with success. You want to edit a couple of files
/etc/pptpd.conf
/etc/ppp/chap-secrets
/etc/ppp/options
You are probably going to use samba
smb.conf
read the help files for what you want I am researching openvpn it seems more secure with the whole key & certificate thing. Let me know how it goes....

---

### Post by rich on 2006-03-12
I'll add a vote for openvpn.

I don't pretend to really understand the security stuff, but enough people say it runs in ascending order :
PPTP (low)
IPSEC (med)
SSL (high)

Its then an absolute bonus that it is a breeze to set up and (IMHO) appears to run faster than PPTP. Plus it appears straight forward to roll out to windows clients.

The only thing you need to decide is whether you're really going to go for one certificate for each user. I'm too lazy for that, so I went for one certificate per type of user. 

Given all that, I can't really see why it's worth doing pptp. 



Rich

---

