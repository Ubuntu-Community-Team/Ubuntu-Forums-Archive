---
title: "Need help patching oss driver in Jackd2"
date: 2013-09-10
forum: Ubuntu Studio
---

### Post by Ishmael_Quartary on 2013-09-10
Hello,

I am using Ubuntu Studios 13.04 and need help patching the diff file below for jackd2 to contain the oss driver. Here it is

```
diff -Naur jackd2-1.9.7~dfsg/linux/wscript jj/linux/wscript
--- jackd2-1.9.7~dfsg/linux/wscript   2011-03-30 17:04:29.000000000 +0200
+++ jj/linux/wscript   2011-05-17 14:06:05.708972806 +0300
@@ -2,6 +2,8 @@
 # encoding: utf-8
 
 def configure(conf):
+    conf.env['BUILD_DRIVER_OSS'] = True
+
     conf.check_cfg(package='alsa', atleast_version='1.0.18', args='--cflags --libs')
     conf.env['BUILD_DRIVER_ALSA'] = conf.is_defined('HAVE_ALSA')
 
@@ -57,6 +59,8 @@
                        'alsa/ice1712.c'
                        ]
 
+    oss_driver_src = ['oss/JackOSSDriver.cpp', '../common/memops.c']
+ 
     ffado_driver_src = ['firewire/JackFFADODriver.cpp',
                         'firewire/JackFFADOMidiInput.cpp',
                         'firewire/JackFFADOMidiOutput.cpp',
@@ -67,6 +71,9 @@
     if bld.env['BUILD_DRIVER_ALSA'] == True:
         create_jack_driver_obj(bld, 'alsa', alsa_driver_src, "ALSA")
 
+    if bld.env['BUILD_DRIVER_OSS'] == True:
+        create_jack_driver_obj(bld, 'oss', oss_driver_src, "OSS")
+
     if bld.env['BUILD_DRIVER_FREEBOB'] == True:
         create_jack_driver_obj(bld, 'freebob', 'freebob/JackFreebobDriver.cpp', "LIBFREEBOB")
 
diff -Naur jackd2-1.9.7~dfsg/solaris/oss/JackBoomerDriver.cpp jj/solaris/oss/JackBoomerDriver.cpp
--- jackd2-1.9.7~dfsg/solaris/oss/JackBoomerDriver.cpp   2011-03-30 17:04:32.000000000 +0200
+++ jj/solaris/oss/JackBoomerDriver.cpp   2011-05-17 14:06:05.708972806 +0300
@@ -30,7 +30,7 @@
 #include "memops.h"
 
 #include <sys/ioctl.h>
-#include <sys/soundcard.h>
+#include "/usr/lib/oss/include/sys/soundcard.h"
 #include <fcntl.h>
 #include <iostream>
 #include <assert.h>
diff -Naur jackd2-1.9.7~dfsg/solaris/oss/JackOSSAdapter.cpp jj/solaris/oss/JackOSSAdapter.cpp
--- jackd2-1.9.7~dfsg/solaris/oss/JackOSSAdapter.cpp   2011-03-30 17:04:32.000000000 +0200
+++ jj/solaris/oss/JackOSSAdapter.cpp   2011-05-17 14:06:05.708972806 +0300
@@ -23,7 +23,7 @@
 #include "memops.h"
 
 #include <sys/ioctl.h>
-#include <sys/soundcard.h>
+#include "/usr/lib/oss/include/sys/soundcard.h"
 #include <fcntl.h>
 #include <iostream>
 #include <assert.h>
diff -Naur jackd2-1.9.7~dfsg/solaris/oss/JackOSSDriver.cpp jj/solaris/oss/JackOSSDriver.cpp
--- jackd2-1.9.7~dfsg/solaris/oss/JackOSSDriver.cpp   2011-03-30 17:04:32.000000000 +0200
+++ jj/solaris/oss/JackOSSDriver.cpp   2011-05-17 14:06:05.708972806 +0300
@@ -30,7 +30,7 @@
 #include "memops.h"
 
 #include <sys/ioctl.h>
-#include <sys/soundcard.h>
+#include "/usr/lib/oss/include/sys/soundcard.h"
 #include <fcntl.h>
 #include <iostream>
 #include <assert.h>

```

While looking inside jackd2 I found that oss driver option has been disabled in **debian** but enabled only in **solaris.** I have a good diff 
file for patching the oss driver in jackd2 but have been unsuccessful in showing the driver in debian and need help in what I am doing 
wrong. These are the steps that I have taken below.

```
apt-get install dpkg-dev
apt-get source jackd2
apt-get build-dep jackd2
ln -s /home/username/jackd2-1.9.9.5+20130127git15950eb1/solaris/oss/ /home/username/jackd2-1.9.9.5+20130127git15950eb1/linux/
cd jackd2-1.9.9.5+20130127git15950eb1
patch -p1 -i ../jackd2_oss.diff
```

When running patch -p1 -i ../jackd2_oss.diff the results are

```
(Stripping trailing CRs from patch.)
patching file linux/wscript
Hunk #1 FAILED at 2.
Hunk #2 succeeded at 67 with fuzz 2 (offset 10 lines).
Hunk #3 succeeded at 81 with fuzz 2 (offset 12 lines).
1 out of 3 hunks FAILED -- saving rejects to file linux/wscript.rej
(Stripping trailing CRs from patch.)
patching file solaris/oss/JackBoomerDriver.cpp
(Stripping trailing CRs from patch.)
patching file solaris/oss/JackOSSAdapter.cpp
(Stripping trailing CRs from patch.)
patching file solaris/oss/JackOSSDriver.cpp
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 30 with fuzz 1.
```

Then I get this error below when running dpkg-source --commit

```
dpkg-source: error: cannot represent change to jackd2-1.9.9.5+20130127git15950eb1/linux/oss:
dpkg-source: error:   new version is symlink to /home/xonar-studios/jackd2-1.9.9.5+20130127git15950eb1/solaris/oss/
dpkg-source: error:   old version is nonexistent
dpkg-source: error: unrepresentable changes to source
```

Can someone help me on what I am doing wrong concerning this error?

---

### Post by Ishmael_Quartary on 2013-09-17
This thread has been solved. I was able to use the patch on jackd2 version 1.9.7 and the oss driver built flawlessly. The bad news is I could not build it from the higher versions above jackd2-1.9.7 using this patch. But the good news is I used the built oss driver from this patch and applied it to the higher versions of jackd2 and it runs great when I start up jack server.

If anyone has any questions how I successfully build the oss driver for jackd2 and how to get it running pm me or reply to this thread.

Regards

IQ4

---

