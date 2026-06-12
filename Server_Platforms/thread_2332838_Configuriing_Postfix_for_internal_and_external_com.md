---
title: "Configuriing Postfix for internal and external communication through two networks"
date: 2016-08-04
forum: Server Platforms
---

### Post by radiac2 on 2016-08-04
Hi together,

our mail-server worked quite well, sending and receiving mails through eth0 (internet connection). Now we are using openvpn to connect two companies and I have to reconfigure postfix, to send and receive mails through the vpn tunnel as well, but only for a special domain (or can it discover this itself?!) as the mail traffic shall not be send through the internet. So how do I tell this postfix?

I tried to add the openvpn IP to the inet_interfaces parameter but that didn't work. 

Does anybody of you has a clue?

Thanks a lot!

Lars

---

