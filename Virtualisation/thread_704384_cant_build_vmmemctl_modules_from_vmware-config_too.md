---
title: "cant build vmmemctl modules from vmware-config tools script"
date: 2008-02-22
forum: Virtualisation
---

### Post by MiniMe_uk on 2008-02-22
So I've searched the internet looking for solutions to my problem.  Basically I'm running ESX server, with ubuntu 7.10 server running as a guest.  I can install the tools without problem but when it comes to running the vmware-config-tools.pl I get as far as selecting the location of C header files.

I've downloaded the following and untar'd them.

linux-headers-2.6.22-14
linux-source-2.6.22
vmware-any-any-update115

when it comes to running vmware-config-tools.pl I run into problems, I'm not a newbie but am starting to run around in circles :(

root@ubuntu:~# /usr/bin/vmware-config-tools.pl

Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
Trying to find a suitable vmmemctl module for your running kernel.

None of the pre-built vmmemctl modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmmemctl module
for your system (you need to have a C compiler installed on your system)?
[yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-source-2.6.22/include

The path "/usr/src/linux-source-2.6.22/include" is a kernel header file
directory, but it does not contain the file "linux/version.h" as expected.
This can happen if the kernel has never been built, or if you have invoked the
"make mrproper" command in your kernel directory.  In any case, you may want to
rebuild your kernel.

I've not compiled my kernel from source just using the standard kernel image 2.6.22-14

Nothing I've found online suggests that installing VMWare tools on ubuntu is either hard or complicated yet I'm getting stuck at this point.  I have about 6 ubuntu guest machines running already.... so everything is running its just these damn tools that i need to get installed...  Any help or advise would be great.  I've started with a bare bones server install so if there is something missing a pointer in the right direction would be great.

Many thanks

Gabe

---

### Post by fjgaude on 2008-02-22
My only suggestion is a question: Do you have build-essential and xinetd installed?

If not,

```
sudo apt-get install xinetd build-essential
```

That might get you through the rough spot.

---

### Post by MiniMe_uk on 2008-02-22
Hi thanks for the reply, 

build-essential was already installed and I cant see how installing xinet will get me around the problem at hand 

The path "/usr/src/linux-source-2.6.22/include" is a kernel header file
directory, but it does not contain the file "linux/version.h" as expected.
This can happen if the kernel has never been built, or if you have invoked the
"make mrproper" command in your kernel directory.  In any case, you may want to
rebuild your kernel.

do i need to complie a custom kernel to be able make use of vmware tool in ubuntu? I cant believe this is so hard esp when every howto looks so simple to follow and install.

---

### Post by fjgaude on 2008-02-22
Okay... no, I've never had to compile a kernel using vmware server. I get the binary directly from their site at vmware.com. The install.pl file has always worked going through many computers and kernel versions. I don't have any source files on my computers.

As kernel updates come in the only thing necessary is to run the vmware-config.pl file again, in /usr/bin. And we are done, back in business.

---

### Post by Dougga on 2009-10-06
I'm having the identical problem.
There appears to be nothing I can do to get the memory management piece of VMWare tools to work.

I've run the install tool several times after installing various things I felt might help, but alas, nadda.
Details on error:


make[1]: Entering directory '/usr/src/linux-headers-2.6.28-15-server'
  CC [M] /tmp/vmware-config2/vmmemctl-only/backdoorGcc32.o
  CC [M] /tmp/vmware-config2/vmmemctl-only/os.o
/tmp/bmware-config2/vmmemctl-only/os.c: In function 'os_init':
/tmp/vmware-config2/vmmemctl-only/os.c:590: error: 'struct proc_dir_entry' has no member named 'get_info'


Can anyone help?

---

