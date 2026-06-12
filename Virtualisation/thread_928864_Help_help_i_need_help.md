---
title: "Help help i need help"
date: 2008-09-24
forum: Virtualisation
---

### Post by touchapedia on 2008-09-24
man this is **annoying** me i need someone to help me fix this error


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
if you know how please send a reply or email thanks

---

### Post by prshah on 2008-09-24
> **touchapedia said:**
> 
 Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..


As a first step: Open a terminal, (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install virtualbox-ose-modules-generic
```

---

### Post by touchapedia on 2008-09-24
> **prshah said:**
> As a first step: Open a terminal, (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install virtualbox-ose-modules-generic
```
it gives me this in terminal

reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages

---

### Post by prshah on 2008-09-25
> **touchapedia said:**
>   virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages

```
sudo apt-get install virtualbox-ose-modules-2.6.24-20-generic
``` The virtualbox-ose-generic is a metapackage that should automatically select the correct version for your running kernel; but that didn't happen, so the above command will work.

---

### Post by touchapedia on 2008-09-25
this is what i get i uninstalled virtualbox and did it and this is what happend

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  virtualbox-ose-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable
E: Broken packages

---

### Post by pingnak on 2008-09-25
I have the same problem.  For some reason that 'latest, greatest' -20 kernel ain't installed, but the configurator thinks it is, but once it tries, it discovers it can't install the -20 version because for whatever reason, I'm not running the -20 kernel.

Looks like I have versions up to -19 installed, but nothing touched my grub/menu.lst to update it, so -16 is running.

You can manually install the version that matches the kernel you're currently running.

Check the kernel version that you're actually running.  The numbers should match with the module.

So, if you have 2.6.24-16-generic installed as the kernel...
sudo apt-get install virtualbox-ose-modules-2.6.24-16-generic

Remember, the NEXT time an 'automatic update' updates the kernel, this will break, and you'll need to manually install the kernel goodies for THAT.

---

### Post by melojo on 2008-09-25
type 
uname -r in a console and that will tell you what kernel you have

---

### Post by touchapedia on 2008-09-25
2.6.24-19-generic

it says this ^^^^^

---

### Post by melojo on 2008-09-26
> **touchapedia said:**
> 2.6.24-19-generic

it says this ^^^^^
Sorry it took so long to get back to you
you may have already figured it out!!!
type in a console
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic

---

### Post by ad_267 on 2008-09-27
I'm having the same problem. That worked for me.

---

