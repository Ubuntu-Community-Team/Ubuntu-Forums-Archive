---
title: "Constant inbound trafic in Ubuntu 11.04"
date: 2011-05-25
forum: Security
---

### Post by JanusDC on 2011-05-25
Hi,

I have a network monitor and I see a constant inbound traffic of around 98KiB/s. I ran  
```
sudo netstat -natp
```
and stopped/killed all the processes that were there until this command does not shows anything, however the constant 98 KiB/s inbound traffic is still there.

The monitor I am using is the "system monitor" applet (I am using "Ubuntu Classic (without effects)". 

How else could I track what process is doing this? 

Just in case: If I disconnect the network cable, of course, it stops, so it may not be a bug in the monitor.

Cheers

---

### Post by JanusDC on 2011-05-25
It suddenly stopped... what makes me even more curious to know what was that and why I didn't see it with netstat.

Any insight?

---

### Post by jorritTyb on 2011-05-25
Could be someone trying an attack on your computer?

Just guessing.

---

### Post by JanusDC on 2011-05-25
I guess no, since I am behind the University's firewall...

---

