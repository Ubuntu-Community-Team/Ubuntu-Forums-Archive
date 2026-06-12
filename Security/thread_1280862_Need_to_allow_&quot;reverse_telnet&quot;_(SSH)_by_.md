---
title: "Need to allow &quot;reverse telnet&quot; (SSH) by untrusted user to USB tty."
date: 2009-10-02
forum: Security
---

### Post by MobileTech on 2009-10-02
I have found many references on how to do this with a Cisco router as the SSH host, but I need to enable a remote user to connect to a non-functioning Cisco router, not connect to a UNIX console through a functioning router.

I work for a sub-contractor on this island and from time to time get router service calls from (phone company A) where I go to some server room and connect my netbook (Kubuntu 9.04) to the console port on the router and talk on the phone with their IT people relaying information and settings back and forth. In these situations the internet to the router is down. I would like to be able to jack in and tell the remote tech OK, SSH to (my 3G IP) as user x with password xx, and let them log in directly to the router, without access to my system (ie no minicom or can't exit minicom or see any local files). It would also be handy if I could see and interact with what's going on via a Konsole window.

Does anyone know how to do this?

---

### Post by Lars Noodén on 2009-10-02
Try looking at the ProxyCommand option for SSH and the ForceCommand+ChrootDirectory options for SSHd.

---

### Post by Rob_H on 2009-10-02
How are you making the connection tp the router over USB? What protocol/program? If it's some kind of TCP/IP connection, you might be able to use the port forwarding features of SSH to bridge the remote technician's machine to the router. And by creating a specific user account for this on your Kubuntu box, you can lock down access to anything on the netbook with chroot and so forth.

Alternatively, you might want to consider a desktop sharing tool, especially if you want to watch what's happening.

---

### Post by MobileTech on 2009-10-02
> **Rob_H said:**
> How are you making the connection tp the router over USB? What protocol/program? If it's some kind of TCP/IP connection...

Cisco Routers use RS-232  on the console port. It is a serial console. Hence my mention of minicom and usb tty.

---

### Post by Rob_H on 2009-10-02
> **MobileTech said:**
> Cisco Routers use RS-232  on the console port. It is a serial console. Hence my mention of minicom and usb tty.

Then +1 for Lars' suggestion.

---

### Post by Lars Noodén on 2009-10-03
You can use **tee** to capture the output in a log file and use **tail** to watch it real time as the consultant works.  

The guest user is a member of the group cconsult.  The serial connection for my test is on device ttyUSB0, which is a USB to serial converter.  

From sshd_config
```

Match Group cconsult
   ChrootDirectory /var/chroot-test
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand cu -s 19200 -l /dev/ttyUSB0 | tee /var/tmp/cu.log

```

When the consultant is logged in then you can follow along: **sudo tail -f /var/chroot-test/var/tmp/cu.log**

The consultant's login shell is set to /bin/rbash, so cu above cannot have the full path.  

The real bite was making /dev for the chroot environment.  I guess use of **lsof** can show which devices are needed.  I eventually tar'ed the existing /dev into the chroot environment.  

Here are the directories minus dev:
[indent]
drwxr-xr-x 2 root root 4096 2009-10-03 22:05 ./bin
drwxr-xr-x 2 root root 4096 2009-10-03 21:54 ./lib
drwxr-xr-x 2 root root 4096 2009-10-03 19:54 ./lib64
drwxr-xr-x 3 root root 4096 2009-10-03 19:54 ./usr
drwxr-xr-x 2 root root 4096 2009-10-03 22:18 ./usr/bin
drwxr-xr-x 4 root root 4096 2009-10-03 22:10 ./var
drwxrwxrwt 2 root root 4096 2009-10-03 22:18 ./var/lock
drwxrwxrwt 2 root root 4096 2009-10-03 22:15 ./var/tmp
[/indent]

Note:
lock and tmp need weird permissions.
The group will need write permission to the serial device, in this example it is ttyUSB0:

[indent]
chgrp cconsult dev/ttyUSB0
[/indent]

There are three executables needed for the above setup:
[indent]
/bin/rbash
/usr/bin/cu
/usr/bin/tee
[/indent]

Note: 
 In a regular system, rbash is a symlink to bash.
 In a regular system lib64 is a symlink to lib.

**ldd** tells us that the following libraries are needed:

[indent]
/lib/libnsl.so.1
/lib/libncurses.so.5
/lib/libdl.so.2
/lib/libc.so.6
/lib64/ld-linux-x86-64.so.2
[/indent]

Was that the kind of set up you were looking for?

---

### Post by MobileTech on 2009-12-02
> **Lars Noodén said:**
> 
Was that the kind of set up you were looking for?

Awesome, that was exactly what I was looking for! (well, except for the lib64... my netbook is 32 bit)

---

### Post by Lars Noodén on 2009-12-04
Excellent.  

Since writing that, I also was reminded that it is possible to do tricks with [screen](http://manpages.ubuntu.com/manpages/karmic/en/man1/screen.1.html) or [tmux](http://www.openbsd.org/cgi-bin/man.cgi?query=tmux) to attach two users to the same session.  That would allow you both to type, if that would be useful.   Both log in to the same account and then try to attach to an existing session

Make a script, such as /usr/local/bin/screeners:
```

#!/bin/sh

# try attaching to an existing screen session or,
# or if none exist, make a new screen session

/usr/bin/**screen** -x || \
  /usr/bin/**screen** \
     sh -c "/usr/bin/**cu** -s 19200 -l /dev/ttyUSB0 **|** \
     /usr/bin/**tee** /tmp/consultant.log"

```

Then use that script as the **ForceCommand**

---

