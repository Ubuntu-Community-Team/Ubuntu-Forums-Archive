---
title: "Lineage II Disappearing Terrain and Sky"
date: 2009-06-08
forum: Wine
---

### Post by chumbucket91 on 2009-06-08
Hey everyone,
 I'm experiencing a weird graphical glitch when playing Lineage II under Wine v1.1.22, Ubuntu 8.10, with FGLRX drivers on an ATI Radeon HD 4850. It only occurs when players, NPCs, or enemies come into my viewing range, no matter how large the viewing range is. While they are fading in and partially transparent, the ground, the sky, and most static meshes completely disappear, leaving the screen mostly black. Sometimes my character will disappear too! Once they have fully spawned, however, everything returns to normal.
 Here are some example pictures of the bug:
[[IMG]http://img205.imageshack.us/img205/773/screenshotdefaultwinede.th.png[/IMG]]("http://img205.imageshack.us/my.php?image=screenshotdefaultwinede.png")
[[IMG]http://img266.imageshack.us/img266/773/screenshotdefaultwinede.th.png[/IMG]]("http://img266.imageshack.us/my.php?image=screenshotdefaultwinede.png")

 In addition, I get this error message when starting the game:
[[IMG]http://img265.imageshack.us/img265/773/screenshotdefaultwinede.th.png[/IMG]]("http://img265.imageshack.us/my.php?image=screenshotdefaultwinede.png")

 And this is all the stuff that Wine puts out:
```
chumbucket@mark-desktop:~/.wine/dosdevices/c:/Program Files/Lineage II/system$ wine loaderCT1++.exe

L2 CT1++ loader version 2.92 by M.Soltys (aka DStuff).
Tick adjustments: 12 ms / 48 ms / 5000 ms
fixme:reg:GetNativeSystemInfo (0x10a2fc3b) using GetSystemInfo()
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:thread:NtSetInformationThread info class 17 not supported yet
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:thread:NtSetInformationThread info class 17 not supported yet
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x37f902e): Stub!
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x10a99b12): Stub!
.
.................
chumbucket@mark-desktop:~/.wine/dosdevices/c:/Program Files/Lineage II/system$ fixme:process:GetProcessWorkingSetSize (0xffffffff,0x33e828,0x33e824): stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33e78c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33e824,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33a3dc,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:thread:NtSetInformationThread info class 17 not supported yet
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xa3dc6c9): Stub!
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1b34d8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33a810,0x00000000), stub!
fixme:keyboard:RegisterHotKey (0x2004a,49268,0x00000001,27): stub
fixme:imm:ImmReleaseContext (0x2004a, 0x146358): stub
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:d3d:state_patchedgestyle (WINED3DRS_PATCHEDGESTYLE,1065353216) not yet implemented

```So here are my questions:
1) I looked up how to enable ATI's AGP, and apparently there's a "smartgart" application that I could run in the Windows Catalyst Control Center, but where's it's Linux equivalent? Or does it even exist?
2) There weren't any similar bug reports that I could find in Lineage II's bug list on the Wine website, but are there similar issues with other games that could point me in the right direction?
[s]3) Does anyone know of any Lineage II settings that I can enable or disable that will prevent other characters from fading in and out, so that I won't have this problem?[/s] Scratch that, a cursory glance through L2.ini revealed that there aren't any settings I can change to stop transparency effects from displaying. :\
4) Any other ideas to fix this bug? XD

Thanks for the help! If there's any other information that I forgot to provide, let me know. It's really annoying to play L2 with this glitch, and I worked so hard to get it working at all, so I'd like it to work perfectly if possible.

---

### Post by chumbucket91 on 2009-06-12
Bump for justice and popcorn. :popcorn: (I didn't see any anti-bumping rules, but if I missed one and this is an inappropriate bump, sorry!)
If no one has any ideas, are there any forums that I could go to in order to get help? I asked on other Lineage II-related forums and they told me to go here 'cause they only dealt with Windows technical issues, not Linux/Wine ones.

---

### Post by whogivesaskit on 2010-05-14
i have the same problem...

---

