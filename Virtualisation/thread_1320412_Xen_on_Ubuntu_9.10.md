---
title: "Xen on Ubuntu 9.10"
date: 2009-11-09
forum: Virtualisation
---

### Post by Debug26 on 2009-11-09
Does Ubuntu 9.10 Karmic support XEN ?
 
# uname -a
Linux host 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 
# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
 
Anybody installed XEN on Ubuntu 9.10 ?

---

### Post by eqx311 on 2009-11-09
> **Debug26 said:**
> Does Ubuntu 9.10 Karmic support XEN ?
 
# uname -a
Linux host 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 
# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
 
Anybody installed XEN on Ubuntu 9.10 ?

I'm trying and it still doesn't work...
linux-2.6-xen (2.6.35.5)
xen-3.4 (xen-3.4-testing.hg)

following this blog post:
[http://www.itkovian.net/base/xen_hypervisor_with_ubuntu_karmic_koala](http://www.itkovian.net/base/xen_hypervisor_with_ubuntu_karmic_koala)

does anyone of you guys has luck with this ?

---

### Post by shoutrain on 2009-11-09
> **Debug26 said:**
> Does Ubuntu 9.10 Karmic support XEN ?
 
# uname -a
Linux host 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 
# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
 
Anybody installed XEN on Ubuntu 9.10 ?

after installed ubuntu-xen-desktop, i got 2.6.31-14-generic-pae too, but xen can not work, and when i excute "xm list", i got messages below:

=================messages start===================
ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in <module>
    from xen.xm import main
  File "/usr/lib/python2.6/dist-packages/xen/xm/main.py", line 61, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')
==================messges end==================

refered these messages to google, i found many people met the same situation, but no clear solution.  some people said maybe cpu does not support fully virtualization, just support pae.

---

### Post by tapas_mishra on 2009-11-10
I m not trying Ubuntu 9.10 but 9.04 
from past one week and have not yet been able to boot successfully from the xen kernel 
I will tell the steps that I did 
and check these links which are giving some information as they might be useful on the forum
[http://www.infohit.net/blog/post/compiling-a-xen-dom0-kernel-for-ubuntu-jaunty.html](http://www.infohit.net/blog/post/compiling-a-xen-dom0-kernel-for-ubuntu-jaunty.html)
what they suggested is to use Debian Kernels as Ubuntu does not support Xen
I got this some where on net do  not remember exactly and no idea wether it is right or wrong
then this is the users manual 
[http://tx.downloads.xensource.com/downloads/docs/user/#SECTION01140000000000000000](http://tx.downloads.xensource.com/downloads/docs/user/#SECTION01140000000000000000)
which says the libraries needed to install Xen 
may be archives here help you 
[http://mulps.wordpress.com/2009/05/29/compiling-xen-kernel-2-6-29-2/](http://mulps.wordpress.com/2009/05/29/compiling-xen-kernel-2-6-29-2/)
and also this one
[http://bderzhavets.wordpress.com/2009/01/03/setup-xen-330-ubuntu-intrepid-server-dom0-via-build-xen-kernel-based-on-httpxenbitsxensourcecomextlinux-2627-xenhg/](http://bderzhavets.wordpress.com/2009/01/03/setup-xen-330-ubuntu-intrepid-server-dom0-via-build-xen-kernel-based-on-httpxenbitsxensourcecomextlinux-2627-xenhg/)


On this page there seems to be some solution 
as they mentioned 

[http://bderzhavets.wordpress.com/2009/06/25/setup-xen-3-4-1-dom0-on-top-of-ubuntu-9-04-server-via-marc-a-dahlhauss-udev-patch/](http://bderzhavets.wordpress.com/2009/06/25/setup-xen-3-4-1-dom0-on-top-of-ubuntu-9-04-server-via-marc-a-dahlhauss-udev-patch/)
that 

> Different option is to install xenified kernel 2.6.30.2 via download :-
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.30.2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.30.2.tar.bz2)
and applying Andrew Lyon’s rebased patches set

# wget [http://gentoo-xen-kernel.googlecode.com/files/xen-patches-2.6.30-3.tar.bz2](http://gentoo-xen-kernel.googlecode.com/files/xen-patches-2.6.30-3.tar.bz2)


also it mentiones that there has been an update in git source


> 
************************************************************
Updated on 10/05/09 due to changes in JF’s Git Repo
************************************************************
Install pvops enabled kernel 2.6.31.1  from Jeremy Fitzhardinge git repository. Checkout the most recent branch:-

# git clone git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-xen
# cd linux-2.6-xen

So hope this helps you.If you get it working then do post here so that we benefit.

---

### Post by nilgiri on 2009-11-10
Any one try upgrading from an 8.04 xen setup to 9.04?  How about to 9.10 after that?  I know you won't get the latest kernel, but would everything else go and still work with the older xen-kernel from hardy?  Personally, I'm interested in newer versions of mdadm so my RAID does not freak out when booting.

---

### Post by nevilarus on 2009-11-10
I'm using Xen on Ubuntu 9.04. 
I want to make a clone of my computer then run it on Xen. I tried using dd but it didn't work. So anyone can help me ?

Thanks.
P/S: Sorry , I'm new here. And I don't know where to post :confused:

---

### Post by tapas_mishra on 2009-11-10
> **nevilarus said:**
> I'm using Xen on Ubuntu 9.04. 
I want to make a clone of my computer then run it on Xen. I tried using dd but it didn't work. So anyone can help me ?

Thanks.
P/S: Sorry , I'm new here. And I don't know where to post :confused:
Hi nevilarus
even if you came here by chance please do post how did you got Xen running on Ubuntu 9.04 I am trying this from a long time as it is clear in my above messages any help would be appreciable what did you put in your .config file when you compiled Xen kernel the steps you did 

I am myself a newbie for Xen but you may have a look at the following link
[http://gmane.org/](http://gmane.org/)
they have a list of users and developers where you can find the questions.

---

### Post by tapas_mishra on 2009-11-10
I have got some more information on internet for compiling this kernel Xen which I am searching I am posting it here if some one has done the similar as mentioned then do inform here in this thread the results

These instructions are for AMD machine so please make sure you dont mess up with the things 
==============================================================
It is  about the procedure for compiling vanilla kernel from source and customize it according to your hardware specifications and then compiling latest XEN from source and patching it with Linux.
First install these packages:
 
 sudo apt-get install iproute  bridge-utils  gcc make  gettext
 sudo apt-get install libcurl4-openssl-dev è openssl problem resolved
 sudo apt-get install python-dev zlib1g-dev bcc libsdl-dev pciutils-dev è zlib problem resolved.
  
     First we will compile latest XEN Hypervisor from source.
 
 Go to [http://www.xen.org/products/xen_source.html](http://www.xen.org/products/xen_source.html) and download the latest XEN hypervisor from there. [Version 3.4.1 at the time of writing the guide]
 Xen 3.4.1 is available WITH and WITHOUT 2.6.18 dom0 kernel. We need the version without dom0 linux because we will compile our own vanilla kernel.
I am seting up XEN 3.4.1 on amd64 hardware and running debian distribution on it with upgraded kernel.
My hardware specifications:
unme -a
Linux hactar-04 2.6.31.4-user-kvm-vanilla #1 SMP Wed Oct 21 16:35:11 BST 2009 x86_64 GNU/Linux
 **Build / Install Xen**
 
[LIST=1]
[*]mkdir /home/user/xen
[*]cd /home/user/xen
[*]tar -xzf xen-3.4.1
[*]cd xen-3.4.1
[*]make xen
[*]make install-xen
[*]make tools
[*]make install-tools
[/LIST]
  [B]Build Vanilla kernel
[/B]
Now we will build th PV_Ops Kernel. The Vanilla kernel source will be downloaded from Jeremy's tree. Jeremy's git tree on [kernel.org]("http://kernel.org/") contains the pv_ops dom0 patches. If we use Jeremy's tree then we do not any extra patches to bind XEN with kernel source.
  
[LIST=1]
[*]mkdir /home/user/linux
[*]cd /home/user/linux
[*]git clone git://[URL="http://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.gitlinux-2.6-xen"]git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git
     [/URL]
[*][ linux-2.6-xen]("http://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.gitlinux-2.6-xen")
[*]cd linux-2.6-xen
[*]git checkout origin/xen/master -b xen/master
[*] make menuconfig  [see Note below]
[*]make-kpkg clean
[*]CONCURRENCY_LEVEL=N fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
[*]This will make the debian packages in the parent directory which you can install
[/LIST]
 **[B]Note:** Please choose the following xen specific optiions in kernel configuration.[/B]

  
Processor type and features ---> Subarchitecture Type (PC-compatible) ---> (X) Enable Xen compatible kernel
Bus options (PCI etc.)  ---> 
[*] PCI support
                                           
[*]   Xen PCI Frontend
                                            [ ]     Xen PCI Frontend Debugging (NEW)
Device Drivers  ---> XEN  ---> 
[*] Privileged Guest (domain 0)
                                             <*> Backend driver support (NEW)
                                             <*>   Block-device backend driver (NEW)
                                             <*>   Block-device tap backend driver (NEW)
                                              <*>   Network-device backend driver (NEW)
                                               (8)     Maximum simultaneous transmit requests (as a power of 2) (NEW)
                                                [ ]     Pipelined transmitter (DANGEROUS) (NEW)
                                               < >     Network-device loopback driver (NEW)
                                               <*>   PCI-device backend driver (NEW)
                                                        PCI Backend Mode (Virtual PCI)  --->
                                                         [ ]     PCI Backend Debugging (NEW)
                                                          < >   TPM-device backend driver (NEW)
                               <M>   SCSI backend driver (NEW)
                               <M> Block-device frontend driver
                               <M> Network-device frontend driver
                               <M>   Network-device frontend driver acceleration for Solarflare NICs (NEW)
                               <M> SCSI frontend driver (NEW)
                               <*> User-space granted page access driver (NEW)
                               <*> Framebuffer-device frontend driver (NEW)
                               <*>   Keyboard-device frontend driver (NEW)
                               
[*] Disable serial port drivers (NEW)
                               <*> Export Xen attributes in sysfs (NEW)
                               (256) Number of guest devices (NEW)
                                   Xen version compatibility (3.0.4 and later)  --->
 
After xen confiuration, please make sure that .config has the following parameter configuration:
 
[LIST]
[*]CONFIG_XEN=y
[*]CONFIG_XEN_MAX_DOMAIN_MEMORY=32
[*]CONFIG_XEN_SAVE_RESTORE=y
[*]CONFIG_XEN_DOM0=y
[*]CONFIG_XEN_PRIVILEGED_GUEST=y
[*]CONFIG_XEN_PCI=y
[*]CONFIG_PCI_XEN=y
[*]CONFIG_XEN_BLKDEV_FRONTEND=m
[*]CONFIG_NETXEN_NIC=m
[*]CONFIG_XEN_NETDEV_FRONTEND=m
[*]CONFIG_XEN_KBDDEV_FRONTEND=m
[*]CONFIG_HVC_XEN=y
[*]CONFIG_XEN_FBDEV_FRONTEND=m
[*]CONFIG_XEN_BALLOON=y
[*]CONFIG_XEN_SCRUB_PAGES=y
[*]CONFIG_XEN_DEV_EVTCHN=y
[*]CONFIG_XEN_BACKEND=y
[*]CONFIG_XEN_BLKDEV_BACKEND=y
[*]CONFIG_XEN_NETDEV_BACKEND=y
[*]CONFIG_XENFS=y
[*]CONFIG_XEN_COMPAT_XENFS=y
[*]CONFIG_XEN_XENBUS_FRONTEND=m
[/LIST]
  
Install these debian packages using
sudo dpkg -i <name>
Add the following line to /etc/fstab
 none /proc/xen xenfs defaults 0 0
and reboot the machine.
 
After installing the debian packages, the Grub Entry will look like the following:
title             Xen 3.4.1 / Debian GNU/Linux, kernel 2.6.31.4-user-xen-4
root             (hd0,0)
kernel          /boot/xen-3.4.1.gz
module          /boot/vmlinuz-2.6.31.4-user-xen-4 root=/dev/sda1 ro console=tty0
module          /boot/initrd.img-2.6.31.4-user-xen-4

---

### Post by nevilarus on 2009-11-10
> **tapas_mishra said:**
> Hi nevilarus
even if you came here by chance please do post how did you got Xen running on Ubuntu 9.04 I am trying this from a long time as it is clear in my above messages any help would be appreciable what did you put in your .config file when you compiled Xen kernel the steps you did 

I am myself a newbie for Xen but you may have a look at the following link
[http://gmane.org/](http://gmane.org/)
they have a list of users and developers where you can find the questions.

Thanks.
I think I'm just lucky . After install xen using "apt-get install" , I suffered the same errors like these (posted above)
> =================messages start===================
ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in <module>
    from xen.xm import main
  File "/usr/lib/python2.6/dist-packages/xen/xm/main.py", line 61, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')
==================messges end==================There are many pages on the internet discuss about this error. Compiling the Xen kernel is one way , but in fact , I don't know what it means. Because I'm noob :p
When I thought I should give up and switch to another distro, I found a Xen kernel package upload by s.o. I gave it a try , and surprisingly , It ran smoothly !
That's all. I'm still asking myself " Is it just that simple ?" :-k

---

### Post by sdowney717 on 2009-11-11
hi, where is the "xen kernel" package by s.o.
thanks, i might want to try out xen

---

### Post by tapas_mishra on 2009-11-12
> **sdowney717 said:**
> hi, where is the "xen kernel" package by s.o.
thanks, i might want to try out xen
I have finally got some luck in trying over Xen there are supported Operating System and some Operating Systems do not support 
I had been googling since I was getting a lot of errors as I had tried to install Xen or say compile a Dom0 kernel on it from jeremy repository on the unsupported OS,
and since from my post it is absolutely clear that I am a novice as far as Xen is concerned 
I came across a good book about XEN 
A hands on guide to the art of virtualization Jeanna Mathews
[http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3](http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3)

I am posting the above link so that if some one like me is searching for a lot of basic questions among documentations etc does not get confused by the blogs on internet everything available for free does not leads to the right solution.But still it has a lot of support on the community and a good place to ask questionbs is [http://gmane.org]("http://gmane.org/") the mailing list about xen users it is here 
[http://lists.xensource.com/xen-users](http://lists.xensource.com/xen-users)

A relevant thing to search on internet will be 
CONFIG_XEN_PCI
CONFIG_NETXEN_NIC
Initially they appear to be jargons but if you keep googling and reading you will answers.
See the discussion on the thread where I have replied 
on this page [http://ubuntuforums.org/showthread.php?t=1323407](http://ubuntuforums.org/showthread.php?t=1323407) abbout which Operating Systems are supported right now and which not
I hope this helps to a lot of people like me for whom Linux is a Hobby and they want to try Xen.

---

### Post by amateo on 2009-11-23
Hello,

  I'm trying to follow the howto posted by tapas_mishra. I can build and install xen, but I can't build a vanilla kernel. In step 6 I get:

amateo@felis117:~$ git checkout origin/xen/master -b xen/master
fatal: git checkout: branch xen/master already exists

  You also talk about a kernel package developed by s.o., where can I download it?

---

### Post by foamz on 2009-11-25
> **nevilarus said:**
> Thanks.
I think I'm just lucky . After install xen using "apt-get install" , I suffered the same errors like these (posted above)
There are many pages on the internet discuss about this error. Compiling the Xen kernel is one way , but in fact , I don't know what it means. Because I'm noob :p
When I thought I should give up and switch to another distro, I found a Xen kernel package upload by s.o. I gave it a try , and surprisingly , It ran smoothly !
That's all. I'm still asking myself " Is it just that simple ?" :-k

That error means you are not using the xen kernel. If you do "uname -r" you can see which kernel you are using.

Whats this package you talk about 'uploaded by s.o." ?

---

