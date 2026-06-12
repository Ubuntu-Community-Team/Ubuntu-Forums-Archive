---
title: "thermald 1.3-7 package bug on today's updates"
date: 2014-12-04
forum: Ubuntu Development Version
---

### Post by slickymaster on 2014-12-04
Anyone got this?```
...
Setting up thermald (1.3-7) ...
Job for thermald.service failed. See "systemctl status thermald.service" and "journalctl -xe" for details.
invoke-rc.d: initscript thermald, action "start" failed.
dpkg: error processing package thermald (--configure):
 subprocess installed post-installation script returned error exit status 1
```

[https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1399131](https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1399131)

---

### Post by zika on 2014-12-04
> **slickymaster said:**
> Anyone got this?```
...
Setting up thermald (1.3-7) ...
Job for thermald.service failed. See "systemctl status thermald.service" and "journalctl -xe" for details.
invoke-rc.d: initscript thermald, action "start" failed.
dpkg: error processing package thermald (--configure):
 subprocess installed post-installation script returned error exit status 1
```

[https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1399131](https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1399131)Yeap, purged thermald for now.

---

### Post by slickymaster on 2014-12-04
> **zika said:**
> Yeap, purged thermald for now.

I'm assuming you don't expect your machine to overheat. ;)

---

### Post by zika on 2014-12-04
> **slickymaster said:**
> I'm assuming you don't expect your machine to overheat. ;)No, I do not expect thermald to prevent it. I do that in old fashioned manner by planning HW characteristics in advance and in accordance with my usage of it.

---

### Post by slickymaster on 2014-12-04
> **zika said:**
> No, I do not expect thermald to prevent it. I do that in old fashioned manner by planning HW characteristics in advance and in accordance with my usage of it.
Better safe than sorry.:p

---

### Post by mc4man on 2014-12-04
No issue here (though on -proposed
> synaptic:26695): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 187569 files and directories currently installed.)
Preparing to unpack .../thermald_1.3-7_amd64.deb ...
thermald stop/waiting
Unpacking thermald (1.3-7) over (1.3-6) ...
Processing triggers for dbus (1.8.8-2ubuntu2) ...
Processing triggers for ureadahead (0.100.0-17) ...
Processing triggers for man-db (2.7.0.2-3) ...
Setting up thermald (1.3-7) ...
thermald start/running, process 27104


---

### Post by zika on 2014-12-04
> **mc4man said:**
> No issue here (though on -proposedAt a laptop at my work there was no issuse also, just on the machine at my home, main workhorse in my life... ;)
> **slickymaster said:**
> Better safe than sorry.:pThat is why I rely (only, exclusively) on HW... ;)

---

### Post by slickymaster on 2014-12-04
> **mc4man said:**
> No issue here (though on -proposed

Yeah, didn't get it also on a different test box with yesterday's image.

---

### Post by mc4man on 2014-12-04
Saw the same thing on the software-center issue, had no issue upgrading though had had it (SC) upgraded some time ago, likely when it was in -proposed
I generally have -proposed enabled to see what's upcoming though don't always use it. 
(-except when I forget it is enabled, then just hope for the best, haven't been 'burned' yet

---

### Post by ventrical on 2014-12-04
> **slickymaster said:**
> Anyone got this?```
...
Setting up thermald (1.3-7) ...
Job for thermald.service failed. See "systemctl status thermald.service" and "journalctl -xe" for details.
invoke-rc.d: initscript thermald, action "start" failed.
dpkg: error processing package thermald (--configure):
 subprocess installed post-installation script returned error exit status 1
```

[https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1399131](https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1399131)

Worked fine here on my xubuntu default.

```

Setting up thermald (1.3-7) ...
thermald start/running, process 13252

```

---

### Post by slickymaster on 2014-12-05
A fix has already been committed.

thermald 1.3-8 should be available within the next 12 or so hours.

---

