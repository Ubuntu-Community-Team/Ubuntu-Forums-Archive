---
title: "Test Drive Unlimited"
date: 2008-12-06
forum: Wine
---

### Post by Saytr on 2008-12-06
Hello. Test Drive Unlimited is running fine, but I cant seem to get the sound working :(. Is there any way I can fix this ??

Here is the output:

```
ilkan@ilkan-desktop:~$ wine /home/ilkan/.wine/drive_c/Program Files/Atari/Test Drive Unlimited/TestDriveUnlimited.exe
wine: cannot find '/home/ilkan/.wine/drive_c/Program'
ilkan@ilkan-desktop:~$ env WINEPREFIX="/home/ilkan/.wine" wine "C:\Program Files\Atari\Test Drive Unlimited\TestDriveUnlimited.exe"
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x20bed4c,0x00000000), stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x124e68) call to IWineD3DDevice_CreateSurface failed
fixme:d3d_texture:basetexture_generate_mipmaps (0x4be6e50) : stub
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(1024,768)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4be7f20,0x4be7ba0): stub
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 429
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 266
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
wine: Unhandled page fault on read access to 0x00000000 at address 0x434bfa (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00434bfa).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00434bfa ESP:020bf178 EBP:00000000 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000001 ECX:00000000 EDX:00000000
 ESI:0000001c EDI:00000000
Stack dump:
0x020bf178:  0000001c 00000000 00020000 0098ec74
0x020bf188:  00000001 00000000 00020028 004344bb
0x020bf198:  00000000 00020028 00000000 020bf1dc
0x020bf1a8:  7ece1dcc 00000000 7ecbc22a 00020028
0x020bf1b8:  0000001c 00000000 00000000 00020028
0x020bf1c8:  7ece1dcc 020bf1dc 7ece1dcc 00000000
Backtrace:
0x00434bfa: movl        0x0(%ecx),%eax
Modules:
Module  Address                 Debug info      Name (120 modules)
PE        400000- 1eb7000       Export          testdriveunlimited
PE      18000000-18033000       Deferred        binkw32
PE      70bd0000-70c35000       Deferred        shlwapi
ELF     7b800000-7b93c000       Deferred        kernel32<elf>
  \-PE  7b820000-7b93c000       \               kernel32
ELF     7bc00000-7bca9000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca9000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7c61e000-7c629000       Deferred        libgcc_s.so.1
ELF     7c64b000-7c6ad000       Deferred        winedos<elf>
  \-PE  7c650000-7c6ad000       \               winedos
ELF     7c75d000-7d49d000       Deferred        libglcore.so.1
ELF     7d49d000-7d542000       Deferred        libgl.so.1
ELF     7d542000-7d5d7000       Deferred        opengl32<elf>
  \-PE  7d560000-7d5d7000       \               opengl32
ELF     7dc0a000-7dc0e000       Deferred        libgpg-error.so.0
ELF     7dc0e000-7dc5b000       Deferred        libgcrypt.so.11
ELF     7dc5b000-7dc6b000       Deferred        libtasn1.so.3
ELF     7dc6b000-7dc73000       Deferred        libkrb5support.so.0
ELF     7dc73000-7dca5000       Deferred        libcrypt.so.1
ELF     7dca5000-7dd1b000       Deferred        libgnutls.so.13
ELF     7dd1b000-7dd3e000       Deferred        libk5crypto.so.3
ELF     7dd3e000-7ddcb000       Deferred        libkrb5.so.3
ELF     7ddcb000-7ddf4000       Deferred        libgssapi_krb5.so.2
ELF     7ddf4000-7de27000       Deferred        libcups.so.2
ELF     7de72000-7dea5000       Deferred        uxtheme<elf>
  \-PE  7de80000-7dea5000       \               uxtheme
ELF     7dea5000-7deb9000       Deferred        midimap<elf>
  \-PE  7deb0000-7deb9000       \               midimap
ELF     7deb9000-7dee0000       Deferred        msacm32<elf>
  \-PE  7dec0000-7dee0000       \               msacm32
ELF     7dee0000-7dfa3000       Deferred        libasound.so.2
ELF     7dfa4000-7dfa7000       Deferred        libkeyutils.so.1
ELF     7dfa7000-7dfaa000       Deferred        libcom_err.so.2
ELF     7dfaa000-7dfc1000       Deferred        msacm32<elf>
  \-PE  7dfb0000-7dfc1000       \               msacm32
ELF     7dfc1000-7dff6000       Deferred        winealsa<elf>
  \-PE  7dfd0000-7dff6000       \               winealsa
ELF     7e009000-7e012000       Deferred        libxcursor.so.1
ELF     7e012000-7e017000       Deferred        libxfixes.so.3
ELF     7e017000-7e01a000       Deferred        libxcomposite.so.1
ELF     7e01a000-7e020000       Deferred        libxrandr.so.2
ELF     7e020000-7e028000       Deferred        libxrender.so.1
ELF     7e028000-7e02d000       Deferred        libxxf86vm.so.1
ELF     7e02d000-7e030000       Deferred        libxinerama.so.1
ELF     7e030000-7e050000       Deferred        imm32<elf>
  \-PE  7e040000-7e050000       \               imm32
ELF     7e050000-7e055000       Deferred        libxdmcp.so.6
ELF     7e055000-7e06d000       Deferred        libxcb.so.1
ELF     7e06d000-7e06f000       Deferred        libxcb-xlib.so.0
ELF     7e06f000-7e072000       Deferred        libxau.so.6
ELF     7e072000-7e159000       Deferred        libx11.so.6
ELF     7e159000-7e167000       Deferred        libxext.so.6
ELF     7e167000-7e17f000       Deferred        libice.so.6
ELF     7e17f000-7e187000       Deferred        libsm.so.6
ELF     7e187000-7e189000       Deferred        libnvidia-tls.so.1
ELF     7e1a5000-7e23d000       Deferred        winex11<elf>
  \-PE  7e1b0000-7e23d000       \               winex11
ELF     7e26a000-7e28b000       Deferred        libexpat.so.1
ELF     7e28b000-7e2b5000       Deferred        libfontconfig.so.1
ELF     7e2b5000-7e2ca000       Deferred        libz.so.1
ELF     7e2ca000-7e337000       Deferred        libfreetype.so.6
ELF     7e355000-7e39f000       Deferred        dsound<elf>
  \-PE  7e360000-7e39f000       \               dsound
ELF     7e39f000-7e3d7000       Deferred        dinput<elf>
  \-PE  7e3b0000-7e3d7000       \               dinput
ELF     7e3d7000-7e4bd000       Deferred        oleaut32<elf>
  \-PE  7e3f0000-7e4bd000       \               oleaut32
ELF     7e4bd000-7e4d0000       Deferred        libresolv.so.2
ELF     7e4d5000-7e4ee000       Deferred        dinput8<elf>
  \-PE  7e4e0000-7e4ee000       \               dinput8
ELF     7e4ee000-7e50d000       Deferred        iphlpapi<elf>
  \-PE  7e4f0000-7e50d000       \               iphlpapi
ELF     7e50d000-7e572000       Deferred        rpcrt4<elf>
  \-PE  7e520000-7e572000       \               rpcrt4
ELF     7e572000-7e67e000       Deferred        ole32<elf>
  \-PE  7e590000-7e67e000       \               ole32
ELF     7e67e000-7e6b3000       Deferred        winspool<elf>
  \-PE  7e690000-7e6b3000       \               winspool
ELF     7e6b3000-7e774000       Deferred        comctl32<elf>
  \-PE  7e6c0000-7e774000       \               comctl32
ELF     7e774000-7e7de000       Deferred        msvcrt<elf>
  \-PE  7e780000-7e7de000       \               msvcrt
ELF     7e7de000-7e908000       Deferred        shell32<elf>
  \-PE  7e7f0000-7e908000       \               shell32
ELF     7e908000-7e9b4000       Deferred        comdlg32<elf>
  \-PE  7e910000-7e9b4000       \               comdlg32
ELF     7e9b4000-7e9c8000       Deferred        lz32<elf>
  \-PE  7e9c0000-7e9c8000       \               lz32
ELF     7e9c8000-7e9e1000       Deferred        version<elf>
  \-PE  7e9d0000-7e9e1000       \               version
ELF     7e9e1000-7e9f6000       Deferred        psapi<elf>
  \-PE  7e9f0000-7e9f6000       \               psapi
ELF     7e9f6000-7ea42000       Deferred        dbghelp<elf>
  \-PE  7ea00000-7ea42000       \               dbghelp
ELF     7ea42000-7ead4000       Deferred        winmm<elf>
  \-PE  7ea50000-7ead4000       \               winmm
ELF     7ead4000-7eb00000       Deferred        ws2_32<elf>
  \-PE  7eae0000-7eb00000       \               ws2_32
ELF     7eb00000-7eb54000       Deferred        advapi32<elf>
  \-PE  7eb10000-7eb54000       \               advapi32
ELF     7eb54000-7ebf2000       Deferred        gdi32<elf>
  \-PE  7eb60000-7ebf2000       \               gdi32
ELF     7ebf2000-7ed3c000       Deferred        user32<elf>
  \-PE  7ec10000-7ed3c000       \               user32
ELF     7ed3c000-7ee4a000       Deferred        wined3d<elf>
  \-PE  7ed50000-7ee4a000       \               wined3d
ELF     7ee4a000-7ee7a000       Deferred        d3d9<elf>
  \-PE  7ee50000-7ee7a000       \               d3d9
ELF     7ef9a000-7efa5000       Deferred        libnss_files.so.2
ELF     7efa5000-7efbd000       Deferred        libnsl.so.1
ELF     7efbd000-7efe2000       Deferred        libm.so.6
ELF     b7c20000-b7c2a000       Deferred        libnss_nis.so.2
ELF     b7c2b000-b7c2f000       Deferred        libdl.so.2
ELF     b7c2f000-b7d7e000       Deferred        libc.so.6
ELF     b7d7f000-b7d97000       Deferred        libpthread.so.0
ELF     b7d97000-b7da0000       Deferred        libnss_compat.so.2
ELF     b7db5000-b7eeb000       Deferred        libwine.so.1
ELF     b7eed000-b7f09000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Atari\Test Drive Unlimited\TestDriveUnlimited.exe
        00000028   15
        00000023    0
        00000022    0
        00000021    0
        00000009    0 <==
0000000c
        0000001f    0
        0000001a    0
        00000014    0
        00000013    0
        00000012    0
        0000000e    0
        0000000d    0
0000000f
        00000016    0
        00000015    0
        00000011    0
        00000010    0
00000017
        0000001b    0
        00000019    0
        00000018    0
0000001c
        00000020    0
        0000001e    0
        0000001d    0
00000024
        00000025    0
Backtrace:
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs

```

---

### Post by Saytr on 2008-12-06
Bump! come on anyone please ?

---

### Post by hikaricore on 2008-12-07
Please wait 24-48 hours before bumping your posts.

Aside from that there is nothing useful in that output all I see are a few d3d errors that likely mean nothing.
Could you tell if you're using pulseaudio or atleast what version of Ubuntu you're running?

---

### Post by Saytr on 2008-12-07
> **hikaricore said:**
> Please wait 24-48 hours before bumping your posts.

Aside from that there is nothing useful in that output all I see are a few d3d errors that likely mean nothing.
Could you tell if you're using pulseaudio or atleast what version of Ubuntu you're running?

Im running on Ubuntu 8.04 Hardy Heron. Also Im running on ALSA

---

