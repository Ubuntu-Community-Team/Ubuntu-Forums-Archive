---
title: "Unable to use a discrete GPU on a laptop, vgargb: this pci device is not a vga device"
date: 2016-03-18
forum: Ubuntu Development Version
---

### Post by mnox on 2016-03-18
I've installed Ubuntu Gnome 16.04 beta on a brand new laptop because I couldn't get 15.10 live cd to boot on it no matter what I did.
16.04 booted (with nomodeset) and installed just fine. It also asked me to disable Secure Boot, so that proprietary drivers could run, which I did.

My previous (and now dead) laptop used Nvidia's Optimus, too, so I know how to handle most of the problems that come with it. However, the problem I'm getting with 16.04 is completely different and I'm not even sure if this is the right forum to ask for help.

Whenever I boot Ubuntu Gnome, I get a black screen. I read through all the logs and it seems that this time the problem is not with the x server, but with the proprietary driver or maybe even the kernel. Here's a screenshot of the kernel log:
[https://drive.google.com/file/d/0B9GqACYn0ETzejl5QWszSUpVUEU/view?usp=sharing](https://drive.google.com/file/d/0B9GqACYn0ETzejl5QWszSUpVUEU/view?usp=sharing)
It seems that nvidia-modeset allocates and immediately frees the GPU, which is then followed by "vgargb: this pci device is not a vga device" message.

My laptop is Lenovo Z70 with Nvidia 840M discrete GPU. If I purge all the Nvidia stuff (drivers, cuda, prime), it boots to desktop just fine using Intel drivers.
Problem is, I ABSOLUTELY NEED a Linux system with cuda and recent OpenGL (4.3+) support to work on my master's thesis. 
I don't care about the Intel card at all. I just want to set the discrete one as the default using nvidia-prime (just like in my old laptop) and forget about it.

I also checked if it's possible to turn off the Intel card altogether from BIOS and the answer is no - I can only disable the discrete one.
Finally, the Nvidia GPU itself is fine. The laptop came with Windows 10 and it works there without any problems.

Any help would be appreciated.

---

### Post by aljosa2 on 2016-03-18
Hi, have you tried Ubuntu instead of Ubuntu Gnome?
Currently I'm running Ubuntu alongside Windows 10 - no problems with optimus *(Lenovo Y700-17ISK)* whether I want to use Intel or Nvidia.
Here are my BIOS settings:
- switchable graphics
- fast boot disabled
- intel platform trust technology disabled

My practise: after clean installation and full system update, Nvidia driver installation via additional drivers *(for my Lenovo nvidia 960m and other two Asus notebooks N750JV and X750JN with Nvidia 750M and 840m, current Nvidia driver is 361.28 and everything works ok)*.

---

### Post by aljosa2 on 2016-03-18
By the way, here are the two options if you want to install fresh Xenial: current and pending.
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
I installed latest pending few days ago.

---

### Post by mnox on 2016-03-19
Thanks aljosa2. As you have suggested, I downloaded and installed Ubuntu instead of Ubuntu Gnome. 
While I still get that strange *"vgargb: this pci device is not a vga device"* message in the kernel log, which I've never seen before, the **discrete card works fine now**.

How do I notify Ubuntu Gnome team of this problem?

Moreover, should I mark this thread as solved? To me it doesn't matter all that much if I use Ubuntu or Ubuntu Gnome, so my problem is solved. 
However, the problem in Ubuntu Gnome persists and no workaround has been suggested for it.

---

### Post by aljosa2 on 2016-03-19
Check if you have the latest Lenovo BIOS installed in your notebook.
*BIOS Update released on 11/6/2015:*
*[http://support.lenovo.com/hr/hr/products/laptops-and-netbooks/lenovo-z-series-laptops/z70-80?beta=false](http://support.lenovo.com/hr/hr/products/laptops-and-netbooks/lenovo-z-series-laptops/z70-80?beta=false)*

You can also make one experiment: Inside 'Nvidia Prime' choose 'Intel' and restart computer, then inside BIOS reset all settings to 'default optimized' and see if something changes.

Open terminal and execute the 'ubuntu-bug linux' command and then follow the instructions.

---

### Post by fthx on 2016-03-19
I ran in the same bug.
From your workaround to use Ubuntu/Unity, I found a more convenient workaround : use lightdm as manager, not gdm.
It works to use Ub Gnome, waiting for a proper solution.

---

### Post by mnox on 2016-03-19
My laptop was already updated to latest BIOS when I bought it.

I used 'sudo prime-select intel' to change to the Intel card from tty. Afterwards, I could boot and log in without any problems.
I reset the BIOS settings, as aljosa2 suggested, then tried using the discrete card again. Still doesn't work.

Submitted a bug report to launchpad using 'ubuntu-bug linux': [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559576](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559576)

---

### Post by bozhidar2 on 2016-06-01
> **aljosa2 said:**
> Hi, have you tried Ubuntu instead of Ubuntu Gnome?
Currently I'm running Ubuntu alongside Windows 10 - no problems with optimus *(Lenovo Y700-17ISK)* whether I want to use Intel or Nvidia.
Here are my BIOS settings:
- switchable graphics
- fast boot disabled
- intel platform trust technology disabled

My practise: after clean installation and full system update, Nvidia driver installation via additional drivers *(for my Lenovo nvidia 960m and other two Asus notebooks N750JV and X750JN with Nvidia 750M and 840m, current Nvidia driver is 361.28 and everything works ok)*.

I have Y700 and I can't install the NVIDIA driver no matter what... after trying numerous of solutions I either get 1)Black Screen or 2)Stuck at login. Can you tell me where can I find more information about your set up? I would like to use my GTX 960 and also install Cuca.

Thanks,
bozhidar

---

### Post by aljosa2 on 2016-06-02
Hi bozhidar,
recently I've made a new clean installation of Ubuntu 16.04 and all went wrong while installing Nvidia driver via additional drivers (same problem on Asus notebook too)
Here's how I solved this annoying problem:

> sudo apt-get purge nvidia*
sudo apt autoremove
sudo reboot

> sudo apt update && sudo apt install -f
sudo apt upgrade
sudo apt dist-upgrade

BIOS settings:
- switchable graphics
- fast boot disabled
- intel platform trust technology disabled
- secure boot disabled

> sudo apt install nvidia-361 nvidia-settings nvidia-prime

By the way, something strange is happening on Lenovo website
[http://support.lenovo.com/hr/en/products/laptops-and-netbooks/ideapad-y-series-laptops/y700-17isk?tabName=Downloads&linkTrack=Mast:SubNav:Support:Drivers%20and%20Software|Drivers%20and%20Software&beta=false](http://support.lenovo.com/hr/en/products/laptops-and-netbooks/ideapad-y-series-laptops/y700-17isk?tabName=Downloads&linkTrack=Mast:SubNav:Support:Drivers%20and%20Software|Drivers%20and%20Software&beta=false)
already 10-15 days it is impossible to find any BIOS (update) file.

---

### Post by coffeecat on 2016-06-02
Xenial no longer in development - thread closed.

@bozhidar2, I notice you have posted on no fewer than three separate threads with the same problem. Please do not hijack others' threads, but start your own - you are more likely to get help that way. Also, please do not cross post. One thread per problem only.

---

