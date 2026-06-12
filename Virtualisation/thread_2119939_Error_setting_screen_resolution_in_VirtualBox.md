---
title: "Error setting screen resolution in VirtualBox"
date: 2013-02-25
forum: Virtualisation
---

### Post by olddave1 on 2013-02-25
Hi,

Followed the wiki. Get this
```

david@david-VirtualBox:~$ xrandr -q
Screen 0: minimum 64 x 64, current 800 x 600, maximum 32000 x 32000
VBOX0 connected 800x600+0+0 0mm x 0mm
   800x600        60.0*+
   640x480        60.0  
david@david-VirtualBox:~$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
david@david-VirtualBox:~$ xrandr --addmode VBOX0 1368x768_60.00X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  20
  Current serial number in output stream:  21
david@david-VirtualBox:~$ xrandr -q
Screen 0: minimum 64 x 64, current 800 x 600, maximum 32000 x 32000
VBOX0 connected 800x600+0+0 0mm x 0mm
   800x600        60.0*+
   640x480        60.0  
  1368x768_60.00 (0x155)   85.2MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.8KHz
        v: height  768 start  771 end  781 total  798           clock   59.9Hz

```
I also found this thread [http://ubuntuforums.org/showthread.php?t=1880909](http://ubuntuforums.org/showthread.php?t=1880909) and have installed the virtualbox-guest* packages. 

Here is my graphics support
```

david@david-VirtualBox:~$ sudo lshw -C display
[sudo] password for david: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=0
       resources: memory:e0000000-e7ffffff

```
There is no xorg.conf in /etc/X11 so not sure about the options to add a modeline to that file, as it does not exist.

Ideas?

Thx.

David

---

### Post by olddave1 on 2013-02-26
Hi,

No luck, I added a xorg.conf as below. Weirdly the login screen is 1368x768 but as soon as I login it reverts to 800x600 and that is the top resolution availalbe in the Display options.

Here is the xorg.conf I added to /etc/X11 directory
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vboxvideo"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1368x768"
	EndSubSection
EndSection

```
So it can display the correct resolution but something is overriding it and only displaying the 800x600 resolution.

Ideas?

Thx.

David

---

### Post by olddave1 on 2013-02-27
In the end I was advised to remove my xorg.conf and reboot. Then use Ctrl key + F to go to full screen, that worked. No idea what was different to before when it didn't.

---

