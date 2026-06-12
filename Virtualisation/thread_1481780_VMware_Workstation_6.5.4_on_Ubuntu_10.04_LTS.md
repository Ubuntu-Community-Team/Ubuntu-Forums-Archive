---
title: "VMware Workstation 6.5.4 on Ubuntu 10.04 LTS"
date: 2010-05-12
forum: Virtualisation
---

### Post by Dravic on 2010-05-12
This is for those of you you may still be having issues installing VMware workstation 6.5.x ( and 7.x) on the new Ubuntu 10.04 LTS release.

While using several helpful links (I'll add below) and some good old fashion trouble shooting I was able to get workstation 6.5.4 installed and running. 
It started out with having the installation freeze during the configuration phase of installing vmware player. It would just hang there, but at least they were capturing the ctrl-c and the install would clean up after itself and exit. 
While exercising my goole-fu I was able to get past that issue following the steps on here.

[http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html](http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html)

1. Start the installation 
2. run a loop to kill the &#8220;vmware-modconfig-console&#8220; that hangs the installation. 

At this point installation finished, but running &#8220;vmware-modconfig --console &#8211;install-all&#8221; would generate an odd error for me when trying to do the vmnet compiling. 

[I]# vmware-modconfig --console --install-all 
&#8230; 
&#8230; 
&#8230; 
make: ***  /tmp/vmware-root/modules/vmnet-only: No such file or directory.  Stop[FONT=monospace]
[/FONT]Unable to install vmnet 
# [/I]

googling vmnet install errors led me to 

[http://communities.vmware.com/message/1401588#1401588](http://communities.vmware.com/message/1401588#1401588)(for 7.x) 
and 
[http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32](http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32)

which describe patching needed in order to get vmnet to compile correctly. 

As I wanted to know what the patch and scripts where doing I opened them up with gedit and then just did the following manually (mostly from the second link as the two links perform similar tasks ) 

1. tar xvf /usr/lib/vmware/modules/source/vmnet.tar -C /tmp 
2. tar xvf /usr/lib/vmware/modules/source/vmci.tar -C /tmp 
3. cd /tmp 
 4. vi  both &#8220;vmnet-only/vnetUserListener.c&#8221; and &#8220;vmci-only/include/pgtbl.h&#8221;  adding  #include "compat_sched.h" to both files.
5. tar cvf /usr/lib/vmware/modules/source/vmnet.tar /tmp/vmnet-only 
6. tar cvf /usr/lib/vmware/modules/source/vmci.tar /tmp/vmci-only

 Thinking I was finally at the end of my ordeal , I reran &#8220;vmware-modconfig-console&#8220; and was greeted with the same error...  ugh 

Looking closer at my error compared to some of the others, I realized my error wasn't from within the vmnet directory, but that the directory did exist at all. 

*make: *** /tmp/vmware-root/modules/vmnet-only: No such file or directory.  Stop  *

odd..  why would /tmp/vmware-root/modules/vmnet-only not exist. So I started the &#8220;vmware-modconfig --console &#8211;install-all&#8221; command again and stopped the process (ctrl-z) in mid recompile. 

Strange the recompile creates the /tmp/vmware-root/modules/#### directories for everything else except for vmnet-only.  So I unpacked the source files as I had before 

1. tar xvf /usr/lib/vmware/modules/source/vmnet.tar -C /tmp 
2. tar xvf /usr/lib/vmware/modules/source/vmci.tar -C /tmp 

and copied the relevant patched directories over with a little shell expansion, **WHILE THE COMPILE WAS PAUSED (ctrl-z). **

cp -pr /tmp/vm{ci,net}-only /tmp/vmware-root/modules/ 

I then **RESUMED (#fg)** &#8220;vmware-modconfig --console &#8211;install-all&#8221; 

and  

Starting VMware services:[INDENT] Virtual machine monitor                                                done    
[/INDENT][INDENT] Virtual machine communication interface                                done    
[/INDENT][INDENT] Blocking file system                                                   done    
[/INDENT][INDENT] Virtual ethernet                                                       done    
[/INDENT][INDENT] Shared Memory Available                                                done 
[/INDENT]SUCCESS..  


hope it helps...

---

### Post by airmid on 2010-05-21
Thank you!!! That worked for me!!

---

### Post by arch0njw on 2010-05-30
The reason the instructions here ([http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32](http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32)) did not work is because there is a superfluous /tmp in the path.  The instructions should be as follows:

tar xvf /usr/lib/vmware/modules/source/vmnet.tar -C /tmp
tar xvf /usr/lib/vmware/modules/source/vmci.tar -C /tmp

cd /tmp

perl -pi -e 's,("vnetInt.h"),\1\n#include "compat_sched.h",' vmnet-only/vnetUserListener.c
perl -pi -e 's,("compat_page.h"),\1\n#include "compat_sched.h",' vmci-only/include/pgtbl.h

tar cvf /usr/lib/vmware/modules/source/vmnet.tar vmnet-only
tar cvf /usr/lib/vmware/modules/source/vmci.tar vmci-onlyThat's because you are already in /tmp and the path prefix "/tmp/" shouldn't be included.  Now, perhaps that is fine for another distro, but not for us.  Using those modified instructions I was able to get workstation 6.5.4 to work just fine.

Thank you for getting the information together!  It was invaluable!!!

---

### Post by jfrome on 2010-06-11
arch0njw, thanks for the correction.  Worked like a charm!

---

### Post by rhandsome on 2010-06-11
I'm trying to install VMWare Workstation 7.1.0 on Lucid 10.4 64bit and I keep getting this error: ./VMware-Workstation-Full-7.1.0-261024.x86_64.bundle: 110: Syntax error: newline unexpected 

Can anyone help?

---

### Post by cyjambo on 2010-06-24
> **arch0njw said:**
> The reason the instructions here ([http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32](http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32)) did not work is because there is a superfluous /tmp in the path.  The instructions should be as follows:

tar xvf /usr/lib/vmware/modules/source/vmnet.tar -C /tmp
tar xvf /usr/lib/vmware/modules/source/vmci.tar -C /tmp

cd /tmp

perl -pi -e 's,("vnetInt.h"),\1\n#include "compat_sched.h",' vmnet-only/vnetUserListener.c
perl -pi -e 's,("compat_page.h"),\1\n#include "compat_sched.h",' vmci-only/include/pgtbl.h

tar cvf /usr/lib/vmware/modules/source/vmnet.tar vmnet-only
tar cvf /usr/lib/vmware/modules/source/vmci.tar vmci-onlyThat's because you are already in /tmp and the path prefix "/tmp/" shouldn't be included.  Now, perhaps that is fine for another distro, but not for us.  Using those modified instructions I was able to get workstation 6.5.4 to work just fine.

Thank you for getting the information together!  It was invaluable!!!

Of course! Thanks for the tip, now it works fiiine! :)

Peace!

---

### Post by gpalouk on 2010-06-26
Worked PERFECT for me too! 
(VMware Workstation 6.5.4 on Ubuntu 10.04 LTS)

This is the SUPER-POWER of Ubuntu Community and UbuntuForums!!!

The best OS and Distro that I ever had !!!!

The last two years that I'm using exclusively Ubuntu I have managed to solve every problem in 5 minutes searching in UbuntuForums..!!!!

Is there other OS (as Windows ](*,) ) and Distro that have such a POWERFULL community all in one place??? NO!!

UbuntuForums RULES!!! :-)

---

### Post by dazndom on 2010-06-27
Could one of you guys please write a HOWTO install vmware for newbs like me who cant follow what you guys are doing, i dont even know what a loop is ??

cheers D

---

### Post by kopelovd on 2010-06-29
> **rhandsome said:**
> I'm trying to install VMWare Workstation 7.1.0 on Lucid 10.4 64bit and I keep getting this error: ./VMware-Workstation-Full-7.1.0-261024.x86_64.bundle: 110: Syntax error: newline unexpected 

Can anyone help?

rhandsome: I had the same issue, it was because I clicked on the "Start Download Manager" button when I downloaded vmware workstation from vmware's site. I found that when I instead click "download manually" I get the full ~314MB file. Try this instead.

---

### Post by tompenrose on 2010-07-20
VMware Workstation 7.1 solves the problems, but of course you must upgrade.  This is actually one of the weaknesses of Linux that Windows is better at handling.  Upgrade the distribution and watch the extinction of purchased proprietary software.  I use Linux almost exclusively, but this is a bummer.

---

### Post by TimsterC on 2010-08-04
> **arch0njw said:**
> The reason the instructions here ([http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32](http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32)) did not work is because there is a superfluous /tmp in the path.  The instructions should be as follows:

tar xvf /usr/lib/vmware/modules/source/vmnet.tar -C /tmp
tar xvf /usr/lib/vmware/modules/source/vmci.tar -C /tmp

cd /tmp

perl -pi -e 's,("vnetInt.h"),\1\n#include "compat_sched.h",' vmnet-only/vnetUserListener.c
perl -pi -e 's,("compat_page.h"),\1\n#include "compat_sched.h",' vmci-only/include/pgtbl.h

tar cvf /usr/lib/vmware/modules/source/vmnet.tar vmnet-only
tar cvf /usr/lib/vmware/modules/source/vmci.tar vmci-onlyThat's because you are already in /tmp and the path prefix "/tmp/" shouldn't be included.  Now, perhaps that is fine for another distro, but not for us.  Using those modified instructions I was able to get workstation 6.5.4 to work just fine.

Thank you for getting the information together!  It was invaluable!!!


Thanks that's great. Works like a charm

---

### Post by Wnutt on 2010-08-08
Worked great for me too.

Just make sure you wipe out all /tmp/vmware-config* directories before attempting to build, so a previously-failed build directory isn&#8217;t caching bad objects.

(thanks to D. Rossier on the second referencing link above).

And also look for old config files in /etc/vmware or in your home ~/.vmware

I had this problem because I first installed the VMWare player before trying the workstation version.

Anyway, thanks again for this very helpful posting !

Fred

---

### Post by hovrashko on 2010-09-25
didnt work for me =(

---

### Post by senormoll on 2010-10-19
I know this thread is a bit old but I just wanted to go on the record as saying this worked for Ubuntu Maverick on kernel 2.6.32.22

Very nice work OP

---

### Post by dkavraal on 2010-11-14
great! eventually worked! I have been dealing with for the last 3 days.

thank you.

---

### Post by thordom on 2010-12-07
Just so you are aware this solution also work for Ubuntu 10.10 with VMware Workstation 6.5.5 (nice to see VMware still haven't resolved this issue!)

---

### Post by arch0njw on 2010-12-07
> **thordom said:**
> Just so you are aware this solution also work for Ubuntu 10.10 with VMware Workstation 6.5.5 (nice to see VMware still haven't resolved this issue!)

Technically 6.5.4 is only supported on an Ubuntu 9.04 host.  Lame, perhaps, but at least they say what they support...

VMware Workstation 7.1 supports Ubuntu 10.04 -- likely it would need some fiddling to run on 10.10.  That's how it has been for years.

This would be why, when I can, I use VirtualBox instead.  The ridiculous lag in support is annoying.

---

### Post by stevecoh1 on 2011-07-31
Great!  I have some info locked away in an old vm, (I no longer use VMWare but Virtual box) and of course I've upgraded my ubuntu many times. 

Now I find that this link:  [http://linux.aldeby.org/vmware-works...rmic-9-10.html](http://linux.aldeby.org/vmware-works...rmic-9-10.html)

is dead.  I relied on this link to tell me what to do when I faced this problem.  Does anyone have the full information salted away somewhere?

---

### Post by android-eve on 2011-08-17
> **stevecoh1 said:**
> Great!  I have some info locked away in an old vm, (I no longer use VMWare but Virtual box) and of course I've upgraded my ubuntu many times. 

Now I find that this link:  [http://linux.aldeby.org/vmware-works...rmic-9-10.html](http://linux.aldeby.org/vmware-works...rmic-9-10.html)

is dead.  I relied on this link to tell me what to do when I faced this problem.  Does anyone have the full information salted away somewhere?
Does [this]("http://www.linuxquestions.org/questions/linux-virtualization-90/vmware-workstation-6-5-5-on-ubuntu-10-04-install-freezes-854709/#post4218918") help?

---

