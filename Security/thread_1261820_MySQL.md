---
title: "MySQL"
date: 2009-09-09
forum: Security
---

### Post by phillw on 2009-09-09
I think I got a bit carried away ......

Whilst reading my logs I, logrotate is complaining ...

Hmmmm.....

When I re-installed MySQL I deleted the user debian-admin.... Log-rotate, obviously is complaining !!!
As the server is only on my test rig, can I simply remove the cron job ?

The 2nd one, has me puzzled .....

Warning: The SSH configuration option 'PermitRootLogin' has not been set.
         The default value may be 'yes', to allow root access.
Warning: The SSH configuration option 'Protocol' has not been set.
         The default value may be '2,1', to allow the use of protocol version 1.
[FONT=Arial]Reported by rkhunter ... Only....  [/FONT]etc/ssh/ssd_config is ...

```

PermitRootLogin no
.
.
Protocol 1,2
.
.

```
[LIST=1]
[*]Should protocol be 2,1  and
[*]why is rkhunter reporting that PermitRootLogin has not been set ?
[/LIST]

Thanks,

Phill.

---

### Post by Bachstelze on 2009-09-09
Protocol should be 2. SSHv1 is old and insecure, so it's better to disable it completely. As for why rkhunter is reporting that, no idea. I don't use it.

---

### Post by phillw on 2009-09-09
```
Protocol should be 2.
```

Altered, anyone for the PermitRootLogin query and log-rotate ?

Thanks.

Phill.

---

