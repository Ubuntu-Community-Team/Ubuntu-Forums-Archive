---
title: "VMware Workstation problem with Hardy 8.04"
date: 2008-04-27
forum: Virtualisation
---

### Post by bmwman on 2008-04-27
I'm trying to install VmWare workstation 6.0.3. It installed successfully and i have the shortcuts in the menu for it. Anyway, when i run the configuration script i get some error. I tried the patch i found online and it crashes right before the end. I tried this patch vmware-any-any-update116.

Here is what i get:

Trying to find a suitable vmnet module for your running kernel.

None of the pre-built vmnet modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmnet module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Unknown VMware Workstation 6.0.3 build 80004 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmnet-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config4/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config4/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config4/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config4/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config4/vmnet-only/bridge.o
/tmp/vmware-config4/vmnet-only/bridge.c:35:8: error: "defined" cannot be used as a macro name
make[2]: *** [/tmp/vmware-config4/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Any ideas how to make it work?? Thanks in advance

---

### Post by coloured on 2008-04-27
I downloaded the beta [http://communities.vmware.com/community/beta/workstation6.5](http://communities.vmware.com/community/beta/workstation6.5)
which works, but its slow because debugging is enabled and can't be disabled.

Im going for virtualbox instead
[www.virtualbox.org](www.virtualbox.org)

---

### Post by gary vollink on 2008-04-27
You might be able to follow my vmware-player work-around.  It looks like the same error.

[http://ubuntuforums.org/showthread.php?t=769821](http://ubuntuforums.org/showthread.php?t=769821)

---

### Post by bmwman on 2008-04-28
I downloaded the new beta 6.5 and works fine. I have Vmware Workstation in Windows and i can convert my current system with XP Pro to virtual and open it inside Ubuntu. Saves me time to reinstall everything over again. I've tried the method with Vmware server but seems too complicated and i'm not fond of the web based interface on VMware server.

Thanks for the help.

---

### Post by pppluka on 2008-04-28
Hello.

As I wrote in another thread, solution below is for Player, not Workstation, so solution does not apply directly to Workstation...

[http://linhost.info/index.php/archives/166](http://linhost.info/index.php/archives/166)

It worked very well for me. I was one of the users, for whom, after Hardy Heron install, vmware player stopped working, but now it is o.k.

---

### Post by smittex on 2008-04-28
I have the same issue. VMWare Workstation 6.0, Ubuntu 8.04, VMWare-any-any update 116.  after installing build-essential, i get the following error:

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config4/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config4/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config4/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config4/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config4/vmnet-only/bridge.o
/tmp/vmware-config4/vmnet-only/bridge.c:35:8: error: "defined" cannot be used as a macro name
make[2]: *** [/tmp/vmware-config4/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Anyone have a workaround?

---

### Post by bmwman on 2008-04-28
> **smittex said:**
> I have the same issue. VMWare Workstation 6.0, Ubuntu 8.04, VMWare-any-any update 116.  after installing build-essential, i get the following error:

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config4/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config4/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config4/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config4/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config4/vmnet-only/bridge.o
/tmp/vmware-config4/vmnet-only/bridge.c:35:8: error: "defined" cannot be used as a macro name
make[2]: *** [/tmp/vmware-config4/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Anyone have a workaround?

Download the new beta [http://communities.vmware.com/commun...workstation6.5](http://communities.vmware.com/commun...workstation6.5) . it worked for me without any patching on Hardy 8.04. Also I have VM ware workstation in Windows and converted my whole system to virtual. I didn't have to reinstall anything and works great.

---

### Post by charon79m on 2008-05-03
I'm running into this same error when installing VMWare Server on 8.04 as well.

---

### Post by agurk on 2008-05-03
There's a problem with any-any-update116, I had to do the following:

cd vmware-any-any-update116
tar -xf vmnet.tar
nano vmnet-only/bridge.c
On line 35, change #ifdef to #if
mv vmnet.tar vmnet.tar.orig
tar -cf vmnet.tar vmnet-only/
rm -rf vmnet-only/

And then finally:
sudo ./runme.pl

---

### Post by smittex on 2008-05-03
I was experiencing the same issues as all of you have after I upgraded to hardy.  I tried the 13, 14, 15, & 16 patches to no avail (I am on 64-bit).  I didn't necessarily want to go the route of the Server or Player edition, so I tried the 6.5 beta mentioned above but got into some issues while in the VM.  Finally, I went to the VM site and downloaded the eval of the latest workstation public release (64-bit tar.gz install); of course, I had to sign up for a new account because I already "tried" an older version.  Installed perfeclty and works wonderfully now.

---

### Post by SniperSlap on 2008-05-07
I'm now getting:

 bridge-wlan0: enabling the bridge
 bridge-wlan0: is a Wireless Adapter
 vmnet: You are trying to use wireless bridged networking together with
 vmnet: vmware-any-any-update.  This is not supported configuration, and
 vmnet: your wireless bridge will probably not work.


Strange considering the last version of linux & vmware bridged perfectly!  Hardy Heron has been a total step backwards for me in terms of productivity.  Set me back huge.

I know this can be done, it's just likely going to take the right combination of fiddling.  If anyone can help, it'd be appreciated!

---

### Post by agurk on 2008-05-08
The post from forum user Hauke-m helped me getting my wireless bridge going:
[http://communities.vmware.com/message/887952](http://communities.vmware.com/message/887952)

---

