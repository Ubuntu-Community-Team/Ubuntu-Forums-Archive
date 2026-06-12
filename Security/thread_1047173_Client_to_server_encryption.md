---
title: "Client to server encryption"
date: 2009-01-22
forum: Security
---

### Post by ruipedroca on 2009-01-22
Hi,

I wanted to have a server in a datacenter, but I'm worried about how to secure the communications.

We only run ubuntu machines (server and clients) and the server will have webmail, forum and a samba server).

Would it really be necessary a VPN with Cisco routers (or Draytek) and an expensive firewall or are there other solutions you would advise?

---

### Post by hyper_ch on 2009-01-22
what do you want to secure against what/whom?

---

### Post by ruipedroca on 2009-01-22
> **hyper_ch said:**
> what do you want to secure against what/whom?

Well, first of all the usernames and passwords that give access to webmail, forum, samba folders, because for what I've read around they are sent in http which might be "listened". 

Second, the files themselves, ie, I'd like them to go encrypted all the way from the client until the server.

I've read about OpenVPN, SSL and Kerberos, but I need some advice, because, for example Firefox 3 seems to have SSL 3.0 and TLS 1.0 for encryption, but I don't know if it's enough.

If you were to do it, how would you do it?


Regards!

---

### Post by hyper_ch on 2009-01-23
well, if you want to encrypt the files you'll have to get luks/dm-crypt and very likely you need to encrypt that system on the fly as you don't have access to it. It's not impossible but not so easy.

and for the data exchange, use https for webbrowser stuff (webmail, forum). Don't use samba but sftp/scp, TLS for email clients...

---

### Post by ruipedroca on 2009-01-25
thanks, hyper_ch!

---

