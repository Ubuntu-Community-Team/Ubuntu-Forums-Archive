---
title: "Issues with virtualbox after installation"
date: 2017-10-15
forum: Virtualisation
---

### Post by rgonzalez3894 on 2017-10-15
Hello Everyone, I recently installed virtualbox on my ubuntu 16.04 OS by  typing "sudo apt-get install virtualbox" but once it finished  installing, there was a message saying that secure boot is enabled and  when i try opening it using the command "virtualbox" I get the following  message: 

WARNING: The character device /dev/vboxdrv does not exist.
  Please install the virtualbox-dkms package and the appropriate   headers, most likely linux-headers-generic.    
You will not be able to start VMs until this problem is fixed.&#65279;

Edit, after removing lock and running "sudo dpkg --configure -a" I got the following:  

 Your system has UEFI Secure Boot enabled.                                   
 &#9474;                                                                             
 &#9474; UEFI Secure Boot is not compatible with the use of third-party drivers.     
 &#9474;                                                                             
 &#9474; The system will assist you in toggling UEFI Secure Boot. To ensure that     
 &#9474; this change is being made by you as an authorized user, and not by an       
 &#9474; attacker, you must choose a password now and then use the same password     
 &#9474; after reboot to confirm the change.                                         
 &#9474;                                                                             
 &#9474; If you choose to proceed but do not confirm the password upon reboot,       
 &#9474; Ubuntu will still be able to boot on your system but the Secure Boot        
 &#9474; state will not be changed.                                                  
 &#9474;                                                                             
 &#9474; If Secure Boot remains enabled on your system, your system may still

---

### Post by Rick St. George on 2017-10-23
Did you also install any keys? Repo? Modify Source List?  Here is what I would do.

Open Terminal - Verify version / codename;

```

lsb_release -a

```

Using whatever plain text editor like gedit or scite
```

sudo gedit /etc/apt/sources.list

```

Note the Codename (example xenial - if different, replace in below code)
Add the following line to your /etc/apt/sources.list: 
```

deb http://download.virtualbox.org/virtualbox/debian xenial contrib

```

SAVE & Close.

Add Key, and combine with Downloading and Registering;

```

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add - 
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

```

Make sure DKMS is installed. May need to re-install to current kernal.
```

dkms status

```

Make sure Computer and OS is upto date (should do from time to time);

```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

```


Rebuild all DKMS modules for the currently running kernel: 

```

dkms autoinstall

```

Install Latest Version of VirtualBox (as of Oct. 2017);
```

sudo apt-get install virtualbox-5.2

```

Reboot computer. Afterwards, launch VirtualBox. Follow instructions using Manual download from here;
[http://download.virtualbox.org/virtualbox/UserManual.pdf](http://download.virtualbox.org/virtualbox/UserManual.pdf)

Instructions for installing above were found here;
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Please NOTE: According to VirtualBox website above;
**[COLOR=#FF0000]Update:[/COLOR]** The Guest Additions image with the 5.2.0 release fails to work with recent Linux guest kernels. 
Therefore, we will have to wait for a FIX.

Hope this helps!
Peace,
Rick

---

