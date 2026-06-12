---
title: "Your kernel was built with &quot;gcc&quot; version &quot;4.2.3&quot;, you're using &quot;4.2.4&quot;"
date: 2008-12-02
forum: Virtualisation
---

### Post by jackalista on 2008-12-02
Hi Folks,

I'm running ubuntu 8.04 and have been simply accepting the software updates as they come along.  Yesterday I tried to fire up vmware workstation and it wouldn't start:

----------------
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl
----------------


So I tried /usr/bin/vmware-config.pl.  It is complaining that my kernel was built with gcc 4.2.3, while I'm trying to use gcc 4.2.4.  I'm pretty sure I recently saw a software update to gcc, which may explain why the new version is installed.  Here's the message I got from vmware-config.pl:

----------------
Your kernel was built with "gcc" version "4.2.3", while you are trying to use "/usr/bin/gcc" version "4.2.4". This configuration is not recommended and VMware Workstation may crash if you'll continue. Please try to use exactly same compiler as one used for building your kernel. Do you want to go with compiler "/usr/bin/gcc" version "4.2.4" anyway? [no] 
----------------

Long story short, I don't really know what's going on here and I can't run vmware wkstn which is a big problem.  I suspect that both the kernel and gcc have been updated, it appears that at least gcc has been updated since I'm pretty sure I saw a recent update to it.  

How do I fix this and what exactly is wrong here?  Also, how does one avoid this in the future?  I guess I shouldn't take every software update without thinking?  I don't mind doing upgrades at reasonable times, but I'd rather do it *on purpose* than get roped in without consent as I am now, if someone can explain how to fix it and how to avoid it in the future I'd be most grateful.

Here's the full transcript from running vmware-config.pl:



# /usr/bin/vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

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

---

### Post by bodhi.zazen on 2008-12-02
You can either say "yes" to that final question :

> "/usr/bin/gcc" version "4.2.4" anyway? [no] 

Or you can set your gcc version. See this thread :

[http://ubuntuforums.org/showthread.php?t=65638](http://ubuntuforums.org/showthread.php?t=65638)

---

### Post by casperfelix on 2008-12-20
Had the same problem and decided to compile with later version of GCC. Worked fine, no problems yet.

---

### Post by derekshaw on 2009-01-01
> **bodhi.zazen said:**
> 

Or you can set your gcc version. See this thread :
[http://ubuntuforums.org/showthread.php?t=65638](http://ubuntuforums.org/showthread.php?t=65638)

This does not work.  

Setting the CC envvar to 4.2.3 (to match what the kernel was compiled with) results in the same message from vmware-config.pl.  

The newest workstation ('.bundle') does not complain, but the vmware server 2 still uses the perl-configuration script, and setting the CC envvar definitely has no effect.

has anyone found a place to download gcc 4.2.3?  If someone is compiling ubuntu kernels with it, it must be available somewhere.  Any tips appreciated.

Thanks in advance!

---

### Post by dcstar on 2009-01-02
> **derekshaw said:**
> 
........
has anyone found a place to download gcc 4.2.3?  If someone is compiling ubuntu kernels with it, it must be available somewhere.  Any tips appreciated.


Why?, I have not seen one person report a problem with just acknowledging the message and letting it run anyway.

---

### Post by derekshaw on 2009-01-03
> **dcstar said:**
> Why?, I have not seen one person report a problem with just acknowledging the message and letting it run anyway.

Because this is is not a hobbyist machine.  It is going to be a production machine, with mission-critical applications running on it, and the author of the software *explicitly* warns against compiling the modules with a different compiler than the one used to compile the kernel.

I would be a fool to put my client's business into such a situation, and if it went sideways, and the client fired me, I wouldn't be surprised to be sued for negligence in the performance of my duties.  30 people not working for a day is the same as me not working for a month.  In this case it's worth it do "do it right".

In the event, I could not find a reasonable way to either install the earlier version of gcc, or roll-back the changes that were made by the updates, so I decided to re-install ubuntu 8.04, 'pinned' (locked) the gcc versions, then applied the patches, then installed vmware server, and it compiles the modules without complaint.

Not a great solution, but one that lets me move forward without violating an explicit injunction.

---

### Post by bodhi.zazen on 2009-01-04
> **derekshaw said:**
>  

<clip> 

Not a great solution, but one that lets me move forward without violating an explicit injunction.

Why is this not a great solution ? If I were using Ubuntu in your situation I would go with 8.04 (LTS).

Otherwise it sounds as if it is up and running, so, IMO, perfect.

---

### Post by StormTrooperVII on 2009-01-07
> **bodhi.zazen said:**
> Why is this not a great solution ? If I were using Ubuntu in your situation I would go with 8.04 (LTS).

Otherwise it sounds as if it is up and running, so, IMO, perfect.

First of all, the original poster WAS using 8.04, as am I.  

The reason that his solution was not great is because he did the responsible thing and applied the ubuntu-supplied patches as they were given to him, but the packages were mismatched and his progress was halted.  His choices were:
1) Let it compile anyway despite explicit warning by the author (NOT an option, because he REQUIRED it to be 100% stable)
2) Reinstall from scratch, and simply don't apply the patches that cause the mismatch (not a great solution because you should be able to apply packages).

The fault here is not with the original poster, or with vmware, but rather with Ubuntu's extraordinary failure to intelligently and properly keep its repositories in a sensible state.  It's extremely dumb to have a different version of gcc installed on your machine than what was used to compile your kernel AND no option to get the proper one.  Note that the minor version changed (4.2.3 vs 4.2.4) but the repositories only distinguish between 4.1 and 4.2 etc on that level.

This is a bug in ubuntu (specifically the repositories).  It should be fixed as immediately as possible, and it should NOT happen again.

</rant>

---

### Post by dcstar on 2009-01-07
> **derekshaw said:**
> Because this is is not a hobbyist machine.  It is going to be a production machine, with mission-critical applications running on it, and the author of the software *explicitly* warns against compiling the modules with a different compiler than the one used to compile the kernel.

I would be a fool to put my client's business into such a situation, and if it went sideways, and the client fired me, I wouldn't be surprised to be sued for negligence in the performance of my duties.  30 people not working for a day is the same as me not working for a month.  In this case it's worth it do "do it right".

In the event, I could not find a reasonable way to either install the earlier version of gcc, or roll-back the changes that were made by the updates, so I decided to re-install ubuntu 8.04, 'pinned' (locked) the gcc versions, then applied the patches, then installed vmware server, and it compiles the modules without complaint.

Not a great solution, but one that lets me move forward without violating an explicit injunction.

A "not recommended" message is a long way away from any sort of explicit warning saying never to do this, and the author gives people the option to easily override the message and carry on - so if you do this then you check if the program runs, and most of us have no problem at all.

Major differences in compiler versions may well cause problems, minor differences in complier versions may not as they could just be things like bug fixes to ensure that the compiler runs correctly - you'd have to check the release notes to see what actually changed. I'd seriously doubt that much of the compiler output would be be different with a minor version change, and if it was then it may not run at all.

Many (many) packages that are currently in the repositories have probably been compiled using compiler versions far removed from the kernel you are running now, if you are going to be true to your philosophy you need to download the source of every package you are currently running and recompile them - and **never** install a .deb package you don't know has been compiled with the version your kernel used.

Of course you are quite entitled to decide that you don't want to accept this sort of risk with VMWare, but don't exaggerate it to something more than the message is.

---

### Post by StormTrooperVII on 2009-01-08
> **dcstar said:**
> Many (many) packages that are currently in the repositories have probably been compiled using compiler versions far removed from the kernel you are running now
You've missed the point though, vmware is a kernel module and it's good practice to compile kernel modules with the same version of gcc as the kernel.  If this was just a regular program, like firefox or something, then sure it doesn't really matter what version of gcc it's compiled with, so long as all necessary libraries are present.  And, it doesn't matter how those libraries were compiled either.

We trust that all kernel modules, or anything else that deals with the kernel closely, are compiled correctly for the kernel that we're using.  That's the job of the repository maintainers: to worry about that kind of stuff so that we don't have to.


> **dcstar said:**
> Of course you are quite entitled to decide that you don't want to accept this sort of risk with VMWare, but don't exaggerate it to something more than the message is.
How exactly do you exaggerate "This configuration is not recommended and VMware Workstation may crash if you'll continue."?  

To confess, I chose to do what you say on my personal workstation, and just ignore the message and continue, but for a production environment when your job is on the line, you take messages like that VERY seriously.  9 times out of 10, it's probably nothing, but it's just not worth the laziness that 10th time.

---

### Post by PilotJLR on 2009-01-08
IF you are running production **server** workloads on VMware Workstation... yes, you should be retrained (I hope you are not fired).

If you are using Server2, then 8.04.1 is not on the guest compatibility list... 8.04 is. This is one reason why a prebuild kernel module is not available:

[http://pubs.vmware.com/guestnotes/](http://pubs.vmware.com/guestnotes/)

You're between a rock and a hard place... staying on 8.04 and not applying updates is not an acceptable solution (to me), but going to a newer kernel requires you a compile a kernel module.

**But overall... if this is really mission critical, then you should be using a guest OS on the compatibility list (CentOS, if you like) and a better hypervisor (ESXi).**
I would never put a mission critical workload on Server.

---

### Post by derekshaw on 2009-01-10
I logged on to note that the just-distributed kernel (for ubuntu 8.0.4 --  on the approved list for vmware SERVER)  has been compiled with gcc 4.2.4, so the distribution of compiler and kernel are, for now, once again synchronised.

```
xxx:~$ cat /proc/version
Linux version 2.6.24-23-generic (buildd@crested) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:13:46 UTC 2008
```

That means this thread should be closed.

---

### Post by JohnPhys on 2009-01-12
This thread should *not* be closed, as I still get the same error.  While vmware-config.pl no longer complains, each time I reboot the machine and run vmware in a console it tells me that it has not been correctly configured for the system, and to run /usr/bin/vmware-config.pl

While I have no direct evidence that the gcc/kernel mismatch is still responsible, I highly suspect it since I did not have these errors prior to that issue.  I even ran /usr/bin/vmware-uninstall.pl and re-installed using version 1.0.8 to try and clear up the issue, but it remains.

How is vmware/whatever determining what the version of gcc is?  I notice that apt-cache policy on gcc-4.2 gives version 4.2.4 but on gcc it gives 4.2.3.

---

### Post by dcstar on 2009-01-14
> **JohnPhys said:**
> 
.........
How is vmware/whatever determining what the version of gcc is?  I notice that apt-cache policy on gcc-4.2 gives version 4.2.4 but on gcc it gives 4.2.3.

The vmware-config.pl script uses: ```
gcc -dumpversion
``` and /proc/version.

---

### Post by dcstar on 2009-01-14
> **StormTrooperVII said:**
> You've missed the point though, vmware is a kernel module and it's good practice to compile kernel modules with the same version of gcc as the kernel.  If this was just a regular program, like firefox or something, then sure it doesn't really matter what version of gcc it's compiled with, so long as all necessary libraries are present.  And, it doesn't matter how those libraries were compiled either.
........

Whether it is a kernel module or not doesn't really matter if the code is compiled correctly. Since most modules are compiled at the same time as a kernel then it usually isn't an issue - and it will only be an issue if a subsequent compilation creates incorrect code.

It is highly unlikely that a 3rd level version difference in gcc will result in different code being generated - and if it did chances are you would find out immediately as the VMWare module would not work (or "crash" as per the warning message). As I pointed out, you need to see the gcc developer's release notes to see the difference between the two versions to determine any outcome on a particular use. If it was a second level version difference - like 4.2 vs 4.3 - then there may well be differences in compiler output, but not with this minor difference.

As far as I can see, the VMWare install compilation with your current kernel headers generates code with the correct kernel entry points for all the other precompiled VMWare code to use - which is why a recompile is necessary after every kernel change.

---

### Post by Zack McCool on 2009-01-14
Really, what it comes down to is this:  VMWare workstation is not designed for a production environment.  Really, Server isn't either.  If your job is on the line because of a VM issue, you owe it to yourself to scrap the host OS altogether, and install ESXi on compatible hardware.  That is sure to remain stable.

I use VMWare Server on 8.04.1, and did compile using the mis-matched kernel and compiler.  This machine runs a few VM's 24x7, and they've been going for weeks without issue.

I also run ESX 3.0 on a server, and run my Directory, SQL and Web servers there, but I wouldn't trust them to the standard add-on products...

---

### Post by slashzulu on 2009-01-31
>I logged on to note that the just-distributed kernel (for ubuntu 8.0.4 -- >on the approved list for vmware SERVER) has been compiled with gcc 4.2.4, >so the distribution of compiler and kernel are, for now, once again >synchronised.

so, is someone going to point out HOW you upgrade to the
latest kernel image compiled with gcc 4.2.4 ?

Do you just point to a 'special' repository?
Im running linux-image-2.6.24-23-generic and tried apt-get install
and I keep getting a 'its already  the newest version message .....

---

### Post by dcstar on 2009-02-01
> **slashzulu said:**
> >I logged on to note that the just-distributed kernel (for ubuntu 8.0.4 -- >on the approved list for vmware SERVER) has been compiled with gcc 4.2.4, >so the distribution of compiler and kernel are, for now, once again >synchronised.

so, is someone going to point out HOW you upgrade to the
latest kernel image compiled with gcc 4.2.4 ?
........

If you are that desperate then compile it yourself. There are many detailed HOWTOs on kernel compilation and installation.

---

### Post by slashzulu on 2009-02-01
>so, is someone going to point out HOW you upgrade to the
latest kernel image compiled with gcc 4.2.4 ?

>Do you just point to a 'special' repository?
Im running linux-image-2.6.24-23-generic and tried apt-get install
and I keep getting a 'its already the newest version message .....

David wrote:
>If you are that desperate then compile it yourself. There are many detailed HOWTOs on kernel compilation and installation.
_
Desperation has nothing to do with it, I can see your
a student of of english - you had no idea what the question asked.
It sounds as if in your rambling's you basically recompile a kernel image instead of downloading an image. 
Thats all I was after , but its ok David ,your a good boy anyway....  uff

---

### Post by slashzulu on 2009-02-03
For VMWARE kernel compiled with wrong gcc version,  quickest fix is to  boot with older kernel at boot prompt!
:popcorn:

---

