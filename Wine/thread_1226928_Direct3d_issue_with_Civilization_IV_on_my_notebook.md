---
title: "Direct3d issue with Civilization IV on my notebook"
date: 2009-07-30
forum: Wine
---

### Post by mtausig on 2009-07-30
Hy!

I am running Civilization IV (plus extensions) succesfully on my desktop PC under wine. Now, I wanted to play on my notebook as well and simply copied the installation folder from the PC to the notebook.

The problem is, that the graphics do not work. If I run the game in full screen mode, the screen turns black and a few seconds later, X crashes and I am returned to the gdm login screen. If I run the game in windowed mode, the opening animations and the menu are loaded and displayed, but the graphics in the wine window are flickering horrible so that almos nothing can be seen.

The configuration is set to use the wine-builtin versions of D3D8 and D3D9, the rest of the graphic libraries used are the native ones.

The notebook is a Lenovo X200 with an INtel GMA4500MHD chip running ubuntu intrepid and wine 1.0.1

Here is the output of wine:

```

fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
[Repeated]
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Logs.lnk
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
[Repeated]
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
[Repeated]
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
[Repeated]
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\CivilizationIV.ini.lnk
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x60026 0x00000000
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
[Repeated]
'import site' failed; use -v for traceback
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:win:EnumDisplayDevicesW ((null),0,0x32efb8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4f0,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xaf34140) : stub
[Repeated]
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
[Repeated]
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0xaf34140) : stub
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet

```

I assume, that the "err:d3d:getColorBits Unsupported format: xxx" lines are the cause of the problem, but I do not know what to make of them.

Any suggestions what to do?

cheers
Mathias

---

### Post by jacksaff on 2009-07-30
Installing civ4 on your laptop and copying your saves across might work better.
Is your laptop graphics chip fast enough to run civ4? You might need to turn down a lot of detail. Civ4 is surprisingly resource hungry in the graphics department.

---

### Post by mtausig on 2009-07-30
The notebook doesn't have an optical drive, which makes a reinstallation problematic. I know that I could use an Iso image, but the whole installation procedure (game+patch+extension+patch+nocd) is a bit of a pain in the ***, so I would like to reuse the existing and working installation.

As for the speed: I don't know, but since it works on my Desktop PC with the onboard graphic chip, I assume it will work with the notebook as well. But I am not even getting as far as seein the speed of the game.

---

### Post by S0m3th1ngw13rd on 2009-07-30
It could be that the GPU in your laptop can't handle Civ IV, check out link.

[http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-4500MHD-GMA-X4500MHD.9883.0.html](http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-4500MHD-GMA-X4500MHD.9883.0.html)

Not sure if this is issue but its what I would lean toward.

---

### Post by mtausig on 2009-07-31
Do you really think, that a too slow graphic card can result in corrupted images and an X-server crash? That strikes me kind of funny.

---

### Post by ArmenianLeader4 on 2009-07-31
Do you get the problem at startup or during gameplay? 
If it was at startup, you could try re-installing its because it looks to me as though wine is unable to decipher the specialty cursors needed throughout the game.

If it happens during gameplay, it could be your CPU. you should check to make sure you have the minimum requirements on your computer. Alot of laptops arent able to handle the amount of memory needed to run complex games like Civ4. You can try clearing some ram or something, but as far as that goes, you're on your own.

---

