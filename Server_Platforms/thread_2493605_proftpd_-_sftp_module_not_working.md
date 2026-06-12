---
title: "proftpd - sftp module not working"
date: 2023-12-19
forum: Server Platforms
---

### Post by dhaecker on 2023-12-19
Hi,

strange thing with sftp module of proftpd 1.3.7c in Ubuntu 22.
The module will be skipped during startup.
Starting proftpd in debug mode "proftpd -d 10"
shows the following line:

<IfModule>: skipping 'mod_sftp.c' section at line 9

That's all. Any idea what's wrong?

Tried to compile newer version of proftpd to check if issue is related to all newer version.
But didn't find all packages which needs to be preinstalled to compile proftpd on ubuntu.
Does anybody have an hint for me where to find a list of packages which are needed to be installed to compile proftpd from scratch on ubuntu?

---

### Post by TheFu on 2023-12-19
Why use anything other than sftp-server?

[https://ubuntuforums.org/showthread.php?t=2493543&p=14170159#post14170159](https://ubuntuforums.org/showthread.php?t=2493543&p=14170159#post14170159)

---

### Post by dhaecker on 2023-12-19
> **TheFu said:**
> Why use anything other than sftp-server?

[https://ubuntuforums.org/showthread.php?t=2493543&p=14170159#post14170159](https://ubuntuforums.org/showthread.php?t=2493543&p=14170159#post14170159)

If this would have been an option I would have used it already.

---

### Post by dhaecker on 2023-12-20
In the config file modules.conf
The line "LoadModule mod_sftp.c" is commented out.
As consequence, sftp configurations will be skipped if configured.
This default configuration in modules.conf is new since ubuntu 22.

---

