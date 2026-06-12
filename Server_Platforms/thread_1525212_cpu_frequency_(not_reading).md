---
title: "cpu frequency (not reading)"
date: 2010-07-06
forum: Server Platforms
---

### Post by tr8dr on 2010-07-06
I'm running the latest ubuntu server distribution on a dual E5520 system.   I had switched motherboard and done a reinstall of the kernel, etc.

On reinstall, I noticed that there is no cpufreq directory(ies) under /sys/devices/system/cpu/cpu*.   I could not determine whether there is a module that needs to be loaded or why this would not be present.

I did the usual sensors-detect and loaded the appropriate modules.  I can see cpu temperatures and fan speeds correctly.   

I was running a full load on the 2 cpus (16 threads) with a load of approximately 14-15 on top.  catting /proc/cpuinfo showed the cpus running at 1/2 speed, which I thought was odd.   Without the cpuinfo_cur_freq, which I've known to provide accurate info in the past, not sure if the cpuinfo reading is correct.

I am running with kernel:  2.6.32-23-server on a Asus Z8PE-D12X motherboard, 2x E5520.    Here is the first column of output of lsmod:

[FONT="Courier New"]
w83795
fbcon
tileblit 
snd_hda_intel
font 
snd_hda_codec
bitblit 
snd_hwdep 
softcursor
snd_pcm 
snd_timer 
vga16fb 
psmouse
snd
vgastate 
serio_raw 
soundcore  
w83627ehf 
hwmon_vid  
ioatdma  
snd_page_alloc 
shpchp 
dca 
coretemp  
i2c_i801 
lp
parport 
usbhid
hid 
usb_storage  
e1000e 
[/FONT]

Thanks for your help.

---

