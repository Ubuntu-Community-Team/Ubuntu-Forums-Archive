---
title: "dovecot-postfix package security question"
date: 2010-01-25
forum: Server Platforms
---

### Post by hanzgroove on 2010-01-25
Hi,

Today I installed the dovecot-postfix package on my server. Everything is working nicely but admittedly I don't know much about administering my own mail server. I just followed a tutorial I found online.

My question is, in my mail.log I'm seeing incoming connections like so:

mail dovecot: imap-login: Login: user=<user@domain.com>, **method=PLAIN**, rip=11.111.111.11, lip=111.111.111.111, **TLS**

The method=PLAIN part scares me a bit. But then I see the TLS at the end. So I'm not sure if thats a good thing or a bad thing and if I need to be worried about security.

I'd appreciate any help/guidance on this.

Thanks

---

### Post by Roger_Smith on 2010-01-25
Just means your user logged in with plaintext login but used TLS encryption on the connection to your server.

---

