---
title: "High CPU usage on xorg with ubuntu 22 systum76 with NVIDIA and external monitors"
date: 2022-06-09
forum: System76 Support
---

### Post by jayventi on 2022-06-09
High CPU usage on xorg with ubuntu 22 with NVIDIA and external monitors
runnuing ubuntu 22.04 on a System76 Gazelle with 
    NVIDIA NVIDIA GeForce GTX 1650 
    NVIDIA Driver Version: 510.73.05

I have two external monitors monitors a 

```
~$ xrandr
Screen 0: minimum 320 x 200, current 6000 x 3840, maximum 16384 x 16384
eDP-1 connected primary 1920x1080+0+2449 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     59.98*+  59.97    59.96    59.93  
   .
   .
   .
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+4080+2412 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+
   1680x1050     59.88  
   .
   .
   .
DP-1-0 connected 2160x3840+1920+0 left (normal left inverted right x axis y axis) 527mm x 296mm
   3840x2160     60.00*+  29.98  
   .
   .
   .
DP-1-1 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0xa0) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
.
.
.
  640x480 (0x84) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```

I'm also showing  hidpi-daemon installed I installed the system76 driver support package
```
sudo ps aux | grep hidpi


2798  0.0  0.0 267956 21492 ?        Sl   11:05   0:00 /usr/bin/python3 /usr/lib/hidpi-daemon/hidpi-notification
2825  0.0  0.1 442868 46680 ?        Sl   11:05   0:00 /usr/bin/python3 /usr/lib/hidpi-daemon/hidpi-daemon

```

I've recently read an article [https://support.system76.com/articles/hidpi-multi-monitor/](https://support.system76.com/articles/hidpi-multi-monitor/) that suggested I should only configure my resolution and monitor setups in the article suggests that I should use the tool "NVIDIA X Server" but the one installed with my most recent driver pack is NVIDIA Server 
    ```
$ nvidia-settings -v

    nvidia-settings:  version 510.47.03
          The NVIDIA Settings tool.

```
this version does not contain a menu entry with (X server display configuration) which means I cannot set individual monitor resolutions also the only monitor connected under the driver in the current version is the DELL monitor (DP-1-0 ).

The question is what's the proper set of demons and Nvidia driver version and resolution configuration method that's recommended to kill the excessive CPU load?

---

