---
title: "PuTTY and TTY7 (startup messages)"
date: 2011-03-15
forum: Server Platforms
---

### Post by Moerby on 2011-03-15
Hi, I'm a bit of an Ubuntu noob so I'm having a tough time figuring this out. 

In Ubuntu 10.04 you can press ALT+F7 to see the startup messages when you're at the server. I believe this switches to TTY7? 

Now, when I access the same server through SSH and PuTTY, the ALT+F7 sequence produces garbled characters. There also doesn't seem to be a way in PuTTY itself to send the ALT+F7 sequence either.

So does anyone know how I can view the contents of TTY7 (startup messages) through PuTTY?

Thanks!

---

### Post by BkkBonanza on 2011-03-16
The Alt F7 won't work at an ssh terminal. It is only for the console.
 
The dmesg command will show the boot messages and you can look in a couple of log files too - like /var/log/syslog or /var/log/messages but these are often a bit different from what shows on the console.

I'm not aware of a method to attach to the tty console during ssh. The ssh uses a different terminal system (ptsX) than the ttyX ones. The only way I've been able to view the console remotely was using a KVM unit that hooks onto the vga port and feeds it over the network.

---

### Post by Moerby on 2011-03-16
Thank you BkkBonanza! I wish dmesg weren't so cryptic to look at :) For someone new to Ubuntu, it's hard to know what to look for in there. Also, the time stamps are numeric numbers like [   22.926743]. Ouch!

---

### Post by BkkBonanza on 2011-03-16
I think the time stamps are seconds since start. Also piping it to less makes it easier to browse thru, you can page up/down etc. 

dmesg |less

Interpreting some lines is always a bit of a challenge though.

---

### Post by CharlesA on 2011-03-16
Also note that any output while the system was booting is output to /var/log/boot.log, so you can check it after booting.

---

### Post by Moerby on 2011-03-16
Thanks guys for the help. 

That /var/log/boot.log file will work for me.

---

