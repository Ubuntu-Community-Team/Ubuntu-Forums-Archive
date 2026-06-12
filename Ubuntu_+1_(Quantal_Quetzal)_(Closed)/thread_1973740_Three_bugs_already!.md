---
title: "Three bugs already!"
date: 2012-05-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-05-05
Just upgraded another system ..and got these...

---

### Post by pressureman on 2012-05-05
Three bugs already, and we haven't even hit the first alpha?! This is outrageous! Somebody should call Mr Shuttleworth right now.

---

### Post by Docaltmed on 2012-05-05
That's it. I'm leaving Ubuntu.

---

### Post by ventrical on 2012-05-05
I think the wheels have come off on this one machine . I can't get grub to recognize the new 3.4 kernel. It will only recognize the 3.2s. I have 4 installs on a 1/2TBSATA. 2 Quantals, 1 precise and 1 Maveric.

---

### Post by effenberg0x0 on 2012-05-05
> **ventrical said:**
> I think the wheels have come off on this one machine . I can't get grub to recognize the new 3.4 kernel. It will only recognize the 3.2s. I have 4 installs on a 1/2TBSATA. 2 Quantals, 1 precise and 1 Maveric.

I found 3.2.0-23 #36 to be more stable for me so far. I can't get past boot on 3.4, one oops after the other. I thought it was my overclock (recently increased it a little), but it was not. It's OK at this stage of development anyway.

Regards,
Effenberg

---

### Post by ventrical on 2012-05-05
> **effenberg0x0 said:**
> I found 3.2.0-23 #36 to be more stable for me so far. I can't get past boot on 3.4, one oops after the other. I thought it was my overclock (recently increased it a little), but it was not. It's OK at this stage of development anyway.

Regards,
Effenberg

Thanks for your reply. I was just  posting this as I was also replying to your topic about Nvidia drivers in another forum and I thought I had the most recent kernel installed. It DID download and *install* but it just will not register in GRub. My point being I did not want to make a wrong assumption about the nVidia graphics problems, which I did , but have corrected that.

---

### Post by ventrical on 2012-05-05
> **pressureman said:**
> Three bugs already, and we haven't even hit the first alpha?! This is outrageous! Somebody should call Mr Shuttleworth right now.

:)

---

### Post by ronacc on 2012-05-05
the 3.4 kernel is up and running fine on my amd64/nvidia box , I do not have the xorg-edgers PPA ( or any other one ) added so Nvidia-current won't build yet but thats OK I can live with 1024X768 for awhile :lolflag:

---

### Post by ventrical on 2012-05-05
> **ronacc said:**
> the 3.4 kernel is up and running fine on my amd64/nvidia box , I do not have the xorg-edgers PPA ( or any other one ) added so Nvidia-current won't build yet but thats OK I can live with 1024X768 for awhile :lolflag:

  I don't know what happened here Ronacc .  The updates updated to the 3.4 kernel (no ppas) but they  are not in the GRUb menu, I tried <sudo update-grub> on all 4 installs on that system, but those kernels will just not show up.

Otherwise they are working  fine , Oh yes .. there is one ppa on one install on the same system when I was testing a 3.3rc for PRecise but I do  not think that would inhibit Grub from registering the 3.4 kernels  on those two installs. This is, of course, a multi-boot system.


```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-19-generic
Found initrd image: /boot/initrd.img-3.2.0-19-generic
Found linux image: /boot/vmlinuz-3.2.0-18-generic
Found initrd image: /boot/initrd.img-3.2.0-18-generic
Found linux image: /boot/vmlinuz-3.2.0-17-generic
Found initrd image: /boot/initrd.img-3.2.0-17-generic
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found linux image: /boot/vmlinuz-3.0.0-11-generic
Found initrd image: /boot/initrd.img-3.0.0-11-generic
Found linux image: /boot/vmlinuz-3.0.0-10-generic
Found initrd image: /boot/initrd.img-3.0.0-10-generic
Found linux image: /boot/vmlinuz-3.0.0-9-generic
Found initrd image: /boot/initrd.img-3.0.0-9-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
Found Ubuntu quantal (development branch) (12.10) on /dev/sda10
Found Ubuntu precise (development branch) (12.04) on /dev/sda8
done

```

---

### Post by fjgaude on 2012-05-05
No issues with grub and kernel 3.4:

```
frank@cutie:~$ sudo update-grub
[sudo] password for frank: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.4.0-1-generic
Found initrd image: /boot/initrd.img-3.4.0-1-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04 LTS (12.04) on /dev/sda1
Found Ubuntu 11.10 (11.10) on /dev/sda2
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb1
done
```

Of course my Intel graphics may make it easier than ATI or nvidia.

Are you not booting from sda10? No.

---

### Post by ronacc on 2012-05-05
@ ventrical  check your /boot and see if all parts of the 3.4 kernel are there . abi , config , initrid , system map and vmlinuz . if they are try adding a stanza for it to /boot/grub/grub.cfg using gedit ( bad practice but it works ) you can just copy the stanza for one of the 3.2 kernels and paste it in and change the 3.2... instances to 3.4 ...   .

---

### Post by jerrylamos on 2012-05-05
3.4 took several passes at updating and booting alternately with precise before it finally would run.  Screen turned black and flat screen monitor went to sleep.  Unclear why it is running now, if it is not broken can't fix it.

That's quantal unity-2D.  This is quantal lubuntu, and is still stuck at 3.2.0-24.  I don't know when/if 3.4 would be available for lubuntu.  Do note this is generic no pae flag which might have something to do with it.

Jerry

Woops, who's on first.  I do have a precise lubuntu which did update to 3.4 in another partitiion on the same pc as the 3.2.0-24 quantal lubuntu, both at generic no pae.
It's a Thinkpad T40 with Lynx, Ocelot, Pangolin, Quetzal if I can remember which one is booted at the moment....

---

### Post by ronacc on 2012-05-05
jerry you may have hit on it . I was already setup for gnome (gs) when I installed the 3.4 kernel so it failsafed to gnome ( non-gs ) without the nvidia driver .

---

### Post by ventrical on 2012-05-05
> **ronacc said:**
> @ ventrical  check your /boot and see if all parts of the 3.4 kernel are there . abi , config , initrid , system map and vmlinuz . if they are try adding a stanza for it to /boot/grub/grub.cfg using gedit ( bad practice but it works ) you can just copy the stanza for one of the 3.2 kernels and paste it in and change the 3.2... instances to 3.4 ...   .


Ok .. I'll try that .. but I am wondering if this may have something to do with it:

linux-headers-3.3.0-030300rc1_3.3.0-030300rc1.201201191835_all.deb
linux-headers-3.3.0-030300rc1-generic-pae_3.3.0-030300rc1.201201191835_i386.deb
linux-image-3.3.0-030300rc1-generic-pae_3.3.0-030300rc1.201201191835_i386.deb


 I have that in my download directory and that is at the top of the stack on GRUB .. yet 3.2.0-24 loaded just fine. I'm just wondering how to get rid of those from GRub.

---

### Post by ventrical on 2012-05-05
@ronacc,

 Ther is no such kernel in that directory yet here is synaptic history:

---

### Post by ronacc on 2012-05-05
to get rid of that from grub delete all 4 parts ( abi , config , initrid , system map and vmlinuz) from /boot and then update grub . if you can get to a gui go to aditional drivers and deactivate your proprietary driver ,then reboot and reinstall the 3.4 kernel , I think that should work , anyway I hope it don't nuke your sys .

---

### Post by ventrical on 2012-05-05
> **ronacc said:**
> to get rid of that from grub delete all 4 parts ( abi , config , initrid , system map and vmlinuz) from /boot and then update grub . if you can get to a gui go to aditional drivers and deactivate your proprietary driver ,then reboot and reinstall the 3.4 kernel , I think that should work , anyway I hope it don't nuke your sys .


Did all that ... but the entries are still in the GRub Menu. System not nuked yet. Gonna keep trying here.

---

### Post by ventrical on 2012-05-05
@ronacc,

 Ok .. I was able to get the 3.4.n-n kernel up in Grub. Major problems with NVidia. Will not let me in and forces me to 800x600 mode.

Edit .. btw .. the 3.2.0-24 kernel works just fine.

---

### Post by ronacc on 2012-05-05
yeah the nvidia driver isn't building without the xorg-edgers PPA . I'm stuck in low res also since I don't have any PPA's added at this stage of the game , I was able to go to displays and coax 1024x768 out of it .

---

### Post by ventrical on 2012-05-05
I have two QQ installs on the same system so I'll try installing the ppa on one of them later. The other I'll wait for the repos. I have that kernel working great with Intel based graphics.

Thanks for all of your help ronacc.

---

### Post by effenberg0x0 on 2012-05-05
@ronacc, ventrical
I was wondering if maybe the old IgnoreABI trick could help at this point. You know it:
```

sudo nano /etc/X11/xorg.conf

Section "ServerFlags"
Option "IgnoreABI" "true"
EndSection
```
Did you give it a try?

The desktops I'm testing won't boot with this kernel. It doesn't look like a video issue (it says something about wrong names for each the cores and reboots, very fast).

Regards,
Effenberg

---

### Post by ronacc on 2012-05-05
Thanks for the sugestion but no help on the nvidia driver , it did let me bump the res with nouveau up to 1280x1024 .

---

### Post by effenberg0x0 on 2012-05-05
> **ronacc said:**
> Thanks for the sugestion but no help on the nvidia driver , it did let me bump the res with nouveau up to 1280x1024 .

Maybe you can improve things with a custom xorg.conf?

I'd really like to use Open Source drivers and don't have to care about rebuilding the kernel module manually at kernel updates, etc. I haven't used Nouveau for a long while: It used to keep my GPU/VGAmem frequency always on an overclocked state. Temps and, thus, fans wen't crazy and noisy. And the FPS was cut in half (which I guess is probably related more to Mesa at that point). How is it performing nowadays in your opinion?

Regards,
Effenberg

---

### Post by ventrical on 2012-05-06
Here is what I get with the 3.4.n-n kernel.

---

### Post by ventrical on 2012-05-06
> **effenberg0x0 said:**
> @ronacc, ventrical
I was wondering if maybe the old IgnoreABI trick could help at this point. You know it:
```

sudo nano /etc/X11/xorg.conf

Section "ServerFlags"
Option "IgnoreABI" "true"
EndSection
```Did you give it a try?

The desktops I'm testing won't boot with this kernel. It doesn't look like a video issue (it says something about wrong names for each the cores and reboots, very fast).

Regards,
Effenberg

No , didn't work.

 Here is what I get from jockey.log:

HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-05-06 01:47:41,976 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-06 01:47:41,977 WARNING: /sys/module/nvidia_current/drivers does not exist, cannot rebind nvidia_current driver

---

### Post by effenberg0x0 on 2012-05-06
> **ventrical said:**
> No , didn't work.

 Here is what I get from jockey.log:

HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-05-06 01:47:41,976 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-06 01:47:41,977 WARNING: /sys/module/nvidia_current/drivers does not exist, cannot rebind nvidia_current driver

I know what this is, I think I can help. I had this exact symptom sometime during Precise and couldn't find a viable explanation for it for a while. Until I checked which modules were effectively loaded (lsmod) and couldn't find NVidia module. I had just installed NVidia, it was impossible for the module to not be loaded.

After some searching, I found out that /etc/modprobe.d/nvidia-something.conf (can't remember the exact name) I had nvidia set as an **alias**, pointing to **nvidia_current**. But, of course, I had no module named nvidia_current. It made no sense, I was using the proprietary-installer drivers, not nvidia-current* packages.

So, every time I tried to manually load NVidia kernel module (like sudo modprobe nvidia, for example) I received an error saying that module nvidia_current didn't exist. modinfo nvidia would show me nvidia.ko normally installed and no module names nvidia-current.ko. Of course that was also happening during boot.

As soon as I commented out that alias and tried to manually load the nvidia module, it worked normally. And so it did after booting. I don't know what adds that alias there, I'm not used to installing nvidia-current* packages from repos. But anyway, search and you'll find this alias.

If I'm right, as soon as you disable/remove it, you'll have nvidia working normally again. Also, make sure nouveau is blacklisted if you don't want to use it.  At this point, you'll at least have the proper module able to be loaded. Now, how it works or not with this kernel, that is unsure for me.

Regards,
Effenberg

---

### Post by ventrical on 2012-05-06
So how would I comment this out?

# This file was installed by nvidia-current
# Do not edit this file manually

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current
alias nouveau off
alias lbm-nouveau off

---

### Post by effenberg0x0 on 2012-05-06
> **ventrical said:**
> So how would I comment this out?

# This file was installed by nvidia-current
# Do not edit this file manually

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current
alias nouveau off
alias lbm-nouveau off

There it is... Add a single '#' to the nvidia_current line. The end result will be:
```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
#alias nvidia nvidia_current
alias nouveau off
alias lbm-nouveau off
```

Then, if you have a nvidia.ko (which you can check with sudo modinfo nvidia) it will at least have a chance of being properly loaded at boot. 
```
sudo modinfo nvidia
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/video/nvidia.ko
alias:          char-major-195-*
version:        295.20
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.2.0-23-generic SMP mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int

```
If you don't, just run the proprietary installer again so it can build and load the module. Now without this alias, the module will load normally. Remember to wipe your current /etc/X11/xorg.conf (otherwise, in some cases, X might load with unneeded/wrong settings). You can also run nvidia-xconfig to set /etc/X11/xorg.conf.

Regards,
Effenberg

---

### Post by ronacc on 2012-05-06
a custom xorg wouldn't have helped because the driver wouldn't build so no nvidia.ko . I had bugged it yesterday and my bug was duped to another one which contained a workaround , basicly there are missing header files for most archs . see [ https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506 ]( https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506 ) . for the workaround , it worked for me .

---

### Post by ventrical on 2012-05-06
> **ronacc said:**
> a custom xorg wouldn't have helped because the driver wouldn't build so no nvidia.ko . I had bugged it yesterday and my bug was duped to another one which contained a workaround , basicly there are missing header files for most archs . see [ https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506 ]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506") . for the workaround , it worked for me .


Hi Ronacc,

What directory do we get that system.h file from?

Thanks in advance..

---

### Post by ventrical on 2012-05-06
> **effenberg0x0 said:**
> There it is... Add a single '#' to the nvidia_current line. The end result will be:
```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
#alias nvidia nvidia_current
alias nouveau off
alias lbm-nouveau off
```Then, if you have a nvidia.ko (which you can check with sudo modinfo nvidia) it will at least have a chance of being properly loaded at boot. 
```
sudo modinfo nvidia
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/video/nvidia.ko
alias:          char-major-195-*
version:        295.20
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.2.0-23-generic SMP mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int

```If you don't, just run the proprietary installer again so it can build and load the module. Now without this alias, the module will load normally. Remember to wipe your current /etc/X11/xorg.conf (otherwise, in some cases, X might load with unneeded/wrong settings). You can also run nvidia-xconfig to set /etc/X11/xorg.conf.

Regards,
Effenberg


Thanks effenberg.  I tried that but it didn't work.

dale@dale-desktop:~$ sudo modprobe nvidia
[sudo] password for dale: 
FATAL: Module nvidia not found.

---

### Post by effenberg0x0 on 2012-05-06
> **ventrical said:**
> Thanks effenberg.  I tried that but it didn't work.

dale@dale-desktop:~$ sudo modprobe nvidia
[sudo] password for dale: 
FATAL: Module nvidia not found.

The only way to understand this is to perform tests and go deeper into the bug. Your error was:
> **ventrical said:**
>  nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

Do you have a module for nvidia_current? 
```
ls -la /lib/modules/`uname -r`/updates/dkms/nvidia_current.ko
locate nvidia_current.ko
```
If so, that alias makes sense, should be there and active. But the error you reported pointed out you did not have it. SO I'll guess that's not the case.

Do you have a module for nvidia (nvidia driver installed by the proprietary installer):
```
ls -la /lib/modules/`uname -r`/kernel/drivers/video/nvidia*
locate nvidia.ko
```

If you don't have any NVidia kernel module, you need to re-install nvidia, either from repos or the proprietary installer. I suggest the proprietary installer, as it scans and fixes missing files/symlinks too.

If you do have at least one nvidia module in the system, do you have it currently loaded?
```
lsmod | grep "nvidia*"
```

If not, can you successfully load a nvidia module manually?
```
sudo modprobe nvidia
```
or
```
sudo modprobe nvidia_current
```

And check again with
```
lsmod | grep "nvidia*"
```

Also, look at messages immediately after loading the kernel module, to see if it loaded with no errors:
```
dmesg
```
If a proper nvidia module is loaded and you restart lightdm...
```
Ctrl+Alt+F6
sudo service lightdm stop
sudo service lightdm start

```
...and run nvidia-settings, can you improve / configure the display? Or does it tell you that you have no nvidia module/drivers in use in a pop-up immediately when you start it?

If not: When you look at /etc/X11/xorg.conf, is it by any chance wrong, not loading nvidia as the driver for device 0? Are modes for the current display wrong? Maybe the server layout is broken? In any of these case, removing /etc/X11/xorg.conf, running nvidia-xconfig and restarting lightdm, running nvidia-settings again improved things?

If not: Do you have NVidia OpenGL drivers in /usr/lib and /usr/lib32? Are symlinks by any chance broken (pointing to non-existing files)?
```
ls -la /usr/lib*/*GL*
```

If you don't have such drivers, a reinstall of either nvidia_current or nvidia proprietary drivers should be performed. I suggest the proprietary installer, as it scans and fixes missing files/symlinks too.

Regards,
Effenberg

PS: The procedure to install NVidia using the proprietary installer:

- Download the installer from NVidia. I suggest trying version **295.20**.

**For 32-Bit:**
```
cd && cd Downloads
wget download.nvidia.com/XFree86/Linux-x86/295.20/NVIDIA-Linux-x86-295.20.run
```

**For 64-Bit:**
```
cd && cd Downloads
wget download.nvidia.com/XFree86/Linux-x86_64/295.20/NVIDIA-Linux-x86_64-295.20.run
```

- Make the installer executable:
```
sudo chmod +x NVIDIA-Linux*295.20.run
```

- Switch to a VT and stop lightdm:
```
Ctrl+Atl+F6
sudo service lightdm stop
```

- Run the installer:
```
cd && cd Downloads
sudo ./NVIDIA-Linux*295.20.run
```

**Answer yes to everything the installer proposes.** Only exception: If a message saying you have a **different version of GCC** installed, ignore it, select "no" to proceed with the install. Yes to all other questions.

- Restart lightdm
```
sudo service lightdm start
```

- Go to the Dash/Nvidia-Settings. Try to improve/customize settings.

---

### Post by ronacc on 2012-05-06
> **ventrical said:**
> Hi Ronacc,

What directory do we get that system.h file from?

Thanks in advance..

here is the workaround from the link I posted . ```
Workaround:
 Copy the missing header files from arm

cd /usr/src/linux-headers-3.4.0-1/arch
 sudo cp arm/include/asm/system.h x86/include/asm/
 sudo cp arm/include/asm/compiler.h x86/include/asm/
 sudo cp arm/include/asm/system_info.h x86/include/asm/
 sudo cp arm/include/asm/system_misc.h x86/include/asm/

and then reinstall the kernel. 
``` just  copy and paste each line one at a time into a terminal . 

I tried this and it worked for me . I do not claim credit for this , the one who submitted that bug report is the one who gets the credit .

what the cmds do is batch copy the header files from /usr/src/linux-headers-3.4.0-1/arch/arm/include/asm/      TO     /usr/src/linux-headers-3.4.0-1/arch/x86/include/asm/  .

---

### Post by ventrical on 2012-05-07
Thanks Ronacc,

I tried this and it did nothing on this PC. I am going to remove the kernel and try installing it again. If that doesn't work I'll try effenbergs suggestion...

thanks again..

---

### Post by ventrical on 2012-05-07
Tried again on another install of Quantal on the same system. At least I was able to report one of bug so far.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/995962](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/995962)

 Now why that popped up during the 3.4.n-n kernel install with the Nvidia card .. I have no idea. 

It does have an onboard ATI graphics but I have AGP nvidia enabled. Mabey there is a conflict and this may be the problem.

EDIT .. ok I was also able to squeeze out  a nvidia bug report:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/995970](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/995970)

---

### Post by ventrical on 2012-05-07
Now I am perplexed.

Installing the kernel 3.4.0-1.2 fails to build the nvidia-current module due to missing kernel header files.

any idea what I did or did not do?

---

### Post by ventrical on 2012-05-07
@effenberg

cd && cd Downloads sudo ./NVIDIA-Linux*295.20.run

I did this to a 'tee' and the installer failed completely. Could not capture the several error messages.

I'll try a purge/ reinstall later on.

---

### Post by ronacc on 2012-05-07
> **ventrical said:**
> Now I am perplexed.

Installing the kernel 3.4.0-1.2 fails to build the nvidia-current module due to missing kernel header files.

any idea what I did or did not do?

attached is an SS of my /usr/src/linux-headders-3.4.0-1-generic/arc/x86/include/asm folder check yours and see if it looks like that ( note it runs way off the bottom of the SS ) . if not the copy oreration I posted previously didn't work for some reason .

---

### Post by ventrical on 2012-05-07
I got pretty well the exact same thing .. but I can't make it smaller because I have no control over resolution of screen.

---

### Post by ventrical on 2012-05-07
I removed nvidia-current, got resolution control back but no Unity 3D. It auto fell-back to 2D.

---

### Post by ventrical on 2012-05-07
> **ronacc said:**
> here is the workaround from the link I posted . [code]Workaround:
 Copy the missing header files from arm

cd /usr/src/linux-headers-3.4.0-1/arch
 sudo cp arm/include/asm/system.h x86/include/asm/
 sudo cp arm/include/asm/compiler.h x86/include/asm/
 sudo cp arm/include/asm/system_info.h x86/include/asm/
 sudo cp arm/include/asm/system_misc.h x86/include/asm/

and then reinstall the kernel. .

I am not sure what you mean by "reinstall the kernel" It may be here where I messed up.

---

### Post by ronacc on 2012-05-07
> **ventrical said:**
> I am not sure what you mean by "reinstall the kernel" It may be here where I messed up.

after I copied the header files I went to synaptic and marked this file for reinstallation linux-image-3.4.0-1-generic (3.4.0-1.3)  . then I rebooted and had a working nvidia driver ( nvidia-current  295.49 ) note I have NO PPA's so my xserver is 1.11.3  . none of this may work with the xorg-edgers stuff , of course that should work with out all this monkey motion .

---

### Post by ventrical on 2012-05-07
WoW!!  Finally got it working! I tried the formula you posted the first time and it did not work but I think I installed the kernel  wrong. I had a 'black-screen' for a while but used recovery from GRub, then sysfck. This time I reinstalled  the nvidia-current again and I didn't get any errors and now I have full graphics back. Bacially I did what you suggested all over again - and it's working great for now ! Thanks again :)

...just an edit side note... these problems are really touchy at times..

---

### Post by ronacc on 2012-05-07
graphics problems can make you tear your hair out . you should install MC on first boot ( its in the repos ) that way if you black screen you can atleast get to a basic (very) file manager that runs from console ( much like the old msdos norton commander ) . it makes it easier and faster searching through folders moving files and even doing basic editing of scripts .

---

### Post by ventrical on 2012-05-07
> **ronacc said:**
> graphics problems can make you tear your hair out . you should install MC on first boot ( its in the repos ) that way if you black screen you can atleast get to a basic (very) file manager that runs from console ( much like the old msdos norton commander ) . it makes it easier and faster searching through folders moving files and even doing basic editing of scripts .

24 years of msdos ... it kinda grows on ya :)  I'll be sure to check out Midnight Commander.:)  Thanks again. I'll keep an eye on all of this  as things develop.

---

### Post by ventrical on 2012-05-08
> **ronacc said:**
> graphics problems can make you tear your hair out . you should install MC on first boot ( its in the repos ) that way if you black screen you can atleast get to a basic (very) file manager that runs from console ( much like the old msdos norton commander ) . it makes it easier and faster searching through folders moving files and even doing basic editing of scripts .

That little program is just what the doctor ordered.!! Works beautiful off the QQ iso. I never knew they had something like that that worked from terminal. Thank again Ronacc.

---

### Post by ronacc on 2012-05-08
glad you find it usefull , I stumbled across years ago and it has been a first boot install ever since . They kinda keep it a secret I found it while searching through synaptic for alternative file managers to play with :p

---

### Post by effenberg0x0 on 2012-05-08
MC is great, even in DOS :)
Just a note: On the desktop, you might find gnome-commander or tuxcmd to be a better option visually. I use MC on console in tuxcmd on GUI.

Regards,
Effenberg

---

### Post by ventrical on 2012-05-09
> **effenberg0x0 said:**
> MC is great, even in DOS :)
Just a note: On the desktop, you might find gnome-commander or tuxcmd to be a better option visually. I use MC on console in tuxcmd on GUI.

Regards,
Effenberg

Thanks effenberg. Appreciate that. MC on the console  is just great.  Now I can see what the heck you guys are talking about when you  re referring to the directory structure. Makes it a lot more clear for me. I think that should be a 'tool'  included in the tools section of the testers wiki.

---

### Post by effenberg0x0 on 2012-05-09
> **ventrical said:**
> Thanks effenberg. Apperciate that. MC on the console  is just great.  Now I can see what the heck you guys are talking about when you  re referring to the directory structure. Makes it a lot more clear for me. I think that should be a 'tool'  included in the tools section of the testers wiki.

It's great that it helped you visualize the "tree" better. Since the subject is somewhat about tools that may help when you're at console, check out Byobu. You use to split a terminal, more or less like you can do with a terminal in GUI. 

There's a screenshot [here]("http://3.bp.blogspot.com/-jDtEiVBdwAo/TyGc94NQYVI/AAAAAAAAE2s/sOwaBSE9Jnw/s1600/Screenshot+at+2012-01-26+12:23:59.png").

Regards,
Effenberg

---

