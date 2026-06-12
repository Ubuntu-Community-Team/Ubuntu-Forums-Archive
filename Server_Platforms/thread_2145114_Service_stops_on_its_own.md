---
title: "Service stops on its own"
date: 2013-05-14
forum: Server Platforms
---

### Post by bullet333 on 2013-05-14
Ubuntu 12.10
Squid3 3.1
Dansguardian 2.10.1.1
Postfix 2.9.6
Webmin 1.620

My Squid3 server uses Dansguardian as a web filter.  I've noticed that several times (randomly) the service would stop on its own.  I installed Monit to restart the service automatically on failure but that's just a workaround until I resolve this issue for good.

I browsed the syslog file and noticed some strange things going on when Dansguardian restarted and not exactly sure how to diagnose the problem.  Maybe one of you could please help me out?

```

May 14 11:15:08 Squid dansguardian[1858]: Content scanner plugin init returned error value: -1
May 14 11:15:11 Squid dansguardian[1858]: Content scanner plugin init returned error value: -1
May 14 11:15:11 Squid dansguardian[1858]: Error loading CS plugins
May 14 11:15:11 Squid dansguardian[1858]: Error re-parsing the dansguardian.conf file or other DansGuardian configuration files
May 14 11:15:35 Squid dansguardian[3636]: Started sucessfully.
May 14 11:17:01 Squid CRON[3671]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

I've also attached my Dansguardian Configuration File (Dansguardian.conf) to this post after cleaning up the comments.  If you need anymore information don't hesitate to ask me.  Also forgive me as I'm still pretty new to the linux environment so go easy on me :)

Thanks!

---

