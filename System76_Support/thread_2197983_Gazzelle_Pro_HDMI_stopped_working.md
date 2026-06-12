---
title: "Gazzelle Pro HDMI stopped working"
date: 2014-01-06
forum: System76 Support
---

### Post by jsatt22 on 2014-01-06
I have a Gazelle Pro (gazp9) running Kubuntu 13.04 64bit. On Friday afternoon, I was using a second monitor over HDMI with no problem whatsoever. The machine was powered down over the weekend, then powering it up first thing this morning it no longer recognizes the HDMI port is even available. I have tested it with a couple different monitors, and still no luck.

Output for xrandr show
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

```
where there was previsouly always an entry for HDMI1.

```

>> sudo lspci -v -s 00:02
00:02.0 VGA compatible controller: Intel Corporation Haswell Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
        Subsystem: CLEVO/KAPOK Computer Device 0655
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: i915

```

Running "udevadm monitor" does nothing when connecting/disconnecting cable. I had not updated any packages since 12/30/13, well before this was an issue, until I began troubleshooting this issue this morning, at which point I updated to kernel 3.8.0-35-generic and xserver-xorg-video-intel to 2:2.21.6-ubuntu4.3. Also found someone having a similar issue [http://askubuntu.com/questions/345622/hdmi-stopped-working-ubuntu-13-04](http://askubuntu.com/questions/345622/hdmi-stopped-working-ubuntu-13-04). Any help or additional things to check would be much appreciated.

---

### Post by jsatt22 on 2014-01-06
And just like that, it begins working again. without further changes or explaination.

---

### Post by Helsvell on 2014-02-27
I have the exact same issue today.  xrandr does not show HDMI1 any more.  This is on a Gazelle Pro with Intel HD4600 integrated graphics.

---

### Post by Helsvell on 2014-02-27
Did your issue ever return after it fixed itself?

---

### Post by Helsvell on 2014-02-27
Ok so rebooting doesn't fix this. Or shutting down the computer and starting again with the HDMI cable plugged in.

However, when I shut down the computer and turned it back on with the HDMI cable removed xrandr displays the missing HDMI port and when I connect the monitor everything works again.

---

