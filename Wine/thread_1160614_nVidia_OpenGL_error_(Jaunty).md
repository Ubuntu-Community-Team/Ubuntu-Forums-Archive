---
title: "nVidia OpenGL error (Jaunty)"
date: 2009-05-15
forum: Wine
---

### Post by abhiroopb on 2009-05-15
In Hardy and Intrepid I installed Counter-Strike Condition Zero using wine and it worked fine. I had proprietary nVidia drivers installed then.

Today I installed the same game in Jaunty. I am using nVidia driver 180, which seems to be the latest one in the repository. When I start the game, I get the following error in the terminal:

```

$ wine "/home/abhiroop/.wine/drive_c/Valve/Condition Zero/hl.exe" -game czero 
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x9a4, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5ec,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1440x900x32 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x16 @0! (XRandR)

```

And I also get a pop-up box saying:
"Video mode is not supported. The game will now run in Software mode." 

Clicking OK causes the error again and click Cancel closes everything.

I uninstalled all nvidia related drivers and ran the game and it ran fine.

Therefore, it appears as though there is some problem with Jaunty, the proprietary nVidia drivers and OpenGL.

Can anyone help?

UPDATE: I have attached the output for "glxinfo".
UPDATE: I have attached my xorg.conf file.

---

### Post by DavidFromCanada on 2009-08-15
Hey I have this same problem, did you find a solution?

---

### Post by abhiroopb on 2009-08-16
Hey...

Yes I did figure it out. Unfortunately, I have no idea what it is specifically! Actually I don't even remember this thread!

What I would suggest is adding metamodes to your xorg.conf file. I use dual monitors and this turns of my laptop monitor and I play on my external screen.

I added the following line to Screen "Section":
```

Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1440+0; CRT: 1440x900+0+0,NULL"

```

Let me know if this helps.

---

### Post by DavidFromCanada on 2009-08-16
I appreciate your help but I have an intel graphics card on my eee PC (800x480 res). To play any games I need to have them set in a 640x480 resolution, so none of my games that did work in Intrepid work. I'll see if there is an intel equivalent xorg config of the one you gave me.

---

