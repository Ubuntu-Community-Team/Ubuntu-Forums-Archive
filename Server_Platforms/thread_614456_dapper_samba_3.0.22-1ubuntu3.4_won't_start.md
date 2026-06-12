---
title: "dapper samba 3.0.22-1ubuntu3.4 won't start"
date: 2007-11-16
forum: Server Platforms
---

### Post by dmizer on 2007-11-16
I have a dapper samba server set up and hosting a drive to a small office.

today i installed some security patches via apt.  during the apt process the winbind and samba daemons are restarted, but they fail to start, and get stuck in process, hanging at:
```
Setting up samba (3.0.22-1ubuntu3.4) ...
 * Starting Samba daemons...
```
samba never starts (it's been working flawlessly for over a year).

checking the logs in /var/log for both the linux kernel, and the samba daemon indicate that the daemon was started without error, but ps -A does not show samba.

restarting the server allows samba to start, but then there are dpkg problems with an interrupted package install.
```
dpkg: error processing samba (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 samba
```

not too sure how to resolve this one.

---

### Post by jtc on 2007-11-16
I've also got some trouble with the latest samba upgrade in Dapper.

Now nmbd segfaults/panics when you (try to) start it.

Here is a debug-output

> 
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1211853120 (LWP 8743)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ddb933 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d853c9 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#3  0x080cc403 in smb_panic2 (
    why=0xfffffe00 <Address 0xfffffe00 out of bounds>, decrement_pid_count=1)
    at lib/util.c:1545
#4  0x080cc525 in smb_panic (why=0xfffffe00 <Address 0xfffffe00 out of bounds>)
    at lib/util.c:1506
#5  0x080b8624 in push_ascii (dest=0xfffffe00, 
    src=0x818e1e0 "hornburg (Midgard)", dest_len=4294967295, flags=5)
    at lib/charcnv.c:844
#6  0x08073c63 in send_announcement (subrec=0x812da20, 
    announce_type=<value optimized out>, from_name=0x818e0dc "HORNBURG", 
    to_name=0x0, to_type=0, to_ip={s_addr = 0}, announce_interval=-1079002516, 
    server_name=0xfffffe00 <Address 0xfffffe00 out of bounds>, 
    server_type=105003, 
    server_comment=0xfffffe00 <Address 0xfffffe00 out of bounds>)
    at nmbd/nmbd_sendannounce.c:119
#7  0x08073e2a in send_host_announcement (subrec=0x812da20, work=0x812de98, 
    servrec=0x818e0d0) at nmbd/nmbd_sendannounce.c:210
#8  0x08074167 in announce_my_server_names (t=1195204350)
    at nmbd/nmbd_sendannounce.c:257
#9  0x08062b7d in main (argc=-512, argv=0xbfafc104) at nmbd/nmbd.c:449


(Doesn't say me much thought.)

---

### Post by ahobbs on 2007-11-17
I'm getting the same problem with Dapper (6.06) and Samba 3.0.22.  Mine had also been working flawlessly for almost a year until it automatically upgraded last night. :(

It's been so long since I've had to play with the Linux box (I use it only as a file and print server), that I'm really rusty on all the config files -- but it appears as though everything is working normally except for Samba.  A couple of oddities:

[LIST=1]
[*]When I reboot the computer or restart samba (sudo /etc/init.d/samba restart), I get this warning: "start-stop daemon: warning: failed to kill <number>: No such process"

[*]testparm gives the following warning: "WARNING: passdb expand explicit = yes is deprecated"
[/LIST]

I can post the dump of smb.conf service definitions if it would help diagnose the problem.  I'm running a really light server version of Dapper with Fluxbox as the desktop manager.  I might try to download the latest version of Samba 3.0.27 from Samba.org, but don't wan't to introduce any new problems...

Thanks for any insights!

---

### Post by ahobbs on 2007-11-17
SOLVED

Had to downgrade back to samba 3.0.22-1ubuntu3.3.

> $ aptget install samba=3.0.22-1ubuntu3.3

When it prompts to use current solution, use "." (period followed by enter) to go to the next solution -- 3rd one is to downgrade.

> $ aptget forbid-version samba=3.0.22-1ubuntu3.4

Don't want to install that one again!

Thanks to other posters -- [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042)

---

### Post by dmizer on 2007-11-18
thank you ahobbs ... the update has been fixed, but my main server got stuck with the bad update and it wouldn't correct itself.  your solution got me back online.  thank you.

---

