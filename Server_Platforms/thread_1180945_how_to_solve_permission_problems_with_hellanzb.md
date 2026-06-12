---
title: "how to solve permission problems with hellanzb?"
date: 2009-06-07
forum: Server Platforms
---

### Post by musta78 on 2009-06-07
Ok.  This is what i get when i try to start hellanzb on my ubuntu 8.04.2 server.

magnus@server1:~$ hellanzb.py
An unexpected problem occurred, exiting: IOError'>: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 554, in main
    init(options)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 334, in init
    Hellanzb.Logging.initLogFile(logFile = logFile, debugLogFile = debugLogFile)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Logging.py", line 577, in initLogFile
    backupCount = backupCount)
  File "/usr/lib/python2.5/logging/handlers.py", line 109, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding)
  File "/usr/lib/python2.5/logging/handlers.py", line 61, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding)
  File "/usr/lib/python2.5/logging/__init__.py", line 770, in __init__
    stream = open(filename, mode)
IOError: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 20, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 554, in main
    init(options)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 334, in init
    Hellanzb.Logging.initLogFile(logFile = logFile, debugLogFile = debugLogFile)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Logging.py", line 577, in initLogFile
    backupCount = backupCount)
  File "/usr/lib/python2.5/logging/handlers.py", line 109, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding)
  File "/usr/lib/python2.5/logging/handlers.py", line 61, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding)
  File "/usr/lib/python2.5/logging/__init__.py", line 770, in __init__
    stream = open(filename, mode)
IOError: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'


It's a permission problem, but i don't know what to do.

---

### Post by drave99 on 2009-06-08
what happens if you run "touch /var/tmp/hellanzb.log"

cant see why you would not have rights to /var/tmp

---

### Post by musta78 on 2009-06-09
Thank you.  I wrote the command and started hellanzb again, and there it was.

Not sure what the touch command did, but it worked.  

Could you explain maybe?

---

### Post by musta78 on 2009-06-10
Ok, so after a new install I got the same message, and this time touch gave me an answer:

touch: cannot touch `/var/tmp/hellanzb.log': Permission denied

It's strange because it's only a file that tells what that has happened, like the name says a log file.  

But for some reason, after editing the config file, I get this error. And I only change where all the files would end up......

---

### Post by musta78 on 2009-06-10
Ok, now I'm just beeing stupid.  Forgot to launch the program with sudo........

---

### Post by drave on 2009-06-16
looks like that script doesnt create the file if it doesnt exist. touch is doing that

---

