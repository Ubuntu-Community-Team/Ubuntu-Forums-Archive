---
title: "What kind of mail program should I use for this?"
date: 2010-12-08
forum: Server Platforms
---

### Post by Underpants on 2010-12-08
I have 4 Windows boxes. Server 2008 R2 with IIS SMTP running on them. 

Their config is pretty simple. There are some basic ACLs in place for which servers and send mail, and also a set for who can relay to external domains.

all external domains are routed through a smarthost (third party hosted service)

we have 2 internal domains defined in the SMTP server so any mail addressed to those routes to our in house Exchange system. 


 - I'd like to do this with some linux boxes instead. Mostly as a learning process. I'd like something that has a reasonable amount of logging for the mail that's being sent through it. Windows is pretty bleak in this area. I can't decide which system to use, exim, postfix, sendmail, etc. 

does anyone have any thoughts on this?

---

### Post by HermanAB on 2010-12-09
Depends on how much time you have to waste.  Postfix will keep you busy for 2 weeks or so, the first time you try to set it up, while Citadel installs in about 20 minutes when using the Easy Install script.  Pick your own poison...

---

