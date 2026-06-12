---
title: "Installing vmware tools on ubuntu 7.10 guest (C header directory does not exist)"
date: 2007-10-28
forum: Virtualisation
---

### Post by jesseAnger on 2007-10-28
I have Ubuntu 7.10 installed in a virtual machine using vmware. Im now trying to install the vmware tools. Well running the install for the tools via the terminal and a command line i run into this error:

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

I believe i will have to install c headers for 7.10 myself but need instruction on how.

Another action i have preformed was this command 

sudo apt-get install lius-headers-$(uname -r)

i then got the following error: E:/ Couldn't find package lius-headers-2.6.22.14-generic

Any info is appreciated.

---

### Post by bodhi.zazen on 2007-10-28
1. it is liuux hraders with a x (you have linus with a S) ~ :lolflag:

See this link : [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by jesseAnger on 2007-10-28
Besides that can you help?

---

### Post by bodhi.zazen on 2007-10-29
The link I gave you gives step-by-step instructions.

What part are you having a problem with ?

---

### Post by jesseAnger on 2007-10-29
I didn't notice the link, ill let you know how i make out.

---

### Post by wfrutiger on 2007-11-25
Have you tried running the following commaned ?

updatedb 

If you run that command after you install the linux headers it tends to help the vmware-tools installer find the path to the headers.

---

### Post by Brian96 on 2007-11-26
> **bodhi.zazen said:**
> 1. it is liuux hraders with a x (you have linus with a S) ~ :lolflag:

See this link : [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

I am having trouble installing vmware tools. I typically use vmware to run a Windows host, but this weekend I've been using it to play with other distros.

Anyway, I have tried this in separate installations of Xubuntu and LinuxMint, both based on Gutsy. In each case, I get the same error message. Here is the output:

[quote=Shell Output]
rutland@rutland-virtual:~$ sudo /home/rutland/Desktop/vmware-tools-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware-tools.

Execution aborted.

rutland@rutland-virtual:~$ 

[/quote]

When I try to re-install I get the message that it is already installed. If I try to uninstall it says that it can't find lib-something or other. Any ideas?

---

### Post by bodhi.zazen on 2007-11-26
> **Brian96 said:**
> I am having trouble installing vmware tools. I typically use vmware to run a Windows host, but this weekend I've been using it to play with other distros.

Anyway, I have tried this in separate installations of Xubuntu and LinuxMint, both based on Gutsy. In each case, I get the same error message. Here is the output:



When I try to re-install I get the message that it is already installed. If I try to uninstall it says that it can't find lib-something or other. Any ideas?

cd into /home/rutland/Desktop/vmware-tools-distrib/

(the error message is using a relative path starting with a ".")

The run "sudo ./vmware-install.pl"

---

### Post by Brian96 on 2007-11-26
> **bodhi.zazen said:**
> cd into /home/rutland/Desktop/vmware-tools-distrib/

(the error message is using a relative path starting with a ".")

The run "sudo ./vmware-install.pl"

Thanks, that sorted it out. (Although, I never figured out how to remove what little had been installed of vmware tools, so I reinstalled the guest OS and started from scratch.)

---

