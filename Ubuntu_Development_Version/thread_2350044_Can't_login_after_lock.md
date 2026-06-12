---
title: "Can't login after lock"
date: 2017-01-20
forum: Ubuntu Development Version
---

### Post by cariboo on 2017-01-20
I just recently installed xubuntu on my laptop, I can login at the login screen, but when the system goes into screen lock, I can't login again. In /var/log/auth.log, I see the following error message:

```
alexis lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
```

What I have tried:

[LIST]
[*]Set login without a password
[*]Created a symlink to /lib/x86_64-linux-gn/security in /lib
[*]Set automatic screen lock to never
[/LIST]

Just so there aren't any questions about what version I'm using:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu Zesty Zapus (development branch)"
```

Has any one got a suggestion on how to solve this problem?

---

### Post by flocculant on 2017-01-21
Hi - seems to be a bug with lightdm and/or lightlocker.

You can revert to 1.21.1-0ubuntu1 or -0ubuntu2 lightdm and see how that goes. We're waiting on that to be fixed.

[https://launchpad.net/ubuntu/+source/lightdm/1.21.1-0ubuntu1](https://launchpad.net/ubuntu/+source/lightdm/1.21.1-0ubuntu1)
[https://launchpad.net/ubuntu/+source/lightdm/1.21.1-0ubuntu2](https://launchpad.net/ubuntu/+source/lightdm/1.21.1-0ubuntu2)

[lpbug]1656399[/lpbug]

---

### Post by rburkartjo on 2017-01-21
try this. at logon screen open a virtual terminal. logon. then type rm .Xauthority. you will be prompted if you want to over write. type y. then press enter. then reboot. worked for me recently. good luck.

---

