---
title: "Xen, I just can't get passthrough to work with my GTX750Ti"
date: 2016-06-21
forum: Virtualisation
---

### Post by BSDShoes on 2016-06-21
I'm currently setting up a Xen (Ubuntu with Windows 10 on physical disk via HVM) on an i3 6100, 16GB DDR4 ram and two 120GB SSD's.  VT-d is supported and enabled and HVM shows up in xl dmesg, I've tried every trick that I can find on the internet and can't seem to boot Windows via passthrough since it just dumps some errors, it however boots up without passthrough but is super sluggish and only runs at 1024x768 and the "PCI device" is unknown in the Window system.  My main GPU is the Intel's onboard GPU.

Are there some guides specifically for 16.04 LTS? I've followed guides based on 14.10 and Mint and Debian, all coming out with some different results.

---

### Post by MAFoElffen on 2016-06-22
Zen 4.0, Windows 8.0 or newer...
[http://lime-technology.com/forum/index.php?topic=31754.0](http://lime-technology.com/forum/index.php?topic=31754.0)
[https://www.reddit.com/r/linux_gaming/comments/3lnpg6/gpu_passthrough_revisited_an_updated_guide_on_how/](https://www.reddit.com/r/linux_gaming/comments/3lnpg6/gpu_passthrough_revisited_an_updated_guide_on_how/)
[http://gro.solexiv.de/2012/08/pci-passthrough-howto/](http://gro.solexiv.de/2012/08/pci-passthrough-howto/)
[https://rafalcieslak.wordpress.com/2014/08/15/multi-os-gaming-wo-dual-booting-excelent-graphics-performance-in-a-vm-with-vga-passthrough/](https://rafalcieslak.wordpress.com/2014/08/15/multi-os-gaming-wo-dual-booting-excelent-graphics-performance-in-a-vm-with-vga-passthrough/)
[https://forums.linuxmint.com/viewtopic.php?t=112013](https://forums.linuxmint.com/viewtopic.php?t=112013)

This one uses Arch Linux, but the guide has very has good info on isolating and setting up i[COLOR=#3F4549][FONT=&amp]ommu groups for the GPU to be passed through to VM's:[/FONT][/COLOR]
[https://bufferoverflow.io/gpu-passthrough/](https://bufferoverflow.io/gpu-passthrough/)

If all you need is to have a higher resolution in Windows in a Windows guest ... the challenge of Video in VNC or Spice sessions, is that a VM Guest has no monitor to query and get EDID data for default resolutions. In a Linux guest, you can add modes via grub (virtual tty console resolution), xrandr (script to create mode, add mode set mode) , or xorg.conf (ignore edid, add modes, set default mode). Windows you can do via the registry. 

First, calculate your video memory requirements via this formula: 
 width * height * 4 = bytes
Example: 1920 * 1080 * 4 = 8294400 bytes
Adjust your video memory of your VM guests config file to reflect that requirement. 
```

...
<video>
  <model type='qxl' [COLOR=#ff0000]vram='8294400[/COLOR][COLOR=#ff0000]'[/COLOR] heads='1'/>                                                            
  <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
</video>
...

```
Then edit the registry. I learned this from working with vSphere ESXi, [VMware KB article #1003, Adding video resolution modes to Windows guest operating systems]("https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003") :
> 
You can modify a Windows guest operating system to support some additional video resolutions, as long as your combination of monitor and video hardware supports them. To do this, edit the Windows registry in the guest operating system after having installed VMware Tools.


Caution: This article contains information about modifying the Windows registry. Before making any registry modifications, ensure that you have a current and valid backup of the registry and the virtual machine. For more information on backing up and restoring the registry, see the Microsoft article 136393.
 
Note: The preceding link was correct as of December 10, 2015. If you find that the link is broken provide a feedback and a VMware employee will update the link.
 
Note: Take a full backup of the registry prior to editing it. Do not skip this step. 
Step 1- Open the Windows Registry editor. Click Start > Run, type regedit , and press Enter. 
Step 2- The specific registry key will vary by version of Windows. Search (go to Edit > Find) for this key: vmx_svga . The correct key has several sub-keys, but it is the main key that should be edited. 
Step 3- Create a new string value (REG_SZ ) for each new resolution. Name the new value Resolution.x , where x is one higher than the highest number listed. Ensure that you correctly identify the highest number, as the values are not listed in numerical order. 
Step 4- Modify the data in the new value. Enter the desired resolution using the format WIDTHxHEIGHT . For example, to add a resolution of 1600 x 1024 pixels, enter 1600x1024 . 
Step 5- Repeat steps 3 and 4 for any other desired resolutions.
Step 6- Restart the guest operating system.
Step 7-  Log on as an administrator, and verify that the new resolutions are available:
 a. Go to Start > Settings > Control Panel > Display > Settings.
 b. Adjust the Screen Area slider control.


Note: Resolutions that are not supported by the physical monitor and video hardware are not available to be selected.

This an old svga patch for qemu (used by both KVM and Xen), where you use to add modes to the vga section of the SeaBIOS module...
```

diff -Naur a/roms/seabios/vgasrc/bochsvga.c b/roms/seabios/vgasrc/bochsvga.c
--- a/roms/seabios/vgasrc/bochsvga.c    2014-04-17 14:47:11.000000000 +0100
+++ b/roms/seabios/vgasrc/bochsvga.c    2014-05-01 14:47:02.190874993 +0100
@@ -99,6 +99,9 @@
     { 0x190, { MM_DIRECT, 1920, 1080, 16, 8, 16, SEG_GRAPH } },
     { 0x191, { MM_DIRECT, 1920, 1080, 24, 8, 16, SEG_GRAPH } },
     { 0x192, { MM_DIRECT, 1920, 1080, 32, 8, 16, SEG_GRAPH } },
+    { 0x193, { MM_DIRECT, 1600, 900, 16, 8, 16, SEG_GRAPH } },
+    { 0x194, { MM_DIRECT, 1600, 900, 24, 8, 16, SEG_GRAPH } },
+    { 0x195, { MM_DIRECT, 1600, 900, 32, 8, 16, SEG_GRAPH } },
 };
 
 static int dispi_found VAR16 = 0;

```
... but you can see by >>"[this]("https://fossies.org/dox/qemu-2.6.0/bochsvga_8c_source.html#l00378")"<<, in lines 58 through 101, that patch is already applied to QEMU 2.6, SEABIOS, bochsvga.c ... (so if you use "vga"...) (But the QEMU package in main for 16.04 is still v2.5)

Edit-- Attached are screen shots of Win10_build1511 and Win Server 2016 TP4 showing resolutions up to 2650x1600, just using spice and qxl.

---

### Post by BSDShoes on 2016-06-22
Managed to get passthrough to work, guest Windows finds the card but stops the driver (error 43) so that's another thing I need to figure out.

---

### Post by MAFoElffen on 2016-06-22
If you go to the :
1. Control Panel > device manager... 
2. Right-click on device >  Properties > General Tab > Device status > Check if it says it is working properly or not > Close properties.
3. On the device, right-click on it > Uninstall.
4. On computer Name > right-click > scan for hardware changes
5. Repeat step 2.

Depending on the Windows version, for your NVidia card, you may have to first check for updates to get MS'es NVidia driver from their updates ... or dl it (then install) directly from NVidia. This does this same with my GTX 970 and GTX 980's on native Windows until I do either of those. I don't remember about what I had to do for my GTX 750ti. I remebr that I prematurely paniced ... until I realized that it took a few minutes before Windows figures out on it's own, that it really was an NVidia card and it needed a different driver for it.

But if you go to NVidia downloads and use their autorecognize Java app and it says it cannot find one of their card ... then you would know you still had a passthrough problem or not. If it saw it, then it would confirm that it is showing thorugh the pass-through.

---

### Post by BSDShoes on 2016-06-22
Windows 10 installed the Nvidia drivers, I already looked at device manager and that's where I saw the error 43 message, I will try uninstall it tonight to see if anything happens.  I was in the middle of downloading the Nvidia driver from the website while it happened.

Also I noticed there's a "PCI Device" with a yellow "!" on it under device manager, wonder if that's anything to do with the GPU as well.

---

### Post by MAFoElffen on 2016-06-22
Curious is it is the hdmi audio from that same card...

---

### Post by BSDShoes on 2016-06-22
Oh maybe should I take off the audio port from passthrough? I didn't think about that.

---

### Post by MAFoElffen on 2016-06-22
i'm thinking you should check to see if it is in a different iommu group as the GPU and if you have that passed through.

Often that is the problem with passing through a GPU with hdmi... but I think if they are on the same physical card (they are) that you should pass them both through. Not sure the driver will work right if only part of it is showing through. I'm thinking that the driver would fail if it sees incomplete hardware for what it expects. That make sense?

---

### Post by BSDShoes on 2016-06-27
I managed to get passthrough to work with qemu-kvm and libvirt (but Windows in the VM crashes after a while despite it finding the GTX750Ti card but doesn't crash at all if I turn IOMMU off).  So cnosidering Xen, I *must* be missing something, for expermentation sake I'm going to do a clean reinstall and do it again.

---

### Post by MAFoElffen on 2016-06-27
Keep us posted on what you find. (Or if it just works and you don't know why.)

---

