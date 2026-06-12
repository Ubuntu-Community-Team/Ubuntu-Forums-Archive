---
title: "PC speaker &quot;beep&quot; when done booting"
date: 2007-06-03
forum: Server Platforms
---

### Post by MrCreosote on 2007-06-03
Hi there,

I'd like the PC speaker to produce a beep  when it's done booting. When it's "ready". How could I do this on my 6.06 LTS server? I remember IPCop had such a feature and I was quite fond of it for some reasons...and yes, I realize you don't reboot a server that much but I'm trying to build a router/gateway/firewall/kitchen sink on my box right now and this would be useful for a while...

Thanks...

---

### Post by craigp84 on 2007-06-04
Hi MrCreosote,

```
sudo apt-get install beep
```

Add the following to /etc/init.d/beep

```

#!/bin/bash
#
# beep
# Notify when the system is up, or going down
# Craig Perry, 4th Jun 2007

BEEP=/usr/bin/beep
. /lib/lsb/init-functions

case "$1" in
  start)
    log_begin_msg "Audible notification - System Now Up..."
    for i in `seq 750 1500`; do
      $BEEP -l 2 -f $i
    done
    log_end_msg 0
    ;;
  stop)
    log_begin_msg "Audible notification - System Going Down..."
    for i in `seq 1500 -1 750`; do
      $BEEP -l 2 -f $i
    done
    log_end_msg 0
    ;;
  *)
    log_success_msg "Usage: $0 {start|stop}"
    exit 1
    ;;
esac
exit 0

```

Then make it executable:
```
chmod +x /etc/init.d/beep
```

Finally, install some hooks to make it run:
```
sudo update-rc.d beep defaults 99 01
```

This gives you an ascending tone when the system comes up, and a descending tone as it's starting to shutdown (i.e. confirms you've pressed the power button correctly).

Hope this helps

-c

---

