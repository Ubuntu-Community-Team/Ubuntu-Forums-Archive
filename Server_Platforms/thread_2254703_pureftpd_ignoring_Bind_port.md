---
title: "pureftpd ignoring Bind port"
date: 2014-11-29
forum: Server Platforms
---

### Post by lambdafox on 2014-11-29
I have pureftpd installed.

/etc/pureftpd/Conf/Bind is set to ,990

But, when I start and stop the service or reboot, and do $ sudo netstat -lp --inet, pureftpd is not listening on port 990.  It is getting a different random port every time. At the moment the pureftpd service is listening for ftp on port 2058 and ftps on port 1986.

I have tried the Bind file with and without the leading comma and that does not change this behavior.

PassivePortRange is set to 6500 6600
TLS is set to 2
VerboseLog is set to yes

There is no file:
\var\log\pureftpd.log

There is a file:
var\log\pureftpd\transfer.log
but it is empty.

Please help.

I am running Ubuntu GNOME 14.04 [amd64], but I doubt this is a gnome-centric problem...

---

### Post by bashiergui on 2014-11-30
You can't bind a service to a privileged port, which is anything less than 1024. Only root can bind to privileged ports. Choose a port number higher than that.

---

### Post by lambdafox on 2014-12-01
> **bashiergui said:**
> You can't bind a service to a privileged port, which is anything less than 1024. Only root can bind to privileged ports. Choose a port number higher than that.

I changed \etc\pureftpd\Conf\Bind to ,21990

I then restarted.  pureftpd is now listening on port 2221 for ftp and nothing for ftps

---

### Post by lambdafox on 2014-12-02
Troubleshooting update:

Please remember, that I am a Linux noobie, but tech oldie...

I suspected that somehing was getting mangled when ubuntu created the wrapper wtih the text files in  \etc\pureftpd\Conf

So, I made a back up of those and deleted all of them and restarted my system.

When I did sudo netstat -lp --inet I see pure-ftpd is listening for ftp on port 2215

I then did  sudo service pure-ftpd stop

I again ran the netstat command.  I was surprised to see that it still shows pureftpd is listening for ftp on port 2215

I did  sudo service pure-ftpd status and it says that pure-ftpd has been stopped and is not running.

I did the netstat command again, and it still shows pure-ftpd listening on port 2215.

Please, someone who understands netstat explain this to me???

---

