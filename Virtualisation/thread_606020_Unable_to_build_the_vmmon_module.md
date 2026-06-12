---
title: "Unable to build the vmmon module"
date: 2007-11-07
forum: Virtualisation
---

### Post by bcom on 2007-11-07
Hello:

VMware server worked properly in Fiesty Fawn.  It no longer worked after upgrade to Gutsy Gibbon so I followed the "How to Install VMware server on Ubuntu 7.1." guide.  

All went well until I ran sudo ./runme.pl as instructed.  Got to the end and received the following message:

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from include/linux/poll.h:11,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:29:
include/linux/fs.h: In function ‘iget’:
include/linux/fs.h:1717: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Any suggestions or recomendations?

Thanks

---

### Post by geedew on 2007-11-09
I am having the exact same issue..

running on a toshiba m205 tablet 1.5ghz tabtop. Pretty sure this is a Gutsy Issue.  I followed the same guide you did and it errors out just as yours did.  I would imagine we need a new patch file for gutsy.

** Correction **
I actually recieved cc1plus warnings also, whcih gave errors in some functions.

---

### Post by bcom on 2007-11-10
Thanks for the feedback.

I think you are right about it being a Gutsy issue.  I've pretty much stopped using Windows and now only run it in VMware server.  

Let's hope for a fix in the near future.

---

### Post by sethvath on 2007-11-18
This is an issue with the kernel. Read the following link and apply the patch

[http://kb.vmware.com/selfservice/mic...xternalId=1623](http://kb.vmware.com/selfservice/mic...xternalId=1623)

In terminal: sudo ./runme.pl

You should be able to compile vmmon then

---

### Post by americanLoki on 2007-11-18
> **sethvath said:**
> This is an issue with the kernel. Read the following link and apply the patch

[http://kb.vmware.com/selfservice/mic...xternalId=1623](http://kb.vmware.com/selfservice/mic...xternalId=1623)

In terminal: sudo ./runme.pl

You should be able to compile vmmon then

The above instructions did work for me but it looks like the URL was cut short. Here is a link with the full URL
[Installing VMWare products on unsupported Linux distributions]("http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1623")

---

### Post by billmeek on 2007-11-18
The any-any patch isn't required if you download VMware Server 1.0.4 from [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by srnka on 2008-10-07
I have the same problem with installing VMware 1.0.4 to Ubuntu 8.04
The URL with patch didn't help me
Any idea?
Thanks

---

