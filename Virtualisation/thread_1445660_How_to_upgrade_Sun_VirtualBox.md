---
title: "How to upgrade Sun VirtualBox"
date: 2010-04-02
forum: Virtualisation
---

### Post by satimis on 2010-04-02
Hi folks,

host - ubuntu 9.10 64bit
virtualizer - Sun VirtualBox

I have the newest version "virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_amd64.deb" download. Please advise how to install it to upgrade the running VBox "Version 3.1.4 r57640"? Can I just run dpkg to install it and then the running package will be upgraded? TIA

B.R.
satimis

---

### Post by mikewhatever on 2010-04-02
Yes, dpkg -i or double click.

---

### Post by satimis on 2010-04-02
> **mikewhatever said:**
> Yes, dpkg -i or double click.

Hi,

Thanks for your advice.

Ran "sudo gdebi-gtk package" to install the package without complaint.

Reboot PC.  Some VMs can't start (others can).  Warning```

Failed to open/create the internal network
'Host IntrfaceNetworking-br0'
(VERR_SUPDRV_COMPONENT_NOT_FOUND).

Failed to attach the network LUN
(VERR_SUPDRV_COMPONENT_NOT_FOUND).

One of the kernel modules was not successfully loaded. Make sure that no kernel modules from an older version of VirtualBox exits.  Then try to recompile and reload the kernel modules by executing
'/etc/init.d/vboxdrv setup' as root
(VERR_SUPDRV_COMPONENT_NOT_FOUND).

```

Shutdown PC and restart it.  The same.  Please advise how to fix the problem.  TIA

B.R.
satimis

---

### Post by mikewhatever on 2010-04-02
Try searching for virtualbox in Synaptic and removing all versions. When done, reinstall the package you downloaded.

---

### Post by Chronon on 2010-04-02
Did you add the repository?  You should be able to just "sudo apt-get upgrade" if so.  Make sure you install dkms, as this will allow automatic recompilation of kernel modules when necessary.

---

### Post by satimis on 2010-04-03
> **mikewhatever said:**
> Try searching for virtualbox in Synaptic and removing all versions. When done, reinstall the package you downloaded.

On Synaptic
removed```

virtualbox-3.1 3.1.6-59338_Ubuntu_karmic

```

not removed```

python-libvirt
libvirt-bin

```

Reboot PC

$ sudo gdebi-gtk Downloads/virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_amd64.deb ```

[sudo] password for satimisu910: 
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.9

```

```

Setting up virtualbox-3.1 (3.1.6-59338_Ubuntu_karmic) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Success!
 * Starting VirtualBox kernel module                                            
 * modprobe vboxnetflt failed. Please use 'dmesg' to find out why

Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...

```

Reboot PC

$ dmesg | grep VirtualBox```

[  117.949410] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)

```
What does it mean?  I installed 64bit package


Edit:

# /etc/init.d/vboxdrv setup```

 * Stopping VirtualBox kernel module                                            
 * Cannot unload module vboxdrv

```


B.R.
satimis

---

### Post by satimis on 2010-04-03
> **Chronon said:**
> Did you add the repository?  You should be able to just "sudo apt-get upgrade" if so.  Make sure you install dkms, as this will allow automatic recompilation of kernel modules when necessary.

Hi Chronon,

Thanks for your advice.

I'm running Sun VirtualBox here.  The original package was download on Sun website.  This is my 1st upgrade

B.R.
satimis

---

### Post by satimis on 2010-04-03
Hi folks,


I found out the cause why some VM can't start. If;

On Sun VirtualBox
Settings -> Network
Adapter 1
[check] Enable Network Adapter
Attached to: Bridged Adapter
Name: br0

VM can't start

if selecting;
Attached to: NAT

then VM can start.  It can connect Internet.  But host can't ping its ip address.  Nor it can ping host.  The ip address shown on ifconfig is correct.

B.R.
satimis

---

### Post by HermanAB on 2010-04-03
Hmm, in my experience, if you are using VMs, then you should not do upgrades.  

Unless you a masochist with a very large amount of free time on your hands...

---

### Post by satimis on 2010-04-03
Hi folks,


Problem solved as follows;

Repeat;


 $ sudo /etc/init.d/vboxdrv setup```

 * Stopping VirtualBox kernel module                                           *  done.
 * Removing old VirtualBox netadp kernel module                                *  done.
 * Removing old VirtualBox netflt kernel module                                *  done.
 * Removing old VirtualBox kernel module                                       *  done.
 * Recompiling VirtualBox kernel module                                        *  done.
 * Starting VirtualBox kernel module                                          
 * modprobe vboxnetflt failed. Please use 'dmesg' to find out why

```


 $ sudo modprobe vboxnetflt```

FATAL: Error inserting vboxnetflt (/lib/modules/2.6.31-20-generic/updates/dkms/vboxnetflt.ko): Invalid module format

```


 $ sudo insmod /lib/modules/2.6.31-20-generic/updates/dkms/vboxnetflt.ko 


 $ lsmod | grep vbox```

vboxnetflt             14288  0 
vboxdrv              1778380  1 vboxnetflt

```

Problem solved.

Network -> Bridged Adapter

is now working.

One day gone already.



Edit:

The solution above stated seems NOT permanent.  On next reboot it must rerun;

$ sudo insmod /lib/modules/2.6.31-20-generic/updates/dkms/vboxnetflt.ko

otherwise the said problem returns.


satimis

---

### Post by jcoles on 2010-12-22
I made the solution persistent by adding the following line to /etc/rc.local:

insmod /lib/modules/`uname -r`/updates/dkms/vboxnetflt.ko

This really shouldn't be necessary. 
modprobe, which is supposed to be smarter than insmod, cannot insert vboxnetflt. It always complains that the module has an invalid format. This is why another solution I have seen -- adding vboxnetflt to the /etc/modules file -- cannot work.

---

