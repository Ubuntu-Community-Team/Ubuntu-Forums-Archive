---
title: "Latest 7.10 kernel update broke vmware"
date: 2008-06-22
forum: Virtualisation
---

### Post by josir on 2008-06-22
Hi folks, 

the latest 7.10 kernel (linux7 2.6.22-15-generic) broke my vmware server. It halts with could not open /dev/vmmon. Booting from 2.6.22-14 it is working fine.

The vmware server is 1.0.4 build-56528 (installed using only the repositories)

From older posts, I tried **sudo vmware-config.pl** but I got 

sudo: vmware-config.pl: command not found

Does someone has any tip on how to fix this problem?

Thanks in advance,
Josir Gomes

---

### Post by davekenny on 2008-06-22
I can help with running the vmware-config.pl
cd to /usr/bin
then sudo ./vmware-config.pl

however I can also tell you this might not fix the problem. My vmware server is not running even after rerunning the vmware-config.pl command

davekenny

---

### Post by AbEx on 2008-06-22
Same problem here.
Complete removal and reinstall has not worked for me either.
Haven't had much time to troubleshoot beyond that yet.
Anyone get it going again?

---

### Post by fjgaude on 2008-06-22
If you installed first time around with vmware-any-any-update115 or something like that you need to run the runme.pl file in that program, after you cd to the directory and use ./ before the command.

---

### Post by AbEx on 2008-06-22
Never ran the vmware-any-any-update115 myself. 
Just used the vmware-server package from the repository.

---

### Post by gtdaqua on 2008-06-23
> **josir said:**
> Hi folks, 

the latest 7.10 kernel (linux7 2.6.22-15-generic) broke my vmware server. It halts with could not open /dev/vmmon. Booting from 2.6.22-14 it is working fine.

The vmware server is 1.0.4 build-56528 (installed using only the repositories)

From older posts, I tried **sudo vmware-config.pl** but I got 

sudo: vmware-config.pl: command not found

Does someone has any tip on how to fix this problem?

Thanks in advance,
Josir Gomes

Installing from the repositories is not a good option. VMWare's latest update with security and bug fixes is 1.0.6 as of 23rd June. 

See the sticky in this forum to install VMWare Server. If you are using 64-bit go here:
[http://ubuntuforums.org/showthread.php?t=826626]("http://ubuntuforums.org/showthread.php?t=826626")

It will work with Gutsy too.

---

### Post by doug-M on 2008-06-24
> **gtdaqua said:**
> Installing from the repositories is not a good option. 

Then what is the point of having package management? I realize you are stating what currently works but that isn't really the way a functioning system should operate.

From my point of view I want to use software from the repositories. If too many packages, such as VMWare, don't exist or are broken in the repositories then I'll have to look for an alternative OS. The repositories are one of the key areas that Ubuntu really shines as compared to Windows.

So back on topic.

The Kernel update appears to have broken many different systems.

The Kubuntu forums have an interesting post:
 	
vmware-server not working after kernel update 
[http://kubuntuforums.net/forums/index.php?topic=3095628.0](http://kubuntuforums.net/forums/index.php?topic=3095628.0)

Which seems to point to this:
Kernel Vulnerability in Ubuntu 8.04 LTS. Upgrade Now!
[http://news.softpedia.com/news/Kernel-Vulnerability-in-Ubuntu-8-04-LTS-Upgrade-Now-87195.shtml](http://news.softpedia.com/news/Kernel-Vulnerability-in-Ubuntu-8-04-LTS-Upgrade-Now-87195.shtml)

> ATTENTION: Due to an unavoidable ABI change, the kernel packages have a new version number, which will force you to reinstall and recompile all third-party kernel modules you might have installed. For example, after the upgrade to the above version of your kernel package, a software such as VirtualBox will not work anymore, therefore you must recompile the kernel module by issuing a specific command in the terminal. Moreover, if you use the linux-restricted-modules package, you have to update it as well to get modules which work with the new Linux kernel version.

So the question is how/when will the repository get fixed.

---

### Post by doug-M on 2008-06-25
For anyone else that might hit this thread. After upgrading from Kernel  2.6.22-14 to 2.6.22-15 the symptoms I saw were:


Trying to start or restore a virtual machine gave the error:
```
Unable to change virtual machine power state:
The process exited with an error: End of error message.
```

Trying to reinstall vmware-server gave:
```
E: vmware-server: 
subprocess post-installation script returned error exit status 1
```

In the details:
```
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.
```

---

### Post by doug-M on 2008-06-25
Choosing to boot the 2.6.22-14 kernel with GRUB during startup (hit ESC for the menu). Allows VMWare to work again.

Unfortunately in my case many other modules were updated for the 2.6.22-15 kernel and they don't work with the 14 kernel, for example NVidia drivers.

---

### Post by josir on 2008-06-25
Hi folks, at least I know this is not happening only to me ;)

About the repositories: I prefers also to use the repository and I agree that this is the Ubuntu main advantage over other distributions and other OSes. 

But... vmware is a closed application and I think Canonical and other developers are "priorizing" their efforts on open source apps like kvm and virtualbox.

But... vmware has a huge users base and people should be warned that if we upgrade to new kernel, vmware will stop to work. That's one of the advantages o use repositories, right?

Well, after this repositories talk, let's go back to the main thread:

Does anybody recommends a good tutorial on how to install a vmware server 1.06 on Ubuntu Feisty?

I will also try virtualbox either - some folks told me that virtualbox is better than vmware...

PS: When are they going to fix the repository ? As any other bugs, we have to post this problem on lauchpad bug tracking - after that they will classify the problem and suggests the solution.

Thanks for all comments,
Josir Gomes

---

### Post by lgdahl on 2008-06-26
> **josir said:**
> But... vmware is a closed application and I think Canonical and other developers are "priorizing" their efforts on open source apps like kvm and virtualbox.

The kernel upgrade broke VirtualBox, too.

Lasse

---

### Post by spliner on 2008-06-26
Anyone found a solution to this issue yet?

-Spliner

---

### Post by zimjim on 2008-06-27
I had the same problem but this fixed it 
[https://answers.launchpad.net/ubuntu/+question/36849](https://answers.launchpad.net/ubuntu/+question/36849)

---

### Post by doug-M on 2008-06-27
The above mentioned thread fix gives this solution, I get an error on the install since it tries to run vmware-server, I think I can ignore it though. Where would one normally point this part to "KPKG_DEST_DIR=<where the deb package should go>"?

Or does anyone have an example of the exact commands they used?

sudo apt-get install vmware-server-kernel-source
cd <temp dir>
tar xvjf /usr/src/vmware-server.tar.bz2
cd modules/vmware-server-kernel/
export KPKG_DEST_DIR=<where the deb package should go> # otherwise fakeroot won't work
export KVERS=`uname -r`
fakeroot debian/rules binary-modules
sudo dpkg -i $KPKG_DEST_DIR/vmware-server-kernel-modules-`uname -r`*.deb
cd -
rm -r modules
sudo /etc/init.d/vmware-server restart

---

### Post by jmori on 2008-06-28
> **doug-M said:**
> For anyone else that might hit this thread. After upgrading from Kernel  2.6.22-14 to 2.6.22-15 the symptoms I saw were:


Trying to start or restore a virtual machine gave the error:
```
Unable to change virtual machine power state:
The process exited with an error: End of error message.
```

Trying to reinstall vmware-server gave:
```
E: vmware-server: 
subprocess post-installation script returned error exit status 1
```

In the details:
```
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.
```

Thats exactly the messages that i have. Im kinda glad that im not the only one with this problem. But i just discovered it today. Did anybody body solved it yet? i really need to get back to use those virtual machines

---

### Post by NJN on 2008-06-30
Thanks for the link zimjim, that fixed it for me.

> **doug-M said:**
> The above mentioned thread fix gives this solution, I get an error on the install since it tries to run vmware-server, I think I can ignore it though. Where would one normally point this part to "KPKG_DEST_DIR=<where the deb package should go>"?

doug-M, I used /tmp for both <temp dir> and KPKG_DEST_DIR

---

### Post by josir on 2008-07-02
> **zimjim said:**
> I had the same problem but this fixed it 
[https://answers.launchpad.net/ubuntu/+question/36849](https://answers.launchpad.net/ubuntu/+question/36849)

It worked perfectly. Thanks zimjim.

---

### Post by davidshere on 2008-07-02
In my experience, a kernel update **always** breaks vmware server.  I run three different vmware hosts, and each time updates are sent down, I sift through them looking to see if there's a kernel update.  If there is,  I do this before I run the update: 
```
uname -a > correctKernel
```
so that I can remember which kernel I know works (since the virtual machines are running at that point).  Then I change /boot/grub/menu.lst so that it continues to use the same kernel after the machine is updated.  Note that I assume that the new kernel won't work, because I have yet to see a new one that does.

For the machine I'm on right now, the correct kernel is ```
Linux raptor 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686 GNU/Linux
```  I've been using this one for a long time.  I went through a lot of hassle to get it to work with this kernel.  But that's another story.  It's funny, too, that of the three servers, each has a different "correct" kernel.  The other two are:
```
Linux lancer   2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
Linux cadillac 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

Ubuntu seems to be sending kernel updates down once a week these days, so it is quite a hassle to keep up with.  I'm hearing "Maybe we should use windows to host our virtual machines instead -- it would seem to be much more stable."  At this point it's hard to disagree.

---

### Post by sg3524 on 2008-07-26
The solution on launchpad worked great after working through some local stuff.  I added my notes to launchpad in case someone else can benefit.  Here's a copy

> This worked great after working through some dependencies (Gutsy).

I already had build-essential installed, but also needed kernel-devel. Without kernel-devel the make command executed by the debian/rules file would fail while trying to install (make: **[binary-modules] Error 1). I assume something similar would happen without build-essential.

Also found I had to replace every instance of 'uname -r' in the instructions provided by pure_ascii with the output of that command. When I run uname -r at my command line I get this: 2.6.22-15-generic (don't cut and past this into your commands - run the command and use the output from your system).

So replaced every instance of 'uname -r' above with 2.6.22-15-generic (no quotes).

Worked like a champ.

Thanks pure_ascii for the great solution.

---

