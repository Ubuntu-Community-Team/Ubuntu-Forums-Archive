---
title: "Discussion: most desirable mech_list for /etc/postfix/sasl/smtpd.conf?"
date: 2010-06-24
forum: Security
---

### Post by Fatman_UK on 2010-06-24
Hi all.

No urgency to this one, just looking for some discussion. :) 

It occurred to me it might be handy to set up a SMTP relay for my own personal use. I've followed the usual guides to install Postfix and Cyrus SASL on my Lucid server. I've screwed down the "smtpd_tls_security_level = encrypt" and "smtpd_tls_auth_only = yes" settings and changed listening ports, so it's not an open relay. It seems to work well enough.

Now I'm wondering what to do with my mech_list setting (see title). I want to keep it short, restricted to the best authentication protocols, but also support the maximum number of clients (Thunderbird, Outlook, Eudora etc).

Currently my mech_list looks like this but I think we can do better:

```
mech_list: login digest-md5 gssapi
```

I have login for Outlook and I think Thunderbird is negotiating gssapi but I'm not sure.

---

