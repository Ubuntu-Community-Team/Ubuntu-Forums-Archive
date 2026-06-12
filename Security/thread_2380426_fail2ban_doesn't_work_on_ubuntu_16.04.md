---
title: "fail2ban doesn't work on ubuntu 16.04"
date: 2017-12-17
forum: Security
---

### Post by g3kxyz on 2017-12-17
I've followed countless guides to get fail2ban to work but everytime I un-comment anything in the file /etc/fail2ban/jail.local then the service fails to start with the following error

```
# systemctl status fail2ban.serviceâ&#8212; fail2ban.service - Fail2Ban Service
   Loaded: loaded (/lib/systemd/system/fail2ban.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since Sun 2017-12-17 11:21:09 CST; 7s ago
     Docs: man:fail2ban(1)
  Process: 6333 ExecStop=/usr/bin/fail2ban-client stop (code=exited, status=0/SUCCESS)
  Process: 6356 ExecStart=/usr/bin/fail2ban-client -x start (code=exited, status=255)
 Main PID: 6107 (code=killed, signal=TERM)


Dec 17 11:21:09 g3k.pw systemd[1]: fail2ban.service: Control process exited, code=exited status=255
Dec 17 11:21:09 g3k.pw systemd[1]: Failed to start Fail2Ban Service.
Dec 17 11:21:09 g3k.pw systemd[1]: fail2ban.service: Unit entered failed state.
Dec 17 11:21:09 g3k.pw systemd[1]: fail2ban.service: Failed with result 'exit-code'.
Dec 17 11:21:09 g3k.pw systemd[1]: fail2ban.service: Service hold-off time over, scheduling restart.
Dec 17 11:21:09 g3k.pw systemd[1]: Stopped Fail2Ban Service.
Dec 17 11:21:09 g3k.pw systemd[1]: fail2ban.service: Start request repeated too quickly.
Dec 17 11:21:09 g3k.pw systemd[1]: Failed to start Fail2Ban Service.
```

In other words the service will start if I don't configure fail2ban to do ANYTHING to secure my server.

---

### Post by g3kxyz on 2017-12-27
Bump

---

### Post by Habitual on 2017-12-27
> **g3kxyz said:**
> In other words the service will start if I don't configure fail2ban to do ANYTHING to secure my server.

If it won't start after you "edit" please show us the edits. ;)
More importantly, what/where are you editing?
The First thing /etc/fail2ban/jail.conf suggests is 
```
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```
I recommend placing only enabled jails in /etc/fail2ban/jail.local
This is key to a good modular setup.

default out of the box experience used to be ssh protection was enabled.
IDK lately, Also believe there's an edit to make for enabling systems back-ends using fail2ban, before it will start...

Version of fail2ban?
```
fail2ban-client -V | head -1
```

---

