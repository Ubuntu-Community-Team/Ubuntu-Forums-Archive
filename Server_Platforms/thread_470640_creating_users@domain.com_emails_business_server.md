---
title: "creating users@domain.com emails business server"
date: 2007-06-11
forum: Server Platforms
---

### Post by damirk on 2007-06-11
Hi all,

As the heading might be a little bit vague here is a list of what I would like to do and what I know. As I have been using Linux for a couple of months now I wouldn't call my self a newbie as such but I still have lots to learn so I apologise if I don't quite understand something or don't explain it well.

I would like:
I would like to create my own email address, that is I would like to have [email]damirk@myowndomainname.com[/email] and not just for me but my whole family. I would like to receive emails and send them via kontact and have my whole family doing the same. 

I have done:
Currently running ubuntu-server LAMP 6.06 LTS. Other pc's; laptop running kubuntu and family pc running windows xp (havn't been able to convert my dad old programmer to Linux just yet) all of which are behind a NETGEAR router, firewall. I have a dyndns domain name setup.

A How-To would be great in regards to what I would like to do. Thanks in advance for all your help, really appreciated.

---

### Post by Wardazo on 2007-06-12
Hi

I don't mean to be defeatist here but the easiest way to do this is to use a service like google apps (free). They will supply you with [email]you@yourdomain.com[/email], [email]you1@yourdomain.com[/email]... I'm assuming you already have a domain name.

The benefits of google apps are virtually no spam and your emails are virtually never classified as spam.

If you decide to run your own emails service for your family you will constantly be haunted by these two problems of which them most frustrating is certainly the second one.

You can then get and send your email via the web interface or Kontact.

Ward

---

### Post by obimeister on 2007-06-12
Not sure what you mean, but you need postix for mail traffic and ie courier for IMAP. Then you need to forward port 25 from firewall to your server.

---

### Post by Mr. C. on 2007-06-13
You have a dynamic IP address - forget acting as a mail server.  Most sites will reject email from a dynamic address.

If you really want to run a mail server, get yourself a static IP, and start learning the basics.

Otherwise, just get a domain name from one of the many registrars, and setup mail forwarding records to your favorite mail providers.

MrC

---

