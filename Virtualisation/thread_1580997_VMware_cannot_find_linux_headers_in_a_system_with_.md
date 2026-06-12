---
title: "VMware cannot find linux headers in a system with a just-compiled kernel"
date: 2010-09-24
forum: Virtualisation
---

### Post by JanusDC on 2010-09-24
I've installed VMware 7.0.0 in Ubuntu 10.04. Then I've upgraded Ubuntu to 10.10 (the beta release) and I could not compile the vmware modules any more since it complains it cannot find the linux headers.

My first attempt was to check I have the headers installed and just in case to make a symlink from the correct headers to /usr/src/linux. It doesn't work. So, I just uninstalled VMware and installed it again. Same result. Then I installed the ubuntu package with the sources and compiled the kernel by myself, again I pointed /usr/src/linux to the correct sources. Same result, VMware still complains about not finding the headers. I reinstalled VMware again with no luck.

What could be the problem? I am using kernel sources 2.6.35 (ubuntu version) and VMware version 7.0.0.

Cheers.

---

### Post by fjgaude on 2010-09-24
I think VMware is not keeping up with the way the kernel is changing. If you go here you might be able to fix your issue:

[https://bbs.archlinux.org/viewtopic.php?pid=815476](https://bbs.archlinux.org/viewtopic.php?pid=815476)

---

### Post by JanusDC on 2010-09-24
Thanks for you answer. However it didn't work. I guess it could be because the patch is for vmware 7.1.1 and I have vmware 7.0.0. However, it didn't complain about not being able to apply the patch. But at the end I got the same error:

janus@katu /tmp $ sudo vmware-modconfig --console --install-all
gcc and kernel headers must be installed

and if I just run vmware I get a window saying that it cannot find the kernel headers and asking me to point it out (which is useless).

---

### Post by fjgaude on 2010-09-24
You do have the normal utilities, like gcc, installed?

---

### Post by JanusDC on 2010-09-24
> **fjgaude said:**
> You do have the normal utilities, like gcc, installed?

Yes, I do. I guess the problem shouldn't be in that direction, since I just compiled the kernel (i.e. all the tools to compile the modules are there), however, keep shooting, probably  there is something I've forgot.

---

### Post by fjgaude on 2010-09-24
I tell you, things have been changing so fast these days... The latest updates to Ubuntu x64, 10.04 has caused the latest update to VMware Player 3.1.2 to not work, and even 3.1.1 doesn't any longer work... we have wait and see what comes out of VMware or what patch may come from this forum... sorry!

---

### Post by JanusDC on 2010-09-24
Ok. Thanks! Will see if I can get VMware 7.1.1 to try that patch.

Cheers.

---

### Post by TJet1.8 on 2010-09-30
Every kernel release has it's own set of kernel headers.
Whenever you upgrade your kernel, you will need to download the "new" kernel headers and recompile the vmware modules to work with the new kernel/kernel headers.

If you upgraded from ubuntu 10.04 to ubuntu 10.10, you will have the new kernel...and the "old" kernel headers, possibly the old gcc files as well.
VMware will not compile properly this way.

So...install the new kernel headers and gcc:
sudo apt-get install linux-headers-$(uname -r) gcc

Then try to re-compile the VMware modules:
sudo vmware-modconfig --console --install-all

Now...you can also install the dkms framework (Dymanic Kernel Module Support) to automatically install the the Linux Header files automatically everytime a new kernel is installed.

sudo apt-get install linux-headers-$(uname -r) gcc dkms

This way, all you have to do after a kernel update is re-compile the vmware modules with the "sudo vmware-modconfig --console --install-all" command.

Also...VMware Workstation 7.0.0 is quite buggy and has known issues with compilation errors.
They fixed it with 7.1...and they recently released 7.1.2 .
I would try to install the newest version as it is free to upgrade from 7.0 to 7.1.2 "if" you have a legal version of VMware Workstation.

Hope this helps...good luck.

:popcorn:

---

### Post by nvjopsddhapnv on 2010-12-17
> **fjgaude said:**
> I think VMware is not keeping up with the way the kernel is changing. If you go here you might be able to fix your issue:

[https://bbs.archlinux.org/viewtopic.php?pid=815476](https://bbs.archlinux.org/viewtopic.php?pid=815476)

I am facing the same problem after upgrading to ubuntu 10.10 ... I have done all the steps mentioned in the above link but no hope ... I am getting the same error ... any help??

---

### Post by blacksunseven on 2010-12-18
Just spent the last three hours with this issue but the good news, I've solved it (for me, at least). Here's what I did:

[LIST=1]
[*]sudo apt-get install linux-headers-`uname -r` --reinstall
[*]ln -s /usr/src/linux-headers-`uname -r`/include/generated/autoconf.h /usr/src/linux-headers-`uname -r`/include/linux/autoconf.h
[*]ln -s /usr/src/linux-headers-`uname -r`/include/generated/utsrelease.h /usr/src/linux-headers-`uname -r`/include/linux/utsrelease.h
[*]Try running the vmware-tools install script again
[/LIST]

I know this isn't presented elegantly but I am so tired; just wanted to get this on here for all those struggling.

---

### Post by HermanAB on 2010-12-20
The root of the problem:
When you compile the kernel, ensure that the version in the Makefile is the same as that reported by uname -a.

The moral of the story is that if you are using VMware, don't upgrade your kernel.

---

### Post by subarashi on 2011-02-25
Hi everyone, i got the same problem as many of you installing my vmware workstation 7.0.0 build-203739 on ubuntu 10.10 with a kernel  2.6.35-25-generic

I am just a starter on ubuntu, so don't expect a reply from you if you have any concern what i am about to post. I just want to help, like others did for me. 

The following steps worked for me.

1- I patched my kernel according to a website, sorry i lost the link, but this is what i did

cd /tmp
wget [http://www.sputnick-area.net/scripts...el-2.6.35.bash](http://www.sputnick-area.net/scripts...el-2.6.35.bash)
sudo chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
sudo ./vmware7.1.1-patch-kernel-2.6.35.bash

The script will say...

sudo vmware-modconfig --console --install-all

Then...

start the VMWare workstation as usual from...
Applications > System Tools > VMWare Workstation


For me it didn't work after that, for others it might. I got problem with gcc and linux header but everything was already installed.

2- After i followed what Blacksunseven said above 
   a- ln -s /usr/src/linux-headers-`uname -r`/include/generated/autoconf.h /usr/src/linux-headers-`uname -r`/include/linux/autoconf.h
   b- ln -s /usr/src/linux-headers-`uname -r`/include/generated/utsrelease.h /usr/src/linux-headers-`uname -r`/include/linux/utsrelease.h
 
I compiled again vmware modules
sudo vmware-modconfig --console --install-all

I got problem with vmnet

3- I used the following link to solve my vmnet problem
[http://bovitron.com/blogostu/2010/06/01/vmware-workstation-with-linux-kernel-2-6-33-4/#comments](http://bovitron.com/blogostu/2010/06/01/vmware-workstation-with-linux-kernel-2-6-33-4/#comments) 

i compiled again vmware modules, no errors and start vmware, worked with success  :D . 
I just hope, this will help some of you

---

