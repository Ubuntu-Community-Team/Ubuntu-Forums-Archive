---
title: "IMAP and SMTP Server (vDomain support)"
date: 2010-11-23
forum: Server Platforms
---

### Post by RaymondBeaudoin on 2010-11-23
Hi All,

I'm looking to create a solution that uses an IMAP server with virtual domain support, as I host the .net/.org/.com versions of my domain. I'd prefer not to create linux users, but rather have them be stored in MySQL (as I would like to use the same e-mail across all domains), but I'm open to any suggestions. I've looked a bit into Dovecot and Courier, but didn't quite see anything that seemed to match. Maybe I've missed something? Of course, I'd also need to pair that with an SMTP service if you have suggestions.

Thank you and happy holidays! :popcorn:

-Raymond

Update: I found an old article on Dovecot with MySQL support: [http://www.webmonkey.com/2010/02/set_up_a_debian_or_ubuntu_machine_as_a_maildrop/](http://www.webmonkey.com/2010/02/set_up_a_debian_or_ubuntu_machine_as_a_maildrop/)

I'll try that out, but if anyone else has suggestions I'd much appreciate it. Thank you!

---

### Post by HermanAB on 2010-11-24
Citadel of course.  It takes about 20 minutes to set up using the Easy Install script and it does everything.

---

