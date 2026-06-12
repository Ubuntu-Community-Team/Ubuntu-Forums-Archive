---
title: "wine/game error"
date: 2010-12-16
forum: Wine
---

### Post by smupid on 2010-12-16
OK so i gave up on installing fable since i have yet to figure that out
but i tried one of my very old PC games
called "_Siege Of Avalon_"
anyways i got wine to finish the install on it 
but when i got to play the game
it gives me and error.

something about **binkplay.exe**

```

military@military-desktop:~$ wine /home/military/.wine/dosdevices/c:/windows/SOA/SoA_CD.exe
fixme:shell:IShellLinkA_fnGetPath (0x196f28): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x195c38): WIN32_FIND_DATA is not yet filled.
military@military-desktop:~$ fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x130460,0x130380): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1304b8,0x1303b8): stub
fixme:d3d_caps:wined3d_guess_card_vendor Received unrecognized GL_VENDOR "VIA Technology". Returning HW_VENDOR_NVIDIA.
fixme:d3d_caps:select_card_nvidia_mesa Card selection not handled for Mesa Nouveau driver
fixme:win:EnumDisplayDevicesW ((null),0,0x33e4a8,0x00000000), stub!
m Files\Digital Tome\Siege Of Avalon\BinkPlay.exe: main/renderbuffer.c:2067: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
wine: Assertion failed at address 0x7c2da832 (thread 003b), starting debugger...
fixme:dbghelp_dwarf:compute_location Only supporting one breg (18 -> 24)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1445f8,0x1444f8): stub
fixme:dmime:IDirectMusicPerformance8Impl_Init (iface = 0x164c18, dmusic = (nil), dsound = (nil), hwnd = (nil))
fixme:dmime:IDirectMusicPerformance8Impl_AddPort (0x164c18, (nil)): stub
err:dmloader:IDirectMusicLoaderImpl_IDirectMusicLoader_SetObject : could not attach stream to file
fixme:d3d_caps:wined3d_guess_card_vendor Received unrecognized GL_VENDOR "VIA Technology". Returning HW_VENDOR_NVIDIA.
fixme:d3d_caps:select_card_nvidia_mesa Card selection not handled for Mesa Nouveau driver
fixme:win:EnumDisplayDevicesW ((null),0,0x11cf3d8,0x00000000), stub!
BU\DIGI~VKQ\SIEG~SSX\DTMain1.exe: main/renderbuffer.c:2067: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.



```

---

### Post by smupid on 2010-12-17
guessing no one has any input on this?
well if i figure it out ill post it here
will be checking in and out occasionally.

---

### Post by smupid on 2010-12-18
well i guess im just gonna go install a windows into my laptop and use that for the games since i have yet to find one game that works for my new linux version

---

