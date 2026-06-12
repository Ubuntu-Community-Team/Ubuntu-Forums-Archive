---
title: "Since Ubuntu CE doesn't recognize my video card..."
date: 2012-11-28
forum: Ubuntu Christian Edition
---

### Post by fredbird67 on 2012-11-28
I tried booting Ubuntu CE both on my computer at work as well as at home, and it gave me an error message of being unable to properly detect my video card. :(  I have _never_ had this problem with any other distro at all, and so therefore, while anyone, of course, is welcome to comment, I'd really like to hear from the Ubuntu CE lead developer himself on this one, because I've got a MAJORLY burning question here:

To the Ubuntu CE lead developer, if you're reading this, I'd like to know how you got Firefox and Chromium's proxy settings configured and locked down so that they can't be changed short of having sudo/root access.  Because I've been looking online for days trying to figure this one out, mainly with Chromium (I've found stuff on this that sounds like it should work on Firefox).

Namely, what I'd like to be able to do is pull off what you've done in a Linux installation with a lightweight desktop environment or window manager.

Thanx in advance,
Fred in St. Louis

PS -- alternately, would there by any chance be some kind of script or .deb package that will automate all this? (hey, there's an idea for people such as myself who can't run the latest Ubuntu, like I'm now unable to do)

---

### Post by QIII on 2012-11-28
Developers generally don't hang out here, so you are probably shouting at the sea.

What do you mean when you say it won't recognize your video card?  What exactly happens?

---

### Post by 2F4U on 2012-11-28
With those kind of graphics problems, it would certainly a good idea to post your hardware specs. Could you also make clear whether you get this problem when booting from a liveCD or from an already installed system.

---

### Post by fredbird67 on 2012-11-28
This was from a live USB.

---

### Post by QIII on 2012-11-28
In order to help (you'll have to settle with us, I'm afraid, because the lead developer probably doesn't hang out here), we need more information.  Let's deal with the video first.

What underlying Ubuntu version?
Machine specs?
A better description of the observed behavior.

All we know right now is that you have some version of Ubuntu CE that you are trying to boot from a live USB and your graphics card is "not being recognized."

---

### Post by prism01 on 2012-11-28
Hi
As you may have noticed from another thread, this author is running Ubuntu CE as an installed usb.
 
a) Nobody, including a developer can help unless the specifications of the system are provided, particularly the video card, etc.
 
Newer video cards, or video cards that have had something added to the board, or not placed on the board, as an inducement for sale can also be especially irksome.
 
Sometimes a live system will not see a video card when an installed one will, this being due, most usually, to space constraints, but not always. Sometimes video cards are just a problem to any distro.
 
b) You said that the usb is "live" does that mean that you have the .iso on a usb and did not "install" it?
 
c) The scripting for the Chrome browser is provided by "Dansguardian". It is specifically designed to not be able to be altered by the end user.
 
This is because one of the primary assumptions of the distro is that one has children which one does not want to be exposed to certain things on the net.
 
Perusal of other threads concerning Dansguardian may be of assistance, as they have been to other inquirers. A visual inspection of the first page of threads will reveal several topics which are germane. :)
 
An alternative would be to install other browsers unless one only uses Chrome or FF.
 
d) As to "pulling off" the distro as a more lightweight system one can easily install a variety of desktops, such as LXDE, or XFCE from the repositories.
 
[http://www.linuxlinks.com/article/2008112315231841/Desktop.html](http://www.linuxlinks.com/article/2008112315231841/Desktop.html)
 
Again, if the more experienced people than this author are to be able to help, they have to be provided with the specifications of the video card, etc.
 
prism01

---

### Post by fredbird67 on 2012-11-28
OK, after plugging in a live USB of Linux Lite (a brand-new lightweight Ubuntu-based distro with Xfce as its default desktop -- it's also what I have installed on my computer at home) and opening a terminal and running "lspci", here's what came up:

> 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


Does this tell y'all everything yuns need to know?

I won't be home for about 7 more hours, but once I'm home, I'll post those, too.  Since I can't stand Unity (and prefer Xfce), I have no intention at all of installing Ubuntu CE itself, but what I'm after here is how to find the code used to lock down the proxy settings in FF and Chrome so that I can incorporate those into my installation.

PS -- Just in case it's needed, I also ran "glxinfo" (after installing mesa-utils) and got the following:

> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G41 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, GL_ARB_multitexture, 
    GL_EXT_framebuffer_sRGB, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_occlusion_query, GL_ARB_shadow, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_EXT_stencil_two_side, 
    GL_EXT_texture_cube_map, GL_NV_depth_clamp, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, 
    GL_MESA_texture_array, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_texture_rg, 
    GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ac 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x06a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x06b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x074 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x076 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x079 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x07f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x081 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x083  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x084  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x085  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x086  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x087  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x095  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x096  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x097 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x098 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x099 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

root@root:~# 


---

### Post by fredbird67 on 2012-11-29
On my computer at home, here's the output of "lspci":

> 00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 USB controller: NEC Corporation USB (rev 43)
00:0a.1 USB controller: NEC Corporation USB (rev 43)
00:0a.2 USB controller: NEC Corporation USB 2.0 (rev 04)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)


And, when running "glxinfo", I get:

> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6200/AGP/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.35
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

120 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x031 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x033 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x041 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x043 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x044 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x045 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x047 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x049 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x052 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x058 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x05a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x05c 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x05e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x05f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x060 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x061 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x062 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x064 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x066 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x067 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x068 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x069 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x06a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x06c 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x06e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x06f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x070 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x071 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x072 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x073 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x074 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x075 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x076 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x077 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x078 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x079 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x07a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x07b 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x07c 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x07d 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x07e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x07f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x080 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x081 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x082 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x083 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x084 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x085 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x086 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x087 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x088 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x089 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08b 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x08c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x08d 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08e 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x090 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x091 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x092 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x093 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x094 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x095 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x096 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x097 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x098 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon

179 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x099 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x09c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x09d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0a0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a2 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0ab 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0ad 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0ae 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0af 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0b0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0b1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b2 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bd 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0be 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0bf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c2 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0ca 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0cb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0cc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0cd 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0ce 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0cf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d1 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d2 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0da 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0dc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0dd 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0de 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0df 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e1 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e2 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0ea 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0eb 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0ec 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0ed 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ee 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0ef 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0f0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0f1 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f3 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f4 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f5 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0f6 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0f7 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0f8 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0f9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0fa 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0fb 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0fc 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0fd 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0fe 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0ff 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x100 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x101 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x102 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x103 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x104 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x105 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x106 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x107 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x108 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x109 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10b 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x10c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x10d 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10e 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x110 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x111  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x112  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x113  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x118  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x119  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 None
0x11a  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x11b  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x11c  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x11d  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x11e  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x11f  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x120  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x121  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x122  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x123  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x124  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x125  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x126  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x127  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x128  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x129  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x12a  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x12b  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x12c  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x12d  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x12e  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x12f  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x130  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x131  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x132  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x133  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x134  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x135  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x136  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x137  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x138  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x139  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x13a  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x13b  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x13c  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x13d  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x13e  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x13f  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x140  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x141  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x142  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x143  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x144  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x145  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x146  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x147  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x148  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x149  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x14a  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x14b  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None


---

### Post by prism01 on 2012-11-30
Hi
Well, the thought was that someone more knowledgable than this author would pop by to address the problem, but not so.

You will have to make do with this author's small opinion.

The situation seems to be well described in these two lines from the above post:

> 
OpenGL renderer string: GeForce 6200/AGP/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.35
The situation is probably, notice that this author does not say that it IS the problem, but the situation is probably that of the number 6200.

This author has run a 6200 card before and was not pleased with the results.

Also this author has had the devil of a time with "AGP" cards.

The situation is, the author assumes that you know this, but others may not...

The situation is with the numbering is that the "original" stock version numbers are things like 6000.

Numbers like 6200 USUALLY indicate that there has been either:

a) something not placed on the card that was on the original version
b) something added to the card that was not the original version.

In these cases, nothing "wrong" was done, it was merely that the vendor wanted to either provide a less expensive card than the original, or that there was an enhancement, usually for gaming situations, to get the frame rate up, or rendering of certain colours etc.

If there are people who are not aware of it, there is a webpage that is called the Linux Hardware Compatability List:

[http://www.linux-drivers.org/display.html](http://www.linux-drivers.org/display.html)

It used to be in the not so long ago that the HCL was kept at the site.

And, there were comments by users as to the good, bad and ugly side of things like video cards.

However, that seems to be gone now, when one clicks the link for Nvidia, one gets the Nvidia site and the drivers and that is about it.

One might as well just use the drivers from the distribution's repository.

So....to sum this up.... it is probable that the situation is just that of a 2 in the version number and that the driver does not do well with that version.

And, as stated before, the author did not like the experience with the 6200 card.

A search in Google for "Nvidia 6200 card linux" popped this reply in the third return:

[http://forums.linuxmint.com/viewtopic.php?f=59&t=113017](http://forums.linuxmint.com/viewtopic.php?f=59&t=113017)

There is not much more that what is quoted below so one need not necessarily go to the site but..

notice the date and this author will note that there were no replies, and the Mint forums are usually pretty good about having timely replies.

And also, this was a PCI card.  And PCI cards usually are not that much of a problem.

> 
Nvidia 6200 card
on Fri Sep 21, 2012 8:14 pm                             
I have a GEforce 6200 card  256 mb that I have tried multiple times to try to get to run CCSM and enable compiz effects. 
I have installed multiple drivers ( i think i am running 304.47 and still I cannot get it to work-)


You might try the "nouveau" driver, or if there is not a philosophical problem with it, run the Nvidia app for the Nvidia wrapper for the driver.

I'm sorry that I could not be of more help.

And again, perhaps someone more knowledgeable will pop by.

prism01

---

### Post by prism01 on 2012-12-02
If you tried Nouveau drivers any luck?

prism01

---

