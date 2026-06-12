---
title: "LXC bootup modprobe error"
date: 2015-03-19
forum: Virtualisation
---

### Post by alex351 on 2015-03-19
Hi guys,

I know LXC is not real virtualization - I still hope this is the right sub forum ;-)

I have an LXC container up and running and dont have any real issues but during boot I get the following error message:

```
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.13.0-46-generic/modules.dep.bin'



```

I've read that a kernel-image reinstall might fix the issue but I am not sure that is possible also inside an LXC container...

Again - the system works - I just would like to get rid of the error message...

---

### Post by mushinspace on 2015-03-20
I'm experiencing this too.

Running depmod on my LXC server helped with the messages, but the guest still report the same errors.

Hopefully, some else has the magic fix!

---

### Post by alex351 on 2015-05-29
I have the also issue...basically iptables errors, moddep - anybody has a clue how to fix this?

```
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin' * Starting configure network device security   ...done.
 * Starting set console font   ...done.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
<4>init: console-font main process (128) terminated with status 1
 * Starting set console font   ...fail!
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
 * Starting userspace bootsplash   ...done.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
<4>init: setvtrgb main process (144) terminated with status 1
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
 * Stopping userspace bootsplash   ...done.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
 * Starting Send an event to indicate plymouth is up   ...done.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
 * Stopping Send an event to indicate plymouth is up   ...done.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 12
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 12
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
 * Starting Initialize or finalize resolvconf   ...done.
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables-restore v1.4.21: iptables-restore: unable to initialize table 'filter'


Error occurred at line: 1
Try `iptables-restore -h' or 'iptables-restore --help' for more information.


Problem loading ipv6 (skipping)
Problem running '/etc/ufw/before.rules'
Problem running '/etc/ufw/after.rules'
Problem running '/lib/ufw/user.rules'
<4>init: ufw pre-start process (115) terminated with status 1
<4>init: console-setup main process (212) terminated with status 1
 * Starting Uncomplicated firewall   ...fail!
 * Starting Signal sysvinit that virtual filesystems are mounted   ...done.
 * Starting Signal sysvinit that virtual filesystems are mounted   ...done.
 * Starting Bridge udev events into upstart   ...done.
 * Starting Signal sysvinit that local filesystems are mounted   ...done.
 * Starting configure network device security   ...done.
<30>systemd-udevd[268]: starting version 204
 * Starting device node and kernel event manager   ...done.
 * Starting Signal sysvinit that remote filesystems are mounted   ...done.
 * Starting Mount network filesystems   ...done.
 * Stopping Mount filesystems on boot   ...done.
 * Starting Failsafe Boot Delay   ...done.
 * Starting Enabling additional executable binary formats   ...done.
 * Starting flush early job output to logs   ...done.
 * Starting load modules from /etc/modules   ...done.
 * Stopping load modules from /etc/modules   ...done.
 * Starting D-Bus system message bus   ...done.
 * Starting SystemD login management service   ...done.
 * Stopping flush early job output to logs   ...done.
 * Stopping Mount network filesystems   ...done.
 * Starting system logging daemon   ...done.
 * Starting mDNS/DNS-SD daemon   ...done.
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated   ...done.
<4>init: avahi-cups-reload main process (454) terminated with status 1
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated   ...fail!
 * Starting configure network device   ...done.
 * Starting Bridge file events into upstart   ...done.
 * Starting Bridge socket events into upstart   ...done.
 * Starting munin-node   ...done.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.16.0-4-amd64/modules.dep.bin'
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)



```

---

### Post by wildmanne39 on 2015-05-29
Please use normal fonts except to highlight a specific small amount of text.
Thanks

---

