---
title: "Upstart won’t start two instances of daemon after reboot"
date: 2013-01-31
forum: Server Platforms
---

### Post by dazz100 on 2013-01-31
Hi
I am trying to configure a Ubuntu server to run two instances of a daemon “motion”.
I have succeeded in modifying init.d scripts to run two instances of the program.  

To achieve that I have

Created the directory “/etc/motion2/” containing the relevant config file
Created the directory “/var/run/motion2” to store the PID file
Copied and modified /etc/init.d/motion2 the start stop restart script for the 2nd instance.
Copied and created a motion2 file in "/etc/defaults/"
Created a synlink “/usr/bin/motion2” pointing to the executable “/usr/bin/motion”

This is detailed in the post 
[http://ubuntuforums.org/showthread.php?t=2108463](http://ubuntuforums.org/showthread.php?t=2108463)

I can stop / start the two instances individually as intended.

The problem I now have is that after a reboot, only one daemon “motion” is started.  The other instance “motion2” does not start automatically.  It will start if I run the init.d start script from the command line.

I don’t know enough about Upstart to know where to look to fix this problem. 
If it is a problem with my init.d scripts, I would expect it would show when I manually start/stop the motion and motion2 daemons.

If it is a problem with the way Upstart does things after reboot, I don’t know how to fix that.

Dazz

---

### Post by dazz100 on 2013-02-06
Hi

I have done a bit of digging around the system.  I note that the rc<x>.d directories have scripts for <motion> but not the 2nd <motion2> instance I have added.

I am going to try copying/renaming my init.d/motion2 script to the rc<x>.d directories.

Dazz

---

### Post by dazz100 on 2013-02-07
Hi

I fixed this problem by adding sym links to the rc<x>.d directories.  

These sym links point to the script in the init.d directory.
I just used the existing sym links for motion to create the links for motion2.


Dazz

---

