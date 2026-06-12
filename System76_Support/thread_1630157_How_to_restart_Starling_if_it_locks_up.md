---
title: "How to restart Starling if it locks up?"
date: 2010-11-24
forum: System76 Support
---

### Post by tc101 on 2010-11-24
This has never happened, but if my Starling ever locked up and I wanted to reboot but had no control with mouse or keyboard, should I just press the power button on the side, or is  there a better way?

---

### Post by tc101 on 2010-11-25
I will close this thread.  I tried the reboot using the power key and it worked fine.  No one suggested a better way, so I assume that is the best way to do it.

---

### Post by carl lindsay on 2010-12-06
i also want to know about the starling, that when it locks up then how to restart starling. if any one has better sugession than please tell.[B] 

[http://mymusiccircle.com/](http://mymusiccircle.com/)
[/B]

---

### Post by isantop on 2010-12-06
Holding the Power Button works fine as a very last resort, but if you're going to try that, the best option to try first is to type each of the following letters, in order:
```
r    e    i    s    u    b
```
while holding Alt and PrtSc/SysRq. It should restart, but if it doesn't, holding the power button couldn't do any more harm anyway.

It's a good first stp, though you should also reserve it for when your system isn't responding.

(This will work 100% of the time as long as the kernel hasn't locked up)

---

### Post by Dave_L on 2010-12-07
> **isantop said:**
> ... type each of the following letters, in order:
```
r    e    i    s    u    b
```
while holding Alt and PrtSc/SysRq.

Is that order preferred over ```
r  s  e  i  u  b
``` (Raising Skinny Elephants Is Utterly Boring)?

---

### Post by isantop on 2010-12-07
It shouldn't make too much of a difference, but I'd go with mine. The "S" syncs the hard drive, while "E" and "I" end, then kill all processes except init, respectively. It makes sense to me to kill the processes writing to the disk before syncing the rest of the data there.

Just for reference, each keypress:

R: Resets the keyboard to a more generic system mode.
E: Asks all running processes to terminate.
I: Kills all remaining processes.
S: Syncs all data to the hard disk.
U: Remounts the hard disk in read-only mode.
B: Reboots the system.

---

### Post by tlroche on 2010-12-07
> **isantop said:**
> [Alt+PrtSc+each member of the sequence [r e i s u b] does]

R: Resets the keyboard to a more generic system mode.
E: Asks all running processes to terminate.
I: Kills all remaining processes.
S: Syncs all data to the hard disk.
U: Remounts the hard disk in read-only mode.
B: Reboots the system.

Ah, yes: "Reboot Even If System Utterly Broken." But I can never remember that they bind to Alt+PrtSc :-(

---

### Post by Dave_L on 2010-12-08
> **isantop said:**
> It shouldn't make too much of a difference, but I'd go with mine. ,,,

Thanks.  I'll switch to the mnemonic "Raising Elephants Is So Utterly Boring." :)

---

