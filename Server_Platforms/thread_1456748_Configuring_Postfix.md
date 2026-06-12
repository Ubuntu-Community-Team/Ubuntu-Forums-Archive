---
title: "Configuring Postfix"
date: 2010-04-17
forum: Server Platforms
---

### Post by Nascentes on 2010-04-17
Hey guys...

I am currently completely re-installing my web server for the second time and am using LAMP this time around.

At the end of the installation I selected LAMP, OpenSSH and Mail Server

I am in the config part of the Server installation for Postfix right now and I need some help...

Someone a few days ago told me that if I was going to have a mail server, I should use smtp so that is what I am doing. I just have no clue what to put in this blank...

> 
Please specify a domain, host, host:port, [address] or [address]:port. Use the form [destination] to turn off MX lookups.
Leave this blank for no relay host.

Do no specify more than one host.

The relayhost parameter specifies the default host to send mail to when no entry is matched in the optional transport(5) table. When no relay host is given, mail is routed directly to the destination.

SMTP relay host (blank for none):



My guess would be that I would just use my servers local IP address, but I"m not 100%...

Any help would be terrific. 

Thanks

---

### Post by lisati on 2010-04-22
"relayhost" is sometimes used if you want to use another server to send out mail on behalf of your server, e.g. if you want to go through your ISP's server for some reason.

It's probably safe to leave it blank.


edit: moved to "Server platforms"

---

### Post by dudumomo on 2010-04-22
Indeed.
But in some case, it is easier to use the relayhost of your ISP as for example Microsoft don't use a backlist but a whitelist. Then you have to declare your server to Microsoft. 
Etc...

---

