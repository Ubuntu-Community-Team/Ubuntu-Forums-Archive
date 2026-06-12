---
title: "prevent dpkg from (re-)starting services"
date: 2008-05-07
forum: Server Platforms
---

### Post by leidola on 2008-05-07
Hi!

I'm using hardy on a fileserver. In the exported directory there are several ubuntu versions used as root filesystem for thin clients, e.g. hardy-i386, hardy-amd64 which I installed via debootstrap. I chroot into their directories to install new packages, updates etc. The problem is, that every time I install the update of a service, the service is restarted in the chrooted environment.

Is there a way to prevent dpkg from restarting these services?

Thanks in advance!

---

### Post by leidola on 2008-05-08
Perhaps the problem is a bit misunderstanding:

The chrooted environment shall not run any service, but whenever I install an update of e.g. cups, cups is started. 

Deleting the services from /etc/rc* directories is not an option, as they
are needed by the clients.

---

### Post by leidola on 2008-05-09
Hi!

Just got a mail from Michael Biebl at debian-user and the suggested script seems to work fine.

> policy-rc.d to your rescue.

Read the man page of invoke-rc.d : "INIT SCRIPT POLICY"
and /usr/share/doc/sysv-rc/README.policy-rc.d.gz

A simple /usr/sbin/policy-rc.d could look like this:

# cat /usr/sbin/policy-rc.d
#!/bin/sh
echo "************************************" >&2
echo "All rc.d operations denied by policy" >&2
echo "************************************" >&2
exit 101


---

