---
title: "Vmware workstation"
date: 2008-06-12
forum: Virtualisation
---

### Post by SpenceMakesSense on 2008-06-12
I have gotten vmware workstation and it came in a tar.gz file and I have no idea how to install it. I found a sh file and im thinking thats it but im not too sure about anything

---

### Post by chunchengch on 2008-06-12
extract the .tar.gz file you downloaded with the command tar -zvxf, such as

[COLOR="Red"]$ tar -zvxf VMware-workstation-6.0.3-80004.i386.tar.gz[/COLOR]

after that, a folder vmware-distrib will be created, then run these commands to install VMware Workstation, you may just press enter for all the questions asked in the installation procedure.

[COLOR="Red"]$ cd vmware-distrib
$ sudo ./vmware-install.pl[/COLOR]

---

### Post by 2K2GTP on 2008-06-12
I too am trying to install/run VMware workstation, however I am trying to install VMware-workstation-6.0.4-93057.i386.tar.gz.  I have extracted the files, ran the install, with out running the config (per instructions I found on-line), and then ran the vmware-any-any-update-116 patch and ran the config from there.  It installed and I can launch it, but when I go to create new virtual machines within VMware I get the following error message.

*vmmon module expecting 168.0, got 167.0.  You have an incorrect version of the 'vmmon' kernel module. Try reinstalling VMware Workstation.*

I have re-ran the install multiple times and I keep getting the same thing.  

Does anyone have any ideas of how I can resolve this?

I am running Ubuntu 8.04 w/ kernel 2.6.24.18-generic

---

### Post by chunchengch on 2008-06-12
> **2K2GTP said:**
> ... then ran the vmware-any-any-update-116 patch and ran the config from there...

you don't need to run this patch, it is for older version of VMware Workstation, just run these commands:


[COLOR="Red"]$ tar -zvxf VMware-workstation-6.0.4-93057.i386.tar.gz
$ cd vmware-distrib
$ sudo ./vmware-install.pl[/COLOR]

---

### Post by bodhi.zazen on 2008-06-12
See the sticky at the top of this forums, (although labeled "server" same basic instructions with workstation).

---

### Post by bodhi.zazen on 2008-06-12
> **chunchengch said:**
> you don't need to run this patch, it is for older version of VMware Workstation, just run these commands:


[COLOR="Red"]$ tar -zvxf VMware-workstation-6.0.4-93057.i386.tar.gz
$ cd vmware-distrib
$ sudo ./vmware-install.pl[/COLOR]

The any-any patch is not needed with the new and improved VMWare (Server 1.0.6). Not sure about Workstation...

---

### Post by 2K2GTP on 2008-06-12
Since I have/had VMware server installed on this machine earlier, (it was working) and then installed VMware Workstation 6.0.4, do you think that could be causing my problems?  Should I attempt to uninstall the old vmware server and uninstall my current vmware workstation install and then re-run the workstation install?  (How do you uninstall the apps, since they weren't installed as deb packages)  Sorry for the noob questions.

thanks in advance!

---

### Post by chunchengch on 2008-06-12
> **2K2GTP said:**
> Since I have/had VMware server installed on this machine earlier, (it was working) and then installed VMware Workstation 6.0.4, do you think that could be causing my problems? ...

I don't have VMware Server installed, but I think it would not cause any problem with both server and workstation installed.

> **2K2GTP said:**
> ... Should I attempt to uninstall the old vmware server and uninstall my current vmware workstation install and then re-run the workstation install? ...

The installer vmware-install.pl will remove the previous version or incomplete installation of VMware Workstation before it starts a new installation.

---

### Post by greenbag on 2008-06-13
if you come across this error:

```
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.
```

then this will help:

```
run installer until you get to where it asks to run vmware-config.pl


then open 2nd terminal, and:

   1. cd /usr/lib/vmware/modules/source
   2. sudo cp vmmon.tar vmmon.tar.orig
   3. sudo tar xvf vmmon.tar
   4. cd vmmon-only/include/
   5. sudo vi vcpuset.h
   6. change line 74 from: #include “asm/bitops.h” to: #include “linux/bitops.h”
   7. rm vmmon.tar
   8. sudo tar cvf vmmon.tar vmmon-only/
   9. sudo rm -rf vmmon-only/
  10. sudo vmware-config.pl
```

just installed yesterday  :)

---

