---
title: "smartd + Postfix: Configure heirloom-mailx to use Postfix server"
date: 2015-03-07
forum: Server Platforms
---

### Post by peridian on 2015-03-07
Hi,

We have a Postfix smtp relay or "smarthost" on the network, which can be reached via the internal-only DNS CNAME of "mail.domain"

Manually using the mail command from a different server can send emails to a destination address via the relay.

Having now setup smartmontools on several servers, I wanted to change the email address option in smartd.conf from "-m root" to "-m [EMAIL="address@external.domain"]address@external.domain[/EMAIL]"

How do I configure the local mailx package on the smartd server so that it knows how to find the Postfix server?  Do I configure smartd, heirloom-mailx, or do I change the local root account to forward its local mail?

Regards,
Rob.

---

