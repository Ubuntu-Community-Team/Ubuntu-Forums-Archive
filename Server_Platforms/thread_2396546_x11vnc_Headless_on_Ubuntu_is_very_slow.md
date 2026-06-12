---
title: "x11vnc Headless on Ubuntu is very slow"
date: 2018-07-17
forum: Server Platforms
---

### Post by mangocats on 2018-07-17
For what it's worth, I'm chasing the same problem: x11vnc on Ubuntu 16.04 (on a NUC 7i5) trying to run headless and I have a terribly slow refresh rate.

I've used x11vnc in many other configurations including headless and never encountered this slow refresh rate before.

FWIW, this is my .profile that launches x11vnc when the user is auto-logged in at boot time:

```
export DISPLAY=:0
xrandr --fb 1920x1080
x11vnc -usepw -shared -forever -o /var/log/x11vnc.log -bg -noxdamage -rfbport 5910 -rfbportv6 5910

```

and a sample x11vnc.log:

```

sw@inmand1-u16:/var/log$ cat x11vnc.log
17/07/2018 13:59:07 passing arg to libvncserver: -rfbport
17/07/2018 13:59:07 passing arg to libvncserver: 5910
17/07/2018 13:59:07 passing arg to libvncserver: -rfbportv6
17/07/2018 13:59:07 passing arg to libvncserver: 5910
17/07/2018 13:59:07 -usepw: found /home/sw/.vnc/passwd
17/07/2018 13:59:07 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 2189
17/07/2018 13:59:07 Using X display :0
17/07/2018 13:59:07 rootwin: 0x134 reswin: 0x4000001 dpy: 0xcc9890
17/07/2018 13:59:07
17/07/2018 13:59:07 ------------------ USEFUL INFORMATION ------------------
17/07/2018 13:59:07
17/07/2018 13:59:07 Wireframing: -wireframe mode is in effect for window moves.
17/07/2018 13:59:07   If this yields undesired behavior (poor response, painting
17/07/2018 13:59:07   errors, etc) it may be disabled:
17/07/2018 13:59:07    - use '-nowf' to disable wireframing completely.
17/07/2018 13:59:07    - use '-nowcr' to disable the Copy Rectangle after the
17/07/2018 13:59:07      moved window is released in the new position.
17/07/2018 13:59:07   Also see the -help entry for tuning parameters.
17/07/2018 13:59:07   You can press 3 Alt_L's (Left "Alt" key) in a row to
17/07/2018 13:59:07   repaint the screen, also see the -fixscreen option for
17/07/2018 13:59:07   periodic repaints.
17/07/2018 13:59:07
17/07/2018 13:59:07 XFIXES available on display, resetting cursor mode
17/07/2018 13:59:07   to: '-cursor most'.
17/07/2018 13:59:07   to disable this behavior use: '-cursor arrow'
17/07/2018 13:59:07   or '-noxfixes'.
17/07/2018 13:59:07 using XFIXES for cursor drawing.
17/07/2018 13:59:07 GrabServer control via XTEST.
17/07/2018 13:59:07
17/07/2018 13:59:07 Scroll Detection: -scrollcopyrect mode is in effect to
17/07/2018 13:59:07   use RECORD extension to try to detect scrolling windows
17/07/2018 13:59:07   (induced by either user keystroke or mouse input).
17/07/2018 13:59:07   If this yields undesired behavior (poor response, painting
17/07/2018 13:59:07   errors, etc) it may be disabled via: '-noscr'
17/07/2018 13:59:07   Also see the -help entry for tuning parameters.
17/07/2018 13:59:07   You can press 3 Alt_L's (Left "Alt" key) in a row to
17/07/2018 13:59:07   repaint the screen, also see the -fixscreen option for
17/07/2018 13:59:07   periodic repaints.
17/07/2018 13:59:07
17/07/2018 13:59:07 XKEYBOARD: number of keysyms per keycode 7 is greater
17/07/2018 13:59:07   than 4 and 51 keysyms are mapped above 4.
17/07/2018 13:59:07   Automatically switching to -xkb mode.
17/07/2018 13:59:07   If this makes the key mapping worse you can
17/07/2018 13:59:07   disable it with the "-noxkb" option.
17/07/2018 13:59:07   Also, remember "-remap DEAD" for accenting characters.
17/07/2018 13:59:07
17/07/2018 13:59:07 X FBPM extension not supported.
17/07/2018 13:59:07 X display is capable of DPMS.
17/07/2018 13:59:07 --------------------------------------------------------
17/07/2018 13:59:07
17/07/2018 13:59:07 Default visual ID: 0x21
17/07/2018 13:59:07 Read initial data from X display into framebuffer.
17/07/2018 13:59:07 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/7680
17/07/2018 13:59:07
17/07/2018 13:59:07 X display :0 is 32bpp depth=24 true color
17/07/2018 13:59:07
17/07/2018 13:59:07 ListenOnTCPPort: Address already in use
17/07/2018 13:59:07 listen6: bind: Address already in use
17/07/2018 13:59:07 Not listening on IPv6 interface.
17/07/2018 13:59:07 fb read rate: 1631 MB/sec
17/07/2018 13:59:07 fast read: reset -wait  ms to: 10
17/07/2018 13:59:07 fast read: reset -defer ms to: 10
17/07/2018 13:59:07 The X server says there are 10 mouse buttons.
17/07/2018 13:59:07 Error: could not obtain listening port.
17/07/2018 13:59:07 deleted 60 tile_row polling images.
17/07/2018 14:00:24 Got connection from client 10.74.113.178
17/07/2018 14:00:24   other clients:
17/07/2018 14:00:24 Normal socket connection
17/07/2018 14:00:24 Disabled X server key autorepeat.
17/07/2018 14:00:24   to force back on run: 'xset r on' (3 times)
17/07/2018 14:00:24 incr accepted_client=2 for 10.74.113.178:30234  sock=12
17/07/2018 14:00:24 Client Protocol Version 3.8
17/07/2018 14:00:24 Protocol version sent 3.8, using 3.8
17/07/2018 14:00:24 rfbProcessClientSecurityType: executing handler for type 2
17/07/2018 14:00:25 active keyboard: turning X autorepeat off.
17/07/2018 14:00:27 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x00000016)
17/07/2018 14:00:27 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x00000015)
17/07/2018 14:00:27 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x0000000F)
17/07/2018 14:00:27 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEC9)
17/07/2018 14:00:27 Enabling full-color cursor updates for client 10.74.113.178
17/07/2018 14:00:27 Enabling NewFBSize protocol extension for client 10.74.113.178
17/07/2018 14:00:27 Using ZRLE encoding for client 10.74.113.178
17/07/2018 14:00:29 client useCopyRect: 10.74.113.178 -1
17/07/2018 14:00:29 client_set_net: 10.74.113.178  0.0014

```

---

### Post by wildmanne39 on 2018-07-17
Moved to own thread!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

