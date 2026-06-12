---
title: "Won't boot after updating 14.04"
date: 2014-12-24
forum: Ubuntu Studio
---

### Post by corpius on 2014-12-24
Yesterday I installed Ubuntu Studio 14.04 for my musical needs :)

but... after installing the updates the OS won't boot anymore. I'm a novice user when it comes to linux, but I did some research and found that when going back to the kernel that came with the installation the OS boots normally. I think that the problem is related to the video driver, because when I select the AMD proprietary driver the OS does boot with the new low latency kernel ([COLOR=#333333][FONT=Ubuntu]3.13.0.43)[/FONT][/COLOR]. But it won't be able to go full screen, which is probably caused by the AMD proprietary driver.

Anywho I could need some help with getting the OS to boot with the latest updates and without using the AMD proprietary driver.

My system is based around the AMD/ATI Kabini 5350

---

### Post by oldfred on 2014-12-24
I do not know Studio, nor AMD.

But how did you install video driver and low latency kernel?
If not in dpkg or installed from Ubuntu repository you have to re-enable the integration of the video driver into the kernel.

        man mkinitramfs
sudo update-initramfs -u 
or this which is all kernels:
sudo update-initramfs -k all -c

---

### Post by corpius on 2014-12-29
> **oldfred said:**
> I do not know Studio, nor AMD.

But how did you install video driver and low latency kernel?
If not in dpkg or installed from Ubuntu repository you have to re-enable the integration of the video driver into the kernel.

        man mkinitramfs
sudo update-initramfs -u 
or this which is all kernels:
sudo update-initramfs -k all -c
Ubuntu studio has the low latency kernel by default. I didn't install videos driver and low latency kernel manually, I used the update manager. The kernel gets updated to version 3.13.0.43, because it's marked as security update. 

I tried re-enabling the integration of the video driver as you suggested, but without success. I noticed that the update manager also runs the same commands after installing the new kernel, so that could certainly not be the problem. Ubuntu studio only works after removing the new kernel and its dependencies. I think that there might be some compatibility problems with the new kernel and my hardware (AMD athlon 5350).

For now I'll make sure that I don't mark the new kernel for installation when updating the packages, but it would be nice to get it working with the new kernel.

---

