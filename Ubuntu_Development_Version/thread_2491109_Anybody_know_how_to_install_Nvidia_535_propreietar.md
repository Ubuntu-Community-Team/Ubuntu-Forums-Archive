---
title: "Anybody know how to install Nvidia 535 propreietary drivers."
date: 2023-09-26
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2023-09-26
I used the Nvidia GUI app and set the driver to install.  When I reboot Nvidia app says I am using Nvidia Performance, but about says I am using Intel graphics, not even the UHD version.
I have Nvidia GTX 1650 with Intel UHD graphics card.

Henry

---

### Post by #&amp;thj^% on 2023-09-26
I've never heard of a  Nvidia GUI app??
```
nvidia-smi
Tue Sep 26 09:27:50 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.104.05             Driver Version: 535.104.05   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 Ti     Off | 00000000:01:00.0 Off |                  N/A |
| N/A   40C    P8               1W /  50W |    378MiB /  4096MiB |      8%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      2806      G   /usr/lib/xorg/Xorg                          217MiB |
|    0   N/A  N/A      5354      G   xfwm4                                         2MiB |
|    0   N/A  N/A    106951      G   /usr/bin/python                              11MiB |
|    0   N/A  N/A    127241      G   /usr/lib/firefox/firefox                    143MiB |
+---------------------------------------------------------------------------------------+
```
and:
```
inxi -G
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 535.104.05
  Device-2: AMD Renoir driver: amdgpu v: kernel
  Device-3: Syntek Integrated Camera driver: uvcvideo type: USB
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: amdgpu,nvidia
    unloaded: fbdev,modesetting,nouveau,vesa dri: radeonsi gpu: amdgpu
    resolution: 1920x1080~120Hz
  API: OpenGL v: 4.6.0 NVIDIA 535.104.05 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2

```
Do you have switchable graphics option in your bios?
```
prime-select query
nvidia


```

---

### Post by oldfred on 2023-09-26
With Ubuntu, you do not install the nVidia app or .run file from nVidia. That requires, in effect, reinstall with every kernel update.

You install nVidia driver as part of install or can boot recovery mode to terminal.
If booted you can use the drivers tab in system to choose a proprietary driver.

Install nVidia If you just want default version - recommended one
sudo ubuntu-drivers autoinstall

If .run version installed you must use it to uninstall it.
If previous version installed & changing, you must purge first or you get conflicts. New driver does not completely overwrite an old driver.
sudo apt-get remove --purge nvidia-*
#What is installed
dkms status
Whats available
dpkg -l | grep -i nvidia
ubuntu-drivers devices
You then can manually choose any in list or auto install recommended one.
sudo apt-get install nvidia-XXX 


[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Hewjr100 on 2023-09-26
What I have always done is go to software drivers select Nvidia then install.  After reboot I can than use Nvida app to select Nvidia performance and reboot.  from that point on no updates including kernel changes anything.  I used the same procedure but cannot get Nvidia to stick.

Henry

> +---------------------------------------------------------------------------------------+| NVIDIA-SMI 535.104.05             Driver Version: 535.104.05   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650        Off | 00000000:01:00.0 Off |                  N/A |
| N/A   50C    P0               6W /  50W |      3MiB /  4096MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      1788      G   /usr/bin/gnome-shell                          1MiB |
+---------------------------------------------------------------------------------------+[/QUOT[QUOTE]

> Graphics:  Device-1: Intel CometLake-H GT2 [UHD Graphics] driver: i915 v: kernel
  Device-2: NVIDIA TU117M driver: nvidia v: 535.104.05
  Device-3: Luxvisions Innotech HP TrueVision HD Camera driver: uvcvideo
    type: USB
  Display: wayland server: X.Org v: 1.23.2 with: Xwayland v: 23.2.0
    compositor: gnome-shell v: 45.0 driver: dri: iris gpu: i915
    resolution: 1920x1080~60Hz
  API: OpenGL v: 4.6 Mesa 23.1.7-1ubuntu1 renderer: Mesa Intel UHD Graphics
    (CML GT2

> prime-select query
on-demand

---

### Post by #&amp;thj^% on 2023-09-26
Ok Nvidia-Settings 
Never got an answer for "Do you have switchable graphics option in your bios?"
But no matter to use Nvidia Driver:
```
sudo prime-select nvidia
```
go back to intel:
```
sudo prime-select intel
```
Each of those commands will take a logout and login to see any changes, or a reboot.
And nVidia will not always act right right on a Wayland session, best to use X11 for nvidia.

---

### Post by Hewjr100 on 2023-09-26
Will switch to X11.

Henry

---

### Post by Hewjr100 on 2023-09-26
Yes I have swithcable graphics if have both intel and nvidia available and I have enabled nvidia in previous versons of Ubuntu without any problems.  I always swith to Nvidia.  It's only the GTX 1650 but I blelieve its better than the default.

Henry

---

### Post by #&amp;thj^% on 2023-09-26
> **Hewjr100 said:**
>   I always swith to Nvidia.  It's only the GTX 1650 but I blelieve its better than the default.

Henry
+1
nVidia dose have a slight edge on media related application's.

---

