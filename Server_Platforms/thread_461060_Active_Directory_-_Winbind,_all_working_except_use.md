---
title: "Active Directory - Winbind, all working except users logging in"
date: 2007-06-01
forum: Server Platforms
---

### Post by telex4 on 2007-06-01
I've followed [this tutorial]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") and every step works fine (I can get tickets, authenticate, etc.) However, when I try to login either in KDM or over ssh it fails.

Trying via KDM seems to login (I don't get any password errors), but it then restarts X and dumps me straight back at the login prompt. The following entries show up from "last" and /var/log/auth.log:

```

**last**
tom.chan :0                            Fri Jun  1 15:06 - 15:06  (00:00)

**/var/log/auth.log**
Jun  1 15:06:13 hotdesk3 pam_winbind[5904]: user 'tom.chance' granted access
Jun  1 15:06:13 hotdesk3 pam_winbind[5904]: user 'tom.chance' OK
Jun  1 15:06:13 hotdesk3 pam_winbind[5904]: user 'tom.chance' granted access
Jun  1 15:06:13 hotdesk3 kdm: :0[5904]: (pam_unix) session opened for user tom.chance by (uid=0)
Jun  1 15:06:13 hotdesk3 kdm: :0[5904]: (pam_unix) session closed for user tom.chance

```

Trying via ssh yields its own problems. I'm doing it with Putty from a Windows workstation, and it seems to login (I don't get a bad password error) but the connection is immediately closed. There is no entry in "last", but this shows up in auth.log:

```

Jun  1 15:17:58 hotdesk3 sshd[6474]: Accepted password for tom.chance from 192.168.0.64 port 2399 ssh2
Jun  1 15:17:58 hotdesk3 sshd[6476]: (pam_unix) session opened for user tom.chance by (uid=0)
Jun  1 15:17:58 hotdesk3 sshd[6474]: fatal: login_get_lastlog: Cannot find account for uid 507
Jun  1 15:17:58 hotdesk3 sshd[6474]: syslogin_perform_logout: logout() returned an error
Jun  1 15:17:58 hotdesk3 sshd[6476]: (pam_unix) session closed for user tom.chance

```

Has anyone got any suggestions?

---

### Post by telex4 on 2007-06-04
If it helps at all, I've just checked the logs on the domain controller and there aren't any obvious problems there. Successful account logon records appear for both attempts, and look like this:

> Logon attempt by: MICROSOFT_AUTHENTICATION_PACKAGE_V1_0
Logon account: tom.chance
Source workstation: \\HOTDESK3
Error code: 0x0

Similar records appear with other "Account Logon" records in the security event log.

I'm still mystified.

---

