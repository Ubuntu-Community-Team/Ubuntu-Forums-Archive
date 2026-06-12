---
title: "Need some help w/ ipv6 and nat64"
date: 2013-05-09
forum: Server Platforms
---

### Post by hiro24 on 2013-05-09
Hello all!

I'm working on getting my network transitioned to ipv6 and I'm stumbling a bit.  I was wondering if anybody could point me in the right direction.  Specifically I need help w/ the ipv6 to ipv4 communication.  I have a box set up at my network edge, and on the inside I'm world routable ipv6.  On my server at the edge of my network I have 2 NICs, one w/ IPv6 and one w/ IPv4.  I'm to understand I can set this box up w/ nat64 and it will translate back and forth between my ipv6 network and the ipv4 internet, but I'm a little fuzzy on how to set this up.  Can anybody help me out here, or point me in the right direction?

---

### Post by matt_symes on 2013-05-09
Thread moved to **server platforms**.

You're more likely to get a response in this subforum.

---

### Post by lemming465 on 2013-05-12
Since the internet is [still about 98.7% IPv4]("http://www.google.com/ipv6/statistics.html"), if you have v4 available, being dual-stack is the best way to go.  For v6-only clients to access v4-only servers, there are at least 3 issues, only 2 of which are solvable.

First, you need a NAT64 translater to rewrite IPv6 packets as IPv4 packets.  Second, you need a DNS64 translater, so that you can synthesize AAAA records when the destination host only has A.  Third, you are going to have to live with a certain level of protocol and web site breakage, because anything which embeds literal IPv4 addresses like FTP or Skype or subparts of complex web pages is likely to break.  Typically NAT64 translators are written for simplicity and scalability, and compared to classic NAT44 gateways, they have practically no proxy or protocol rewrite support.  So simple things like SSH or SMTP or HTTP to well-designed web sites will work, and everything else will break.  In spite of that, NAT64+DNS64 appears to be the main transition mechanism actually being deployed, because the alternatives such as NAT444 (NAT44 at the user plus more NAT44 at a carrier - ISP or cellphone company - gateway) or dual-stack-lite suck worse.

This week, on Linux, a typical ploy seems to be using [tayga/]("http://www.litech.org/tayga/") as the NAT64 translator and Bind 9.8 and the DNS64 translator.  You need some IPv4 addresses to feed tayga, and an IPv6 prefix of /63 or larger, because you need a spare /64 to put your /96 IPv4 surrogate addresses under.  You can find more detailed directions at places like:
[http://www.tunnelbroker.net/forums/index.php?topic=1998.0](http://www.tunnelbroker.net/forums/index.php?topic=1998.0)
[http://ipvsix.me/?p=106](http://ipvsix.me/?p=106)

---

