---
title: "exim4 + mailman problem"
date: 2008-10-10
forum: Server Platforms
---

### Post by artesvida on 2008-10-10
Hello,

I've already followed the instructions here:
[https://help.ubuntu.com/8.04/serverguide/C/mailman.html](https://help.ubuntu.com/8.04/serverguide/C/mailman.html)

Which gets me pretty far, but it seems that mailman doesn't want to send any mail.  The logs say "Low level SMTP error: (111, 'Connection refused')."  After doing a bit of research, it appears that mailman is trying to send outgoing messages via SMTP to localhost.  And, if I try to telnet localhost 25, I get connection refused.  So, obviously, I need to get my mail handler to allow this type of connection.

I'm using exim4 (please don't ask why) and I can't see where I tell the server to accept incoming SMTP connections from 127.0.0.1 or localhost.  If I use exim directly to send a message, it works fine.  I can open up an SMTP connection to this host from *another* host, but not the localhost.  Any thoughts?

Thank you!

---

