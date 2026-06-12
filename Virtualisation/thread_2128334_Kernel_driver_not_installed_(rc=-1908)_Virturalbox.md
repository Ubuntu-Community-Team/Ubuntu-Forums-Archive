---
title: "Kernel driver not installed (rc=-1908) Virturalbox Error Ubuntu 12.10 on Acer C7"
date: 2013-03-22
forum: Virtualisation
---

### Post by pauler1 on 2013-03-22
I have looked in a variety of places for a solution and am only posting as a last resort.  If this is a redundant post I apologize in advance.

I am running Ubuntu 12.10 "Chrubuntu" on an Acer C7 and I have had a hard time trying to get Windows 7 installed in Virturalbox.
Whenever I try to start the VM i get the error:
Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]
as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I have tried a number of ways to fix this problem including:
[COLOR=#000000]*sudo apt-get install linux-headers-3.5.0-17-generic*[/COLOR]
[COLOR=#000000]*sudo apt-get remove virtualbox-dkms - gives me the error *[/COLOR]E: Unable to locate package virtualbox-dkm
[COLOR=#000000][I]sudo apt-get install virtualbox-dkms

does anyone know if I will be able to install virturalbox? I would like to uninstall it and start all over trying to get it to work but i'm not really sure how to do that.  
any help is appreciated, thanks :)[/I][/COLOR]

---

### Post by ibjsb4 on 2013-03-22
Not virtualbox-dkms, just dkms on the host.

 **Note:** Ubuntu/Debian users might want to install the **dkms** package to ensure that the VirtualBox host kernel modules (*vboxdrv*, *vboxnetflt* and *vboxnetadp*) are properly updated if the linux kernel version changes during the next apt-get upgrade.  For Debian it is available in Lenny backports and in the normal  repository for Squeeze and later. The dkms package can be installed  through the Synaptic Package manager or through the following command: 
 
sudo apt-get install dkms 
Got that from here

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Also install build-essentials

---

### Post by XBMC old School on 2013-03-24
> **ibjsb4 said:**
> Not virtualbox-dkms, just dkms on the host.

 **Note:** Ubuntu/Debian users might want to install the **dkms** package to ensure that the VirtualBox host kernel modules (*vboxdrv*, *vboxnetflt* and *vboxnetadp*) are properly updated if the linux kernel version changes during the next apt-get upgrade.  For Debian it is available in Lenny backports and in the normal  repository for Squeeze and later. The dkms package can be installed  through the Synaptic Package manager or through the following command: 
 
sudo apt-get install dkms 
Got that from here

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Also install build-essentials

Ya so i didnt understand or it wasn't said in other posts, but the commands are to be done in the guest addition. 

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

Man, did i learn to RTM. Haha hope this squares you away.

---

### Post by thetechguy911 on 2013-03-29
Hello pauler1
I have searched all over for solution, and have had no luck until I came across a site by kevinhodge.
Open a terminal using ctrl-alt-T, then enter the following commands:
wget [http://www.cisgendered.com/~keyvin/virtualbox-kernel-mods-3.4.0.deb](http://www.cisgendered.com/~keyvin/virtualbox-kernel-mods-3.4.0.deb)
then:
sudo dpkg -i virtualbox-kernel-mods-3.4.0.deb

Then, just run virtualbox and let the magic begin. 
Original website:[http://kevinhodge.com/WP/?tag=chrubuntu](http://kevinhodge.com/WP/?tag=chrubuntu)

"I have not failed, I have just found 10,000 ways not to make a lightbulb" Thomas Edison

---

### Post by pauler1 on 2013-04-04
Thanks! worked like a charm

---

