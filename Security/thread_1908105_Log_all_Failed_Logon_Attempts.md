---
title: "Log all Failed Logon Attempts"
date: 2012-01-12
forum: Security
---

### Post by aceofalltrades on 2012-01-12
I have ubuntu setup to log the failed logons of know accounts.  I need to get it to log the logon attempts of unknown accounts.  I know that this could capture users passwords when they accidentally type there password in the username field.

---

### Post by aceofalltrades on 2012-01-13
Any help would be appreciated. i know that i have done this before i just can't remember how i did it.  This is a requirement that i have to meet for my work.

I have the login.def LOG_UNKFAIL_ENAB set to YES.  But the when i test this with a username that doesn't exist it doesn't show in the log.

---

### Post by CharlesA on 2012-01-13
Is that for local logins or ssh logins?

---

### Post by Doug S on 2012-01-13
Hi Charles: I had assumed aceofalltrades meant local logins, because I have always noticed the invalid names for SSH attempts in the auth.log file. Regardless, it is good to clarify.
 
aceofalltrades: I tried a local login on my system and then searched my entire /var/log directory, but didn't find the invalid user name anywhere. Then I did the edit you mentioned to the /etc/login.defs file. I didn't even re-boot or restart anything. It worked for me, and made an entry in the /var/log/auth.log file. Log segment below:```
Jan 13 09:51:47 doug-64 sudo:     doug : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/nano login.defs
Jan 13 09:52:55 doug-64 login[2533]: pam_unix(login:auth): check pass; user unknown
Jan 13 09:52:55 doug-64 login[2533]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty4 ruser= rhost=
Jan 13 09:52:55 doug-64 login[2533]: pam_winbind(login:auth): getting password (0x00000388)
Jan 13 09:52:55 doug-64 login[2533]: pam_winbind(login:auth): pam_get_item returned a password
Jan 13 09:52:58 doug-64 login[2533]: FAILED LOGIN (1) on '/dev/tty4' FOR '[COLOR=red]fred[/COLOR]', Authentication failure
J
```

---

### Post by CharlesA on 2012-01-13
> **Doug S said:**
> Hi Charles: I had assumed aceofalltrades meant local logins, because I have always noticed the invalid names for SSH attempts in the auth.log file. Regardless, it is good to clarify.

That's how it works for me too. I was just curious. ;)

---

### Post by aceofalltrades on 2012-01-13
Yes i do me local logon's and not the ssh ones.
Here is what i get in my auth.log when i try unkown usernames

Jan 13 15:23:16 226972 gdm-session-worker[2525]: pam_tally(gdm:auth): pam_get_uid; no such user
Jan 13 15:23:17 226972 gdm-session-worker[2525]: pam_unix(gdm:auth): check pass; user unknown
Jan 13 15:23:17 226972 gdm-session-worker[2525]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Jan 13 15:23:20 226972 gdm-session-worker[2532]: pam_tally(gdm:auth): pam_get_uid; no such user
Jan 13 15:23:21 226972 gdm-session-worker[2532]: pam_unix(gdm:auth): check pass; user unknown
Jan 13 15:23:21 226972 gdm-session-worker[2532]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 

I think it is something to do with the gdm file in the /etc/pam.d folder.   I will have to dig more into what that file does.  

Shawn

---

