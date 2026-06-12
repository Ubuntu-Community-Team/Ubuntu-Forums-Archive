---
title: "CoD / Intel 82852/855GM Graphics Card"
date: 2009-06-18
forum: Wine
---

### Post by kilps on 2009-06-18
I'm trying to run Call of Duty (Game of the Year Edition) under wine. I know that my hardware can run the game under Windows.

When I run it I am told "Your video card is missing one or more features required to run Call of Duty." and given the following output:

> CODUO MP 1.41 build win-x86 Aug 23 2004
----- FS_Startup -----
Current language: english
Current search path:
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\pakuo06.pk3 (12 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\pakuo05.pk3 (3 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\pakuo04.pk3 (7646 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\pakuo03.pk3 (2275 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\pakuo02.pk3 (790 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\pakuo01.pk3 (1652 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\pakuo00.pk3 (6231 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition/uo
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\paka.pk3 (41 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak9.pk3 (149 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak8.pk3 (235 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak6.pk3 (3 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak5.pk3 (4858 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak4.pk3 (1668 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak3.pk3 (1992 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak2.pk3 (694 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak1.pk3 (2642 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\pak0.pk3 (12816 files)
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition/main
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\uo\localized_english_pakuo00.pk3 (2578 files)
    localized assets pak file for english
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\localized_english_pak3.pk3 (7 files)
    localized assets pak file for english
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\localized_english_pak2.pk3 (9 files)
    localized assets pak file for english
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\localized_english_pak1.pk3 (3736 files)
    localized assets pak file for english
Z:\home\geoff\Desktop\Call of Duty Game of the Year Edition\main\localized_english_pak0.pk3 (1204 files)
    localized assets pak file for english

File Handles:
----------------------
51241 files in pk3 files
execing default_mp.cfg
couldn't exec language.cfg
execing uoconfig_mp.cfg
couldn't exec autoexec_mp.cfg
========= autoconfigure
configure_mp.csv: using configuration 800 cpu MHz 256 sys MB 64 vid MB
execing configure_mp.cfg
fs_basegame is write protected.
fs_basepath is write protected.
fs_homepath is write protected.
Hunk_Clear: reset the hunk ok
...detecting CPU, found Intel Pentium III
Measured CPU speed is 1.16 GHz
System memory is 497 MB (capped at 1 GB)
Video card memory is 64 MB
Streaming SIMD Extensions (SSE) supported

Winsock Initialized
Opening IP socket: localhost:28960
Hostname: geoff-laptop
IP: 127.12.34.56
WARNING: IPX_Socket: bind: WSAEINVAL
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'C:\windows\system32\opengl32.dll' ): succeeded
...setting mode 3: 640 480 FS
...using colorbits of 32
...calling CDS: ok
...registered window class
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...34 PFDs found
...hardware acceleration found
...PIXELFORMAT 9 selected
...creating GL context: succeeded
...making context current: succeeded
Initializing OpenGL extensions

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 7.4
GL_EXTENSIONS:  GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
----- CL_Shutdown -----
RE_Shutdown( 1 )
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...deleting GL context: success
...releasing DC: success
...destroying window
...resetting display
...shutting down QGL
...unloading OpenGL DLL
-----------------------
Hunk_Clear: reset the hunk ok
Your video card appears to be missing one or more features required to run Call of Duty.

You should install the latest drivers for your video card, being sure to uninstall the old drivers first.  If you already have the latest drivers, you should completely uninstall the drivers and then reinstall them.  This fixes most problems.  If the game still doesn't work, it may be that your video card does not have the minimum features required.  Please check the readme for more information, including a list of supported video cards.
When running via the command line I get the following:
> get fences failed: -1
param: 6, val: 0
fixme:win:EnumDisplayDevicesW ((null),0,0x554f798,0x00000000), stub!
fixme:keyboard:RegisterHotKey ((nil),0,0x00000001,9): stub
fixme:keyboard:UnregisterHotKey ((nil),0): stub
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?According to lspci my graphics card is an Intel 82852/855GM. Wine is version 1.0.1 and I'm running Ubuntu 9.04

Can anyone give me any pointers here? Thanks

---

### Post by NightMKoder on 2009-06-18
1) get a new video card! (seriously, intel support is abismal in general, but <900 is even less)
2) Upgrade to the latest wine.

It may be the CoD is detecting that your card doesn't support some opengl feature (vertex programs?) and bailing.

---

### Post by kilps on 2009-06-19
> **NightMKoder said:**
> 1) get a new video card! (seriously, intel support is abismal in general, but <900 is even less)
2) Upgrade to the latest wine.

It may be the CoD is detecting that your card doesn't support some opengl feature (vertex programs?) and bailing.

I'd love to get a new video card - this one is an integrated one in a 4 year old laptop ... so as soon as I get my new pc :p

After I posted this I changed to the repositories on the winehq site and updated to the latest version, that didn't work :(

As I said the game runs fine under Windows with the same hardware so my guess is it must be wine not detecting/communicating the graphics card's capabilities correctly...

---

