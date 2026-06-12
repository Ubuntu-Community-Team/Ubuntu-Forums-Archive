---
title: "Problems installing virtual box"
date: 2013-01-12
forum: Virtualisation
---

### Post by saskatchewan on 2013-01-12
I am running Ubuntu 12.04 on an ASUS U31S with a Samsung external DVD.

I am trying to install virtual box to run windows 7 (yes i have a license)  

However, when I start the windows install it says:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Then when installing windows it says

"device drivers are missing"

When I browse either the windows disk or the dvd rom disk it says it finds nothing.

Any suggestions?

THanks

---

### Post by Stormlord on 2013-01-12
It's a bit strange Virtualbox did not install DKMS on your system automatically.  Nevertheless, you should do as it says.  Run Synaptic, type DKMS in the quick search box and install it.  Alternatively, you could type 'sudo apt-get install dkms' (NO QUOTES) in a terminal window to install it.

After that, open a terminal and type 'sudo /etc/init.d/vboxdrv setup' (NO QUOTES).  That should do.  I am not sure about your Windows guest installation though.  That might have to be re-installed but I am not sure.

---

### Post by saskatchewan on 2013-01-12
This is the response I get when I type it in a terminal.

shawn@shawn-U31SD:~$ sudo apt-get install dkms
[sudo] password for shawn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 lib32gcc1 liboil0.3:i386 lib32stdc++6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.


Then when I run windows set-up, I get:

A required device cd/dvd device driver is missing...... etc.

---

### Post by efflandt on 2013-01-12
Apparently you did not realize there is a "Virtualisation" forum where questions/answers for this belong [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

How did you install virtualbox and what version are you running.  I installed it in 64-bit Ubuntu 12.04 using the instructions for "Debian-based Linux distributions"  at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) (which adds it to repositories) when it was still 4.2.4. It recently automatically updated itself to 4.2.6 with Update Manager during routine Ubuntu updates.

Although, I probably already had **dkms** installed, so nvidia video drivers could update automatically for new kernels.

Did you add your username to **vboxusers** group?

Did you also install the **VirtualBox Extension Pack** from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) (maybe that is required to access USB CD/DVD)?

---

### Post by howefield on 2013-01-12
Thread moved to the "*Virtualisation*" forum.

Check that you have installed the headers to match your kernel.

---

### Post by saskatchewan on 2013-01-12
I tried it again and it worked.

Now how do I post this as solved?

Thanks!!

---

### Post by howefield on 2013-01-12
> **saskatchewan said:**
> Now how do I post this as solved?

Thread Tools, near the top of the thread.

---

