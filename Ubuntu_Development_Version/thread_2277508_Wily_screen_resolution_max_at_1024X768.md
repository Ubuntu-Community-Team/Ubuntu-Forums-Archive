---
title: "Wily screen resolution max at 1024X768"
date: 2015-05-09
forum: Ubuntu Development Version
---

### Post by ubername on 2015-05-09
Hi
Just 'upgraded' from Vivid to Wily (Changed all references in sources.list from vivid to wily) . Screen resolution is now at 1024x768 rather than 1920x1080. I did 
```
sudo apt-get install intel-microcode
```

after

```
sudo ubuntu-drivers devices
```

Any clues?

This from

```
sudo lshw -c video
```

 *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)



P.S. I am aware that this is a very developmental branch of ubuntu, so if there is no fix at the moment, or no-one knows the fix this is cool. Just posting a 'status report'

---

### Post by dino99 on 2015-05-09
to find error: xorg.0.log and journalctl

maybe purge the driver then reinstall it (no xorg.conf needed nowadays for single screen)

---

### Post by grahammechanical on 2015-05-09
Wily Werewolf is being built on the Vivid Vervet code base. This early in the 26 week development period wily is still very much vivid. The command ubuntu-drivers devices will give information about the video adapter and the available video drivers. It will not change anything.

We can get different information from this command

```
xrandr
```

This is what I see

> Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.1*+   60.0     59.9     50.0     24.0     60.0     50.0  
   1440x480       60.1  
   1280x1024      75.0  
   1280x800       84.9  
   1280x720       60.0     59.9     50.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9     59.9  

My setting is 1920 x 1080. What video driver are you using? Have you tried using Additional Drivers to change video drivers? By the way, if I use a VGA cable I do not get 1920 x 1080. VGA is not capable of running the higher resolutions. To get those I have to use DVI or HDMI connections.

Regards.

---

### Post by ubername on 2015-05-09
OK one of those frequent issues where Hardware fails at the same time as software updates. Re-seating the cable between monitor and machine has sorted it.

---

### Post by deadflowr on 2015-05-09
Is that something that is really frequent for you?
Seems like it should be a freak issue rather than a frequent one.

---

