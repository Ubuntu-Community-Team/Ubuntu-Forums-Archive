---
title: "No input/output from jack"
date: 2012-08-18
forum: Ubuntu Studio
---

### Post by btilford on 2012-08-18
Any tricks to getting sound to route through? I worked through the realtime permissions issues that were preventing me from starting the  server and am getting no error messages but no applications that use  seem to get a signal in/out. I do however have sound it just doesn't seem to be going through .

Messages from Starting QCtl
```

23:33:14.440 Patchbay deactivated.
23:33:14.460 Statistics reset.
23:33:14.473 ALSA connection change.
23:33:14.479 D-BUS: Service is available (org..service aka dbus).
23:33:14.537  connection change.
23:33:14.548 Client activated.

```

Other info
```

>lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

>d --version
dmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
dmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
dmp version 1.9.8 tmpdir /dev/shm protocol 8


>cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.24.

```

---

### Post by Redeen on 2012-08-18
Don't know if this will be much help, but check Jack/Setup.  Check to see if Jack is trying to get sound from onboard mic. Seem to be serious I/O setup issues with Studio 12.04 - I'm stuck, too.

---

