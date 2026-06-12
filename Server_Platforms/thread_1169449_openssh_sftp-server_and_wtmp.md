---
title: "openssh sftp-server and wtmp"
date: 2009-05-25
forum: Server Platforms
---

### Post by masmad on 2009-05-25
Is it proper behaviour that ssh logins get logged in /var/log/wtmp and logins that use sftp-server do not?

If that's the case, are the latter logged anywhere? 

I've tried this on Dapper and Jaunty, and both update /var/log/wtmp when I login using ssh but when I use a sftp-client, the logins do not show up using last or lastlog.

---

### Post by Alekz_ on 2009-05-25
Try /var/log/auth.log

It supposed to be there... :)

---

### Post by masmad on 2009-05-25
Well yes, but getting a convenient view of users last logins would require quite a bit of grepping considering that auth.log rotates every now and then...

Finding out whether a user has ever logged in might also prove difficult considering that the oldest logs are long gone by now :D.

---

