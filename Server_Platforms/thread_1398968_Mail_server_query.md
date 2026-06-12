---
title: "Mail server query"
date: 2010-02-05
forum: Server Platforms
---

### Post by Rich78 on 2010-02-05
Just setting up my own mail server and I can't get mail to the server from my DNS host.  The MX records are pointing to this server, however I get "Destination address required".

Do I need to install DNS on my mail server machine as well?

---

### Post by noway2 on 2010-02-05
My understanding is that yes, mail servers rely on having DNS lookup capability.  Depending on which mail program you are using there may be ways around the requirement.  Assuming you are using Postfix, here is a link to some information that may help.  Search for the term DNS.  [http://www.postfix.org/faq.html](http://www.postfix.org/faq.html)

---

### Post by Rich78 on 2010-02-05
Thanks, I've installed Bind9 and configured it all and bingo it works :D.

It makes sense it needs DNS but I just hoped to do without it, just as I didn't really want to run a mail server on my webserver but it's the only way I can forward mail.

Next problem is, can I configure this mail server to accept mail from multiple domains and forward the mail on?


eg.  

Send an email to
        [email]info@mydomain1.com[/email]                  email forwards to [email]me@googlemail.com[/email]
        [email]info@mydomain2.com[/email]                  email forwards to [email]me2@googlemail.com[/email]

?

---

