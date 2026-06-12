---
title: "Vmware  WSK 9 kernel header 3.8 generic not found"
date: 2013-01-23
forum: Virtualisation
---

### Post by vrzs on 2013-01-23
Hello, 
while trying to install vmware wsk-9 on Ubuntu (kernel 3.8) I have a message that says : 
kernel headers for version 3.8.xxx were not found.

I have them installed along with build essential.
I 've read many post on that, but it still does not work.

What can I do.

Best of all .

V.

---

### Post by adamski99 on 2013-01-27
i had same problem and this solved it for me:

[http://slackblogs.blogspot.co.uk/2012/11/vmware-workstation-901-and-linux-kernel_18.html](http://slackblogs.blogspot.co.uk/2012/11/vmware-workstation-901-and-linux-kernel_18.html)


if you create a symbolic link to the moved header:
ln -s /usr/src/linux-3.7-rc6/include/generated/uapi/linux/version.h \ /usr/src/linux-3.7-rc6/include/linux/version.h

replace linux-3.7-rc6 with your kernel version.

this fixed it for me

hope it helps

ads

---

### Post by swex on 2013-02-21
created bash script to handle problems with VMware Player on 13.04
[http://paste.kde.org/677882/](http://paste.kde.org/677882/)

---

### Post by Script Warlock on 2013-02-25
thanks for this got my vmware player up and running on ubuntu 13.04.

---

### Post by gorgor_bay on 2013-03-06
Thanks for the script, however vmware modules are still not compiling on my system (3.8.0-10-generic)

Here is the output:
```
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: entrant dans le répertoire « /tmp/modconfig-LNBFOK/vmmon-only »
/usr/bin/make -C /lib/modules/3.8.0-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/linux/driver.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/linux/hostif.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/apic.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/comport.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/cpuid.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/memtrack.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/phystrack.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/task.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/common/vmx86.o
  CC [M]  /tmp/modconfig-LNBFOK/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/modconfig-LNBFOK/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/modconfig-LNBFOK/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/modconfig-LNBFOK/vmmon-only/vmmon.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: entrant dans le répertoire « /tmp/modconfig-LNBFOK/vmmon-only »
make[1]: « postbuild » est à jour.
make[1]: quittant le répertoire « /tmp/modconfig-LNBFOK/vmmon-only »
cp -f vmmon.ko ./../vmmon.o
make: quittant le répertoire « /tmp/modconfig-LNBFOK/vmmon-only »
Using 2.6.x kernel build system.
make: entrant dans le répertoire « /tmp/modconfig-LNBFOK/vmnet-only »
/usr/bin/make -C /lib/modules/3.8.0-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/driver.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/hub.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/userif.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/netif.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/bridge.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/filter.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/procfs.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/smac_compat.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/smac.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/vnetEvent.o
  CC [M]  /tmp/modconfig-LNBFOK/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/modconfig-LNBFOK/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/modconfig-LNBFOK/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/modconfig-LNBFOK/vmnet-only/vmnet.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: entrant dans le répertoire « /tmp/modconfig-LNBFOK/vmnet-only »
make[1]: « postbuild » est à jour.
make[1]: quittant le répertoire « /tmp/modconfig-LNBFOK/vmnet-only »
cp -f vmnet.ko ./../vmnet.o
make: quittant le répertoire « /tmp/modconfig-LNBFOK/vmnet-only »
Using 2.6.x kernel build system.
make: entrant dans le répertoire « /tmp/modconfig-LNBFOK/vmblock-only »
/usr/bin/make -C /lib/modules/3.8.0-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/block.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/control.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/dentry.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/file.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/inode.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/module.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/stubs.o
  CC [M]  /tmp/modconfig-LNBFOK/vmblock-only/linux/super.o
/tmp/modconfig-LNBFOK/vmblock-only/linux/control.c: In function ‘ExecuteBlockOp’:
/tmp/modconfig-LNBFOK/vmblock-only/linux/control.c:285:9: attention : assignment from incompatible pointer type [enabled by default]
/tmp/modconfig-LNBFOK/vmblock-only/linux/control.c:296:4: attention : passing argument 1 of ‘putname’ from incompatible pointer type [enabled by default]
In file included from include/linux/proc_fs.h:5:0,
                 from /tmp/modconfig-LNBFOK/vmblock-only/linux/control.c:28:
include/linux/fs.h:2052:13: note: expected ‘struct filename *’ but argument is of type ‘char *’
/tmp/modconfig-LNBFOK/vmblock-only/linux/dentry.c:38:4: attention : initialization from incompatible pointer type [enabled by default]
/tmp/modconfig-LNBFOK/vmblock-only/linux/dentry.c:38:4: attention : (near initialization for ‘LinkDentryOps.d_revalidate’) [enabled by default]
/tmp/modconfig-LNBFOK/vmblock-only/linux/dentry.c: In function ‘DentryOpRevalidate’:
/tmp/modconfig-LNBFOK/vmblock-only/linux/dentry.c:104:7: attention : passing argument 2 of ‘actualDentry->d_op->d_revalidate’ makes integer from pointer without a cast [enabled by default]
/tmp/modconfig-LNBFOK/vmblock-only/linux/dentry.c:104:7: note: expected ‘unsigned int’ but argument is of type ‘struct nameidata *’
/tmp/modconfig-LNBFOK/vmblock-only/linux/inode.c:49:4: attention : initialization from incompatible pointer type [enabled by default]
/tmp/modconfig-LNBFOK/vmblock-only/linux/inode.c:49:4: attention : (near initialization for ‘RootInodeOps.lookup’) [enabled by default]
  LD [M]  /tmp/modconfig-LNBFOK/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "putname" [/tmp/modconfig-LNBFOK/vmblock-only/vmblock.ko] undefined!
  CC      /tmp/modconfig-LNBFOK/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/modconfig-LNBFOK/vmblock-only/vmblock.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: entrant dans le répertoire « /tmp/modconfig-LNBFOK/vmblock-only »
make[1]: « postbuild » est à jour.
make[1]: quittant le répertoire « /tmp/modconfig-LNBFOK/vmblock-only »
cp -f vmblock.ko ./../vmblock.o
make: quittant le répertoire « /tmp/modconfig-LNBFOK/vmblock-only »
Using 2.6.x kernel build system.
make: entrant dans le répertoire « /tmp/modconfig-LNBFOK/vmci-only »
/usr/bin/make -C /lib/modules/3.8.0-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/linux/driver.o
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/linux/vmciKernelIf.o
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/common/vmciContext.o
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/common/vmciDatagram.o
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/common/vmciDoorbell.o
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/common/vmciDriver.o
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/common/vmciEvent.o
  CC [M]  /tmp/modconfig-LNBFOK/vmci-only/common/vmciHashtable.o
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:127:4: erreur: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:127:4: erreur: un élément de l'initialisation n'est pas une constante
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:127:4: erreur: (near initialization for ‘vmci_driver.remove’)
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:1754:1: erreur: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vmci_probe_device’
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:1982:1: erreur: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vmci_remove_device’
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:119:12: attention : ‘vmci_probe_device’ used but never defined [enabled by default]
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:121:13: attention : ‘vmci_remove_device’ used but never defined [enabled by default]
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:2063:1: attention : ‘vmci_interrupt’ defined but not used [-Wunused-function]
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:2137:1: attention : ‘vmci_interrupt_bm’ defined but not used [-Wunused-function]
/tmp/modconfig-LNBFOK/vmci-only/linux/driver.c:1717:1: attention : ‘vmci_enable_msix’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[2]: *** [/tmp/modconfig-LNBFOK/vmci-only/linux/driver.o] Erreur 1
make[2]: *** Attente des tâches non terminées....
make[1]: *** [_module_/tmp/modconfig-LNBFOK/vmci-only] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.8.0-10-generic »
make: *** [vmci.ko] Erreur 2
make: quittant le répertoire « /tmp/modconfig-LNBFOK/vmci-only »
Unable to install all modules.  See log for details.

Done
```

Any idea what could be wrong?

---

### Post by gorgor_bay on 2013-03-06
Found the solution, had to modify the script according to: 

```
12c12
< cd vmci-only
---
> cd vmci-only/linux
19c19
< cd ..
---
> cd ../..
```

---

### Post by tangramor on 2013-05-17
I met the same problem with [COLOR=#0000cd]**VM8**[/COLOR] on ubuntu 13.04, and when I tried to use swex's script to fix it, I got some other problems on driver.c . 

1st, on VM8 the driver.c is located in **vmci-only/linux/driver.c** but not vmci-only/driver.c

2nd, there are some other errors after executed swex's script on [COLOR=#0000cd]**VM8**[/COLOR], you need to compare with the original driver.c to fix them. 

In fact, I think swex's script is not compliant with [COLOR=#0000cd]**VM8**[/COLOR], so I modified it to:

```

#!/bin/bash
if [[ $UID != 0 ]]; then
    echo "Please run this script with sudo:"
    echo "sudo $0 $*"
    exit 1
fi

sudo ln -s /usr/src/linux-headers-$(uname -r)/include/generated/uapi/linux/version.h /usr/src/linux-headers-$(uname -r)/include/linux/version.h

cd /usr/lib/vmware/modules/source
sudo cp vmci.orig.tar vmci.tar
sudo cp -n vmci.tar vmci.orig.tar

sudo tar -xf vmci.tar
cd vmci-only/linux/

sudo sed '127s/.*/   .remove = vmci_remove_device,/' driver.c > driver.c.tmp
mv driver.c.tmp driver.c
sudo sed '1744s/.*/static int/' driver.c > driver.c.tmp
mv driver.c.tmp driver.c
sudo sed '1972s/.*/static void/' driver.c > driver.c.tmp
mv driver.c.tmp driver.c
cd ../..
sudo tar -cf vmci.tar vmci-only/

sudo rm vmci-only/ -Rf
sudo vmware-modconfig --console --install-all
sudo rm /usr/src/linux-headers-$(uname -r)/include/linux/version.h
echo "Done"


```

---

### Post by Andy Q on 2013-05-17
Thanks! This works for me with VMWare Player 4 and Ubuntu 13.04

But can I put in a word for

```

sudo sed -i '127s/.*/   .remove = vmci_remove_device,/' driver.c

```
rather than creating temp files!

Andy

---

### Post by linux.girl on 2013-06-07
Hello, 

I have a similar problem, but with workstation 8 and ubuntu 13.04 - both 64 bit.

After the upgrade to linux-headers-3.8.0-23-generic, I could no longer launch vm workstation. Now I manage to open vmware workstation after I applied an old patch that I have, but the problem is that I cannot power on any of the vms that I have, I get these two errors:

Could not open /dev/vmmon: No such file or directory. Please make sure that the kernel module `vmmon' is loaded.

 
and
 
Failed to open device "/dev/vmci": No such file or directory Please make sure that the kernel module 'vmci' is loaded. Module DevicePowerOn power on failed.

 

If I run sudo modprobe vmmon and sudo modprobe vmci, the vms run - but after reboot, I have to run it again...

**Update: @[[COLOR=#000000]tangramor[/COLOR]]("http://ubuntuforums.org/member.php?u=1822087") - your script with the adaptation for vm8 solved my problem, thanks!!**

---

### Post by chrisguk on 2013-06-25
> **swex said:**
> created bash script to handle problems with VMware Player on 13.04
[http://paste.kde.org/677882/](http://paste.kde.org/677882/)

Works perfect, great post!

---

### Post by r_avital on 2013-06-27
Thanks everybody for the suggestions, but this is still failing on my end:

Ubuntu 13.04 64-bit, re-installed VMWare Player 3.1.0 which had been working fine for years prior to the updated to Ubuntu 13.04.  Attempting to run vmplayer gives the following:

```
Logging to /tmp/vmware-myname/setup-12352.log
ERROR: Module vmmon not found.
ERROR: Module vmnet not found.
ERROR: Module vmblock not found.
ERROR: Module vmci not found.
ERROR: Module vsock not found.
ERROR: Module vmmon not found.
ERROR: Module vmnet not found.
ERROR: Module vmblock not found.
ERROR: Module vmci not found.
ERROR: Module vsock not found.
ERROR: Module vmmon not found.
ERROR: Module vmnet not found.
ERROR: Module vmblock not found.
ERROR: Module vmci not found.
ERROR: Module vsock not found.
```
Then, a window asking me to install modules that need to be compiled into the running kernerl.  I click "install" - and the above list repeats, then exit to prompt.

What I've done so far: 

1. Manually created the sym-link:```
sudo ln -s /usr/src/linux-headers-3.8.0-25-generic/include/generated/uapi/linux/ /usr/src/linux-headers-3.8.0-25-generic/include/linux/version.h
```

2. Ran the script referenced above, with the following output:```
 
ln: failed to create symbolic link &#8216;/usr/src/linux-headers-3.8.0-25-generic/include/linux/version.h/version.h&#8217;: File exists
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/3.8.0-25-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:40:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
Unable to install vmmon
Done
```

The only part of the output that makes sense to me is the first line, unable to create the link because it already exists (I created it manually).

Any ideas, anyone, before I go back to Lucid?  Please?

TIA

---

### Post by chrisguk on 2013-06-27
Hi,

You seem to be going around in circles.  To ensure it works as desired I recommend completely removing VMware and all it's setting directories and application preferences.  Then reinstall.  There is a patch available on the VMware communities site, just Google " kernel 3.8 VMware patch Linux" and you should find it.  Apply the patch manually first then run the script on this thread.  I am currently building a complete solution to the problem and post post once it's complete.  

If you have any problems then please come back to me.

---

### Post by r_avital on 2013-06-27
Thank you so much, chris, and beyond that, thank you for working on a comprehensive solution.

I neglected to mention earlier, that I had already uninstalled and reinstalled vmplayer.  So based on that, I proceeded with the patch you mentioned.  I had errors, my apologies, I didn't bother to record them.

On a hunch, I went to the vmware site and downloaded vmplayer version 5.0.2 build-1031769, installed it, then ran the patch, with the following result:
```
./vmware9.k3.8rc4.patch: 1: ./vmware9.k3.8rc4.patch: ---: not found
./vmware9.k3.8rc4.patch: 2: ./vmware9.k3.8rc4.patch: +++: not found
./vmware9.k3.8rc4.patch: 3: ./vmware9.k3.8rc4.patch: @@: not found
./vmware9.k3.8rc4.patch: 4: ./vmware9.k3.8rc4.patch: .name: not found
./vmware9.k3.8rc4.patch: 5: ./vmware9.k3.8rc4.patch: .id_table: not found
./vmware9.k3.8rc4.patch: 6: ./vmware9.k3.8rc4.patch: .probe: not found
./vmware9.k3.8rc4.patch: 7: ./vmware9.k3.8rc4.patch: Syntax error: "(" unexpected


```

Again, on a hunch, in the hope that this version already had the patch, I tried to simply run the player.  I don't know for certain whether it has the patch or not, but this version runs fine for me.  I'm not "married" to any particular version of vmplayer, so this solution works for me.

Again, thank you so much, and enjoy the weekend!

Cheers

---

### Post by Tim_Larry on 2013-08-25
to apply the patch you need to run the patch command  ```
sudo patch -p0 < vmci.linux-3-8.patch 

```
but there are other steps you will need to do first.

[https://communities.vmware.com/message/2235951#2235951](https://communities.vmware.com/message/2235951#2235951)

---

