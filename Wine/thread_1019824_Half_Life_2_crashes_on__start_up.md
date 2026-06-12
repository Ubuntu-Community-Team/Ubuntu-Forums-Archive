---
title: "Half Life 2 crashes on  start up"
date: 2008-12-23
forum: Wine
---

### Post by edmonds on 2008-12-23
hi 
i think i have installed Half Life 2 correctly, My Steam works.
But when i start half life it gets as far as the loading  page and then goes back to the desk top.

The is what my terminal says:
:~$ cd .wine/drive_c/Program\ Files/Valve/Steam
:~/.wine/drive_c/Program Files/Valve/Steam$ WINEDEBUG=fixme-all wine steam.exe -applaunch 220 -novid -dxlevel 81 -width 1024 -height 768 -fullscreen -heapsize 1024000 -refresh 60 +map_background none "$@"

err:ntdll:RtlpWaitForCriticalSection section 0x7bc906e4 "loader.c: loader_section" wait timed out in thread 0020, blocked by 0009, retrying (60 sec)
CellID: Fetching server list from CSDS. . .
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
CellID: CSDS returned 217 servers.
CellID: Connecting to 208.111.158.50:27031. . .
CellID: Connect to 208.111.158.50:27031 took 276 MS
CellID: Nothing beat our old best time of 46 MS
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

thats as far as it goes.
thanks
tom

---

