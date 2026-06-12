---
title: "Ubuntu 15.04 &amp; VMware Workstation 11.1"
date: 2015-04-24
forum: Virtualisation
---

### Post by RichardET on 2015-04-24
I installed the latest Ubuntu last night - unfortunately VMware is now broken.  I have uninstalled and reinstalled, but the kernel modules fail to build.  
It's really annoying.

---

### Post by sammiev on 2015-04-24
We need a new update from VMware so we can use the latest kernel in 15o4. I used a old kernel a few weeks back and was good to go.

---

### Post by RichardET on 2015-04-26
Found the solution:
[https://communities.vmware.com/thread/509225](https://communities.vmware.com/thread/509225)

This can be fixed by running the following steps as Root (in a terminal):
 
Step 1: log in as root (e.g. sudo -s)
Step 2: Enter your Root password.
Step 3: Enter these commands: 
 
curl [http://pastie.org/pastes/9934018/download](http://pastie.org/pastes/9934018/download) -o /tmp/vmnet-3.19.patch
 
cd /usr/lib/vmware/modules/source
tar -xf vmnet.tar
patch -p0 -i /tmp/vmnet-3.19.patch
mv vmnet.tar vmnet.tar.SAVED
tar -cf vmnet.tar vmnet-only
rm -r vmnet-only
vmware-modconfig --console --install-all
 
VMware will now compile the vmnet module for Kernel 3.19. (please make sure you have DKMS installed)
 
Hope it will work for you. In my case this solved the problem with VMware Player 7.

---

### Post by sammiev on 2015-04-26
> **RichardET said:**
> Found the solution:
[https://communities.vmware.com/thread/509225](https://communities.vmware.com/thread/509225)

This can be fixed by running the following steps as Root (in a terminal):
 
Step 1: log in as root (e.g. sudo -s)
Step 2: Enter your Root password.
Step 3: Enter these commands: 
 
curl [http://pastie.org/pastes/9934018/download](http://pastie.org/pastes/9934018/download) -o /tmp/vmnet-3.19.patch
 
cd /usr/lib/vmware/modules/source
tar -xf vmnet.tar
patch -p0 -i /tmp/vmnet-3.19.patch
mv vmnet.tar vmnet.tar.SAVED
tar -cf vmnet.tar vmnet-only
rm -r vmnet-only
vmware-modconfig --console --install-all
 
VMware will now compile the vmnet module for Kernel 3.19. (please make sure you have DKMS installed)
 
Hope it will work for you. In my case this solved the problem with VMware Player 7.

I will have to wait for the update as it will not work for me on 3.19.0-15-generic. but Thanks

---

### Post by sub sexy on 2015-05-06
Thanks Richard. This worked for me as well after a clean install. Thanks a million for the information

---

### Post by dexxster on 2015-05-29
Hi,

it worked for me on latest Ubuntu 15  doing so:

wget [http://pastie.org/pastes/9934018/download](http://pastie.org/pastes/9934018/download) -o /tmp/vmnet-3.19.patch
 **cat /tmp/vmnet-3.19.patch**
cd /usr/lib/vmware/modules/source
tar -xf vmnet.tar
**patch -p0 -i /tmp/download**
mv vmnet.tar vmnet.tar.SAVED
tar -cf vmnet.tar vmnet-only
rm -r vmnet-only
vmware-modconfig --console --install-all
cat /tmp/vmnet-3.19.patch

I hope it works for you too.

:-)

---

### Post by Featalene on 2015-06-06
I'm trying this patch with VMware Workstation 10 with kernels from 3.19.0-15 through 3.19.0-18 with no success. If the patch is different for WS 10 would some kind person point me in the right direction? If there is a different patch available I seem to be google-challenged at the moment.

---

### Post by au10tic on 2015-06-11
hmm, i am using workstation 11.1.0 build-2496824 ubuntu has kernel 3.19.0.18-generic, but something doesnt match here.

in the steps above it says [COLOR=#000000][I]cd /usr/lib/vmware/modules/source but there is no "vmware" folder on the installation path, there is a vmware-tools also once you're inside the /usr/lib/vmware-tools/modules/source folder there is no vmnet.tar file, there are vmxnet.tar and a vmxnet3.tar

so when i follow the steps above by richardet just modifying the path and file, when i run [/I][/COLOR][COLOR=#000000][I]patch -p0 -i /tmp/vmnet-3.19.patch i get the below;
[/I][/COLOR]can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur vmnet-only.a/driver.c vmnet-only/driver.c
|--- vmnet-only.a/driver.c	2014-11-20 20:13:56.000000000 -0500
|+++ vmnet-only/driver.c	2015-02-09 15:40:10.916640592 -0500
--------------------------
File to patch: 
[COLOR=#000000][I]
so is waiting for me to i guess provide a file, any advice?[/I][/COLOR]

---

### Post by KartDriver on 2015-06-15
The solution posted by RichardET worked great for me on Kubuntu 15.04 with VMWare Workstation 11.1!

Thanks!

---

### Post by vincentertainment on 2015-06-28
Thank you,  RichardET!
This worked for me.

---

### Post by kmajaa on 2015-06-29
[COLOR=#000000]Thank you, RichardET!
Worked for me as well. [/COLOR]

---

### Post by Darryl_Baker on 2015-07-17
I fixed my issue by buying the upgrade and then using the patch. :( An expensive solution.

---

### Post by lambdafox on 2015-08-11
> **RichardET said:**
> ...
 
Step 1: log in as root (e.g. sudo -s)
Step 2: Enter your Root password.
Step 3: Enter these commands: 
 
curl [http://pastie.org/pastes/9934018/download](http://pastie.org/pastes/9934018/download) -o /tmp/vmnet-3.19.patch
 
cd /usr/lib/vmware/modules/source
tar -xf vmnet.tar
patch -p0 -i /tmp/vmnet-3.19.patch
mv vmnet.tar vmnet.tar.SAVED
tar -cf vmnet.tar vmnet-only
rm -r vmnet-only
vmware-modconfig --console --install-all
 
...

I would like to confirm that this worked for me with:

Xubuntu Core 15.04 amd64 (kernel:3.19.0-15-generic) & VMWare 11.1.0 build-2496824

I had to install curl first.

:D

---

### Post by andres34 on 2015-11-27
[B]" patch -p0 -i /tmp/download " what does it do?
keep getting "no such directory" errors...
[/B]

---

### Post by andres34 on 2015-11-27
[I]andy@HP-Laptop:~$ sudo /tmp/vmnet-3.19.patch
sudo: /tmp/vmnet-3.19.patch: command not found
andy@HP-Laptop:~$ patch -p0 -i /tmp/vmnet-3.19.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur vmnet-only.a/driver.c vmnet-only/driver.c
|--- vmnet-only.a/driver.c    2014-11-20 20:13:56.000000000 -0500
|+++ vmnet-only/driver.c    2015-02-09 15:40:10.916640592 -0500
--------------------------
File to patch:  [/I]

**I cantget passed this...  **

---

### Post by sammiev on 2015-11-27
> **andres34 said:**
> [I]andy@HP-Laptop:~$ sudo /tmp/vmnet-3.19.patch
sudo: /tmp/vmnet-3.19.patch: command not found
andy@HP-Laptop:~$ patch -p0 -i /tmp/vmnet-3.19.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur vmnet-only.a/driver.c vmnet-only/driver.c
|--- vmnet-only.a/driver.c    2014-11-20 20:13:56.000000000 -0500
|+++ vmnet-only/driver.c    2015-02-09 15:40:10.916640592 -0500
--------------------------
File to patch:  [/I]

**I cantget passed this...  **

Try [this]("http://ubuntuforums.org/showthread.php?t=2303546") post.

---

