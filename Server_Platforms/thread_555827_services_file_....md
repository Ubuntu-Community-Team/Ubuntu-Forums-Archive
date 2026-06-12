---
title: "services file ..."
date: 2007-09-20
forum: Server Platforms
---

### Post by fahd on 2007-09-20
Hi folks!
I am eager to know where does the system store the services (demons) which run at start up time (may be some where in /etc directory)? Thanks a lot.

Fahd

---

### Post by MJN on 2007-09-20
You might need to elaborate on your question slightly, but to get you going the list of services which start (and stop) at each run-level is defined in /etc/rc#.d/ where # is the run-level 0 = halt, 1 = single user, 2-05 = multi-user and 6 = reboot. The default run-level is 2 hence everything listed /etc/rc2.d/ that starts with S is started during the boot process. Each entry usually refers to a script in /etc/init.d/

Note also that everything in /etc/rcS.d/ is also started, along with the script /etc/rcS.local (empty by default).

Services can be started by other means also, so perhaps it may be worth expanding on your thoughts behind the question to focus towards the answer you require.

The services themselves usually reside in /usr/bin, /usr/sbin, and more besides but I'm not sure if that's what you're asking.

Does that help?

Mathew

---

### Post by fahd on 2007-09-21
In redhat-based systems there is a package called: 
chkconfig --list 
which lists the actual services. That was my question. What is the name of such package in deb-based (ubuntu) systems. Thanks a lot.

Fahd

---

### Post by MJN on 2007-09-21
**sysv-rc-conf** is probably as close as you're going to get in terms of direct functional equivalence to chkconfig but, leaving the --list option aside, **update-rc.d** is the 'common' Debian-way of controlling service action at each run-level as discussed above.
 
For a GUI solution check out ksysv ([http://docs.kde.org/stable/en/kdeadmin/ksysv/index.html) ]("http://docs.kde.org/stable/en/kdeadmin/ksysv/index.html%29")or bum ([http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)).
 
Mathew

---

