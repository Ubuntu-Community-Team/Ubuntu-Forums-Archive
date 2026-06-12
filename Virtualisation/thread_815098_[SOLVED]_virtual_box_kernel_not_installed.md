---
title: "[SOLVED] virtual box kernel not installed"
date: 2008-06-01
forum: Virtualisation
---

### Post by famous3warriors on 2008-06-01
I have virtual box installed and working.  I had not used virtual box for about a week did some upgrades and now I was going to use it to change some dwg files to eps files and now it will not open.  It gives me this error of virtual box kernel not installed.  I had all of my programs like autocad and adobe cs2.  How can I fix this problem?  Thanks.  I really do appreciate your help. Oh yeah I am using Ubuntu 8.04 hardy heron and virtual box 1.6.0.

---

### Post by bluefrog on 2008-06-01
you certainly have upgraded your kernel.

Do as you are told in the error message.

---

### Post by famous3warriors on 2008-06-01
Thanks for the advice it worked thanks.

---

### Post by daqron on 2011-01-06
> **bluefrog said:**
> Do as you are told in the error message.
But it's easier to blindly dismiss all error messages and Google them instead. We've been conditioned to expect that when something doesn't work in Linux we will face a long and tedious process involving numerous exotic shell commands, package upgrades, and throwing of objects across the room in frustration. How could a person know that simply doing what it says in the error message would actually work?

Out of naive curiosity, why can't vbox execute the necessary changes by itself if it already 'knows' what is wrong?

---

### Post by JKyleOKC on 2011-01-07
> **daqron said:**
> Out of naive curiosity, why can't vbox execute the necessary changes by itself if it already 'knows' what is wrong?Would you really want any running program to blindly make major modifications to your system, automatically? Seems to me that one of the chief advantages of *nix systems over Microsoft's offerings is that they don't permit, much less encourage, such shenanigans.

Specifically, compiling a new kernel driver, and then making it available for automatic installation into the kernel, are actions that require root privileges. VirtualBox, however, runs as the logged-in user although it does install the driver as root at boot time.

The compile takes several minutes, too, so if it happened without warning at boot time you would quite likely decide something had failed and try to take back control of things -- possibly making the system unbootable.

And finally, the last couple of automatic kernel upgrades have failed to include the header files required to compile the driver, causing the setup process to fail until I downloaded the headers manually.

All in all, the current system seems to be a good compromise between automatic repair and making the system vulnerable...

---

### Post by junkboxy on 2011-01-09
> **bluefrog said:**
> you certainly have upgraded your kernel.
 
Do as you are told in the error message.
 
Reminds me of the infamous Windows error in the dial-up days. "There is no Dialtone" 
about as straight forward as it gets. Quite possibly the most clear error message around. You got no dial Tone bub...is that phone line plugged in?
 
Yeah if all else fails actually read the error message.

---

### Post by sdowney717 on 2011-01-10
apparently it is no longer automatic.
I have similar issues and people say install dkms and 
you wont get this message.
But then some say it is not designed to be automatically upgrading the kernel. 

So can you have it both ways?** Either it is or it is not**, designed to be automatic.

---

### Post by JKyleOKC on 2011-01-10
DKMS is **supposed** to be automatic; that's its whole reason for existence. However the two most recent kernel updates that I've gotten through automatic updating have failed to include the required header files, so that the "automatic" upgrade of the modules fails. And since DKMS sends its output, **including error messages**, to /dev/null I never saw any indication of the failure until I tried to launch vbox after doing the update.

Until the developers put the header files back in as something included in the update packages, it's necessary to manually download the linux-header files for the new kernel after doing the update, and then run the vboxdrv setup command again.

---

