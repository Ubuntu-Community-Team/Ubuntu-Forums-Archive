---
title: "SMTP/Postfix server and client mail program"
date: 2008-07-16
forum: Server Platforms
---

### Post by john.hall on 2008-07-16
I set up a postfix server and put the MX record in the DNS server:
```

pluto.blah.blah.               IN      MX      10      serverA

```
I also have NIS set up.  /var/mail is shared (rw,root_squash,sync) via NFS and the client has it mounted.

I log onto the client with a user that is shared over NIS.  I try to send mail to another NIS user using the "mail" program.  But the message returns and says "Mailing to remote domains not supported."    I can, however, telnet into the machine on port 25 and send mail that way.

How can I get the mail program to understand how to send mail?

---

