---
title: "Setting Resolution for Headless X11"
date: 2020-02-13
forum: Virtualisation
---

### Post by mloiterman on 2020-02-13
**Background**
[LIST]
[*]New Ubuntu 19.10 installed into a Proxmox  6.1-5 Virtual Machine  
[*]Proxmox Host has an Nvidia GT710 passed through to the Ubunutu VM.
[*]No monitor is connected to Nvidia card installed into Proxmox host
[*]Installed xserver-xorg-video-dummy to get X to work without a monitor attached
[*]GT710 is seen by Ubuntu.  From within the VM:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)

```
[/LIST]

**Objective**
[LIST]
[*]Use the GT710 to obtain higher resolution for VNC remote connections with no monitor attached.
[*]Understand what changes need to be made to my xorg.conf file in order to take full advantage of my Nvidia card for VNC connections.
[/LIST]

**Setup**
If I use the following /etc/X11/xorg.conf file I can connect via VNC, but resolution is 1024x800 at 24bit as one would expect:
```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "dummy"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 31.5-48.5
    VertRefresh 50-70
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1024x800"
    EndSubSection
EndSection
```

If I use this xorg.conf file, I can connect, but I only get a black screen:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"              #change for AMD or Intel
    VendorName     "NVIDIA Corporation"  #this, too
    Option "NoLogo" "1"                  #also this
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Virtual 1920 1080
    Option          "AllowEmptyInitialConfiguration" "True"
    EndSubSection
EndSection

```


**Additional Troubleshooting Data**
```

 nvidia-smi
Thu Feb 13 07:39:44 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 435.21       Driver Version: 435.21       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 710      Off  | 00000000:01:00.0 N/A |                  N/A |
| 40%   31C    P0    N/A /  N/A |      0MiB /  2002MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+

```

```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK208B [GeForce GT 710] [10de:128b] (rev a1)
	Subsystem: eVga.com. Corp. GK208B [GeForce GT 710] [3842:2717]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GK208 HDMI/DP Audio Controller [10de:0e0f] (rev a1)
	Subsystem: eVga.com. Corp. GK208 HDMI/DP Audio Controller [3842:2717]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

```

---

### Post by mloiterman on 2020-02-14
Anyone?

---

### Post by Skaperen on 2020-02-14
try changing the driver to "dummy" in the HD one.

---

