---
title: "AD Authentication Problem"
date: 2010-11-04
forum: Server Platforms
---

### Post by woogy on 2010-11-04
Hey everybody,

To begin, this is the thread that I always use to set up my Ubuntu boxes for AD authentication:

[http://ubuntuforums.org/showthread.php?t=91510]("http://ubuntuforums.org/showthread.php?t=91510")

I've had this 10.04 server running for about three months with AD authentication running on it perfect. I have multiple Samba shares that authenticate from AD as well. For some reason, this week it decided to completely stop accepting any authentication from AD.

I checked all of my config files, they are all untouched. I have restarted the machine multiple times. I have unjoined and rejoined the domain on the Ubuntu server. I have no audit failures in my security logs on the domain controller.

Output of /var/log/auth.log whenever I try to log on via an AD user:

```
Nov  4 11:58:50 caribbean sshd[1869]: Invalid user justin from 10.3.17.12
Nov  4 11:58:50 caribbean sshd[1869]: Failed none for invalid user justin from 10.3.17.12 port 54738 ssh2
Nov  4 11:58:51 caribbean sshd[1869]: pam_winbind(sshd:auth): getting password (0x00000000)
Nov  4 11:58:51 caribbean sshd[1869]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_WRONG_PASSWORD, Error message was: Wrong Password
Nov  4 11:58:51 caribbean sshd[1869]: pam_winbind(sshd:auth): user 'justin' denied access (incorrect password or invalid membership)
Nov  4 11:58:51 caribbean sshd[1869]: pam_unix(sshd:auth): check pass; user unknown
Nov  4 11:58:51 caribbean sshd[1869]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=justinwin7.up-times.local
Nov  4 11:58:53 caribbean sshd[1869]: Failed password for invalid user justin from 10.3.17.12 port 54738 ssh2
```

Thanks for your help,
Justin

---

### Post by woogy on 2010-11-04
Bump, even some troubleshooting steps would be great - I'm not 100% sure where to look for other possible errors and/or information.

Thanks!

---

### Post by luvshines on 2010-11-05
Howdy !!

Have you tried logging in with domain\\username (assuming \ as your winbind separator)

---

