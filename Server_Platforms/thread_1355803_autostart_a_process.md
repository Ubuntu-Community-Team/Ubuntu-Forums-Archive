---
title: "autostart a process"
date: 2009-12-15
forum: Server Platforms
---

### Post by NetSkay on 2009-12-15
hello
i have programmed a custom python script that i would like to start up automatically on boot, it doesnt take any special arguments or anything just standard
python myscript.py

the script itself can daemonize, so i just need a way to execute the command as root on start up, i know i have to place something in the /etc/init.d but not sure what...

anyone?!

thnx

---

### Post by BkkBonanza on 2009-12-15
You can simply add the command to /etc/rc.local
Anything in there will get run at the end of booting.

Or you can use upstart. In this case use an existing script in /etc/event.d as an example to make your own. This way you can have respawn if you need.
(respawn allows for the program to be auto-restarted if it gets killed)
eg. /etc/event.d/tty1

---

