---
title: "htaccess htpasswd problem"
date: 2006-12-07
forum: Server Platforms
---

### Post by uberlinux on 2006-12-07
Sorry, I fixed the problem, it was a coding error in htaccess!


*So I don't think that godaddy uses ubuntu servers to host my site but I don't know where else to turn, cause they don't have a forum and I've already tried all the stuff on their support site.*

I've don't exactly as godaddy instructed me to do in using htaccess and htpasswd to password protect a directory, all to no avail.

Does anyone see anything wrong with these two files I'm using?

.htaccess
```

AuthUserFile /home/content/l/o/g/login_name/html/professional/.htpasswd
AuthGroupFile /dev/null
AuthName EnterPassword
AuthType Basic

require valid-user 

```

.htpasswd
```

employers:aJC9SI6DkuPxI

```
Thanks in advance

---

