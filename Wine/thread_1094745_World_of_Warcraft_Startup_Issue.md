---
title: "World of Warcraft Startup Issue"
date: 2009-03-12
forum: Wine
---

### Post by SuperNapalm on 2009-03-12
Got a problem starting up wow.
Installing went fine (using Wine 1.1.6 btw), patching went okay too but every time i try to start the game i get this error...

[http://img7.imageshack.us/my.php?image=errora.png](http://img7.imageshack.us/my.php?image=errora.png)

Worth noting I can hear sound in the background.

My PC Specs:
Intel Pentium D 945 3.4ghz
2gb ram
Sapphire Radeon 4670

Any ideas what's going on?

---

### Post by hikaricore on 2009-03-13
Are your video drivers properly installed?

What error output do you get when running the game from a terminal?

---

### Post by SuperNapalm on 2009-03-13
```
john@john-desktop:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x13c510)->(0x32db60)
fixme:shdocvw:OleControl_FreezeEvents (0x13c510)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x13c510)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x13cb18): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d238): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d238): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13da78): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13da78): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13da78): WIN32_FIND_DATA is not yet filled.
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mshtml.dll"
err:ole:CoGetClassObject no class object {25336920-03f9-11cf-8fd0-00aa00686f13} could be created for context 0x3
err:shdocvw:http_load_hack Could not create HTMLDocument: 80040154
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x13c510)
fixme:shdocvw:OleObject_Close (0x13c510)->(1)
fixme:shell:DllCanUnloadNow stub
john@john-desktop:~$ fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x3aedbc,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x3aebe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af2ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af408,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x13de40) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

```

Thats the output I get running from a terminal, loaded the launcher, clicked Play and then I get that error in the first post. Just ended the process afterwards.

As for the drivers I installed the ones from the ATI site and I think they're installed correctly.

I ran fglrxinfo and got
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4670
OpenGL version string: 2.1.8494 Release

```

---

### Post by SuperNapalm on 2009-03-13
Anyone?
Would be nice to get this sorted before my raid starts tonight :P

---

### Post by Pikestaff on 2009-03-13
I was getting that error on a fairly regular basis until recently, usually it happened at specific points (mage tables being summoned, last boss in Gundrak turning into a rhino).  Why it was doing that I have no idea but a complete reinstall of the game fixed it >.>

I think it is an OpenGL thing since the only people I've heard of having this problem or similar problems are Mac/Linux users (OpenGL) or Windows users using OpenGL.

---

### Post by SuperNapalm on 2009-03-13
Thing is I havern't even managed to get into the game AT ALL :/ . Havern't turned on OpenGl as far as I'm aware. I've tried with both the Ubuntu provided drivers and the ones provided by ATI, get same error.
Also I cant open any options in the launcher, half the window turns gray and freezes...

---

### Post by hikaricore on 2009-03-13
Don't start the game from the launcher.. run WoW.exe directly.

Make sure you disable all desktop effects before trying to launch the game, and if you havn't enabled opengl mode please do so.

---

### Post by SuperNapalm on 2009-03-13
Turns out turning on OpenGl fixed it ><
Cursor wouldnt appear but set it to my usual resolution and it was fine.
Dalaran is laggy although on Maggy thats not a unusual occurance.

---

### Post by Pikestaff on 2009-03-13
Well you should try OpenGL if you can, because that's how WoW runs best in Linux most of the time.  Just add **SET gxApi "opengl"** to your Config.wtf.  Though if you haven't been able to get into the game at all I dunno if you'd have a Config.wtf file yet =/  ATI is known for being tricky to get working, best of luck though.

Edit: Haha, see you fixed it right as I posted.  Glad you got it all figured out.  Good luck with your raid :)

---

### Post by hikaricore on 2009-03-13
Fantastic that you got it working!

There are several guides around for increasing your framerate and such, you may wanna try them out after you get through your raid. :p
You may also want to look into overclocking your video card if ati has such an option, it always helped me squeeze out 5-10fps more on my nvidia card.

---

### Post by SuperNapalm on 2009-03-13
On Windows you could but not on Ubuntu it seems :/
It is lagging quite a bit so I'll check around for some guides :)

---

