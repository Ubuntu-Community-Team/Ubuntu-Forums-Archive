---
title: "Help ? - Howto set up VPN and samba with mysql"
date: 2008-10-23
forum: Server Platforms
---

### Post by zitcon on 2008-10-23
Hi

I am setting up a fileserver at my home for me and my family, and want following things:

**Samba:**
User database that use mysql

Different permissions / acces on folders , example :
\\server\pvt\max - Only accesable by user max
\\server\pvt\Nina - Only accesable by Nina
\\server\Media\ - Read permissions by everyone
- I also want an admin user (me) , that have 777 permission on all folders .

**VPN**
At this point, I am really blank .
Use OpenVPN ?
I've googled for tutorials and howtos, but that was really not much help .
- Is it possible to use the same mysql DB ?

**What I've done so far**
Not much really, never done this before so I don't know where to start .
- Samba is working, not with wanted user-db , tough 
- Installed OpenVPN

**Info**
Server: HP pavillion DV9377
Router / Modem : THOMSON ST780

**:::::**
Then, do any of you guys know how to do this ?
All tips that can get me up and running is appreciated , including links that I maybe skipped/missed when I was googleing .

Thanks for even reading my post .
:)

---

### Post by zitcon on 2008-10-24
*Bump*

Is there anyone at all that can help me ? ..

---

### Post by alain1988 on 2012-07-11
the vpn part is easy 

nano /etc/pptpd.conf

set your local op
and your remote ip (public ip)

close and save

nano /etc/ppp/option

add the lines
ms-dns 8.8.8.8
ms-dns 8.8.4.4
these are dns server of google you can add your providers's dns server also
close and save it 

nano /etc/ppp/chap-secrets

this file stores the user name and passwords for the vpn settings
ex
Linux.user thispassword * 
save and close

make sure the server has an static ip adrres
add this iptable

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
and add it to the boot sequince also

nano /etc/rc.local
**[COLOR=#3333FF][FONT=&quot][/FONT][/COLOR]**sysctl -w net.ipv4.ip_forward=1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

reboot the server

and port forward the vpn ports
for the mysql user i will look it up

---

### Post by sisco311 on 2012-07-11
Old thread closed.

[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

---

