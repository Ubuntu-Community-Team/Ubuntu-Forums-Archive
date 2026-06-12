---
title: "NMBD failing on boot and on command"
date: 2011-09-13
forum: Server Platforms
---

### Post by Freshhy on 2011-09-13
Hey everyone,
For some reason nmbd is failing to start on boot and also for:
```
sudo service nmbd start
```

I have tried:
```
sudo dpkg-reconfigure samba-common-bin
```
as has been referenced as a possible solution in a few bugs, but still get the same error.

/var/log/syslog states this:
```
init: nmbd pre-start process (1651) terminated with status 1
```

SMBD is running fine during boot and after.

Weirdly nmbd started on its own, after a day of the server being on and then after the server rebooted it failed to start again.

Cheers.

---

### Post by Freshhy on 2011-09-17
Anyone I have had no luck.

---

### Post by papibe on 2011-09-17
Could you post this file?
```
 /etc/init/nmbd.conf 
```
Regards.

---

### Post by ian dobson on 2011-09-17
Hi,

What do you see when you run nmbd directly from the command line as root?

 nmbd -i -S -F

On my box I see:-
nmbd version 3.5.8 started.
Copyright Andrew Tridgell and the Samba Team 1992-2010
Unknown parameter encountered: "refresh"
Ignoring unknown parameter "refresh"
Unknown parameter encountered: "otlocks"
Ignoring unknown parameter "otlocks"
Unknown parameter encountered: "refresh"
Ignoring unknown parameter "refresh"
Unknown parameter encountered: "otlocks"
Ignoring unknown parameter "otlocks"
standard input is not a socket, assuming -D option
bind failed on port 137 socket_addr = 255.255.255.2.
Error = Cannot assign requested address
nmbd_subnetdb:make_subnet()
  Failed to open nmb bcast socket on interface 255.255.255.2 for port 137.  Error was Cannot assign requested address
ERROR: Failed when creating subnet lists. Exiting.

and it doesn't run in deamon or interactive mode.

Regards
Ian Dobson

---

### Post by Freshhy on 2011-09-17
Thanks for your replies.

Contents of nmbd.conf
```
description "NetBIOS name server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

pre-start script
        [ -f /etc/samba/smb.conf ] || { stop; exit 0; }

        install -o root -g root -m 755 -d /var/run/samba
        NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null`

        [ "x$NMBD_DISABLED" = xYes ] && { stop; exit 0; }

        exit 0
end script

exec nmbd -D

```

And the output of nmbd -i -S -F

```
nmbd version 3.5.8 started.
Copyright Andrew Tridgell and the Samba Team 1992-2010
standard input is not a socket, assuming -D option
started asyncdns process 4848
```

Thanks. This seemed to get nmbd to start. But how do I get it to start on boot?

---

### Post by papibe on 2011-09-17
Try this:

First backup your conf file:
```
$ sudo cp /etc/init/nmbd.conf /etc/init/nmbd.conf,old
```
Then edit the file and replace this line:
```
start on (local-filesystems and net-device-up IFACE!=lo)
```
For this one:
```
start on (local-filesystems)
```
Save the file and try restarting the service again.

Hope it helps,
Regards.

P.D.: this launchpad [bug]("https://bugs.launchpad.net/null/+bug/582376") is my reference.

---

