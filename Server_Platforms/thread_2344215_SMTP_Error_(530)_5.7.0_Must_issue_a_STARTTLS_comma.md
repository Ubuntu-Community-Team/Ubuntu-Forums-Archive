---
title: "SMTP Error (530) 5.7.0 Must issue a STARTTLS command first"
date: 2016-11-23
forum: Server Platforms
---

### Post by fabioescabrita on 2016-11-23
I am trying to use port 587 in roundcubemail running in the same machine as my mail server, and i am always receiving this error:
> 
    SMTP Error (530): Failed to set sender "X" (5.7.0 Must issue a STARTTLS command first).

I have already changed,

    > smtpd_tls_security_level=encrypt

to

    > smtpd_tls_security_level=may

and nothing happen, and i have already 'submission' uncommented. Those was the solutions that i have found to solve this problem, but till now no result here.

Main.cf:
[http://pastebin.com/aEtC0AJt](http://pastebin.com/aEtC0AJt)

Master.cf:
[http://pastebin.com/023uu2T8](http://pastebin.com/023uu2T8)

And i dont know if it is related but i cannot login through IMAP port 993.

I am only able to use ports 25 and 143 without SSL.

I cannot send mails internally, all mails pass through my ISP mail server, where my email domain is.

Anyone?

---

