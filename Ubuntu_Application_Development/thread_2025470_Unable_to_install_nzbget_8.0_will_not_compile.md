---
title: "Unable to install nzbget 8.0 will not compile"
date: 2012-07-14
forum: Ubuntu Application Development
---

### Post by egandt on 2012-07-14
libsigc++-2.0-0c2a is already the newest version.
libsigc++-2.0-dev is already the newest version.
libsigc++-2.0-doc is already the newest version.
libsigc++-1.2-5c2 is already the newest version.
libsigc++-1.2-dev is already the newest version.
libsigc++-dev is already the newest version.
libsigc++0c2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


...
checking for ncurses.h... yes
checking for library containing refresh... -lncurses
checking whether to include code for par-checking... yes
checking for libsigc... yes
checking sigc++/type_traits.h usability... yes
checking sigc++/type_traits.h presence... yes
checking for sigc++/type_traits.h... yes
checking libpar2/libpar2.h usability... yes
checking libpar2/libpar2.h presence... yes
checking for libpar2/libpar2.h... yes
checking for library containing _ZN12Par2RepairerC1Ev... -lpar2
checking for libpar2 linking... yes
checking whether libpar2 supports cancelling... no
checking whether to use TLS/SSL... yes
checking gnutls/gnutls.h usability... yes
checking gnutls/gnutls.h presence... yes
checking for gnutls/gnutls.h... yes
checking for library containing gnutls_global_init... -lgnutls
checking for library containing gcry_control... -lgcrypt
checking whether to use an empty SIGCHLD handler... yes
checking whether to include all debugging code... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands


So the packages are installed and the config script works and finds everything, but as soon as I attempt to execute make I get the following:
nzbget.cpp:727:30: warning: ignoring return value of âssize_t write(int, const void*, size_t)â, declared with attribute warn_unused_result [-Wunused-result]
g++  -g -O2  -lxml2   -L/usr/lib -lsigc-2.0   -L/usr/lib -L/usr/lib -o nzbget  ArticleDownloader.o BinRpc.o ColoredFrontend.o Connection.o Decoder.o DiskState.o DownloadInfo.o Frontend.o Log.o LoggableFrontend.o NCursesFrontend.o NNTPConnection.o NZBFile.o NetAddress.o NewsServer.o Observer.o Options.o ParChecker.o PrePostProcessor.o QueueCoordinator.o QueueEditor.o RemoteClient.o RemoteServer.o Scanner.o Scheduler.o ScriptController.o ServerPool.o svn_version.o TLS.o Thread.o Util.o XmlRpc.o nzbget.o  -lgcrypt -lgnutls -lpar2 -lncurses -lxml2 -lpthread 
/usr/bin/ld: ParChecker.o: undefined reference to symbol 'sigc::trackable::trackable()'
/usr/bin/ld: note: 'sigc::trackable::trackable()' is defined in DSO /usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/libsigc-2.0.so so try adding it to the linker command line
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/libsigc-2.0.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[1]: *** [nzbget] Error 1
make[1]: Leaving directory `/usr/src/nzbget-0.8.0'
make: *** [all] Error 2


However this seems correctly configured and linked:
root@fireserver:/usr/src/nzbget-0.8.0# ldconfig -p | grep libsigc-2.0.so
        libsigc-2.0.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libsigc-2.0
.so.0
        libsigc-2.0.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libsigc-2.0.s
o


I'm unsure how to continue, and would perfer 8.0 than the old 7.2 which is the only package I can find for 12.04, but why the build issue, everything looks fine?


Thanks,
ERIC

---

### Post by egandt on 2012-07-16
Orginal command:
g++ -g -O2 -lxml2 -L/usr/lib -lsigc-2.0 -L/usr/lib -L/usr/lib -o nzbget ArticleDownloader.o BinRpc.o ColoredFrontend.o Connection.o Decoder.o DiskState.o DownloadInfo.o Frontend.o Log.o LoggableFrontend.o NCursesFrontend.o NNTPConnection.o NZBFile.o NetAddress.o NewsServer.o Observer.o Options.o ParChecker.o PrePostProcessor.o QueueCoordinator.o QueueEditor.o RemoteClient.o RemoteServer.o Scanner.o Scheduler.o ScriptController.o ServerPool.o svn_version.o TLS.o Thread.o Util.o XmlRpc.o nzbget.o -lgcrypt -lgnutls -lpar2 -lncurses -lxml2 -lpthread 

Working Command: 
g++  -g -O2  -lxml2   -L/usr/lib -L/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -lsigc-2.0   -L/usr/lib -L/usr/lib -o nzbget  ArticleDownloader.o BinRpc.o ColoredFrontend.o Connection.o Decoder.o DiskState.o DownloadInfo.o Frontend.o Log.o LoggableFrontend.o NCursesFrontend.o NNTPConnection.o NZBFile.o NetAddress.o NewsServer.o Observer.o Options.o ParChecker.o PrePostProcessor.o QueueCoordinator.o QueueEditor.o RemoteClient.o RemoteServer.o Scanner.o Scheduler.o ScriptController.o ServerPool.o svn_version.o TLS.o Thread.o Util.o XmlRpc.o nzbget.o  -lgcrypt -lgnutls -lpar2 -lncurses -lxml2 -lpthread -lsigc-2.0

Note that "-lsigc-2.0" is in the wrong location, when I added it at the end of the line it comiples correctly.  I do not see why this should be the case, but what works works

---

### Post by danger89 on 2012-12-14
Thank you so much! I edited the Makefile.

Before:
> LDFLAGS =  -lxml2   -L/usr/lib -lsigc-2.0 -L/usr/lib -L/usr/lib -L/usr/lib -L/usr/lib
LIBOBJS = 
LIBS = -lz -lssl -lpar2 -lncurses -lxml2 -lpthread

After:

> 
LDFLAGS =  -lxml2   -L/usr/lib -L/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -L/usr/lib -L/usr/lib -L/usr/lib -L/usr/lib
LIBOBJS = 
LIBS = -lz -lssl -lpar2 -lncurses -lxml2 -lpthread -lsigc-2.0

Is this some bug in nzbget or? I using nzbget 9.0

---

### Post by war59312 on 2013-02-11
Nicely done, thanks a lot!

For 9.1

Replace (Lines 172-174):

```
LDFLAGS =  -lxml2   -L/usr/lib -lsigc-2.0   -L/usr/lib -L/usr/lib -L/usr/lib
LIBOBJS = 
LIBS = -lz -lgcrypt -lgnutls -lpar2 -lncurses -lxml2 -lpthread
```

With (Lines 172-174):

```
LDFLAGS =  -lxml2   -L/usr/lib -L/usr/lib/x86_64-linux-gnu/sigc++-2.0/include   -L/usr/lib -L/usr/lib -L/usr/lib
LIBOBJS = 
LIBS = -lz -lgcrypt -lgnutls -lpar2 -lncurses -lxml2 -lpthread -lsigc-2.0
```

---

