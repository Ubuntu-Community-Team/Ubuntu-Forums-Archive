---
title: "noob needs help with mysql"
date: 2011-09-23
forum: Server Platforms
---

### Post by bakan723 on 2011-09-23
Hey guys I am new here so I kindly ask you all to bear with me while I learn.  

My problem is with mysql.  I am somewhat familiar with it.  I have used it in windows a little bit.  

Basically I am trying to run a server for an online soccer game called winning eleven 9 liveware evolution.  Running this server requires me installing mysql and setting up a user called fiveserver and making a database.  

instructions for windows setup can be found here"
[http://mapote.com/fiveserver/win32_howto.html](http://mapote.com/fiveserver/win32_howto.html)

there is a linux version of this software but so far i have been unable to get it to work and there are no linux instructions.  

can someone please help me im so confused

---

### Post by jonobr on 2011-09-23
Have you installed it?

```
sudo apt-get install mysql-server
```

are you running PHP? If so you will also need to install the php module for mysql 5:

   ```
 sudo apt-get install php5-mysql
```

To create a new database, use the mysqladmin command:

```
mysqladmin create <databasename>
```

Theres a lot of info out there but heres one I found
[http://neoartcool.wordpress.com/2011/02/28/mysql-on-ubuntu/](http://neoartcool.wordpress.com/2011/02/28/mysql-on-ubuntu/)

---

### Post by bakan723 on 2011-09-23
I have made the database successfully but when i go to the run file for fiveserver a terminal window pops up and then disappears.  This terminal is supposed to stay open.  

I know i am not providing the best info here but I am a new convert from windows please excuse my lack of information

---

### Post by Iowan on 2011-09-23
Not really a networking problem.
Moved to Server Platforms - for now...

---

### Post by bakan723 on 2011-09-23
sorry about posting in the improper section

---

### Post by bakan723 on 2011-09-24
No one out there can help me?  I think it might be a permissions issue because when i drag the run file from the gui to a terminal and run it in terminal it says cannot access fiveserver.yaml permission denied.  

But when i run the program by itself it just opens a terminal and it closes almost instantly

---

### Post by bakan723 on 2011-09-25
this is the error I get when I drag and drop the run file from my games server:


brock@brock-Linux:~$ '/service/fiveserver/run' 
touch: cannot touch `/var/log/fiveserver/fiveserver.log': Permission denied
chown: changing ownership of `/var/log/fiveserver/fiveserver.log': Operation not permitted
chgrp: changing group of `/var/log/fiveserver/fiveserver.log': Operation not permitted
Traceback (most recent call last):
  File "/usr/bin/twistd", line 19, in <module>
    run()
  File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
    app.run(runApp, ServerOptions)
  File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
    runApp(config)
  File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
    _SomeApplicationRunner(config).run()
  File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 376, in run
    self.logger.start(self.application)
  File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 216, in start
    observer = self._getLogObserver()
  File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 139, in _getLogObserver
    logFile = logfile.LogFile.fromFullPath(self._logfilename)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 49, in fromFullPath
    os.path.dirname(logPath), *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 162, in __init__
    BaseLogFile.__init__(self, name, directory, defaultMode)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 41, in __init__
    self._openFile()
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 167, in _openFile
    BaseLogFile._openFile(self)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 65, in _openFile
    self._file = file(self.path, "r+", 1)
IOError: [Errno 13] Permission denied: '/var/log/fiveserver/fiveserver.log'
brock@brock-Linux:~$

---

### Post by patryk77 on 2011-09-25
What version are you running and where did you get it/how did you install it?

Judging by the errors you are getting, you are missing the permissions to write the log file.

You should really try and understand [Linux File Permissions](https://help.ubuntu.com/community/FilePermissions).

You can try and make the Log Folder world writable: 
sudo mkdir -p /var/log/fiveserver/
sudo chmod 777 /var/log/fiveserver/ 
/service/fiveserver/run &

If that still doesn't work, you can try and run the service as admin:
sudo /service/fiveserver/run &

Just note that running software you get from sources you may not trust **IS A SECURITY RISK**, especially if you run it as root (which is what [sudo does](https://help.ubuntu.com/community/RootSudo)).

I am not saying "don't do it", just that I don't know the software you are trying to run, and while it is *probably* safe, _I_ can't vouch for it ;)

---

### Post by bakan723 on 2011-09-25
hey man thanks for the answers the help is much apreciated i have been racking my brain for two days with this and not much progress.  I have tried both your suggestions with no luck.  The first suggestion produced the same result and the second produced this:

brock@brock-Linux:~$ sudo /service/fiveserver/run &
[1] 14868
brock@brock-Linux:~$ sudo: /var/lib/sudo writable by non-owner (040777), should be mode 0700

---

### Post by patryk77 on 2011-09-25
When you run a process in the background (whish is what the & at the end of the .../run & command does), it often prints warnings to the screen, even though it doesn't exit the program.

```
sudo: /var/lib/sudo writable by non-owner (040777), should be mode 0700
```
This might be a warning and not an error.

If you press enter after that, does it say:

```
[1]+  Done                    /service/fiveserver/run
```
or something similar?

Edit: If it *does* say done, then yeah, the program exited. But that's not **all** bad, as you now have a logfile to help ;)
```
cat /var/log/fiveserver/fiveserver.log
```


Can you try and connect to it?

---

### Post by bakan723 on 2011-09-25
hehe i didnt think to hit enter again im a dummy lol this is what i got


[1]+  Stopped                 sudo /service/fiveserver/run
brock@brock-Linux:~$

---

### Post by patryk77 on 2011-09-25
No worries... Yeah, stopped means it aborted.

I don't actually have a /var/lib/sudo
Run this:
sudo ls -al /var/lib/sudo

---

### Post by bakan723 on 2011-09-25
brock@brock-Linux:~$ sudo ls -al /var/lib/sudo
sudo: /var/lib/sudo writable by non-owner (040777), should be mode 0700
[sudo] password for brock: 
total 12
drwxrwxrwx  3 root root  4096 1985-01-01 00:00 .
drwxrwxrwx 67 root root  4096 2011-09-24 00:18 ..
drwxrwxrwx  2 root brock 4096 1985-01-01 00:00 brock
brock@brock-Linux:~$

---

### Post by bakan723 on 2011-09-25
btw thank you so much for this help it means a lot to me and many other guys who play on the server.  You are awesome for helping and it is much appreciated

---

### Post by patryk77 on 2011-09-25
That sounds like it's an error related to sudo and not the server.

Run:
```
sudo chmod 0700 /var/lib/sudo
# That should print the same warning
sudo echo aaa
# That should print "aaa" and no more warning.

```
You can always revert the permissions with:
sudo chmod 040777 /var/lib/sudo
but you probably shouldn't.

Then:
```
cat /var/log/fiveserver/fiveserver.log
```

If it says you don't have permissions to read it:
```
sudo cat /var/log/fiveserver/fiveserver.log
```

---

### Post by patryk77 on 2011-09-25
> **bakan723 said:**
> btw thank you so much for this help it means a lot to me and many other guys who play on the server.  You are awesome for helping and it is much appreciated

Not a problem :)

It always feels nice when my (and our, if I may speak for the community) help is appreciated, but I always feel I get more than I put back (the best OS out there), so I am just trying to do my share when I can :D

---

### Post by bakan723 on 2011-09-25
/run/fiveserver/fiveserver.pid'
2011-09-24 00:04:12-0400 [-] Log opened.
2011-09-24 00:04:12-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:04:12-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:04:12-0400 [-] Traceback (most recent call last):
2011-09-24 00:04:12-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:04:12-0400 [-]     run()
2011-09-24 00:04:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:04:12-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:04:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:04:12-0400 [-]     runApp(config)
2011-09-24 00:04:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:04:12-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:04:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:04:12-0400 [-]     self.postApplication()
2011-09-24 00:04:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:04:12-0400 [-]     self.startApplication(self.application)
2011-09-24 00:04:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:04:12-0400 [-]     self.config['pidfile'])
2011-09-24 00:04:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:04:12-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:04:12-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:04:41-0400 [-] Log opened.
2011-09-24 00:04:41-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:04:41-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:04:41-0400 [-] Traceback (most recent call last):
2011-09-24 00:04:41-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:04:41-0400 [-]     run()
2011-09-24 00:04:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:04:41-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:04:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:04:41-0400 [-]     runApp(config)
2011-09-24 00:04:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:04:41-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:04:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:04:41-0400 [-]     self.postApplication()
2011-09-24 00:04:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:04:41-0400 [-]     self.startApplication(self.application)
2011-09-24 00:04:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:04:41-0400 [-]     self.config['pidfile'])
2011-09-24 00:04:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:04:41-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:04:41-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:05:08-0400 [-] Log opened.
2011-09-24 00:05:08-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:05:08-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:05:08-0400 [-] Traceback (most recent call last):
2011-09-24 00:05:08-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:05:08-0400 [-]     run()
2011-09-24 00:05:08-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:05:08-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:05:08-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:05:08-0400 [-]     runApp(config)
2011-09-24 00:05:08-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:05:08-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:05:08-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:05:08-0400 [-]     self.postApplication()
2011-09-24 00:05:08-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:05:08-0400 [-]     self.startApplication(self.application)
2011-09-24 00:05:08-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:05:08-0400 [-]     self.config['pidfile'])
2011-09-24 00:05:08-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:05:08-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:05:08-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:07:23-0400 [-] Log opened.
2011-09-24 00:07:23-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:07:23-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:07:23-0400 [-] Traceback (most recent call last):
2011-09-24 00:07:23-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:07:23-0400 [-]     run()
2011-09-24 00:07:23-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:07:23-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:07:23-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:07:23-0400 [-]     runApp(config)
2011-09-24 00:07:23-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:07:23-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:07:23-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:07:23-0400 [-]     self.postApplication()
2011-09-24 00:07:23-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:07:23-0400 [-]     self.startApplication(self.application)
2011-09-24 00:07:23-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:07:23-0400 [-]     self.config['pidfile'])
2011-09-24 00:07:23-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:07:23-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:07:23-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:35:35-0400 [-] Log opened.
2011-09-24 00:35:35-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:35:35-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:35:35-0400 [-] Traceback (most recent call last):
2011-09-24 00:35:35-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:35:35-0400 [-]     run()
2011-09-24 00:35:35-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:35:35-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:35:35-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:35:35-0400 [-]     runApp(config)
2011-09-24 00:35:35-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:35:35-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:35:35-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:35:35-0400 [-]     self.postApplication()
2011-09-24 00:35:35-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:35:35-0400 [-]     self.startApplication(self.application)
2011-09-24 00:35:35-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:35:35-0400 [-]     self.config['pidfile'])
2011-09-24 00:35:35-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:35:35-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:35:35-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:35:49-0400 [-] Log opened.
2011-09-24 00:35:49-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:35:49-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:35:49-0400 [-] Traceback (most recent call last):
2011-09-24 00:35:49-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:35:49-0400 [-]     run()
2011-09-24 00:35:49-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:35:49-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:35:49-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:35:49-0400 [-]     runApp(config)
2011-09-24 00:35:49-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:35:49-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:35:49-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:35:49-0400 [-]     self.postApplication()
2011-09-24 00:35:49-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:35:49-0400 [-]     self.startApplication(self.application)
2011-09-24 00:35:49-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:35:49-0400 [-]     self.config['pidfile'])
2011-09-24 00:35:49-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:35:49-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:35:49-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:53:58-0400 [-] Log opened.
2011-09-24 00:53:58-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:53:58-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:53:58-0400 [-] Traceback (most recent call last):
2011-09-24 00:53:58-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:53:58-0400 [-]     run()
2011-09-24 00:53:58-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:53:58-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:53:58-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:53:58-0400 [-]     runApp(config)
2011-09-24 00:53:58-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:53:58-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:53:58-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:53:58-0400 [-]     self.postApplication()
2011-09-24 00:53:58-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:53:58-0400 [-]     self.startApplication(self.application)
2011-09-24 00:53:58-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:53:58-0400 [-]     self.config['pidfile'])
2011-09-24 00:53:58-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:53:58-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:53:58-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:54:34-0400 [-] Log opened.
2011-09-24 00:54:34-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:54:34-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:54:34-0400 [-] Traceback (most recent call last):
2011-09-24 00:54:34-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:54:34-0400 [-]     run()
2011-09-24 00:54:34-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:54:34-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:54:34-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:54:34-0400 [-]     runApp(config)
2011-09-24 00:54:34-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:54:34-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:54:34-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:54:34-0400 [-]     self.postApplication()
2011-09-24 00:54:34-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:54:34-0400 [-]     self.startApplication(self.application)
2011-09-24 00:54:34-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:54:34-0400 [-]     self.config['pidfile'])
2011-09-24 00:54:34-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:54:34-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:54:34-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:55:07-0400 [-] Log opened.
2011-09-24 00:55:07-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:55:07-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:55:07-0400 [-] Traceback (most recent call last):
2011-09-24 00:55:07-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:55:07-0400 [-]     run()
2011-09-24 00:55:07-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:55:07-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:55:07-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:55:07-0400 [-]     runApp(config)
2011-09-24 00:55:07-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:55:07-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:55:07-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:55:07-0400 [-]     self.postApplication()
2011-09-24 00:55:07-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:55:07-0400 [-]     self.startApplication(self.application)
2011-09-24 00:55:07-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:55:07-0400 [-]     self.config['pidfile'])
2011-09-24 00:55:07-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:55:07-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:55:07-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:55:15-0400 [-] Log opened.
2011-09-24 00:55:15-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:55:15-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:55:15-0400 [-] Traceback (most recent call last):
2011-09-24 00:55:15-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:55:15-0400 [-]     run()
2011-09-24 00:55:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:55:15-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:55:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:55:15-0400 [-]     runApp(config)
2011-09-24 00:55:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:55:15-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:55:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:55:15-0400 [-]     self.postApplication()
2011-09-24 00:55:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:55:15-0400 [-]     self.startApplication(self.application)
2011-09-24 00:55:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:55:15-0400 [-]     self.config['pidfile'])
2011-09-24 00:55:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:55:15-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:55:15-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:55:27-0400 [-] Log opened.
2011-09-24 00:55:27-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:55:27-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:55:27-0400 [-] Traceback (most recent call last):
2011-09-24 00:55:27-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:55:27-0400 [-]     run()
2011-09-24 00:55:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:55:27-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:55:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:55:27-0400 [-]     runApp(config)
2011-09-24 00:55:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:55:27-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:55:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:55:27-0400 [-]     self.postApplication()
2011-09-24 00:55:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:55:27-0400 [-]     self.startApplication(self.application)
2011-09-24 00:55:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:55:27-0400 [-]     self.config['pidfile'])
2011-09-24 00:55:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:55:27-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:55:27-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:55:28-0400 [-] Log opened.
2011-09-24 00:55:28-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:55:28-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:55:28-0400 [-] Traceback (most recent call last):
2011-09-24 00:55:28-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:55:28-0400 [-]     run()
2011-09-24 00:55:28-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:55:28-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:55:28-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:55:28-0400 [-]     runApp(config)
2011-09-24 00:55:28-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:55:28-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:55:28-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:55:28-0400 [-]     self.postApplication()
2011-09-24 00:55:28-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:55:28-0400 [-]     self.startApplication(self.application)
2011-09-24 00:55:28-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:55:28-0400 [-]     self.config['pidfile'])
2011-09-24 00:55:28-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:55:28-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:55:28-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-24 00:56:41-0400 [-] Log opened.
2011-09-24 00:56:41-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-24 00:56:41-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-24 00:56:41-0400 [-] Traceback (most recent call last):
2011-09-24 00:56:41-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-24 00:56:41-0400 [-]     run()
2011-09-24 00:56:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-24 00:56:41-0400 [-]     app.run(runApp, ServerOptions)
2011-09-24 00:56:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-24 00:56:41-0400 [-]     runApp(config)
2011-09-24 00:56:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-24 00:56:41-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-24 00:56:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-24 00:56:41-0400 [-]     self.postApplication()
2011-09-24 00:56:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-24 00:56:41-0400 [-]     self.startApplication(self.application)
2011-09-24 00:56:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-24 00:56:41-0400 [-]     self.config['pidfile'])
2011-09-24 00:56:41-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-24 00:56:41-0400 [-]     f = open(pidfile,'wb')
2011-09-24 00:56:41-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-25 02:53:12-0400 [-] Log opened.
2011-09-25 02:53:12-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-25 02:53:12-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-25 02:53:12-0400 [-] Traceback (most recent call last):
2011-09-25 02:53:12-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-25 02:53:12-0400 [-]     run()
2011-09-25 02:53:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-25 02:53:12-0400 [-]     app.run(runApp, ServerOptions)
2011-09-25 02:53:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-25 02:53:12-0400 [-]     runApp(config)
2011-09-25 02:53:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-25 02:53:12-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-25 02:53:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-25 02:53:12-0400 [-]     self.postApplication()
2011-09-25 02:53:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-25 02:53:12-0400 [-]     self.startApplication(self.application)
2011-09-25 02:53:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-25 02:53:12-0400 [-]     self.config['pidfile'])
2011-09-25 02:53:12-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-25 02:53:12-0400 [-]     f = open(pidfile,'wb')
2011-09-25 02:53:12-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-25 02:53:27-0400 [-] Log opened.
2011-09-25 02:53:27-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-25 02:53:27-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-25 02:53:27-0400 [-] Traceback (most recent call last):
2011-09-25 02:53:27-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-25 02:53:27-0400 [-]     run()
2011-09-25 02:53:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-25 02:53:27-0400 [-]     app.run(runApp, ServerOptions)
2011-09-25 02:53:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-25 02:53:27-0400 [-]     runApp(config)
2011-09-25 02:53:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-25 02:53:27-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-25 02:53:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-25 02:53:27-0400 [-]     self.postApplication()
2011-09-25 02:53:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-25 02:53:27-0400 [-]     self.startApplication(self.application)
2011-09-25 02:53:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-25 02:53:27-0400 [-]     self.config['pidfile'])
2011-09-25 02:53:27-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-25 02:53:27-0400 [-]     f = open(pidfile,'wb')
2011-09-25 02:53:27-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-25 03:35:06-0400 [-] Log opened.
2011-09-25 03:35:06-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-25 03:35:06-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-25 03:35:06-0400 [-] Traceback (most recent call last):
2011-09-25 03:35:06-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-25 03:35:06-0400 [-]     run()
2011-09-25 03:35:06-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-25 03:35:06-0400 [-]     app.run(runApp, ServerOptions)
2011-09-25 03:35:06-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-25 03:35:06-0400 [-]     runApp(config)
2011-09-25 03:35:06-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-25 03:35:06-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-25 03:35:06-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-25 03:35:06-0400 [-]     self.postApplication()
2011-09-25 03:35:06-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-25 03:35:06-0400 [-]     self.startApplication(self.application)
2011-09-25 03:35:06-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-25 03:35:06-0400 [-]     self.config['pidfile'])
2011-09-25 03:35:06-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-25 03:35:06-0400 [-]     f = open(pidfile,'wb')
2011-09-25 03:35:06-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-25 03:35:26-0400 [-] Log opened.
2011-09-25 03:35:26-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-25 03:35:26-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-25 03:35:26-0400 [-] Traceback (most recent call last):
2011-09-25 03:35:26-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-25 03:35:26-0400 [-]     run()
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-25 03:35:26-0400 [-]     app.run(runApp, ServerOptions)
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-25 03:35:26-0400 [-]     runApp(config)
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-25 03:35:26-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-25 03:35:26-0400 [-]     self.postApplication()
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-25 03:35:26-0400 [-]     self.startApplication(self.application)
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-25 03:35:26-0400 [-]     self.config['pidfile'])
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-25 03:35:26-0400 [-]     f = open(pidfile,'wb')
2011-09-25 03:35:26-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
brock@brock-Linux:~$

---

### Post by patryk77 on 2011-09-25
The error I see that keeps repeating is:
IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'

You can run:
ls -l /var/run/
And see if the /var/run/fiveserver/ directory exists, but it probably doesn't (the software *should* create it if it doesn't, but that is probably a bug)
If it doesn't exist:
sudo mkdir -p /var/run/fiveserver
sudo /service/fiveserver/run &

If it still doesn't run, see what else is new in the log file.

---

### Post by bakan723 on 2011-09-25
brock@brock-Linux:~$ sudo mkdir -p /var/run/fiveserver
sudo: /var/lib/sudo/brock writable by non-owner (040777), should be mode 0700
[sudo] password for brock: 
brock@brock-Linux:~$ sudo /service/fiveserver/run &
[1] 16836
brock@brock-Linux:~$ sudo: /var/lib/sudo/brock writable by non-owner (040777), should be mode 0700


[1]+  Stopped                 sudo /service/fiveserver/run
brock@brock-Linux:~$ 

sorry for posting all the code im just not sure what information you need so I am just providing all that I have

---

### Post by bakan723 on 2011-09-25
again thank you so much for the help I cannot even begin to tell you how much it means to me.  I will be sure to pass on the favor and help anyone possible with ubuntu.  It is a great OS and I regret not switching earlier.

---

### Post by patryk77 on 2011-09-25
Did you run the:
```
sudo chmod 0700 /var/lib/sudo
# That should print the same warning
sudo echo aaa
# That should print "aaa" and no more warning.
```?

And post the output of ```
sudo tail -n 30 /var/log/fiveserver/fiveserver.log
```

---

### Post by bakan723 on 2011-09-25
brock@brock-Linux:~$ sudo chmod 0700 /var/lib/sudo
sudo: /var/lib/sudo/brock writable by non-owner (040777), should be mode 0700
[sudo] password for brock: 
brock@brock-Linux:~$ sudo echo aaa
sudo: /var/lib/sudo/brock writable by non-owner (040777), should be mode 0700
[sudo] password for brock: 
aaa
brock@brock-Linux:~$ sudo tail -n 30 /var/log/fiveserver/fiveserver.log
sudo: /var/lib/sudo/brock writable by non-owner (040777), should be mode 0700
[sudo] password for brock: 
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-25 03:35:26-0400 [-]     self.postApplication()
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-25 03:35:26-0400 [-]     self.startApplication(self.application)
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-25 03:35:26-0400 [-]     self.config['pidfile'])
2011-09-25 03:35:26-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-25 03:35:26-0400 [-]     f = open(pidfile,'wb')
2011-09-25 03:35:26-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
2011-09-25 04:05:15-0400 [-] Log opened.
2011-09-25 04:05:15-0400 [-] twistd 10.2.0 (/usr/bin/python 2.7.1) starting up.
2011-09-25 04:05:15-0400 [-] reactor class: twisted.internet.selectreactor.SelectReactor.
2011-09-25 04:05:15-0400 [-] Traceback (most recent call last):
2011-09-25 04:05:15-0400 [-]   File "/usr/bin/twistd", line 19, in <module>
2011-09-25 04:05:15-0400 [-]     run()
2011-09-25 04:05:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
2011-09-25 04:05:15-0400 [-]     app.run(runApp, ServerOptions)
2011-09-25 04:05:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
2011-09-25 04:05:15-0400 [-]     runApp(config)
2011-09-25 04:05:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
2011-09-25 04:05:15-0400 [-]     _SomeApplicationRunner(config).run()
2011-09-25 04:05:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 378, in run
2011-09-25 04:05:15-0400 [-]     self.postApplication()
2011-09-25 04:05:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 205, in postApplication
2011-09-25 04:05:15-0400 [-]     self.startApplication(self.application)
2011-09-25 04:05:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 306, in startApplication
2011-09-25 04:05:15-0400 [-]     self.config['pidfile'])
2011-09-25 04:05:15-0400 [-]   File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 267, in setupEnvironment
2011-09-25 04:05:15-0400 [-]     f = open(pidfile,'wb')
2011-09-25 04:05:15-0400 [-] IOError: [Errno 2] No such file or directory: '/var/run/fiveserver/fiveserver.pid'
brock@brock-Linux:~$

---

### Post by patryk77 on 2011-09-25
It no longer complains about the /var/lib/sudo directory, but it does about one of its files, so let's fix that:

sudo chmod 0700 /var/lib/sudo/brock

Then let's see why it doesn't create the file:
sudo ls -al /var/run/fiveserver/

---

### Post by bakan723 on 2011-09-25
i actually went into nautilus as root and changed permissions for that folder for my user and now it works like a charm........ i think.  so far so good

---

### Post by patryk77 on 2011-09-25
Good!

I don't see why it wouldn't work with sudo though?

Anyways, if it works that's great. The following couple resources should help out with understanding the permissions/sudo, so take a look at them some time if you're curious about the system... They will hopefully make it easier to deal with similar permission problems should they ever arise again :)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Any other problems, post back :)

---

### Post by bakan723 on 2011-09-25
hey man i have rebooted my pc and it seems i cannot start it again now and permissions i set look to be as i set them any thoughts?

---

### Post by patryk77 on 2011-09-25
Post the output of:
tail -n 30  /var/log/fiveserver/fiveserver.log
ls -al /var/run/fiveserver/

again.

---

