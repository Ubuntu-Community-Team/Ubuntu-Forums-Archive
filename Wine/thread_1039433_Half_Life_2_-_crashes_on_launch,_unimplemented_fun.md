---
title: "Half Life 2 - crashes on launch, unimplemented function vstdlib_s.dll?"
date: 2009-01-14
forum: Wine
---

### Post by edmonds on 2009-01-14
hi
i've been trying  to get half life 2 running  in  wine.
just upgraded to ubuntu 8.10. Wine 1.01.
DID:
[HKEY_CURRENT_USER\Software\Wine\Direct3D] 
"DirectDrawRenderer"="opengl" "OffscreenRenderingMode"="backbuffer" "PixelShaderMode"="enabled" "UseGLSL"="disabled" "VertexShaderMode"="hardware" "VideoMemorySize"="512"

GET THIS:
:~/.wine/drive_c/Program Files/Valve/Steam$ WINEDEBUG=fixme-all wine steam.exe -applaunch 220 -novid -window -console -dxlevel 81 -width 1024 -height 768 -heapsize 1024000 -refresh 60
err:ntdll:RtlpWaitForCriticalSection section 0x7bc932a4 "loader.c: loader_section" wait timed out in thread 001f, blocked by 0009, retrying (60 sec)
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 242 servers.
CellID: Connecting to 119.167.242.103:27031. . .
CellID: Connect to 119.167.242.103:27031 took 392 MS
CellID: Nothing beat our old best time of 41 MS
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
wine: Call from 0xea894d3 to unimplemented function vstdlib_s.dll.Q_CopyAndFixSlashes, aborting


Any ideas what i am doing  wrong?

thanks
tom

---

### Post by cogadh on 2009-01-14
Do you have desktop effects enabled? If so, disable them, it will interfere with Wine.

BTW - Next time, you might want to use the forum ```
 tags when you post terminal output. It makes reading it much easier:
[code]:~/.wine/drive_c/Program Files/Valve/Steam$ WINEDEBUG=fixme-all wine steam.exe -applaunch 220 -novid -window -console -dxlevel 81 -width 1024 -height 768 -heapsize 1024000 -refresh 60
err:ntdll:RtlpWaitForCriticalSection section 0x7bc932a4 "loader.c: loader_section" wait timed out in thread 001f, blocked by 0009, retrying (60 sec)
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 242 servers.
CellID: Connecting to 119.167.242.103:27031. . .
CellID: Connect to 119.167.242.103:27031 took 392 MS
CellID: Nothing beat our old best time of 41 MS
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
wine: Call from 0xea894d3 to unimplemented function vstdlib_s.dll.Q_CopyAndFixSlashes, aborting
```

---

### Post by edmonds on 2009-01-14
hi cogadh
just checked in  Appearance and i have No Visual Efects selected.
sorry about the code, i don't know what 'forum [code] tags' are.

tom

---

### Post by cogadh on 2009-01-14
> **edmonds said:**
> hi cogadh
just checked in  Appearance and i have No Visual Efects selected.
Have you disabled the Steam Community features in Steam before launching the game? That used to cause crashes like you describe, but I thought it was fixed in Wine already (could be wrong about that, though)
> sorry about the code, i don't know what 'forum [code] tags' are.
Its BBCode, kind of like HTML that you can insert into your posts to do different things like make text **bold** or [color=red]colored[/color]:
[http://ubuntuforums.org/misc.php?do=bbcode]("http://ubuntuforums.org/misc.php?do=bbcode")

---

### Post by edmonds on 2009-01-15
hi
Steam Community features in Steam is and was disabled.

what does vstdlib_s.dll, are there any clues there?

tom

---

### Post by cogadh on 2009-01-15
Not really, that DLL is supposedly related in some way to Steam's online components, hence why I asked about the Community Features, but I am not aware of what it actually does.

Considering that vstdlib_s.dll error was the last error in a string of errors, this could be a cascading effect, where one or more of the previous errors actually caused the error in vstdlib_s.dll. Most of the previous errors are 3D related, so it could indicate a problem with your graphics card or drivers. What do you have for a graphics card?

You launched the game with quite a few option flags on it, which adds some additional wrinkles to the problem. Are all of those really required? Have you tried running the game with just the "dxlevel" flag set? BTW - that "-heapsize" one appears to be inaccurate. If you were trying to tell the game to use 1GB of RAM, the number you should use is 1048576.

Lastly, the registry edits. HL2 should run fine without adding any of those. In fact, the only registry edit I am aware of that might be required is ""OffscreenRenderingMode"="fbo" instead of "OffscreenRenderingMode"="backbuffer".

---

### Post by edmonds on 2009-01-15
ok
i deleted the edits i n regedit. i restarted with:
WINEDEBUG=fixme-all wine steam.exe -applaunch 220 -dxlevel 81 -window -console -width 1024 -height 768

still got to Loading when it crashes.

Here's the stuff (sorry not coded properly, i don't really ge that):

~/.wine/drive_c/Program Files/Valve/Steam$ WINEDEBUG=fixme-all wine steam.exe -applaunch 220 -dxlevel 81 -window -console -width 1024 -height 768
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 233 servers.
CellID: Connecting to 117.121.248.125:27031. . .
CellID: Connect to 117.121.248.125:27031 took 408 MS
CellID: Nothing beat our old best time of 47 MS
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0xacdfa4 "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F


so its still this d3d.

i have a geforce 9600gt and nvidia driver 177.82

---

