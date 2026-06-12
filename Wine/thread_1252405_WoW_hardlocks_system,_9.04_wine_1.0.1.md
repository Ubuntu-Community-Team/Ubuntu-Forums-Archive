---
title: "WoW hardlocks system, 9.04 wine 1.0.1"
date: 2009-08-28
forum: Wine
---

### Post by dal on 2009-08-28
Having issues trying to run World of Warcraft on my system. After a indeterminate time period (sometimes minutes, sometimes hours) of gameplay both screens blank out (I'm using nvidia twinview) and the system stops responding to any input (I can't alt-Fx to get a terminal window up, or use alt-sysRq key combos, for instance). However it appears to keep doing anything it's doing (If I'm playing a song or video I keep getting audio, and network transfers via samba keep going) for about 20-30sec, before the system completely freezes and requires a hard reset (see below - I have since worked out that the machine will display the login screen if I leave it long enough, and the ssh server stays responsive during this process).

I've tried using a different desktop environment (gnome, kde and xfce), turning off compiz and desktop effects in the desktop environments' settings panels, disabling the composite extension in xorg.conf, and setting the processor affinity to keep it on one cpu core (all were suggested as possible remedies to similar problems on other webforums). No dice :(

My system is as follows:

K/Ubuntu 9.04, 2.6.28-15-generic kernel, nvidia 180.60 binary drivers on a 9600gt card, xserver-xorg package 1:7.4~5ubuntu18, xserver-xorg-core package 2:1.6.0-0ubuntu14, wine 1.0.1.

I have been trying to run wow in opengl mode, but am about to try removing that from my config.wtf, and if that doesn't help I'm looking at trying the wine ppa for a newer version. If neither of those fixes work, I'm going to be pretty much stumped I think. Any suggestions would be much appreciated :)

---

### Post by dal on 2009-08-29
Well, switching to wine 1.1.28 (the ppa version) did the trick. OpenGL and d3d both work under this version of wine.

Stick kinda scary that anything running in userspace could bring the whole system down like that though :( (Edit: I've since found out that the system is not completely dead, and that the culprit appears to be xorg or the nvidia drivers - see later post)

---

### Post by dal on 2009-08-29
Appears I spoke too soon, it worked ok for a couple of hours and then hardlocked twice within ten minutes :(

---

### Post by dal on 2009-08-30
This was in /var/log/kern.log from when one of the crashes happened - the first line is the last line of the bootup sequence, and then obviously the other stuff is when I was trying sysrq key combos - so obviously they were being received by the system and it was acting on them to some extent - although the last combo I tried (reboot) obviously didn't work as I had to use the reset button, and the screens were dead so I missed the nice help message :(


Aug 29 08:37:34 k-desktop kernel: [   76.000220] eth0: no IPv6 routers present
Aug 29 09:46:57 k-desktop kernel: [ 4239.970359] SysRq : Keyboard mode set to system default
Aug 29 09:47:05 k-desktop kernel: [ 4247.586370] SysRq : Keyboard mode set to system default
Aug 29 09:47:14 k-desktop kernel: [ 4256.482374] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK aLlcpus showMem Nice powerOff showPc show-all
-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks
Aug 29 09:50:18 k-desktop kernel: Inspecting /boot/System.map-2.6.28-15-generic

---

### Post by GeoPirate on 2009-09-01
just curious, you're using 180.xx drivers, the 185.xx are much more stable I think, may help with your problem.

---

### Post by dal on 2009-09-08
Thanks, I'll switch drivers and test it out when the servers are back up :)

---

### Post by dal on 2009-09-09
Well, I did switch over to the 185.xx series, but after half an hour of gameplay I got the same result. This time, however, I had my laptop on hand so I attempted to ssh in to see if I could gather any information about what happens to the machine during these episodes. This is what I found out:

The machine does not actually hardlock or reset itself. It makes all the sounds of resetting - fan kicks into high gear, after 30sec or so the machine beeps like it does at the post screen when first powered on, hard drive clicks over - but the ssh session stayed active right through until I was looking at the login screen again (and the screen stayed blank until then as well).

top shows the wow process with 1-2% of the cpu, and the Xorg process with 90%+. In the general course of gameplay, the processes are reversed, and even when xorg spikes as it does occasionally it doesn't go above 5% or so.

dmesg shows the errors:

[ 9144.681768] Xorg[4571]: segfault at 9643f000 ip b6426fbc sp bfe17d40 error 6 in nvidia_drv.so[b63b7000+3c5000]                                            
[ 9173.636422] pidgin[5969]: segfault at 8f1c000 ip b7e8c253 sp b3ff4790 error 6 in libX11.so.6.2.0[b7e5d000+ea000]

It might be worth knowing that wow is the only thing I run on my machine that really stresses the video card - I do use the VDPAU enabled version of mplayer for some x264 video playback, but don't play any other games, render 3d graphics via cuda or w/e. After wow, the next most graphically intensive application I use would be compiz or google earth. So between that fact and the dmesg errors, wine is most likely off the hook (anyone know how/if I can move this thread to another forum?).

So, what do people think? Xorg bug? Nvidia driver bug? Any ideas on how I can work out which is the culprit, and gather more information to pass on to the relevant developers?

---

### Post by dal on 2009-09-09
Including the first bit of xdpyinfo output on the offchance it could help someone help me work out what's happening:

name of display:    :0.0 
version number:    11.0  
vendor string:    The X.Org Foundation
vendor release number:    10600000    
X.Org version: 1.6.0                  
maximum request size:  16777212 bytes 
motion buffer size:  256              
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst                       
number of supported pixmap formats:    7            
supported pixmap formats:                           
    depth 1, bits_per_pixel 1, scanline_pad 32      
    depth 4, bits_per_pixel 8, scanline_pad 32      
    depth 8, bits_per_pixel 8, scanline_pad 32      
    depth 15, bits_per_pixel 16, scanline_pad 32    
    depth 16, bits_per_pixel 16, scanline_pad 32    
    depth 24, bits_per_pixel 32, scanline_pad 32    
    depth 32, bits_per_pixel 32, scanline_pad 32    
keycode range:    minimum 8, maximum 255            
focus:  window 0x26000f8, revert to PointerRoot     
number of extensions:    29                         
    BIG-REQUESTS                                    
    Composite                                       
    DAMAGE                                          
    DOUBLE-BUFFER                                   
    DPMS                                            
    DRI2                                            
    GLX                                             
    Generic Event Extension                         
    MIT-SCREEN-SAVER                                
    MIT-SHM                                         
    NV-CONTROL                                      
    NV-GLX                                          
    RANDR                                           
    RECORD                                          
    RENDER                                          
    SECURITY                                        
    SHAPE                                           
    SYNC                                            
    X-Resource                                      
    XC-MISC                                         
    XFIXES                                          
    XFree86-DGA                                     
    XFree86-VidModeExtension                        
    XINERAMA                                        
    XINERAMA                                        
    XInputExtension                                 
    XKEYBOARD                                       
    XTEST                                           
    XVideo                                          
default screen number:    0                         
number of screens:    1                             

screen #0:
  dimensions:    3600x1200 pixels (983x321 millimeters)
  resolution:    93x95 dots per inch                   
  depths (7):    24, 1, 4, 8, 15, 16, 32               
  root window id:    0x13c                             
  depth of root window:    24 planes                   
  number of colormaps:    minimum 1, maximum 1         
  default colormap:    0x20                            
  default number of colormap cells:    256             
  preallocated pixels:    black 0, white 16777215      
  options:    backing-store NO, save-unders NO         
  largest cursor:    64x64                             
  current input event mask:    0xfac033                
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          KeymapStateMask          ExposureMask             
    StructureNotifyMask      SubstructureNotifyMask   SubstructureRedirectMask 
    FocusChangeMask          PropertyChangeMask       ColormapChangeMask       
  number of visuals:    84                                                     
  default visual id:  0x21                                                     
  visual:                                                                      
    visual id:    0x21                                                         
    class:    TrueColor                                                        
    depth:    24 planes                                                        
    available colormap entries:    256 per subfield                            
    red, green, blue masks:    0xff0000, 0xff00, 0xff                          
    significant bits in color specification:    8 bits


Also, wow is being run in windowed mode if this makes a difference.

---

