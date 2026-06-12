---
title: "Nvidia GTX980/970 makes installing Linux hard ..."
date: 2014-10-01
forum: Ubuntu Development Version
---

### Post by xeizoo on 2014-10-01
On one of my PC:s(my Windows-gaming box) I use a brand new Nvidia GTX980, I wanted to run Linux in dual boot because some things are better done in Linux. Unfortunately so is everything related to X a no go in both Ubuntu and Debian using the GTX980. Not even a live distro works. The proprietary Nvidia driver(343.22) probably works, but it is hard to install it when the screen is totally blank. Yes the cmd frame buffer don't work and modern distributions turns on the frame buffer very early in the boot stage, which means everything gets blank quite immediately, it's impossible to type any commands.

I guess I can solve the problem by switching back to an older card and install 343.22, and then I assume boot will work, but there must be a better solution without replacing hardware back and forth. Anyone?

---

### Post by oldfred on 2014-10-01
NVIDIA GeForce GTX 980: The Best GPU For Linux Gamers
[http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx980&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx980&num=1)

I had a much older nVidia (9600GT)and always had to use nomodeset to get to low level graphics or until I installed the nVidia driver from the repository. 

But I just installed to a new system with 14.04.1 with a somewhat older nVidia card (GT620) and it just booted without the nVidia driver.

So does nomodeset work or can you boot with open source driver?
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

The Phoronix site uses PPAs to get the latest drivers and support software. And often a very new kernel rather than the default as that may also be required.

        
 Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
New kernels ppa
xorg-edgers PPA
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)

---

### Post by xeizoo on 2014-10-01
Thanks Freddie! Sounds like good advice, I will try that!  :-)

---

### Post by oldfred on 2014-10-01
Looks like all the NVidia drivers are here with xorg-edgers for trusty & utopic:
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)

My Mom was the last one to call me freddie. :) And she's not been with us for 30 years. But if she called me Frederick I knew I was in trouble.

---

### Post by cariboo on 2014-10-02
I'm in the same boat, I have a GTX-750. None of the drivers in the repositories work, so I had to resort to the the drivers in the edgers-xorg ppa. They work great, with my dual monitor setup, but virtualbox has a problem with the version of X being used, so the virtualbox additions don't work.

---

