---
title: "ubuntu 22 permission \ different environment issue setting coredump"
date: 2024-01-04
forum: Security
---

### Post by ilia2 on 2024-01-04
I am migrating one of our servers from centos 7 to ubutnu 22.4 lts

Found an interesting issue:

set [FONT=Arial]**/etc/security/limits.conf** is set set with:
[/FONT]```

[FONT=Arial]* soft core unlimited[/FONT]
[FONT=Arial]* hard core unlimited
[/FONT]
```
created new user named AAA,

code i am trying to run inside python3 shell:
```
i[B]mport resource
resource.getrlimit(resource.RLIMIT_CORE)
resource.setrlimit(
    resource.RLIMIT_CORE,
        (resource.RLIM_INFINITY, resource.RLIM_INFINITY)
    )
[/B]
```

when login to the user using the command:
[B]sudo su AAA
[/B]the code works and i can set core dump to unlimited 


when login to the user with:
[FONT=Arial]**sudo -i -u ****AAA**[B] /bin/bash

[/B]the python code fails, user dont have permission 
[/FONT]

---

