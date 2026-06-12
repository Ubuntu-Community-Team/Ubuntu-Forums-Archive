---
title: "VMware server 2 vsock warning"
date: 2008-11-08
forum: Virtualisation
---

### Post by remy06 on 2008-11-08
Hi, 

Wondering if anyone encountered this vsock warning when installing vmware server 2 on intrepid.

```
None of the pre-built vsock modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vsock module.

Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
/tmp/vmware-config0/vsock-only/linux/util.c: In function ‘VSockVmciLogPkt’:
/tmp/vmware-config0/vsock-only/linux/util.c:157: warning: format not a string literal and no format arguments
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
  CC      /tmp/vmware-config0/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
Unable to make a vsock module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vsock.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

The VM communication interface socket family is used in conjunction with the VM
communication interface to provide a new communication path among guests and 
host.  The rest of this software provided by VMware Server is designed to work 
independently of this feature.  If you wish to have the VSOCK feature  you can 
install the driver by running vmware-config.pl again after making sure that 
gcc, binutils, make and the kernel sources for your running kernel are 
installed on your machine. These packages are available on your distribution's 
installation CD.
[ Press the Enter key to continue.] 

```
it says i got to make sure gcc,binutils,make and kernel sources for my running kernel are installed.Any advice on how to fix it?

---

### Post by _Poincare on 2008-11-09
I get the same error when I am trying to compile vmtools with Ubuntu 8.10. I once found another thread on this virtualization forum but no one replies and the "advice" people give is incorrect, just plain wrong, or they say "just use Ubuntu 8.04." Well, thanks for that lame advice, but I am asking about Ubunutu 8.10 not 8.04.  Basically it seems if you want to use VMWare and Ubuntu 8.10 it is not possible to install/compile the vmtools.  Too bad, wish more people could help on this or offer suggestions that "work!"

---

### Post by thierrybo on 2008-11-09
I experienced the exact same error with  "2.6.27-7-generic #1 SMP ... x86_64 GNU/Linux" and vmware-server 2.0.0-116503.x86_64 

Was installed in Hardy (working) and upgraded yesterday to Intrepid. Trying to solve this since one day. Tried [http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-module]("http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-module") and [http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627]("http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627") workarounds without success. 
Currently downloading vmware-server 2.0.0-122956.x86_64 to see if this chnage anything.

---

### Post by remy06 on 2008-11-10
i've tried vmware server 2 build 122956 x86 on intrepid following some of the links also but unsuccessful.Seems like there is still no solution for intrepid but am sure people are working it out so we may have to wait patiently.

---

### Post by pkc on 2008-11-11
I am having same issue after upgrading to intrepid kubuntu.  This will probably be a major issue for anyone relying on vmware server 2 for more than just hobby work.

There is a patch but apparently its only for 1.x  [http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/](http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/)


VMware server 2 error during install:

None of the pre-built vsock modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)? [yes]    

Extracting the sources of the vsock module.

Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vsock-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'                     
  CC [M]  /tmp/vmware-config3/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config3/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config3/vsock-only/linux/util.o
/tmp/vmware-config3/vsock-only/linux/util.c: In function ‘VSockVmciLogPkt’:
/tmp/vmware-config3/vsock-only/linux/util.c:157: warning: format not a string literal and no format arguments
  CC [M]  /tmp/vmware-config3/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config3/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-config3/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-config3/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/tmp/vmware-config3/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/tmp/vmware-config3/vsock-only/vsock.ko] undefined!
  CC      /tmp/vmware-config3/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config3/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config3/vsock-only'
Unable to make a vsock module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config3/vsock.o': -1 Unknown symbol in module

---

### Post by veloce on 2008-11-11
I have vmware server 2 working on 2 Intrepid installations, a desktop and a server.

When I upgraded these two machines to Intrepid I was using vmware server 1.06.  I had the vsock error on one machine when re-compiling the drivers but not the other.  I used the patch someone else mentioned to get that one working.

In one install I had difficulty with the header files.  I think the Intrepid upgrade failed to get the right ones.  This would be worth checking - perhaps uninstall and re-install them? 

In both cases I had a warning about the version of gcc (I think) being used but the final product worked fine.

I have also heard of people having success with vmware serve 2 and  the patch (even though it's supposedly only for 1.xx):  
[http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/](http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/)

---

### Post by remy06 on 2008-11-11
I experienced the gcc warning when trying to install vmware server 2 on hardy.

Now I got the vsock warning when trying to install on Intrepid.I have also tried the patch on vm server 2 but the warning still exist.Just to point out that I tried to proceed despite the warning and am able to complete the installation,although im not sure if it will introduce any errors during usage yet.

yeah the patch works fine for vm server 1.0x.

---

### Post by thierrybo on 2008-11-12
Hi,

I found the time to test again the vmware-update-2.6.27-5.5.7-2.tar.gz patch, but this time on a fresh 8.10 / 64 setup inside virtualbox (as a side note, it happens this vmware issue allowed me to discover again virtualbox). 

The build still fails on vsock, but this time  the web interface runs well, I can create VM, but not run them. Power up fails at 95 %, "Failed to initialize monitor device" but this is perhaps too "complicated" (who want to install a virtualization sofware inside a virtualized guest :) ). 

On my real machine Vmware 2 was installed before upgrade to 8.10, but removed it and installed it again, so this should not be different.

---

### Post by selllwow on 2008-11-12
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com), [sell gaia gold](http://www.virdeal.com), [sell ffxi gil](http://www.virdeal.com), [sell maple story mesos](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

### Post by remy06 on 2008-11-16
Hi thierrybo,

I have the same exact issue as yours when using the patch.Seems like its better to do without it.Except minus the vsock feature.

reference to this thread:
[http://ubuntuforums.org/showthread.php?p=6193469#post6193469]("http://ubuntuforums.org/showthread.php?p=6193469#post6193469")

---

### Post by bodhi.zazen on 2008-11-17
Rumor has it the next version of VMWare Server will fix this ;)

---

### Post by chaeron on 2008-11-20
> **bodhi.zazen said:**
> Rumor has it the next version of VMWare Server will fix this ;)

When???

---

### Post by CyberAngel on 2008-11-21
Same problem here of course :(

---

### Post by TpyKv on 2008-11-23
yeah same problem here too, every time I upgrade, I have similar issues...

DOH!

---

### Post by dev13 on 2008-11-25
> **remy06 said:**
> ```
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
```

This is because vsock depends on symbols from vmci module; the information is missing when vsock is built.  I got vsock to build  like this.  (You need to have already installed vmware tools.)

```

$ cd /tmp
$ tar xf /usr/lib/vmware-tools/modules/source/vmci.tar
$ tar xf /usr/lib/vmware-tools/modules/source/vsock.tar
$ cd vmci-only
$ make
$ cp Module.symvers ../vsock-only
$ cd ../vsock-only
$ make

```

Copy /tmp/vsock.o to the appropriate location in /lib/modules, rerun '[FONT="Courier New"]depmod -a[/FONT]' etc.

You also need to change
```

answer VSOCK_CONFED no

```
to
```

answer VSOCK_CONFED yes

```
in [FONT="Courier New"]/etc/vmware-tools/locations[/FONT] so that [FONT="Courier New"]/etc/init.d/vmware-tools[/FONT] will load vsock on startup.

---

### Post by thierrybo on 2008-11-25
? But vmware-tools is build on guest machines, here the error occurs within host?

---

### Post by msageg8 on 2008-11-26
you also delete any comments and trackbackslet's go to the forum Good Services[img]http://pic.piclib.net/sunvv/images/pic/new20_711.gif[/img]About all go to= Good Services ok!sites where they can express&#65281;[shanghai escorts](http://www.sh-escort.com/)-shangHai Escort of real photos[DC Contactors](http://www.kntelec.com/)-manufacture of heavy duty DC contactors[wow gold](http://www.wowpowerleveling-wow.com/)-wow powerleveling our primary service[chemical milling](http://www.etchingmachine.org/)-chemical milling help you to power

---

### Post by dev13 on 2008-11-27
Oops, I misread the original message.  I got a similar error trying to install vmware tools in a guest, and the above was how I solved *that*.

It does look like the cause for the error in the host is the same though.  Does vmci get compiled for the host also?  Can you get the Module.symvers file from it?

---

### Post by delgurth on 2008-11-28
> **dev13 said:**
> Oops, I misread the original message.  I got a similar error trying to install vmware tools in a guest, and the above was how I solved *that*.

It does look like the cause for the error in the host is the same though.  Does vmci get compiled for the host also?  Can you get the Module.symvers file from it?

Yup, you can get it in the host/server version of vmware also. 

I've patched the vmware-config.pl script with attached patch and with that I solved this issue. Thanks for pointing me at the right direction how to solve this.

This patch is for the most recent 2.0.0 version of VMWare: 122956

---

### Post by micahel on 2008-11-28
> **delgurth said:**
> Yup, you can get it in the host/server version of vmware also. 

I've patched the vmware-config.pl script with attached patch and with that I solved this issue. Thanks for pointing me at the right direction how to solve this.

This patch is for the most recent 2.0.0 version of VMWare: 122956

very good! tested the patch right now and it works OK! :)

```
kubuntu 8.10 intrepid

uname -a
Linux host 2.6.27-10-generic #1 SMP Fri Nov 21 19:19:18 UTC 2008 x86_64 GNU/Linux

lsmod |grep v
vmnet                  54732  3
vsock                  31536  0
vmci                   65832  1 vsock
vmmon                  85968  0
(...)

```

thanks for the good job!

cheers, michael

---

### Post by chaeron on 2008-11-29
Just upgraded my VMWare Workstation install to the "hot-off-the-press" 6.5.1 build-126130.

No joy in mudville, I'm afraid.  The same problem exists.  When you try to rebuild the vmware-toolbox, the vsock module will not insert in the Intrepid kernel.

Very disappointing....I was hoping that VMWare would have fixed this issue in the latest release.

So still no cut/paste between the host OS and the guest for now with Workstation 6.5.1.

Maybe next version....<sigh>

In the meantime, if some kind soul was able to create a similar patch for the Workstation /usr/bin/vmware-config-tools.pl script, that would be very much appreciated!

---

### Post by bond00 on 2008-11-29
Nice work Delgurth! Worked perfectly for me as well. For those who don't know how to patch the vmware-config.pl file it's simply:

sudo patch /usr/bin/vmware-config.pl /path/to/vmware-config.pl.patch

---

### Post by delgurth on 2008-12-01
> **bond00 said:**
> For those who don't know how to patch the vmware-config.pl file it's simply:

sudo patch /usr/bin/vmware-config.pl /path/to/vmware-config.pl.patch

Or if you want to patch it before installing vmware from sources you need to go inside the unpacked source folder (in my case vmware-server-distrib) and do:

patch bin/vmware-config.pl /path/to/vmware-config.pl.patch

No sudo needed then and the installer works right away, otherwise you need to fix it after installing vmware.

---

### Post by delgurth on 2008-12-01
Of course, this same problem occurs when you try to install the vmware-tools on for example an Ubuntu 8.10 server.

Attached patch fixes that problem in the vmware-config-tools.pl script.

You can either apply it to the source (in vmware-tools-distrib) by running

patch bin/vmware-config-tools.pl /path/to/vmware-config-tools.pl.patch

Or if you have already installed the tools

sudo patch /usr/bin/vmware-config-tools.pl /path/to/vmware-config-tools.pl.patch

---

### Post by delgurth on 2008-12-01
> **chaeron said:**
> 
In the meantime, if some kind soul was able to create a similar patch for the Workstation /usr/bin/vmware-config-tools.pl script, that would be very much appreciated!

I've now also created a patch for my version of the vmware-config-tools.pl script, but that is for the Server version of VMWare and not the Workstation. But you can try to apply the patch to a copy of the script, to see if the patch can be applied.

---

### Post by balboa41 on 2008-12-03
Thanks a lot!  It worked like a charm for me!   It would be interesting if VMware could patch it by default or Ubuntu to have it patched automatically.  Not that I'm lazy, just that I like when things install flawlessly.   ;)

---

### Post by emiel.prinsen on 2008-12-03
Thanks, now I am able to start up the virtual machine I needed so badly.

---

### Post by Nerdcentric on 2008-12-04
> **bond00 said:**
> Nice work Delgurth! Worked perfectly for me as well. For those who don't know how to patch the vmware-config.pl file it's simply:

sudo patch /usr/bin/vmware-config.pl /path/to/vmware-config.pl.patch

Thanks for posting the patch instructions--saved me a lot of searching! :)

---

### Post by gdfernandes on 2008-12-06
I was having the same problem and when I applied the patch to vmware-config.pl, the vsock module compilation worked just fine.

Thanks

---

### Post by Stumpy842 on 2008-12-07
> **delgurth said:**
> Of course, this same problem occurs when you try to install the vmware-tools on for example an Ubuntu 8.10 server.

Attached patch fixes that problem in the vmware-configure-tools.pl script.

You can either apply it to the source (in vmware-tools-distrib) by running

patch bin/vmware-configure-tools.pl /path/to/vmware-configure-tools.pl.patch

Or if you have already installed the tools

sudo patch /usr/bin/vmware-[COLOR="Red"]configure[/COLOR]-tools.pl /path/to/vmware-[COLOR="Red"]configure[/COLOR]-tools.pl.patch

Thank you for this! For some reason I had to re-diff the patch from the link above, perhaps some spurious whitespace chars, but after that it worked fine.

BTW, the line should be:

sudo patch /usr/bin/vmware-[COLOR="Red"]config[/COLOR]-tools.pl /path/to/vmware-[COLOR="Red"]config[/COLOR]-tools.pl.patch

Thanks again ;)

---

### Post by delgurth on 2008-12-08
> **Stumpy842 said:**
> Thank you for this! For some reason I had to re-diff the patch from the link above, perhaps some spurious whitespace chars, but after that it worked fine.

BTW, the line should be:

sudo patch /usr/bin/vmware-[COLOR="Red"]config[/COLOR]-tools.pl /path/to/vmware-[COLOR="Red"]config[/COLOR]-tools.pl.patch

Thanks again ;)

Fixed the config thingy in my original post, thanks. And odd that you needed to re-diff the patch, seems it's in Windows newline format, but the original has Unix newline formatting. Trying to fix that now.

---

### Post by nonZero on 2008-12-08
Hi delgurth!

Thanks for the patch!

I think that adding this to [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) would help out users to find this info easier.

Thanks again,

nonZero

---

### Post by thierrybo on 2008-12-09
Yes, 

this works. Unfortunately the web interface is not so reliable, it often stops responding at all .

---

### Post by mshenoy4573 on 2008-12-15
thanks delgruth....the patch worked for me too..
and thanks bond00 as I didnt know how to apply the patch being new to this

gr8 work people....love this community loadsssssss of help here

---

### Post by pkc on 2008-12-18
I have moved my VM's to the latest VirtualBox and have to admit I am impressed with its simple interface and performance. There were some tweaks getting USB to work but after that, more USB devices worked correctly with VirtualBox than with VMServer.  I like VMServer's remote web access but that is the only feature I miss.  VirtualBox is also letting me run Solaris10 (albeit slow), Solaris Express Community Edition, and OpenSolaris.

---

### Post by xbaez on 2008-12-18
> **delgurth said:**
> Of course, this same problem occurs when you try to install the vmware-tools on for example an Ubuntu 8.10 server.

Attached patch fixes that problem in the vmware-config-tools.pl script.

You can either apply it to the source (in vmware-tools-distrib) by running

patch bin/vmware-config-tools.pl /path/to/vmware-config-tools.pl.patch

Or if you have already installed the tools

sudo patch /usr/bin/vmware-config-tools.pl /path/to/vmware-config-tools.pl.patch

Awesome, it worked!

---

### Post by m_gr_01 on 2008-12-30
> **delgurth said:**
> Yup, you can get it in the host/server version of vmware also. 

I've patched the vmware-config.pl script with attached patch and with that I solved this issue. Thanks for pointing me at the right direction how to solve this.

This patch is for the most recent 2.0.0 version of VMWare: 122956

Wow, excellent job. It just worked, plainly perfect.
Thanks a lot. 

Same version of VMWare server, 
Ubuntu 8.10 and openSUSE 11.1, kernel 2.6.27.7-9.

---

### Post by topoignaz on 2009-01-03
It worked perfectly on my Ubuntu 8.10, kernel 2.6.27-11. Thank you delgurth & bond00

---

### Post by whaou on 2009-01-04
for me it still doesn't work. But I don't know whether it's the patch or something else. 

```
jonas@R2D2:~$ sudo patch /usr/bin/vmware-config.pl /home/jonas/Desktop/vmware-config.pl.patch 
patching file /usr/bin/vmware-config.pl
Hunk #1 succeeded at 4166 with fuzz 1 (offset 45 lines).
Hunk #2 FAILED at 4193.
1 out of 2 hunks FAILED -- saving rejects to file /usr/bin/vmware-config.pl.rej

```

sorry it's in german

```
Building the vmmon module.

Unknown VMware Server 2.0.0 build 122956 detected. Building for Server 1.0.0.
Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.27-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
/tmp/vmware-config1/vmmon-only/linux/hostif.c: In Funktion »HostIF_SetFastClockRate«:
/tmp/vmware-config1/vmmon-only/linux/hostif.c:3441: Warnung: Übergabe des Arguments 2 von »send_sig« entfernt Kennzeichner von Zeiger-Ziel-Typ
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
cc1plus: Warnung: Kommandozeilenoption "-Werror-implicit-function-declaration" ist gültig für C/ObjC, aber nicht für C++
cc1plus: Warnung: Kommandozeilenoption "-Wdeclaration-after-statement" ist gültig für C/ObjC, aber nicht für C++
cc1plus: Warnung: Kommandozeilenoption "-Wno-pointer-sign" ist gültig für C/ObjC, aber nicht für C++
cc1plus: Warnung: Kommandozeilenoption "-Wstrict-prototypes" ist gültig für Ada/C/ObjC, aber nicht für C++
In file included from /tmp/vmware-config1/vmmon-only/common/task.c:1195:
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function »void Task_Switch_V45(VMDriver*, Vcpuid)«:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2667: Warnung: »sysenterState.SysenterStateV45::validEIP« könnte in dieser Funktion uninitialisiert verwendet werden
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2667: Warnung: »sysenterState.SysenterStateV45::cs« könnte in dieser Funktion uninitialisiert verwendet werden
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2667: Warnung: »sysenterState.SysenterStateV45::rsp« könnte in dieser Funktion uninitialisiert verwendet werden
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2667: Warnung: »sysenterState.SysenterStateV45::rip« könnte in dieser Funktion uninitialisiert verwendet werden
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: module vmmon.ko uses symbol 'init_mm' marked UNUSED
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-9-generic'
cp -f vmmon.ko ./../vmmon.o
make: Verlasse Verzeichnis '/tmp/vmware-config1/vmmon-only'
The vmmon module loads perfectly into the running kernel.

```
........
```
Building the vmnet module.

Unknown VMware Server 2.0.0 build 122956 detected. Building for Server 1.0.0.
Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.27-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config1/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /tmp/vmware-config1/vmnet-only/vmnet.o
see include/linux/module.h for more information
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-9-generic'
cp -f vmnet.ko ./../vmnet.o
make: Verlasse Verzeichnis '/tmp/vmware-config1/vmnet-only'
The vmnet module loads perfectly into the running kernel.

```

I really don't have a clue what's that about but VMware still won't start.

edit: Ok I reinstalled Vmware and now everything works fine for me. thank you

---

### Post by Pullkick on 2009-01-07
Brilliant!

Thanks a lot!

---

### Post by SergZhukov on 2009-01-20
2delgurth: nice work!
Patched & builded.
But webAccess still does not start silently :(
Ubuntu 8.10 x64, 2.6.27-9-server, VMware server 2.0.0 122956

---

### Post by emtjr928 on 2009-01-29
Trying to apply this patch. Have it on my desktop. Running the command gives me this. What have I done wrong. I should note that I am using 2.6.27-11 kernel in ibex.

emtjr928@emtjr928-desktop:~/Desktop$ sudo patch /usr/bin/vmware-config.pl /home/emtjr928/desktop/vmware-config.pl.patch
patch: **** Can't open patch file /home/emtjr928/desktop/vmware-config.pl.patch : No such file or directory

---

### Post by bipolar on 2009-01-30
@emtjr928:
Capitalization counts. It's "Desktop" not "desktop" in the path to the patch.

---

### Post by emtjr928 on 2009-01-30
Doh! In his best Homer Simpson voice.
Thnx.

---

### Post by lucaspr on 2009-02-01
> **delgurth said:**
> Yup, you can get it in the host/server version of vmware also. 

I've patched the vmware-config.pl script with attached patch and with that I solved this issue. Thanks for pointing me at the right direction how to solve this.

This patch is for the most recent 2.0.0 version of VMWare: 122956

Thanx! This also fixed the problem here!!

---

### Post by chaeron on 2009-02-01
Anyone taken a try at doing a version of this patch for us long-suffering VMWare Desktop users?

The config file for Desktop is /usr/bin/vmware-config-tools.pl

Thanks!

---

### Post by spezifanta on 2009-02-09
Thank you so much!

---

### Post by leysionAI on 2009-03-19
> **delgurth said:**
> I've now also created a patch for my version of the vmware-config-tools.pl script, but that is for the Server version of VMWare and not the Workstation. But you can try to apply the patch to a copy of the script, to see if the patch can be applied.

Thanks very much! It does work! :D I have tried the script on my VMWare Workstation, after I patched, my Virtual Machine functioned well. Now I can use Unity, drag&drop between host and guest. 
VMWare:6.5.0
guest ubuntu 8.10

---

### Post by exedm on 2009-03-30
> **leysionAI said:**
> Thanks very much! It does work! :D I have tried the script on my VMWare Workstation, after I patched, my Virtual Machine functioned well. Now I can use Unity, drag&drop between host and guest. 
VMWare:6.5.0
guest ubuntu 8.10

Could you please explain exactly how did you do it? I also have VMWare Workstation 6.5.0 and Ubuntu 8.10 and I can't seem to get VMtools running properly.
Thanks.

---

### Post by kingborel on 2009-04-04
Awesome patch, fxed my issue perfectly. Thanks!

---

### Post by D00mM4r1n3 on 2009-04-12
Thank you for the patches. I am running the latest build:

Latest Version: 2.0.1 | 2009/03/31 | Build: 156745

on Ubuntu 9.04 Beta, and experienced the vsock errors. The config patch took care of all of the errors. Only the warning for line 157 of util.c remains, but it doesn't appear as though that has any negative impact. There was no tools file in the version I downloaded either (directly from VMware), but the web based browser is somehow still able to install the tools.

---

### Post by Khaele on 2009-04-20
Hi gurus,

It worked also for me, thank you!

```
user@host:~$ sudo uname -a
Linux host 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

```

```
None of the pre-built vsock modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vsock module.

VMWare config patch VSOCK!
`/tmp/vmware-config0/../Module.symvers' -> `/tmp/vmware-config0/vsock-only/Module.symvers'
Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.27-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
/tmp/vmware-config0/vsock-only/linux/util.c: In function ‘VSockVmciLogPkt’:
/tmp/vmware-config0/vsock-only/linux/util.c:157: warning: format not a string literal and no format arguments
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
The vsock module loads perfectly into the running kernel.

```

---

### Post by BryanPearson on 2009-04-22
I am running VMware Workstation 6.5.2 build-156735 and while the patches discussed here worked for the previous version of Workstation (6.5.1) and VMware Server 2.0 and Ubuntu 8.10, they aren't working for me in the current version with 2.6.27.11-generic.  The symptom I have is that the shared clipboard isn't functional.  Anyone else seeing this?  I haven't tried it with VMware Server 2.01 yet, which is now three weeks old.

---

### Post by BryanPearson on 2009-04-22
Sorry for the false alarm - I found a note which I am sure is from a post here:

The second issue is that vmware-user doesn't automatically start - this is because we accidentally left out a line in the autostart config. vmware-user is responsible for lots of stuff, including screen resizing. A workaround is to specify /usr/bin/vmware-user to autostart in System > Preferences > Sessions.

I had forgotten this step.  It is working now.  Just to be sure I uninstalled the tools, and then re-installed from the set that comes with 6.5.2 build-156735 and I found that it works without the patches.

---

### Post by brainbuz on 2009-04-22
I've successfully gotten vmware server up on the last beta and the 4-16 RC for Jaunty Server x64. 

Here's my recipe:

If you are not logged in as root, remember to precede all commands with sudo. 

Register an account at the VMWare site. Once you are logged in you can download VMWare Server, you will need to save the Product Keys from the download page to a text file. 

_tar –xvf <download file>_
_apt-get install linux-headers-`uname –r` build-essential xinetd_
_cd /vmware-server-distrib_
_./vmware-install.pl_
To most questions you will accept the default. 
If it doesn't accept your Product Key, you can enter that after installation.
You may want to specify a different directory than the default for your virtual machine location, I give them a big partition and mount it at vm, then share it with Samba so it is easy to put stuff there.
The last question asks you to configure VMWare server. Answer No. 
You will need to create an account at Ubuntu Forums in order to download this file: [http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015](http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015) to /usr/bin/
_patch /usr/bin/vmware-config.pl /usr/bin/vmware-config.pl.patch_
Now you can run _/usr/bin/vmware-config.pl_. This script will walk you through setting up your networks and compiles some support libraries. Generally go with the default.
Launch firefox to _https://<your vmware host name>:8333_ and login with the account specified during installation (default is the account used for install), from the application menu choose enter serial number and cut and paste the number you saved earlier. From administration you may want to add one or more user accounts, on linux these must be local accounts, the web interface seems unaware of domain accounts accessible through winbind.

---

### Post by zeropegleg on 2009-04-27
no manual entry for patch.  do i need to apt-get install patch?

---

### Post by zeropegleg on 2009-04-27
got my answer.  i used synaptic package manager and installed dpatch.  new to patch mgt in ubuntu but i get it now.  works great thanks all.

---

### Post by zeropegleg on 2009-04-27
one final issue however is that i'm running jaunty - ubuntu 9.04 and downloaded the latest vmware server tar bundle 2.0.1 Build 156745.

i've not been able to find the vmware-config-tools.pl file in either usr/bin nor /bin directories.

does anyone know where this file is located in the latest vmware server (after vmware server gets installed that is!)?

---

### Post by veloce on 2009-04-27
> **zeropegleg said:**
> one final issue however is that i'm running jaunty - ubuntu 9.04 and downloaded the latest vmware server tar bundle 2.0.1 Build 156745.

i've not been able to find the vmware-config-tools.pl file in either usr/bin nor /bin directories.

does anyone know where this file is located in the latest vmware server (after vmware server gets installed that is!)?

it's just called vmware-config.pl now.

(and it's in /usr/bin)

---

### Post by raykroeker on 2009-05-16
The patch also works on Jaunty:  2.6.28-11-generic

Much appreciated.

---

### Post by VikingTiger on 2009-05-16
Amazing. The vmware-config.pl patch worked beautifully. Thanks a lot, brainbuz, for your instructions!

---

### Post by shinji257 on 2009-05-23
Sweet.  Your patch worked great brainbuz.

---

### Post by styven on 2009-05-24
Hi tere,

I seem to be having a problem completing a vmware install, doesn't like the gcc version. **If i tell it to not use the version i have it does this.....**

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

**If i tell it to use the version i have it does this...........**

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] yes 

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:160: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
/tmp/vmware-config0/vmmon-only/linux/driver.c:145: warning: initialisation from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:149: warning: initialisation from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1661: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

styven@styvens-desktop ~/vmware-distrib $

---

### Post by veloce on 2009-05-24
> **styven said:**
> Hi tere,

I seem to be having a problem completing a vmware install, doesn't like the gcc version. 

Other than being in the wrong thread, your gcc version isn't the problem - it is safe to ignore that warning.  

What you need is the patch your vmware-config.pl file. I don't have the links handy, but if you search this forum you should find it pretty readily.

---

### Post by E_lexy on 2009-05-27
I ran the patch and afterwards the vmware-config.pl ran without problems.
I can now startup the webclient.

But when I start my XP guest i get:
```

 Version mismatch with vmmon module: expecting 208.0, got 138.0. You have an incorrect version of the `vmmon' kernel module. Try reinstalling VMware Server. 

```

EDIT-> you need to uninstall and then reinstall VMware first. Then it works!

---

### Post by any.linux12 on 2009-05-27
run: sudo vmware-config.pl

that will re-compile you kernel version and maybe fix the problem

---

### Post by caperillar on 2009-06-06
Hi there,

I followed all instructions and finally I get installed VMServer. When I connect in HostOnly mode everything is perfect, the problem is if I connect the guest OS (XP) in "Bridged" mode, then the message "connectivity limited or null" appears. I don't know why, but the interface vmnet0 wasn't created when it was started the VMserver, all of the others interfaces were created.

In the /dev directory:
```
ls /dev/vm*
/dev/vmci   /dev/vmnet0  /dev/vmnet2  /dev/vmnet4  /dev/vmnet6  /dev/vmnet8
/dev/vmmon  /dev/vmnet1  /dev/vmnet3  /dev/vmnet5  /dev/vmnet7  /dev/vmnet9
```
All modules are loaded:
```
lsmod | grep v
vmnet                  47812  18 
vsock                  24952  0 
vmci                   58324  2 vsock
vmmon                  76912  6 
```
Distro: Ubuntu 9.04 - Jaunty Jackalope.
kernel: 2.6.28-11-generic

Any clue? Thanks.

Carlos


NEWS!

I found this [http://ubuntuforums.org/showthread.php?t=938611]("http://ubuntuforums.org/showthread.php?t=938611") and my IPS restrict the IP assignment. I will prove tomorrow over a network without that restriction.

---

### Post by aristar on 2009-06-08
I have exactly the same problem on the same configuration as caterpillar.
I have to say that VMWare Workstation 6.5 doesn't work with vnet0 neither....

---

### Post by HDave on 2009-06-10
@delgurth -- Thanks for the patch to vmware-config-tools.pl it definitely worked as advertised.  However, I did notice that I still cannot build the vmhgfs module.  I am running Ubuntu Server 9.04 asa guest on Ubuntu 9.04 host running vmware server and am not sure if I even need this.

I get a compile error in page.o -- error  unknown field  'prepare_write' yada yada yada"

Any ideas?

---

### Post by HDave on 2009-06-11
I also noticed another error during the install:

```
No drivers for X.org version 7.5.0
```

I don't know why, but for some reason my screen is HUGE and refuses to resize with containing window.  Mouse grabbing works, but it doesn't seem copy and paste do.

Any ideas?

---

### Post by RealG187 on 2009-06-29
> **delgurth said:**
> Yup, you can get it in the host/server version of vmware also. 

I've patched the vmware-config.pl script with attached patch and with that I solved this issue. Thanks for pointing me at the right direction how to solve this.

This patch is for the most recent 2.0.0 version of VMWare: 122956

How do you use that file, I need to get bridged networking in VMWare on Ubuntu 9.04

---

### Post by HDave on 2009-06-30
> **HDave said:**
> I don't know why, but for some reason my screen is HUGE and refuses to resize with containing window.  Mouse grabbing works, but it doesn't seem copy and paste do.

Solved my problem.  Figured out that for some (bug) reason, the vmware server console for the virtual machine needed to be closed and reopened after I logged in and the vmware-user process had started.

---

### Post by andrewmv on 2009-08-07
Excellent, Delgurth!
I can confirm that this patch worked perfectly to solve the vcore module compilation problem for VMware Server 2.0.1 build-156745 on my Ubuntu 9.04-Desktop system running kernel 2.6.28-14-generic.

The Ubuntu upgrade path seems to have been relevant for previous posters, so for the record, this system was in-place upgraded from Gutsy->Hardy->Intrepid->Jaunty.

Thanks much!

---

### Post by carlbeech on 2009-10-03
Hi All,

Has anyone got vmware server 2 (preferably build 156745) working?

I've done the download, I've performed the vmware-config.pl.patch (which seemed to apply correctly), however I get the following message when doing the compile phase of the config routine...:

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-11-generic/build/include]                         

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.31-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-11-generic'                     
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o                                    
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:31:                    
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here                        
In file included from /tmp/vmware-config3/vmmon-only/./include/vmware.h:38,                            
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:99:                                
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined 
In file included from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:103,                          
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:37,                        
                 from /tmp/vmware-config3/vmmon-only/./common/vmx86.h:33,                              
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:29,                                
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:101:                               
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined         
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined        
In file included from /tmp/vmware-config3/vmmon-only/./include/vm_basic_asm.h:46,                      
                 from /tmp/vmware-config3/vmmon-only/./include/rateconv.h:45,                          
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:40,                        
                 from /tmp/vmware-config3/vmmon-only/./common/vmx86.h:33,                              
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:29,                                
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:101:                               
/tmp/vmware-config3/vmmon-only/./include/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined   
/tmp/vmware-config3/vmmon-only/./include/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined  
/tmp/vmware-config3/vmmon-only/./include/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined  
/tmp/vmware-config3/vmmon-only/./include/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined  
In file included from /tmp/vmware-config3/vmmon-only/./include/vm_asm.h:43,                            
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:103:                               
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined        
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined        
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:119:                               
/tmp/vmware-config3/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined             
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:             
/tmp/vmware-config3/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:                              
/tmp/vmware-config3/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’   
/tmp/vmware-config3/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’    
/tmp/vmware-config3/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’  
/tmp/vmware-config3/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’    
/tmp/vmware-config3/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’   
/tmp/vmware-config3/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’    
/tmp/vmware-config3/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’  
/tmp/vmware-config3/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’    
/tmp/vmware-config3/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1                                         
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2                                                
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-11-generic'                                        
make: *** [vmmon.ko] Error 2                                                                                 
make: Leaving directory `/tmp/vmware-config3/vmmon-only'                                                     
Unable to build the vmmon module.                                                                            

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and   
"http://www.vmware.com/go/unsup-linux-tools".                               

Execution aborted.




- I'm using Ubuntu Karmic (latest patch levels)
GCC 4:4.4.1-1ubuntu1
Kernel headers 2-6-31-11

Many thanks

Carl.

---

### Post by HDave on 2009-10-05
Did you install the headers for your kernel?

```
sudo aptitude install linux-headers-`uname -r`
```

I know that karmic has upgraded the version of gcc....

---

### Post by FoolishStar on 2009-10-15
> **delgurth said:**
> Yup, you can get it in the host/server version of vmware also. 

I've patched the vmware-config.pl script with attached patch and with that I solved this issue. Thanks for pointing me at the right direction how to solve this.

This patch is for the most recent 2.0.0 version of VMWare: 122956

Thank you, resolved my problem on Debian lenny :)

---

### Post by ivan-s on 2009-11-10
I can't put the patch on vmware-install.pl:

$ patch vmware-install.pl vmware-config.pl.patch.txt
patching file vmware-install.pl
Hunk #1 FAILED at 4121.
Hunk #2 FAILED at 4148.


Version of vmware is 2.0.2
What could I do? Download version 2.0.0 ?

---

### Post by sdowney717 on 2009-11-10
you can run vmware player 3.0 which lets you create and edit vm's.
IMO, this runs the networking faster than the server.
it also installed without any fuss.

---

### Post by ivan-s on 2009-11-15
The script help me 
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

---

### Post by bheart on 2009-12-10
> **delgurth said:**
> Yup, you can get it in the host/server version of vmware also. 

I've patched the vmware-config.pl script with attached patch and with that I solved this issue. Thanks for pointing me at the right direction how to solve this.

This patch is for the most recent 2.0.0 version of VMWare: 122956

thanks for your apport.

now it's working fine.

---

### Post by stallione on 2010-01-11
Thanks, the patch works with 2.6.28-17-generic
VMware Server 2.0.2 build-203138

Stallione.

---

### Post by Zoide7777 on 2010-02-09
It worked!  Thanks so much delgurth!

---

### Post by ieee754 on 2010-03-04
> **brainbuz said:**
> I've successfully gotten vmware server up on the last beta and the 4-16 RC for Jaunty Server x64. 

Here's my recipe:

If you are not logged in as root, remember to precede all commands with sudo. 

Register an account at the VMWare site. Once you are logged in you can download VMWare Server, you will need to save the Product Keys from the download page to a text file. 

_tar –xvf <download file>_
_apt-get install linux-headers-`uname –r` build-essential xinetd_
_cd /vmware-server-distrib_
_./vmware-install.pl_
To most questions you will accept the default. 
If it doesn't accept your Product Key, you can enter that after installation.
You may want to specify a different directory than the default for your virtual machine location, I give them a big partition and mount it at vm, then share it with Samba so it is easy to put stuff there.
The last question asks you to configure VMWare server. Answer No. 
You will need to create an account at Ubuntu Forums in order to download this file: [http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015](http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015) to /usr/bin/
_patch /usr/bin/vmware-config.pl /usr/bin/vmware-config.pl.patch_
Now you can run _/usr/bin/vmware-config.pl_. This script will walk you through setting up your networks and compiles some support libraries. Generally go with the default.
Launch firefox to _https://<your vmware host name>:8333_ and login with the account specified during installation (default is the account used for install), from the application menu choose enter serial number and cut and paste the number you saved earlier. From administration you may want to add one or more user accounts, on linux these must be local accounts, the web interface seems unaware of domain accounts accessible through winbind.

I can confirm this works with VMware Server 2.0.2 build-203138 on debian 

#uname -a
Linux sydpxe 2.6.26-2-686 #1 SMP Sat Dec 26 09:01:51 UTC 2009 i686 GNU/Linux

#vmware-config.pl

.................

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family:                           done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.2 build-203138 for Linux for this 
running kernel completed successfully.

.................


thankyou thankyou!

---

### Post by hulkeypoo on 2010-04-06
how to fix vsock error (vsock won't build)

Are you working with vmware tools or server > 2.0?

Does this error look familar?  

[COLOR="Red"]insmod: error inserting '/tmp/vmware-config0/vsock.o': -1 Unknown symbol in module[/COLOR]

replace [COLOR="Blue"]/usr/lib/vmware/modules/source/vsock.tar [/COLOR]
with this patched file that includes the missing symbols.
[COLOR="Indigo"]http://www.worldmulticast.com/help_me_out/vsock.tar[/COLOR]

run the vmware config perl script (following directions to remove any old files) and it will compile the vsock stuff without error!
enjoy!

---

### Post by fratzi on 2010-04-08
this fixed ALL my errors (i tried a lot before!)

[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

---

### Post by HDave on 2010-04-09
I have to say that after constantly stuggling with this issue after every release, I finally switched over to open-vm-tools.  Its a click away in synaptic and works with both desktop and server vm's for vmware workstation and desktop.  Easy peasy.

---

### Post by Morcego XXX on 2010-08-03
delgurth, your patch works like charm on Debian 5 amd64 + VMware Server 2.
 
vsock warning is gone, tyvm.

---

### Post by tuique on 2010-08-11
Thank you delgurth and bond00.

---

