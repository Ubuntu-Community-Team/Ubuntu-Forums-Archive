---
title: "VMware Console error"
date: 2008-12-18
forum: Virtualisation
---

### Post by quikone8 on 2008-12-18
I have my Server running and am able to access the console but the Power up button reports an error.  I assume that it has something to do with a serial number???  Anyway I have tried to enter a serial number, but it reports back that I do not have the permission to enter a serial number and that I must be using an adimn account.  I launch the program in a gnome enviroment.  Am I doing something wrong?  Can I launch the program in terminal?  Is that the real problem?

---

### Post by quikone8 on 2008-12-18
bump

---

### Post by Dedoimedo on 2008-12-19
Try starting the server with sudo vmware-server on the command line. Likewise, if you can post the exact errors you receive, it would be nice. You will have to start from the command line, f course.

And later on, if you want to deep-debug, you can also run strace against the vmware-server binary. But first, try sudo.

Dedoimedo

---

