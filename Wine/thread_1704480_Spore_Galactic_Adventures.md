---
title: "Spore Galactic Adventures"
date: 2011-03-10
forum: Wine
---

### Post by Joseph Schwenker on 2011-03-10
I'm trying to run Spore Galactic Adventures on Wine 1.3.15, but I get an error asking for the disk, even though the game loads fine. I have the disk in the drive, and even tried re-inserting it. This is the terminal output.

```
fixme:thread:SetThreadIdealProcessor (0x84): stub
fixme:thread:SetThreadIdealProcessor (0x8c): stub
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 4124 (SPI_GETMOUSESONAR)
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee30,0x00000000), stub!
ERROR: 
	Could Not Find D3DKMTEscape in gdi32.dll
	Could Not Find D3DKMTOpenAdapterFromHdc in gdi32.dll
ERROR: 
	Could Not Find D3DKMTEscape in gdi32.dll
	Could Not Find D3DKMTOpenAdapterFromHdc in gdi32.dll
fixme:thread:SetThreadIdealProcessor (0x120): stub
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x89d, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xc3322e8,0xc332208): stub
fixme:thread:SetThreadIdealProcessor (0x1b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xcf95dd8,0xcfa21a0): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x500dc, 0x142fb0): stub
fixme:volume:GetVolumePathNameW (L"C:\\Program Files\\Electronic Arts\\SPORE_EP1\\SporebinEP1\\SporeApp.exe", 0x32efe8, 260), stub!
fixme:thread:SetThreadIdealProcessor (0x1e4): stub
fixme:thread:SetThreadIdealProcessor (0x1ec): stub
fixme:thread:SetThreadIdealProcessor (0x1ec): stub
fixme:thread:SetThreadIdealProcessor (0x1f0): stub
fixme:imm:ImmGetOpenStatus (0x142fb0): semi-stub

```

Any ideas how to get Wine to recognize the disk in the drive?

---

### Post by Joseph Schwenker on 2011-04-14
For anyone encountering this thread in the future, you may want to try following the instructions of someone from Wine AppDB.

> And now I too have worked it out ;-) 

For those that come across this in the future the trick is to open your wine config and mount the cd path from linux in the "drives" tab (in my case I mounted /media/SC4DELUXE2 as d:)

I'm not sure if these even work, but it's worth a shot.

---

