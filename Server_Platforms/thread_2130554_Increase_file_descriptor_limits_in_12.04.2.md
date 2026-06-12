---
title: "Increase file descriptor limits in 12.04.2"
date: 2013-03-29
forum: Server Platforms
---

### Post by Alan Wong on 2013-03-29
Having some issues increasing the file descriptor limits on my system. 

I've setup the limits in /etc/security/limits.conf and edited the pam login modules to enable that, all is displaying well with ulimit -n -S and ulimit -n -H

However im still having issues with the file descriptor limits not being increased from 1024 in the system headers.

So far i've edited __FD_SETSIZE in /usr/include/linux/posix_types.h and in /usr/include/x86_64-linux-gnu/bits/typesizes.h however unrealircd is still complaining about it being set to 1024.

I know previously on 11.04 you changed this in /usr/include/bits/typesizes.h however that doesnt exist in 12.04, so im stumped. Nout on google as to how to do this in 12.04

---

### Post by matt_symes on 2013-03-29
Hi

Does this thread in anyway help ?

[http://ubuntuforums.org/showthread.php?t=1961208](http://ubuntuforums.org/showthread.php?t=1961208)

Kind regards

---

### Post by Alan Wong on 2013-03-29
Unfortunately not. All values there seem to be fine too. Unrealircd specifically complains about fd_setsize

```
ulimit -n -S
4096

```

```
ulimit -n -H
10240

```

```
cat /proc/sys/fs/file-max
402932

```

---

### Post by matt_symes on 2013-03-29
Hi

What about this ?

[http://www.linuxquestions.org/questions/ubuntu-63/help-with-fd_setsize-412458/](http://www.linuxquestions.org/questions/ubuntu-63/help-with-fd_setsize-412458/)

or this 

[http://www.unrealircd.com/faq.php](http://www.unrealircd.com/faq.php)

(search for [COLOR=#000000][FONT=Verdana]FD_SETSIZE[/FONT][/COLOR])

Kind regards

---

