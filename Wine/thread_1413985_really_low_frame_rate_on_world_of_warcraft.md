---
title: "really low frame rate on world of warcraft"
date: 2010-02-23
forum: Wine
---

### Post by Arminius on 2010-02-23
I'm using wine version 1.1.38
and Ubuntu of course, and I'm getting about 1 frame every 30 seconds, so is there a definitive installation instruction for wow on Ubuntu?

---

### Post by Arminius on 2010-02-23
the log in window comes up as per normal
but it really is one frame around every minute.

---

### Post by Arminius on 2010-02-23
bump

---

### Post by Arminius on 2010-02-24
bump

---

### Post by overdrank on 2010-02-24
Hi and please be patient, do not bump so quickly. :) Moved to Wine

---

### Post by brt on 2010-02-24
have a look at this:

[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine")

---

### Post by Arminius on 2010-02-24
I'm afraid that wasn't helpful
but I did try running the game from terminal, and it did come up with alot of code that someone might find useful in diagnosing the problem?

```
user@HAL9000:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50727.762 / 8.0.50727.4053
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\World of Warcraft\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed4c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea68,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f250,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f474,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x39efa8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0e0,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1bfb70,0x1bfa70): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f7b8): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f7b8): stub
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39de8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39deb4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39dd64,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404584) using GetSystemInfo()
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGenTextures @ basetexture.c / 252
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d_surface:surface_load_ds_location No up to date depth stencil location
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGenTextures @ basetexture.c / 252
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGenTextures @ basetexture.c / 252
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGenTextures @ basetexture.c / 252
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:imm:ImmReleaseContext (0x30030, 0x1852e0): stub
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffers() @ context.c / 2092
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:state_zwritenable >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDepthMask(0) @ state.c / 205
fixme:d3d_shader:gen_arbfp_ffp_shader >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glProgramStringARB() @ arb_program_shader.c / 5904
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d_shader:fragment_prog_arbfp >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glBindProgramARB(GL_FRAGMENT_PROGRAM_ARB, desc->shader) @ arb_program_shader.c / 5982
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d_shader:fragment_prog_arbfp >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glBindProgramARB(GL_FRAGMENT_PROGRAM_ARB, desc->shader) @ arb_program_shader.c / 5982
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d_shader:fragment_prog_arbfp >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glBindProgramARB(GL_FRAGMENT_PROGRAM_ARB, desc->shader) @ arb_program_shader.c / 5982
fixme:d3d_shader:state_arb_specularenable >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glProgramEnvParameter4fvARB(GL_FRAGMENT_PROGRAM_ARB, ARB_FFP_CONST_SPECULAR_ENABLE, col) @ arb_program_shader.c / 5363
fixme:d3d_shader:fragment_prog_arbfp >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glBindProgramARB(GL_FRAGMENT_PROGRAM_ARB, desc->shader) @ arb_program_shader.c / 5982
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:d3d_shader:fragment_prog_arbfp Out of memory
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:d3d_shader:fragment_prog_arbfp Out of memory
fixme:d3d:loadVertexData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glBindBufferARB @ state.c / 4288
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d_shader:state_arb_specularenable >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glProgramEnvParameter4fvARB(GL_FRAGMENT_PROGRAM_ARB, ARB_FFP_CONST_SPECULAR_ENABLE, col) @ arb_program_shader.c / 5363
fixme:d3d_shader:fragment_prog_arbfp >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glBindProgramARB(GL_FRAGMENT_PROGRAM_ARB, desc->shader) @ arb_program_shader.c / 5982
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3525
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:d3d9:IDirect3DDevice9Impl_CreateIndexBuffer Failed to allocate buffer memory.
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:d3d9:IDirect3DDevice9Impl_CreateIndexBuffer Failed to allocate buffer memory.
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:d3d9:IDirect3DDevice9Impl_CreateIndexBuffer Failed to allocate buffer memory.
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:stretch_rect_fbo >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glReadBuffer() @ device.c / 5836
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
fixme:d3d:buffer_Unmap >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFlushMappedBufferRange @ buffer.c / 1181
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:heap:HEAP_GetPtr Invalid heap 0x110000!
fixme:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffers() @ context.c / 2092
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:heap:HEAP_GetPtr Invalid heap 0x110000!
err:heap:HEAP_GetPtr Invalid heap 0x110000!
wine: Unhandled page fault on read access to 0xbed821cc at address 0x7c638f6c (thread 0009), starting debugger...
err:heap:HEAP_GetPtr Invalid heap 0x110000!
wine client error:9: read: Bad address
Killed

```

---

### Post by Mark Phelps on 2010-02-24
> **Arminius said:**
> I'm using wine version 1.1.38
and Ubuntu of course, and I'm getting about 1 frame every 30 seconds, so is there a definitive installation instruction for wow on Ubuntu?

Are you getting this slow frame rate all the time? Or only when attempting to run games in Wine?

IF the latter, what video card/chip are you using?  If it's one of the "legacy" ATI cards/chips, you're using the open source drivers and you're not going to get decent gaming frame rates.

---

### Post by Arminius on 2010-02-24
I'm only trying to run wow on wine.
It's not the hardware cause I've run wow under wine on this computer before and it worked fine.

not sure what but something is missing with this install.

---

### Post by Arminius on 2010-02-25
bump

---

### Post by cburner on 2010-02-25
Are you using opengl or Direct X rendering? If you are using Direct X (not really that stable), try adding -opengl to your command line as in:

```
user@HAL9000:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
```

---

### Post by pedro_orange on 2010-02-26
> **cburner said:**
> Are you using opengl or Direct X rendering? If you are using Direct X (not really that stable), try adding -opengl to your command line as in:

```
user@HAL9000:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
```

Yes it seems he's running under d3d (according to the terminal log)
I would highly recommend using -opengl (and if the sound is annoying you -nosound)

OP; have you seen this before? It's an entire "How to install / troubleshoot" 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Also, be more patient. Bumping your post all the time is only going to get it ignored.

---

### Post by DoktorSeven on 2010-02-26
> **Arminius said:**
> I'm only trying to run wow on wine.
It's not the hardware cause I've run wow under wine on this computer before and it worked fine.

not sure what but something is missing with this install.

Even though you've played it on this computer before, you might still be having issues with graphics drivers now.  Be *sure* you have the proper graphics drivers working for your card (fglrx for ATi, nvidia for, well, NVidia) and that **glxinfo | grep direct** comes back with "direct rendering: Yes".  If you're using open-source drivers, any card other than modern ATi/nvidia, or your 3d is misconfigured in any way, you're going to get slow graphics, period.

Also, as others noted, make sure you're using OpenGL for WoW, but really, using D3D won't make it run horribly slow -- the only thing that really does that is misconfigured 3d acceleration as I noted.  So I'd investigate that even if you might think that it *should* be working, because it certainly seems like it is not.

---

### Post by Arminius on 2010-02-26
bump

---

### Post by Arminius on 2010-02-26
ignore that bump, I saw no replies even after I refreshed the page, it had been a day since the previous bump, but after I bumped it a lot of replies suddenly show up.
sorry if my bumps are alot, just not able to do dailys :(

---

### Post by Arminius on 2010-02-26
> **DoktorSeven said:**
> Even though you've played it on this computer before, you might still be having issues with graphics drivers now.  Be *sure* you have the proper graphics drivers working for your card (fglrx for ATi, nvidia for, well, NVidia) and that **glxinfo | grep direct** comes back with "direct rendering: Yes".  If you're using open-source drivers, any card other than modern ATi/nvidia, or your 3d is misconfigured in any way, you're going to get slow graphics, period.

Also, as others noted, make sure you're using OpenGL for WoW, but really, using D3D won't make it run horribly slow -- the only thing that really does that is misconfigured 3d acceleration as I noted.  So I'd investigate that even if you might think that it *should* be working, because it certainly seems like it is not.

thank you dok, that was the prob, never occured to me that there might be a problem with the video driver since I was running video files just fine.

Still a few problems with bits of the screen not showing up but I'll open a new thread for that.

thanks

---

