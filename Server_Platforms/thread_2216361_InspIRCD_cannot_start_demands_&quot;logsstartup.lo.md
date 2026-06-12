---
title: "InspIRCD cannot start: demands &quot;logs/startup.log&quot;"
date: 2014-04-11
forum: Server Platforms
---

### Post by BigBananaMan on 2014-04-11
EDIT:  The problem has been resolved by compiling the version of inspircd from the git repository and using the latest version of Ubuntu in the chroot jail.


Situation:
        After a week of dependency hell, syntax errors in source packages, etc.; I decided to install InspIRCD from the repo instead of compiling and encountered a show stopping error with exit status 5.
        I've googled the error message and got nothing relevant so I thought I'd check the plethora of wisdom here before taking the next step, punching irc in the face- erm punching it in the eth0.
        I have a feeling this is a bug in the software rather than configuration error and I'm going to end up moving on to Charybdis next.  Any ideas how to just bypass the file checks or force it to disregard errors and launch anyway?
        If else, just pointing me in the right direction should do it.

Relevant server info:
        Ubuntu 14.04 amd64(installed and updated last night) inside a chroot jail running on a headless Ubuntu 12.04 amd64 server updated April 9 (requesting restart, will be done 0300EST Sunday).
        InspIRCD version 2.0.5-1 binary at /usr/sbin
        All of the inspircd config files are set to irc:irc 660 and were written for inspircd 2.1 but are compatible with 2.0 unless I missed something.
        More info available if needed but pretty much everything in the chroot is stock 14.04.

Error message on stdout after running /etc/init.d/inspircd start: (no stderr output)
        "ERROR: Could not open initial logfile logs/startup.log: No such file or directory"

Log files specified in inspircd.conf:
        "/var/log/ircd-activity.log" and "/var/log/ircd-error.log"                    #I've searched all of my configs for "startup.log" and have not accidentally specified any other locations.
               

Modifications made to /etc/init.d/inspircd:
        #IRCDLOG="/var/log/inspircd.log"                                               #I disabled this "inspircd.log" (after the error) because it's wastefully redundant, I already specified how I want the logs written in inspircd.conf.
        #IRCDARGS="--logfile $IRCDLOG --config $IRCDCONF"
        IRCDARGS="--config $IRCDCONF"

Relevant strace output:
        ...
        open("logs/startup.log", O_RDWR|O_CREAT|O_APPEND, 0666) = -1 ENOENT (No such file or directory)
        fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
        mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fb140c53000
        write(1, "ERROR: Could not open initial lo"..., 83ERROR: Could not open initial logfile logs/startup.log: No such file or directory
        ) = 83
        close(3)                                = 0
        exit_group(5)                           = ?
        +++ exited with 5 +++

Workaround attempts:
        Tried mkdir/touching the file (irc:irc 660) at /var/log/startup.log
        mkdir/touching the file at /logs/startup.log
        mkdir/touching the file at /etc/logs/startup.log
        mkdir/touching the file at /usr/sbin/logs/startup.log   (Is "logs/" in relation to the binary, config, root?)
        Edited the line "USER="irc"" in /etc/init.d/inspircd to read "USER="root"" in the hopes that it will generate the file itself.
        /etc/init.d/inspircd force-reload
        Said something nasty.
        Brandished a knife.

Alternately, if anybody can suggest a better IRCD that actually works, that'll be a solution to the problem.  (IRCD-Hybrid has been disqualified as unworkable/expensive)

---

