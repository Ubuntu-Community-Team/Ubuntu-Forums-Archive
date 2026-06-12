---
title: "systemd-logind,cgmanager: failed: invalid request"
date: 2015-01-12
forum: Ubuntu Cloud and Juju
---

### Post by yusui-tomikawa on 2015-01-12
Hello. I need your help.
I am using Ubuntu 14.04.1 LTS 64bit minimal on a VPS service.


The following error message is output to /var/log/auth.log by rebooting server.

> 
**/var/log/auth.log**

Jan 12 02:27:05 myhost [COLOR=#ff0000]systemd-logind[297]: cgmanager: cgm_list_children for controller=systemd, cgroup_path=user failed: invalid request[/COLOR]
Jan 12 02:27:05 myhost systemd-logind[297]: New seat seat0.
Jan 12 02:27:06 myhost sshd[493]: Server listening on 0.0.0.0 port 22.
Jan 12 02:27:06 myhost sshd[493]: Server listening on :: port 22.

What is the cause of the problem?
Or is this ignorable error message?

---

