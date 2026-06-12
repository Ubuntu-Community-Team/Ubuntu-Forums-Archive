---
title: "Road Runner and outbound SMTP: any hope?"
date: 2005-12-10
forum: Server Platforms
---

### Post by abstractgray on 2005-12-10
I'm trying to host a Wordpress installation on my Ubuntu box, and Wordpress likes to send emails to me whenever someone leaves a comment or uses the included anonymous email form.  These emails just die in the Postfix queue since my ISP, Road Runner, blocks outbound port 25.

Is there anything I can do about this?  Road Runner has an SMTP relay server but I think it requires the From address to be a Road Runner email account.  I am very bad at Postfix and have no idea how to set this up to make it work.  Has any Road Runner customer had any luck with remote mail delivery?

---

### Post by J.C. Denton on 2005-12-11
[QUOTE=abstractgray]Is there anything I can do about this?  Road Runner has an SMTP relay server but I think it requires the From address to be a Road Runner email account.[/QUOTE]
Last time I used RR, they didn't require an @rr address.  Try adding this to your Postfix main.cf:
```
relayhost = smtp-server.YOURAREA.rr.com
```
...replacing YOURAREA with your Road Runner service area.

---

