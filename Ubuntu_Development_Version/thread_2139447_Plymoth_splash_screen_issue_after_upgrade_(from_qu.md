---
title: "Plymoth splash screen issue after upgrade (from quantal to raring)"
date: 2013-04-26
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-04-26
I just upgraded this system to raring from quantal
running the 3.8.9 mainline kernel
using the xorg edgers ppa
running nvidia 319
native screen resolution is 1600x900
i have tried reconfiguring v86d plymouth 
setting the Plymouth theme
when it boots i get the text version of the xubuntu plymouth theme and it is only using the top left corner of the screen, about 640x480 pixels
the shutdown screen is right but it is stretched to fill the screen
my efforts have managed to get it this far it was giving a black screen for boot and shutdown at first
```
~$ cat /etc/initramfs-tools/conf.d/splash
FRAMEBUFFER=y
~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset uvesafb mode_option=1280x800-24 mtrr=3 scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x800
GRUB_GFXPAYLOAD_LINUX=1280x800x32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
~$ cat /etc/initramfs-tools/modules | tail -1
uvesafb mode_option=1280x800-24 mtrr=3 scroll=ywrap
~$ sudo hwinfo --framebuffer
> hal.1: read hal dataprocess 6140: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=Launch helper exited with unknown return code 1
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.nKoKkFdi9hC
  Hardware Class: framebuffer
  Model: "NVIDIA GF108 Board - 1071v1p1"
  Vendor: "NVIDIA Corporation"
  Device: "GF108 Board - 1071v1p1"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xfb000000-0xfbdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

EDIT: My grub file was somehow altered during upgrade, special characters were converted to spaces

---

### Post by WorLord on 2013-04-26
The nVidia binary drivers (*any* version) automatically disable any plymouth framebuffer splash screen, as framebuffers do not play well with nVidia cards and the binary driver in particular.  

This comes directly from nVidia.  

So any deb package from Ubuntu blacklists fbdev and related modules... without those it is literally impossible for the boot screen to be anything other than plain old VGA.

Go ahead -- ask me how I found all this out.  :-)

---

### Post by pqwoerituytrueiwoq on 2013-04-26
i have always had it full screen, it was just stretched to fill the screen
i had the splach screen, the non-text one with the nvidia drivers before, and have done it on my desktop as a clean install
i have been using this trick since lucid lynx (10.04)

---

