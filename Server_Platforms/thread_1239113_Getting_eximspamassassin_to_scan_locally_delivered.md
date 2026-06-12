---
title: "Getting exim/spamassassin to scan locally delivered emails, not emails relayed via it"
date: 2009-08-13
forum: Server Platforms
---

### Post by ayqazi on 2009-08-13
Hi,

So I've got this server I use to collect emails for my domain, but I also use it to relay emails via it.

I've got SpamAssassin enabled and scanning emails inbound to that server just fine - Thunderbird can see the headers SpamAssassin adds and it knows how to deal with them.

However, SpamAssassin still scans emails that get relayed through the server to other addresses, like Hotmail or GMail accounts.  How do I stop it doing that?

Basically, I uncommented the following section in exim4.conf.template:

```

acl_check_data:

...

  warn
    spam = Debian-exim:true
    message = X-Spam_score: $spam_score\n\
              X-Spam_score_int: $spam_score_int\n\
              X-Spam_bar: $spam_bar\n\
              X-Spam_report: $spam_report

```

---

