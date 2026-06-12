---
title: "Recent Update  brings back Nvidia big Screen"
date: 2012-06-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-02
As the title suggests, working about with zsyncing .iso files, re-boot and then, voila', the nVidia Big Screen bug on one of my main machines.:) lol

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

---

### Post by effenberg0x0 on 2012-06-04
Hi Ventrical, 

My guesses would be:
- Nouveau is being loaded because there's no nvidia-current or nvidia kernel modules.
- nvidia or nvidia-current are available, but these kernel modules were build for a previous kernel, with a different toolchain, and won't be loaded in the current one.

The only way I can think of to test/fix what's going on there:
- Use lsmod | grep nouveau, lsmod | grep nvidia to see what is loaded, if any;
- Use modinfo nvidia, modinfo nvidia-current, modinfo nouveau to see whats available and their versions.
- Try to manually load one of the available modules (stop lightdm service, modprobe <the module>, start lightdm service) to see if it fixes it. If so, investigate grub command line and /etc/modprobe.d.
- If a correct module is loaded and the problem persists, look into /etc/X11/xorg.conf and GL libs/.so.
- If no module is available, get proper kernel modules.

Regards,
Effenberg

---

### Post by pal1965 on 2012-06-04
..something about Optimus ??

---

### Post by effenberg0x0 on 2012-06-04
> **pal1965 said:**
> ..something about Optimus ??

Prime?

Regards,
Effenberg

---

### Post by pal1965 on 2012-06-04
Sorry! I made a mistake when reading  first post and understood badly

---

### Post by ventrical on 2012-06-04
> **effenberg0x0 said:**
> Hi Ventrical, 

My guesses would be:
- Nouveau is being loaded because there's no nvidia-current or nvidia kernel modules.
- nvidia or nvidia-current are available, but these kernel modules were build for a previous kernel, with a different toolchain, and won't be loaded in the current one.

The only way I can think of to test/fix what's going on there:
- Use lsmod | grep nouveau, lsmod | grep nvidia to see what is loaded, if any;
- Use modinfo nvidia, modinfo nvidia-current, modinfo nouveau to see whats available and their versions.
- Try to manually load one of the available modules (stop lightdm service, modprobe <the module>, start lightdm service) to see if it fixes it. If so, investigate grub command line and /etc/modprobe.d.
- If a correct module is loaded and the problem persists, look into /etc/X11/xorg.conf and GL libs/.so.
- If no module is available, get proper kernel modules.

Regards,
Effenberg

Thanks effenberg:

```
camel2@ubuntu:~$ modinfo nouveau
filename:       /lib/modules/3.4.0-3-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
license:        GPL and additional rights
description:    nVidia Riva/TNT/GeForce
author:         Stephane Marchesin
srcversion:     F5205F948001F0C008EAAA0
alias:          pci:v000012D2d*sv*sd*bc03sc*i*
alias:          pci:v000010DEd*sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,ttm,mxm-wmi,wmi,video,i2c-algo-bit
intree:         Y
vermagic:       3.4.0-3-generic SMP mod_unload modversions 686 
parm:           agpmode:AGP mode (0 to disable AGP) (int)
parm:           modeset:Enable kernel modesetting (int)
parm:           vbios:Override default VBIOS location (charp)
parm:           vram_pushbuf:Force DMA push buffers to be in VRAM (int)
parm:           vram_notify:Force DMA notifiers to be in VRAM (int)
parm:           vram_type:Override detected VRAM type (charp)
parm:           duallink:Allow dual-link TMDS (>=GeForce 8) (int)
parm:           uscript_lvds:LVDS output script table ID (>=GeForce 8) (int)
parm:           uscript_tmds:TMDS output script table ID (>=GeForce 8) (int)
parm:           ignorelid:Ignore ACPI lid status (int)
parm:           noaccel:Disable all acceleration (int)
parm:           nofbaccel:Disable fbcon acceleration (int)
parm:           force_post:Force POST (int)
parm:           override_conntype:Ignore DCB connector type (int)
parm:           tv_disable:Disable TV-out detection (int)
parm:           tv_norm:Default TV norm.
        Supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J,
            hd480i, hd480p, hd576i, hd576p, hd720p, hd1080i.
        Default: PAL
        *NOTE* Ignored for cards with external TV encoders. (charp)
parm:           reg_debug:Register access debug bitmask:
        0x1 mc, 0x2 video, 0x4 fb, 0x8 extdev,
        0x10 crtc, 0x20 ramdac, 0x40 vgacrtc, 0x80 rmvio,
        0x100 vgaattr, 0x200 EVO (G80+) (int)
parm:           perflvl:Performance level (default: boot) (charp)
parm:           perflvl_wr:Allow perflvl changes (warning: dangerous!) (int)
parm:           msi:Enable MSI (default: off) (int)
parm:           ctxfw:Use external HUB/GPC ucode (fermi) (int)
parm:           mxmdcb:Santise DCB table according to MXM-SIS (int)
camel2@ubuntu:~$ modinfo nvidia-current
filename:       /lib/modules/3.4.0-3-generic/updates/dkms/nvidia_current.ko
alias:          char-major-195-*
version:        295.53
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.4.0-3-generic SMP mod_unload modversions 686 
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
camel2@ubuntu:~$ 

```

for some reason it just decided to start working with  3.4.0-3..  I'll keep my eye on it.

---

### Post by effenberg0x0 on 2012-06-04
> **ventrical said:**
> Thanks effenberg:

```
camel2@ubuntu:~$ modinfo nouveau
filename:       /lib/modules/3.4.0-3-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
license:        GPL and additional rights
description:    nVidia Riva/TNT/GeForce
author:         Stephane Marchesin
srcversion:     F5205F948001F0C008EAAA0
alias:          pci:v000012D2d*sv*sd*bc03sc*i*
alias:          pci:v000010DEd*sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,ttm,mxm-wmi,wmi,video,i2c-algo-bit
intree:         Y
vermagic:       3.4.0-3-generic SMP mod_unload modversions 686 
parm:           agpmode:AGP mode (0 to disable AGP) (int)
parm:           modeset:Enable kernel modesetting (int)
parm:           vbios:Override default VBIOS location (charp)
parm:           vram_pushbuf:Force DMA push buffers to be in VRAM (int)
parm:           vram_notify:Force DMA notifiers to be in VRAM (int)
parm:           vram_type:Override detected VRAM type (charp)
parm:           duallink:Allow dual-link TMDS (>=GeForce 8) (int)
parm:           uscript_lvds:LVDS output script table ID (>=GeForce 8) (int)
parm:           uscript_tmds:TMDS output script table ID (>=GeForce 8) (int)
parm:           ignorelid:Ignore ACPI lid status (int)
parm:           noaccel:Disable all acceleration (int)
parm:           nofbaccel:Disable fbcon acceleration (int)
parm:           force_post:Force POST (int)
parm:           override_conntype:Ignore DCB connector type (int)
parm:           tv_disable:Disable TV-out detection (int)
parm:           tv_norm:Default TV norm.
        Supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J,
            hd480i, hd480p, hd576i, hd576p, hd720p, hd1080i.
        Default: PAL
        *NOTE* Ignored for cards with external TV encoders. (charp)
parm:           reg_debug:Register access debug bitmask:
        0x1 mc, 0x2 video, 0x4 fb, 0x8 extdev,
        0x10 crtc, 0x20 ramdac, 0x40 vgacrtc, 0x80 rmvio,
        0x100 vgaattr, 0x200 EVO (G80+) (int)
parm:           perflvl:Performance level (default: boot) (charp)
parm:           perflvl_wr:Allow perflvl changes (warning: dangerous!) (int)
parm:           msi:Enable MSI (default: off) (int)
parm:           ctxfw:Use external HUB/GPC ucode (fermi) (int)
parm:           mxmdcb:Santise DCB table according to MXM-SIS (int)
camel2@ubuntu:~$ modinfo nvidia-current
filename:       /lib/modules/3.4.0-3-generic/updates/dkms/nvidia_current.ko
alias:          char-major-195-*
version:        295.53
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.4.0-3-generic SMP mod_unload modversions 686 
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
camel2@ubuntu:~$ 

```

for some reason it just decided to start working with  3.4.0-3..  I'll keep my eye on it.

Hey Ventrical,

Good. modinfo shows you have the right versions for both nouveau and nvidia-current kernel modules available for use in the 3.4.0-3 tree. So you can check which one is loaded and working right now with lsmod | grep nouveau and lsmod | grep -i nvidia. And you can experiment with both to see which works better there. I believe both will work (they do here, same versions and kernel).

Regards,
Effenberg

---

### Post by ventrical on 2012-06-04
camel2@ubuntu:~$ lsmod | grep nouveau
(nothing comes up here)


camel2@ubuntu:~$ lsmod | grep -i nvidia
nvidia              10979833  56 
camel2@ubuntu:~$

---

