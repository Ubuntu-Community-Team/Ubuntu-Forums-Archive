---
title: "Docsis-Server 3.5"
date: 2009-06-12
forum: Server Platforms
---

### Post by DouganBrightaxe on 2009-06-12
Here is what I am trying to do: Install Docsis-Server 3.5 preferably to Ubuntu 9.04 64 bit server.

The package was originally designed for Red Hat so I know I have a bunch of work ahead of me.  I may be missing something for the dependencies to get this running, hopefully someone here can help with that.  

I am trying to install from this file - 
[http://users.accesscomm.ca/docsis_server/docsis-server-current.tar.bz2](http://users.accesscomm.ca/docsis_server/docsis-server-current.tar.bz2)

Continually I come back to this error:
checking for m4... /usr/bin/m4
configure: error:  GNU M4 is needed

I have a copy of my config.log @ [http://magnorock.googlepages.com/config.log](http://magnorock.googlepages.com/config.log) 

I have verified on all of the distros and m4 is right where it should be.  

I have tried on both i386 and 64 bit versions of Ubuntu and then I tried Fedora Core 11 just to see if it made a difference.  I keep getting to the same error on all of those systems.  I am a bit deadlocked right now and really would like to get this up and running.  If anyone can provide some advice or help I would be more then happy to hear it.

---

### Post by muzaka on 2009-07-13
Seems to be a problem with automake.

In "configure" change line 23768 to
```
  ac_is_gnu_m4=`echo $ac_m4_vers | grep -q GNU && echo GNU` ;
```

In "configure.in" change line 105 to
```
  ac_is_gnu_m4=`echo $ac_m4_vers | grep -q GNU && echo GNU` ;
```

---

