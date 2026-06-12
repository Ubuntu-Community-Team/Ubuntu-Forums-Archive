---
title: "Remote system will not reboot"
date: 2012-08-09
forum: Server Platforms
---

### Post by Barefootpanda on 2012-08-09
I'm attempting to reboot a remote system. I have sent the reboot command and received...

```
root@backup:/home/NAME# reboot

Broadcast message from NAME@backup
	(/dev/pts/1) at 14:22 ...

The system is going down for reboot NOW!
root@backup:/home/NAME# reboot
```

I cannot open a new SSH connection to the system, but I have two open. One is responding and will launch things like top and allow me to move around. The other has died.

I'm not sure if it's a busy resource not letting me reboot or if it's a stuck system process that I could kill to get the reboot to work.

I CANNOT get physical access to this system for about a month. The only authorized person is on a month long holiday.

Ideas?

---

### Post by koenn on 2012-08-09
if that one session still accepts commands, why don't you start shutting down services there, kill processes, ... make the thing as idle as possible, then if necessary issue the reboot command again ?

maybe cancel the shutdown first, then reboot after you've manually stopped most of what the server is doing ? 


no guarantees though. you may need to exit the ssh session, and if you can't get in while the server hangs, you're still toast.

---

### Post by thnewguy on 2012-08-09
Have you tried using telinit to change the runlevel? If memory serves, run level 2 is the normal runlevel for Ubuntu and 6 triggers a reboot.

On a side note, if everything else on the server is working and the reboot isn't urgent then you might consider leaving it alone. Mucking about with a machine to which neither you nor anyone else can physically access is asking for trouble.

---

### Post by Barefootpanda on 2012-08-09
> **thnewguy said:**
> Have you tried using telinit to change the runlevel? If memory serves, run level 2 is the normal runlevel for Ubuntu and 6 triggers a reboot.

On a side note, if everything else on the server is working and the reboot isn't urgent then you might consider leaving it alone. Mucking about with a machine to which neither you nor anyone else can physically access is asking for trouble.

Agree.

Won't changing the runlevel drop my ssh connection?

---

### Post by Barefootpanda on 2012-08-09
I'm also noticing I have defunct processes that appear attached to init.

---

