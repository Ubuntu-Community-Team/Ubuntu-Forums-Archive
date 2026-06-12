---
title: "SPORE - i see only the menu"
date: 2009-10-07
forum: Wine
---

### Post by LuciusMare on 2009-10-07
Hello,i had SPORE installed before i switched to ubuntu.I tried to run it,but failed,i see the menu,and nothing else (screenshot below).I blind-clicked to a planet,then i got to the "cell part" and again,just the menu,nothing else.And the intro video was also weird,i could see sometimes through the planet,and the asteroid was also half-transparent.When i run it from a terminal,there are a lot of errors,so i cant catch the first ones,they get buried under a lot of those:
```
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1173
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1968
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1173
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1968
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1173
```I googled that i have to recompile wine,and under that page in comments that i do not,just upgrade wine,but i have the newest version!Do you know what to do?

---

### Post by Incendia on 2009-10-07
It says on [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652") that is should work fine.
Is all your hardware compatible with spore?
[]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652")

---

### Post by LuciusMare on 2009-10-08
Well,as you see,it does not work.Also,I suppose that my HW is compatibile w/ SPORE,i could run it on windows.
edit: even running in safe mode does not work.

---

### Post by LuciusMare on 2009-10-08
Okay,so i did all the dance with compilling...but still the same.
edit:Also installing by wine!Nothing!Here is the log:
```
fixme:ole:CoInitializeSecurity (0x551610,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"ICQ Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x85e7d4,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:thread:SetThreadIdealProcessor (0xa0): stub
fixme:thread:SetThreadIdealProcessor (0xa8): stub
fixme:xinput:XInputGetState (0 0x2fcf1ac)
fixme:xinput:XInputGetState (1 0x2fcf1ac)
fixme:xinput:XInputGetState (2 0x2fcf1ac)
fixme:xinput:XInputGetState (3 0x2fcf1ac)
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 4124 (SPI_GETMOUSESONAR)
fixme:win:EnumDisplayDevicesW ((null),0,0x2fced80,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0x108): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x9da6138,0x9da6038): stub
fixme:thread:SetThreadIdealProcessor (0x17c): stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x9da64b0,0x9da6438): stub
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:volume:GetVolumePathNameW (L"C:\\Program Files\\Electronic Arts\\SPORE\\Sporebin\\SporeApp.exe", 0x2fceff4, 260), stub!
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:thread:SetThreadIdealProcessor (0x1a8): stub
fixme:thread:SetThreadIdealProcessor (0x1b0): stub
fixme:thread:SetThreadIdealProcessor (0x1b0): stub
fixme:thread:SetThreadIdealProcessor (0x1b4): stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmReleaseContext (0x30034, 0x15fc18): stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:imm:ImmGetOpenStatus (0x15fc18): semi-stub
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer @ surface.c / 1181
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1979
```

---

### Post by Incendia on 2009-10-09
Are you running the propriety drivers for your graphics card?
Have you seen if your hardware is compatible with Spore?
Do you have a Windows/Mac Partition on your PC so you can test the hardware on that?

[http://www.spore.com/what/specs_spore](http://www.spore.com/what/specs_spore)

---

### Post by LuciusMare on 2009-10-09
> **Incendia said:**
> Are you running the propriety drivers for your graphics card?
Have you seen if your hardware is compatible with Spore?
Do you have a Windows/Mac Partition on your PC so you can test the hardware on that?

[http://www.spore.com/what/specs_spore](http://www.spore.com/what/specs_spore)
yes i am,and for the rest,read my posts.
> **LuciusMare said:**
> Well,as you see,it does not work.Also,I suppose that my HW is compatibile w/ SPORE,i could run it on windows.
edit: even running in safe mode does not work.

---

### Post by Dullstar on 2009-10-10
If you guys can get this to work great, Windows can go to my digital dustbin!

---

