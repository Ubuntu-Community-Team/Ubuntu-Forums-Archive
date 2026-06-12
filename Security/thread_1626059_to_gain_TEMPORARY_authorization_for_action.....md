---
title: "to gain TEMPORARY authorization for action?...."
date: 2010-11-19
forum: Security
---

### Post by VcDeveloper on 2010-11-19
What is this?  My 2wire only allows HTTP/HTTPS access and this is my home office network.  I was checking my auth.log for a previous question I posted and this popped up:

```
Nov 19 17:41:51 anointed polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:*** to gain TEMPORARY authorization for action org.freedesktop.systemtoolsbackends.set for system-bus-name::1.105 [users-admin] (owned by unix-user:***)
```

---

### Post by VcDeveloper on 2010-11-19
Well, I did a filter and notice quite a few of these entries.  Looked at my processes and notice it's a deamon policy kit.  Is this ok?  I'm assuming its a ubuntu standard module.

---

### Post by CharlesA on 2010-11-20
Are you running Ubuntu desktop edition? If so, that's normal.

```
ubuntu@ubuntu-VirtualBox:~$ cat /var/log/auth.log |grep TEMPORARY
Nov 11 20:09:21 ubuntu-VirtualBox polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 successfully authenticated as unix-user:ubuntu to gain TEMPORARY authorization for action org.debian.apt.install-or-remove-packages for system-bus-name::1.41 [/usr/bin/python2.6 /usr/bin/update-manager --no-focus-on-map] (owned by unix-user:ubuntu)

```

---

### Post by VcDeveloper on 2010-11-20
OK Thanks!...

---

