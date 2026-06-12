---
title: "[Samba4] LDAP over SSL"
date: 2016-01-03
forum: Server Platforms
---

### Post by elegant2 on 2016-01-03
Hi guys, I'm a bit new to Samba AD but I've managed to setup everything and am now looking to add LDAP over SSL according to the [Samba wiki]("https://wiki.samba.org/index.php/Configuring_LDAP_over_SSL_(LDAPS)_on_a_Samba_AD_DC"). My issue is that when I assign a trusted certificate to the DC, LDAP and everything related seems to stop (nmap shows all ports are now closed). This does not occur with a self-signed certificate. I am generating the certificate like so:

[COLOR=#000000][FONT=monospace]openssl genrsa -out myKey.pem 2048
openssl req -sha512 -new -key myKey.pem -out myCSR.pem
openssl x509 -sha512 -req -in myCSR.pem -CA rootCert.pem -CAkey rootCA.key -CAcreateserial -out myCert.pem -days 365[/FONT][/COLOR]

'[COLOR=#000000][FONT=monospace]rootCert.pem[/FONT][/COLOR]' was added to the ca-certificates after being rename to a .crt extension and running [COLOR=#000000][FONT=monospace]'update-ca-certificates[/FONT][/COLOR]'.

Verifying the cert '[COLOR=#000000][FONT=monospace]openssl verify /usr/local/samba/private/tls/myCert.pem[/FONT][/COLOR]' returns '[COLOR=#000000][FONT=monospace]OK[/FONT][/COLOR]' but '[COLOR=#000000][FONT=monospace]openssl s_client -showcerts -connect localhost:636[/FONT][/COLOR]' is denied with error 111 because port 636 is now closed along with many others due to having configured this certificate in '[COLOR=#000000][FONT=monospace]smb.conf[/FONT][/COLOR]'.

I'm unable to figure out what I'm missing but something on the Samba side does not like that I added these. If anyone has any insight into what I'm missing it would be greatly appreciated.

---

