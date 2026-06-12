---
title: "Error message when trying to install vmware server on kubuntu 8.04"
date: 2008-04-27
forum: Virtualisation
---

### Post by VictorWarner on 2008-04-27
I have just installed kubuntu 8.04 and trying to install vmware server 1.05 with "sudo ./vmware-install.pl". Before I ran this command I installed linux headers, build-essential, but I am getting the following error message (that vmmon module cannot be built.

```
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
/tmp/vmware-config2/vmmon-only/linux/driver.c:147: warning: initialisation from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:151: warning: initialisation from incompatible pointer type
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

I would be grateful for any information on how to resolve this.

Victor Warner.

---

### Post by PilotJLR on 2008-04-27
Have you already applied the 116 any-any patch?

[http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html](http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html)

---

### Post by fjgaude on 2008-04-27
From:

[http://ubuntuforums.org/showthread.php?t=770873](http://ubuntuforums.org/showthread.php?t=770873) 

**Installing VMWare Server in Hardy**

This is a cleaned up copy of the instructions for installing the VMWare Server from tar.gz found at [http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976) with a correction thanks to forrestallen. Since the Hardy Beta forums are now locked I thought it might be best to make a copy here to allow further discussion if needed.

First install the packages needed by vmware.

```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install xinetd
```

for 64bit installs also install the ia32-libs

```
sudo apt-get install ia32-libs
```

Additionally I recommend installing the linux-header metapackage appropriate to your kernel. "sudo apt-get install linux-headers-generic" for desktops in the standard kernel and "sudo apt-get install linux-headers-server" for server installs. This makes it easier down the road, automatically pulling down the headers if the kernel gets updated.

next download vmware server and expand it out somewhere

```
tar -xvzf VMware-server-1.0.5-80187.tar.gz
```

then do the install

```
cd vmware-server-distrib
sudo ./vmware-install.pl
```

Answer the questions, the defaults are fine. Eventually it will start compiling and fail.

grab the any to any patch 116 from
[http://uruz.org/files/vmware-any-any-update-116.tgz](http://uruz.org/files/vmware-any-any-update-116.tgz)

```
wget http://uruz.org/files/vmware-any-any-update-116.tgz
tar -xvzf vmware-any-any-update-116.tgz
cd vmware-any-any-update116
sudo ./runme.pl
```

Finally you can configure vmware server (note this usually will be run automatically at the end of the any-any patch, no need to run it twice)

```
 sudo vmware-config.pl
```

answer all the questions and it should compile fine.

once installed I received an error trying to launch vmware so I cheated and copied the libraries over, which seems to have resolved that issue.

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

(I found this tip online as well but now I can not find the link.)

For 64 bit users there is one additional step in order to allow vmware console to launch:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

the solution came from [https://bugs.launchpad.net/ubuntu/+s...bs/+bug/177869](https://bugs.launchpad.net/ubuntu/+s...bs/+bug/177869) however I had to change libgdk_pixbuf-2.0.so.0.1200.3 to libgdk_pixbuf-2.0.so.0.1200.9.

if you get an error like this at the end of the compile step:

```
Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key
```

then create the key and cert files for vmware. (I think, though I am not certain, this came up because I had not yet installed the ia32-libs on my 64-bit machine prior to doing the initial install.)

```
sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt
```

Also note that I had a number of issues on one upgraded machine where I was using the partner repositories debs prior to the upgrade. I would recommend backing up your VMs and then removing the VMWare install completely prior to upgrading.

Let us know how you are doing.

---

### Post by VictorWarner on 2008-04-28
Following the suggestions worked. Thank you very much for the help.

Victor Warner.

---

### Post by fjgaude on 2008-04-28
It's amazing how many little details are required to get everything to work right. More needed to get USB support, eh?

It's a normal miracle to have virtualization and Linux work so well.

---

### Post by celsdogg on 2008-04-28
thanks a million for this! it worked beautifully!

---

### Post by Isthan on 2008-04-29
Hello, thanks for the guide and clarification on the information that is floating around.  I have completed the steps that you've listed and gotten this result at the end of runme.pl:

The configuration of VMware Server 1.0.5 build-80187 for Linux for this running kernel completed successfully.

Now when I go to applications > Other > VMWare Server Console, the program appears to load in the task bar and after about 10-12 seconds disappears and does not load.  Any advice?  The output of runme.pl notes that the virtual machine monitor is loaded.  Should I be able to use this gui?

---

### Post by fjgaude on 2008-04-29
> **Isthan said:**
> Hello, thanks for the guide and clarification on the information that is floating around.  I have completed the steps that you've listed and gotten this result at the end of runme.pl:

The configuration of VMware Server 1.0.5 build-80187 for Linux for this running kernel completed successfully.

Now when I go to applications > Other > VMWare Server Console, the program appears to load in the task bar and after about 10-12 seconds disappears and does not load.  Any advice?  The output of runme.pl notes that the virtual machine monitor is loaded.  Should I be able to use this gui?

I can't think of much to offer except to run the command as root, vmware.

See what happens. If that works, then try the GUI again. It should work from the GUI. That's the way to setup the guest.

---

### Post by PilotJLR on 2008-04-29
Did you already run these two commands?
```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```

If that doesn't do it, then run "vmware" in the terminal as your normal user and post the error message output.

---

### Post by PilotJLR on 2008-04-29
[disregard this post, cause i can't find how to delete it]   :-)

---

### Post by ozzon on 2008-05-27
I am trying to get this to work and it's all installed but when I attempt to start the vmware server it fails.
I did install the 116-any-any and followed all the above but I get this:
```

root@uniqs:/var/log# /etc/init.d/vmware start
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

root@uniqs:/var/log# /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

root@uniqs:/var/log# 
```

After a reboot if I try the same then I can run the config and afterwards it fails the same way... 
Logs are empty...

Any assistance welcome!

I just noticed this is for kubuntu, mine is ubuntu...

Ozz.

---

### Post by ozzon on 2008-05-28
After rebuild of the vmon module it shows this:```
root@uniqs:/home/ozz# /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed

```

When I tried to restart. then I'm back to where I was before...

Ozz.

---

### Post by ozzon on 2008-06-01
Bump???

Ozz.

---

### Post by ozzon on 2008-06-01
Solved my problem by removing the Vnic.

Ozz.

---

### Post by TpyKv on 2008-08-27
can you tell me how you did this? having no luck at the moment & might have the same problem as you. ..

---

