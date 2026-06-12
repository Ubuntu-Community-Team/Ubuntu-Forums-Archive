---
title: "AppArmor with net_bind_service capability"
date: 2018-11-22
forum: Security
---

### Post by samer123er on 2018-11-22
hi,

I want to give the nc tool the capacity to listen to port 80 using AppArmor.
I have defined the following profile:

```


#include <tunables/global>


/bin/nc.openbsd {


  #include <abstractions/base>
  #include <abstractions/consoles>
  #include <abstractions/nameservice>


capability net_bind_service,




}



```

when execute the following command:
/bin/nc.openbsd -l 80

it returns always permission denied message.

my profile is put in enforce mode and it is loaded by AppArmor service.

any help?

---

