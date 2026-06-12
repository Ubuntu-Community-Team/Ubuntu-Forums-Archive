---
title: "SSH passwordless login, home folder permission problem"
date: 2010-07-09
forum: Server Platforms
---

### Post by tjw09003 on 2010-07-09
I got ssh passwordless login to work.

if /var/www permissions are set to 750 it works, but when trying to access the server from a browser it shows permission denied.

when I set /var/www to 777, users can access the files through a browser but then ssh passwordless login doesn't work.

anyway around this, so both will work?

---

### Post by tjw09003 on 2010-07-09
Nevermind, set it to 755 and it all works :D

---

