---
title: "Samba upgrade on Ubuntu 8.04 LTS"
date: 2010-03-31
forum: Server Platforms
---

### Post by snpz on 2010-03-31
Hi there!
Situation:
Domain controller - Ubuntu 8.04 LTS, Samba 3.0.28a, LDAP
File Server - Ubuntu 8.04 LTS, Samba 3.0.28a. A lot of user shares.
Workstations - WinXP, on startup %u.bat files map network drives from File server.
Right now we have a couple of new PC's with Win7 and OpenSuSE 11.2. None of them can join
Tryed to upgrade samba servers to 3.4.5 using source code. On domain controller everything works, but on file server i can not access any of shares after upgrade.
Can anyone explain where is that difference between samba 3.0.28a and samba 3.4.5?!
Had to downgrade because of this problem.

---

### Post by spynappels on 2010-03-31
What sort of problems are you having accessing the Samba shares from the Win7 machines? I had problems to begin with but got it working on stock 8.04LTS boxes.

---

### Post by snpz on 2010-03-31
I can add Win7 workstation to domain, but only using Win7 registry fixes, but i cant login after workstation is added.
With OpenSuSE 11.2 i can't even join domain using samba 3.0.28a.

---

### Post by spynappels on 2010-03-31
What worked for me was to escape the username with a \ (or was it /?)so that the login creds were:

\user       (Samba User)
password    (Samba Password)

and the Domain was then not specified. without this it tries to specify a domain as well as a user and this will not work.

Might help you.

---

### Post by snpz on 2010-03-31
Users are stored in LDAP ;)
Everything is authorized against LDAP - zimbra e-mail and other web services.
But thanks for advice :)

---

