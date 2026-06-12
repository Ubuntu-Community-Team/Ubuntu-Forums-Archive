---
title: "open (/dev/ttyUSB0): Permission denied : Line in use"
date: 2013-06-24
forum: Server Platforms
---

### Post by Lars Noodén on 2013-06-24
I'm trying to open a serial connection and get the following error when I try to connect either through my own account or via root using sudo:

```

cu -s 19200 -l /dev/ttyUSB0
cu: open (/dev/ttyUSB0): Permission denied
cu: /dev/ttyUSB0: Line in use

```

I am a member of the group 'dialout'

```

ls -lh /dev/ttyUSB0 
crw-rw---- 1 root dialout 188, 0 Jun 24 13:15 /dev/ttyUSB0

```

What step am I missing?

---

### Post by koenn on 2013-06-24
what I gather from [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=264626](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=264626) and [https://bugzilla.redhat.com/show_bug.cgi?id=145459](https://bugzilla.redhat.com/show_bug.cgi?id=145459)
is that cu drops privileges to uucp:uucp and  your serial port device must be rw for both that user and that group. Or something similar with unusual/unexpected permission requirements.

---

### Post by Lars Noodén on 2013-06-25
I tried with accounts that were in the group UUCP and not in the group.  Yesterday, it made no difference, neither worked.  Today, it makes no difference both work.  My only guess is that the serial hardware itself got in some kind of confused state.

---

