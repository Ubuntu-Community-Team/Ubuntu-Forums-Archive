---
title: "lighter weight os for better online video with older hardware?"
date: 2013-05-16
forum: The Cafe
---

### Post by sdowney717 on 2013-05-16
is it possible?
I have a dv9005us laptop with go 6150 nvidia. It struggles with internet video smoothness, gets jumpy,  laggy etc...

So would a different linux version work any better than ubuntu ?
Or is it doomed to be sub par forever.

---

### Post by evilsoup on 2013-05-16
Have you tried Lubuntu? Or just installing LXDE from the repos & using it instead of Unity? Even Xubuntu/XFCE might give you better performance.

---

### Post by Irihapeti on 2013-05-16
If you're really game, you can just install a command-line system plus Openbox, and then add only the programs that you want.

---

### Post by sdowney717 on 2013-05-16
I can try that.
other than that is there any older linux os that would have been better for that laptop?

I am happy with it except for online video.

this is the specs, it has 2gb ram

```
ProcessorAMD Turion 64 X2 mobile technology TL-50 / 1.6 GHz ( Dual-Core )
Memory1.0 GB / 2.0 GB (max)
Hard Drive100.0 GB - Serial ATA-150 - 5400.0 rpm
Operating SystemMicrosoft Windows XP Media Center Edition
Display Type17.0 in TFT active matrix
Max Resolution1440 x 900 ( WXGA+ )
Graphics ProcessorNVIDIA GeForce Go 6150 Shared video memory (UMA)
Optical DriveDVD±RW (+R DL) / DVD-RAM
```

---

### Post by lykwydchykyn on 2013-05-16
Are you using the built-in nvidia driver or the proprietary one?  With those specs it's more likely a driver problem than a lack of system resources.

---

### Post by Irihapeti on 2013-05-16
You could try something like Puppy Linux (which I haven't used for ages and ages, so I'm not up with what they're doing nowadays) and see if that helps.

I'm no expert on such things, but I wonder if the processor speed has something to do with it.

---

### Post by Irihapeti on 2013-05-16
I'll leave it to lykwydchykyn, who I think is better informed on this than I am.

---

### Post by ajgreeny on 2013-05-16
I also agree with lykwydchykyn, because I do not really think those specs are so low that they are your main problem.

I had ubuntu 12.04 running on a sempron 2400+ with a similar 2GB ram and it ran very well, not with unity, of course, as that was far too slow and my ATI 9200SE could not run it properly, so I chose the classic fallback DE.  In my opinion Xubuntu would be better for you, but that is just because I have found it to be so much nicer an OS than Ubuntu.

---

### Post by snowpine on 2013-05-16
Try downloading the video (using your favorite video downloader) then watching locally from your hard drive (using your favorite video player; I find mplayer to be the smoothest). Works every time for me!

---

### Post by sdowney717 on 2013-05-16
I actually found not using the nvidia driver worked a little better. which i found very odd


i just installed lubuntu desktop and it is no better. all it really does is put in another desktop, the underlying system is still the same.

---

### Post by sdowney717 on 2013-05-16
would using 32 bit ubuntu be better for me than 64 bit?
i am using 64 bit

glxgears was 500 now only 300??

```
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.349 FPS
302 frames in 5.0 seconds = 60.207 FPS
302 frames in 5.0 seconds = 60.210 FPS
302 frames in 5.0 seconds = 60.207 FPS
301 frames in 5.0 seconds = 60.003 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 4866 requests (4866 known processed) with 0 events remaining.
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_framebuffer_sRGB, 
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
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NV4E
OpenGL version string: 2.1 Mesa 9.1.1
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
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_ARB_depth_texture, GL_ARB_occlusion_query, 
    GL_ARB_shadow, GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, 
    GL_NV_depth_clamp, GL_NV_fog_distance, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_NV_primitive_restart, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_occlusion_query2, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_pixel_buffer_object, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_gpu_program_parameters, 
    GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, GL_OES_EGL_image, 
    GL_ARB_copy_buffer, GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, 
    GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_ES2_compatibility, GL_ARB_debug_output, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_get_program_binary, GL_ARB_robustness, 
    GL_ARB_timer_query, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_ARB_internalformat_query, 
    GL_ARB_texture_storage, GL_ARB_invalidate_subdata

192 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x1bd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1be 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1bf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1c0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1c1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1c2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1c3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1c4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1c5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1c6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1c7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1c8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1c9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x1ca 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x1cb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x1cc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x1cd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x1ce 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x1cf 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x1d0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x1d1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x1d2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x1d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x1d4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x1d5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x1d6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x1d7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x1d8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x1d9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x1da 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x1db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x1dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x1dd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x1de 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x1df 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x1e0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x1e1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x1e2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x1e3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x1e4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x1e5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x1e6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x1e7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x1e8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x1e9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x1ea 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x1eb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1ec 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1ee 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1ef 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1f1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1f2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1f4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1f5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1f7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1f8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1f9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1fa 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1fb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1fd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1fe 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x200 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x201 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x202 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x203 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x204 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x205 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x206 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x207 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x208 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x209 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x20a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x20b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x20c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x20d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x20e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x20f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x210 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x211 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x212 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x213 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x214 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x215 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x216 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x217 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x218 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x219 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x21a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x21b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x21c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x21d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x21e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x21f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x220 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x221 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x222 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x223 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x224 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x225 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x226 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x227 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x228 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x229 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x22a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x22b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x22c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x22d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x22e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x22f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x230 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x231 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x232 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x233 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x234 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x235 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x236 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x237 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x238 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x239 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x23a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x23b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x23c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x23d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x23e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x23f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x240 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x241 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x242 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x243 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x244 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x245 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x246 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x247 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x248 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x249 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x24a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x24b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x24c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x24d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x24e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x24f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x250 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x251 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x252 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x253 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x254 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x255 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x256 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x257 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x258 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x259 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x25a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x25b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x25c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x25d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x25e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x25f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x260 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x261 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x262 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x263 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x264 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x265 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x266 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x267 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x268 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x269 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x26a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x26b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x26c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x26d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x26e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x26f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x270 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x271 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x272 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x273 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x274 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x275 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x276 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x277 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x278 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x279 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x09c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

288 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x09d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0a1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0a3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0a5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0a7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0a9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0aa 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0ab 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0ac 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0ad 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0ae 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0af 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b3 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0b6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0b7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0b8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0ba 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0bb 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0bc 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0bd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0be 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0bf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0c0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0c1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0c2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0c3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0c4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0c5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0c6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0c7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0c8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0c9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0ca 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0cb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0cc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0cd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ce 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0da 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0db 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0dc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0dd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0de 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0df 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0e6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0e8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0eb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0ec 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0ee 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ef 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0f1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0f8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0f9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0fa 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0fb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0fd  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0fe  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ff  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x100  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x101  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x102  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x103  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x104  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x105  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x106  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x107  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x108  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x109  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x10a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x10b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x10c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x10d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x10e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x10f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x110  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x111  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x112  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x113  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x114  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x115  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x116  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x117  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x118  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x119  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x11a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x11b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x11c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x11d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x11e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x11f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x120  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x121  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x122  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x123  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x124  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x125  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x126  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x127  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x128  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x129  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x12a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x12b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x12c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x12d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x12e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x12f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x130 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x131 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x132 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x133 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x134 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x135 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x136 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x137 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x138 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x139 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x13a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x13b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x13c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x13d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x13e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x13f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x140 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x141 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x142 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x143 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x144 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x145 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x146 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x147 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x148 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x149 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x14a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x14b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x14c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x14d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x14e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x14f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x150 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x151 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x152 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x153 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x154 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x155 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x156 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x157 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x158 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x159 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x15a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x15b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x15c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x15d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x15e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x15f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x160 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x161 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x162 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x163 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x164 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x165 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x166 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x167 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x168 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x169 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x16a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x16b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x16c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x16d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x16e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x16f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x170 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x171 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x172 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x173 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x174 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x175 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x176 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x177 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x178 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x179 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x17a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x17b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x17c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x17d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x17e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x17f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x180 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x181 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x182 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x183 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x184 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x185 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x186 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x187 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x188 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x189 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x18a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x18b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x18c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x18d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x18e  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x18f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x190  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x191  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x192  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x193  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x194  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x195  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x196  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x197  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x198  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x199  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x19a  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x19b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x19c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x19d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x19e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x19f  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1a0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1a1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1a2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1a3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1a4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1a5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1a6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1a7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1a8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1a9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1aa  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1ab  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1ac  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1ad  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1ae  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1af  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1b0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1b1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1b2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1b3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1b4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1b5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1b6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1b7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1b8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1b9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1ba  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1bb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1bc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None

dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ glxgears


```

---

### Post by ajgreeny on 2013-05-17
Forget about glxgears; the framerate it shows is the same as your refresh rate, useless as a benchmark; not that it was ever much good for that!
See the lines at the start of your terminal output.

---

### Post by pqwoerituytrueiwoq on 2013-05-17
stick with 64bit
your problem is adobe flash, it is designed poorly and is very inefficient, your best bet is pausing the video and using smplayer/vlc/parle/totem to play it
here is a script to find and play paused videos (for youtube to work you have to change the playback quality)
[http://pastebin.com/HU7zdSDC](http://pastebin.com/HU7zdSDC)

flash tends to suck even on the most powerful hardware on the market, flash will use 80% of a cpu and a video player would use 5% if that

---

### Post by anoldone on 2013-05-17
As for downloading embedded videos for later viewing, you can try JDownloader. Package is in a repository.
 It's great for connections with bandwidth issues. It fetches and parsers links, saving them into a manager, so you can stop/resume downloading when you want.

---

### Post by pissedoffdude on 2013-05-18
Give Bodhi linux a shot.  I've always found it super lightweight.  Also try chrome (might as well check chromium too though) instead of firefox and see if that makes a difference.  I'm recommending chrome because its Pepper Flash plugin has performed better than Adobe's in my case

---

### Post by HomesteadMommy on 2013-05-18
I agree, Bhodi linux is great, I've been using it as my main OS for my old laptop for over a year now.  I only have 2 GB of RAM but it runs very well and no problems with videos.

---

### Post by mips on 2013-05-18
Can you provide a link to a video you have tried and specify the resolution of the video you selected. I wanna test it this side for comparison as my laptop has much lower specs.

---

### Post by houseworkshy on 2013-05-20
Debian wheezy, Mepis 11, and AntiX all work really well with my 1.8gig RAM, streaming video included.    All can be tested live too though for Wheezy you would need to get a specific live image from the Debian live project.

---

### Post by mips on 2013-05-20
looks like the OP did a hit & run :D

---

### Post by HermanAB on 2013-05-20
Hmm, it sounds to me as if you have a network problem, since that hardware should be good enough for smooth playback.  If it can handle the horribly inefficient Gnome/Unity desktop, then it must be able to play video too.  

Try a different connection (wired/wireless) and see if there is a difference.

---

### Post by monkeybrain2012 on 2013-05-20
Use Lubuntu and avoid flash as much as possible. Use  these greasemonkey scripts and play flash with mplayer or totem (if you use Chrome then totem would work if you install the scripts with tampermonkey)

[https://userscripts.org/scripts/show/87011](https://userscripts.org/scripts/show/87011)
[http://linterna-magica.nongnu.org/](http://linterna-magica.nongnu.org/)
(you may need only one, LM works on more sites but VT gives you more control. You can also have both and configure which works for which site)

I have an old hp Pavillion dv2 laptop (~2 g of rams), using lubuntu 12.04 and these scripts and the open source raedon driver. It is fast and  smooth and boots in 15 sec (it took vista about 5 minutes) I can watch whole 720p online movies with no lag (if internet connection is good, of course)  With vista even local movie files with 720p totally froze.

---

