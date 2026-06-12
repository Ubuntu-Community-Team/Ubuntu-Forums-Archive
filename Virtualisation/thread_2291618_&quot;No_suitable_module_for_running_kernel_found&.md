---
title: "&quot;No suitable module for running kernel found&quot; error installing VirtualBox"
date: 2015-08-21
forum: Virtualisation
---

### Post by Novitk on 2015-08-21
Hello, I'm trying to install VirtualBox 4.3.10 (the default version in the repositories) on an up to date Xubuntu 14.04, but I receive this error message in the terminal:

```
"No suitable module for running kernel found"
```

When I open VirtualBox and try to run a virtual machine, it gives me this error:

```
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'


as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

It seems vboxdrv wasn't created during virtualbox-dkms installation (due to the error "No suitable module for running kernel found"):

```
$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
```

As far as I've read other topics, this error is related to Virtualbox driver not being created. Some solutions I've found tell to install linux-headers and build-essential, but they are already installed here. This is the list of related packages that might be needed that I already have installed:

[LIST]
[*]linux-image-3.19.0-26-generic
[*]linux-image-extra-3.19.0-26-generic
[*]linux-headers-3.19.0-26
[*]linux-headers-3.19.0-26-generic
[*]module-assistant
[*]virtualbox-dkms
[*]dkms
[*]build-essentia
[/LIST]



I'm using Linux 3.19.0-26-generic:

```
$ uname -r
3.19.0-26-generic

```

Could someone help me, please?

---

### Post by Novitk on 2015-08-21
By the way, installing the .deb file (v. 5.0.2) from VirtualBox website worked just fine. I wonder why the version in the repositories is not working :/

---

### Post by Sarkozy on 2015-08-22
Great Novitk!  I have the same problem, but forgive my limited experience with installing vbox.  
How did you get your "worked just fine." to work??
Also, this is Ubuntu, not Xubuntu (but I'm testing that elsewhere too).
Best Thx, rgds

background...  Question:  How did you get it to work???
I  downloaded that version - 5.0.2, ran it via the Ubuntu Software Center,  and it again failed with the same error.  Went to /tmp, found the  package there, did the same thing and got the same result.  Then  extracted the package, looked through the directories, found vboxdrv  added setup and it wouldn't run.

---

### Post by Novitk on 2015-08-23
It doesn't matter if it's Ubuntu or Xubuntu. Virtualbox requires some packages to be installed previous to its installation. You must install the *headers for your kernel* version and the package *build-essential* first: 

```
$ sudo apt-get install linux-headers-$(uname -r) build-essential
```

After that, reinstall the .deb file from Virtualbox site. Note this is not a solution to the broken package in repositories, but a workaround to have some version of Virtualbox running in your machine. The topic remains open.

---

### Post by bisherbas on 2015-08-23
Experiencing the same problem. None of the suggestions worked for me. Running Xubuntu 14.04.3 with with kernel 3.19.0-26.

```
Unpacking virtualbox-dkms (4.3.10-dfsg-1ubuntu5) over (4.3.10-dfsg-1ubuntu5) ...
Preparing to unpack .../virtualbox-guest-utils_4.3.10-dfsg-1ubuntu5_amd64.deb ...
Unpacking virtualbox-guest-utils (4.3.10-dfsg-1ubuntu5) over (4.3.10-dfsg-1ubuntu5) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up virtualbox (4.3.10-dfsg-1ubuntu5) ...
 * Stopping VirtualBox kernel modules                                                                            [ OK ] 
 * Starting VirtualBox kernel modules                                                                                   
 * No suitable module for running kernel found [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Setting up virtualbox-dkms (4.3.10-dfsg-1ubuntu5) ...
Loading new virtualbox-4.3.10 DKMS files...
Building only for 3.19.0-26-generic
Building initial module for 3.19.0-26-generic
Error! Bad return status for module build on kernel: 3.19.0-26-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.3.10/build/make.log for more information.
 * Stopping VirtualBox kernel modules                                                                            [ OK ] 
 * Starting VirtualBox kernel modules                                                                                    
* No suitable module for running kernel found [fail]
```

---

