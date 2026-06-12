---
title: "PHP5, db4 and dba_open errors"
date: 2011-09-28
forum: Server Platforms
---

### Post by ktmom on 2011-09-28
This is the error:

```
PHP Warning:  dba_open(/path/to/file/removed.com.db,wd): Driver initialization failed for handler: db4:
```

The back story - 

Installing Vadmin plugin for Squirrelmail.  The system relies on using some flavor of dbm to save configuration info.  My system (packages installed from repositories) offers db4 as a choice.  More typically, this module is setup with gdbm.

Based on [Debian Bug report logs]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565242") it's been suggested the problem I'm experiencing may be with the version of libdm that is in use.  I've not been clever enough to confirm which package is used.

Unfortunately, I'm in a bit over my head since I don't know how to enable gdbm (I suppose PHP needs to be recompiled). Or I could update the libdm which handles life better, but since I can't figure out what package it's part of ...

Can someone please help me get onto the right track? 

```

Server info:
   Ubuntu Linux 10.04.3
   Linux 2.6.39.1-linode34 on i686
   Apache/2.2.14 (Ubuntu)


phphInfo;
   PHP Version 5.3.2-1ubuntu4.9
   server is protected with the Suhosin Patch 0.9.9.1
   Zend Engine v2.3.0

   dba
       DBA support     enabled
       Supported handlers      cdb cdb_make db4 inifile flatfile

       Directive       Local Value     Master Value
       dba.default_handler     db4     db4
```

---

