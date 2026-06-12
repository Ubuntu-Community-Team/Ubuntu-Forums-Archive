---
title: "SSHD and MySQL running - but why?"
date: 2011-06-29
forum: Server Platforms
---

### Post by Neo23x0 on 2011-06-29
My Ubuntu 11.04 has an OpenSSH Daemon and MySQL database running although I checked all runlevel directories for startup scripts and did not find any.

I installed bum to check for any startup scripts that would cause these services to start. I would like to start them manually on demand. I dont need them running all the time. 

As I said - I checked all /etc/rc... directories for startup scripts - none. I used sysv-rc-conf to check that they are disabled but  finally I got these two services running.

Any ideas?

---

### Post by diesch on 2011-06-29
Ubuntu 11.04 uses [Upstart](http://upstart.ubuntu.com/cookbook/) to manage services so you need to have a look at /*etc/init/*

---

### Post by Neo23x0 on 2011-06-29
Thanks,

Upstart is new to me. I'll check it out. 
I disbaled the confs simply by renaming them to *.noexec 
That should help, right.

The configuration files look pretty complex. 

Thanks a lot for your quick reply.

---

### Post by RudyG on 2011-07-07
Neo did you get this to work? I found instructions for disabling mysqld from starting up here: [Askubuntu]("http://askubuntu.com/questions/40072/how-to-stop-apache2-mysql-from-starting-automatically-as-computer-starts")
But they don't seem to work. Here are the steps that I followed:
1. sudo -i
2. echo "manual" >> /etc/init/mysql.override

These steps produced a file called /etc/init/mysql.override. Inside this file is a lone word "manual". However upon restarting I still see mysqld running.:confused:

Rudy

---

