---
title: "Ssl smtp with postfix"
date: 2009-10-16
forum: Server Platforms
---

### Post by tflags on 2009-10-16
Hello, trying to set up a SMTP (postfix) server and already installed DOVECOT (??) IMAP SSL with public cert & all. Works fine. SMTP via port 25 (non SSL) also works fine but SMTP SSL via port 465 is not answering. I don't think the server is listening on that port.
Any help? Thanks,

---

### Post by noway2 on 2009-10-16
Two things to try for starters.  One, use netstat to confirm whether or not anything is listening on this port.  Two, in the Dovecot configuration file you will need to add a section to tell it to listen on this port, just like you have for the regular port.  I don't have access to my server right now, otherwise I would show you a sample configuration.

---

