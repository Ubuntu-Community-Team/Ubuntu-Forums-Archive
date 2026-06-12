---
title: "/etc/security/limits.conf can only be deceased and not increased??"
date: 2021-11-12
forum: Server Platforms
---

### Post by philpug on 2021-11-12
Hi,

I'd like to make the below changes to my ubuntu server. 

It seems if I change the /etc/security/limits.conf file to match this it doesn't take affect. 

I can reduce the defaults using the limits.conf but I can't increase them.

What am I doing wrong here?

What do I need to change to be able to increase these limits?


[TABLE="class: tableblock frame-all grid-all stretch, width: 964"]
[TR]
[TH="class: halign-left valign-top, align: left"]Parameter[/TH]
[TH="class: halign-left valign-top, align: left"]Description[/TH]
[TH="class: halign-left valign-top, align: left"]Setting[/TH]
[/TR]
[TR]
[TD="class: halign-left valign-top"]nofile
[/TD]
[TD="class: halign-left valign-top"]The number of files the host OS can keep open at once.
[/TD]
[TD="class: halign-left valign-top"]65536
[/TD]
[/TR]
[TR]
[TD="class: halign-left valign-top"]nproc
[/TD]
[TD="class: halign-left valign-top"]The number of processes the OS can run simultaneously.
[/TD]
[TD="class: halign-left valign-top"]65536
[/TD]
[/TR]
[TR]
[TD="class: halign-left valign-top"]memlock (soft)
[/TD]
[TD="class: halign-left valign-top"]The maximum locked-in address space a particular user can allocate. Once allocated, the pages stay in physical memory, which speeds up operations on the ledger database. The soft limit applies to the owner of the process, which will be radixdlt in our case.
[/TD]
[TD="class: halign-left valign-top"]unlimited
[/TD]
[/TR]
[TR]
[TD="class: halign-left valign-top"]memlock (hard)
[/TD]
[TD="class: halign-left valign-top"]The maximum locked-in address space that can allocated on the OS as a whole. This value can only be set by the root user. Any soft memlock cannot exceed the value of the hard memlock.
[/TD]
[TD="class: halign-left valign-top"]unlimited
[/TD]
[/TR]
[/TABLE]

---

### Post by Doug S on 2021-11-12
It is not clear what you are doing wrong. Post your /etc/security/limits.conf file.

---

### Post by MAFoElffen on 2021-11-12
Doug S is right in that no one has any idea what your limits.conf file looks like to see if you might have syntax errors or anything commented out...

And: Are you rebooting the server after you change the limits.conf file to pick up the changes?

I'm thinking that your file probably looks something similar to (but just guessing what yours looks like):
```

#/etc/security/limits.conf
#
# Notes:
#   - Restart Server for limits to take effect...
#   - Using a high number (greater than ~20000) for soft and hard nproc may cause 
#     system instability and hangs on Centos 7, though not on Ubuntu 18, 19, and 20.
#   - Check current limits: cat /proc/PID/limits
#
#<domain>      <type>  <item>         <value>
#
root           hard    nofile         65536
root           hard    nproc          65536
radixdlt       soft    memlock        unlimited
root           hard    memlock        unlimited

# End of file

```

I have used 'unlimited" to stress test servers and see just where they fail/crash...
```

# /etc/security/limits.conf
# To Stress Test Servers
# Check limits:
#    cat /proc/PID/limits

*        -      core         unlimited
root     -      core         unlimited
*        -      data         unlimited
root     -      data         unlimited
*        -      fsize        unlimited
root     -      fsize        unlimited
*        -      memlock      unlimited
root     -      memlock      unlimited
*        -      nofile       1048576
root     -      nofile       1048576
*        -      rss          unlimited
root     -      rss          unlimited
*        -      stack        unlimited
root     -      stack        unlimited
*        -      cpu          unlimited
root     -      cpu          unlimited
*        -      nproc        unlimited
root     -      nproc        unlimited
*        -      as           unlimited
root     -      as           unlimited
*        -      maxlogins    unlimited
root     -      maxlogins    unlimited
*        -      maxsyslogins unlimited
root     -      maxsyslogins unlimited
*        -      locks        unlimited
root     -      locks        unlimited
*        -      sigpending   unlimited
root     -      sigpending   unlimited
*        -      msgqueue     unlimited
root     -      msgqueue     unlimited

# End Of File


```
Then verify as logged in as a specific user also with 
```

ulimit -Sa
ulimit -Ha

```
and test with this recursive function
```
:(){ :|:& };:

```

---

### Post by philpug on 2021-11-13
Actually it looks like just the hard limit is changing. Just testing on another machine with the phil user and only trying to change the nofile parameter. I get the following.

```

#/etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain> <type> <item> <value>
#
root hard nofile 2048
root soft nofile 2048
phil - nofile 65536

# End of file
```

```


ulimit -Sa


core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 30756
max locked memory       (kbytes, -l) 65536
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 30756
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

```

ulimit -Ha

core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 30756
max locked memory       (kbytes, -l) 65536
max memory size         (kbytes, -m) unlimited
open files                      (-n) 65536
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) unlimited
cpu time               (seconds, -t) unlimited
max user processes              (-u) 30756
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```


Is there something I need to do to enforce the change to the soft limits as well?

---

### Post by philpug on 2021-11-13
I'm not sure if there was a type of something somewhere but I managed to get everything working as expected now. Thanks for your help.

---

### Post by MAFoElffen on 2021-11-13
Just another "factor" to consider...

If you expect a user or group to get a certain limit, and and they were restricted at less than you expected... It is first come. first serve. ...and... If a value is not valid, it will be ignored. 

On getting a lower limit, or being restricted at a lower level than expected... The promise, if valid is: If an entities limit value is high, they can "possibly" get up to that limit "in a perfect world." But that world, that slice of the pie, is effected by what it left from current users, groups and the OS (root) in that point of time. They can only possibly have a slice (access) to what is "left" of the pie. 
> Is there something I need to do to enforce the change to the soft limits as well? 				

On soft and hard limits... Hard limits are "Here is the boundary." Soft limits are somewhat like "suggestions" You said "enforce..." But soft limits can be temporarily changed by a non-root user or application up to the limit of the hard limit.
> 
The getrlimit and setrlimit system calls **allow a process to read and set limits on the system resources that it can consume**. ... The soft limit may never exceed the hard limit, and only processes with superuser privilege may change the hard limit...

But most user's do not know that they can or how to adjust those soft limits on their own, so...

***
So this is solved for you now?

---

### Post by TheFu on 2021-11-13
Please use the "thread tools" button and mark this thread as SOLVED to help community members not waste time.

---

### Post by LHammonds on 2021-11-16
> **philpug said:**
> Hi,

I'd like to make the below changes to my ubuntu server. 

It seems if I change the /etc/security/limits.conf file to match this it doesn't take affect. 

I can reduce the defaults using the limits.conf but I can't increase them.

What am I doing wrong here?

What do I need to change to be able to increase these limits?


[TABLE="class: tableblock frame-all grid-all stretch, width: 964"]
[TR]
[TH="class: halign-left valign-top, align: left"]Parameter[/TH]
[TH="class: halign-left valign-top, align: left"]Description[/TH]
[TH="class: halign-left valign-top, align: left"]Setting[/TH]
[/TR]
[TR]
[TD="class: halign-left valign-top"]nofile[/TD]
[TD="class: halign-left valign-top"]The number of files the host OS can keep open at once.[/TD]
[TD="class: halign-left valign-top"]65536[/TD]
[/TR]
[TR]
[TD="class: halign-left valign-top"]nproc[/TD]
[TD="class: halign-left valign-top"]The number of processes the OS can run simultaneously.[/TD]
[TD="class: halign-left valign-top"]65536[/TD]
[/TR]
[TR]
[TD="class: halign-left valign-top"]memlock (soft)[/TD]
[TD="class: halign-left valign-top"]The maximum locked-in address space a particular user can allocate. Once allocated, the pages stay in physical memory, which speeds up operations on the ledger database. The soft limit applies to the owner of the process, which will be radixdlt in our case.[/TD]
[TD="class: halign-left valign-top"]unlimited[/TD]
[/TR]
[TR]
[TD="class: halign-left valign-top"]memlock (hard)[/TD]
[TD="class: halign-left valign-top"]The maximum locked-in address space that can allocated on the OS as a whole. This value can only be set by the root user. Any soft memlock cannot exceed the value of the hard memlock.[/TD]
[TD="class: halign-left valign-top"]unlimited[/TD]
[/TR]
[/TABLE]


Rather than make changes system-wide, you could apply them to a specific process.  For example, I run a game server that touches a LOT of files due to how they designed their file system (lose files instead of packed file) so most tutorial talk about modifying the limits of the entire system.

However, I run the engine as a systemd service and as such, I specified the limit inside the systemd configuration which worked perfectly.

Example:  /lib/systemd/system/arkservice\@.service

```

[Unit]
Description=ARK: %i
Wants=network-online.target
After=syslog.target network.target nss-lookup.target network-online.target
[Service]
Type=simple
Restart=on-failure
RestartSec=30
StartLimitInterval=180s
StartLimitBurst=3
KillMode=control-group
KillSignal=SIGQUIT
SendSIGHUP=no
SendSIGKILL=yes
FinalKillSignal=SIGKILL
RuntimeMaxSec=infinity
[COLOR=#ff0000]LimitNOFILE=100000[/COLOR]
#ExecStartPre=/opt/ark/scripts/game-sync-1.sh %i
TimeoutStartSec=180
ExecStart=/opt/ark/scripts/game-start.sh %i
ExecReload=
TimeoutStopSec=120
ExecStop=/opt/ark/scripts/game-stop.sh %i
User=arkservice
Group=arkserver
[Install]
WantedBy=multi-user.target
```

LHammonds

---

