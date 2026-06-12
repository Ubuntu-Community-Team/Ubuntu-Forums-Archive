---
title: "UFW port alias"
date: 2012-12-25
forum: Server Platforms
---

### Post by Gareth_2007 on 2012-12-25
merry christmas every one,

my list of allowed ports is getting a bit big going to different machines etc.

is there any way i can add an alias to a port number?

i would like to see the alias and not the number like what is done with ssh and samba.

thanks

---

### Post by samosamo on 2012-12-25
Your question made me think of /etc/services file. Most nix apps make good use of it. So I googled it, check it out

[quote=https://help.ubuntu.com/community/UFW#Services]
Services
You can also allow or deny by service name since ufw reads from /etc/services To see get a list of services:

less /etc/services
Allow by Service Name


sudo ufw allow <service name>
example: to allow ssh by name

sudo ufw allow ssh
Deny by Service Name


sudo ufw deny <service name>
example: to deny ssh by name

sudo ufw deny ssh
[/quote]

---

