---
title: "/usr/local/lib/libgmodule-2.0.so.0: could not read symbols: Invalid operation"
date: 2013-03-27
forum: Ubuntu Application Development
---

### Post by sherwin2008 on 2013-03-27
When complie Skeltrack, error occured, any suggestions?


config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

   Skeltrack 0.1.10
   =====================

              Install prefix:   /usr/local
    Build introspection data:   auto
     Build API documentation:   no
           Enable debug mode:   no
      Enable automated tests:   yes
              Build examples:   yes

root@ubuntu:~/Skeltrack# make
make  all-recursive
make[1]: Entering directory `/root/Skeltrack'
Making all in skeltrack
make[2]: Entering directory `/root/Skeltrack/skeltrack'
  GISCAN Skeltrack-0.1.gir
/usr/bin/ld: /root/Skeltrack/skeltrack/tmp-introspectkSTAQY/Skeltrack-0.1.o: undefined reference to symbol 'g_module_open'
/usr/bin/ld: note: 'g_module_open' is defined in DSO /usr/local/lib/libgmodule-2.0.so.0 so try adding it to the linker command line
/usr/local/lib/libgmodule-2.0.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/sh', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/root/Skeltrack/skeltrack/tmp-introspectkSTAQY/Skeltrack-0.1', '-export-dynamic', '-L.', '-lskeltrack-0.1', '-lm', '-pthread', '-L/usr/local/lib', '-lgio-2.0', '-lgobject-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/root/Skeltrack/skeltrack/tmp-introspectkSTAQY/Skeltrack-0.1.o']' returned non-zero exit status 1
make[2]: *** [Skeltrack-0.1.gir] Error 1
make[2]: Leaving directory `/root/Skeltrack/skeltrack'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/Skeltrack'
make: *** [all] Error 2
root@ubuntu:~/Skeltrack# ^C
root@ubuntu:~/Skeltrack#

---

### Post by schragge on 2013-03-30
Check that you have all prerequisites installed. See [http://tayyabnaseer.blogspot.de/2012/05/installing-skeltrack-on-ubuntu.html](http://tayyabnaseer.blogspot.de/2012/05/installing-skeltrack-on-ubuntu.html) The link is for Ubuntu 11.10, so some of the commands listed there probably need to be adjusted in order to work on a newer Ubuntu release.

---

### Post by sherwin2008 on 2013-04-02
Thank you. I redo the steps carefully . This error doesn't happen again.

---

