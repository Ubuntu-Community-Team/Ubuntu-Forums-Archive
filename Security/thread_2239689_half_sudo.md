---
title: "half sudo"
date: 2014-08-15
forum: Security
---

### Post by fkkroundabout on 2014-08-15
say there's a program or a package that you have to install, but sudo seems like it just gives complete and total permissions to it. is there not something equivalent to half-sudo or something ? perhaps so a program could read system files but not write to them, for example

---

### Post by TheFu on 2014-08-15
Doing an install - well, that is a SYSTEM-LEVEL permissions thing - unless you force the install to be to your HOME.  It is possible to extremely limit the exact options that any user can use with any program. m**an sudoers** is really complete and easy to understand (assuming the correct background knowledge).

To understand UNIX group and file permissions, "ubuntu permissions" is the term to google.

After a program is installed on the system, you can manage permissions to many of them by controlling the group and/or removing "other" execute permissions.  Sometimes it may be easier to place users to be blocked, then remove g+x permissions.  
For programs that work using a network port - there isn't anything I know outside of the program's user-permissions management to address that.

UNIX file and directory permissions have elegant solutions for almost every need.  When they fail, use ACLs - but I avoid ACLs since they are easy to forget about and can royally screw a day of troubleshooting. I know that I've been burned at least a few times. ;)

---

### Post by ian-weisser on 2014-08-16
> **fkkroundabout said:**
> sudo seems like it just gives complete and total permissions to it.

An example would help.
If an application has incorrect permissions, runs as root when it shouldn't, or behaves improperly with your data, please file a bug report.
We don't put up with misbehaving applications.

---

