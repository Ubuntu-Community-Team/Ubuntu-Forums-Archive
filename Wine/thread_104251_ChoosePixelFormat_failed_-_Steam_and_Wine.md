---
title: "ChoosePixelFormat failed - Steam and Wine"
date: 2005-12-15
forum: Wine
---

### Post by kerm on 2005-12-15
I was exited to get Steam to run as well as getting Half-Life going (under Software mode at least) using the guide from: [HTML]http://appdb.winehq.org/appview.php?versionId=1554[/HTML] 
But I am having some serious issues. First of all, despite having 3D acceleration up-and-running on my nVidia card, I can't get Half_Life to run in OpenGL mode while D3D mode just crashes Wine. When I try to get into OpenGL mode, I get a pop-up box that says "ChoosePixelFormat failed" and then the game resets to Software mode.

If that's not all, check this screenshot...it's like this all the time...even when I launch directly into the game (-applaunch 70), the Gnome toolbars are still present:

[IMG]http://home.comcast.net/~cjpennell/Screenshot-1.png[/IMG]

Also, here is what Wine is complaining about to my console:
```

fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows ve rsion to 'nt40' or 'win31'.
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not regist ered
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0 -8fcf-00aa006bcc59}, hres is 0x80040154
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at  the moment!
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
[COLOR="Blue"]*Note: About a few dozen of the above line*[/COLOR]
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe3e120)->(00000000,00000008 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe3e120)->(00000000,00000013 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe3fe78)->(0003009c,00000013 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe3fe78)->(0003009c,00000013 )
fixme:wave:DSD_CreateSecondaryBuffer (0x7ab762d8,0x7fb1f754,28,0,0x7ab7db4c,0x7a b75bf4,0x7ab7db28): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x7ab762d8,0x7feabe6c,180e0,0,0x76b53874,0 x7feac0dc,0x76b53850): stub
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
err:dsound:DSOUND_MixOne underrun on sound buffer 0x76b53828
fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows ve rsion to 'nt40' or 'win31'.
fixme:wave:DSD_CreateSecondaryBuffer (0x7ab762d8,0x76b79164,180e0,0,0x76bb58d4,0 x76ba515c,0x76bb58b0): stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe11898)->(00000000,00000008 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe11898)->(00000000,00000013 )
err:opengl:X11DRV_ChoosePixelFormat glXChooseFBConfig returns NULL (glError: 0)
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe164c8)->(00000000,00000008 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe164c8)->(00000000,00000013 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe176d0)->(0006002a,00000013 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe176d0)->(0006002a,00000013 )
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:wave:DSD_CreateSecondaryBuffer (0x76bfaf18,0x7fb1f754,28,0,0x76c0bd4c,0x76 c0c434,0x76c0bd28): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x76bfaf18,0x7fea963c,180e0,0,0x7fea98d4,0 x7fe9d8b4,0x7fea98b0): stub
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows ve rsion to 'nt40' or 'win31'.
err:dsound:DSOUND_MixOne underrun on sound buffer 0x76c0bd00
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fea9888
err:dsound:DSOUND_MixOne underrun on sound buffer 0x76c0bd00
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fea9888
err:dsound:DSOUND_MixOne underrun on sound buffer 0x76c0bd00
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fea9888

```

I hope this all my sense...the point is I want to play Half-Life under OpenGL mode without all the GUI clutter. Please help even if maybe you know the answer to only part of the problem.

Thanks,
kerm

---

### Post by Kebabji on 2005-12-29
i have the same "choosepixelformat failed" error - i'm runnign with an ati mobility m6 ly and kde, but have found no solution yet :/

---

### Post by Peksi on 2005-12-29
I had same problem with nvidia. I only reinstalled nvidia drivers and it started to work..

---

### Post by kerm on 2005-12-30
I talked to one one of the Wine HL2 maintaners on irc about a week ago and he basically said that I would probably have to put up with the problems until they iron out the kinks on their end (at least I'm not alone regarding these issues)...but he wasn't sure what I could do in the meantime.  

I haven't tried doing a clean reinstallation of nvidia drivers but it's worth a shot. Also, I read that some people switch to a lighter windows manager (like fluxbox or something like that) before they run steam games and that helps. There's also some X config stuff that one may try, but that potentially presents it's own problems.

As for me, I uninstalled Wine and Steam for right now. I decided to try Quake2 multiplayer for the first time and it's really the closest thing I've found in Linux to the fun I have playing HLDM and Opposing Force. Still, I miss all the HL mods like Sven Coop and "Pirates, Vikings and Knights" but if I need to, I can run to the Windows box in the cold, dark basement anytime for a quick fix I suppose. :neutral:

---

### Post by fkm on 2007-08-28
I only have this problem when trying to start a Steamapp in Compiz-Fusion and Beryl.
Otherwise (normal KDE and empty session with only wine started) everything works just fine. Well not everything, everything. But almost ;)

---

