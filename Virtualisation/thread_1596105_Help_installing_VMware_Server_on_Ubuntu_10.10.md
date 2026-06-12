---
title: "Help installing VMware Server on Ubuntu 10.10"
date: 2010-10-13
forum: Virtualisation
---

### Post by rumy on 2010-10-13
Hi Guys,

The last time I installed server 10.04 I managed to get VMware server running with great difficulty.

I recently messed up my server and decided to reinstall so I installed the latest 10.10.

I followed instructions [here]("https://help.ubuntu.com/community/VMware/Server") and [here]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/") same as last time. However, this time around I keep getting stuck with this error:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.35-22-server/include/

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.35-22-server).  Even if the module were to 
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 
```


Any help would be much appreciated. 

P.S. I am a newbie so a little hand holding please :D

---

### Post by kwiatu5 on 2010-10-14
I have the same problem. I also tried to provide path to many localizations like these:

> /usr/src/linux-headers-2.6.35-22-generic-pae/include/linux/version.h
/usr/src/linux-headers-2.6.35-22-generic/include/linux/version.h
/usr/src/linux-headers-2.6.35-22-virtual/include/linux/version.h
/usr/src/linux-headers-2.6.35-22/include/xen/interface/version.h
/usr/src/linux-headers-2.6.35-22/include/linux/dvb/version.h
/usr/src/linux-headers-2.6.35-22/include/sound/version.h
/usr/include/linux/version.h
/usr/include/linux/dvb/version.h


but I always get that sources aren't compatible with running kernel.

Help.

---

### Post by gyimesia on 2010-10-14
Hello,

I have the same problem.

Any suggestion?

---

### Post by CharlesA on 2010-10-14
*Moved to **Virtualization**.*

---

### Post by Gnea on 2010-10-14
Hi, I just worked this problem for someone on IRC, so I'll go ahead and summarize how it was solved.

First of all, you'll need to head over to VMware's site:

[http://communities.vmware.com/message/1608187](http://communities.vmware.com/message/1608187)

and there you will find the solution.  Here is the solution as well, in case that link decides to not work again:

```

solution for me (ubuntu 10.10; kernel 2.6.35-20-generic):

cd /tmp
wget http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash
chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
./vmware7.1.1-patch-kernel-2.6.35.bash

I do it and after i execute:
vmware-modconfig --console --install-all

```

Enjoy!  :guitar:

---

### Post by aiens on 2010-10-14
This is stil not working...
 
I've got the same message again with vmware server

---

### Post by rumy on 2010-10-14
Still does not work, same error.

---

### Post by UltimateWager on 2010-10-14
The patch appears to be for VMWare Player. I haven't looked inside it yet to see if a similar patch would work for VMWare Server, but it doesn't appear as though trying to patch Server with the Player patch does much.

---

### Post by HermanAB on 2010-10-15
Howdy,

VMware Server is best avoided.  Either use VMware Player, VMware Workstation or VMware ESX.

---

### Post by yuppy on 2010-10-17
> **Gnea said:**
> Hi, I just worked this problem for someone on IRC, so I'll go ahead and summarize how it was solved.

First of all, you'll need to head over to VMware's site:

[http://communities.vmware.com/message/1608187](http://communities.vmware.com/message/1608187)

and there you will find the solution.  Here is the solution as well, in case that link decides to not work again:

```

solution for me (ubuntu 10.10; kernel 2.6.35-20-generic):

cd /tmp
wget http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash
chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
./vmware7.1.1-patch-kernel-2.6.35.bash

I do it and after i execute:
vmware-modconfig --console --install-all

```Enjoy!  :guitar:

  its not working bro :(  still same error

---

### Post by kwiatu5 on 2010-10-17
I'm wokring and I think that I'll have a solution this night. Be patient! ;-)

---

### Post by kwiatu5 on 2010-10-17
So... The problem is that the vmware-server-distrib/bin/vmware-config.pl script doesn't recognize version of our kernel headers. So let help him to pass this test.

I put new line at 2713 line in vmware-config.pl (use VIM or VI).
And I write this, to pass next test of kernel version:
> 
$header_version_uts=$gSystem{'uts_release'};
It looks like that with above line (bolded):
>     $header_version_uts = direct_command(
      shell_string($gHelper{'echo'}) . ' '
      . shell_string($uts_headers . $pattern
                     . ' UTS_RELEASE') . ' | ' . shell_string($gHelper{'gcc'})
      . ' ' . shell_string('-I' . $answer) . ' -E - | '
      . shell_string($gHelper{'grep'}) . ' ' . shell_string($pattern));
    chomp($header_version_uts);
    $header_version_uts =~ s/^$pattern \"([^\"]*)\".*$/$1/;
**$header_version_uts=$gSystem{'uts_release'};**
    if (not ($header_version_uts eq $gSystem{'uts_release'})) {
      if ($source eq 'user') {
        print wrap('The directory of kernel headers (version '
                   . $header_version_uts . ') does not match your running '
                   . 'kernel (version ' . $gSystem{'uts_release'} . ').  Even '
                   . 'if the module were to compile successfully, it would not '
                   . 'load into the running kernel.' . "\n\n", 0);
      }
      return '';
    }
  }
Good way is to create symbolic link at /usr/src/linux to /usr/src/linux-headers-2.6.35-22-generic
Save file and run: sudo ./bin/vmware-config.pl

---

### Post by aaron465 on 2010-10-17
I have installed linux-headers-2.6.35-22-generic from apt and edited the vmware-config.pl file as you suggested (as well as creating the symbolic link) but now I get this error:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is a kernel header file directory, but it
does not contain the file "linux/autoconf.h" as expected.  This can happen if
the kernel has never been built, or if you have invoked the "make mrproper"
command in your kernel directory.  In any case, you may want to rebuild your
kernel.

```
Do you have any other ideas?

Thanks,
Aaron

---

### Post by kwiatu5 on 2010-10-17
Try:
> 
cp /usr/src/linux-headers-2.6.35-22-generic/include/generated/autoconf.h /usr/src/linux-headers-2.6.35-22-generic/include/linux/autoconf.h


---

### Post by aaron465 on 2010-10-17
Hmm it is not happy, the vmmon module is failing to compile now. 

```
root@JohnConnor:/home/aaron/vmware-server-distrib/bin# ./vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.35-22-generic/include

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /usr/src/linux-headers-2.6.35-22-generic/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:31:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:78: error: conflicting types for âpoll_initwaitâ
include/linux/poll.h:72: note: previous declaration of âpoll_initwaitâ was here
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:99:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:108: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/msr-index.h:236: note: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config0/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:329: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:333: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:401: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:407: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_ReadIfEqualWrite64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:460: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Andâ:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:506: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_And64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:551: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Orâ:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:595: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Or64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:640: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Xorâ:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:684: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Xor64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:729: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Addâ:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:773: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:775: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Add64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:816: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Subâ:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:860: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:862: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Sub64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:903: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Incâ:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:945: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:947: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Inc64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:986: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Decâ:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1028: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1030: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_Dec64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1069: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: At top level:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1223: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1227: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_ReadAdd64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1313: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: At top level:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1536: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1663: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function âAtomic_ReadWrite64â:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1796: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h: At top level:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:486: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:779: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:820: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:922: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:119:
/tmp/vmware-config0/vmmon-only/./common/hostif.h:53: warning: "WINNT_DDK" is not defined
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function âLinuxDriverSyncCallOnEachCPUâ:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1423: error: too many arguments to function âsmp_call_functionâ
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function âLinuxDriver_Ioctlâ:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âeuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âfsuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âegidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âfsgidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:2007: error: too many arguments to function âsmp_call_functionâ
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.
```

I assume that vmware will fix this themselves eventually with an update or patch of some kind?

---

### Post by kwiatu5 on 2010-10-17
This is for you aaron465: [http://www.saarlinux.de/blog/?p=5](http://www.saarlinux.de/blog/?p=5)


So I've solved this problem, but now I don' know how many patches I used to do it. I think that useful pathes are:
[http://www.saarlinux.de/blog/?p=5](http://www.saarlinux.de/blog/?p=5)
and this one: [http://www.jwh.me.uk/2009/10/03/compiling-vmware-2-01-modules-on-recent-2-6-kernels/](http://www.jwh.me.uk/2009/10/03/compiling-vmware-2-01-modules-on-recent-2-6-kernels/)

I'm reminding that I use:
VMware-server-2.0.2-203138.i386.tar.gz
Ubuntu 10.10 x86 Desktop with 2.6.35-22-generic Kernel

You can overvrite your modules at /usr/lib/vmware/modules/source by using my patched modules, but remember that you do it for your own risk and I'm not take care and rensponsibility for any damages.

**Download:**
[vmci.tar]("http://www.kwiatu5.tkdami.net/kwiatek.org/ubuntu10.10_kernel2.6.35-22-generic/vmci.tar") [vmmon.tar]("http://www.kwiatu5.tkdami.net/kwiatek.org/ubuntu10.10_kernel2.6.35-22-generic/vmmon.tar") [vmnet.tar]("http://www.kwiatu5.tkdami.net/kwiatek.org/ubuntu10.10_kernel2.6.35-22-generic/vmnet.tar") [vsock.tar]("http://www.kwiatu5.tkdami.net/kwiatek.org/ubuntu10.10_kernel2.6.35-22-generic/vsock.tar")

I paste it only for education need and I can delete if I trespass copyrights.

---

### Post by aaron465 on 2010-10-18
Fantastic, this worked a treat! 

Thank you very much for your help,
Aaron

UPDATE: It installed but vmci does not seem to work, and I cannot start any virtual machines! This is starting to annoy me now! :P Sort it out vmware!

---

### Post by kwiatu5 on 2010-10-18
aaron465, paste here a information from debugger why vmci won't start.

I worked around problem with vsock.tar with VMware Player 3.1.2 build-301548 which wasn't able to start. I applied to my /usr/lib/vmware/modules/source/vsock.tar (you can download it from second post above) this how-to -> [https://bbs.archlinux.org/viewtopic.php?pid=836641](https://bbs.archlinux.org/viewtopic.php?pid=836641) and it's works perfectly.
VMPlayer 3.1.2 on Ubuntu 10.10 with 2.6.35-22-generic works perfectly!!!

I just uninstalled VMWare Server 2.0.2 where I had also problems with remote control plugin to firefox 3.6.10... VMWare Player gives functions to create wirtual machines so I have all what I want. Many hours with Server 2.0.2... damn... but ok. If somebody want to start VMWare Server on ubuntu 10.10 can do it ;)

regards, 
Piotr Kwiatek

---

### Post by aaron465 on 2010-10-18
Thanks for your help, I am using Virtualbox with cli now, vmware has caused too much hassle!

Aaron

---

### Post by fjgaude on 2010-10-18
My feelings as of now is that VMware Server is dead in the water, with little VMware support. Their Player takes its place and if that isn't good enough go to Workstation. For a real server requirement they wish us to go to ESXi.

Player 3.1.2 is all I need in my present situation.

---

### Post by kwiatu5 on 2010-10-18
yes, but somebody, who build a server without GUI and wants to run many guests may be interested vmware server to run guests in service mode.. i think...

vmplayer is good and give enough features which I want.

---

### Post by hother on 2010-10-19
Hi.

> **rumy said:**
> 
```

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.35-22-server).  Even if the module were to 
compile successfully, it would not load into the running kernel.
```

You have to copy the file **utsrelease.h** from <your header-directory>/generated/ to <your header-directory>/include/
E.g.:
/usr/src/linux/include/generated/utsrelease.h to /usr/src/linux/include/linuc/utsrelease.h

Possibly you have to do the same with autoconf.h



After doing that i have much errors in 'make'

I'm using linux-headers-2.6.35-22-server

Anyone any suggestions?
(sorry for my 'german english')

---

### Post by An0maly on 2010-10-19
I managed to install Vmware Server VMware-server-2.0.2-203138.x86_64 on my 10.10 running 2.6.35-22-generic , however Authd seems a bit unstable at times , I seem to crash the process when trying to add a specific VM or if I try to launch a running VM's console .

I read the guide and DLed the patch found on this site , further down the page there is an even more detailed guide posted by user ( Mark Tebong ) in the comments section  

[http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/](http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/)

HTH :)

---

### Post by morpheusj30 on 2010-10-28
The solution can be found here:
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

it worked for me.... and yes the solution is not for just 9.10.

---

### Post by doug-M on 2010-10-30
> **aaron465 said:**
> 
I assume that vmware will fix this themselves eventually with an update or patch of some kind?

VMWare has abandoned VMWare Server so don't expect to see any patches or updates. 


Look at the link below, I read it as it died Jan 2010 but they are providing minimal support (no fixes) until 2011-06-03. I don't know why they still list as a product on their website it really isn't.

General Support Life Cycle Polices
[http://www.vmware.com/support/policies/lifecycle/general/index.html](http://www.vmware.com/support/policies/lifecycle/general/index.html)
VMware Server 	General Availability 	End of General Support
 		(YYYY/MM/DD) 		(YYYY/MM/DD)
Version 2.x 	2008/09/23 		2011/06/30
Version 1.x 	2006/07/12 		2010/03/23
*VMware Server was declared End Of Availability on January 2010. Support will be limited to Technical Guidance for the duration of the support term.

---

### Post by nacho_dh on 2010-11-05
> **Gnea said:**
> Hi, I just worked this problem for someone on IRC, so I'll go ahead and summarize how it was solved.

First of all, you'll need to head over to VMware's site:

[http://communities.vmware.com/message/1608187](http://communities.vmware.com/message/1608187)

and there you will find the solution.  Here is the solution as well, in case that link decides to not work again:

```

solution for me (ubuntu 10.10; kernel 2.6.35-20-generic):

cd /tmp
wget http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash
chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
./vmware7.1.1-patch-kernel-2.6.35.bash

I do it and after i execute:
vmware-modconfig --console --install-all

```

Enjoy!  :guitar:

worked for me, here are the steps I followed:

1) first installed vmware workstation 7.1.2

sudo sh .vmware-workstation-full-7.1.2-301548.x86_64.bundle

2) after the install, i followed the steps Gnea provided.

3) profit!

---

### Post by jshuford on 2010-11-15
> **Gnea said:**
> Hi, I just worked this problem for someone on IRC, so I'll go ahead and summarize how it was solved.

First of all, you'll need to head over to VMware's site:

[http://communities.vmware.com/message/1608187](http://communities.vmware.com/message/1608187)

and there you will find the solution.  Here is the solution as well, in case that link decides to not work again:

```

solution for me (ubuntu 10.10; kernel 2.6.35-20-generic):

cd /tmp
wget http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash
chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
./vmware7.1.1-patch-kernel-2.6.35.bash

I do it and after i execute:
vmware-modconfig --console --install-all

```Enjoy!  :guitar:

Your solution worked for me...Thank you :)

---

### Post by kwagga on 2010-11-20
Didn't work for me. The explanation seems to be for Vmware Workstation, not Vmware Server. Anyone else found a solution yet?

---

### Post by doug-M on 2010-11-20
Personally I just gave up on VMWare. VMWware server in particular is now a dead product, VMWare is not going to fix it in any way.

I had VMWare Server mostly working but my machine (host and guests) would freeze for 2-10 seconds every five minutes or so making it almost impossible to work on. 

I am now running the unmodified VMWare guests in VirtualBox.

---

### Post by jay_kay70 on 2011-01-10
Hi,

Help required to install VMware workstation 7.1.3-i386 bundle on UBUNTU 10.10. AS I'm a newbi for UBUNTU, Step by step installation Procedure might be of great help. 

Thanks in advance.

JK.

---

### Post by doug-M on 2011-01-11
If you own VMWare workstation then I believe VMWare should provide you support.

If you don't own it well then maybe shame on you :) and try VirtualBox instead. I used to love VMWare but Virtualbox has been a great replacement.

---

### Post by devoda on 2011-01-13
Thanks Gnea! That solved my vmmon build error 2 on 10.10 install vmware 7.1.2 x64.

---

### Post by neketh69 on 2011-01-31
I found this solution. I don't know the full repercussions, so tread at your own risk.

When prompted with the following;

Error 1:

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.33).  Even if the module were to compile
successfully, it would not load into the running kernel.
What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]
This can be resolved by editing version.h (usually in /usr/src/linux/include/linux) and adding this line:

#define UTS_RELEASE "2.6.33"

Then, 

Error 2:

The path “/usr/src/linux/include” is a kernel header file directory, but it does not contain the file “linux/autoconf.h” as expected.  This can happen if the kernel has never been built, or if you have invoked the “make mrproper” command in your kernel directory.  In any case, you may want to rebuild your kernel.
What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]

As the latest kernel doesn’t seem to contain this file, I took the autoconf.h file from 2.6.22.2, and copied it to the correct place.

This made VMware compile (until it errored on other stuff, which can be fixed using this script: [http://radu.cotescu.com/2010/01/19/how-to-install-vmware-server-ubuntu-fedora-opensuse/](http://radu.cotescu.com/2010/01/19/how-to-install-vmware-server-ubuntu-fedora-opensuse/)).

---

### Post by yumgnomeandthensome on 2011-02-13
from 
[http://www.vmware.com/support/ws71/doc/releasenotes_ws713.html](http://www.vmware.com/support/ws71/doc/releasenotes_ws713.html)
(i've just installed this version and did't get this issue)
**Resolved Issues**

  The following issues are resolved in VMware Workstation 7.1.3.


[LIST]
[*]     When you install VMware Workstation on an operating system that uses a post-2.6.34 Linux kernel, the vmmon module fails to compile.
[*]   The vmxnet and vsock guest modules fail to compile on operating systems that use post-2.6.32 Linux kernels.
[*]   When you install VMware Tools on an operating system that uses a post-2.6.34 Linux kernel, the vsock.ko module fails to build.
[*]     Unity mode does not work with an Ubuntu 10.10 64-bit guest operating system.
[*]   An unrecoverable error occurs when you select the **Novell NetWare**, **Sun Solaris**, or **Other** guest operating system type in the New Virtual Machine wizard.
[*]     When you run bulkDeploy.exe to deploy a Pocket ACE package into one or more  locations, it crashes with the error     SSL Wrapper: invoked uninitilized function  AES_set_encrypt_key!.
[/LIST]

---

