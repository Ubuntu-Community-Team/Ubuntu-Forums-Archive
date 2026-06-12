---
title: "What is core.1xxxx files at / ?"
date: 2010-01-25
forum: Server Platforms
---

### Post by Kemon on 2010-01-25
I have a VPS with Ubuntu 8.10 64bit and I was looking at / and found like 10.000 files from "core.1000" to "core.10000".

What is that? Something I can delete or it is a application that I have installed?

Some of the files at "/":
-rw-------  1 root root   5435392 Jan 15 10:00 core.5755
-rw-------  1 root root   5562368 Dec 14 16:39 core.5757
-rw-------  1 root root   5160960 Dec 22 08:40 core.5758
-rw-------  1 root root   5431296 Dec 26 05:09 core.5759
-rw-------  1 root root   5632000 Nov 18 14:00 core.5764
-rw-------  1 root root   5570560 Dec 15 02:17 core.5766
-rw-------  1 root root   5419008 Dec 25 02:17 core.5768

---

### Post by Xianath on 2010-01-25
Core files are memory dumps of crashed programs. The number is the process ID (PID). These are useful to developers of the program or others who would like to debug the crash. 

Something's crashing on your box that you don't know about. See what program generated them, the "file" utility should be able to tell you that (and if not, gdb can). Let's take it from there.

Cheers,
Peter

---

### Post by Kemon on 2010-01-25
This is what I got when I wrote: file core.10000

core.10000: ELF 64-bit LSB core file x86-64, version 1 (SYSV), SVR4-style, from '/usr/sbin/console-kit-daemon'

Any idè what this is?

---

### Post by Xianath on 2010-01-25
Please have a look at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/196724") and let us know whether you're seeing the same error messages.

One thing I'm wondering is, you're not running the LTS but you're still two versions behind, have you considered upgrading to the latest stable release?

Regards,
Peter

---

### Post by Kemon on 2010-01-25
I have bought that VPS form a service since I have a crapy internet.

But.....

* I restored the server and started form the beginning.
* Updated the system as sudo.
* Created an account for myself.
* Added my user as sudo.
* Server reboot.
* Logged in with my new account.
* Installed mysql-server php5 php5-mysql php5-mcrypt
* Made some subdomains.
* Server reboot.
* Made a script for ventrilo(.com) at /home/USER/.sh/vt.sh:
```
#! /bin/bash
cd /home/kemon/ventsrv
./ventrilo_srv -d
```
* Installed ia32-libs (had a problem to run vent servere before so I found out what I had to install to get it work)
* Added 'sh /home/USER/.sh/vt.sh' to '/etc/rc.local' (vent server starts when the server have to reboot or something)

[COLOR="Silver"]But.... Around here I saw the core.xxxxx files started to get back! Tryed to shutdown the vent server, but they still come.[/COLOR]

Edit: ia32-libs is the problem!! But I really want to run vent on my server.

Can it be fixed?


Thanks for help!

---

### Post by Kemon on 2010-01-26
Is there any way that I can get it to work with 32bit ventrilo on 64bit ubuntu?

---

