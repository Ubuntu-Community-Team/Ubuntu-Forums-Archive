---
title: "My server doesnt reboot"
date: 2009-10-09
forum: Server Platforms
---

### Post by ncnbnt on 2009-10-09
Hello,

i have ubuntu 8.04 and all are ok.

Im running "reboot" says 


Broadcast message from [email]root@blabla.com[/email]
        (/dev/pts/2) at 17:23 ...

The system is going down for reboot NOW!

BUT THE SSH(PUTTY IS STILL ON AND STILL LISTENING)
ALSO THE SERVER IS UP.
NO ERRORS IN SYSLOG


PLEASE HEELPP

---

### Post by karlson on 2009-10-09
> **ncnbnt said:**
> Hello,

i have ubuntu 8.04 and all are ok.

Im running "reboot" says 


Broadcast message from [email]root@blabla.com[/email]
        (/dev/pts/2) at 17:23 ...

The system is going down for reboot NOW!

BUT THE SSH(PUTTY IS STILL ON AND STILL LISTENING)
ALSO THE SERVER IS UP.
NO ERRORS IN SYSLOG


PLEASE HEELPP

What's the output of: 

```

ps -ef | grep init.d

```

---

### Post by ncnbnt on 2009-10-09
root      4197     1  0 18:05 ?        00:00:00 /bin/sh /etc/init.d/rc 2
root      4925  4922  0 18:06 ?        00:00:00 /bin/sh -e /etc/init.d/apache2 restart
root      4945  4880  0 18:06 pts/0    00:00:00 grep init.d

---

### Post by superc0w on 2009-10-10
Try other commands, and see if they help it's not a permanent fix but try theses:
init 6
shutdown -r now

if none of those work (init 6 may take a while) your dmesg log may also shed some light.

---

