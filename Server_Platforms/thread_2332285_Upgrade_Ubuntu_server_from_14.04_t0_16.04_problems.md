---
title: "Upgrade Ubuntu server from 14.04 t0 16.04 problems"
date: 2016-07-30
forum: Server Platforms
---

### Post by deepakdeshp on 2016-07-30
Hello ,

I upgraded from Ubuntu server 14.04 to 16.04. Kindly help with following queries.

1. After upgrade the Kernel hasnt been upgraded to version 4.x

```
 inxi -FxzSystem:    Host: ubuntu-i386 Kernel: 3.13.0-24-generic i686 (32 bit gcc: 4.8.2)
           Console: tty 1 Distro: Ubuntu 16.04 xenial
```

2. There have been some errors while upgrading. Where is  the log file for the same?
3. I need to run a command at system start up. What is the process for the same? The script is ready for the command as follows. Where should I copy and link  the script?

```
 [COLOR=#000000]#######################################################[/COLOR]    #! /bin/sh
    # . /etc/rc.d/init.d/functions    # uncomment/modify for your killproc
    case "$1" in
        start)
        echo "Starting noip2."
        /usr/local/bin/noip2
        ;;
        stop)
        echo -n "Shutting down noip2."
        killproc -TERM /usr/local/bin/noip2
        ;;
        *)
        echo "Usage: $0 {start|stop}"
        exit 1
    esac
    exit 0 [COLOR=#000000]    #######################################################[/COLOR]
```

---

