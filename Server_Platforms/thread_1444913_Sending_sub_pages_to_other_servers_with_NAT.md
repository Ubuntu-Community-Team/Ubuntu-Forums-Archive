---
title: "Sending sub pages to other servers with NAT"
date: 2010-04-01
forum: Server Platforms
---

### Post by CyberCowboy on 2010-04-01
OK I'm not sure where would be the best place to post this so I'm trying this forum in the hopes that either I can get an answer or pointed to where to ask.

On my home network I have an [amahi]("http://www.amahi.org/") server and a web/mail (apache2) server.  These are both just for home use.

The web/mail server has my squirrelmail so it obviously needs port 80 sent to it and is presently accessable from the outside world, but I'd like to make a sub page (i.e. [http://domain.com/HERE](http://domain.com/HERE)) where the HERE points to my AMAHI server so I can share some of the content on that box with family (home movies and photos mostly)

My router is a PFSense box 192.168.1.1, web/mail is a fully patched 9.04 in a virtualbox 3 with Apache 2 192.168.1.204, Amahi is fedora 12 192.168.1.10.

I'm fairly good with hardware but basically crap when it comes to web admin I followed How-to Forges's Perfect server guide for the web/mail box (but am not using the DNS feature on it, using it on AMAHI) any help or additional info would be greatly appreciated.

---

### Post by Jekshadow on 2010-04-01
Apache2 + [mod_proxy]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html")?

---

### Post by CyberCowboy on 2010-04-02
> **Jekshadow said:**
> Apache2 + [mod_proxy]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html")?

that looks like it might just work with the proxypass directive.  Will have to do some research on usage and such but might just work, thanks.

---

