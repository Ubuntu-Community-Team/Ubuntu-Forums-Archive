---
title: "Permission Denied Session Closed"
date: 2016-11-09
forum: Server Platforms
---

### Post by ehamdja on 2016-11-09
Hi All, I need help if someone could guide me. I'm running ubuntu 16.04 server. I just recently cloned my hard drive from previously working system. But now with the new drive i can't no longer login to the terminal. When i entered my login, it didn't even ask my password. It gave me permission denied and session closed.
Below is the var/log/auth.log result

```
Nov  9 02:58:31 erickh-odroidXU4 login[2130]: PAM pam_parse: expecting return value; [...requiped]
Nov  9 02:58:31 erickh-odroidXU4 login[2130]: PAM pam_parse: expecting return value; [...requiped]
Nov  9 02:58:35 erickh-odroidXU4 login[2130]: pam_unix(login:session): session opened for user erickh by SHELLINABOX(uid=0)
Nov  9 02:58:35 erickh-odroidXU4 systemd: PAM pam_parse: expecting return value; [...requiped]
Nov  9 02:58:35 erickh-odroidXU4 systemd-logind[1113]: New session c2 of user erickh.
Nov  9 02:58:35 erickh-odroidXU4 systemd: PAM pam_parse: expecting return value; [...requiped]
Nov  9 02:58:35 erickh-odroidXU4 systemd: pam_unix(systemd-user:session): session opened for user erickh by (uid=0)
Nov  9 02:58:35 erickh-odroidXU4 login[2130]: Permission denied
Nov  9 02:58:35 erickh-odroidXU4 systemd-logind[1113]: Removed session c2.
```

Could someone give me any input what went wrong? Thank you.

---

### Post by volkswagner on 2016-11-10
Did you have an encrypted /home directory?

Are you able to log in as root?

Can you use recovery mode and login?

---

### Post by ehamdja on 2016-11-11
No, i don't have encrypted /home directory. I'm not able to login as root as well but i also run webmin for my server and is able to login using webmin. This is what confuses me. Also since i am new to ubuntu server, how do i go into recovery mode? Thank you

---

### Post by QIII on 2016-11-11
Are you booting from microSD/eMMC to / on a hard drive so the OS is actually running from HDD?

When you say you can't log in, is that using a mouse, keyboard and monitor connected directly to your XU4?

---

### Post by ehamdja on 2016-11-11
I am booting from eMMC and that's where my OS is installed. I accessed it from shellinabox and once I entered my username it just login without asking password and just showed permission denied and session closed. When I try login directly with monitor and keyboard connected to my XU4, it's the same, but just looping asking username and skipped password and try to login then back to asking username. I tried both my username and root and both giving the same result.

---

### Post by ehamdja on 2016-11-14
anybody have any suggestion?

---

