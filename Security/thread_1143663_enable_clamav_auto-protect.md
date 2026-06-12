---
title: "enable clamav auto-protect"
date: 2009-04-30
forum: Security
---

### Post by hallve_revera on 2009-04-30
hii... im newbie in linux and have a lil question here
i need to know how to use clamav as a auto-protect antivirus in my ubuntu just like in windows
thank in advance

---

### Post by khelben1979 on 2009-04-30
If you really feel that you need this, then [check out this webpage]("http://code.google.com/p/clamav-cron/").

I only scan my system sometimes when I'm going to share files to other Windows systems, since a Linux system can obtain Windows viruses, but they never causes any damage to the Linux system itself.

---

### Post by hallve_revera on 2009-05-02
noo...
i mean how to use clamdscan as daemon

---

### Post by cariboo on 2009-05-02
The clamav documentation is available [here]("http://www.clamav.net/doc/latest/"), go to page 11, there are instructions on how to setup on access scanning. It is a little to involved to tell you how to do it here.

---

### Post by hallve_revera on 2009-05-04
do i have to install the dazuko program for the clamd to running in my system
i got an error when i tried to compiled it...???
i installed the clamav from synaptic...
is there any side effect from installing in synaptic..??

do i need to compile it from source..???

i have a problem when tried to compiled it.. i can't find the zlib and zlib-devel packages... any idea...?????

thanks:guitar:

---

### Post by cariboo on 2009-05-04
Have you got build-essential installed? Zlibc and zlibc1g-dev are available in the repositories, as well as build-essential

---

### Post by hallve_revera on 2009-05-05
forget about compiling..
i still need help to get clamd working in my ubuntu..
what should i do in the first time when i installed it from synaptic


thanks for your answer

---

### Post by hallve_revera on 2009-05-07
any help plz
this what i got when tryinng to ru "sudo clamd"

ERROR: LOCAL: Socket file /var/run/clamav/clamd.ctl is in use by another process.



any help with this error
thanks

---

### Post by cariboo on 2009-05-07
Once you install clamav, you should have to do anything but scan driectories for viruses. To do a scan open a terminal and type:

```
clamscan -r/CODE]

this will scan your home directory recursively. TO get daily updates, in a terminal type:

[CODE]sudo freshclam
```

this will create a cron job that will check for updates daily.

For more scan options, check:

```
man clamscan
```

---

