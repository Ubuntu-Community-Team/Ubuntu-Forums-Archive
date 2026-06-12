---
title: "Postfix Address Rewriting"
date: 2009-06-09
forum: Server Platforms
---

### Post by PJDouglas on 2009-06-09
Hi,

I have Postfix configured as a relay server with no local mail delivery.

All mail sent to postfix is automatically delivered to a smarthost.

I want postfix to rewrite the sender/from address of all mail received before it is sent to the smarthost.

I have the following line in main.cf:-

sender_canonical_maps = hash:/etc/postfix/sender_canonical

and my sender_canonical file reads:-

@domain.com    @paul.com

I have ran postmap /etc/postfix/sender_canonical to commit the changes and postfix reload.

From my understanding that is all I need to do. All emails still have the originating address of domain.com and not paul.com.

Not sure what else I need to do.

Any help would be appreciated.


Kind Regards


Paul.

---

### Post by PJDouglas on 2009-06-12
Finally, got this working!

Postfix does not allow address rewriting by default on remote mail because it goes against mail standards. You need to add the following line to [main.cf]("http://main.cf/") to rewrite addresses on remote mail:-

remote_header_rewrite_domain = domain.invalid

---

