---
title: "How to tell if this is a false positive..."
date: 2008-01-20
forum: Server Platforms
---

### Post by kameleon25 on 2008-01-20
The other day I noticed when I ran "ls" on my Ubuntu 7.10 server I got this:ls
ls: unrecognized prefix: do
ls: unparsable value for LS_COLORS environment variable
So I started digging and found a few places that stated this could be due to a rootkit being installed. This is my web server running ISPConfig and only the bare minimum ports have ever been open to let it run. So once I heard/read it could have been a rootkit I immediately installed chkrootkit and rkhunter. Here is the part of the rkhunter output that bothers me (I cut the OK parts):
```
    /bin/ls                                                  [ Warning ]
    /bin/netstat                                             [ Warning ]
    /bin/ps                                                  [ Warning ]
    /usr/bin/find                                            [ Warning ]
    /usr/bin/md5sum                                          [ Warning ]
    /usr/bin/pstree                                          [ Warning ]
    /usr/bin/top                                             [ Warning ]
    /sbin/ifconfig                                           [ Warning ]
    SHV4 Rootkit                                             [ Warning ]
    SHV5 Rootkit                                             [ Warning ]
    Checking for hidden files and directories                [ Warning ]

System checks summary
=====================

File properties checks...
    Files checked: 123
    Suspect files: 8

Rootkit checks...
    Rootkits checked : 110
    Possible rootkits: 2
    Rootkit names    : SHV4 Rootkit, SHV5 Rootkit

Applications checks...
    Applications checked: 8
    Suspect applications: 0
```

Any ideas on what to check specifically to see if i have been rooted? Everywhere I find when I search google just says format and reinstall. But I don't want to do that unless I have been infected. 

Thanks in advance for any and all help.

---

### Post by Vinno on 2008-01-20
At first thought, i thought it might be a color error with .bashrc file but have you install anything lately that modified the /bin/ls??

Seems very sus indeed. I would lean against the format too.

What kind of php/cgi scripts you serving from your webserver, check out if they are the latest version and any know exploits.

---

### Post by kameleon25 on 2008-01-21
All I have running thus far is a wordpress site and a gallery2 site. The wordpress is the only one that was installed before this began. I guess I could restore to a backup and just see if that does it. I am also setting up remote logging of all my machines so next time I will have a better idea of when something happened. 

Thank you for the input.

---

### Post by kameleon25 on 2008-01-21
Just as an update:

I decided to try unset LS_COLORS and the error on ls went away and color returned. So I did a little digging an ran the md5sum on ls on this machine and a few other ubuntu 7.10 machines I have. They all returned the same md5sum EXCEPT the one that I believe to be root'd. So I wil lbe backing up my database and restoring the filesystem from backup.

---

