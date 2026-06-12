---
title: "Edit ssh config for password login"
date: 2009-09-27
forum: Security
---

### Post by sprouty on 2009-09-27
Hi,

I'm using ubuntu 8.10 with open ssh sever installed. Does anyone know if i can edit the config file for custom login i.e.
<ip Address>,<Username>,<Password>,<date time stamp>

Any information would be gratefull. I've tried googleing but nothing so far!!

Many Thanks,
Sprouty

---

### Post by bodhi.zazen on 2009-09-27
Not sure what you are wanting but yes you have options.

[SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

[SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by sprouty on 2009-10-02
Wow just read that back and it makes no sence sorry!!!

I've had ssh enabled on my ip address and see a lot attempts for different user to login. I was wondering if there a way to see/log what password and username combination they are using... 

Just something i would be intresting in seeing? anyone got something like this set up?

---

### Post by BQAggie2006 on 2009-10-02
/var/log/auth.log will log what usernames had failed attempts

---

### Post by sprouty on 2009-10-02
yer, i want to get the password(S) that they are using

---

### Post by BQAggie2006 on 2009-10-02
Don't know how possible that is since passwords transmitted through SSH are encrypted. You might be able to run Wireshark and then run any passwords collected through John the Ripper.

---

### Post by cariboo on 2009-10-03
Most attempts to log in via ssh use a dictionary attack, you should see the usernames and passwords the attacker is trying in /var/log/auth.log

---

### Post by sprouty on 2009-10-03
In /var/log/auth.log i can only see the username no password: please see the end of my auth.log

```
Oct  3 10:37:14 hostname1 sshd[9236]: Invalid user bob from <myIP>
Oct  3 10:37:14 hostname1 sshd[9236]: Failed none for invalid user bob from <myIP> port 1193 ssh2
Oct  3 10:37:17 hostname1 sshd[9236]: pam_unix(sshd:auth): check pass; user unknown
Oct  3 10:37:17 hostname1 sshd[9236]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=<myIP>
Oct  3 10:37:20 hostname1 sshd[9236]: Failed password for invalid user bob from <myIP> port 1193 ssh2
Oct  3 10:37:58 hostname1 sshd[9239]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=<myIP>  user=<Valid user>
Oct  3 10:37:59 hostname1 sshd[9239]: Failed password for <Valid user> from <myIP> port 1196 ssh2
```

Many THanks,
Paul

---

