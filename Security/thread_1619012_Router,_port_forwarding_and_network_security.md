---
title: "Router, port forwarding and network security"
date: 2010-11-11
forum: Security
---

### Post by malcmail on 2010-11-11
As it stands I have a small home network operating behind my modem/router. Some of the ports on this are forwarded to my PS3 for gaming but I was looking at forward some for my file server.

At the moment I've forwarded port xxx22 to port 22 on my server for SSH for instance. ANd similarly 21 for FTP (although it doesnt seem to want to connect for any more than a few seconds using that).  What I was thinking of doing was placing a small website for a handful of ppl to use on the server too and port forward again - xxx80 to 80. It works just fine but I'm a little concerned on the security front.

As I've moved the port to something different from the outside world I'm presuming I will have already cut the potential for malicious folks to wander in but is there anything else I should be doing? At the moment there's no firewall operating on the server, usually as its hidden behind the modem/router. But if I open this thign up more permanently what should I be doing? I've read a few articles on it but I'm always left with the overwhelming thought of "Thats if theres no firewall in my router" as they just seem to do the same.

Any help gratefully appreciated as always :)

---

### Post by CharlesA on 2010-11-11
Personally, I wouldn't expose plain FTP to the internet, I'd just use SFTP instead, since it uses SSH as a transport medium.

If you forward a port, you are only opening that port to the outside world, the firewall is still working fine.

If you've got SSH open to the internet, just make sure that it's secured properly - use complex passwords for *all* user accounts, disable root logins, etc.

---

### Post by SlugSlug on 2010-11-11
I install fail2ban (and or denyhosts)  to protect from SSH attacks,

port 80 is open to all and so is my ftp (just a useful place to dump stuff I need to transfer from A>B)

---

### Post by SeijiSensei on 2010-11-11
> **malcmail said:**
> ANd similarly 21 for FTP (although it doesnt seem to want to connect for any more than a few seconds using that).

FTP is a very difficult protocol to manage because in "active" mode it requires opening a second port over which the data is sent.  One alternative is [WebDAV]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") which can be enabled using the Apache webserver.  If you take this approach, you'll want to use authentication (see below).

> What I was thinking of doing was placing a small website for a handful of ppl to use on the server too and port forward again - xxx80 to 80. It works just fine but I'm a little concerned on the security front.

If you're only supporting a few people, use [authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html").  "Basic" authentication with a decent password is not hard to set up.  If you're worried about having the password(s) sniffed, look into using a [self-signed SSL certificate]("http://www.perturb.org/display/Apache_self_signed_certificate_HOWTO.html") and allow only HTTPS connections.

---

### Post by malcmail on 2010-11-14
Thanks very much for all the help there. I may be back if I get a bit stuck. Scrap that - I'm sure I'll be back WHEN I get a bit stuck ;)

---

### Post by malcmail on 2010-11-19
Thanks again guys. Tried sftp when I was away this week and worked like an utter dream :).

---

