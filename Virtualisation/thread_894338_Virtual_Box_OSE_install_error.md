---
title: "Virtual Box OSE install error"
date: 2008-08-19
forum: Virtualisation
---

### Post by Icroc on 2008-08-19
I am a beginner with Linux.  No longer wishing to support Bill's lifestyle I have installed Ubuntu 8.04 and it is working fine. I have a problem unfortunately, I still need to use an XP platform for one particular piece of software.  I have ticked the box to select Virtual Box OSE in the Add/Remove Applications  and it appears to have installed.  I already have a partition with XP running and Virtual Box has identified XP as a Virtual Machine.  When I try to start XP as a Virtual Machine I get the following error message

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).
[/COLOR][/COLOR]
Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/COLOR]


I have tried to download from the website without success.  Searching the Web, this seems to have  been a problem for some time.

Can anyone tell me in “simple speak” what to do to activate Virtual Box in Ubuntu 8.04?

Thanks in advance

---

### Post by Ryadt on 2008-08-19
Try ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Zeitgeist6149 on 2008-08-19
i seem to be having the same problem. i'm a new linux user as well. i get the same error and i tried sudo apt-get update && sudo apt-get upgrade but nothing was needed to upgrade.  

any more suggestions?

---

### Post by Separ on 2008-08-19
Try removing the old module.
```
sudo apt-get remove virtualbox-ose-modules*
```
```
sudo apt-get purge virtualbox-ose-modules*
```
Then install the new one.
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

---

### Post by linuxguymarshall on 2008-08-19
I have had the same issue and eventually just switched to VMWare but if there is a fix I could really use it.

---

### Post by Separ on 2008-08-19
Look at my above post, the error is caused by the wrong module package being installed.

---

### Post by novus721 on 2008-08-20
I am having similar problems. I purged the old version, but every time I go to reinstall I have issues with the kernel still. I always suggests that I install virtualbox-ose-modules-generic, but my box won't let me as I have  virtualbox-ose-modules-2.6.24-20-generic but it is not installed. When I try to install it I get this.

```
$ sudo apt-get install virtualbox-ose-modules-2.6.24-20-generic Reading package lists... Done
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

The following packages have unmet dependencies:
  virtualbox-ose-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable
E: Broken packages

```

any ideas???

---

### Post by MarkDTS on 2008-08-20
I'm also experiencing a similar error when I attempt to launch the virtual machine. 

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

Any help would be appreciated.

---

### Post by Sam442 on 2008-08-22
> **Separ said:**
> Try removing the old module.
```
sudo apt-get remove virtualbox-ose-modules*
```
```
sudo apt-get purge virtualbox-ose-modules*
```
Then install the new one.
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

fixed mine, thanks :KS

---

### Post by MarkDTS on 2008-08-23
Hey guys! 

I've solved my issue above with something relatively simple. I simply went into my Users and Groups menu and augmented the permissions for this application. After I did this VirtualBox was able to access and write to the drivers that had been restricted by the root profile. 

I'm still relatively new to Ubuntu, so if someone has a streamline version of this process please post it. 




Below are the steps that I took. 

From the SYSTEM menu select ADMINISTRATION.

 
Navigate to the USERS AND GROUPS menu option. 


From the USERS SETTINGS window select UNLOCK to gain access to the root profile.


Highlight root from the list and select MANAGE GROUPS from the sidebar menu.


In GROUP SETTINGS you will need to scroll through you application list until you find VBOXUSERS.


Highlight this listing and select PROPERTIES from the sidebar menu. 


Check the boxes next to your current profile name and the root profile. 


Click OK and restart your system. 


You should now be able run VirtualBox without the error. 
```
1908 (VERR_VM_DRIVER_NOT_INSTALLED).
```




I really hope this helps.
Feel free to ask any questions. ;)

---

### Post by bro on 2008-08-23
> **Separ said:**
> Try removing the old module.
```
sudo apt-get remove virtualbox-ose-modules*
```
```
sudo apt-get purge virtualbox-ose-modules*
```
Then install the new one.
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

Excellent. Worked for me too.

---

### Post by lbriner on 2008-08-31
The latest VirtualBox modules available are for version 2.6.24-20 of the linux kernel and the current latest version of the kernel in ubuntu at least is 2.6.24-19 so it might offer you the upgrade but should fail to install it (because it doesn't have the required kernel). If somehow you did upgrade to the latest versions, which presumably won't work, follow the instructions above to remove the current modules and install using uname -r which will ensure you have the modules for your kernal, oh and don't upgrade VirtualBox until the next kernel arrives (not sure why the VB upgrades are available now!!).

---

