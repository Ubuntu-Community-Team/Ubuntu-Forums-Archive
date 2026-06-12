---
title: "openssh listing connected sftp clients"
date: 2007-07-19
forum: Server Platforms
---

### Post by phiphedog on 2007-07-19
I have installed OpenSSH and have set up a SFTP server with hostkey authentication. and I want to be able to see who is connected and what files they have requested or uploaded.

in [COLOR="Blue"]/etc/ssh/sshd_conf[/COLOR] I have put the following entries:

[COLOR="Blue"]# Logging
SyslogFacility AUTH
LogLevel DEBUG[/COLOR]

and in the /[COLOR="Red"]etc/syslog.conf file[/COLOR] I have put the following line

[COLOR="Red"]auth.debug               /var/log/ssh.log[/COLOR]

In the ssh.log file I can see who requests a connection and if they are succesful or not but I am unable to see who is still connected, what they have requested and what they have uploaded.

Is there even a system command that will tell me who is connected on what port?

---

### Post by Mr. C. on 2007-07-20
Modify your sftp Subsystem line in sshd_config:

```
Subsystem       sftp    /usr/local/libexec/sftp-server -l DEBUG3
```

and restart the ssh server.  This will increase the log level for sftp-server, which will prefix lines with the debug level names, where DEBUG3 is the highest debug level.  Man sftp-server for more details of log levels.

MrC

---

### Post by phiphedog on 2007-07-21
I have the following line in my /etc/ssh/sshd_config

```
Subsystem sftp /usr/lib/openssh/sftp-server	-l	DEBUG3
```

but when I try to restart the ssh demon it gives the following error

```
bob@bob-desktoppc:~$ sudo /etc/init.d/ssh restart
Password:
 * Restarting OpenBSD Secure Shell server...    /etc/ssh/sshd_config line 75: garbage at end of line; "-l".
```

I had a look in my man for sftp-server and it says nothing about the working of the program. In the man page for sftp it says to use the -v option to raise the logging level but I think this is just for command line use, because when I add it to my sshd_config file as you suggested I do with the -l DEBUG 3 it give the same error.

any suggestions?

---

### Post by Mr. C. on 2007-07-21
Sorry, the -l log level option is available on newer versions of openssh.  It was added in July of 2006, and the debian/Ubuntu version is older (v 4.3p2).  I build my own software, so have a newer version (4.6p1).

I'm not sure what is requried, or if it is possible, to get the data you want with the Ubuntu/Debian version.

You could build from source.

MrC

---

