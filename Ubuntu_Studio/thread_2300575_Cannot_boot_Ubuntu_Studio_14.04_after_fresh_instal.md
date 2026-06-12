---
title: "Cannot boot Ubuntu Studio 14.04 after fresh install."
date: 2015-10-26
forum: Ubuntu Studio
---

### Post by sethanath2 on 2015-10-26
Hi,

I successfully installed Ubuntu Studio 14.04 on my laptop.
However, I could not boot after performing fresh install on my PC (ASUS A8N32-SLI Deluxe).
This PC has two video cards on it, which are "2GB GDDR5 EVGA GEFORCE GTX 750 Ti" and "Radeon HD5450 Core Edition".

The installation would go through successfully, but, during the first boot, it would just stop with the blinking cursor.

Can you help? I was not able to see Xfce Desktop no matter how long I left it there.

Thanks.

---

### Post by sethanath2 on 2015-10-26
Hi,

I forgot to mention that this same machine and video cards has been installed successfully with Linux Mint 17.1 and 17.2. 

Thank you.

---

### Post by sethanath2 on 2015-10-27
Hi,

I found some of the problem. I formatted the hard drive first before installing Ubuntu Studio this time. Afterward, I did fresh installation with Ubuntu Studio, and the installation was successful.
I think the problem that I had previously might come from gParted within Ubuntu Studio. It might not format my hard disk successfully during the installation.
I was able to use Xfce desktop through XOrg driver from the first boot, and performed many software update. 

However, here is the new problem. By changing from XOrg driver and using the proprietary driver instead, for [COLOR=#000000]"2GB GDDR5 EVGA GEFORCE GTX 750 Ti" graphic card, I was not able to use Xfce desktop again.
What I saw was the linux command prompt asking for my username and password.

Can you help? I need to be able to use the [/COLOR]proprietary driver with Xfce DE.

[COLOR=#000000]Thanks.
[/COLOR]

---

### Post by sethanath2 on 2015-11-02
> **sethanath2 said:**
> 

However, here is the new problem. By changing from XOrg driver and using the proprietary driver instead, for [COLOR=#000000]"2GB GDDR5 EVGA GEFORCE GTX 750 Ti" graphic card, I was not able to use Xfce desktop again.
What I saw was the linux command prompt asking for my username and password.

Can you help? I need to be able to use the [/COLOR]proprietary driver with Xfce DE.

[COLOR=#000000]Thanks.
[/COLOR]

The error message during boot is "MPU-401 device not found or device busy".

---

### Post by CrocoDuck on 2015-11-03
> **sethanath2 said:**
> 
I formatted the hard drive first before installing Ubuntu Studio this time.[COLOR=#000000]
[/COLOR]

Yeah, I always got that problem with the Ubuntu installer. For some reason, when you install over a pre-existing Linux installation, even if you act as re-making the partitions, the installer messes things up. I noticed it with 10.04 and since then I always prepare the partition first and then reboot to install ([this tool]("http://www.sysresccd.org/SystemRescueCd_Homepage") is cool, btw). Pretty weird it still happens though.

As for the video-card problem, my guess is that the lowlatency kernel does not like the proprietary drivers. I would guess that the standard Ubuntu kernel is updated more often and as such gets better compatibility for this sort of things. When you are dropped to the shell, log into your user and then install the standard one. This should do the job:

```
sudo apt-get install linux-headers-generic linux-image-generic
```

 You should be able to boot into it through GRUB at boot time. If not, this should fix it:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

See how it goes. lowlatency or realtime kernels are not necessary unless you need some low latency audio processing done. From your [other posts]("http://ubuntuforums.org/showthread.php?t=2300400") seems to me that you are more interested in playback, so latency is not an issue for you.

---

### Post by sethanath2 on 2015-11-04
Hi,

Thank you very much for your help. Those two commands that you mentioned do work.
Here are the other problems. I have to use grub menu in order to get into Xfce DE successfully, or I would end up with the same "Device not ready" problem.

These are the steps, I use.
1. During booting, I will need to keep hitting Esc button to use GRUB menu.
2. Choose "Advance options for Ubuntu".
3. I will see
[LIST]
[*]Ubuntu, with Linux 3.19.0-32-lowlatency 
[*]Ubuntu, with Linux 3.19.0-32-lowlatency (recovery mode) 
[*]Ubuntu, with Linux 3.19.0-32-generic 
[*]Ubuntu, with Linux 3.19.0-32-generic (recovery mode) 
[*].... 
[*].... 
[*].... 
[/LIST]
  Now, I will have to choose the forth option "Ubuntu, with Linux 3.19.0-32-generic (recovery mode)" and "resume     Resume normal boot" in order to get it to work.
The other options would not work for my computer.

Can you help me further?

Thanks.

---

### Post by CrocoDuck on 2015-11-05
> **sethanath2 said:**
> Now, I will have to choose the forth option "Ubuntu, with Linux 3.19.0-32-generic (recovery mode)" and "resume     Resume normal boot" in order to get it to work.
The other options would not work for my computer.


Uhm... I am surprised you have to resort to recovery mode to complete the boot. From [this page]("http://www.linuxmint.com/rel_rafaela_cinnamon_whatsnew.php") relative to Linux Mint 17.2, that you said you installed successfully, I can see that the kernel in use in that distro is at version 3.16. My guess at this point is that 3.19 is not a good friend of the video drivers. This might be either a kernel regression or the proprietary driver not able do keep up with the updates of the kernel. I am not sure about how straightforward is kernel regression in Ubuntu distros, I never did it. Have a look at [this]("https://wiki.ubuntu.com/Kernel/MainlineBuilds"), my suggestion is to try the 3.16 version as in Linux Mint. Alternatively, you could install an LTS version of Ubuntu and then the [Ubuntu Studio audio packages]("https://apps.ubuntu.com/cat/applications/ubuntustudio-audio/") on top of that. It should give you a cleaner system. Follow [this guide]("https://help.ubuntu.com/community/Grub2/Submenus") to edit default GRUB boot kernel and other parameters.

---

### Post by sethanath2 on 2015-11-06
> **CrocoDuck said:**
> Uhm... I am surprised you have to resort to recovery mode to complete the boot. From [this page]("http://www.linuxmint.com/rel_rafaela_cinnamon_whatsnew.php") relative to Linux Mint 17.2, that you said you installed successfully, I can see that the kernel in use in that distro is at version 3.16. My guess at this point is that 3.19 is not a good friend of the video drivers. This might be either a kernel regression or the proprietary driver not able do keep up with the updates of the kernel. I am not sure about how straightforward is kernel regression in Ubuntu distros, I never did it. Have a look at [this]("https://wiki.ubuntu.com/Kernel/MainlineBuilds"), my suggestion is to try the 3.16 version as in Linux Mint. Alternatively, you could install an LTS version of Ubuntu and then the [Ubuntu Studio audio packages]("https://apps.ubuntu.com/cat/applications/ubuntustudio-audio/") on top of that. It should give you a cleaner system. Follow [this guide]("https://help.ubuntu.com/community/Grub2/Submenus") to edit default GRUB boot kernel and other parameters.

Hi,

Thank you very much. I ended up installing "grub customizer" to make things easier.
I also modified grub menu to use the information below as the first defaulted option.

Please note that without this "nomodeset", I will need to keep using the recovery mode, so I ended up adding it.

recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  d514b6fc-2d46-4b86-9781-2ec54cb500d0
else
  search --no-floppy --fs-uuid --set=root d514b6fc-2d46-4b86-9781-2ec54cb500d0
fi
   
linux    /boot/vmlinuz-3.19.0-25-lowlatency root=UUID=d514b6fc-2d46-4b86-9781-2ec54cb500d0 ro  quiet nomodeset 
initrd    /boot/initrd.img-3.19.0-25-lowlatency

Everything works perfectly now.

---

### Post by CrocoDuck on 2015-11-06
Oh cool! Was just a thing of kernel options then, as I see [here]("http://ubuntuforums.org/showthread.php?t=1613132"). Nice!

---

### Post by sethanath2 on 2015-11-06
> **CrocoDuck said:**
> Oh cool! Was just a thing of kernel options then, as I see [here]("http://ubuntuforums.org/showthread.php?t=1613132"). Nice!

I still need to use lower kernel number, just like what you suggested, though.

Thanks.

---

