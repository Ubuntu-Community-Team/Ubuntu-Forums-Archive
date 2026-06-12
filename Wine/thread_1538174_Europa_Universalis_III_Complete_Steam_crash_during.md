---
title: "Europa Universalis III Complete Steam crash during startup"
date: 2010-07-24
forum: Wine
---

### Post by Zorgoth on 2010-07-24
System: Dell Studio 15, wine 1.2, Ubuntu 10.04 64-bit (GNOME+compiz), ATI Mobility Radeon HD 5470

I have all my favorite games up in wine now except Europa Universalis III. I have seen lots of posts by people who have made it worked, but even following all the steps on winehq I get a runtime error during startup while it says "Loading Sounds"

Here is wine's output for EU3:

```

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not regist
ered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc}
could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33cc40,0x00000000), stub!
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x1011a
fixme:win:EnumDisplayDevicesW ((null),0,0x33df5c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e010,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_valida
te_onscreen_formats
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors no
t implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors no
t implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors no
t implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors no
t implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors no
t implemented.
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33e73c,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_valida
te_onscreen_formats
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:query_init Unhandled query type 0x4.
wine: Unhandled exception 0x40000015 at address 0x7bc90023:0x009ec627 (thread 0030), starting debugger...
fixme:winmm:MMDRV_Exit Closing while ll-driver open
err:mmtime:TIME_MMTimeStop Timer still active?!
Process of pid=002f has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
00000008 Steam.exe
        0000002a    1
        00000029    0
        00000028    0
        00000026    0
        00000024   15
        00000022    0
        00000021    0
        00000020    0
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    0
        00000009    0
0000000e services.exe
        00000014    0
        00000010    0
        0000000f    0
00000011 winedevice.exe
        00000017    0
        00000016    0
        00000013    0
        00000012    0
00000018 explorer.exe
        00000019    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```

Please help! I don't want to have to get Windows back to play this game!

---

### Post by Zorgoth on 2010-07-24
Somehow the script in winetricks that sets MaxShadowSize in DirectSound to 0 fixed my problem.  Since I had already done this, I am confused as to why it helped, but it did.  Now all I am missing is music.

---

