---
title: "Need help with specialized postfix setup"
date: 2009-11-14
forum: Server Platforms
---

### Post by toammann on 2009-11-14
Hi everyone,

I'm looking for some help with a special postfix setup. This is what the end should look like:

foo.com is a publicly accessible web/mail server with some "normal" smtp/pop3 accounts set up. (that's already working). Now I want to enable forwarding of certain email addresses to machines in the connected vpn. e.x.: [EMAIL="joe@foo.com"]joe@foo.com[/EMAIL] => [EMAIL="joesmith@workstation.foo.com"]joesmith@workstation.foo.com[/EMAIL], ... I managed to setup the private names (workstation....) using /etc/hosts and I installed postfix (internet + smarthost) on the vpn machines. I already setup relay_host and the appropriate listening interfaces correctly.

unfortunately, i haven't got a clue on how to realize the forwarding from server to vpn. I really want to use smtp for that, and i don't want to use mysql, webinterface or others to realize it. I tried adding something like:

[EMAIL="joe@foo.com"]joe@foo.com[/EMAIL] smtp:[workstation.foo.com] to /etc/postfix/transport with transport_map = hash:/etc/postfix/transport in main.cf, but i only get errors telling me, that [EMAIL="joe@foo.com"]joe@foo.com[/EMAIL] is not in the list of local recipients.

Please let me know how I can solve this, or what feature/config of postfix i'm looking for. Thanks

---

### Post by toammann on 2009-11-14
...looks like postfix is not that a common subject on the forum. Where are the gurus?

---

### Post by falconindy on 2009-11-14
27 minutes elapse and you're feeling abandoned? Should try the postfix mailing lists if you wanted to find a higher concentration of people who know postfix well.

What you need is likely to establish virtual domains on the VPN hosts.

[http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html)

---

### Post by toammann on 2009-11-14
Thanks for the hint, I'll ask there too. I'll probably have to read through the whole virtual stuff docs to sort out which features i don't need then.

about feeling abandoned: it's just that i've replied 5 newbies in the meantime. there is clearly an uneven distribution of knowhow, but i guess that's because of ubuntu's user friendliness. :-)

---

