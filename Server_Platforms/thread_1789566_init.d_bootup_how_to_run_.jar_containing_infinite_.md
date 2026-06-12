---
title: "init.d bootup how to run .jar containing infinite loop"
date: 2011-06-24
forum: Server Platforms
---

### Post by thilina01 on 2011-06-24
I've a requirement of executing a jar file containing an endless loop, it should start executing when the server boot and should continue executing until server halt. 

created the file named "bu" containing

#!/bin/sh
java -jar /home/samara/nano/bu.jar

at /etc/init.d

and created the link for script at: /etc/rc2.d
using code:
sudo ln -s /etc/init.d/bu /etc/rc2.d/S90bu

chmod the file with : sudo chmod 755 /etc/init.d/bu

rebooted using: sudo reboot
==========================
when the server boot-up 
it displays console output of my jar file for every loop execution.

i need my script running with separate thread in CPU and normally boot the system
as like starting apache2 on boot-up 

Any help is appreciated.

---

### Post by thilina01 on 2011-06-24
I think i found the solution
I just added "&" at the end of script
now my server start normally and the file is executing with no problem
my new script looks exactly:

#!/bin/sh
java -jar /home/samara/nano/bu.jar &

if there is any way better than this please let me learn that.

Thank you.

---

