---
title: "udev rules for USB don't work for the &quot;remove&quot; action"
date: 2011-03-03
forum: Server Platforms
---

### Post by Pitt Stains on 2011-03-03
Hello,

I'm running Ubuntu Server Edition 10.04.1 LTS, and I'm having trouble with udev rules.  I want to run a script each time I connect or remove a particular external USB drive.

I've added a file 10-custom.rules to /etc/udev/rules.d/ containing the following line:

```

KERNEL=="sd??", SUBSYSTEM=="block", DRIVERS=="usb", ATTRS{serial}=="2HAA5201", SYMLINK+="off-site-backup", RUN+="/usr/local/share/backuppc/bin/prepare_usb.sh"

```

For now, prepare_usb.sh contains just this code:
```

#!/bin/bash
/usr/bin/touch /home/pstains/udev.test
/bin/echo "${ACTION}" > /home/pstains/udev.test
exit 0

```

prepare_usb.sh is run (and, as a result, /home/pstains/udev.test is updated) every time I plug in the external drive, but it never runs when I unplug the drive.

For debugging purposes, I ran the following command:

```

sudo udevadm test --action="add" /block/sdc/sdc1/

```

... which gave me a whole bunch of output, including the following line:

```

udev_rules_apply_to_event: RUN '/usr/local/share/backuppc/bin/prepare_usb.sh' /etc/udev/rules.d/10-custom.rules:2

```

However, when I ran it with the action set to "remove," i.e.:
```

sudo udevadm test --action="remove" /block/sdc/sdc1/

```

... there were no udev_rules_apply_to_event lines at all in the output.

Any thoughts on how I can rewrite my rules to match both cases?  Or suggestions for getting more useful debugging info?

Thanks,
-Pitt

---

### Post by karre on 2012-04-20
Hi ,

i am facing the same problem .

i wrote my customized rule to mount and umount usb drive to the board.

my mount rule is working and umount rule is not working please suggest me where i am missing.

i have created my rule using udevadm info -a -p /sys/block/sdb

Thanks,
nagaraju.

---

