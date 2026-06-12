---
title: "Resolution on Virtual Console"
date: 2011-02-28
forum: Server Platforms
---

### Post by dlublink on 2011-02-28
Hello,

I want virtual console ( tty1 ) to have a resolution of 1280x1024 instead of the default text 80x25.

So I searched and found I should use the vga= in kernel parameters.

I used dpkg-reconfigure grub-pc to add the vga= to the kernel parameters.

I tried vga=ask, it says it's no longer supported and the system would not boot ( until I removed vga=ask ).

I tried vga=793, and the screen says "out of range".

Both my monitor and video card support 1280x1024.

I am not too concerned about colors. The commands that give the most colors on this machine are ls and asterisk, so I think 8 bit colours is enough.

I am unsure how to proceed. Any pointers would help.

David

Screen Benq q9u3

{{{
hwinfo --framebuffer 

02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.2nAxFcraNG7
  Hardware Class: framebuffer
  Model: "ATI MACH64GT"
  Vendor: "ATI Technologies Inc."
  Device: "MACH64GT"
  SubVendor: "ATI MACH64"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 4 MB
  Memory Range: 0xc5000000-0xc53fffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+1920), 24 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+2400), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+3072), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+3840), 24 bits
  Mode 0x0402: 320x200 (+320), 8 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+960), 24 bits
  Mode 0x0412: 320x240 (+320), 8 bits
  Mode 0x0413: 320x240 (+640), 15 bits
  Mode 0x0414: 320x240 (+640), 16 bits
  Mode 0x0415: 320x240 (+960), 24 bits
  Mode 0x0422: 512x384 (+512), 8 bits
  Mode 0x0423: 512x384 (+1024), 15 bits
  Mode 0x0424: 512x384 (+1024), 16 bits
  Mode 0x0425: 512x384 (+1536), 24 bits
  Mode 0x0432: 400x300 (+400), 8 bits
  Mode 0x0433: 400x300 (+800), 15 bits
  Mode 0x0434: 400x300 (+800), 16 bits
  Mode 0x0435: 400x300 (+1200), 24 bits
  Mode 0x0442: 640x350 (+640), 8 bits
  Mode 0x0443: 640x350 (+1280), 15 bits
  Mode 0x0444: 640x350 (+1280), 16 bits
  Mode 0x0445: 640x350 (+1920), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
}}}

Only mention of video hardware in dmesg after boot ( while screen says out of range ) :

{{{
[   12.859049] Linux agpgart interface v0.103
[   12.902182] piix4_smbus 0000:00:0f.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr
[   12.904357] agpgart-serverworks 0000:00:00.0: can't determine aperture size
[   12.904382] agpgart-serverworks 0000:00:00.0: agp_backend_initialize() failed
[   12.904401] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22
[   12.904438] agpgart-serverworks 0000:00:00.1: can't determine aperture size
[   12.904457] agpgart-serverworks 0000:00:00.1: agp_backend_initialize() failed
[   12.904491] agpgart-serverworks: probe of 0000:00:00.1 failed with error -22
[   13.031731] vga16fb: initializing
[   13.031746] vga16fb: mapped to 0xc00a0000
[   13.031984] fb0: VGA16 VGA frame buffer device

}}}

---

### Post by dlublink on 2011-03-01
lspci -nn | grep VGA

00:03.0 VGA compatible controller [0300]: ATI Technologies Inc 3D Rage IIC 215IIC [Mach64 GT IIC] [1002:4756] (rev 7a)

---

### Post by dlublink on 2011-03-03
After a lot of reading and searching, I found that vga= has been replaced by a new feature called KMS ( Kernel Mode Setting ). As far as I can tell, the card on the said machine is not supported by this feature, but on my other machine with an intel video card I created a file /etc/modprobe.d/i915-kms.conf with the line :
options i915 modeset=1, with this, the resolution is much higher on this other machine.

I will continue searching to see if my mach64 is supported.

---

