---
title: "Having trouble installing VMware Server in 8.04 RC."
date: 2008-04-20
forum: Virtualisation
---

### Post by diablo75 on 2008-04-20
Here's what I started it off with:

```
sudo aptitude install linux-headers-`uname -r` build-essential

sudo aptitude install xinetd
```

And then start the installer python script off as usual, after extracting the tar.gz

I get this at some point:

```
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:48:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config2/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by gnimsh on 2008-04-20
Hi I was having this same issue, so I visited the links from the error messages.  If you go here: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1623](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1623) and then use the any-any patch, it installs just as it normally would.

I extracted this folder to the vmware distrib source folder, and then did a CD into it, and did ls for the file listing.  then do sudo ./runme.pl and that will start the install process.

---

### Post by diablo75 on 2008-04-20
I tried the above patch, and it still screws up.  Here's the latest output:

```
~/Desktop/vmware-server-distrib$ sudo ./runme.pl
[sudo] password for zeke: 
Updating /usr/bin/vmware-config.pl ... now patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config3/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config3/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by gnimsh on 2008-04-20
I installed it but it won't start, so I'm stuck too.  

I was able to get virtualbox installed though.

---

### Post by robertchahine on 2008-04-20
look at this page , it might help
[http://ubuntuforums.org/showthread.php?p=4751634#post4751634](http://ubuntuforums.org/showthread.php?p=4751634#post4751634)

---

### Post by diablo75 on 2008-04-20
Well, I was dealing with this issue while also trying to install Virtual Box.  I used the plane old Add/Remove applet to install it.  Then I created a virtual machine and a drive and attempted to boot a puppy linux iso file.  Before it could boot, it said something about a virtual box linux kernel module not being installed.  So I did a search using synaptic, and I guess I installed the wrong one.  I was kind of forced into a situation where I would have to pick out a different kernel at boot.

Being a fresh system, I decided to take a lazy route and just wipe the HD.  SO, I'm going to be starting with a fresh install of 8.04 RC1.

That being the case, what directions/guide/tutorial should I follow for both Virtual Box and VMware Server to ensure a successful install the first time around.  I'm rather shocked that I've had issues with both.

---

### Post by gnimsh on 2008-04-20
You may just need to wait til the official release date in 4 days and then after its officially released they may have an update coming out to work with the kernel.  That'll be my guess.

---

### Post by diablo75 on 2008-04-20
> **gnimsh said:**
> You may just need to wait til the official release date in 4 days and then after its officially released they may have an update coming out to work with the kernel.  That'll be my guess.

Yeah, I think I'll do that.

---

### Post by apirak01 on 2008-04-21
I have the same problem too.

Here is the solution.
According to this post >> [http://communities.vmware.com/thread/131573](http://communities.vmware.com/thread/131573)
You have to install gcc c++ and use their "vmware-any-any-update116" (it's in previous link) to  solve this problem.
So I search that in Synaptic Package Management and then install g++-3.4.

Now it can build vmmon module.

But I found another problem when I start vmware.
It show >> 
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
<<

Yes, I have to search google again.
And this link >> [http://ubuntuforums.org/showthread.php?p=4719329](http://ubuntuforums.org/showthread.php?p=4719329)
tell me how to solve.
For me, just fix by enter these commands
#cd /usr/lib/vmware/lib/
#sudo mv libpng12.so.0/libpng12.so.0 libpng12.so.0/libpng12.so.0.disabled
#sudo ln -sf /usr/lib/libpng12.so.0 libpng12.so.0/libpng12.so.0
#sudo mv libgcc_s.so.1/libgcc_s.so.1 libgcc_s.so.1/libgcc_s.so.1.disabled
#sudo ln -sf /lib/libgcc_s.so.1 libgcc_s.so.1/libgcc_s.so.1

Now it work.

---

### Post by handband2 on 2008-04-25
If you are still having problems installing vmware-server, Martti Kuparinen has a great howto:  

[**[SIZE="2"]VMware Server Installation - hardy heron - 8.04[/SIZE]**]("http://users.piuha.net/martti/comp/ubuntu/en/server.html")
[http://users.piuha.net/martti/comp/ubuntu/en/server.html](http://users.piuha.net/martti/comp/ubuntu/en/server.html)

---

