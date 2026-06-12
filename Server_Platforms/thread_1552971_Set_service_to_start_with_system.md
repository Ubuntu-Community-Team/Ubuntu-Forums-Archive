---
title: "Set service to start with system"
date: 2010-08-14
forum: Server Platforms
---

### Post by Alan87i on 2010-08-14
running xubuntu 10.4 
I have zoneminder installed and finally working. Sort of. 

It's service or group is www-data .
The problem is it does not start with the system . I can login to the console but zoneminder is always in a stopped state. 

I am trying my best with shell only and have no clue how to remedy this. 
Thanks 
Allan

---

### Post by Sporkman on 2010-08-15
Is there a startup service script for this in /etc/init.d? If so, you can register it as a service & set it to start with:

sudo update-rc.d <service script name> defaults

If not, you can put a command in /etc/rc.local to run it on startup.

---

