---
title: "Removing cron spam from auth.log"
date: 2020-05-02
forum: Server Platforms
---

### Post by vellofrell on 2020-05-02
I keep receiving these messages in /var/log/auth.log every five minutes.

```
May  2 15:25:01 localhost CRON[19178]: pam_unix(cron:session): session opened for user tuptime by (uid=0)May  2 15:25:01 localhost CRON[19178]: pam_unix(cron:session): session closed for user tuptime

```
I added this line to /etc/pam.d/cron:

```
session [success=1 default=ignore] pam_succeed_if.so quiet uid = 103 ruser = tuptime

```

Still seeing the message, but admittedly I'm well out of my wheelhouse on this problem and had to Google around to even come to the above attempt at a fix. Any hints as to what I should do next?

---

### Post by vellofrell on 2020-05-09
Still hoping there is some advice to be had out there regarding these persistent logs I don't want showing in /var/log/auth.log. Tips for making these go away? They didn't used to appear until I decided to attempt uninstalling *tuptime*. 

```
May  9 14:20:01 localhost CRON[26375]: pam_unix(cron:session): session opened for user tuptime by (uid=0)
May  9 14:20:01 localhost CRON[26375]: pam_unix(cron:session): session closed for user tuptime
May  9 14:25:01 localhost CRON[28696]: pam_unix(cron:session): session opened for user tuptime by (uid=0)
May  9 14:25:01 localhost CRON[28696]: pam_unix(cron:session): session closed for user tuptime



```

---

