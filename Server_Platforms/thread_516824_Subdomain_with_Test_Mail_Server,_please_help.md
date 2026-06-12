---
title: "Subdomain with Test Mail Server, please help"
date: 2007-08-03
forum: Server Platforms
---

### Post by quietas on 2007-08-03
Howdy folk, I've been using Ubuntu for quite sometime as the desktop on my laptop, and more recently a home file/print server. Now I want to dive in and do far more.

Here's the situation: Multi-server LAN behind a firewall.
[LIST]
[*]Debian Pirmary DNS server (3.1)
[*]Win2k3 secondary DNS and Primary Domain Controller (windows logins)
[*]Debian mail server (4.0), Couier IMAP w/exim and mailscanner
[*]Several other MS 2kX servers
[*]Several other Debian servers
[/LIST]

Basically as you can see it's a mish-mash of Debian and Win2ksomething. The Debian DNS server and mail server are what I am concerned with for this post, but I thought I'd fill the blanks in case something is relavent.

Now to my problem: I need to set up a second mail server, fully functional on it's own subdomain. I would prefer to use Ubuntu 6.06 since it is LTS as well as fully supported by Zimbra ([website link]("http://www.zimbra.com")).

I can put the mail server on an IP outside of the network, or behind our firewall. What would I need to change on the Debian DNS server and new Ubuntu mail server, so that it will be fully recognized via MX records and DNS.

Any recommendations would be greatly appreciated.

---

### Post by koenn on 2007-08-04
I suppose you'd create a zone file for the sub domain, and have an MX record there for the subdomain mail server

and in the zone file of the parent domain, put an NS record for the sub domain, so that queries are resolved from the sbudomain zone file. 

Never done this, but it would be my first guess.

I don't think you want your servers out in the open, so I'd say you put it behind the firewall, but ideally, you'd have a DMZ for your publically accessible servers.

---

