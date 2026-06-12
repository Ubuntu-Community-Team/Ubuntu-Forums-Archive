---
title: "OpenVPN extending/renewing expiring certificates"
date: 2012-07-05
forum: Server Platforms
---

### Post by kdzida on 2012-07-05
Hello!  I my company we are using OpenVPN for our remote employees. The problem is that their certificates expire in just few  weeks. Is their any way to extend their certification deadline or alter their expiration? The trick is to do so without sending new certificates/keys by email nor by getting their computers back to headquarters :( .

---

### Post by spynappels on 2012-07-05
Hi there,

Would it be possible to host the certificates on your internal network and allow them to pull these down to their machines over their existing VPN connections, traffic would be encrypted in transit so the certs could be transferred securely.

---

### Post by kdzida on 2012-07-06
Thanks for reply spynappels!

Hmm... I guess there is no way to extend expiring certificate. Right?

---

### Post by spynappels on 2012-07-06
Not as far as I know.

---

### Post by SeijiSensei on 2012-07-06
If you are your own CA, and are generating the certs yourself, you may want to change the expiration next time around.  The default is a year, I believe.  I usually add "-days 3650" to the openssl command so the certificates last for ten years.  Here's an [example]("http://www.stanbarber.com/freebsd/creating-self-signed-ssl-certificates-on-freebsd-with-openssl") of how that can be done.

---

### Post by kdzida on 2012-07-08
Thanks SeijiSensei, thanks Spynappels.

---

