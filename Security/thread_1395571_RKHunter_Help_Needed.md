---
title: "RKHunter Help Needed"
date: 2010-02-01
forum: Security
---

### Post by Dalek Draco ON LINUX on 2010-02-01
[FONT=Arial Black][SIZE=2]I've run RKHunter (after updated to latest version) and it came up with the usual:
 /usr/bin/awk                                             [ Warning ]
 /usr/bin/last                                            [ Warning ]
 /usr/bin/ldd                                             [ Warning ]
 /usr/bin/gawk                                            [ Warning ]
 /sbin/init                                               [ Warning ]
 /sbin/runlevel                                           [ Warning ]
 /sbin/sulogin                                            [ Warning ]
 /usr/sbin/rsyslogd                                       [ Warning ]
 /usr/sbin/unhide                                         [ Warning ]
 /usr/sbin/unhide-linux26                                 [ Warning]

Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]

Checking application versions...

    Checking version of Exim MTA                             [ Warning ]
    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]


I've read a little and I assume that these are false positives. 

However it also found:

Checking for TCP port 60922                              [ Warning ]

Which has not come up before. I'm guessing it has something to do with my network...thus I am a little worried. 


Any help/ideas would be appreciated. Thanks.
[/SIZE][/FONT]

---

### Post by unspawn on 2010-02-01
> **Dalek Draco ON LINUX said:**
> I assume that these are false positives. 
The logfile will show you more details than the display output. Regardless there is no reason to assume when you possess the (RKH docs and) common GNU/Linux tools to ensure these are false positives. 


> **Dalek Draco ON LINUX said:**
> Checking for TCP port 60922 [ Warning ] Which has not come up before. I'm guessing it has something to do with my network
TCP/60922 is a port a component of the zaRwT rootkit listens on. If you have verified one of the services you provide legitimately uses the port (see 'lsof -Pwni tcp:60922', 'fuser -n tcp 60922' or the convoluted 'netstat -antple|grep 60922') then you can whitelist it. See examples in rkhunter.conf, the documentation and the rkhunter-users mailing list archives for more details.

---

### Post by Dalek Draco ON LINUX on 2010-02-02
Thanks for replying.  Looks like the port was being used by a legit program. When I run a scan and it's not in use, the warning does not pop up.

---

