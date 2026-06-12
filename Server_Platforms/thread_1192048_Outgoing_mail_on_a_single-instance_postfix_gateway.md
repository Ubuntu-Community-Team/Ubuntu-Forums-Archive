---
title: "Outgoing mail on a single-instance postfix gateway?"
date: 2009-06-19
forum: Server Platforms
---

### Post by snori74 on 2009-06-19
Hi, I'm pretty familiar with postfix/spamassassin type setups for filtering incoming mail to one or more domains - including remote ones through /etc/postfix/transport

BUT, my problem is that I'm now getting requests to handle outgoing mail (to block silly users send junk, and to include AlterMIME "branding") on a gateway that I run which protects several domains.

There's a HOWTO on setting up a second full config, but in fact my domains seem to be able to happily relay their outward mail though the system I have - which I find puzzling.

MY QUESTIONS (finally!!) are:

1 - How come those in relay_domains can in turn relay *out* ? (they are not mentioned in mynetworks)

2 - Can I setup a different set of rules for "outgoing" within on instance

3 - Or should I go with something like: [http://advosys.ca/papers/email/58-postfix-instance.html](http://advosys.ca/papers/email/58-postfix-instance.html)

I'd really like to avoid a second instance, but my amavis/Maia and greylisting seems to be "firing" for outgoing mail (for the one tiny 5-user domain that I'm testing with) in ways that are not appropriate.

Looking for sage advice from Those That Have Been There :-)

Thanks in anticipation,

 - snori74

---

### Post by windependence on 2009-06-19
Are you asking how to set up Altermime? I may be able to help you on that one.

-Tim

---

