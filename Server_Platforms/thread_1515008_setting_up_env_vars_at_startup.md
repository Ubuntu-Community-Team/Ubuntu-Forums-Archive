---
title: "setting up env vars at startup"
date: 2010-06-21
forum: Server Platforms
---

### Post by neoideo on 2010-06-21
Hello,

i have some servers, which together form a cluster.

one of the servers is the "main guy" which has NIS and NFS.
the others mount the partition and can log in whith the same "main" account.

my problem is that i need to call a startup script "settings.sh" to set some enviroment variables for the cluster to work.

this script is on the NFS folder.

i would like if possible to call this script as early as possible, even before login phase, since they are servers and can be shutdown, restarted, etc.

at the moment i need to log via ssh into every one of the 4 nodes and do "source /opt/cfc/sge/default/common/settings.sh" manually each time they reboot.

i would like to put this script somewhere so that it gets called after the NFS mount, but without the need to log into an account. is possible???

otherwise i could set the nodes to automatically login into the main account..

im a little confused on something really simple, i know. But on the past i always used .bash_rc, this time i dont want to take that solution.

any help is welcome!

---

### Post by brettg on 2010-06-21
Call your script from /etc/rc.local

---

### Post by clrg on 2010-06-22
If you only set variables, put it in /etc/profile. That's the ~/.profile for everyone. If you want to do more, write an init script and put it in /etc/rc2.d/. That way you can control when your script gets called. If you just put it in /etc/rc.local, it will always be called last.

---

### Post by neoideo on 2010-06-22
i followed your advices 
im using /etc/profile, at the moment is working good.
thanks!
:guitar:

edit: i also tested adding this line on /etc/rc.local
source /path/settings.sh
but i didnt work, how should it be called when using rc.local? just to know in case

---

### Post by brettg on 2010-06-22
If you put 

```
/path/to/file/myscript.sh 
```

before the "exit" line at the end it will be called every time the system reboots.

---

