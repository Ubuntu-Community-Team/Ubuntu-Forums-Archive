---
title: "Disable hardware acceleration for a single application at a time?"
date: 2016-07-02
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2016-07-02
I'm trying to install KNetWalk in Xubuntu 16.04 VM (VirtualBox).  If I disable 3D acceleration for the VM, it works fine.  However, enabling 3D acceleration causes KNetWalk to just be a black screen with weird flickering, which... well, it's a bit awkward to play the game ;)

Given the nature of 3D acceleration in VirtualBox, KNetWalk probably won't be the only app I want to use that has this type of issue.  So is there a "universal" way to run any single program with hardware acceleration disabled?  Or alternatively, is there a way to disable hardware acceleration across all KDE apps but keeping it enabled for the VM?

(If a whole other X server is needed, I have Xephyr installed FWIW.  But when I tried to run KNetWalk inside a Xephyr it just crashed...)

---

### Post by deadflowr on 2016-07-12
Doesn't
```
LIBGL_ALWAYS_SOFTWARE=1 program-name-here
```
do something like that.
At least it should make the program run with llvmpipe.

---

### Post by &amp;KyT$0P# on 2016-07-13
Doesn't seem to change anything...

Maybe posting some glxinfo output will help figure this out?
```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: Chromium
server glx version string: 1.3 Chromium
server glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
client glx vendor string: Chromium
client glx version string: 1.3 Chromium
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
GLX version: 1.3
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_fragment_shader, 
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
    GL_CR_bounding_box, GL_CR_cursor_position, GL_CR_head_spu_name, 
    GL_CR_performance_info, GL_CR_print_string, GL_CR_readback_barrier_size, 
    GL_CR_saveframe, GL_CR_server_id_sharing, GL_CR_server_matrix, 
    GL_CR_state_parameter, GL_CR_synchronization, GL_CR_tile_info, 
    GL_CR_tilesort_info, GL_CR_window_size, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp

240 GLX Visuals
[...]

240 GLXFBConfigs:
[...]

```

```
$ LIBGL_ALWAYS_SOFTWARE=1 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: Chromium
server glx version string: 1.3 Chromium
server glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
client glx vendor string: Chromium
client glx version string: 1.3 Chromium
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
GLX version: 1.3
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_fragment_shader, 
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
    GL_CR_bounding_box, GL_CR_cursor_position, GL_CR_head_spu_name, 
    GL_CR_performance_info, GL_CR_print_string, GL_CR_readback_barrier_size, 
    GL_CR_saveframe, GL_CR_server_id_sharing, GL_CR_server_matrix, 
    GL_CR_state_parameter, GL_CR_synchronization, GL_CR_tile_info, 
    GL_CR_tilesort_info, GL_CR_window_size, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp

240 GLX Visuals
[...]

240 GLXFBConfigs:
[...]

```

(this one is from inside a Xephyr: [FONT=Courier New]Xephyr -ac -br -noreset :349[/FONT])
```
name of display: :349
display: :349  screen: 0
direct rendering: Yes
server glx vendor string: Chromium
server glx version string: 1.3 Chromium
server glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
client glx vendor string: Chromium
client glx version string: 1.3 Chromium
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
GLX version: 1.3
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig
OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_fragment_shader, 
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
    GL_CR_bounding_box, GL_CR_cursor_position, GL_CR_head_spu_name, 
    GL_CR_performance_info, GL_CR_print_string, GL_CR_readback_barrier_size, 
    GL_CR_saveframe, GL_CR_server_id_sharing, GL_CR_server_matrix, 
    GL_CR_state_parameter, GL_CR_synchronization, GL_CR_tile_info, 
    GL_CR_tilesort_info, GL_CR_window_size, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp

2 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x041 32 tc  0  32  0 r  y y   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None

2 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  1 1 None
0x041 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  1 1 None


```

---

### Post by &amp;KyT$0P# on 2016-07-20
> **deadflowr said:**
> Doesn't
```
LIBGL_ALWAYS_SOFTWARE=1 program-name-here
```
do something like that.
At least it should make the program run with llvmpipe.
By the way, on the host (which currently uses Intel graphics) that does work:
```
$ LIBGL_ALWAYS_SOFTWARE=1 glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_trinary_minmax, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_ES2_compatibility, GL_ARB_blend_func_extended, 
    GL_ARB_clear_buffer_object, GL_ARB_color_buffer_float, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_storage, GL_ARB_texture_swizzle, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_integer, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, GL_KHR_debug, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_window_pos, 
    GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_depth_clamp, GL_NV_fog_distance, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_primitive_restart, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vdpau_interop, GL_OES_EGL_image, 
    GL_OES_read_format, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

12 GLX Visuals
[...]

28 GLXFBConfigs:
[...]
```

So thanks :) I guess my question now is, how to disable hardware acceleration for only one application inside a VirtualBox guest?

---

### Post by howefield on 2016-07-20
Thread moved to the "*Virtualisation*" forum as requested.

---

### Post by MAFoElffen on 2016-07-31
@halogen2

I'm confused. You said that 
```

LIBGL_ALWAYS_SOFTWARE=1 program-name-here

```
Worked for you. But then you asked
```

I guess my question now is, how to disable hardware acceleration for only one application inside a VirtualBox guest?

```
So if you already did something along the lines of
```

LIBGL_ALWAYS_SOFTWARE=1 open-arena

```
... and that worked for you. Isn't that already disabling hardware acceleration per application?

---

### Post by &amp;KyT$0P# on 2016-07-31
According to the glxinfo outputs I've posted, it works for me on the host, but does not work for me in the guest.

---

### Post by MAFoElffen on 2016-07-31
Okay. Now I understand. ...That is *strange*.

---

### Post by deadflowr on 2016-08-14
You know, I wonder if this is related to the 3d accel problem virtualbox has with kde5, in general.
[https://www.virtualbox.org/ticket/14102]("https://www.virtualbox.org/ticket/14102")
I mean you're not running plasma-desktop, but i wonder if just the fact that it's a (assumingly) qt5 application that is problematic.

But to wonder and be right are totally different things.

---

### Post by &amp;KyT$0P# on 2016-08-14
Sounds about right, more than one Qt 5 game have been a bit problematic with 3D acceleration enabled and that's why I'm looking for this as a workaround.

---

### Post by vasa1 on 2016-11-25
Bumping because I deleted halogen2's bump to test my new browser!

---

### Post by &amp;KyT$0P# on 2016-12-02
bump

---

### Post by &amp;KyT$0P# on 2016-12-09
bump

---

### Post by &amp;KyT$0P# on 2016-12-15
bump

---

### Post by &amp;KyT$0P# on 2016-12-21
bump

---

### Post by &amp;KyT$0P# on 2016-12-30
bump

---

### Post by &amp;KyT$0P# on 2017-01-08
bump

---

### Post by &amp;KyT$0P# on 2017-01-18
bump

---

### Post by &amp;KyT$0P# on 2017-01-31
bump

---

### Post by &amp;KyT$0P# on 2017-02-07
bump

---

### Post by &amp;KyT$0P# on 2017-02-13
bump

---

### Post by &amp;KyT$0P# on 2017-02-19
bump

---

### Post by &amp;KyT$0P# on 2017-02-27
bump

---

### Post by &amp;KyT$0P# on 2017-03-06
bump

---

### Post by &amp;KyT$0P# on 2017-03-29
bump

---

### Post by &amp;KyT$0P# on 2017-04-05
bump

---

### Post by &amp;KyT$0P# on 2017-04-15
bump

---

