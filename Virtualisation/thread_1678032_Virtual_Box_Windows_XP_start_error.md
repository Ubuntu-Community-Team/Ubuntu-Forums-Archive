---
title: "Virtual Box Windows XP start error"
date: 2011-01-29
forum: Virtualisation
---

### Post by grandtricks1 on 2011-01-29
Guys please help!
When i start windows Xp from Viroxtual box i get the error

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


WHen i do what it tells me to do i get...

root@cr48-ubuntu:/home/user# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.32.23+drm33.10 cannot be found at
/lib/modules/2.6.32.23+drm33.10/build or /lib/modules/2.6.32.23+drm33.10/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

I searched the forum for answers bu none of thm worked
I'm on Ubuntu 11.4

---

### Post by snowpine on 2011-01-29
"As root" means you need to use the 'sudo' command to perform system administration functions. Also notice the advice that "Ubuntu users should install DKMS first." So:

```
sudo apt-get update
sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup
```

If there are any error messages, please copy & paste and I'll try to help. :)

---

### Post by grandtricks1 on 2011-01-29
ok so i did what you said and updated and installed dkms but it said that dkms was already installed.
Here's what i got when i put in the sudo /etc/init.d/vboxdrv setup and got
root@cr48-ubuntu:/home/user# sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.32.23+drm33.10 cannot be found at
/lib/modules/2.6.32.23+drm33.10/build or /lib/modules/2.6.32.23+drm33.10/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

WHat's the kernal 2.6.32.23+drm33.10?
and i think i did install dkms before i installed vbox

---

### Post by grandtricks1 on 2011-01-29
and how come i can't acess the log... it says permission denied even when im in root

---

### Post by snowpine on 2011-01-29
I am surprised dkms did not install your kernel headers as a dependency, nevertheless you should be able to with:

```
sudo apt-get install linux-headers-generic
```

To view the log file:

```
cat /var/log/vbox-install.log
```

Or open it with your favorite text editor (such as gedit).

However, please note you are not using the supported kernel for Ubuntu 11.04, therefore I am not 100% certain these instructions will work. :(

---

### Post by grandtricks1 on 2011-01-29
For the first one i got 

user@cr48-ubuntu:~$ sudo apt-get install linux-headers-generic
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and vb still gives me the message thing..

and what do you mean by right kernal? 

Can i like downgrade 11.4 to 10.10?

---

### Post by snowpine on 2011-01-29
My understanding is that the DRM kernel is designed for certain 3D graphics cards. Since I am not familiar with this kernel myself, or how you installed it, I don't want to give you bad advice. :)

---

### Post by snowpine on 2011-01-29
See if you can:

```
sudo apt-get install linux-headers-2.6.32.23+drm33.10
```

---

### Post by grandtricks1 on 2011-01-29
... what if i turn off 3d acceleration?
and i tried and got 

user@cr48-ubuntu:~$ sudo apt-get install linux-headers-2.6.32.23+drm33.10
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-2.6.32.23+drm33.10
E: Couldn't find any package by regex 'linux-headers-2.6.32.23+drm33.10'

---

### Post by snowpine on 2011-01-29
I'm afraid I don't know how or where from you installed kernel 2.6.32.23+drm33.10, so I don't know where to find its headers. If you can remember...

Another thing you could try is to reboot and choose a different kernel (non-DRM) from the GRUB boot menu.

---

### Post by grandtricks1 on 2011-01-29
hmm.. im running ubuntu from the cr-48 so i guess i got it from ubuntu download process...
How do i choose a different kernal?
And thnx for the help btw, aprreciate it :)

---

### Post by snowpine on 2011-01-29
I did not realize you were using Google Chrome operating system. I have never used Chrome before, sorry I cannot help you. :(

---

### Post by grandtricks1 on 2011-01-30
x.x i thought it wouldn't really change anything as long as I'm running ubuntu..
but ok thnx for everything!!

---

### Post by NightwishFan on 2011-01-30
It seems like you are running a mainline build of some sort, you need to find the headers for it or nothing will work that uses DKMS. Or you need the generic kernel for it to work.

---

### Post by grandtricks1 on 2011-01-30
and i can find that how?
do i find something made for the main operating system or ubuntu because the laptop im using is still linux

---

### Post by NightwishFan on 2011-01-30
No, it needs to be for your specific kernel. I am not sure what to tell you.

---

### Post by snowpine on 2011-01-30
Google Chrome is somewhat based on Ubuntu, I guess, but that does not necessarily mean an Ubuntu user such as myself can give you accurate advice in all instances. You might have better luck on the Chrome forum: [http://www.google.com/support/forum/p/Chrome](http://www.google.com/support/forum/p/Chrome)

---

### Post by Ankhwatcher on 2011-01-30
I'm having a similar error to this user:
```
sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                                                                                                                                                           *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                                                                                                                                                              *  done.
 * Trying to register the VirtualBox kernel modules using DKMS
Error! Your kernel headers for kernel 2.6.32-28-server cannot be found at
/lib/modules/2.6.32-28-server/build or /lib/modules/2.6.32-28-server/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules
 * Look at /var/log/vbox-install.log to find out what went wrong

```

Any ideas?

Linux Headers and DKMS are already installed.

---

### Post by NightwishFan on 2011-01-30
I have had a similar problem with the Ubuntu kernel, try removing and reinstalling the headers and virtualbox-ose-dkms

---

### Post by Ankhwatcher on 2011-01-30
I found the missing package in synaptics:

---

### Post by dbradley96 on 2011-03-02
Maybe I'm wrong, but the the image is worthless.  I saw the last post and clicked on the thumb nail thinking I could just select what is shown in the screen shot.  You can't read anything.  I'm running into the same issue and thought this could be the answer.

---

### Post by Ankhwatcher on 2011-03-02
> **dbradley96 said:**
> Maybe I'm wrong, but the the image is worthless.  I saw the last post and clicked on the thumb nail thinking I could just select what is shown in the screen shot.  You can't read anything.  I'm running into the same issue and thought this could be the answer.

Well for that you can thank our heroic admin friend.
[My original image is hosted on photobucket and is nice and easy to read.]("http://i44.photobucket.com/albums/f3/Ankhwatcher/Forum%20Pictures/virtualboxsolution.jpg")

---

