---
title: "Eve Online issues"
date: 2009-05-11
forum: Wine
---

### Post by JPLGuy on 2009-05-11
Hello,

I'm having trouble with graphics glitches in Eve Online. None of the fixes described in the forums over at Eve seem to work.

The game does not correctly display any 3D graphics. When a ship is in the hanger, the screen is entirely black. Rotating the view causes lighting changes in the surrounding 2D elements, but no changes in the view results. 

The portrait in the character selection has similar glitches, where part of the portrait is black. 

The display errors seem to coincide with the message 
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 261
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 261
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 261
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:basetexture_bind >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 261
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support

The output of glxinfo is 
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 2.0 Mesa 7.4
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_separate_stencil, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays


I have tested both wine 1.1.21 and 1.0.1. I am using Ubuntu 9.04 and Eve Apocrypha (most recent patch). I am using an Intel GM965 with the drivers distributed with Ubuntu 9.04. I've tried using the "UXA" mode in the xorg configuration, and the various user.reg suggestions from the Eve forums. (Apparently I can't post over there for some reason).

Thanks for any suggestions!

---

### Post by asdfoo on 2009-05-11
> **JPLGuy said:**
> Hello,

I'm having trouble with graphics glitches in Eve Online. None of the fixes described in the forums over at Eve seem to work.

The game does not correctly display any 3D graphics. When a ship is in the hanger, the screen is entirely black. Rotating the view causes lighting changes in the surrounding 2D elements, but no changes in the view results. 

The portrait in the character selection has similar glitches, where part of the portrait is black. 

I have tested both wine 1.1.21 and 1.0.1. I am using Ubuntu 9.04 and Eve Apocrypha (most recent patch). I am using an Intel GM965 with the drivers distributed with Ubuntu 9.04. I've tried using the "UXA" mode in the xorg configuration, and the various user.reg suggestions from the Eve forums. (Apparently I can't post over there for some reason).

Thanks for any suggestions!

Hello

It could be a problem with the Linux drivers for your video card, Intel is known for having Linux drivers that are not as good as their windows counterpart.


NVIDIA is usually the best way to go.

---

### Post by JPLGuy on 2009-05-12
> **asdfoo said:**
> Hello

It could be a problem with the Linux drivers for your video card, Intel is known for having Linux drivers that are not as good as their windows counterpart.


NVIDIA is usually the best way to go.


Thanks for the response asdfoo. Unfortunately a new graphics card isn't going to happen. The GM965 is an integrated graphics card, so my laptop (Fujitsu T4220) doesn't have either the space or the mobo connectors for a new one, AFAIK. I just have to get this one working, or abandon the game.

---

### Post by asdfoo on 2009-05-12
> **JPLGuy said:**
> Thanks for the response asdfoo. Unfortunately a new graphics card isn't going to happen. The GM965 is an integrated graphics card, so my laptop (Fujitsu T4220) doesn't have either the space or the mobo connectors for a new one, AFAIK. I just have to get this one working, or abandon the game.

The error message in your original post refers to a lack of support for handling compressed textures (ati and nvidia drivers have had it forever) which I don't think is supported with intel drivers by default.

Reading a related post, I see someone saying:

"get the s3tc library and install driconf and enable s3tc in driconf."

But I'm not sure on the specifics of how to do that. you might google.com/search?q=driconf+s3tc

---

### Post by JPLGuy on 2009-05-12
> **asdfoo said:**
> The error message in your original post refers to a lack of support for handling compressed textures (ati and nvidia drivers have had it forever) which I don't think is supported with intel drivers by default.

Reading a related post, I see someone saying:

"get the s3tc library and install driconf and enable s3tc in driconf."

But I'm not sure on the specifics of how to do that. you might google.com/search?q=driconf+s3tc

Hi again asdfoo. That was a good lead! I tried googling that error before without that luck. Turns out driconf can be found via Synaptic, and does indeed let you activate support for S3TC textures, the only hitch is that the acceleration mode must be "EXA" in the xorg.conf file, not "UXA" for it to correctly recognize the graphics card. 

I went ahead and did it, and it did remove the error message above. I checked that it was being used with the output of glxinfo. Sadly, the graphics problems are still present, and now I can't get to the in-game hanger screen (previously all-black) without crashes. Usually the crashes just freeze the laptop entirely and require a reboot while loading the station, but sometimes not. The complete terminal output from start to crash is now

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d0000 0 0x33fc70 4
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
fixme:win:EnumDisplayDevicesW ((null),0,0x33a5d0,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30032 0x00000000
fixme:imm:ImmReleaseContext (0x30032, 0x148408): stub
fixme:reg:GetNativeSystemInfo (0x33b778) using GetSystemInfo()
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:dsound:DllCanUnloadNow (void): stub
fixme:dsound:DllCanUnloadNow (void): stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
E\bin\ExeFile.exe: ../../src/xcb_io.c:242: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed.
wine: Assertion failed at address 0xb7fa3430 (thread 002e), starting debugger...

I'm still working on finding the "fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface" error, but the final assertion looks like its in code for Eve, so that's not much help.

Thank you for the help!

---

### Post by asdfoo on 2009-05-12
> **JPLGuy said:**
> Hi again asdfoo. That was a good lead! I tried googling that error before without that luck. Turns out driconf can be found via Synaptic, and does indeed let you activate support for S3TC textures, the only hitch is that the acceleration mode must be "EXA" in the xorg.conf file, not "UXA" for it to correctly recognize the graphics card. 

I went ahead and did it, and it did remove the error message above. I checked that it was being used with the output of glxinfo. Sadly, the graphics problems are still present, and now I can't get to the in-game hanger screen (previously all-black) without crashes. Usually the crashes just freeze the laptop entirely and require a reboot while loading the station, but sometimes not. The complete terminal output from start to crash is now


fixme:toolhelp:Heap32ListFirst : stub
E\bin\ExeFile.exe: ../../src/ :242: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed.
wine: Assertion failed at address 0xb7fa3430 (thread 002e), starting debugger...

I'm still working on finding the "fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface" error, but the final assertion looks like its in code for Eve, so that's not much help.

Thank you for the help!


The SetDepthStencilSurface can be ignored, it happens with a lot of games afaik.

The failed assertaion, although it does say "E\bin\ExeFile.exe" does seem strange since xcb is a library for communicating with X servers, so it would suggest that something in Linux has failed (google xcb_io.c) you might also see the same assertion.

Such assertions are sometimes caused by video drivers interacting with the X server in strange ways.

Not sure if there's anything else that can be done.

---

### Post by Fallout X on 2010-01-10
Hi 

I'm having a bit of an issue.
Everytime I try to get on eve it always crashes and I think it may be these errors.

~/.wine/drive_c/Program Files/CCP/EVE$ wine eve.exe
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d0000 0 0x33fc04 4
~/.wine/drive_c/Program Files/CCP/EVE$

If you have any ideas or suggestions please reply.Also I'm running kubuntu 9.10 and this is my first day.

---

