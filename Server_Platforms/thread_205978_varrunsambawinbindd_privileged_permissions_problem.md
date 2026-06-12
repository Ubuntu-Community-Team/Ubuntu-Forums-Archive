---
title: "/var/run/samba/winbindd_privileged permissions problem with varrun"
date: 2006-06-29
forum: Server Platforms
---

### Post by cod3r3d on 2006-06-29
I have an annoying problem with the following:  Ubuntu Server 6.06 running Samba, Squid and Winbind.  Squid is configured to use ntlm_auth to authenticate users against a Windows domain.  To do this, the group ownership for directory /var/run/samba/winbindd_privileged needs to be changed from "root" to  "proxy".  No problem there, but of course 6.06 uses the varrun temporary filesystem to mount /var/run, so upon reboot the changes to the group ownership are lost.  

I know I can modify the /etc/init.d/winbind script to pre-create this directory and/or fix the group ownership, but I'd rather find a method that doesn't change this script.

Anybody any ideas?

---

### Post by jesse.waters on 2006-06-29
I am delaing with the same problem, a work around

```

sudo vi /etc/init.d/winbind-ch.sh

```

```

#!/bin/sh
#set -x
WINBINDD_PRIVILEGED=/var/run/samba/winbindd_privileged

chmodgrp() {
    chgrp proxy $WINBINDD_PRIVILEGED || return 1
    chmod g+w $WINBINDD_PRIVILEGED || return 1
}

case "$1" in
    start)
        chmodgrp
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
#EOF

```

then have this run after winbind starts up
```

$ sudo update-rc.d  winbind-ch.sh start 21 2 3 4 5 .

```

This will work fine after a reboot but not if your start and stop the services out of order. Also if samba/winbind maintainers update down the road and change the init scripts it, this should not impact it.


HTH,

Jesse

---

