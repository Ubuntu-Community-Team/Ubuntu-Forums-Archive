---
title: "Problems sending eMail since Ubuntu software update"
date: 2009-08-06
forum: Server Platforms
---

### Post by rotorcraig on 2009-08-06
My Ubuntu Hardy mail server uses SMTP (inc AUTH) to send outbound emails via my hosting provider's mail server as a smarthost.

It has worked fine for many months, but stopped working late last week following an APT-GET UPGRADE that downloaded a large number of patches and updates.

I am working on the assumption that it is my Ubuntu Hardy mail server that is at fault, as if I circumvent it and point Thunderbird (or even Telnet) straight at my hosting provider's mail server I can successfully send eMails.  Also because it started failing immediately after this large APT-GET UPGRADE.

The failure text for every eMail that I now try to send is:

[INDENT]"550 Requested action was not taken because this server doesn't handle mail for that user (in reply to RCPT TO command)."[/INDENT]

I will spend time this evening looking at exactly what came down in that upgrade and am hoping that I will find a configuration file or similar that has been overwritten and can be manually corrected.

In the meantime, I just wanted to check whether anyone else experienced and already fixed this problem over the last week or so?

Thanks in advance,

Craig

---

### Post by HermanAB on 2009-08-06
Hmm, just a little tip that you probably don't want to hear:
;)

Auto-updates are usually fine for simple 'out of the box' desktop systems, but when you are doing something special, like running a mail server, then auto-updates should be disabled. You should evaluate the updates on a non-essential system and backup your system before doing an update.  I also usually keep a tar ball of /etc stored in /root for quick reference after a configuration mishap.

---

### Post by rotorcraig on 2009-08-06
Hmm... can't argue with that and shall certainly rethink update strategy as a result of this experience!!!

Thanks

Craig

---

### Post by rotorcraig on 2009-08-07
Traced the problem to a configuration file 

[INDENT]/etc/postfix/main.cf[/INDENT]

I have a line in there 

[INDENT]mailbox_command = procmail -a "$EXTENSION"[/INDENT]

Which had vanished, and as a result Spam was being marked but not moved to my Junk folder.  As soon as I reinstated this line and restarted postfix with

[INDENT]sudo /etc/init.d/postfix restart[/INDENT]

the Spam started being redirected to the Junk folder again, but I was also able to send eMails via my server again.

Dont understand the connection between the two issues, but pleased that things seem to be back to normal!

Craig

---

