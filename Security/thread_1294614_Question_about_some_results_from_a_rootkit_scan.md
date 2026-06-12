---
title: "Question about some results from a rootkit scan"
date: 2009-10-18
forum: Security
---

### Post by BigCityCat on 2009-10-18
Probably nothing but was wondering how to interpret results. Here is the summary from the scan, and then a section from the scan. I am using Karmic.

> System checks summary
=====================

File properties checks...
    Files checked: 128
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 111
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 4 minutes and 8 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)




> 
14:53:35] /usr/sbin/unhide                                  [ Warning ]
[14:53:35] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[14:53:35] /usr/sbin/useradd                                 [ OK ]
[14:53:36] /usr/sbin/userdel                                 [ OK ]
[14:53:36] /usr/sbin/usermod                                 [ OK ]
[14:53:36] /usr/sbin/vipw                                    [ OK ]
[14:53:37] /usr/sbin/unhide-linux26                          [ Warning ]
[14:53:37] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file

---

### Post by cariboo on 2009-10-18
/usr/sbin/unhide and /usr/sbin//unhide-linux26 are installed as dependencies of rkhunter. You can effectively ignore the warnings. You can update rkhunter's database so that the warnings won't show up. I don't have rkhunter installed, so you'll have to check the manpage on how to run the update.

```
man rkhunter
```

---

### Post by BigCityCat on 2009-10-18
Okay thanks a lot.

---

