---
title: "securing a mailserver (exim4)"
date: 2008-04-13
forum: Security Discussions
---

### Post by tmilam on 2008-04-13
I want to set up exim4 for a single domain for the purpose of emailing form data, registration info, and log files automated via cron. With absolutely no experience setting up mailservers I'm concerned that a spammer will use my domain to send out massive amounts of junk mail due to some oversight of mine when setting exim4 up. 

Where should I begin, other than the ubuntu documentation for exim4 located at [https://help.ubuntu.com/7.10/server/C/exim4.html](https://help.ubuntu.com/7.10/server/C/exim4.html) to ensure that this doesn't happen? The last thing I want is to have my domain blacklisted for spamming people.

---

### Post by brian_p on 2008-04-13
> **tmilam said:**
> I want to set up exim4 for a single domain for the purpose of emailing form data, registration info, and log files automated via cron. With absolutely no experience setting up mailservers I'm concerned that a spammer will use my domain to send out massive amounts of junk mail due to some oversight of mine when setting exim4 up. 

Where should I begin, other than the ubuntu documentation for exim4 located at [https://help.ubuntu.com/7.10/server/C/exim4.html](https://help.ubuntu.com/7.10/server/C/exim4.html) to ensure that this doesn't happen? The last thing I want is to have my domain blacklisted for spamming people.

Begin at the link you quote. The second command gives you all you want.

---

### Post by HermanAB on 2008-04-14
Some mail servers simply won't do relaying for anonymous clients, avoiding the whole problem, for example Citadel.  Citadel comes with pretty much all mail protocols ever invented and it is easy to set up a secure system with SSH encryption to all mail and web clients.

Cheers,

H.

---

