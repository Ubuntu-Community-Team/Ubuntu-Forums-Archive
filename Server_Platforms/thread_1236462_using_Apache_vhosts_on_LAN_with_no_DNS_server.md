---
title: "using Apache vhosts on LAN with no DNS server"
date: 2009-08-10
forum: Server Platforms
---

### Post by vallis on 2009-08-10
Hey all,
I've recently made some changes to my Apache setup at home; using a vhost for each site instead of a single vhost with different sites in sub-directories.  This is obviously the better way to do things as my local setup (purely for testing before upload) now mimics that of my web hosting company.

The problem is that using vhosts I need DNS if I want to test my sites from other machines. So is there anything I can do other than to manually set up DNS entries in all of my machines hosts files?

All I want to be able to do is access, for example, [http://mysite.local](http://mysite.local) from any machine on my LAN without having to add "192.168.x.y mysite.local" to every machines hosts file.

My network setup is simple: PCs connected by wire or wireless to a Netgear DG834G, then on to the internet.
The router acts as a DNS server so if possible I would like to add DNS entries there so that all LAN machines are affected.

Any advice would be much appreciated.

Regards,
V.

edit: just realised the router is only a DNS proxy so adding entries wont be possible (I don't think)

---

### Post by R.Bucky on 2009-08-11
Just install BIND or another DNS Server. I operated without DNS for many months because BIND was a pain and I could not configure it. With that said, you can edit your /etc/hosts file to reflect your internal ip associated with your subdomains (e.g. 192.168.1.105 sub.domain.com). However, certain CMS's require the domain name in the path (e.g. Wordpress and Concrete5).

Your router will not provide the proper DNS for NAT'ing.

---

### Post by vallis on 2009-08-12
Thanks for the reply Mark.
I'd thought about setting up a BIND server but, like you, didn't have the motivation to learn its ins and outs.
I guess you're right though, it's the best way.
Once I have BIND set up on my machine I can point my other machines to use me as their first DNS server then the router, which forwards my ISPs DNS servers.

I may be back in touch for some advice on setting up BIND.

Regards,
V.

---

### Post by R.Bucky on 2009-08-12
Sure, anytime. PM me here or use one of the contact forms on my web sites for help.

---

### Post by koenn on 2009-08-13
consider installing dnsmasq.
it's a simple dns + dhcp server. 
It uses de server's /etc/hosts as zone file, so you just enter names and addresses there. That's a lot easier than settinng up bind, and sufficient for your intended use.

---

