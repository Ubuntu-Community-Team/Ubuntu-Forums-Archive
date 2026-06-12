---
title: "Ubuntu 12.04 LTS SSH can't login"
date: 2014-02-28
forum: Server Platforms
---

### Post by fafabone on 2014-02-28
Yesterday my ssh server has been started to reject my login. I can acccess it only in recovery mode via ssh. Obviously ssh service is running when I check in recovery mode, but how can I be sure that it is running in normal mode?
This is my auth.log output:

Feb 28 07:38:35 live login[705]: pam_env(login:session): Unable to open env file: /etc/default/locale: No such file or directory
Feb 28 07:38:35 live login[705]: pam_unix(login:session): session opened for user root by LOGIN(uid=0)
Feb 28 07:38:35 live login[716]: ROOT LOGIN  on '/dev/tty1'
Feb 28 07:39:02 live sshd[558]: Received signal 15; terminating.
Feb 28 07:39:02 live sshd[1757]: Server listening on 0.0.0.0 port 22.
Feb 28 07:39:02 live sshd[1757]: Server listening on :: port 22.
Feb 28 07:39:04 live login[705]: pam_unix(login:session): session closed for user root
Feb 28 07:40:09 live sshd[1550]: Accepted password for root from 2.228.21.14 port 35757 ssh2
Feb 28 07:40:09 live sshd[1550]: pam_env(sshd:setcred): Unable to open env file: /etc/default/locale: No such file or directory
Feb 28 07:40:09 live sshd[1550]: pam_unix(sshd:session): session opened for user root by (uid=0)
Feb 28 07:40:10 live sshd[1784]: pam_env(sshd:setcred): Unable to open env file: /etc/default/locale: No such file or directory
Feb 28 07:54:46 live sshd[1925]: Connection closed by 2.228.21.14 [preauth]

what is /etc/default/locale?

---

### Post by CharlesA on 2014-02-28
It should show your default locale.

In my case it is:

```
LANG="en_US.UTF-8"
```

---

### Post by fafabone on 2014-02-28
What happens if it doesn't exist?

---

