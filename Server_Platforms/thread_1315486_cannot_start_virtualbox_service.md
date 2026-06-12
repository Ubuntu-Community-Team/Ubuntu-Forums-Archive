---
title: "cannot start virtualbox service"
date: 2009-11-05
forum: Server Platforms
---

### Post by chotaguru on 2009-11-05
First of all, Hi all ):P

i have a server installed with ubuntu **9.04** server edition

my problem is that virtualbox module fails compile for the kernel when i do
> /etc/init.d/vboxdrv setup


Here's the vboxdrv log file
> Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.0.10

------------------------------
Deleting module version: 3.0.10
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.0.10/source ->
                 /usr/src/vboxdrv-3.0.10

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.18-128.1.1.el5.028stab062.3 cannot be found at
/lib/modules/2.6.18-128.1.1.el5.028stab062.3/build or /lib/modules/2.6.18-128.1.1.el5.028stab062.3/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


i guess the problem is the kernel version
here's the *uname -r* output
> 2.6.18-128.1.1.el5.028stab062.3
 which obviously looks like a problem

heres the output of *ls /lib/modules/*
> 2.6.18-028stab062.3  2.6.28-11-generic  2.6.28-15-generic  2.6.28-15-server

i see that i could specify the kernel directory, but which directory should i choose, more importantly how can i go about it? :)

My Regards,
:popcorn:

---

### Post by LukeFromAbove on 2009-11-07
Your problem seems to be that the kernel source is not found which is needed to compile a module for the vbox.

Same problem here:
Configuring virtualbox-3.0:
Compilation of the kernel module FAILED!

/var/log/vbox-install.log says:

----------
** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.0.10/source ->
                 /usr/src/vboxdrv-3.0.10

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.28-16-server cannot be found at
/lib/modules/2.6.28-16-server/build or /lib/modules/2.6.28-16-server/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
----------

In my case, solution would be to find the actual kernel source for this binary: 2.6.28-16-server #55-Ubuntu SMP which I have not been able to accomplish so far so:

DOES ANYONE KNOW WHERE TO DOWNLOAD THE SOURCE FOR THIS SERVER KERNEL?

did:
# apt-cache search linux-source
# apt-get install linux-source-2.6.28
# cd /usr/src
# tar xvf linux-source-2.6.28.tar.bz2

and then:
 
# dpkg -i  virtualbox-3.0_3.0.10-54097_Ubuntu_jaunty_i386.deb

Result:  wrong kernel source

---

### Post by lvleph on 2009-11-28
I am having the same issue after installing backports.

EDIT:
The following fixed it
```
sudo apt-get install linux-headers-2.6.31-15-generic
```

---

### Post by boclozz on 2009-12-05
thanks for lvleph  and LukeFromAbove..........

---

### Post by BkkBonanza on 2009-12-05
It's all in the docs if you read them...

---

### Post by LukeFromAbove on 2009-12-05
> **BkkBonaza said:**
> It's all in the docs if you read them...

Interesting comment - it's humanly impossible to "read" all the documentation available, usually it's searched for relevant parts.

Since you seem to know the solution, could you please point me to the place where the answer to my question:

"DOES ANYONE KNOW WHERE TO DOWNLOAD THE SOURCE FOR THIS SERVER KERNEL?"

can be found - that was the essence of the issue. I spent significant time trying to find that with Ubuntu Server on the web.

My solution:  Install Debian, kernel headers, kernel-source, virtualbox - bingo!

It took me much more time trying to find the installed Ubunto-Server kernel source without success than doing a complete Debian re-install.

IMO, if you can't do it with apt-cache search, apt-get install.. and then go on the web trying to find a kernel source for the installed Linux stock kernel and it's not right there something is wrong with the distribution.

---

### Post by BkkBonanza on 2009-12-05
VirtualBox User Manual Section 2.3.2 Installation on Linux Hosts.
I would think this would be the first place to look when having trouble installing into a linux host.

---

### Post by LukeFromAbove on 2009-12-05
> **BkkBonaza said:**
> VirtualBox User Manual Section 2.3.2 Installation on Linux Hosts.
I would think this would be the first place to look when having trouble installing into a linux host.

This has nothing to do how to get the kernel source as I asked. 

Virtualbox install needs kernel source to recompile kernel modules. If kernel sources for running kernel are missing, install fails.

That has been mentioned on this thread before.

Thinking about it and posting does not help, knowing and posting helps.

Thank you

---

### Post by BkkBonanza on 2009-12-05
Did you read the docs indicated there at all. It tells you exactly what to do. You shouldn't skip over stuff. It tells you:

With Debian and Ubuntu releases, you must install the right version of the
linux-headers and if it exists the linux-kbuild package. Current
Ubuntu releases should have the right packages installed by default.

Now, if you need help to install any package at all then thats another question.
And you are wrong - it does not need kernel sources - it needs kernel headers and kbuild. I've done it. But really you should install DKMS and save yourself the bother of this every time a new VBox release comes out.

Once you have installed linux-headers and linux-kbuild then in future kernel updates you will be ready because these will also be updated.

---

### Post by LukeFromAbove on 2009-12-05
> **BkkBonaza said:**
> Did you read the docs indicated there at all. It tells you exactly what to do. You shouldn't skip over stuff. It tells you:

With Debian and Ubuntu releases, you must install the right version of the
linux-headers and if it exists the linux-kbuild package. Current
Ubuntu releases should have the right packages installed by default.

Right, in general. If you just need the headers, the better. But when the kernel source is found, the headers should be there as well.  From the original post, you can read more back there:

> In my case, solution would be to find the actual kernel source for this binary: 2.6.28-16-server #55-Ubuntu SMP which I have not been able to accomplish so far so:
> 
> DOES ANYONE KNOW WHERE TO DOWNLOAD THE SOURCE FOR THIS SERVER KERNEL?


AND:

> Error! Your kernel source for kernel 2.6.28-16-server cannot be found at
> /lib/modules/2.6.28-16-server/build or /lib/modules/2.6.28-16-server/source.
> You can use the --kernelsourcedir option to tell DKMS where it's located.
> Failed to install using DKMS, attempting to install without
> Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
> 

One would assume, based on this error message that the install indeed requires the kernel sources. That was my experience in previous installs. First I thought that just the headers are needed and installed them - nope - it wanted the kernel source!
Since then, I install kernel source - doesn't hurt.

It doesn't matter any more to me, but I think it may be of interest to somebody trying the same thing with that disk:

#define DISKNAME  Ubuntu-Server 9.04 "Jaunty Jackalope" - Release i386

And actually be able to do the install of virtualbox by finding the kernel-source/headers.

So, if you know - please post the web link, where to find the Ubuntu server kernel sources and install them on a machine.

---

### Post by falconindy on 2009-12-05
Kernel source and headers are completely separate animals. Canonical fools people into thinking they're closely related, since  new headers are always pushed out with a new kernel.

Chill, bro. Read the fine manual.

---

### Post by LukeFromAbove on 2009-12-06
> **falconindy said:**
> Kernel source and headers are completely separate animals. Canonical fools people into thinking they're closely related, since  new headers are always pushed out with a new kernel.

Chill, bro. Read the fine manual.

Can't point to the kernel source of kernel 2.6.28-16-server on the web either - right?

---

### Post by falconindy on 2009-12-06
> **LukeFromAbove said:**
> Can't point to the kernel source of kernel 2.6.28-16-server on the web either - right?

WRONG.

[Image]("http://packages.ubuntu.com/jaunty/linux-image-2.6.28-16-server") - [Headers]("http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-16-server")

And here's a git repo: git://kernel.ubuntu.com/ubuntu/ubuntu-jaunty.git

edit: you realize that apt-get has the ability to download source as well.... apt-get source <package-name>

---

### Post by BkkBonanza on 2009-12-06
The easiest way to get the source for your specific install is with Synaptics. Search for linux-source and it will list the package to install matching your kernel version.

You can also use packages.ubuntu.com and type in linux-source and select your version.

Or you can go directly to archive.ubuntu.com and dig through the directory tree to find packages but that's more of a headache.

Pretty much all the info for your requested version is at:
[http://packages.ubuntu.com/jaunty/devel/linux-source-2.6.28](http://packages.ubuntu.com/jaunty/devel/linux-source-2.6.28)

You won't find every minor version archived there because they apply security updates and don't keep every single minor release archived. The current version of 2.6.28 should work fine for any purpose but if you have some weird problem with naming you can use a symlink to resolve.

ln -s blahblah.2.6.28.17-58 blahblah.2.6.28.16

I don't believe there are dependencies wired on specific minor releases. If you need more info contact the Core Devleopers mailing list, details on above page.

As stated above, you do not need kernel sources to build the virtualbox kernel modules. That message you reference may make it seem like you do but the headers have always been enough and I've built it several times. I can't think of any plausible reason why you'd need kernel sources where others only need the headers.

I realize you don't need anything any more because you already switched distros to Debian. I just wonder how that choice is going to pan out for you over time. Nothing wrong with Debian but Ubuntu does add a layer of usefulness and friendliness that it appears will benefit you.

---

### Post by LukeFromAbove on 2009-12-06
> **BkkBonaza said:**
> 
You won't find every minor version archived there because they apply security updates and don't keep every single minor release archived. The current version of 2.6.28 should work fine for any purpose but if you have some weird problem with naming you can use a symlink to resolve.

ln -s blahblah.2.6.28.17-58 blahblah.2.6.28.16


I don't believe there are dependencies wired on specific minor releases. If you need more info contact the Core Devleopers mailing list, details on above page.


Thanks - that makes sense now. Maybe I should have just renamed or symlinked the installed kernel.. headers from the base version "2.6.28-16" (which came down fine) and added the "-server" in this instance and be done with it.

> **BkkBonaza said:**
> 
As stated above, you do not need kernel sources to build the virtualbox kernel modules. That message you reference may make it seem like you do but the headers have always been enough and I've built it several times. I can't think of any plausible reason why you'd need kernel sources where others only need the headers.


The cause for this problem was a mis-match between the name of the running kernel and the installable kernel-headers/sources. 
I tried the 2.6.28-16 - maybe just renaming/symlinking the -server to it would have fixed it?

I got hooked on the kernel sources, because when there is a kernel, the source needs to be somewhere. The same issue existed with kernel-headers. If the kernel source was not needed and the kernel-header name would match the kernel, this message would not come up. They did not match.

I found this link:  [http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/](http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/)

> **BkkBonaza said:**
> 
I realize you don't need anything any more because you already switched distros to Debian. I just wonder how that choice is going to pan out for you over time. Nothing wrong with Debian but Ubuntu does add a layer of usefulness and friendliness that it appears will benefit you.

Well, I evaluated server Linuxes in 2004 and decided for Debian, one reason being HP offering some kind of support and the other's Red Hat, SuSE/Novell were costly, besides other reasons. At that time Ubuntu server came out short in searches for possible support on web forums.

This time with a small project, I thought to give Ubuntu server a spin again - it's looking really good. On the support side though and with this instance of the kernel name not matching an installable package with the time involved to research it, I think Debian is still a better place for me. Desktop may be different, but that's not what I need.

---

### Post by LukeFromAbove on 2009-12-06
> **falconindy said:**
> WRONG.

[Image]("http://packages.ubuntu.com/jaunty/linux-image-2.6.28-16-server") - [Headers]("http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-16-server")

And here's a git repo: git://kernel.ubuntu.com/ubuntu/ubuntu-jaunty.git

edit: you realize that apt-get has the ability to download source as well.... apt-get source <package-name>

Yes, please note from my first post here:

> did:
> # apt-cache search linux-source
> # apt-get install linux-source-2.6.28  <- best fit

You realize the [Image]("http://packages.ubuntu.com/jaunty/linux-image-2.6.28-16-server") (your answer) <>[Source]("http://packages.ubuntu.com/jaunty/linux-source-2.6.28-16-server") (my question) - right?

And the installed server kernel source or patches leading to the source are ... apparently not part of the jaunty package:

~$ wc Jaunty-All-Packg.txt
  30229  264134 2427697 Jaunty-All-Packg.txt
~$ grep 2.6.28-16  Jaunty-All-Packg.txt   | grep server | grep source
~$ grep 2.6.28-16  Jaunty-All-Packg.txt   | grep source
~$ grep 2.6.28-16  Jaunty-All-Packg.txt   | grep kernel
linux-headers-2.6.28-16 (2.6.28-16.55) [security] Header files related to Linux kernel version 2.6.28
linux-headers-2.6.28-16-generic (2.6.28-16.55) [security] Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-16-server (2.6.28-16.55) [security] Linux kernel headers for version 2.6.28 on x86/x86_64
linux-image-2.6.28-16-generic (2.6.28-16.55) [security] Linux kernel image for version 2.6.28 on x86/x86_64
linux-image-2.6.28-16-server (2.6.28-16.55) [security] Linux kernel image for version 2.6.28 on x86/x86_64
linux-image-2.6.28-16-virtual (2.6.28-16.55) [security] Linux kernel image for version 2.6.28 on x86/x86_64
linux-restricted-modules-2.6.28-16-generic (2.6.28-16.21) [security] Non-free Linux kernel modules for version 2.6.28 on x86/x86_64
linux-restricted-modules-2.6.28-16-server (2.6.28-16.21) [security] Non-free Linux kernel modules for version 2.6.28 on x86/x86_64

---

