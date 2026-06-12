---
title: "unity very sluggish"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by odror on 2012-09-30
I have the latest 12.10 packages.

Video (4 monitors HD 6850) using latest fglrx driver.

RAM: 10MB

CPU: i7-3770

HD: SSD

Unity's performance is very sluggish. When I click on the dashboard it takes 4 seconds for the dashboard to come UP and the CPU jumps to 94% (mostly due to the xorg process). it takes addition 4 seconds for the dashboard to go away.

Gnome 3 is less much sluggish.

Is the issue the ati card, the 4 monitors, CPU, or Unity/compiz

Does the nvidia card have the same issues?

Thanks

---

### Post by robert shearer on 2012-09-30
> RAM: 10MB ?????   it might be this...:-)

---

### Post by Rukiri on 2012-09-30
You sure it's not 10GB of ram? My personal recommendation is to use the proprietary drivers at least for when it comes to your video card.  Runs smoothly on my HD 7990 and on my main box with the GTX Geforce 680.

---

### Post by effenberg0x0 on 2012-09-30
Ubuntu Hardware Requirements:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)


Regards,
Effenberg

---

### Post by thotz on 2012-09-30
> **odror said:**
> Unity's performance is very sluggish.

Unity performance got worse with the last updates. 
Hopefully there will be a Unity 6.8 that improves performance.

At least here.

---

### Post by T.J. on 2012-09-30
Assuming that you are using the proprietary ATI driver and not the opensource radeonhd driver - it sounds to me that your ATI video driver is not properly installed, and X is falling back to basic rendering.  I can't be 100% certain, of course, but it has been my experience that the proprietary driver in the Ubuntu archives has installation issues.  


You can try installing the "mesa-utils" package, then see if your driver is installed properly by using "glxinfo".  The output should look something like this:

```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_fbconfig_float, GLX_AMD_gpu_association
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series
OpenGL version string: 4.2.11762 Compatibility Profile Context
OpenGL shading language version string: 4.20
OpenGL extensions:
    GL_AMDX_debug_output, GL_AMDX_vertex_shader_tessellator, 
    GL_AMD_conservative_depth, GL_AMD_debug_output, 
    GL_AMD_depth_clamp_separate, GL_AMD_draw_buffers_blend, 
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_AMD_performance_monitor, GL_AMD_pinned_memory, 
    GL_AMD_query_buffer_object, GL_AMD_sample_positions, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trace, GL_AMD_texture_cube_map_array, 
    GL_AMD_texture_texture4, GL_AMD_transform_feedback3_lines_triangles, 
    GL_AMD_vertex_shader_layer, GL_AMD_vertex_shader_tessellator, 
    GL_AMD_vertex_shader_viewport_index, GL_ARB_ES2_compatibility, 
    GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_program_binary, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_objects, 
    GL_ARB_shader_precision, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_snorm, GL_ARB_texture_storage, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, GL_EXT_texture_array, 
    GL_EXT_texture_buffer_object, GL_EXT_texture_compression_bptc, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_storage, GL_EXT_texture_swizzle, 
    GL_EXT_timer_query, GL_EXT_transform_feedback, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_explicit_multisample, GL_NV_float_buffer, GL_NV_half_float, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_SUN_multi_draw_arrays, GL_WIN_swap_hint, WGL_EXT_swap_control

81 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0c2 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon

91 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0c2 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0c2 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0c2 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 Ncon
0x0c2  0 tc  0 128  0    y .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0c2  0 tc  0 128  0    . .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0c2  0 tc  0  64  0    y .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0c2  0 tc  0  64  0    . .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0c2  0 tc  0  32  0    y .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c2  0 tc  0  32  0    . .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
```


What you are looking for is

direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4

If you have those, it's probably installed properly.  If not, your ATI driver is not functioning properly.   

If you need to get it working, post here, and I'll try walk you through the process of building the driver by hand, assuming again - that the process is the same for 12.10 as it is in 12.04.

---

### Post by odror on 2012-09-30
I have made a mistake I have 10GB of ram. (I do not think that there is any version of Linux that can run with 10 MB of ram)

The problem is 60% solved. Windows decoration was not check on ccsm. I fixed that. Now unity is  less sluggish. The delay now is about 1 second and the CPU jump is only to 44%.

---

### Post by T.J. on 2012-09-30
> **odror said:**
> The problem is 60% solved. Windows decoration was not check on ccsm. I fixed that. Now unity is  less sluggish. The delay now is about 1 second and the CPU jump is only to 44%.

Good deal, and congrats!  I've noticed Unity/Compiz can be twitchy. Filing that bit of information for future use.

---

### Post by odror on 2012-10-01
After multiple updates in the last 24 hours Unity is now more sluggish than ever.

I have plenty of memory, hi-end CPU and SSD drive. There is no reason for it to be so slow. Clicking on the dash can be delayed by 8 seconds. On my system I can compile 5000 line of code in less than the time that the dash responds some time. It is unusually worse in the beginning of the session. It improves later.

---

### Post by Chdslv on 2012-10-02
Odror,

Do you have any problems with desktop cube in 12.10. I too have the latest 12.10, and I had few days of trouble with trying to get the desktop cube working as it should in Unity. It works perfectly in Gnome-Classic. I had un-installed Unity and after reading your post installed it back again to see what's wrong. I am going to keep the Unity DE until the release of 12.10, and then download 12.10 and try that with Compiz in another partition. I installed Gnome 3.6 and in that too the desktop cube didn't work. (I un-installed Gnome 3.6 shell.)  

I have only 3Gb memory, but all Ubuntu based distros work very well in my 3 year old laptop. By the way, even if you have so much memory, Ubuntu 12.10 usually takes less than 1 Gb memory with lot of apps working, graphics too.

Have a good day!

---

### Post by Chdslv on 2012-10-02
T.J,

My laptop has Intel and ATi graphics. It works very well with the Intel driver, which the laptop automatically adapts itself to and 3D works superbly. If I try to install the ATI driver, it gets cranked, so I never install it. Should people, who have dual cards/drivers (on board or not) should never try to install the ATI driver to stay away from trouble?

Thanks!:)

---

### Post by odror on 2012-10-02
> **Chdslv said:**
> Odror,

Do you have any problems with desktop cube in 12.10. I too have the latest 12.10, and I had few days of trouble with trying to get the desktop cube working as it should in Unity. It works perfectly in Gnome-Classic. I had un-installed Unity and after reading your post installed it back again to see what's wrong. I am going to keep the Unity DE until the release of 12.10, and then download 12.10 and try that with Compiz in another partition. I installed Gnome 3.6 and in that too the desktop cube didn't work. (I un-installed Gnome 3.6 shell.)  

I have only 3Gb memory, but all Ubuntu based distros work very well in my 3 year old laptop. By the way, even if you have so much memory, Ubuntu 12.10 usually takes less than 1 Gb memory with lot of apps working, graphics too.

Have a good day!
I have "out of the box" setup, almost no extras. the only difference is that I have 4 monitors (ati video card). When I reduce it to 3 monitors there is improvement in performance, but not as it should be.

---

