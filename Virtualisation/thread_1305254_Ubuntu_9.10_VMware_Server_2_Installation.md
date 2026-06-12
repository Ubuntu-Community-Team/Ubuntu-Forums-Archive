---
title: "Ubuntu 9.10 VMware Server 2 Installation"
date: 2009-10-29
forum: Virtualisation
---

### Post by raiderleaf on 2009-10-29
Hello All,

I have never had trouble like this just getting VMware set up, but I just can't get it to configure right in the terminal to then allow me to open up /usr/bin/vmware . It keeps saying that the vmware-config.pl wasn't set up right. Here is the problem that it is giving me, verbatim:

root@raiderleaf-desktop:/usr/bin# ./vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
Virtual machines failed
Stopping VMware management services:
VMware Virtual Infrastructure Web Access
VMware Server Host Agent failed
Stopping VMware services:
VMware Authentication Daemon done
Virtual machine monitor done

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel. Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-14-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmmon-only'
make -C /lib/modules/2.6.31-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
CC [M] /tmp/vmware-config7/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config7/vmmon-only/linux/driver.c:31:
/tmp/vmware-config7/vmmon-only/./include/compat_wait.h:78: error: conflicting types for â€˜poll_initwaitâ€™
include/linux/poll.h:70: note: previous declaration of â€˜poll_initwaitâ€™ was here
In file included from /tmp/vmware-config7/vmmon-only/./include/vmware.h:38,
from /tmp/vmware-config7/vmmon-only/linux/driver.c:99:
/tmp/vmware-config7/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config7/vmmon-only/./include/vcpuset.h:103,
from /tmp/vmware-config7/vmmon-only/./include/modulecall.h:37,
from /tmp/vmware-config7/vmmon-only/./common/vmx86.h:33,
from /tmp/vmware-config7/vmmon-only/linux/driver.h:29,
from /tmp/vmware-config7/vmmon-only/linux/driver.c:101:
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config7/vmmon-only/./include/vm_asm_x86_64.h:39,
from /tmp/vmware-config7/vmmon-only/./include/vm_asm.h:41,
from /tmp/vmware-config7/vmmon-only/linux/driver.c:103:
/tmp/vmware-config7/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config7/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config7/vmmon-only/./include/vm_asm.h:41,
from /tmp/vmware-config7/vmmon-only/linux/driver.c:103:
/tmp/vmware-config7/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config7/vmmon-only/linux/driver.c:119:
/tmp/vmware-config7/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config7/vmmon-only/linux/driver.c: In function â€˜LinuxDriverSyncCallOnEachCPUâ€™:
/tmp/vmware-config7/vmmon-only/linux/driver.c:1423: error: too many arguments to function â€˜smp_call_functionâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c: In function â€˜LinuxDriver_Ioctlâ€™:
/tmp/vmware-config7/vmmon-only/linux/driver.c:1987: error: â€˜struct task_structâ€™ has no member named â€˜euidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:1987: error: â€˜struct task_structâ€™ has no member named â€˜uidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:1988: error: â€˜struct task_structâ€™ has no member named â€˜fsuidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:1988: error: â€˜struct task_structâ€™ has no member named â€˜uidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:1989: error: â€˜struct task_structâ€™ has no member named â€˜egidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:1989: error: â€˜struct task_structâ€™ has no member named â€˜gidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:1990: error: â€˜struct task_structâ€™ has no member named â€˜fsgidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:1990: error: â€˜struct task_structâ€™ has no member named â€˜gidâ€™
/tmp/vmware-config7/vmmon-only/linux/driver.c:2007: error: too many arguments to function â€˜smp_call_functionâ€™
make[2]: *** [/tmp/vmware-config7/vmmon-only/linux/driver.o] Error 1
make[1]: *** _module_/tmp/vmware-config7/vmmon-only Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [http://vmmon.ko](http://vmmon.ko) Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.
----------------------------------------
Anyone have any ideas?

---

### Post by ericab on 2009-10-29
i have the *exact* same problem!

some please help!

ps, i tried the kernel patchfix method i saw on the vmware forums;

[http://communities.vmware.com/message/1305526#1305526](http://communities.vmware.com/message/1305526#1305526)

it didnt work

---

### Post by radu.ro on 2009-10-29
Check this post on my blog: [How to install VMware Server 2.0.x on Ubuntu 9.10 Karmic Koala]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/"). The VSOCK module won't be compiled but VMware Server will work without it.

Hope it will be useful to you!

---

### Post by ericab on 2009-10-30
thank you for your write-up and reply to our problem.

i tried the steps you outlined but:

eric@lnx-serv:~/temp$ sudo ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh

results in:

There is no archive containing VMware Server in the path you indicated!

"VMware-server-2.0.2-203138.x86_64.tar.gz" is placed in the same folder as "vmware-server-2.0.x-kernel-2.6.31-14-install.sh"

#-o

---

### Post by radu.ro on 2009-10-30
Done. It should work now for x86_64 too. It was a regex I used to identify the archive you had. Before it was
```
"^(VMware-server-2.0.[0-9]-)[0-9]*.[A-Za-z0-9]*.tar.gz"
```
and it didn't match for VMware-server-2.0.2-203138.x86_64.tar.gz, only for the i686 version.

So now the regex is ```
"^(VMware-server-2.0.[0-9]-)[0-9]*.[A-Za-z0-9_]*.tar.gz"
``` and the script should work as advertised. Sorry, I was really tired and that slipped me away.

Download the script again and follow the instructions I wrote in the blog post. Thank you!

---

### Post by supraman_tt on 2009-10-30
> **ericab said:**
> thank you for your write-up and reply to our problem.

i tried the steps you outlined but:

eric@lnx-serv:~/temp$ sudo ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh

results in:

There is no archive containing VMware Server in the path you indicated!

"VMware-server-2.0.2-203138.x86_64.tar.gz" is placed in the same folder as "vmware-server-2.0.x-kernel-2.6.31-14-install.sh"

#-o

I had the same message appear when I attempted to run the script from within the extracted archive. 

Simply move the script to the same level as the tar.gz file.

I'm in the process of installing it now.

Looks to work a treat

Thanks radu.ro

---

### Post by radu.ro on 2009-10-30
@supraman_tt: That was written in the instructions. :D "3. Run the script with super user rights either in the same folder where you have downloaded the server archive, either by providing it the path to that folder."

But @ericab was right. I didn't filtered the output of a regex for the x86_64 version of VMware. Now it works for that too.

---

### Post by ericab on 2009-10-30
ahhh ! 

eric@lnx-serv:~/temp$ sudo ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh

sudo: ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh: **command not found**

O_o

---

### Post by radu.ro on 2009-10-30
> **ericab said:**
> ahhh ! 

eric@lnx-serv:~/temp$ sudo ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh

sudo: ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh: **command not found**

O_o

Make it executable: chmod +x vmware-server-2.0.x-kernel-2.6.31-14-install.sh

---

### Post by ericab on 2009-10-30
DOH !

your a lifesaver !!
thanks for all your work

---

### Post by lucotuslim on 2009-11-01
Guys, I used the above method and successfully install the VMWARE Server 2 (ignored all the error message). 

I was able to startup my old Virtual Machine but I noticed that my mouse only able to move until certain area. When it move beyond that area , it will turn into hand shape and I was unable to click.

Seems I need to fall back to 9.04. 
:(

---

### Post by ericab on 2009-11-01
mmm no, i think you need to install vmware tools.

---

### Post by lucotuslim on 2009-11-01
I retry all over again.. meaning reinstall the Virtual Machine (Enterprise Linux 4) and also install the VMWare Tool. 

The problem still the same.

---

### Post by jimfcl on 2009-11-03
Hi, I wonder if you can help?  I run the script and after the untarring I see the following output;

Testing patch...
Reversed (or previously applied) patch detected!  Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file vmci-only/Makefile.rej
Reversed (or previously applied) patch detected!  Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file vmnet-only/Makefile.rej
Reversed (or previously applied) patch detected!  Skipping patch.
6 out of 6 hunks ignored -- saving rejects to file vmnet-only/netif.c.rej
The patch cannot be applied. :(

Any ideas?

Thanks for any and all replies!

---

### Post by radu.ro on 2009-11-04
> **jimfcl said:**
> Hi, I wonder if you can help?  I run the script and after the untarring I see the following output;

Testing patch...
Reversed (or previously applied) patch detected!  Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file vmci-only/Makefile.rej
Reversed (or previously applied) patch detected!  Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file vmnet-only/Makefile.rej
Reversed (or previously applied) patch detected!  Skipping patch.
6 out of 6 hunks ignored -- saving rejects to file vmnet-only/netif.c.rej
The patch cannot be applied. :(

Any ideas?

Thanks for any and all replies!

It seems that you already have the patch applied somehow. Delete the vmware-server-distrib folder and start again...

---

### Post by radu.ro on 2009-11-04
@jimfcl: Go to my blog post again as there are two solutions for the mouse problems.

---

### Post by keptjaws on 2009-11-05
Hi Radu,

     I followed up your link and love your script very much. BTW, about mouse problem, i don't understant what is your option 2's meaning. I'm newby in linux. Can u tell me what exactly should i do step by step,please? Thanks in advance.

---

### Post by jimfcl on 2009-11-05
Hi Radu, I'm all up and running!

Thanks for all your time and efforts!

---

### Post by lucotuslim on 2009-11-05
Radu, I will try again this weekend using your post [http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala) . 

Will post my result here.

---

### Post by radu.ro on 2009-11-09
> **keptjaws said:**
> Hi Radu,

     I followed up your link and love your script very much. BTW, about mouse problem, i don't understant what is your option 2's meaning. I'm newby in linux. Can u tell me what exactly should i do step by step,please? Thanks in advance.

Sure... Edit ~/.profile and at the end of the file write these two lines:
```
VMWARE_USE_SHIPPED_GTK=yes
export VMWARE_USE_SHIPPED_GTK
```

That should do the trick. After you'll log in again the variable should be set for you.

---

### Post by radu.ro on 2009-11-09
> **lucotuslim said:**
> Radu, I will try again this weekend using your post [http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala) . 

Will post my result here.
Please post your results on the post's comments section as it will be more easy for me to respond there and thus you will get a faster answer.

---

### Post by tspec on 2009-11-26
This seems to be about as far as I'm getting, any ideas?

> Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                       failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                               failed
Stopping VMware services:
   VMware Authentication Daemon                           done
   Virtual machine communication interface                done
   Virtual machine monitor                                done
   Bridged networking on /dev/vmnet0                      done
   Host network detection                                 done
   DHCP server on /dev/vmnet1                             done
   Host-only networking on /dev/vmnet1                    done
   DHCP server on /dev/vmnet8                             done
   NAT service on /dev/vmnet8                             done
   Host-only networking on /dev/vmnet8                    done
   Virtual ethernet                                       failed
Unable to stop services for VMware Server

Execution aborted.

Housekeeping...
Thank you for using the script!
Author: Radu Cotescu
[http://radu.cotescu.com](http://radu.cotescu.com)


---

### Post by tspec on 2009-11-30
Worked it out. Had to reinstall the entire OS. Things were getting messy because previously the OS installed was an upgrade to Jaunty and this script didn't seem to like the fact there was already a copy of vmware installed prior etc. Sometimes it's less painful just to cut your losses and do a fresh rebuild.

---

### Post by lucotuslim on 2009-12-03
Hi, I able to solve the mouse does not work properly by follow this guide. 

[http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/](http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/)

---

### Post by greekodan on 2010-05-03
> **radu.ro said:**
> Check this post on my blog: [How to install VMware Server 2.0.x on Ubuntu 9.10 Karmic Koala]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/"). The VSOCK module won't be compiled but VMware Server will work without it.

Hope it will be useful to you!

Hey Radu,

Thanks for the post. I tried posting there on your blog but could'nt so here it is: 

So I'm a complete newbie. I'm trying to install VMWare 2.0.1 on Ubuntu 9.10. So I've downloaded the files "VMware-server-2.0.1-156745.x86_64.tar.gz" and your script "vmware-server-2.0.x-kernel-2.6.3x-install.sh" and then ran the commands

$ chmod +x vmware-server-2.0.x-kernel-2.6.3x-install.sh
$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
[sudo] password for xxx: 
./vmware-server-2.0.x-kernel-2.6.3x-install.sh: 3: Syntax error: Unterminated quoted string
 
So you see I get an error. Any idea on how to go ahead?

---

