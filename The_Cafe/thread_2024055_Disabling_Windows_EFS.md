---
title: "Disabling Windows EFS"
date: 2012-07-13
forum: The Cafe
---

### Post by Lucradia on 2012-07-13
Just wondering how one would go about disabling Windows' EFS, which is run via lsass.exe. I looked around, and there doesn't seem to be any information on it. My files, all of my documents don't use NTFS Encryption, and I don't care if my Windows system files use encryption or not. I just want it disabled, as it does constant R/W on my HDD.

No, you can't disable it via Services: [http://i.imgur.com/wC53Y.png](http://i.imgur.com/wC53Y.png)

---

### Post by llua+ on 2012-07-13
EFS is a service they don't want you to stop on a running system. Disabling it(from starting on boot) and restarting the system should prevent it from starting(at boot).
 ```
C:\Windows\system32>sc query efs

SERVICE_NAME: efs
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 4  RUNNING
                                **(NOT_STOPPABLE, NOT_PAUSABLE, IGNORES_SHUTDOWN)**
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0
``` iirc by default it set to manual. so something on your system has to be calling the service to start if you continue to see it run.

---

### Post by Lucradia on 2012-07-14
It's funny, because it's set to start at boot. But when I booted this time, it's got this:

```
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users>sc query efs

SERVICE_NAME: efs
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 1  STOPPED
        WIN32_EXIT_CODE    : 1077  (0x435)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0

C:\Users>
```

---

