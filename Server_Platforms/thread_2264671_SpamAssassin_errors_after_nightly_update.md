---
title: "SpamAssassin errors after nightly update"
date: 2015-02-09
forum: Server Platforms
---

### Post by DigiAngel on 2015-02-09
Topic says it....seeing the below now on startup and every email that comes in:
```
Feb  9 05:38:45 gateway spamd[23236]: rules: failed to run T_SPF_PERMERROR test, skipping:
Feb  9 05:38:45 gateway spamd[23236]:  (Can't locate object method "check_for_spf_permerror" via package "Mail: [...]:SpamAssassin::PerMsgStatus" at (eval 1192) line 357.
Feb  9 05:38:45 gateway spamd[23236]: )
Feb  9 05:38:45 gateway spamd[23236]: rules: failed to run T_SPF_HELO_PERMERROR test, skipping:
Feb  9 05:38:45 gateway spamd[23236]:  (Can't locate object method "check_for_spf_helo_permerror" via package "Mail: [...]:SpamAssassin::PerMsgStatus" at (eval 1192) line 560.
Feb  9 05:38:45 gateway spamd[23236]: )
Feb  9 05:38:45 gateway spamd[23236]: rules: failed to run T_SPF_HELO_TEMPERROR test, skipping:
Feb  9 05:38:45 gateway spamd[23236]:  (Can't locate object method "check_for_spf_helo_temperror" via package "Mail: [...]:SpamAssassin::PerMsgStatus" at (eval 1192) line 1049.
Feb  9 05:38:45 gateway spamd[23236]: )
Feb  9 05:38:45 gateway spamd[23236]: rules: failed to run T_SPF_TEMPERROR test, skipping:
Feb  9 05:38:45 gateway spamd[23236]:  (Can't locate object method "check_for_spf_temperror" via package "Mail: [...]:SpamAssassin::PerMsgStatus" at (eval 1192) line 1694.
Feb  9 05:38:45 gateway spamd[23236]: )

```

Anyone else seeing this?

---

### Post by DigiAngel on 2015-02-09
Confirming that the cron restart was at 01:11, and the error started then:

```
Feb  9 01:11:27 gateway spamd.pid: spamd: restarting using '/usr/sbin/spamd --create-prefs --max-children 5 --helper-home-dir -d --pidfile=/var/run/spamd.pid'
Feb  9 01:11:28 gateway spamd[1740]: logger: removing stderr method
Feb  9 01:11:29 gateway spamd[17485]: zoom: able to use 355/355 'body_0' compiled rules (100%)
Feb  9 01:11:30 gateway spamd[17485]: rules: failed to run T_SPF_PERMERROR test, skipping:

```

---

### Post by pv-vigierguitars on 2015-02-09
rules: failed to run T_SPF_HELO_PERMERROR test, skipping:
      (Can't locate object method "check_for_spf_helo_permerror" via package "Mail::SpamAssassin::PerMsgStatus" at (eval 1170) line 19.
)
rules: failed to run T_SPF_TEMPERROR test, skipping:
      (Can't locate object method "check_for_spf_temperror" via package "Mail::SpamAssassin::PerMsgStatus" at (eval 1170) line 614.
)
rules: failed to run T_SPF_PERMERROR test, skipping:
      (Can't locate object method "check_for_spf_permerror" via package "Mail::SpamAssassin::PerMsgStatus" at (eval 1170) line 784.
)
rules: failed to run T_SPF_HELO_TEMPERROR test, skipping:
      (Can't locate object method "check_for_spf_helo_temperror" via package "Mail::SpamAssassin::PerMsgStatus" at (eval 1170) line 1129.

---

### Post by CharlesA on 2015-02-09
Same error for me and it looks like a bad update was pushed out.
[http://unix.stackexchange.com/questions/183763/spamassassin-object-method-location-problems-after-restart](http://unix.stackexchange.com/questions/183763/spamassassin-object-method-location-problems-after-restart)

---

### Post by DigiAngel on 2015-02-09
And there it is...thanks Charles.

---

