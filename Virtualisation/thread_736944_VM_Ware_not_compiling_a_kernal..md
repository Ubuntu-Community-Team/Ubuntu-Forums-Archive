---
title: "VM Ware not compiling a kernal."
date: 2008-03-27
forum: Virtualisation
---

### Post by chrispche on 2008-03-27
Hi  if I run the following I get:

chrispche@chrispche:/usr/bin$ sudo vmware-config.pl
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
your system (you need to have a C compiler installed on your system)? [no] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-12-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-12-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

chrispche@chrispche:/usr/bin$ 

Any fixes for this? Using Hardy Heron Beta.

Thanks,

---

### Post by koresho on 2008-03-27
I'm having the same error, even after downloading the vmware-any-any-114 patch. I'm guessing there is no kernel support for Hardy yet? Are we the first distro to use this kernel?

---

### Post by fjgaude on 2008-03-27
Well, I'm running Hardy and VMware server 1.0.5. Here's the link I used and everything else:


[http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976) Note #10

I went around the long way but I got VMWare server 1.04 installed. Here is what I did, hopefully it will help others. (I also realize the majority of this has been covered many times. I am just including everything because it is easier then figuring out where to start.)

First the obvious, install the supporting packages
Code:

sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install xinetd

next download vmware server and expand it out somewhere
Code:

tar -xvzf VMware-server-1.0.4-56528.tar.gz

then do the install
Code:

cd vmware-server-distrib
sudo ./vmware-install.pl

next, next, yada yada. Eventually it will start compiling and fail.

grab the any to any patch 115 from
[http://knihovny.cvut.cz/ftp/pub/vmwa...date115.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmwa...date115.tar.gz)
Code:

wget [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz)
tar -xvzf vmware-any-any-update115.tar.gz
cd vmware-any-any-update115
sudo ./runme.pl


Finally you can configure vmware server
Code:

 sudo vmware-config.pl

answer all the questions and it should compile fine.

once installed I received an error trying to launch vmware so I cheated and copied the libraries over, which seems to have resolved that issue.
Code:

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

For 64 bit users there is one additional step in order to allow vmware console to launch:
Code:

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8

the solution came from [https://bugs.launchpad.net/ubuntu/+s...bs/+bug/177869](https://bugs.launchpad.net/ubuntu/+s...bs/+bug/177869) however I had to change libgdk_pixbuf-2.0.so.0.1200.3 to libgdk_pixbuf-2.0.so.0.1200.8.

at that stage everything should be working.
__________________

---

### Post by chrispche on 2008-03-27
Ok when I run VMWare I get this now, after successfully compiling it:

chrispche@chrispche:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
chrispche@chrispche:~$ 

However also just to help other's out there I obtained this file which I ran and it compiled it successfully.

vmware-any-any-update-116.tgz

Google it you'll find it. It compiled VMWare for me. Now I just have the above problem.

---

### Post by fjgaude on 2008-03-27
Do you have the file "build-essential"?

If not do this:

```
sudo apt-get install build-essential
```

That will give you the latest gcc compiler.

---

### Post by chrispche on 2008-03-28
Actually I have solved this two post's ago that little cheat the guy was on about. I tried that and viola it's working. Yes I installed build essential a long time ago.

Anyhow it's working now.

Thanks for the input guy or girls.

---

### Post by sensman on 2008-04-01
Hi,

thank you for your great tip. It worked for me except for one thing:

When I tried to follow your instructions I got the following error when running ./runme.pl:

```

  CC [M]  /root/tmp/vmware-config6/vmmon-only/common/cpuid.o
In Datei, eingefügt von include/asm/bitops.h:2,
                 von /root/tmp/vmware-config6/vmmon-only/./include/vcpuset.h:74,
                 von /root/tmp/vmware-config6/vmmon-only/./include/modulecall.h:23,
                 von /root/tmp/vmware-config6/vmmon-only/common/vmx86.h:18,
                 von /root/tmp/vmware-config6/vmmon-only/common/hostif.h:18,
                 von /root/tmp/vmware-config6/vmmon-only/common/cpuid.c:14:
include/asm/bitops_32.h:9:2: Fehler: #error only <linux/bitops.h> can be included directly
make[2]: *** [/root/tmp/vmware-config6/vmmon-only/common/cpuid.o] Fehler 1
make[1]: *** [_module_/root/tmp/vmware-config6/vmmon-only] Fehler 2

```

I could solve this by using the newer version vmware-any-any-update116 which you can download here: [http://vmkernelnewbies.googlegroups.com/web/vmware-any-any-update-116.tgz]("http://vmkernelnewbies.googlegroups.com/web/vmware-any-any-update-116.tgz")

Hope this helps people having the same problem.

Cheers,

Alex.

---

