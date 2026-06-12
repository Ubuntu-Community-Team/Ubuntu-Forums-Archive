---
title: "Creating an upstart service for dumping and uploading a mysql database on shutdown"
date: 2016-01-23
forum: Server Platforms
---

### Post by rodrigomartinho on 2016-01-23
I am running Ubuntu Server 14.04 LTS x64. I have two KVM guests. One is a file server and another runs mysql server.

I have a script that I run on the file server. The script connects via ssh to the guest that runs mysql server, dumps a mysql database and uploads it to another remote server. The script works as expected. Now I want to make this script to run at shutdown.

I have read about upstart and tried to make a service to accomplish this. I created my init file (/etc/init/dotproject_backup.conf) with this content:

```

# dotproject_backup
# This service makes a dump and rsync of a dotproject mysql database prior to shutdown.

description "dotproject backup"
author "Rodrigo Martinho"

start on startup
stop on runlevel [016]

pre-stop script
exec /home/user/script.sh
end script

```

In this example I also put runlevel 6 so I can test it on reboot. I may change that after all works. On reboot, the system isn't waiting for the script to run. In fact it seems the script isn't running at all, as I can see on the log file (/var/log/upstart/dotproject_backup).

I tried some other setups where the script was started, but shutdown completed before the dump was uploaded:

```

# dotproject_backup
# This service makes a dump and rsync of a dotproject mysql database prior to shutdown.

description "dotproject backup"
author "Rodrigo Martinho"

start on runlevel [016] or stopping dbus or deconfiguring-networking

script
exec /home/user/script.sh
end script

```

In this setup I can see on log file that the script was started, but it was killed when file was being uploaded.

I read on another post here that the correct way of accomplishing this is changing the start condition, so script is run before the reboot process is started:

```

# dotproject_backup
# This service makes a dump and rsync of a dotproject mysql database prior to shutdown.

description "dotproject backup"
author "Rodrigo Martinho"

start on starting rc RUNLEVEL=[016]

script
exec /home/user/script.sh
end script

```

But in this example again the shutdown completed before the script. So, my questions are:

- Should I make the service start or stop when runlevel changes for shutdown or reboot?
- How should I make the shutdown to wait until the script is complete?
- Would it be a better approach to run my script as a pre-stop inside another service?

Thanks in advance for any help,

Rodrigo Martinho.

---

### Post by MAFoElffen on 2016-01-23
Just wrapping my head around what you are trying to do...

Reference on SysV Runlevels:
> 
0 &#8212; Halt
1 &#8212; Single-user textmode (For special administration: Brings system to a bare essentials mode for maintenance).
2 &#8212; Local Multiuser textmode with Networking but without network service (like NFS)
3 &#8212; [COLOR=#000000][FONT=Times New Roman]Full Multiuser textmode with Networking ([/FONT][/COLOR]All services are running but X11[COLOR=#000000][FONT=Times New Roman])[/FONT][/COLOR]
4 &#8212; Not used (User-definable)
5 &#8212; Full Multiuser with Networking and X Windows(GUI, with an X-based login screen)
6 &#8212; Reboot


So in that respect, you have the runlevel id's correct, but the location of your script may be in question... Thinking about startup scripts, if you want something to start at each startup, immaterial of what runlevel, then you put it in "/etc/init/". Thinking back on shutdown scripts for runlevels... Usually,if you are wanting a script to execute on a specific runlevel, you put that script into the specific runlevel directory, example "/etc/rc0.d".  But if your want it to execute on multiple runlevels, then you locate your script in "/etc/init.d/" and put symlinks into directories "/etc/rc0.d", "/etc/rc1.d", and "/etc/rc6.d" (tailored to your case) to point back into to that script. And the filename of that symlink (how it sorts alphabetically in order of other filenames in that directory) determines the order it will execute...

But That was the SysV Init System... I'm still learning more on how that changed with Systemd's startup and shutdown. Basically, you start it up as a service, then on the service_name service_script.service file, you point to your shutdown script under the "Service " section. For example...
```

[Unit]
Description=Power-off gpu


[Service]
Type=oneshot
ExecStart=/usr/bin/vgaoff start
ExecStop=/usr/bin/vgaoff stop
RemainAfterExit=yes


[Install]
WantedBy=multi-user.target

```
Honestly, I'm still learning this and stumbling through the changes on how this new system framework works. Still trying to figure that out, but that is my understanding so far. I've had to modify some of my old init scripts, as the Debian Branch works out how they work out on how their flavor works.

---

### Post by rodrigomartinho on 2016-01-23
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

Upstart is the replacement of the System-V init for managing system boot and shutdown, so I am trying to accomplish this using upstart. That's why the script goes on /etc/init, not on /etc/rc*. As far as I'm concerned this should be accomplished with one single file on /etc/init, or even as a stanza on another service file.

---

### Post by rodrigomartinho on 2016-01-28
Anyone could help with this?

---

### Post by ian-weisser on 2016-01-28
> **rodrigomartinho said:**
> Now I want to make this script to run at shutdown.

Two issues:

One,  Upstart has been superseded by systemd for system-level jobs in 15.04  and later. Your Upstart solution will need to be rewritten for systemd targets  when you migrate that server to a newer release of Ubuntu.

Two,  shutdown activities are considered unreliable, and are not  encouraged. There are too many ways to bypass them (power loss, holding  down the  power button, etc). If you must use shutdown, remember to add a check at boot that the shutdown job completed properly.





> **rodrigomartinho said:**
> ```

# dotproject_backup
# This service makes a dump and rsync of a dotproject mysql database prior to shutdown.

description "dotproject backup"
author "Rodrigo Martinho"

start on startup
stop on runlevel [016]

pre-stop script
exec /home/user/script.sh
end script

```

You are saying 'run this script at startup' (instead of shutdown). Since the script completes and terminates itself (it's not a daemon), the pre-stop does nothing.






> **rodrigomartinho said:**
> ```

# dotproject_backup
# This service makes a dump and rsync of a dotproject mysql database prior to shutdown.

description "dotproject backup"
author "Rodrigo Martinho"

start on runlevel [016] or stopping dbus or deconfiguring-networking

script
exec /home/user/script.sh
end script

```

Much better. You are saying 'run this script at shutdown', which is what you want. Unfortunately, you are starting the script *after* the runlevel [016] signal is received, and all the other services (like networking) are busy shutting down, which kills your filesystem and file transfer. Try a 'pre-start script' instead, so Upstart runs the script before emitting the signal.

There are more complex, graceful ways of doing it, using Upstart-style dependencies (or systemd-style targets). Example: Bring down external network connections (to stop activity in the VMs), then backup the VMs, then shut down the VMs, then bring down internal network connections, finally shutdown the host system. You can't easily do that with runlevels.

---

### Post by rodrigomartinho on 2016-01-29
Hi Ian, thanks for your answer.

> **ian-weisser said:**
> 
Two issues:

One,  Upstart has been superseded by systemd for system-level jobs in 15.04  and later. Your Upstart solution will need to be rewritten for systemd targets  when you migrate that server to a newer release of Ubuntu.

Two,  shutdown activities are considered unreliable, and are not  encouraged. There are too many ways to bypass them (power loss, holding  down the  power button, etc). If you must use shutdown, remember to add a check at boot that the shutdown job completed properly.


The idea here is that I have an UPS that will send the shutdown command to the server when battery runs low to a certain amount I define. So power loss shouldn't be an issue. Unfortunately I don't know either how to make a check at boot, but I may know if the script was completed by analyzing its results. 

> **ian-weisser said:**
> 
You are saying 'run this script at startup' (instead of shutdown). Since the script completes and terminates itself (it's not a daemon), the pre-stop does nothing.


This was one of my questions, if I should start or stop the service at shutdown, so this part of the problem is solved.

> **ian-weisser said:**
> 
Much better. You are saying 'run this script at shutdown', which is what you want. Unfortunately, you are starting the script *after* the runlevel [016] signal is received, and all the other services (like networking) are busy shutting down, which kills your filesystem and file transfer. Try a 'pre-start script' instead, so Upstart runs the script before emitting the signal.


I tried this suggestion, but it didn't work either:

```

start on runlevel [016] or stopping dbus or deconfiguring-networking


pre-start script
exec "/home/user/script.sh"
end script

```

As the previous tests, the script started to run, but shutdown completed before file transfer was completed. Then I tried this, which was stated on another post to run the script before shutdown is started: 

```

start on starting rc RUNLEVEL=[016] or stopping dbus or deconfiguring-networking


pre-start script
exec "/home/user/script.sh"
end script

```


In this case it seems the script wasn't run at all. Any other thoughts?

> **ian-weisser said:**
> 
There are more complex, graceful ways of doing it, using Upstart-style dependencies (or systemd-style targets). Example: Bring down external network connections (to stop activity in the VMs), then backup the VMs, then shut down the VMs, then bring down internal network connections, finally shutdown the host system. You can't easily do that with runlevels.


As you stated before, systemd will soon replace upstart in Debian based distros, and I read that it is already used in RedHat based distros. I will consider moving my solution to systemd in the future, but by now I am using Ubuntu Server 14.04 LTS and I don't plan to update it before next LTS version, so I need to accomplish this on Upstart, so maybe I will need to study Upstart dependencies. Do you know any good starting point for that?

Thanks again.

---

