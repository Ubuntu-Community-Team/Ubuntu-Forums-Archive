---
title: "Startup script problems"
date: 2009-12-12
forum: Server Platforms
---

### Post by Violated on 2009-12-12
Hello,

I've been trying to get teamspeak to start on boot. But, i'm failing really hard atm.

I'm running ubuntu server 9.10, with atm running mysql, ftp, apache, php. Teamspeak runs fine, just not right after booting. I've tried multiple methods (or they could all be the same, it looks so simple but, well, it aint working.)

I've tried following this guide: [http://www.linuxforums.org/forum/redhat-fedora-linux-help/24951-start-script-boot.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/24951-start-script-boot.html). Basicly i made a script the script mentioned by Swemic. I put that script in /etc/init.d, wich pointed towards the right scripts to start and shut down the teamspeak server. It didn't worked out.

After that i tried following NVRAM's advice at [http://nixcraft.com/shell-scripting/956-script-file-run-when-linux-boot.html](http://nixcraft.com/shell-scripting/956-script-file-run-when-linux-boot.html). Well, i made the script and all, worked fine. But i got stuck with the symbolic links.

I've tried googling for a good guide how to make a program start after boot, but they're all little pieces of the puzzle.

I hope someone here can help me on how to make my teamspeak server, or any program for that matter, start after boot.

Thanks in advance,
Vio

---

### Post by sisco311 on 2009-12-12
> **Violated said:**
> Hello,

...

After that i tried following NVRAM's advice at [http://nixcraft.com/shell-scripting/956-script-file-run-when-linux-boot.html](http://nixcraft.com/shell-scripting/956-script-file-run-when-linux-boot.html). Well, i made the script and all, worked fine. But i got stuck with the symbolic links.

...

Thanks in advance,
Vio

```
sudo update-rc.d **script** defaults 99
```
where **script** is the name of the init script.


But you can write an upstart job instead of the SysV style init script.

```
description     "Start/Stop TeamSpeak Server"

start on started networking

stop on runlevel [016]

expect fork
respawn

exec /path/to/teamspeak

```

save the file as /etc/init/teamspeak.conf.

A list of all jobs and their states can be obtained by using:
```
initctl list
```

to start/stop the job manually:
```
initctl start teamspeak
```
```
initctl stop teamspeak
```

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

---

### Post by Violated on 2009-12-14
Thanks you, the first solution helped me. Cheers.

---

