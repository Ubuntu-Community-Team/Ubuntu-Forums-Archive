---
title: "Mail server, A, MX, PTR, FPS"
date: 2011-03-11
forum: Server Platforms
---

### Post by Hioushi on 2011-03-11
Greetings,

I'd greatly appreciate your help here, I'm a bit overwhelmed with the amount of information I've been reading recently.

I've setup a postfix server (ubuntu 10.4) and everything is working, smtp and pop3 are ok, and I'm able to send and receive mail. However, gmail and hotmail are receiving mail from my server as spam.

As I understand it, I need to setup an A, MX and PTR record for my domain, and this is where I get lost, set this where? on the domain admin page?.

Same with the FPS record, I've generated my TXT line with the wizard at openspf.org, but where am I supposed to put it?.

The server has a dedicated IP address, my provider handles everything, including the domain, so I need to know if there's something they need to set on their end, or if I have to set it up on the server itself.

Thank you so much for any help you could provide.

---

### Post by rbishop on 2011-03-11
You will need to have whomever handles your DNS entries set those up for you. Once that is done, it may take up to 24hrs for all changes to be propagated around the world, you should be okay.  However depending on who your provider is your mail may continue to be marked as SPAM since most blacklists mark anything from consumer ISP's as SPAM.

---

### Post by Hioushi on 2011-03-11
Thank you for your quick reply.

My confusion lies in the fact that I requested this records to be setup with my server and the provider replied with a link to openspf.org telling me I have to setup it there.

I suppose they want me to send the output of the wizard? (I'll contact them again of course, I just wanted to have things clearer in my mind first).

The provider in question is iWeb.com, in case it's relevant at all.

So there's nothing I have to do in my end except to setup the mail server to use SPF correct?

If it is, I can put pressure on my providers regarding this issue.

---

### Post by rbishop on 2011-03-11
If you are not handling your own DNS, then no you don't have to do anything.

I am assuming that your hosting company has a way of submitting a request for your DNS changes, ie via email, web portal, etc.

Hope this helps.

---

### Post by Hioushi on 2011-03-11
It does, thank you for your help.

---

### Post by SeijiSensei on 2011-03-11
SPF records are added as a "TXT" record in the DNS for a given domain.  So your provider would need to add that for you if you don't have control over your own DNS.  (Personally I can't imagine not being able to maintain my own DNS records even on a hosted account, but there are a lot of ISPs out there.)

Time to do some tests, I think. If you have another Linux computer besides your server, try the following commands:

```

host -t ns yourdomain.com
host -t mx yourdomain.com
host -t txt yourdomain.com
host -t a hostname.yourdomain.com
host -t ptr your.server's.ip.address

```

All of these should resolve correctly.  The "txt" request may not return anything.  If you have SPF records, you'll see something like 

```

IN TXT "v=spf1 a=hostname.yourdomain.com ~all"

```

The most important thing is for the PTR record to match the A record for the machine sending mail.  So if you have an A record for "www.mydomain.com" that points to 10.10.10.10, you'd need a PTR record for 10.10.10.10.in-addr.arpa that points to [www.mydomain.com](www.mydomain.com).  Only your ISP can create a PTR record for your IP address.  The other records are contained in the DNS "zone file" for your domain, which it sounds like your provider maintains as well.

---

