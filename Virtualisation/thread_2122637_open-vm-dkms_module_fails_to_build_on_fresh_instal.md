---
title: "open-vm-dkms module fails to build on fresh installation?"
date: 2013-03-05
forum: Virtualisation
---

### Post by mklnz on 2013-03-05
I just grabbed a fresh copy of Ubuntu 12.0.4.2 64-bit Server, then did an apt-get update and upgrade.
Then, I tried to install apt-get install open-vm-tools

The primary package succeeds, but open-vm-dkms fails to build the kernel modules.

```

Building for 3.5.0-23-generic and 3.5.0-25-generic
Building for architecture x86_64
Building initial module for 3.5.0-23-generic
Error!  Build of vmblock.ko failed for: 3.5.0-23-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/open-vm-tools/2011.12.20/build/ for more information.

```

Anyone with the same issue? I tried Googling but there were almost no results. How can this be, since this is a completely fresh copy of Ubuntu 12.04 and I've done this procedure many times before and never had any issues.


Edit: make.log added

Edit: I see there is an existing bug report on this issue:
[https://bugs.launchpad.net/ubuntu/+source/open-vm-tools/+bug/1083719](https://bugs.launchpad.net/ubuntu/+source/open-vm-tools/+bug/1083719)

---

### Post by meteorrock on 2013-03-05
I just built that module just a week ago on Vmware workstation 9.0 here for my ubuntu guest OS, 64-bit. Using a Windows 7 64-bit Host. It was working fine. Make sure you update your headers first in your terminal. You will need to add the dkms module in your linux box for that module to build. Here is the codes I used. Make sure your Ubuntu linux box is upgraded also before you begin on your module for that fullscreen goodness. :) 

 I used the same generic kernel headers that comes with Ubuntu 12.10 here.  Looks like your headers need to be updated also to a higher grade, I will give the code for the correct headers you need for your module below.  I do not think it will build under linux 3.5.0-23 but I never tried it. Try to purge your linux 3.5.0-23 headers and just try to build it in linux 3.5.0-25 if you can.

```
sudo apt-get purge linux-headers-3.5.0-23-generic
```

```
sudo apt-get install linux-headers-3.5.0-25-generic
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install open-vm-tools
```

 Then we will need our module. Lets get it from the apt-get along with its tools. 

```
sudo apt-get install open-vm-dkms
```

```
sudo apt-get install open-vm-toolbox
```

If you get an error on building your module, try to purge the dkms or the VM tools and start over with the apt-get purge command in your terminal, followed along by the proper name for those tools in the codes above.  Looks like just an outdated kernel headers from what you listed on why it will not build for you.

You will need to reboot your linux guest OS inside of your Vmware and then power your hypervisor back off. Then power it back on to get that module to work. If you get an error on building that module try again. I am not sure on your experience level in linux so if this comes as a matter of course to you, let us know in the forums. :)

---

### Post by mklnz on 2013-03-15
Thanks for your reply, but unfortunately it did not work for me. I purged 3.5.0-23 and installed 3.5.0-25 but it still could not build.

Same error as before, with new kernel:


Error!  Build of vmblock.ko failed for: 3.5.0-25-generic (x86_64)

---

### Post by meteorrock on 2013-03-19
Sorry I did not get back to you sooner. Just thought about rechecking my threads in here for followup


I believe if you get an error on building your module in linux you have to use the <make clean>  command to flush that old kernel out that you tried to build , which is your module for your hypervisor. 

  Make clean deletes all the already compiled object files. If you have a failed make, running make clean in your terminal before trying again is a good idea. After you have done that, retry with that apt-get commands I gave above to get your source files for that module you want built.

~~~~~~~~~~~~~~~~`

Dont forget to run 

```
sudo apt-get upgrade && sudo apt-get update
```


after you use the <make clean> command in your terminal also. Make sure your ubuntu disto is updated through the software center before you get started. Lots of problems will solve themselves with just a simple update.

---

### Post by KubaV on 2013-05-16
It does not work on 3.5.0 kernels. I uninstalled 3.5.0 kernel and installed 3.2.0 kernel and this worked.
```
sudo apt-get purge linux-image-3.5.0* linux-headers-3.5.0*
sudo apt-get install linux-image-3.2.0-41-generic linux-headers-3.2.0-41-generic
```

---

### Post by andrewisett on 2013-07-18
I experienced the same issue as well - though I don't notice any bad side-effects.  Does this only affect the display in the VM console? (I only really use SSH to a couple of virtual servers.)

---

