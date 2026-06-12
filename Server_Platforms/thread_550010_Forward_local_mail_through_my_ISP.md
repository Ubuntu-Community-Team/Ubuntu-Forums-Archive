---
title: "Forward local mail through my ISP"
date: 2007-09-13
forum: Server Platforms
---

### Post by TruckStuff on 2007-09-13
Let me start by saying that I am a qmail admin and this is the first time I've used exim.

I've installed Ubuntu server on a box that is going to do other things, but I need for local mail (e.g. logwatch, etc) to be delivered through my ISP to an external server.  The docs I read said this was as easy as modifying /etc/aliases and dropping a .forward in my home directory.  So I modified /etc/aliases to point mail for root to my local account, then added ~/.forward: ```
deliver me@remotedomain.com
``` This worked well so long as the server delivered the mail.  However I found that many servers would reject this mail since it doesn't come from my mail server.

So then I configured exim as a "Satellite System" and set it to relay through my ISP's mail server.  Now the mail no longer goes to [email]me@remotedomain.com[/email], but instead gets delivered to [email]my-local-account@my.local.fqdn.com[/email] through my ISP.  wtf?? For the life of me I can't find any simple docs that tell me how to configure this correctly.  Any help is appreciated.

---

### Post by psusi on 2007-09-13
If you are familliar with qmail maybe you should use that instead of exim?  I use postfix myself, but instead of forwarding mail out to my normal mailbox, I run dovecot for an imap server and access my mail that way, with a cron job to pull from my normal pop3 server with fetchmail.

---

