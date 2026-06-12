---
title: "Changing postfix port"
date: 2010-03-18
forum: Server Platforms
---

### Post by dre361224 on 2010-03-18
Alright, now here's the problem... I set up postfix and dovecot and they're both working fine, kind of. I receive and can send internal emails without a problem, but I can only receive external emails. Now I'm pretty sure that is because Rogers is blocking outgoing port 25 from what I've seen in my research around the internet.

What I'm trying to accomplish is send external emails using PHP. Is it possible to change to port used to send emails? I don't really care about receiving them at this point. I've read about putting your ISPs SMTP address as a relay host but I'd rather not if I didn't have too.

Any help would be greatly appreciated! I've been going at this email server for many months now without success and it's starting to really get on my nerves...

---

### Post by dre361224 on 2010-03-19
Any pointers would be really appreciated? :(

---

### Post by Xipher on 2010-03-19
Your only option is to relay through another host. Port 25 is the port used to connect for SMTP delivery and there is no way around that, but if you had a host outside your network which accepts mail to relay on an alternate port you could use it as a smart host. Just make sure you're being safe and secure about this and either use authentication or restrict connection to only your IP. Using SSL/TLS would also be a good idea.

---

### Post by dre361224 on 2010-03-19
Alright thank you very much for your replay. I guess I'll have to give Rogers a call on Monday :/

Thank you!

---

### Post by jrssystemsnet on 2010-03-19
> **Xipher said:**
> Your only option is to relay through another host. Port 25 is the port used to connect for SMTP delivery and there is no way around that, but if you had a host outside your network which accepts mail to relay on an alternate port you could use it as a smart host. Just make sure you're being safe and secure about this and either use authentication or restrict connection to only your IP. Using SSL/TLS would also be a good idea.
This.

In general what you're looking for is a mailserver which will accept mail from you on the SUBMISSION port (typically 587), and you will also need to do AUTH to that server to authenticate as a valid user with a password on that server; then the server will be willing to relay mail out from your server.  This is called a "smarthost" in Postfix-ese; you can find a how-to on setting up relaying through a smarthost with AUTH SMTP here: [http://ubuntuwiki.net/index.php/Postfix,_smarthost_with_SMTP_AUTH](http://ubuntuwiki.net/index.php/Postfix,_smarthost_with_SMTP_AUTH)

One word of warning: while you can do this through, say, a Gmail account, it appears that Gmail mangles the headers so that any mail relayed through a Gmail server will be changed so as to have the From: and the Reply-To: set to the Gmail account used for the relaying, regardless of what they originally were... so you probably DON'T want to actually use a Gmail account for this. :)

---

