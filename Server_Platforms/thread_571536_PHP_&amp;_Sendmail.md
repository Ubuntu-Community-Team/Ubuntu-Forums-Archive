---
title: "PHP &amp; Sendmail"
date: 2007-10-09
forum: Server Platforms
---

### Post by Zarathu on 2007-10-09
For some reason, whenever I call any mail()-related function through PHP, it just hangs.  "Waiting for /server/..."

```
sudo apt-get install sendmail
```

That was what I did, and in my php.ini file:

```
[mail function]
; For Win32 only.
;SMTP = localhost
;smtp_port = 25

; For Win32 only.
;sendmail_from = me@example.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail

; Force the addition of the specified parameters to be passed as extra parameters
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =

```

Any ideas?

```
root@jesus:/var/www# whereis sendmail
sendmail: /usr/sbin/sendmail /usr/lib/sendmail /usr/share/sendmail /usr/share/man/man8/sendmail.8.gz
root@jesus:/var/www#
```

---

