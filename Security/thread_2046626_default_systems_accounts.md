---
title: "default systems accounts"
date: 2012-08-23
forum: Security
---

### Post by Loki57701 on 2012-08-23
In the /etc/passwd file there are several default system users that have valid shells:


```

user: daemon     shell: /bin/sh
user: bin        shell: /bin/sh
user: sys        shell: /bin/sh
user: sync       shell: /bin/sync
user: games      shell: /bin/sh
user: man        shell: /bin/sh
user: lp         shell: /bin/sh
user: mail       shell: /bin/sh
user: news       shell: /bin/sh
user: uucp       shell: /bin/sh
user: proxy      shell: /bin/sh
user: www-data   shell: /bin/sh
user: backup     shell: /bin/sh
user: list       shell: /bin/sh
user: irc        shell: /bin/sh
user: gnats      shell: /bin/sh
user: nobody     shell: /bin/sh
user: libuuid    shell: /bin/sh
user: statd      shell: /bin/false
user: sshd       shell: /usr/sbin/nologin

```

I would like to set many of these to /bin/false or nologin, but Im not sure if that's safe to do.

---

### Post by thnewguy on 2012-08-24
I suppose you could do that, though it might be less instrusive if you simply locked the non-user accounts, rather than changing their configuration. If you look at the /etc/shadow file you will see each account has a password field with a * or a ! or a long hashed password. Accounts with a * or a ! can't be logged into in the normal sense. This means even though they do not have a password, a person can't try to guess a password and login. Making sure your system accounts are locked in this fashion is probably less work than changing all the shell entries. In fact, I believe Ubuntu locks these system accounts by default.

Check /etc/shadow and look at the man page for shadow "man shadow" for more information.

---

### Post by Loki57701 on 2012-08-25
Thank you. You are indeed correct, I completely forgot about the shadow file.

---

