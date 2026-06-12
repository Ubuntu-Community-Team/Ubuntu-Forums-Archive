---
title: "When trying to start mysql I get this error:"
date: 2010-04-20
forum: Server Platforms
---

### Post by waloshin on 2010-04-20
unable to connect to system bus: failed to connect to socket /var/run/system_bus_socket: no file or directory

This happens when ever i try to to anything with the upstart job. 

such as vsftpd restart I get the above error. 

unable to connect to system bus: failed to connect to socket /var/run/system_bus_socket: no file or directory

---

### Post by waloshin on 2010-04-20
My solution as nobody can help me! Is to uninstall 10.04 alpha 2 and install 9.10 as for some off reason 10.04 alpha 2 Server is not to fully supported yet.

---

### Post by Jive Turkey on 2010-04-20
Although not really a solution for you, it helps the community to report bugs on stuff like that.  Often, you can get the problem solved through discussion on launchpad, and sometimes even through package updates that patch the bug.

---

### Post by linis_australis on 2011-07-28
I know this is an old old thread but today I began receiving this error when I 'attempt to shut-down. I get the message and shut-down halts, I have to do a power-down at the switch to reboot (booting up is fine). Also, and importantly as, when I look around the web this seems to be related to mysql, I DO NOT HAVE mysql installed!  So what gives and where might I look for more answers. I'm finding nothing of use in the syslog or boot.log

Many thanks for any help!

EDIT: using Ubuntu 11.04 desktop

EDIT: wait, stop the presses. . . my error is a little different but critically so:

"unable to connect to system bus: failed to connect to socket /var/run/dbus/system_bus_socket"

thus maybe I'm asking this in the wrong place.

---

