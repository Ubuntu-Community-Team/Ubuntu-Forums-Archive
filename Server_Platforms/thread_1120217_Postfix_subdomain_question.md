---
title: "Postfix subdomain question"
date: 2009-04-08
forum: Server Platforms
---

### Post by RainyCity on 2009-04-08
While I was working out a way to have my postfix servers receive mail sent to <allnames>@<allsubdomains>.domain.tld I noticed that virtual_mailbox_domains doesn't take ".domain.tld" notation for subdomains. The postfix documentation implies that this is supposed to work and I was wondering if this is something that is broken or if I'm just doing something wrong.

Here are some examples:
### Non-working configuration start ###
main.cf
  virtual_mailbox_domains = /etc/postfix/virtual-domains

virtual-domains
  example.com
  .example.com
### Non-working configuration end ###

### Working configuration start ###
main.cf:
  virtual_mailbox_domains = /etc/postfix/virtual-domains, regexp:/etc/postfix/virtual-domains-regexp

virtual-domains:
  example.com

virtual-domains-regexp:
  /.*\.?example\.com$/
### Working configuration end ###

According to [http://www.postfix.org/postconf.5.html#parent_domain_matches_subdomains]("http://www.postfix.org/postconf.5.html#parent_domain_matches_subdomains") the .example.com notation should work.

Also I'm not interested in listing virtual_mailbox_domains under parent_domain_matches_subdomains because I don't want to receive all messages from all subdomains of all my virtual domains, just a few of them.

Ubuntu server 8.0.4, Postfix version 2.5.1

Thanks

---

