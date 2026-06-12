---
title: "Problem with wakeonlan and pm-suspend"
date: 2011-04-30
forum: Server Platforms
---

### Post by Mirko76 on 2011-04-30
Hello,

i want to use pm-suspend on my ubuntu server 11.04. Everything works fine,
i can wake up the server with the power button, but wake on LAN doesn't work.

My network card is an Intel e1000e. 
If i use acpid with "echo mem > /sys/power/state", wake on LAN works without any problem.

What can i do to solve the problem?

Thanks
Mirko76

---

### Post by egpetrich on 2011-05-01
Someone wrote a HOWTO on this topic:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

The thread started a long time ago, but people have been adding stuff to it recently.

---

