---
title: "Configure server like a shared host"
date: 2008-08-15
forum: Server Platforms
---

### Post by blueherring on 2008-08-15
I'd like to configure my Ubuntu server to look as much like a shared host as I can, to use as a sandbox like development environment for developing multiple client's websites.

I'm basicly a newbie as a system administrator, I've been an on and off 'nix user for a couple decades, and a code of server applications, as well as a consumer of CPanel shared host websites.  I guess I'd mostly like to be able to configure the LAMP and FTP environments to more or less mirror what I'd see using reseller hosting, that is, directories that are protected from each other as user accounts, structure like /home/websitename/public_html, and separate FTP accounts for each website; plus if possible, Apache subdomains like websitename.192.168.x.x.    Would be awesome if I could set up scripts that will automagically configure new sites rather than doing it by hand.

Can you give me some pointers to resource that can help me do this, & perhaps a recommendation for a book?   Thanks 
much:guitar:

---

### Post by cariboo on 2008-08-15
I think [this]("http://www.ispconfig.org/manual_installation.htm") is what you are looking for.

Jim

---

### Post by windependence on 2008-08-16
Check this out:

[http://httpd.apache.org/docs/2.0/vhosts/mass.html](http://httpd.apache.org/docs/2.0/vhosts/mass.html)

-Tim

---

