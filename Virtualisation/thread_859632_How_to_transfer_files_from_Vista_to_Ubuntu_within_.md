---
title: "How to transfer files from Vista to Ubuntu *within VMWare*"
date: 2008-07-14
forum: Virtualisation
---

### Post by Mountaingod on 2008-07-14
I am using VMWare Workstation 6 to run Hardy - the host OS is Vista Ultimate 32.

I simply want to know how I can transfer files from the host OS's hard drive to the virtual drive of the guest OS (ubuntu).

My apologies if it's already been posted, if so I can't seem to find the right words to search for. A link to a howto or FAQ would suffice. Thanks.

---

### Post by fsmithred on 2008-07-15
Set up samba on ubuntu and create a share for your vista user. Then in vista, you can find the share in your network places (or whatever it's called).

---

### Post by Mountaingod on 2008-07-15
My problem appears to be something to do with VMware. I have Samba and smbf installed, but I am dubious as to whether VMware Tools has installed properly. I can get to the internet but no shared folders (on my home network) from Ubuntu. I know these shared folders are there because I CAN get to them from Vista.

During installation of VMWare Tools (from the source tarball), I got this:

> Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmhgfs-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config0/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/cpName.o
In file included from include/linux/string.h:11,
                 from /tmp/vmware-config0/vmhgfs-only/cpName.h:18,
                 from /tmp/vmware-config0/vmhgfs-only/cpName.c:18:
include/linux/types.h:40: error: conflicting types for ‘uintptr_t’
/tmp/vmware-config0/vmhgfs-only/vm_basic_types.h:170: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/tmp/vmware-config0/vmhgfs-only/cpName.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

I have all the packages it is asking for, except 'the kernel sources for your running kernel', which I don't know what that is. The installation CD I have is for Gutsy, not Hardy (I installed and immediately upgraded), so that wouldn't help.

Funnily enough, I installed VMware Tools before upgrading, and I COULD see the MSHOME network - it disappeared after the upgrade to Hardy. Once I had uninstalled & reinstalled VMware Tools - and got the strange issue above - I still can't get access to MSHOME back. Could it therefore be a compatibility issue with Hardy and VMware Tools?

---

### Post by fsmithred on 2008-07-15
Install linux-source-2.6.whatever, where "whatever" corresponds to the kernel version you're running, then run the script they tell you to run. You can look in synaptic for linux-source and install it from there. To find out which kernel you're running, do:

uname -r

If you want to see your Vista shares in Ubuntu, you need to mount them. Search for smbmount to find instructions on that. I've always done it the other way (make shares in linux and access them from windows). You need to install the samba server to do the latter.

---

### Post by bodhi.zazen on 2008-07-15
Samba should be working out of the box :)

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

---

### Post by Keithel on 2008-07-16
> **Mountaingod said:**
> 
During installation of VMWare Tools (from the source tarball), I got this:
[...]
Building the vmhgfs module.

[...]
In file included from include/linux/string.h:11,
from /tmp/vmware-config0/vmhgfs-only/cpName.h:18,
from /tmp/vmware-config0/vmhgfs-only/cpName.c:18:
include/linux/types.h:40: error: conflicting types for &#8216;uintptr_t&#8217;
/tmp/vmware-config0/vmhgfs-only/vm_basic_types.h:170: error: previous declaration of &#8216;uintptr_t&#8217; was here
[...]

I have all the packages it is asking for, except 'the kernel sources for your running kernel', 

AFAIK you do not need the kernel sources -- just the kernel headers.


> **Mountaingod said:**
> Funnily enough, I installed VMware Tools before upgrading, and I COULD see the MSHOME network - it disappeared after the upgrade to Hardy. Once I had uninstalled & reinstalled VMware Tools - and got the strange issue above - I still can't get access to MSHOME back. Could it therefore be a compatibility issue with Hardy and VMware Tools?

**First thing**: The VMHGFS module will only provide you access to filesystems on the *Host from the Guest*.  You are wanting access to files on the _Guest from the Host_.  In order to provide this, you'll have to go the approach other people are talking about -- set up SMB filesharing (windows shared folders, etc).  The vmhgfs module not installing will have no affect on this whatsoever.

**Second thing**: If you wish to get the vmhgfs module compiling and working, there is a small guide posted on this forum showing how to get VMware Tools building and installing properly, as provided by VMware Workstation 6.0.4 build 93057, and a few other versions.  Specifically, if you get the above error you reported, the patch I provided will most likely fix your problem, so follow the guide, and the vmhgfs should then build and install properly.
[VMware Tools for VMware Workstation 6.0.4 build 93057 on Ubuntu 8.04 guest]("http://ubuntuforums.org/showthread.php?t=846691")

---

### Post by Mountaingod on 2008-07-17
Thanks a lot everyone. I'll try all these and get back to you.

---

### Post by Mountaingod on 2008-07-17
Ok, here is my problem as of now. Thanks to Keithel, VMware Tools is now installed correctly - whether I strictly needed it or not, it's nice to know it can no longer pose a problem.

I still can't see the Windows network from within the Ubuntu guest however. Furthermore, I have set up a file in said Ubuntu guest (set the SMB password and so on), with no apparent problem, yet this file does not show up in the Vista host. In fact, Ubuntu itself can't even see this shared file in Places > Network > Windows Network .

Something is preventing this communication from getting to or from the virtual machine, despite internet access itself working fine. Again, there is no discernible problem with Samba or anything else in the Ubuntu guest.

God, I hate networking issues. If it comes to the worst I might even have to reinstall Feisty, wherein I could still see others' shares in my home network. I get the feeling that if I can get past this step I'll be over the hill with this issue.

---

### Post by bodhi.zazen on 2008-07-17
If you are using samba, wait a few minutes it may take a while to see your new shares.

If that fails, what kind of networking are you using ? Bridged or NAT ?

Use bridged ... you may need to re-boot your guest if you are using NAT.

Otherwise see the link I gave you.

---

### Post by dpj23 on 2008-07-17
did you turn on file sharing between host and quest 

vm-> settings-> options -> enable file sharing???

---

### Post by beaver29 on 2008-09-05
i agree that samba is the best way to transfer files if you can get it working.  one other option that i have used is the swiss file knife (SFK).  SFK is a really small utility with lots of functionality including an ftp server.  assuming your guest has network access, you can install SFK on host and guest, and ftp files back and forth.  this method is not as convenient as using a samba server.  if you're moving a lot of files at once, it's a pain.  you pretty much have to pack them in a zip archive so you can just move one file.  but the main advantage of this method is it's really easy to set it up.  if samba isn't "just working out of the box", it's nice to have another option until you get samba working.  this link explains the details:

[http://stahlforce.com/dev/index.php?tool=vmftp]("http://stahlforce.com/dev/index.php?tool=vmftp")

---

