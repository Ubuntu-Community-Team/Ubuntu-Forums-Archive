---
title: "LXC containers do not start"
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by The Keeper on 2014-03-18
In 13.10 I see bunch of errors but the container progresses to login and appears to work fine. In 14.04 I see even more errors but container never gets to login.

Most of these errors are from starting a container, some of the last ones are from stopping the container.
```

<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<3>init: Error while reading from descriptor: Bad file descriptor
<3>init: Error while reading from descriptor: Bad file descriptor
<4>init: hostname main process (4) terminated with status 6
<4>init: plymouth-ready (startup) main process (6) terminated with status 6
<4>init: plymouth main process (8) terminated with status 6
<4>init: hwclock main process (10) terminated with status 6
<4>init: ureadahead main process (12) terminated with status 6
<4>init: startpar-bridge (hostname--started) main process (14) terminated with status 6
<4>init: startpar-bridge (plymouth-ready-startup-started) main process (16) terminated with status 6
<4>init: startpar-bridge (hwclock--started) main process (18) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<3>init: Error while reading from descriptor: Bad file descriptor
<4>init: mountall main process (20) terminated with status 6
<4>init: startpar-bridge (hostname--stopped) main process (22) terminated with status 6
<4>init: startpar-bridge (plymouth-ready-startup-stopped) main process (24) terminated with status 6
<4>init: startpar-bridge (plymouth--stopped) main process (26) terminated with status 6
<4>init: startpar-bridge (hwclock--stopped) main process (28) terminated with status 6
<4>init: startpar-bridge (ureadahead--stopped) main process (30) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<4>init: mountall post-stop process (32) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<3>init: Error while reading from descriptor: Bad file descriptor
<4>init: startpar-bridge (mountall--stopped) main process (34) terminated with status 6
<4>init: console-setup main process (36) terminated with status 6
<4>init: plymouth-stop pre-start process (38) terminated with status 6
<4>init: startpar-bridge (console-setup--started) main process (40) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<3>init: Error while reading from descriptor: Bad file descriptor
<4>init: mountall-shell main process (42) terminated with status 6
<4>init: startpar-bridge (mountall-shell--started) main process (44) terminated with status 6
<4>init: startpar-bridge (console-setup--stopped) main process (46) terminated with status 6
<4>init: startpar-bridge (plymouth-stop--stopped) main process (48) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<3>init: Error while reading from descriptor: Bad file descriptor
<4>init: mountall-shell post-stop process (50) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<4>init: startpar-bridge (mountall-shell--stopped) main process (52) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<4>init: shutdown main process (54) terminated with status 6
<4>init: startpar-bridge (shutdown--started) main process (56) terminated with status 6
<2>init: error.c:219: Assertion failed in _nih_error_raise_system: errno > 0
<2>init: Caught abort, core dumped
<4>init: startpar-bridge (shutdown--stopped) main process (58) terminated with status 6

```

I couldn't find anything from google search results. Does anyone have working LXC containers in 14.04? I might add that these errors happen on containers freshly created from the Ubuntu template.

---

### Post by The Keeper on 2014-03-18
Here is a comparison of output from a container created with Debian template and it works. Both containers are using defaults, their configs have not been altered.

```

lxc-start: Device or resource busy - failed to set memory.use_hierarchy to 1; continuing
lxc-start: Device or resource busy - failed to set memory.use_hierarchy to 1; continuing
INIT: version 2.88 booting
Using makefile-style concurrent boot in runlevel S.
Cleaning up temporary files... /tmp /run /run/lock /run/shm.
mount: cannot remount block device tmpfs read-write, is write-protected
mount: cannot remount block device tmpfs read-write, is write-protected
mount: cannot remount block device proc read-write, is write-protected
mount: cannot remount block device sysfs read-write, is write-protected
mount: cannot remount block device tmpfs read-write, is write-protected
mount: cannot remount block device devpts read-write, is write-protected
Mount point '/dev/console' does not exist. Skipping mount. ... (warning).
Mount point '/dev/tty1' does not exist. Skipping mount. ... (warning).
Mount point '/dev/tty2' does not exist. Skipping mount. ... (warning).
Mount point '/dev/tty3' does not exist. Skipping mount. ... (warning).
Mount point '/dev/tty4' does not exist. Skipping mount. ... (warning).
Mount point '/dev/ptmx' does not exist. Skipping mount. ... (warning).
Activating lvm and md swap...done.
Checking file systems...fsck from util-linux 2.20.1
done.
Mounting local filesystems...done.
/etc/init.d/mountall.sh: 59: kill: Illegal number: 4 1
Activating swapfile swap...done.
Cleaning up temporary files....
Setting kernel variables ...done.
Configuring network interfaces...Internet Systems Consortium DHCP Client 4.2.2
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:16:3e:d5:9b:3f
Sending on   LPF/eth0/00:16:3e:d5:9b:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPOFFER from 10.0.3.1
DHCPACK from 10.0.3.1
bound to 10.0.3.46 -- renewal in 1545 seconds.
done.
Cleaning up temporary files....
INIT: Entering runlevel: 3

```

---

### Post by alan-pater on 2014-03-18
How did you create the containers and how are you starting them?

I am running several LXC containers in 14.04 and have not had any issues.

To create and start a new container I use:
 > ~$ sudo lxc-create -t ubuntu -n BOB
~$ sudo lxc-clone -o BOB -n BETTY 
~$ sudo lxc-start -n BETTY

---

### Post by The Keeper on 2014-03-18
Yep, used lxc-create and lxc-start as you described.

I also tried with just debootstrap without using a template to create an ubuntu container, same problem as described in the first post.
```

debootstrap --include=lxc --arch=amd64 trusty rootfs

```

---

