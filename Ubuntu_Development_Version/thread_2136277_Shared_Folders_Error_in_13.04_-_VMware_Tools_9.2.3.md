---
title: "Shared Folders Error in 13.04 - VMware Tools 9.2.3 - vmhgfs problem"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by Ub11 on 2013-04-17
After installing VMware Tools without a problem, when I run the vmware-config-tools.pl script there is an error when trying to build/load the vmhgfs driver. The gcc, binutils and make modules are installed.  (See error messages below.)

Since the driver is not loaded, the Shared Folders option does not work.  Any ideas how to solve this problem?

(There are no problems when running Ubuntu 12.04 or 12.10 in the same setup of Vmplayer 5.02  with Vmware Tools 9.2.3.)

System Info:
Windows 7 host, Ubuntu 13.04 32 bit Guest - Daily build: 16 April 2013, VMware Tools 9.2.3


```
/tmp/modconfig-5e6o62/vmhgfs-only/inode.c: In function &#8216;HgfsTruncatePages&#8217;:
/tmp/modconfig-5e6o62/vmhgfs-only/inode.c:888:4: error: implicit declaration of function &#8216;vmtruncate&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/tmp/modconfig-5e6o62/vmhgfs-only/inode.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [_module_/tmp/modconfig-5e6o62/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-18-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/modconfig-5e6o62/vmhgfs-only'

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 
```

---

### Post by dino99 on 2013-04-17
sudo apt-get install linux-source

---

### Post by Ub11 on 2013-04-17
Thanks for the advice to run the command:   sudo apt-get install linux-source

 I have tried it, but it did not work first time, the error is still present.

Next week I shall do all the updates and try again: This is after all only a Daily Build and therefore a work in progress.

---

### Post by ONEoo7 on 2013-04-25
Same error. Also tried the command to install linux-source and the error is still there.

System info:
Windows 8 64-bit host, ubuntu 13.04 64-bit 25.april.2013 release and vmware workstation 9.0.2.

---

### Post by bgcngm on 2013-04-26
> **ONEoo7 said:**
> System info:
Windows 8 64-bit host, ubuntu 13.04 64-bit 25.april.2013 release and vmware workstation 9.0.2.
Same environment, same error. Let's hope for a fix to come out soon.

---

### Post by dino99 on 2013-04-26
Maybe its a missing driver builtin the kernel; in such a case file a report : ubuntu-bug linux

[http://www.linuxquestions.org/questions/linux-software-2/command-to-know-the-list-of-drivers-installed-on-my-linux-system-948384/](http://www.linuxquestions.org/questions/linux-software-2/command-to-know-the-list-of-drivers-installed-on-my-linux-system-948384/)

---

### Post by bgcngm on 2013-04-27
Just found an alternative to be able to mount shared folders:

```
sudo apt-get install open-vm-tools
sudo mount -t vmhgfs .host:/ /mnt/hgfs
```

---

### Post by ONEoo7 on 2013-04-27
It works @bgcngm. Thanks :)

---

### Post by bgcngm on 2013-04-27
I was now trying to edit fstab to get it mounted on boot. Already tried adding the following line to /etc/fstab, but no luck:

```
.host:/ /mnt/hgfs vmhgfs defaults 0 0
```

---

### Post by Aox on 2013-04-28
I just wanted to chime in and confirm the problem.  About a day after 13.04 released, I upgraded my Kubuntu vmware guest from 12.10 to 13.04.  When installing tools using the tar installer, the vmhgfs module refuses to build.  The error is identical to what is mentioned above.

A full text of the install process is [here]("http://pastebin.com/wE3L4Vxe").

I've also posted this question in [VMWare forums]("http://communities.vmware.com/message/2233814#2233814"), and [Kubuntu forums]("http://www.kubuntuforums.net/showthread.php?62571-After-13-04-upgrade-I-m-unable-to-build-vmhgfs-module-vmware-tools&p=327266#post327266").  I assume this is the result of changes to the kernel, and that a fix would have to come from VMWare, so that's where I started.  I haven't gotten any response in 3 days though.  I would have expected more people to be affected by this.

I considered switching to openvm-tools...but I was concerned that the filesharing functions might not be present..or might just be weird.  I would prefer to use the vmware UI to adjust share settings and have it auto mount without having to mess with fstab myself.  I also do not want to install the drag and drop file copying thing..as it is a big steaming pile of crud.  On the brief occasion I did have it active, I would accidentally drag an icon over the vm windows and have to sit and wait for several minutes while it "prepared to copy", which from what I can tell...it basically transfers the file at this time.  Only after the long wait can i decline to copy/move.

As you can see in the text I provided..all the required components are installed, including gcc, make, binutils, and current kernel headers.  All of them are detected properly.  All the other components seems to build successfully, except vmhgfs.

---

### Post by Ub11 on 2013-04-30
> **Aox said:**
> I just wanted to chime in and confirm the problem.  About a day after 13.04 released, I upgraded my Kubuntu vmware guest from 12.10 to 13.04.  When installing tools using the tar installer, the vmhgfs module refuses to build.  The error is identical to what is mentioned above.


Thank you to all who have responded. Although I was fairly silent lately, I have regularly checked your responses.

Now we know it is a confirmed problem, experienced by a number of users on different systems, not a small local problem or just a simple user error.

Although open-vm-tools can be made to work, I would also prefer to wait for a vmware-tools update or a white knight (expert) that can work it all out and then tell us how to solve the problem !

---

### Post by dino99 on 2013-04-30
> **Ub11 said:**
> Thank you to all who have responded. Although I was fairly silent lately, I have regularly checked your responses.

Now we know it is a confirmed problem, experienced by a number of users on different systems, not a small local problem or just a simple user error.

Although open-vm-tools can be made to work, I would also prefer to wait for a vmware-tools update or a white knight (expert) that can work it all out and then tell us how to solve the problem !

To get something cleanly fixed, all you need to do is reported that issue (if not yet done) and add as much details as you can.

---

### Post by Ub11 on 2013-04-30
> **dino99 said:**
> To get something cleanly fixed, all you need to do is reported that issue (if not yet done) and add as much details as you can.

User Aox stated in Post #10 above that a question about the problem has already been posted to the Vmware forum and the Kubuntu forum. Also, I was hesitant to post this as a bug since this is not really a normal Ubuntu bug: It is a case of Vmware Player and Vmware Tools that did not work with the new Ubuntu.

This problem was eventually filed earlier today as Bug #1174752 on Launchpad. After about an hour I checked again and discovered that the bug I filed was declared "Invalid" and changed into Question #227866.

Now I can only wait for a solution.


However, after filing the bug, a more detailed search in Launchpad discovered Bug #992029, which is similar to the current problem, although it was filed against Ubuntu 12.04, exactly one year ago. Below is a short quote from the bug:
>  I am running Ubuntu 12.04 as a guest OS on my Win 7 host. While  installing the vmware tools the vmhgfs module fails to compile and  therefore the modprobe vmhgfs fails and hence no shared folder works. 

The bug was later confirmed, but the problem remains unassigned and unsolved to this day.

---

### Post by ryven on 2013-04-30
Same problem here. Currently using a shared network drive to work around the problem, but not ideal : /

---

### Post by krobertson on 2013-05-02
Encountered this tonight as well and think I have worked through it.  It is an issue in the vmware tools, where is is incompatible with the 3.8.0 kernel.  Managed to find some patches and general help from here: [http://erikbryantology.blogspot.com/2013/03/patching-vmware-tools-in-fedora-18.html](http://erikbryantology.blogspot.com/2013/03/patching-vmware-tools-in-fedora-18.html).  Also had an issue with the install script locating some headers, so had to create a few symlinks to make it happy.

My install process was as follows:

```

apt-get -y install linux-headers-$(uname -r) build-essential

cd /lib/modules/$(uname -r)/build/include/linux
sudo ln -s ../generated/utsrelease.h
sudo ln -s ../generated/autoconf.h
sudo ln -s ../generated/uapi/linux/version.h

mount /dev/cdrom /mnt/cdrom
cd /tmp

tar zxvf /mnt/cdrom/VMwareTools-*.tar.gz
cd vmware-tools-distrib
wget https://github.com/ebdevrepo/bin/raw/master/vmware9.compat_mm.patch
wget https://github.com/ebdevrepo/bin/raw/master/vmware9.k3.8rc4.patch
wget https://github.com/ebdevrepo/bin/raw/master/vmware_hgfs_fix.sh
wget https://github.com/ebdevrepo/bin/raw/master/vmware_vmci_fix.sh
chmod a+x *.sh
./vmware_hgfs_fix.sh
./vmware_vmci_fix.sh
./vmware-install.pl -d

```

---

### Post by sarcangeli on 2013-05-02
Hi all,
I'm experiencing the same issue since the upgrade to Ubuntu 13.04, and after googling a bit I found the "white knight" solution.

Here is how they fixed it for Fedora (look at the VMHGFS paragraph in the page, it's bug number 3):
[http://erikbryantology.blogspot.it/2013/03/patching-vmware-tools-in-fedora-18.html](http://erikbryantology.blogspot.it/2013/03/patching-vmware-tools-in-fedora-18.html)

And here is what I did to apply the patch and get it working on Ubuntu.

I downloaded the patch ([https://raw.github.com/ebdevrepo/bin/master/vmware9.compat_mm.patch](https://raw.github.com/ebdevrepo/bin/master/vmware9.compat_mm.patch)) and the fix script ([https://raw.github.com/ebdevrepo/bin/master/vmware_hgfs_fix.sh](https://raw.github.com/ebdevrepo/bin/master/vmware_hgfs_fix.sh)).

I edited the fix script, replacing the line

```
pushd lib/modules/source
```

with 

```
pushd modules/source
```

then I copied the files to the VMWare tools distrib dir and executed the fix:

```
sudo cp vmware9.compat_mm.patch /usr/lib/vmware-tools
sudo cp vmware_hgfs_fix.sh /usr/lib/vmware-tools
cd /usr/lib/vmware-tools
sudo chmod ugo+x vmware_hgfs_fix.sh
sudo ./vmware_hgfs_fix.sh 

```

the output I had after the last command was:
```
/usr/lib/vmware-tools/modules/source /usr/lib/vmware-tools
/usr/lib/vmware-tools/modules/source/vmhgfs-only/shared /usr/lib/vmware-tools/modules/source /usr/lib/vmware-tools
patching file compat_mm.h
/usr/lib/vmware-tools/modules/source /usr/lib/vmware-tools
/usr/lib/vmware-tools
```

At this point, I executed again VMWare tools config 
```
sudo vmware-config-tools.pl
```

And this time the HGFS service compiled fine!

---

### Post by krobertson on 2013-05-02
Ha!  Two people post the same solution within a minute of each other. :)

---

### Post by sarcangeli on 2013-05-02
> **krobertson said:**
> Ha!  Two people post the same solution within a minute of each other. :)

Yes that was funny! I was glad to see we used the same patch, I wasn't doing something silly then. :)

---

### Post by Ub11 on 2013-05-02
> **krobertson said:**
> Encountered this tonight as well and think I have worked through it.  It is an issue in the vmware tools, where is is incompatible with the 3.8.0 kernel.  Managed to find some patches and general help from here: [http://erikbryantology.blogspot.com/2013/03/patching-vmware-tools-in-fedora-18.html](http://erikbryantology.blogspot.com/2013/03/patching-vmware-tools-in-fedora-18.html).  Also had an issue with the install script locating some headers, so had to create a few symlinks to make it happy.

My install process was as follows:

```

apt-get -y install linux-headers-$(uname -r) build-essential

cd /lib/modules/$(uname -r)/build/include/linux
sudo ln -s ../generated/utsrelease.h
sudo ln -s ../generated/autoconf.h
sudo ln -s ../generated/uapi/linux/version.h

mount /dev/cdrom /mnt/cdrom
cd /tmp

tar zxvf /mnt/cdrom/VMwareTools-*.tar.gz
cd vmware-tools-distrib
wget https://github.com/ebdevrepo/bin/raw/master/vmware9.compat_mm.patch
wget https://github.com/ebdevrepo/bin/raw/master/vmware9.k3.8rc4.patch
wget https://github.com/ebdevrepo/bin/raw/master/vmware_hgfs_fix.sh
wget https://github.com/ebdevrepo/bin/raw/master/vmware_vmci_fix.sh
chmod a+x *.sh
./vmware_hgfs_fix.sh
./vmware_vmci_fix.sh
./vmware-install.pl -d

```

Thanks to both krobertson and sarcangeli for posting a solution to this problem.

I started with the method outlined by krobertson (the first one posted) and I can confirm that the problem has been solved for me.

After verifying that vmhgfs has indeed compiled and installed correctly, the /mnt/hgfs folder was checked: The shared folder from the Windows 7 host system that had been set up earlier, was available and working fine for both reading and writing.

---

### Post by socket on 2013-05-02
A workaround for this problem is to edit 'inode.c' and change the line '888' to remove 'compat_truncate' function call (that is responsible for this problem on kernels 3.8.x). This file is inside 'vmware-tools-distrib', so you need to perform the following steps:

Extract VMWare-Tools (probably you will get a folder called vmware-tools-distrib).
Then:
> cd /vmware-tools-distrib/lib/modules/source
> tar xf vmhgfs.tar
> cd vmhgfs-only/
> sudo gedit inode.c
Go to line 888: result = compat_vmtruncate(inode, newSize);
And change it to: result = 0;
Then save the file and exit gedit.
> cd ..
> rm -rf vmhgfs.tar
> tar cf vmhgfs.tar vmhgfs-only/
> rm -rf vmhgfs-only/

Now restart the installing procedure. It worked for me in Xubuntu 13.04.

---

### Post by socket on 2013-05-02
> **socket said:**
> A workaround for this problem is to edit 'inode.c' and change the line '888' to remove 'compat_truncate' function call (that is responsible for this problem on kernels 3.8.x). This file is inside 'vmware-tools-distrib', so you need to perform the following steps:

Extract VMWare-Tools (probably you will get a folder called vmware-tools-distrib).
Then:
> cd /vmware-tools-distrib/lib/modules/source
> tar xf vmhgfs.tar
> cd vmhgfs-only/
> sudo gedit inode.c
Go to line 888: result = compat_vmtruncate(inode, newSize);
And change it to: result = 0;
Then save the file and exit gedit.
> cd ..
> rm -rf vmhgfs.tar
> tar cf vmhgfs.tar vmhgfs-only/
> rm -rf vmhgfs-only/

Now restart the installing procedure. It worked for me in Xubuntu 13.04.

I made a patch to simplify my workaround...

You just need to download these two files:
[https://dl.dropboxusercontent.com/u/16521384/vmhgfs-fix.sh](https://dl.dropboxusercontent.com/u/16521384/vmhgfs-fix.sh)
[https://dl.dropboxusercontent.com/u/16521384/vmtools.inode.c.patch](https://dl.dropboxusercontent.com/u/16521384/vmtools.inode.c.patch)

Instructions:
Create a folder and copy 'vmhgfs-fix.sh', 'vmtools.inode.c.patch' and 'VMwareTools-9.x.x.tar.gz' inside.
If needed, give permission to execute vmhgfs-fix.sh: chmod +x vmhgfs-fix.sh
Then type: ./vmhgfs-fix.sh

This script will extract VMwareTools, patch it and make it ready to be installed.

It is working for me at Xubuntu 13.04 (but it will run fine on Ubuntu, Kubuntu, Edubuntu 13.04...)

vmhgfs-fix.sh
```
#!/bin/bash
#
# Patch to fix VMware-Tools installation in kernel 3.8.x
# Working for Ubuntu 13.04 (Xubuntu and Kubuntu also)
#

# Get VMwareTools file (it should be in the default format VMwareTools-9.x.x...)
VMFILE=`ls | grep VMwareTools-9.*`

if [[ ! $VMFILE ]]
then
  printf "\nERROR: \nVMwareTools-9.(...).tar.gz not found.\n\nYou should place it in the current folder and/or \nRename it as VMwareTools-9... (default format name)\n\n"
  exit
fi

# Check for vmware-tools-distrib folder
if [[ ! -d vmware-tools-distrib ]]
then
  printf "\nExtracting VMware-tools...\n"
  # Extract VMware Tools
  tar xf $VMFILE
else
  printf "\n/vmware-tools-distrib already exists.\nPlease remove it before applying this patch.\n\n"
  exit
fi

# Record the current directory
PATCH_DIR=$PWD

printf "\nApplying patch to VMware-Tools...\n\n"
sleep 3
pushd vmware-tools-distrib/lib/modules/source

# Make a backup of vmhgfs.tar
cp vmhgfs.tar vmhgfs.tar.backup
# Extract vmhgfs.tar
tar xf vmhgfs.tar
# Go to extracted vmhgfs.tar
pushd vmhgfs-only/
# Apply patch
patch -p1 < $PATCH_DIR/vmtools.inode.c.patch
popd
# Remove old vmhgfs.tar
rm -rf vmhgfs.tar
# Repack new vmhgfs.tar
tar cf vmhgfs.tar vmhgfs-only
# Remove vmhgfs-only dir which is not needed
rm -rf vmhgfs-only
popd

printf "\nPatch Applied!\n"
printf "Now try to install VMware-Tools.\n\n"

```

vmtools.inode.c.patch
```
--- ./inode.c	2013-02-26 02:18:24.000000000 +0000
+++ ./inode.c	2013-05-03 00:34:59.995053850 +0100
@@ -885,7 +885,8 @@
    ASSERT(inode);
 
    LOG(4, (KERN_DEBUG "VMware hgfs: HgfsTruncatePages: entered\n"));
-   result = compat_vmtruncate(inode, newSize);
+	 //result = compat_vmtruncate(inode, newSize);
+   result = 0; // Fix for kernels 3.8.x due to an error in truncate function
    if (result) {
       LOG(4, (KERN_DEBUG "VMware hgfs: HgfsTruncatePages: vmtruncate failed "
               "with error code %d\n", result));

```

---

### Post by riteshshrv on 2013-05-04
System Info: Windows 8 x64 Host, Ubuntu 13.04 Guest VMware Workstation 9.0
I faced the same problem here but following code helped me get the shared folders from host:
**sudo apt-get install linux-source**
**sudo apt-get install open-vm-tools**
Just keep on pressing enter for all defaults and then do this at the terminal
**mount -t vmhgfs .host:/ /home/user1/shares**
here "user1" is your username and "shares" is where your shared folders would be displayed.

---

### Post by Baruk on 2013-05-28
Hi,

Thanks a lot for your work.
How can i do to have the shared folder directly after the boot without enter :
[B]mount -t vmhgfs .host:/ /home/user1/shares

[/B]I tried some option with **fstab** but nothing works

---

### Post by bgcngm on 2013-05-28
Read the post two times above yours, the solution is there.

---

### Post by Baruk on 2013-05-29
Hi,

I have read all the post and links but ... nothing work.

1/ Add "[COLOR=#000000][FONT=Ubuntu Mono].host:/ /mnt/hgfs vmhgfs defaults 0 0" in /etc/fstab

2/ Add "[/FONT][/COLOR][COLOR=#000000][FONT=helvetica]mount -t vmhgfs .host:/ /mnt/hgfs  " in [/FONT][/COLOR][COLOR=#333333][FONT=Arial]/etc/init.d/open-vm-tools

If I understand, the **.patch** and **.sh** are not made to have the share folder directly after the boot.[/FONT][/COLOR]

---

### Post by bgcngm on 2013-05-29
> **Baruk said:**
> [COLOR=#333333][FONT=Arial]If I understand, the **.patch** and **.sh** are not made to have the share folder directly after the boot.[/FONT][/COLOR]
You're wrong... the solution above consists in patching VMware Tools so that you're able to install it on Ubuntu 13.04. Afterwards, you'll get it working directly after boot, like before. Read the instructions once again and it must work.

---

### Post by dino99 on 2013-05-29
instead of vmware, use virtualbox

---

### Post by Baruk on 2013-05-29
Thanks a lot, it is working :)

I m beginer in English and Linux, so it is difficult for me to all understand.

---

### Post by Bit Hacker on 2013-06-04
Hi Guys, thanks a lot for working out a solution. I had same problem and now its' working. Now I have a problem with 'Drag and Drop' as I can't drag my files from Windows 7 (host) to Ubuntu 13.04 (guest.) What should I do? Thanks in advance.

---

### Post by cariboo on 2013-06-04
Does this solution also work for Saucy?

---

### Post by John Peterson on 2013-06-11
## hlist_for_each_entry build fix

>Does this solution also work for Saucy?

There's a fix for the `hlist_for_each_entry` build error at [https://github.com/mirror/vmware/issues/7](https://github.com/mirror/vmware/issues/7)

---

### Post by cariboo on 2013-06-12
> **John Peterson said:**
> ## hlist_for_each_entry build fix

>Does this solution also work for Saucy?

There's a fix for the `hlist_for_each_entry` build error at [https://github.com/mirror/vmware/issues/7](https://github.com/mirror/vmware/issues/7)

I was asking in a round about way if you are running vmware on Saucy, as this sub-forum is for the discussing problems encountered while running the development version. For discussing problems with virtualization on released versions the discussions should be in the virtualisation sub-forum

---

### Post by UnSandpiper on 2013-06-28
> **socket said:**
> A workaround for this problem is to edit 'inode.c' and change the line '888' to remove 'compat_truncate' function call (that is responsible for this problem on kernels 3.8.x). This file is inside 'vmware-tools-distrib', so you need to perform the following steps:

Extract VMWare-Tools (probably you will get a folder called vmware-tools-distrib).
Then:
> cd /vmware-tools-distrib/lib/modules/source
> tar xf vmhgfs.tar
> cd vmhgfs-only/
> sudo gedit inode.c
Go to line 888: result = compat_vmtruncate(inode, newSize);
And change it to: result = 0;
Then save the file and exit gedit.
> cd ..
> rm -rf vmhgfs.tar
> tar cf vmhgfs.tar vmhgfs-only/
> rm -rf vmhgfs-only/

Now restart the installing procedure. It worked for me in Xubuntu 13.04.

I tried this several times in my Ubuntu 13.04 VM and took me a while to figure out why this procedure didn't work for me.
I had the vmware-tools already installed and I extracted the vmware-tools once again on my Desktop and and patched according to your instructions.
Then I'd ran bin/vmware-config-tools.pl from the extracted folder on my desktop and it would still fail in line 888.

Turns out that regardless of where you launch vmware-config-tools.pl, if you have vmware-tools already installed it will install from /usr/lib/vmware-tools/modules/source/.
So in that case you need to patch the inode.c in installed path instead of the extracted vmware-tools.

---

### Post by [Neurotic] on 2013-08-10
Worked perfectly! You are a scholar and a gentleman :)

---

### Post by snaremiguel on 2013-09-04
Brilliant patch! Thank you for making it.

---

### Post by amit_sharma2 on 2013-10-07
> **bgcngm said:**
> Just found an alternative to be able to mount shared folders:

```
sudo apt-get install open-vm-tools
sudo mount -t vmhgfs .host:/ /mnt/hgfs
```

This worked like a charm for me in Lubuntu 13.04 - thank you bgcngm!!

---

### Post by cariboo on 2013-10-07
Seeing as Saucy is close to a week and a half from release, I don't see the need for this thread any more. Closed.

---

