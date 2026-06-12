---
title: "How to set Ubuntu guest console resolution while using vboxvideo accelerated driver"
date: 2018-01-17
forum: Virtualisation
---

### Post by ogilvierothchild on 2018-01-17
After much searching, I was able to set both the X and virtual console screen resolutions to 1920x1080 of an ubuntu guest while still using the vboxvideo kernel module.  Basically, in this post I show how to set all resolutions (from grub, boot (including vboxvideo drm module loading), console, X display manager, and X) to the same value so the display just remains in one resolution.

Normally after installing Guest Additions, the virtual consoles all become 800x600 and are relatively useless because I run fullscreen so the pixels are very small, and if one increases the font size, then very little text remains on the screen (in a small box in the center of the screen). 

The trick is to use add the following to /etc/fb.modes

[INDENT][COLOR=#000000][FONT=&quot]mode "1920x1080-60"[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]    # D: 148.500 MHz, H: 67.500 kHz, V: 60.000 Hz[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]    geometry 1920 1080 1920 2160 32[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]    timings 6734 148 88 36 4 44 5[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]    hsync high[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]    vsync high[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]    rgba 8/16,8/8,8/0,8/24[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]endmode
[/FONT][/COLOR][/INDENT]
[COLOR=#000000][FONT=&quot][/FONT][/COLOR]


(from [http://www.cubieforums.com/index.php?topic=50.0](http://www.cubieforums.com/index.php?topic=50.0))

Then in /etc/default/grub change:

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet video=1920x1080-60  vga=864"


and at the end of  /etc/default/grub append the lines


GRUB_GFXMODE=1920x1080x32
GRUB_GFXPAYLOAD_LINUX=keep

Now in the host OS, you need to do something like (from [https://www.virtualbox.org/manual/ch09.html](https://www.virtualbox.org/manual/ch09.html) , search for "864"):

VBoxManage setextradata "Ubuntu VM" "CustomVideoMode1" "1920x1080x32"


This mode (CustomVideoMode1) is the video mode that the "vga=" kernel parameter will connect with.

Follow the directions in [https://askubuntu.com/a/331988](https://askubuntu.com/a/331988) to set lightdm screen resolution, three steps below:


[LIST=1]
[*]log in
[*]use xrandr or the Displays control utility to configure your monitors how you'd like them to be configured in the login screen (ie 1920x1080)
[*]copy ~/.config/monitors.xml to /var/lib/lightdm/.config
[/LIST]

Putting it all together:

[LIST=1]
[*]CustomVideoMode1 gets read by the kernel via the "vga" parameter
[*]GRUB will set its mode using GRUB_GFXMODE
[*]GRUB will leave that mode in place on boot due to GRUB_GFXPAYLOAD_LINUX
[*]When vboxvideo loads, it loads the vboxdrmfb framebuffer driver, which normally sets the resolution back to what it thinks is the native resolution of the display, but I've only seen it go to 800x600 on modern laptops, but it will refer to the "video=" kernel parameter, and look that up in /etc/fb.modes, and use that setting for consoles
[*]When vboxvideo loads and then lightdm (the login screen AKA X display manager) runs, again normally the resolution is set to some random value, so follow the three steps above to get it to start in a sane resolution.
[/LIST]

Video mode setting in Linux is a mess!

---

### Post by lammert-nijhof on 2018-01-21
Nice solution, but what is the problem? 
My virtual machines adapt to the window size I choose, maintaining the pixel size. My HW screen is 1680x1050 and in Virtualbox in full screen the Windows-VM confirms that it is 1680x1050. If I use it in a window it will depend on the size of the window be something like e.g 1216x932. During booting the screen size changes, but who cares that takes less then a minute.

---

### Post by amanduro on 2018-12-02
With Ubuntu-18.04.1-live-server-amd64 as guest on Virtualbox 5.2.22 I have maybe the same problem with the console resolution (but no X installed). Don`t know, if I made something wrong. Resolution is fine on initial boot, but when ..."Initialized vboxvideo 1.0.0 20130823 for 0000:00:02.0 on minor 0"... appears on boot, the system flips back to 800x600. The screen options from the menu of the virtual machine are greyed out and 800x600 is checked. Can someone give a hint where to start with this problem?
Below is filtered output from dmesg.
[    8.106674] vboxvideo: loading out-of-tree module taints kernel.
[    8.147357] vboxvideo: module verification failed: signature and/or required key missing - tainting kernel
...
[    8.927559] vboxvideo 0000:00:02.0: fb0: vboxdrmfb frame buffer device
[    8.927628] [drm] Initialized vboxvideo 1.0.0 20130823 for 0000:00:02.0 on minor 0
...
Best regards,
Amanduro

---

### Post by amanduro on 2018-12-02
and ... hwinfo --framebuffer had an empty output. I found this on google:
[https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg286283.html](https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg286283.html)

Thanks

---

### Post by amanduro on 2018-12-03
After editing again and again /etc/default/grub I've got vboxvideo (vboxdrmfb) to accept 1024x768 finally, which is a significant progress.
Here are the changed lines:
GRUB_CMDLINE_LINUX_DEFAULT="maybe-ubiquity" #that is the default setting
GRUB_CMDLINE_LINUX="video=1024x768-32"
GRUB_GFXMODE="1024x768x32"
GRUB_GFXPAYLOAD_LINUX="1024x768x32"

I didn't find time to dig deeper yet. But maybe someone will find this information usefull. :)

---

### Post by amanduro on 2018-12-06
_Update_
/etc/default/grub Parameter GRUB_GFXPAYLOAD_LINUX changed:
GRUB_GFXPAYLOAD_LINUX="keep" 
--------
fbset -i:
mode "1024x768"
    geometry 1024 768 1024 768 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : vboxdrmfb
    Address     : 0
    Size        : 3145728
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 4096
    Accelerator : No
--------------------
 However there is another drawback in setting a proper screen resolution on a fresh install of ubuntu-18.04.1 Server.
Any attempt to change screen resolutions with fbset gets "ioctl FBIOPUT_VSCREENINFO: Invalid argument".
See [https://bugs.launchpad.net/ubuntu/+source/fbset/+bug/1749443](https://bugs.launchpad.net/ubuntu/+source/fbset/+bug/1749443).
Just for testing I installed a new virtualbox guest with ubuntu-16.04.1 server:
hwinfo --framebuffer:
------------------
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.459]
  Unique ID: rdCR.VICk_A_ErH4
  Hardware Class: framebuffer
  Model: "Oracle VM VirtualBox VBE Adapter"
  Vendor: "Oracle Corporation"
  Device: "Oracle VM VirtualBox VBE Adapter"
  SubVendor: "VirtualBox VESA BIOS"
  SubDevice: 
  Revision: "Oracle VM VirtualBox Version 5.2.22"
  Memory Size: 16 MB
  Memory Range: 0xe0000000-0xe0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0302: 800x600 (+100), 4 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0304: 1024x768 (+128), 4 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0306: 1280x1024 (+160), 4 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+960), 24 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+1920), 24 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+2400), 24 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+3072), 24 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+3840), 24 bits
  Mode 0x0340: 320x200 (+1280), 24 bits
  Mode 0x0341: 640x400 (+2560), 24 bits
  Mode 0x0342: 640x480 (+2560), 24 bits
  Mode 0x0343: 800x600 (+3200), 24 bits
  Mode 0x0344: 1024x768 (+4096), 24 bits
  Mode 0x0345: 1280x1024 (+5120), 24 bits
  Mode 0x0346: 320x200 (+320), 8 bits
  Mode 0x0347: 1600x1200 (+6400), 24 bits
  Mode 0x0348: 1152x864 (+1152), 8 bits
  Mode 0x0349: 1152x864 (+2304), 15 bits
  Mode 0x034a: 1152x864 (+2304), 16 bits
  Mode 0x034b: 1152x864 (+3456), 24 bits
  Mode 0x034c: 1152x864 (+4608), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
-------------------
But fbset gets the same error as described above.
Does anybody know a proper way to test and configure terminal screen resolutions in 18.04 LTS Server running in a VirtualBox Guest environment?

Thanks, amanduro

---

