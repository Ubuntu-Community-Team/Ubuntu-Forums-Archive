---
title: "UNR 9.10 + Jack/Ubuntu Studio Controls it doesnt work"
date: 2010-03-05
forum: Ubuntu Studio
---

### Post by pc999 on 2010-03-05
Hi,

I instaled UNR on my netbook (generic Atom based) and then instaled Ubuntu Studio Controls, then jack and a few audio apps.

But when I try to get jack started, I do launch it and click on star but I get a error

> 
 p, li { white-space: pre-wrap; }  Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.

and in the mensage window

> 
 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:18:46.624 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:18:46.637 Statistics reset.[/COLOR]
 [COLOR=#66cc99]13:18:46.918 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]13:18:47.422 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:18:51.239 Startup script...[/COLOR]
 [COLOR=#990099]13:18:51.241 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]13:18:51.650 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]13:18:51.651 JACK is starting...[/COLOR]
 [COLOR=#990099]13:18:51.652 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]13:18:51.657 JACK was started with PID=2547.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1215994176, from thread -1215994176] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]13:18:52.456 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]13:18:52.457 Post-shutdown script...[/COLOR]
 [COLOR=#990099]13:18:52.458 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]13:18:52.927 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]13:18:53.746 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

I did not alter anything yet, it is a fresh install, but I am quite ready to start producing and meybe even recording on linux.

Any help would be great.

Thanks.

---

### Post by AutoStatic on 2010-03-05
Untick the 'Realtime' option in QjackCtl or modify your */etc/security/limits.conf* file: [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)
Ubuntu Studio Controls contains a bug and doesn't write the correct settings to */etc/security/limits.conf*

---

### Post by pc999 on 2010-03-05
> **AutoStatic said:**
> Untick the 'Realtime' option in QjackCtl or modify your */etc/security/limits.conf* file: [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)
Ubuntu Studio Controls contains a bug and doesn't write the correct settings to */etc/security/limits.conf*


Thanks the untick the Realtime option worked.

I tried (or at least I think I tried :lol: , not really a Linux guy, at least yet), should I report a it as a bug?

Thanks again for your help.

---

### Post by AutoStatic on 2010-03-05
> **pc999 said:**
> Thanks the untick the Realtime option worked.You're welcome, welcome aboard ;)

> **pc999 said:**
> I tried (or at least I think I tried :lol: , not really a Linux guy, at least yet), should I report a it as a bug?This bug has already been reported: [https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082](https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082)

---

### Post by pc999 on 2010-03-05
> **AutoStatic said:**
> You're welcome, welcome aboard ;)

This bug has already been reported: [https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082](https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082)


Sorry wrote it in a worry, I meant that I tried the modify/command thing. But it didnt worked. Dont know if I did it wrong or if it just didnt worked.

Should I report it as a bug?

Thanks.

---

### Post by AutoStatic on 2010-03-05
Could you post the contents of your */etc/security/limits.conf* file?

---

### Post by pc999 on 2010-03-06
> **AutoStatic said:**
> Could you post the contents of your */etc/security/limits.conf* file?

This?

> # /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file
@audio - rtprio 99
@audio - nice -10
@audio - memlock unlimited
@audio - rtprio 99

---

### Post by AutoStatic on 2010-03-06
> **pc999 said:**
> This?Yup :)

You can take out the last *@audio - rtprio 99* line and the *@audio - nice -10* line. And could you also post the outcome of the **groups** command? If it doesn't show the group 'audio' you will have to add your account to that group (System - Administration - Users and Groups).

---

