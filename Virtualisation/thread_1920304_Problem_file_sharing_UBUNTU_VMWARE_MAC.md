---
title: "Problem file sharing UBUNTU VMWARE MAC"
date: 2012-02-04
forum: Virtualisation
---

### Post by JrVerbiest on 2012-02-04
Hello,
 
I have a problem with file sharing under Ubuntu that runs in VMWARE Fusion.




My setup:
VMWARE FUSION running on my MacBook Pro

Ubuntu 11.10 in VM

 
I had a problem with sharing my MAC folders in Ubuntu 

I perform the following steps, found on the internet
 
(optional) if vmware tools is already installed via option 3, it must be uninstalled:
    1.    sudo vmware-uninstall-tools.pl 
    2.    create a directory to store some keys (doesn't matter where)
    3.    navigate to that directory
    4.    wget [http://packages.vmware.com/tools/keys/VMWARE-PACKAGING-GPG-DSA-KEY.pub](http://packages.vmware.com/tools/keys/VMWARE-PACKAGING-GPG-DSA-KEY.pub)
    5.    wget [http://packages.vmware.com/tools/keys/VMWARE-PACKAGING-GPG-RSA-KEY.pub](http://packages.vmware.com/tools/keys/VMWARE-PACKAGING-GPG-RSA-KEY.pub)
    6.    wget [http://packages.vmware.com/tools/VMWARE-PACKAGING-GPG-KEY.pub](http://packages.vmware.com/tools/VMWARE-PACKAGING-GPG-KEY.pub)
    7.    sudo apt-key add *KEY.pub
    8.    cd /etc/apt/sources.list.d
    9.    sudo emacs -nw vmware-tools.list
    10.    add the following line to that file followed by a newline:
    1.    deb [http://packages.vmware.com/tools/esx/4.1latest/ubuntu](http://packages.vmware.com/tools/esx/4.1latest/ubuntu) lucid main restricted
    11.    ctrl+x ctrl+s (saves the file)
    12.    ctrl+x ctrl+c (exits emacs)
    13.    sudo apt-get update    DONE
    14.    sudo apt-get install vmware-open-vm-tools-kmod-source
    15.    sudo module-assistant prepare
    16.    sudo module-assistant build vmware-open-vm-tools-kmod-source 
    17.    sudo module-assistant install vmware-open-vm-tools-kmod
    18.    sudo apt-get install vmware-open-vm-tools
 
After doing this everything works fine. I was able to copy my files

 
But than I have done an update.
 
Results, folder sharing does not work. 

I am unable to access my MAC folders.
 
Any idea what the problem is.
 
Thanks.
JrV

---

