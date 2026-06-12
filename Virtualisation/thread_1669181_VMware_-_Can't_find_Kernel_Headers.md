---
title: "VMware - Can't find Kernel Headers"
date: 2011-01-17
forum: Virtualisation
---

### Post by Gex010 on 2011-01-17
Hi guys,

I'm trying to get VMware workstation up and running... I have followed all the steps provided in the VMware workstation installation guide but it does not provide any information on the following problem.

VMware seems to be installed successfully but when I run it, it says that my kernel header does not match the kernel that I have installed. But I have made sure that the header file I have is the right one (2.6.35-24-generic) it allows me to select the header from another location but the only header files I find are under /usr/src where I select linux-header-2.6.35-24-generic yet VM tells me "C header files matching your running kernel were not found."

Please can someone help!

---

### Post by gmargo on 2011-01-17
Have you installed the **linux-headers-generic** package?  This will install the latest linux-headers package.

---

### Post by HermanAB on 2011-01-18
Howdy,

When all else fails, install the kernel source and compile it.  If you can compile the kernel successfully, then VMware will compile and install itself perfectly.

---

### Post by Gex010 on 2011-01-18
> **HermanAB said:**
> Howdy,

When all else fails, install the kernel source and compile it.  If you can compile the kernel successfully, then VMware will compile and install itself perfectly.

Would you recommend compiling the same version I currently have or should I compile the latest kernel version?

---

### Post by swapii on 2011-10-12
> **gmargo said:**
> Have you installed the **linux-headers-generic** package?  This will install the latest linux-headers package.

Search for this in Synaptic package manager & download the required kernel headers..
n njoy....  :-)

---

### Post by jimmyco2008 on 2012-10-26
Hey all,

I hope it's alright that I bump this, I'm having the same problem.

I'm on Ubuntu 12.10, have the vmware Workstation trial, and it gives me the same error.

I downloaded that linuc generic kernel package, and it now shows up alongside the original in usr/src. 

I tried selecting both and vmware is still letting me have it...

Any ideas? 

Thank you!

---

### Post by ubuntukid on 2012-10-27
Unless I've missed an update, Ubuntu 12.10 is simply to new for VMware workstation. You'll currently have to use 12.04 to use it.

---

### Post by dyrer on 2012-10-28
Vmware as amahi etc they dont work on Ubuntu 12.10
If you want guys to use them, you should stay to 12.04 :(

---

### Post by TJet1.8 on 2012-10-28
The following is all you need to install/keep your kernel headers current and compile them for VMware Workstation:

sudo apt-get install gcc build-essential kernel-headers-$(uname -r) dkms

Where:
gcc = C Compiler to compile the required modules
build-essential = make. and other components needed to compile
kernel-headers-$(uname -r) = headers based on your installed kernel version
dkms = automatically downloads your kernel headers when the kernel is updated.

:popcorn:

OH!....BTW....VMware Workstation 9 "does" work with Ubuntu 12.10, I am using it now :)
The trick is to also install the 3.5-x.x kernel patch...which is readily available on the Internet...

;)

---

### Post by Anubis on 2012-11-17
> **TJet1.8 said:**
> The following is all you need to install/keep your kernel headers current and compile them for VMware Workstation:

sudo apt-get install gcc build-essential kernel-headers-$(uname -r) dkms

Where:
gcc = C Compiler to compile the required modules
build-essential = make. and other components needed to compile
kernel-headers-$(uname -r) = headers based on your installed kernel version
dkms = automatically downloads your kernel headers when the kernel is updated.

:popcorn:

OH!....BTW....VMware Workstation 9 "does" work with Ubuntu 12.10, I am using it now :)
The trick is to also install the 3.5-x.x kernel patch...which is readily available on the Internet...

;)

```
$ sudo apt-get install gcc build-essential kernel-headers-$(uname -r) dkms
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kernel-headers-3.5.0-19-generic
E: Couldn't find any package by regex 'kernel-headers-3.5.0-19-generic'
me@aspire:~$
```:confused:

---

### Post by Solvedthis on 2012-11-27
I had the same problem installing vmware tools on ubuntu 12.10.

This didn't work for me:
[FONT="Courier New"]$ sudo apt-get install gcc build-essential kernel-headers-$(uname -r) dkms[/FONT]

Instead, this did the job:
[FONT="Courier New"]sudo apt-get install linux-headers-$(uname -r)[/FONT]

---

### Post by westside159 on 2013-02-22
> **Solvedthis said:**
> 
[FONT="Courier New"]sudo apt-get install linux-headers-$(uname -r)[/FONT]

This really works! Just solved it using that line! Thanks **Solvedthis**!

---

### Post by matt_symes on 2013-02-23
Old thread. Closed.

---

