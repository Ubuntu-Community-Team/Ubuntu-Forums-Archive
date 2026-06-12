---
title: "exim4 sendmail path in PHP.ini?"
date: 2007-09-24
forum: Server Platforms
---

### Post by UbuNewbie123 on 2007-09-24
Can exim4 work without sendmail installed?

My php.ini file has the following settings:

[PHP]
; For Win32 only.
;sendmail_from = me@localhost.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i
[/PHP]

If I uninstalled sendmail and only have exim4 installed, what do I put for my sendmail_path?

---

### Post by dantrevino on 2007-10-04
if you install only exim4, you should get a symlink from /usr/sbin/sendmail to /usr/sbin/exim4.  If you dont have it, you can create the symlink yourself.

ln -s /usr/sbin/sendmail /usr/sbin/exim4

Then no changes to your php.ini should be required.

dan

---

### Post by lyncas on 2008-06-04
I just installed exim4 and the symbolic link already exists

```

ln -s /usr/sbin/sendmail /usr/sbin/exim
ln: creating symbolic link `/usr/sbin/exim' to `/usr/sbin/sendmail': File exists

```

So, if you install exim after sendmail, your link should be created and you should not have to change php.ini

---

