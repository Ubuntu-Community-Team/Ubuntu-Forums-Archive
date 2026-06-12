---
title: "Help about webserver"
date: 2014-10-24
forum: Security
---

### Post by davidpotter2 on 2014-10-24
Hi ,
i have a hosted Ubuntu server which contain some of our sites. One of them have been hacked... inside the site directory are created automatically a bunch of directories with links to some other sites. If i delete them, they are created back.. how/what i can do?
Directory's are created with an user/group id that is not listed in /etc/pasw.


Ubuntu 9.04
Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g Server at xxx Port 80


Any help appreciated!

---

### Post by matt_symes on 2014-10-24
Hi

> Ubuntu 9.04
Apache/2.2.11 ....

Seriously or is this a typo ?

Kind regards

---

### Post by Iowan on 2014-10-24
Now, would someone like to offer some helpful advice - even if it's "upgrade and use your backup"?

---

### Post by CharlesA on 2014-10-24
> **Iowan said:**
> Now, would someone like to offer some helpful advice - even if it's "upgrade and use your backup"?

I would definitely agree with the whole "reinstall with a supported version and restore data from backups"

9.04 went End of Life on October 23, 2010, so it's been running for over 4 years with no security updates.

If you want to run a server OS, you can run either 12.04 or 14.04 (any LTS version) as they are supported for 5 years from release.

---

