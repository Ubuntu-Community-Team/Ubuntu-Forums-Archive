---
title: "[SOLVED] VMWare wont run Realtime kernel"
date: 2008-09-09
forum: Virtualisation
---

### Post by blastfm on 2008-09-09
Hello,

I recently changed my kernel from generic to realtime to improve my latency problem with audio recording. 
Unfortunately, VMWare server wont run anymore.
Running **sudo /usr/bin/vmware-config.pl** doesn't help.
Here is the output of running that command

> blastfm@MY_home:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

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
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

And it just stops there. I have no idea where to look for the C header files (yes.. still a noob).

BTW, I'm on Hardy AMD64 version and the output of uname -r is
> blastfm@MY_home:~$ uname -r
2.6.24-19-rt


Hope some one can help.

---

### Post by veloce on 2008-09-09
Ready the sticky post on installation of vmware! [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

First code line is:

sudo apt-get install build-essential linux-headers-`uname -r` xinetd

You just need:

sudo apt-get install linux-headers-`uname -r`

---

### Post by blastfm on 2008-09-10
Thank you very much. This worked perfectly.

---

