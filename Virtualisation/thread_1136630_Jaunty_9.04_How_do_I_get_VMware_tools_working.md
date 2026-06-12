---
title: "Jaunty 9.04: How do I get VMware tools working?"
date: 2009-04-25
forum: Virtualisation
---

### Post by Panarchy on 2009-04-25
Hello

Followed the tutorial ([https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)) even tried installing openvm-tools through package manager.

Yet even though I can now launch vmware-toolbox, Ubuntu still doesn't seem to have the capability to automatically resize with the size of the window (vista x64).

Any ideas on how I can get VMware Tools working properly?

Thanks in advance,

Panarchy

---

### Post by dpj23 on 2009-04-25
I ran the install script using the administrator account.  So, I log-in as root selected install vmtools...  selected run in terminal and they installed...  (P.S...  you might to leave the .iso as the CD drive since it might look for the C compiler...)



Now, I will say that it has been a pain in the past to install vmtools in linux quests.  This time it was just like you think it should be...

---

### Post by norreman on 2009-04-27
Try to follow this howto, it has worked for me! After I dist-upgraded from 8.10 to 9.04 I had to repeat the steps.

[http://cccarey.wordpress.com/howtos/howto-install-vmware-tools-on-ubuntu-810-intrepid/](http://cccarey.wordpress.com/howtos/howto-install-vmware-tools-on-ubuntu-810-intrepid/)

- compile and install the latest uriparser (0.7.3) 
- compile the latest open-vm-tools ( 2009.03.18-154848 ) 
- bundle the compilation output and overlay the versions provided by VMWare
- sudo ./vmware-install.pl

---

### Post by Zoide7777 on 2009-04-27
I tried installing VMWare Tools from the official Ubuntu repository by following the procedure here ([http://www.gorillapond.com/2009/03/09/install-vmware-tools-on-ubuntu-linux-reborn](http://www.gorillapond.com/2009/03/09/install-vmware-tools-on-ubuntu-linux-reborn)).

I tried running module-assistant auto-install open-vm but it fails when building the first module. Here is some of the output:

â /usr/src/modules/open-vm/modules/linux/vmhgfs/kernelStubsLinux.o â
â CC [M] /usr/src/modules/open-vm/modules/linux/vmhgfs/link.o â
â CC [M] /usr/src/modules/open-vm/modules/linux/vmhgfs/messageBackdoor.o â
â CC [M] /usr/src/modules/open-vm/modules/linux/vmhgfs/message.o â
â CC [M] /usr/src/modules/open-vm/modules/linux/vmhgfs/module.o â
â CC [M] /usr/src/modules/open-vm/modules/linux/vmhgfs/page.o â
â /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:88: error: unknown â
â field âprepare_writeâ specified in initializer â
â /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:88: warning: â
â initialization from incompatible pointer type â®
â /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:89: error: unknown â
â field âcommit_writeâ specified in initializer â
â /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:89: warning: â
â initialization from incompatible pointer type â
â make[5]: *** [/usr/src/modules/open-vm/modules/linux/vmhgfs/page.o] â
â Error 1 â
â make[4]: *** [_module_/usr/src/modules/open-vm/modules/linux/vmhgfs] â
â Error 2 â
â make[4]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic’ â
â make[3]: *** [vmhgfs.ko] Error 2 â
â make[3]: Leaving directory â
â `/usr/src/modules/open-vm/modules/linux/vmhgfs’ â
â make[2]: *** [build] Error 2 â®
â make[2]: Leaving directory `/usr/src/modules/open-vm’ â
â make[1]: *** [binary-modules] Error 2 â
â make[1]: Leaving directory `/usr/src/modules/open-vm’ â®
â make: *** [kdist_build] Error 2 â

---

### Post by tchoklat on 2009-04-27
Stuffed if I can get this to work. I am trying to install tools in 9.04 on a PCLOS host using VMWare work ststion. this is the output;

tony@ubuntu:~/Desktop/vmware-tools-distrib$ sudo ./vmware-install.pl -d
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmxnet
vmblock
vmmemctl
vmci

I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted

help needed!

Tony

---

### Post by tchoklat on 2009-04-27
Right,

Got the tools installed but no mouse-integration, see my post here - "http://ubuntuforums.org/showthread.php?t=1120414&page3"


> **tchoklat said:**
> Stuffed if I can get this to work. I am trying to install tools in 9.04 on a PCLOS host using VMWare work ststion. this is the output;

tony@ubuntu:~/Desktop/vmware-tools-distrib$ sudo ./vmware-install.pl -d
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmxnet
vmblock
vmmemctl
vmci

I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted

help needed!

Tony

---

### Post by bhaverkamp on 2009-04-28
Installing the following two packages yields a perfectly working ubuntu 9.04 VM on WS 6.5.2. You can blow off the tools install step from workstation and just run this command in your guest.

sudo apt-get install xserver-xorg-input-vmmouse open-vm-tools

---

### Post by benz08 on 2009-04-28
Did you find this enabled drag and drop and screen resizing too? 

I've just done this and the mouse is now working fine, but thats all.

---

### Post by bhaverkamp on 2009-04-28
Yup, screen resizing is working too! I did not have the tools from workstation installed because it kept bailing with 'drivers already installed' messages. I installed the vmmouse driver first and then tools if that makes any difference.

---

### Post by flotux on 2009-04-29
Hi,

I get the same error message as Zoide7777 if I run the following command: 
**[FONT=Courier New]module-assistant auto-install open-vm[/FONT]**

[I][...]
/usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:88: error: unknown field prepare_write specified in initializer
[...][/I]

I've upgraded Ubuntu from 8.10 to 9.04 - maybe a issue of that?

Regards
Flo

---

### Post by Anicka on 2009-04-30
There is a fix to make the vmhgfs-module working. This is all described here: [http://laptopbisnis.blogspot.com/2009/04/ubuntu-904-beta-in-vmware-fusion.html](http://laptopbisnis.blogspot.com/2009/04/ubuntu-904-beta-in-vmware-fusion.html)

The page is originally for fusion-users, but it works also for Workstation 6.5.2 (that's what I'm using). You have to extract the vmghfs-only folder and edit the page.c file as described. After re-taring the whole thing you run the install script. If you get an error message saying something about having to delete some files, do it. In my case it's: ```
sudo rm /lib/modules/2.6.28-11-generic/misc/vm*
```After that you can run the installer without problems and all the modules build and work.

---

### Post by Zoide7777 on 2009-04-30
Thanks Anicka, but apparently the fix is only for the version of VMWare tools that gets copied over when you try to install it from VMWare.  The open-vm source from the Ubuntu 9.04 repository does not have the line that they tell you to modify in the link.

In my case, the relevant sections in /modules/open-vm/modules/linux/vmhgfs/page.c (contained within /usr/src/open-vm.tar.bz2):

[Lines 84-92]

/* HGFS address space operations structure. */
struct address_space_operations HgfsAddressSpaceOperations = {
   .readpage      = HgfsReadpage,
   .writepage     = HgfsWritepage,
[B]   .prepare_write = HgfsPrepareWrite,
   .commit_write  = HgfsCommitWrite,[/B]
#ifdef HGFS_ENABLE_WRITEBACK
   .set_page_dirty = __set_page_dirty_nobuffers,
#endif

The errors were:

 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:88: error: unknown
 field "prepare_write" specified in initializer 
 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:88: warning: 
 initialization from incompatible pointer type 
 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:89: error: unknown 
 field "commit_write" specified in initializer 
 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:89: warning: 
 initialization from incompatible pointer type

---

### Post by korey_sed on 2009-04-30
I was having the same mouse issue where the xorg driver was installed, but the mouse was still captured in vmware. I tried open-vm tools and reinstalling the xorg drivers, but nothing worked. finally I found this and it seems to work for me. Look at the xorg.conf section and comment out the extra lines in yours.
  [http://digfor.blogspot.com/2009/04/ubuntu-904-guest-in-vmware-sluggish.html](http://digfor.blogspot.com/2009/04/ubuntu-904-guest-in-vmware-sluggish.html)

---

### Post by stlsaint on 2009-05-01
PLEASE HELP.....I have the same issue...i am running jaunty on a VMware workstation behind vista home pre. I have the vmware package mounted inside my jaunty station but as i run sudo commands i continue to get this error no matter what i try.....


"faint@Faints-Ubuntu-VM:~/vmtools/vmware-tools-distrib$ sudo apt-get install vmware-installer.pl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware
faint@Faints-Ubuntu-VM:~/vmtools/vmware-tools-distrib$"

PLEASE TELL ME WHAT I AM DOING WRONG!!!!

---

### Post by Anicka on 2009-05-01
> **stlsaint said:**
> PLEASE HELP.....I have the same issue...i am running jaunty on a VMware workstation behind vista home pre. I have the vmware package mounted inside my jaunty station but as i run sudo commands i continue to get this error no matter what i try.....


"faint@Faints-Ubuntu-VM:~/vmtools/vmware-tools-distrib$ sudo apt-get install vmware-installer.pl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware
faint@Faints-Ubuntu-VM:~/vmtools/vmware-tools-distrib$"

PLEASE TELL ME WHAT I AM DOING WRONG!!!!

The installer script doesn't use apt-get. The correct command is "sudo ./vmware-install.pl"
Make sure that you have installed the package build-essential (that you install as normal with apt-get) before running the vmware installer.

---

### Post by Anicka on 2009-05-01
> **Zoide7777 said:**
> Thanks Anicka, but apparently the fix is only for the version of VMWare tools that gets copied over when you try to install it from VMWare.  The open-vm source from the Ubuntu 9.04 repository does not have the line that they tell you to modify in the link.

In my case, the relevant sections in /modules/open-vm/modules/linux/vmhgfs/page.c (contained within /usr/src/open-vm.tar.bz2):

[Lines 84-92]

/* HGFS address space operations structure. */
struct address_space_operations HgfsAddressSpaceOperations = {
   .readpage      = HgfsReadpage,
   .writepage     = HgfsWritepage,
[B]   .prepare_write = HgfsPrepareWrite,
   .commit_write  = HgfsCommitWrite,[/B]
#ifdef HGFS_ENABLE_WRITEBACK
   .set_page_dirty = __set_page_dirty_nobuffers,
#endif

The errors were:

 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:88: error: unknown
 field "prepare_write" specified in initializer 
 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:88: warning: 
 initialization from incompatible pointer type 
 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:89: error: unknown 
 field "commit_write" specified in initializer 
 /usr/src/modules/open-vm/modules/linux/vmhgfs/page.c:89: warning: 
 initialization from incompatible pointer type

Sorry for not being clear on that. I'm not using the open-vm, so I haven't looked for any fix on that. However, I saw that there are a couple of bug reports with open-vm and the kernel 2.6.28.

---

### Post by Robert B on 2009-05-15
I found this website useful regarding this issue: [http://chrysaor.info/?page=faq#ubuntu904_tools](http://chrysaor.info/?page=faq#ubuntu904_tools). It offers a script that does the installation automatically. Even shared folders (using the hgfs module) works.

---

### Post by Zoide7777 on 2009-05-15
> **Robert B said:**
> I found this website useful regarding this issue: [http://chrysaor.info/?page=faq#ubuntu904_tools](http://chrysaor.info/?page=faq#ubuntu904_tools). It offers a script that does the installation automatically. Even shared folders (using the hgfs module) works.

Thanks so much!  That worked perfectly.

---

### Post by ravenrd on 2009-05-17
I had the same problem as outlined in this thread and I could not get it to work with the VMWare tools for VMWare Workstation 6.03 or Workstation 6.5.1. I also tried using the open version of the tools, but it gave the same problems.

I was not thrilled about downloading a script from an unknown site and plug it into my kernel, but I ran out of ideas. I looked through the script and the only fishy thing is that it downloads a precooked VMWare tools for Ubuntu 9.04 from this website so any modifications could have been made in the code. It solved all my problems, but I feel a bit uncomfortable with this. Does anyone
know what changes have been made to the code and if it is safe?

---

### Post by Panarchy on 2009-06-05
Thanks for that script... was what I was looking for

[img]http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif[/img]

---

### Post by etbonick on 2009-08-27
> **korey_sed said:**
> I was having the same mouse issue where the xorg driver was installed, but the mouse was still captured in vmware. I tried open-vm tools and reinstalling the xorg drivers, but nothing worked. finally I found this and it seems to work for me. Look at the xorg.conf section and comment out the extra lines in yours.
  [http://digfor.blogspot.com/2009/04/ubuntu-904-guest-in-vmware-sluggish.html](http://digfor.blogspot.com/2009/04/ubuntu-904-guest-in-vmware-sluggish.html)

That link no longer works. What exactly did you comment out?

---

### Post by mobious on 2009-09-07
Here's what I do an so far it's worked every time..

sudo aptitude update
sudo aptitude install build-essential linux-headers-$(uname -r)
cd /cdrom
cp -a /media/cdrom/VMwareTools* /tmp/
cd /tmp/
tar -vxzf VMwareTools*.gz
cd vmware-tools-distrib/
sudo ./vmware-install.pl

tested on 7.04, 8.04, 8.10 (was kinda buggy), and now 9.01, and 9.04

---

