---
title: "Apparmor Error running aa-logprof"
date: 2024-09-01
forum: Security
---

### Post by lance bermudez on 2024-09-01
Is there a fix for this error yet? I as told that it may have to do with linux containers is that true? I have done updates and still have this error.

Ubuntu version
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04.1 LTS
Release:	        24.04
Codename:	noble

```

aa-logprof error
```

$ sudo aa-logprof

ERROR: Can't parse mount rule mount options=(rw, make-slave) -> **,

```

aa-status
```

$ sudo aa-status
apparmor module is loaded.
225 profiles are loaded.
133 profiles are in enforce mode.
    ....
4 profiles are in complain mode.
    ....
0 profiles are in prompt mode.
0 profiles are in kill mode.
88 profiles are in unconfined mode.
    ....
59 processes have profiles defined.
19 processes are in enforce mode.
    ....
0 processes are in complain mode.
0 processes are in prompt mode.
0 processes are in kill mode.
40 processes are unconfined but have a profile defined.
    ....
0 processes are in mixed mode.

```

---

### Post by lance bermudez on 2024-09-13
Does any one know how to fix this error?

---

