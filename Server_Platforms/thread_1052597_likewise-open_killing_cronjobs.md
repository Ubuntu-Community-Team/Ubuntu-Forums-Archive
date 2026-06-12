---
title: "likewise-open killing cronjobs?"
date: 2009-01-27
forum: Server Platforms
---

### Post by tr333 on 2009-01-27
Before installing likewise-open and joining a domain, there appeared to be no problems with the system running its cronjobs.
auth.log:
```
Jan 27 16:15:01 ubuntu CRON[21823]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Jan 27 16:17:01 ubuntu CRON[21928]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 16:17:01 ubuntu CRON[21928]: pam_unix(cron:session): session closed for user root
Jan 27 16:18:12 ubuntu CRON[21823]: pam_unix(cron:session): session closed for user www-data
Jan 27 16:20:01 ubuntu CRON[22097]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Jan 27 16:23:13 ubuntu CRON[22097]: pam_unix(cron:session): session closed for user www-data
Jan 27 16:25:01 ubuntu CRON[22380]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Jan 27 16:28:12 ubuntu CRON[22380]: pam_unix(cron:session): session closed for user www-data

```

After joining the server to a domain with likewise-open, it appears that the cronjobs are failing.
auth.log:
```
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): failed to get GP info
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): request failed
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): User 'root' is not known.
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): Returning 7 for user "root"
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): request failed
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): User 'root' is not known.
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:account): Returning 7 for user "root"
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:session): PAM config: global:krb5_ccache_type 'FILE'
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:session): request failed
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:session): User 'root' is not known.
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:session): could not create home directory
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:setcred): request failed
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:setcred): User 'root' is not known.
Jan 27 16:39:01 ubuntu CRON[23549]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'

```
Is this a problem with likewise-open, or something i failed to configure properly?

---

### Post by discodan on 2009-02-08
This is happening on my PC also.  It's an Ubuntu 8.04 desktop.  I just started researching the issue.  I'll keep you posted if I figure it out.

---

### Post by discodan on 2009-02-10
Found this... not much help though...

[https://bugs.launchpad.net/ubuntu/+source/bzr/+bug/285623/comments/9](https://bugs.launchpad.net/ubuntu/+source/bzr/+bug/285623/comments/9)

---

### Post by jeremyrnelson on 2009-11-03
Do some Googling for likewise cron expired passwords - it only seems to take place during the countdown to password expiration.

---

