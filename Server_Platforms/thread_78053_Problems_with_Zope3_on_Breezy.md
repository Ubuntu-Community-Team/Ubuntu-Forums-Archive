---
title: "Problems with Zope3 on Breezy"
date: 2005-10-17
forum: Server Platforms
---

### Post by thumper on 2005-10-17
I installed zope3 from the normal Breezy repositories.

I tried to set up an instance in my home directory just like both my zope books say...
```
tim@spike:~$ /usr/lib/zope3/bin/mkzopeinstance -u tim:tim -d zope-instance
Traceback (most recent call last):
  File "/usr/lib/zope3/bin/mkzopeinstance", line 45, in ?
    sys.exit(main(from_checkout=from_checkout))
  File "/usr/lib/python2.4/site-packages/zope/app/server/mkzopeinstance.py", line 48, in main
    return app.process()
  File "/usr/lib/python2.4/site-packages/zope/app/server/mkzopeinstance.py", line 111, in process
    os.chown(options.destination, uid, gid)
OSError: [Errno 1] Operation not permitted: '/home/tim/zope-instance'

```

It seemed to be an ownership issue, so I tried sudo.  This however made the instance owned by user **zope**, so I couldn't start it with ```
tim@spike:~/zope-instance$ ./bin/runzope
Traceback (most recent call last):
  File "./bin/runzope", line 48, in ?
    run()
  File "./bin/runzope", line 44, in run
    main(["-C", CONFIG_FILE] + sys.argv[1:])
  File "/usr/lib/python2.4/site-packages/zope/app/server/main.py", line 58, in main
    setup(load_options(args))
  File "/usr/lib/python2.4/site-packages/zope/app/server/main.py", line 166, in setup
    options.eventlog()
  File "/usr/lib/python2.4/site-packages/ZConfig/components/logger/factory.py", line 32, in __call__
    self.instance = self.create()
  File "/usr/lib/python2.4/site-packages/ZConfig/components/logger/logger.py", line 42, in create
    handler = handler_factory()
  File "/usr/lib/python2.4/site-packages/ZConfig/components/logger/factory.py", line 32, in __call__
    self.instance = self.create()
  File "/usr/lib/python2.4/site-packages/ZConfig/components/logger/handlers.py", line 69, in create
    logger = self.create_loghandler()
  File "/usr/lib/python2.4/site-packages/ZConfig/components/logger/handlers.py", line 87, in create_loghandler
    handler = loghandler.FileHandler(path)
  File "/usr/lib/python2.4/site-packages/ZConfig/components/logger/loghandler.py", line 34, in __init__
    StreamHandler.__init__(self, open(filename, mode))
IOError: [Errno 13] Permission denied: '/home/tim/zope-instance/log/z3.log'

```as I don't have permissions to write into zope's log dir.

Just as a hack, I sudo'ed a chown back to me for the entire directory, then the instance failed to start with ```
tim@spike:~/zope-instance/bin$ ./runzope
Traceback (most recent call last):
  File "./runzope", line 48, in ?
    run()
  File "./runzope", line 44, in run
    main(["-C", CONFIG_FILE] + sys.argv[1:])
  File "/usr/lib/python2.4/site-packages/zope/app/server/main.py", line 58, in main
    setup(load_options(args))
  File "/usr/lib/python2.4/site-packages/zope/app/server/main.py", line 169, in setup
    zope.app.appsetup.config(options.site_definition)
  File "/usr/lib/python2.4/site-packages/zope/app/appsetup/appsetup.py", line 52, in config
    context = xmlconfig.file(file, execute=execute)
  File "/usr/lib/python2.4/site-packages/zope/configuration/xmlconfig.py", line 557, in file
    context.execute_actions()
  File "/usr/lib/python2.4/site-packages/zope/configuration/config.py", line 622, in execute_actions
    callable(*args, **kw)
  File "/usr/lib/python2.4/site-packages/zope/app/onlinehelp/onlinehelp.py", line 123, in registerHelpTopic
    raise ConfigurationError(
zope.configuration.config.ConfigurationExecutionError: zope.configuration.exceptions.ConfigurationError: Help Topic definition /usr/lib/zope3/lib/python/zope/interface/README.txt does not exist
  in:
  File "/usr/lib/zope3/lib/python/zope/app/apidoc/bookmodule/book.zcml", line 11.4-16.10
      <bookchapter
          id="interface"
          title="Interfaces"
          doc_path="README.txt"
          parent="ifaceschema"
          />

```
I had a look, and it is right.  The file /usr/lib/zope3/lib/python/zope/interface/README.txt does not exist.

Has anyone got zope3 working on Breezy from the repositories?  Am I doing something really stupid?

---

### Post by thumper on 2005-10-18
Added to bugzilla.ubuntu.com:
[zope3 mkzopeinstance does not keep user id]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18025")
and
[New zope instance fails to start]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18026")

---

### Post by firehare on 2005-11-30
apt-get install python2.3 python2.3-zopeinterface

---

### Post by John Dooley on 2006-02-14
I had the same problem with the missing README.txt, as above. There was a russian version and I made a copy and renamed it README.txt. sudo bin/runzope then worked. I was able to see Zope 3 in Firefox. However, the port number was not the one that was displayed at installation. I used the one that runzope listed. 

I probably should fake up a english readme or pull down the correct one from zope.org. The code may have been unhappy to see russian and english, But. so far so good.

---

