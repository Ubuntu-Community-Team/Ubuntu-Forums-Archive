---
title: "Unable to run virtual machine in 14.04"
date: 2014-06-27
forum: Virtualisation
---

### Post by RobertKH on 2014-06-27
I seem to be having a problem in getting virtual machines to work. I have actually never ran virtual box at home so maybe I am missing something obvious. I am continuously getting errors when trying to start a virtual box stating the kernel driver was not found and to run /etc/init.d/vboxdrv setup as root. I have tried this and I get an error that states ```
Trying to register the VirtualBox KMS kernel modules using DKMSError! Your kernel headers for kernel 3.5.0-27-generic cannot be found.
Please install the linux-headers-3.5.0-27generic package or use the --kernelsourcedir option to tell DKMS where it's located
...failed!
(failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
(Look at /var/log/vbox-install.log to find out what went wrong)
```

This log just says that it failed to instal using DKMS and when trying to Makefile:183 it was unable to find the sources of my current linux kernel. I can specify and run Make again. I have tried to install using ```
apt-get install linux-headers-3.5.0-27-generic
``` but I get an error that it cannot find any package by regex '.....' You get the gist. 

What am I missing here? Can anyone point me in the right direction?

uname -r results
3.5.0-27-generic

Edit: trying to correct spelling errors - virtualmachine is being run on my home server and trying to set it up via VNC viewer. For some reason I can't copy and paste right now.

---

### Post by RobertKH on 2014-06-27
Ok so maybe a little more information. In looking in my /usr/src/  directory I do not have (what I am assuming to be) the correct linux  headers. I have 3.13.0-27 and 3.13.0-27-generic -  the same for -29. My  question is now how do I get the correct headers. I am unsure of how to  do this. I checked synaptic (software center) for the correct headers  but it doesn't seem to have them.... what next?

---

### Post by DuckHook on 2014-06-27
I don't understand where or why you need to run *make*. Are you compiling VB from source? You do not need to go through the complexity of compiling if you are prepared to add the Oracle PPA to your software sources. This will allow you to install the latest version of VirtualBox straight from Oracle if you so wish. The only drawback is that you will be adding Oracle as a trusted source which is a security concern. It's up to you whether you trust a company as big as Oracle, but in any case, you are essentially taking on the same risk baking your own compilation.

Instructions for adding the PPA are [here]("https://www.virtualbox.org/wiki/Linux_Downloads").

As to your failure to get VB drivers compiling: Why are you running 14.04 using the 12.04.0 kernel? *uname* is telling you that your current kernel is 3.5.0-27, which makes no sense to me. If you upgraded from 12.04 to 14.04 instead of installing a fresh 14.04, you should still use the latest kernel which as of today's date is 3.11.0-23.

To see all of the kernels in your system, please do:```
dpkg --list | grep linux-image
```You may wish to clean up some of your old kernels. Instructions [here]("http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu"). When booting up, make sure you are booting up normally and not invoking the advanced boot option that allows you to select an older kernel. Even if you must select an older kernel for, say, HW compatibility, select an older 3.11, not 3.5.

Last but not least:

1. apt must be invoked with sudo.
2. always do "sudo apt-get update" before installing anything.

---

### Post by RobertKH on 2014-06-28
Gotcha - commands were from su so no sudo necessary. Ran sudo apt-get update multiple times during the process, I was just trying not to write an entire wall here for something that may have been a quick fix.

I will check out the cleaning up of old kernels. I hadn't thought of that.
I found what I was running to be odd as well. I did the upgrade from 12.10 -> 13.10 ->14.04 only a couple of months ago and never touched it since then. This is simply a file share on my network, but I wanted to start running some virtualization to do some testing. 

running the dpkg:

```
rc  linux-image-3.11.0-17-generic                         3.11.0-17.31                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-18-generic                         3.11.0-18.32                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-19-generic                         3.11.0-19.33                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-27-generic                         3.13.0-27.50                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-30-generic                         3.13.0-30.54                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-17-generic                          3.5.0-17.28                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-27-generic                          3.5.0-27.46                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-28-generic                          3.5.0-28.48                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-30-generic                          3.5.0-30.51                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-32-generic                          3.5.0-32.53                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-34-generic                          3.5.0-34.55                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-36-generic                          3.5.0-36.57                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-37-generic                          3.5.0-37.58                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-39-generic                          3.5.0-39.60                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-40-generic                          3.5.0-40.62                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-41-generic                          3.5.0-41.64                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-42-generic                          3.5.0-42.65                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-43-generic                          3.5.0-43.66                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-44-generic                          3.5.0-44.67                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-34-generic                          3.8.0-34.49                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-35-generic                          3.8.0-35.50                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-17-generic                   3.11.0-17.31                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-18-generic                   3.11.0-18.32                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic                   3.11.0-19.33                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-27-generic                   3.13.0-27.50                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                   3.13.0-30.54                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-17-generic                    3.5.0-17.28                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic                    3.5.0-27.46                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-28-generic                    3.5.0-28.48                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-30-generic                    3.5.0-30.51                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-32-generic                    3.5.0-32.53                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-34-generic                    3.5.0-34.55                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-36-generic                    3.5.0-36.57                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-37-generic                    3.5.0-37.58                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-39-generic                    3.5.0-39.60                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-40-generic                    3.5.0-40.62                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-41-generic                    3.5.0-41.64                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-42-generic                    3.5.0-42.65                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-43-generic                    3.5.0-43.66                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-44-generic                    3.5.0-44.67                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-34-generic                    3.8.0-34.49                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-35-generic                    3.8.0-35.50                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.30.36                                        amd64        Generic Linux kernel image
```

---

### Post by DuckHook on 2014-06-28
You need some significant kernel cleanup. I keep some old kernels around just in case, but no more than half-a-dozen. And even in such cases, I try to run my current OS on the kernel that it was designed for as much as I can, which &#8213; for all intents and purposes &#8213; is all of the time.

**CORRECTION** My previous post stated that 3.11.x is the latest kernel and this is incorrect. I am still running Ubuntu 13.10 on the machine I was posting from, and the 3.11.x series is the proper kernel for that version. However, for 14.04, the proper kernel is the 3.13.x series, which your query shows that you in fact have installed.

For your next step, make sure that you boot with the latest 3.13.x kernel and try installing VB again from the Oracle PPA. If it still fails, this time, copy and paste the full error messages back to this board. It is very difficult to help without complete and accurate info, so please provide complete reports.

---

### Post by RobertKH on 2014-06-28
My problem is that it is only displaying 3.5.0-27 and 3.5.0-17 as options to boot. I am not seeing the latest versions of my kernel. in Grub.

---

### Post by DuckHook on 2014-06-28
Please run:```
sudo update-grub
```

---

### Post by RobertKH on 2014-06-28
Ran it, found the 3.13 versions but still only have the 3.5 versions available at boot....

---

### Post by RobertKH on 2014-06-28
This is what I get when I run sudo update-grub

```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /vmlinuz-3.13.0-30-generic
Found initrd image: //initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /vmlinuz-3.13.0-29-generic
Found initrd image: //initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /vmlinuz-3.13.0-27-generic
Found initrd image: //initrd.img-3.13.0-27-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done


```

but for some reason it doesn't see these versions after restart when I try to boot into a newer kernel.

---

### Post by DuckHook on 2014-06-28
During boot, hold down the <Shift> key after POST. This should bring up multiple choice GRUB screen. Choose "Advanced options for Ubuntu". You should see all of your kernels available. Choose the latest kernel: 3.13.x  Allow boot to proceed normally and check using *uname* before trying to install VB.

---

### Post by RobertKH on 2014-06-28
No I get that. I did that and it is only displaying the 3.5 versions as stated previously. Seriously, I am following your steps to a T and getting nowhere....What else can I do? Can i purge the current version? Probably not until I can get it to boot into the newest version correct?

---

### Post by RobertKH on 2014-06-28
aha! I ran ```
sudo grub-install /dev/sda
``` and then ran ```
sudo update-grub
``` and it gave me the newer kernel versions at boot. Now I just have to go through and delete the old kernel versions and test out virtualbox again. BTW I found [this]("https://help.ubuntu.com/community/Grub2/Installing") very useful in this scenario.

---

### Post by DuckHook on 2014-06-29
Excellent!

In your case, please don't delete any old kernels until you've made sure that everything runs smoothly using the new kernel. Even then, keep one or two old kernels around, just in case. I would suggest that you keep a 3.11.x kernel at least. I personally think the 3.5 series to be too old, but some still keep them around for drivers that only work with the last LTS version of Ubuntu (12.04).

---

