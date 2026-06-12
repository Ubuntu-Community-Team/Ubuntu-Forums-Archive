---
title: "NVIDIA driver problems  - Loaded or Not?"
date: 2010-11-08
forum: Ubuntu Studio
---

### Post by windeguy on 2010-11-08
After getting a lot of good help on this thread to install Ubuntu Studio on my laptop 

[http://ubuntuforums.org/showthread.php?t=1608913](http://ubuntuforums.org/showthread.php?t=1608913)

I find I need some help on a graphics card issue. 

I just installed Ubuntu Studio on an old desktop that has a 1.7 GHz P4 with 512MB of memory and a 150 GB Hard Drive.  It has an NVIDIA GeFORCE4 MX4000 AGP  graphics card.  I thought I was able to install the proprietary driver for it, but I am getting poor graphics performance and suspect something is incorrectly set.  

Here is what I have for information thus far.  When I go to **System - Administration - Hardware Drivers** it finds that I have already installed the proprietary NVIDIA drivers version 96 and that the driver is activated and currently in use.  I did in fact previously download an install those drivers as recommended.  




However, I then  opened the **System -Administration -NVIDIA X Server Settings** and got the message:

[B]You do not appear to be using the NVIDIA X Driver.
Please edit your X configuration file. (just run 'nvidia-xconfig'
as root, and restart the X server.[/B]  
When I do as the above message suggests I get:


[B]mike@ubuntustudio:~$ sudo nvidia-xconfig
[sudo] password for mike:

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'[/B]
[B]
UPDATE. [/B]  I just un-installed and did a re-install of suggested NVIDIA driver 96 and it turns out that the driver did not install correctly and was never being used in my system. The file at var/log/jockey.log shows that the driver did not install.   I need a different way to install the driver for this card.  


Any suggestions?

---

### Post by windeguy on 2010-11-08
I figured out why the NVIDIA preferred driver would not install.  I had been using a real time Kernel on my desktop that was recommended for my laptop.  That kernel did not have the proper files needed to install the NVIDIA driver and I did not know how to get those files if in fact they were available.  

So, I downloaded the -11-rt Kernel using Synaptic, and then I downloaded the NVIDIA driver and it properly installed. 

Now I am getting some offload of the CPU by the graphics card. I think the system is usable, but not really quick with respect to the graphics.

---

### Post by bluesscream on 2010-11-08
did you try nvidia's  100.14.11?

---

