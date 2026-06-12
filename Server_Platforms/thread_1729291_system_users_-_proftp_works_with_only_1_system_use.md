---
title: "system users - proftp works with only 1 system user"
date: 2011-04-14
forum: Server Platforms
---

### Post by Niomi on 2011-04-14
I'm niomi and I'm the first account with sudo. I add an account, bob. niomi can get in reliably on active mode. (maybe relevant?: passive doesn't work) bob is jailed to his home directory, niomi is in ftp-special which gives her access to /. bob can't log in and his shell is set to bin/false. What could have gone wrong?

---

### Post by falko on 2011-04-15
Add /bin/false to /etc/shells, and it should work.

---

### Post by Niomi on 2011-04-15
Falko: thank you, but this did not fix my problem.

---

### Post by falko on 2011-04-16
Did you restart ProFTPd?

Can you post your proftpd.conf?

---

