---
title: "Netatalk Auth issues"
date: 2013-12-10
forum: Server Platforms
---

### Post by Default112 on 2013-12-10
Hi there,

I have problem with my Netatalk installation. I allowed guest login and configured pam to authenticate against an active directory. Currently the server is running Ubuntu 12.04 LTS with samba 3 installed. If I try to connect via my macbook (mountain lion) and choose to use the guest account, I'm able to connect. If I try to connect with username and password, it fails. I tried the root user and different users from the active directory. The login window shakes and I'm not logged in. If I connect via samba, everything works fine.

Now for some logs.

Connection with wrong username and password:
```
Dec 10 12:17:48 IMPRESS-S04 afpd[12118]: DHX2 login: default112
Dec 10 12:17:48 IMPRESS-S04 afpd[12118]: PAM DHX2: PAM Success
Dec 10 12:17:54 IMPRESS-S04 afpd[12118]: DHX2: PAM_Error: Authentication failure
```

Connection with correct username and password:
```
Dec 10 12:18:00 IMPRESS-S04 afpd[12128]: DHX2 login: default112
Dec 10 12:18:00 IMPRESS-S04 afpd[12128]: PAM DHX2: PAM Success
Dec 10 12:18:02 IMPRESS-S04 afpd[12128]: DHX2: PAM_Error: Permission denied
```

Connection as guest:
```
Dec 10 13:46:59 IMPRESS-S04 afpd[12960]: <== Start AFP command: AFP_LOGIN
Dec 10 13:46:59 IMPRESS-S04 afpd[12960]: login noauth
Dec 10 13:46:59 IMPRESS-S04 afpd[12960]: AFP3.3 Login by nobody
Dec 10 13:46:59 IMPRESS-S04 afpd[12960]: obj->options.admingid == 0
Dec 10 13:46:59 IMPRESS-S04 afpd[12960]: login: supplementary groups:  65534
Dec 10 13:46:59 IMPRESS-S04 afpd[12960]: ==> Finished AFP command: AFP_LOGIN -> AFP_OK
```

OK, permission denied. Sounds like a problem with permissions. I have defined only one volume and the filesystem permissions are 775.

Any suggestions?

Regards
Default112

---

### Post by Default112 on 2013-12-12
Solved. My PAM config was bogus. The new settings:

```
#%PAM-1.0
#auth     include common-auth
#account  include common-account
#password include common-password
#session  include common-session

auth       required     pam_winbind.so
account    required     pam_winbind.so
session    required     pam_unix.so
```

Authentication works fine now :)

---

