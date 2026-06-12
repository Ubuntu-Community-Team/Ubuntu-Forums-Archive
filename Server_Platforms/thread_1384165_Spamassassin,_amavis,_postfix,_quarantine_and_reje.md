---
title: "Spamassassin, amavis, postfix, quarantine and reject"
date: 2010-01-18
forum: Server Platforms
---

### Post by LarsEriksson on 2010-01-18
I am using the above mentioned setup, and at the momen i only get the SPAM-tagged mails in the quarantine, without sending an error reply to the sender.

I would like to set it up so i get the mail in a quarantine folder _AND_ a reject reply(554?) to the sender of the mail.


Destiny settings in /etc/amavis/conf.d/20-debian_defaults
```
$final_virus_destiny      = D_DISCARD;  # (data not lost, see virus quarantine)
$final_banned_destiny     = D_BOUNCE;   # D_REJECT when front-end MTA
$final_spam_destiny       = D_PASS;
$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)
```

How should i set it up?

---

