---
title: "R730 - Tesla P100 installation"
date: 2023-08-06
forum: Server Platforms
---

### Post by cemdede on 2023-08-06
[COLOR=#000000][FONT=Roboto][COLOR=#111111]Hi,[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto][COLOR=#111111]I cannot make this one work:
I have Dell R730, which works on Ubuntu 22.04.3.
I used Riser 3 and added a P100.
I enabled BIOS GPU Legacy settings as well
[COLOR=#333333][FONT=&amp]I already enabled" Memory Mapped I/O above 4 GB” on BIOS settings.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I disabled “Embedded Video Controller” on BIOS settings[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]The card is plugged into slot 6 on Riser 3 with 8 pin cable ([/FONT][/COLOR][For DELL R730 8pin to 8pin Power Cable Nvidia K80/M40/M60/P40/P100 PCIE GPU @USA | eBay]("https://www.ebay.com/itm/274624139602")[COLOR=#333333][FONT=&amp]).[/FONT][/COLOR]
I used NVIDIA cuda developer website to download the driver and used
sudo sh cuda_12.2.1_535.86.10_linux.run --no-opengl-libs
in order to prevent from installing OPENGL libraries
In the end:
lsmod | grep nvidia

nvidia_drm             77824  0
nvidia_modeset       1302528  1 nvidia_drm
nvidia              56532992  1 nvidia_modeset
nvidiafb               61440  0
vgastate               24576  1 nvidiafb
fb_ddc                 16384  1 nvidiafb
i2c_algo_bit           16384  2 nvidiafb,mgag200
drm_kms_helper        311296  4 mgag200,nvidia_drm
drm                   622592  5 drm_kms_helper,nvidia,mgag200,nvidia_drmlspci | grep NVIDIA

03:00.0 3D controller: NVIDIA Corporation GP100GL [Tesla P100 PCIe 16GB] (rev a1)nvidia-smi

No devices were found
I tried different ways to install the driver, but when I ask for nvidia-smi I always get No devices found.
[B]
Could you please help?

[/B]
 

sudo dmesg | grep nvidia

[   11.925467] nvidiafb: Device ID: 10de15f8 
[   11.925473] nvidiafb: unknown NV_ARCH
[   12.015811] nvidia: loading out-of-tree module taints kernel.
[   12.015827] nvidia: module license 'NVIDIA' taints kernel.
[   12.074954] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   12.097370] nvidia-nvlink: Nvlink Core is being initialized, major device number 508
[   12.236719] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.86.10  Wed Jul 26 23:01:50 UTC 2023
[   12.242512] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
[   12.242514] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:03:00.0 on minor 1
[   12.409378] audit: type=1400 audit(1691342857.950:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=1573 comm="apparmor_parser"
[   12.409403] audit: type=1400 audit(1691342857.950:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=1573 comm="apparmor_parser"
[  531.056647] [drm] [nvidia-drm] [GPU ID 0x00000300] Unloading driver
[  531.106298] nvidia-modeset: Unloading
[  531.139051] nvidia-nvlink: Unregistered Nvlink Core, major device number 508
[  546.540595] nvidia-nvlink: Nvlink Core is being initialized, major device number 508
[  546.693604] nvidia_uvm: module uses symbols from proprietary module nvidia, inheriting taint.
[  546.699398] nvidia-uvm: Loaded the UVM driver, major device number 506.
[  546.705225] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.86.10  Wed Jul 26 23:01:50 UTC 2023
[  546.708939] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
[  546.708942] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:03:00.0 on minor 1
[  546.714750] [drm] [nvidia-drm] [GPU ID 0x00000300] Unloading driver
[  546.752891] nvidia-modeset: Unloading
[  546.780644] nvidia-uvm: Unloaded the UVM driver.
[  546.809003] nvidia-nvlink: Unregistered Nvlink Core, major device number 508
[  562.200098] nvidia-nvlink: Nvlink Core is being initialized, major device number 508
[  562.322454] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.86.10  Wed Jul 26 23:01:50 UTC 2023
[  562.325817] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
[  562.325819] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:03:00.0 on minor 1
[  747.837871] nvidia_uvm: module uses symbols from proprietary module nvidia, inheriting taint.
[  747.844925] nvidia-uvm: Loaded the UVM driver, major device number 506.

[LIST]
[*]nvidia: module verification failed - indicates signed driver issue
[*]nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver
[*]nvidia-uvm: Loaded the UVM driver
[/LIST]
So the core nvidia driver and UVM/modeset modules are loading.
The signature verification failed warning can likely be ignored for now.
**Why nvidia-smi still doesn’t detect the GPU if the modules are clearly loading??? Does anyone has any clue???**

By the way, I made sure: 
PATH includes /usr/local/cuda-12.2/bin
LD_LIBRARY_PATH includes /usr/local/cuda-12.2/lib64


**Why doesn't it see the card?**

[/COLOR]



[/FONT][/COLOR]

---

### Post by QIII on 2023-08-06
Duplicate of [https://ubuntuforums.org/showthread.php?t=2489676](https://ubuntuforums.org/showthread.php?t=2489676)

Closed.

---

