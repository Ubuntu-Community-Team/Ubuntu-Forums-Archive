---
title: "Sansecurity clamd not running issues"
date: 2015-01-07
forum: Server Platforms
---

### Post by Heeter on 2015-01-07
Hi all,

I have been starting to have issues with a existing sanesecurity install with postfix/spamassassin/clamav/14.04LTS.

These errors started last week. When I run test script:

```

/usr/sbin/clamav-unofficial-sigs.sh

```

I get an error that clamd is not running. I do service restarts for "clamav-freshclam" & "clamav-deamon" and they restart [OK]

What can I do to fix this?

Also, where do I find the actual config file for clamav-unofficial-sigs?

Regards

Heeter

---

### Post by bashiergui on 2015-01-10
> Also, where do I find the actual config file for clamav-unofficial-sigs?
Should be /etc/clamav-unofficial-sigs.conf

---

