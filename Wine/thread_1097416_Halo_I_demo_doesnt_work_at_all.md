---
title: "Halo I demo doesnt work at all"
date: 2009-03-15
forum: Wine
---

### Post by Meow27 on 2009-03-15
despite what the appdb says the first halo demo keeps crashing when i run it. 

the install worked perfectly. but the game doesnt

```
~/.wine/drive_c/Program Files/Microsoft Games/Halo Trial$ wine halo.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32d394,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cf0c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32bc8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32bd2c,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32d5e4,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x1fd180) : stub
fixme:imm:ImmReleaseContext (0x4002a, 0x13a448): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x13a448): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (-4,-23)-(804,604)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x9d5a2b0,0x9d855b8): stub
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1457
fixme:d3d:state_multisampmask (WINED3DRS_MULTISAMPLEMASK,0) not yet implemented
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_shader:shader_arb_generate_vshader HW VertexShader Error at position 2054: "Too many parameter variables"
fixme:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1457
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 260
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
intel_batchbuffer.c:145: intel_flush_inline_primitive: Assertion `intel->prim.primitive != ~0' failed.
DRM_I830_CMDBUFFER: -22

```

edit- this problem persists in 1ine 1.1.16-7

---

### Post by Vrekk on 2009-03-16
[http://ubuntuforums.org/showthread.php?t=486986](http://ubuntuforums.org/showthread.php?t=486986)
OR you can try running it on Crossover game, most things work in 7.1.1 and EVERTHING works in 7.2 which will be released soon

---

### Post by hikaricore on 2009-03-16
> Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
intel_batchbuffer.c:145: intel_flush_inline_primitive: Assertion `intel->prim.primitive != ~0' failed.
DRM_I830_CMDBUFFER: -22

Your intel video chipset is likely the issue.
Do other 3d games work on your system?  Native or through WINE?

You may want to consider buying an actual video card for gaming on Linux.

---

### Post by Meow27 on 2009-03-16
im using a laptop so im stuck with an intel card.

its a 3 year old computer so im sure it can run 3d programs. 

but now that you mention it. when i play bzflag here, (natively on linux) it is really slow (my cpu is 1.7 ghz)

but ill test it on windows to see if your assumption is true

edit
i have an intel 915gm, it supports directx9 so i assume that it is perfectly suitable for 3d

---

### Post by hikaricore on 2009-03-16
It may be perfectly suitable for 3d in Windows, but Intel chipsets are notorious for being hit and miss under Linux.

Thank Intel for crappy hardware and drivers.
Check around the fourm for things to try with your intel card/drivers, best of luck.

---

### Post by psysiu on 2009-03-17
```
Mesa 7.2 implementation error: i915_program_error: Exceeded max nr indirect text
ure lookups

```
I've got the same error with Digital Paintball, I am also using Intel graphics chipset and there were no errors like that when I've played paintball last time, maybe year ago.

---

### Post by MYGRA1N on 2009-03-17
> **hikaricore said:**
> It may be perfectly suitable for 3d in Windows, but Intel chipsets are notorious for being hit and miss under Linux.

Thank Intel for crappy hardware and drivers.
Check around the fourm for things to try with your intel card/drivers, best of luck.

Intel chipsets are hit and miss on Windows!:(

---

### Post by mpsii on 2009-03-17
Intel Video is not hit and miss... Regardless, it is an integrated chipset not meant for gaming. Just because the laptop is 3 years old does not mean it is not using a less than capable video card.

Intel video cards are great for 2d, desktop effects, and general computer use. But they are extremely underpowered for games.

Please provide the output of ```
lspci -v
```

---

### Post by Meow27 on 2009-03-17
```
flamehawk@Nebula-Class:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Sony Corporation Vaio VGN-S3XP
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Unknown device 81b8
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 81b8
	Flags: fast devsel
	Memory at 50000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 81bb
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0100000-b01fffff
	Capabilities: [50] Subsystem: Sony Corporation Unknown device 81b9

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 81b9
	Flags: medium devsel, IRQ 10
	I/O ports at 18a0 [size=32]

06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
	Subsystem: Sony Corporation Unknown device 818f
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at b0108000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 54000000-57fff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001

06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 818f
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at b0104000 (32-bit, non-prefetchable) [size=2K]
	Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
	Subsystem: Sony Corporation Unknown device 8190
	Flags: bus master, medium devsel, latency 57, IRQ 21
	Memory at b0105000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 2751
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at b0106000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2

06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
	Subsystem: Sony Corporation Unknown device 81d0
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at b0107000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: [dc] Power Management version 2
```

---

### Post by mpsii on 2009-03-17
Even under Windows, Halo will not run with that Intel chipset as graphics. It just doesn't have it.

---

### Post by hikaricore on 2009-03-17
> **mpsii said:**
> Intel Video is not hit and miss...

It most certainly is.

Search around the forums for the horror/success stories involving Intel video chipsets.
You'll find there's often no rhyme or reason to it and people with the exact same chipset have different results.

---

### Post by Meow27 on 2009-03-17
```
username@Phrozen-Box:~/.wine/drive_c/Program Files/Microsoft Games/Halo Trial$ wine halo.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32d3dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cd54,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32c754,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32c7e4,0x00000000), stub!
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:RegisterEventSourceW ((null),L"Halo"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000048,0x6cd7fc,0x6cd3b4): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000048,0x13bed8,0x6cd3b4): stub
err:eventlog:ReportEventW L"halo.exe"
err:eventlog:ReportEventW L"1.0.0.578"
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L"0.0.0.0"
err:eventlog:ReportEventW L"00000000"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```


this computer has a nvidia 7300 LE

the shortcut doesnt work either

---

### Post by Meow27 on 2009-03-19
bump. that graphics card supports halo for sure, now i still cant run halo, but the game loads less then it did on my laptop

---

