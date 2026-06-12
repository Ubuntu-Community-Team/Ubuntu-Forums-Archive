---
title: "VMWare Workstation 7.0 crashes with Direct3D acceleration (WinXP SP2)"
date: 2011-02-24
forum: Virtualisation
---

### Post by Flaminghedgehog on 2011-02-24
First and foremost, I apologize if I am posting this is a nonsensical manner. I'm a little frustrated as I haven't been able to remedy this for a few days now.

This problem began a week ago. The date was 2011-02-17 (yyyy/mm/dd). Before I did this update via the update manager (System > Administration > Update manager), every one of my applications was working fine before I did this (Most of them still do). I wanted to update my system in this way because I felt that my packages currently installed were outdated; so I did! [(Full Log file for this year so far)]("http://pastebin.com/Stu68KMz")

I updated my system, most of my applications still work. The only oddity I now found was that when I try and play games through a Virtual Machine (Using a Windows XP as a guest operating system) that use any form of Direct3D acceleration, I am presented with the following error.

[IMG]http://forum.ntreev.net/pangya/resized-image.ashx/__size/429x265/__key/CommunityServer.Discussions.Components.Files/18/3678.Screenshot_2D00_Error.3.png[/IMG]
[http://pastebin.com/LLuM9ZtK](http://pastebin.com/LLuM9ZtK) (Output log)

I couldn't make heads or tails over the output log file (And I still cant!), so I searched around for any type of correlation to this error. I found out that this error was related to a video related error in the virtual machine. Formatted the virtual machine guest, tried again, same result.

There was a topic on these forums (and neighboring forums) which told a user to do a apt-get install of driconf, and to disable some form of texture rendering (I can't remember what was said in the topic) in order to remedy this problem. I follow in suit to install driconf and try to run it, aaaaand..!

```
$ driconf 
libGL is too old.
```Failure it seems! I also had a window pop up too.
[IMG]http://oi56.tinypic.com/51ztap.jpg[/IMG]

I searched up both of the errors. Unfortunately, I was unable to find a correct tutorial to step me through the process of remedying this issue. Just my luck!

I decided to give up for a few days to clear my head. Suddenly I noticed something.

[LEFT]On the splash screen of my login screen, the nVidia logo normally appears for a second (Thanks to the removal of the "noLogo" option in the x.org config file!). It appears I'm using a nVidia *[COLOR=Red]beta driver[/COLOR]*[COLOR=Black] which strikes me as odd. I'm currently under the impression that this could very well be the source of my problems as beta drivers are commonly found to have something missing. This is what I'm currently thinking.

I am currently at a loss of what to do. I did [spy a list of packages I could potentially install]("http://pastebin.com/K9Gv6Zub"), but I don't know if I want to do this method of simply installing nVidia packages. Let alone, I wouldn't know what to install in the first place.

Any suggestions as to what I can do? I would like my Direct3D acceleration to work properly without causing my Virtual Machine guest to crash. ("I would love to play my games again!")
[/COLOR] [/LEFT]

For the convenience of others, here is an output of various commands I have done in my terminal. (There is more than one command in this ```
 block)
[CODE]flame@system76-pc:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce G 105M/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 270.18
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_include, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_texture_type_2_10_10_10_REV, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_alpha_test, GL_NV_blend_minmax, 
    GL_NV_blend_square, GL_NV_complex_primitives, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fbo_color_attachments, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragdepth, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_geometry_shader4, 
    GL_NV_gpu_program4, GL_NV_half_float, GL_NV_light_max_exponent, 
    GL_NV_multisample_coverage, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, 
    GL_NV_parameter_buffer_object, GL_NV_parameter_buffer_object2, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_buffer_load, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_lod_clamp, 
    GL_NV_texture_multisample, GL_NV_texture_rectangle, GL_NV_texture_shader, 
    GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_vdpau_interop, GL_NV_vertex_array_range, GL_NV_vertex_array_range2, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_rgb8_rgba8, 
    GL_OES_standard_derivatives, GL_OES_texture_3D, GL_OES_texture_float, 
    GL_OES_texture_float_linear, GL_OES_texture_half_float, 
    GL_OES_texture_half_float_linear, GL_OES_texture_npot, 
    GL_OES_vertex_array_object, GL_OES_vertex_half_float, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon

164 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x75  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x76  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x78  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x79  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x7a  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x7b  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x7c  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x7d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x7e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x7f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x80  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x81  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x82  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x83  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x84  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x85  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x86  0 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x88  0 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x8a  0 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x8b  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x8c  0 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x8d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x8e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x8f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x90  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x91  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x92  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x93  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x94  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x95  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x96  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x97  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x98  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x99  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x9a  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x9b  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x9c  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x9d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x9e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x9f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa0  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xa2  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xa3  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xa4  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xa5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xa6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xa7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa9  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xaa  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xab  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xac  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xad  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xae  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xaf  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xb0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xb1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xb2  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xb3  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xb4  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xb5  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb6  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb7  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb8  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xba  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbb  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xbc  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xbd  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xbe  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbf  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xc0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xc2  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xc3  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xc4  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xc5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xc6  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xc7  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xc8  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xc9  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0xca  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0xcb  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0xcc  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0xcd  0 sg  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0xce  0 sg  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0xcf  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  0 16 16 16 16  0 0 None
0xd0  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  8 16 16 16 16  0 0 None
0xd1  0 sg  0 32  0 r  .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd2  0 sg  0 32  0    .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd3  0 sg  0 32  0 r  y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd4  0 sg  0 32  0    y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd5  0 sg  0 32  0 r  .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd6  0 sg  0 32  0    .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd7  0 sg  0 32  0 r  y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd8  0 sg  0 32  0    y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd9  0 sg  0 64  0 r  .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xda  0 sg  0 64  0    .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdb  0 sg  0 64  0 r  y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdc  0 sg  0 64  0    y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdd  0 sg  0 128  0 r  .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xde  0 sg  0 128  0    .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xdf  0 sg  0 128  0 r  y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe0  0 sg  0 128  0    y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe1  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe2  0 sg  0 32  0    .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe3  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe4  0 sg  0 32  0    y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe5  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe6  0 sg  0 32  0    .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe7  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe8  0 sg  0 32  0    y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe9  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xea  0 sg  0 32  0    .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xeb  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xec  0 sg  0 32  0    y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xed  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xee  0 sg  0 32  0    .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xef  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf0  0 sg  0 32  0    y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf1  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf2  0 sg  0 64  0    .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf3  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf4  0 sg  0 64  0    y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf5  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf6  0 sg  0 64  0    .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf7  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf8  0 sg  0 64  0    y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf9  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfa  0 sg  0 128  0    .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfb  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfc  0 sg  0 128  0    y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfd  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0xfe  0 sg  0 128  0    .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0xff  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x100  0 sg  0 128  0    y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0 16  0 r  .  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x102  0 sg  0 16  0    .  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x103  0 sg  0 16  0 r  y  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x104  0 sg  0 16  0    y  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0 64  0 r  .  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0 64  0    .  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0 64  0 r  y  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0 64  0    y  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0 16  0 r  .  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10a  0 sg  0 16  0    .  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10b  0 sg  0 16  0 r  y  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10c  0 sg  0 16  0    y  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0 16  0 r  .  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x10e  0 sg  0 16  0    .  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x10f  0 sg  0 16  0 r  y  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x110  0 sg  0 16  0    y  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0 64  0 r  .  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x112  0 sg  0 64  0    .  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x113  0 sg  0 64  0 r  y  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0 64  0    y  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0 64  0 r  .  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0 64  0    .  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0 64  0 r  y  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x118  0 sg  0 64  0    y  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None

flame@system76-pc:~$ glxgears -info
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
GL_RENDERER   = GeForce G 105M/PCI/SSE2
GL_VERSION    = 3.3.0 NVIDIA 270.18
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_ES2_compatibility GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_include GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_format_BGRA8888 GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_type_2_10_10_10_REV GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_alpha_test GL_NV_blend_minmax GL_NV_blend_square GL_NV_complex_primitives GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fbo_color_attachments GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragdepth GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_shader_buffer_load GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_lod_clamp GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_OES_depth24 GL_OES_depth32 GL_OES_depth_texture GL_OES_element_index_uint GL_OES_fbo_render_mipmap GL_OES_get_program_binary GL_OES_mapbuffer GL_OES_packed_depth_stencil GL_OES_rgb8_rgba8 GL_OES_standard_derivatives GL_OES_texture_3D GL_OES_texture_float GL_OES_texture_float_linear GL_OES_texture_half_float GL_OES_texture_half_float_linear GL_OES_texture_npot GL_OES_vertex_array_object GL_OES_vertex_half_float GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 42 requests (42 known processed) with 0 events remaining.

```What my x.org config file currently contains.
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.18  (buildd@litembilla)  Sun Jan 23 21:54:04 UTC 2011

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Chi Mei Optoelectronics corp."
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "DRI" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G 105M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1280x720 @1280x800 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```I've also included a zip file containing my system info using sudo apt-get install sysinfo && sysinfo in the terminal. Please tell me if you need any further/additional information.

---

### Post by Hedgehog1 on 2011-02-25
Wow - this is some post (I say this as one hedgehog to another).

I need to get my head around this, please:

You are running Ubuntu 10.04,
You updated to WMware Player 7.0.  What was the previous version?

Did you update the Windows XP Nvidia drivers inside the VM?
Did you update the Ubuntu Nvidia drivers?

Also, just to be sure I have this down:

Is your Ubuntu 10.04 32 or 63 bit?
Is your XP PRO VM 32 or 64 Bit?

Lastly - what level of DirectX are you running inside the VM?

:KS

---

### Post by Flaminghedgehog on 2011-02-25
> **Hedgehog1 said:**
> Wow - this is some post (I say this as one hedgehog to another).
I chuckled. Thanks for putting a smile on my face. :)

To answer your questions in order:
I am running Ubuntu 10.04,
My current version of VMWare Player (or VMWare Workstation) has always been 7.0. I have had no previous version of this in the past. I have tried updating VMWare Player/Workstation, but trying to [install]("http://img340.imageshack.us/img340/118/screenshot12mi.png") or [uninstall]("http://img52.imageshack.us/img52/8962/screenshot25r.png") proved to be fatal.

Yes, I updated the nVidia drivers to the most current redistribution (I believe it's called end-user runtime?) version.
On the date of 2011-02-17, I did a big software update through the update manager (System > Administration > Update Manager)  because I was behind on updates for quite a while. I'm sure there is a few nVidia packages in that update. After all, this is how all this nonsense began! Essentially, if I might have not performed this update, I probably wouldn't be complaining now, would I? :P
Included packages from my 2011-02-17 update:
```
Start-Date: 2011-02-17  22:34:59Install: ttf-umefont (411-1),  libxcb-dri2-0 (1.5-2), libx11-xcb1 (1.3.2-1ubuntu3),  linux-headers-2.6.32-28 (2.6.32-28.55), linux-image-2.6.32-28-generic  (2.6.32-28.55), linux-headers-2.6.32-28-generic (2.6.32-28.55) Upgrade: libsmbclient  (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), openoffice.org-draw  (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2), libkrb5-3 (1.8.1+dfsg-2ubuntu0.3,  1.8.1+dfsg-2ubuntu0.6), libpurple0 (2.6.6-1ubuntu4, 2.6.6-1ubuntu4.3),  libk5crypto3 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.6),  dnsmasq-base (2.52-1, 2.52-1ubuntu0.1), tomboy (1.2.1-0ubuntu1,  1.2.2-0ubuntu1), language-pack-gnome-en-base (10.04+20100714,  10.04+20110204), libc-bin (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.8),  uuid-runtime (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2), base-files  (5.0.0ubuntu20.10.04.2, 5.0.0ubuntu20.10.04.3), xserver-xorg-video-ati  (6.13.0-1ubuntu5, 6.13.1-1ubuntu1~xup3~lucid), unattended-upgrades  (0.55ubuntu4, 0.55ubuntu5), libcupsppdc1 (1.4.3-1ubuntu1.2,  1.4.3-1ubuntu1.3), liblcms1 (1.18.dfsg-1ubuntu2,  1.18.dfsg-1ubuntu2.10.04.1), telepathy-gabble (0.8.12-0ubuntu1,  0.8.12-0ubuntu1.1), ttf-thai-tlwg (0.4.13-4, 0.4.13-4ubuntu0.1),  libwebkit-1.0-common (1.2.0-1, 1.2.5-0ubuntu0.10.04.1), libpurple-bin  (2.6.6-1ubuntu4, 2.6.6-1ubuntu4.3), bind9-host (9.7.0.dfsg.P1-1,  9.7.0.dfsg.P1-1ubuntu0.1), libblkid1 (2.17.2-0ubuntu1,  2.17.2-0ubuntu1.10.04.2), libcupsimage2 (1.4.3-1ubuntu1.2,  1.4.3-1ubuntu1.3), openoffice.org-emailmerge (3.2.0-7ubuntu4.1,  3.2.0-7ubuntu4.2), libcupscgi1 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),  libgudev-1.0-0 (151-12.1, 151-12.3), poppler-utils (0.12.4-0ubuntu5,  0.12.4-0ubuntu5.1), libcomerr2 (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1),  intel-gpu-tools (1.0.2+git20100324-0ubuntu1,  1.0.2+git20100830+c935c60-0ubuntu0sarvatt~lucid), libevdocument2  (2.30.3-0ubuntu1.1, 2.30.3-0ubuntu1.2), openoffice.org-impress  (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2), smbclient (3.4.7~dfsg-1ubuntu3.2,  3.4.7~dfsg-1ubuntu3.3), libcupsdriver1 (1.4.3-1ubuntu1.2,  1.4.3-1ubuntu1.3), evolution-plugins (2.28.3-0ubuntu10,  2.28.3-0ubuntu10.2), libmagickcore2 (6.5.7.8-1ubuntu1,  6.5.7.8-1ubuntu1.1), libxml2-utils (2.7.6.dfsg-1ubuntu1,  2.7.6.dfsg-1ubuntu1.1), evolution (2.28.3-0ubuntu10,  2.28.3-0ubuntu10.2), dnsutils (9.7.0.dfsg.P1-1,  9.7.0.dfsg.P1-1ubuntu0.1), openoffice.org-base-core (3.2.0-7ubuntu4.1,  3.2.0-7ubuntu4.2), mysql-server (5.1.41-3ubuntu12.6,  5.1.41-3ubuntu12.9), cupsddk (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),  wine1.2 (1.2-1ubuntu1~lucidppa1, 1.2.2-1ubuntu1~lucid1),  language-pack-gnome-en (10.04+20100714, 10.04+20110204), libdbus-1-3  (1.2.16-2ubuntu4, 1.2.16-2ubuntu4.1), update-inetd (4.35,  4.35ubuntu0.1), gnome-settings-daemon (2.30.1-0ubuntu1,  2.30.1-0ubuntu1.1), util-linux (2.17.2-0ubuntu1,  2.17.2-0ubuntu1.10.04.2), nvidia-current (260.19.29-0ubuntu1~xup~lucid2,  270.18-0ubuntu1~lucid~xup1), xserver-xorg-core (1.7.6-2ubuntu7.3,  1.7.6-2ubuntu7.5), kdelibs5 (4.4.2-0ubuntu4, 4.4.5-0ubuntu1),  xserver-common (1.7.6-2ubuntu7.3, 1.7.6-2ubuntu7.5), libapparmor-perl  (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.3), empathy-common (2.30.2-0ubuntu1,  2.30.3-0ubuntu1), libmagickwand2 (6.5.7.8-1ubuntu1,  6.5.7.8-1ubuntu1.1), libevview2 (2.30.3-0ubuntu1.1, 2.30.3-0ubuntu1.2),  hpijs (3.10.2-2ubuntu2.1, 3.10.2-2ubuntu2.2), linux-generic  (2.6.32.25.27, 2.6.32.28.32), nvidia-current-modaliases  (195.36.24-0ubuntu1~10.04, 270.18-0ubuntu1~lucid~xup1), cups-client  (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3), mobile-broadband-provider-info  (20100407-1, 20100716-1ubuntu0.1), oxygen-icon-theme (4.4.2-0ubuntu2,  4.4.5-0ubuntu1), libdns64 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),  hplip (3.10.2-2ubuntu2.1, 3.10.2-2ubuntu2.2), at (3.1.11-1ubuntu5,  3.1.11-1ubuntu5.1), plasma-scriptengine-javascript (4.4.2-0ubuntu4.1,  4.4.5-0ubuntu1), libwbclient0 (3.4.7~dfsg-1ubuntu3.2,  3.4.7~dfsg-1ubuntu3.3), ttf-opensymbol (3.2.0-7ubuntu4.1,  3.2.0-7ubuntu4.2), empathy (2.30.2-0ubuntu1, 2.30.3-0ubuntu1),  openoffice.org-style-human (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2),  libapache2-mod-php5 (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.7), subversion  (1.6.6dfsg-2ubuntu1, 1.6.6dfsg-2ubuntu1.1), evolution-common  (2.28.3-0ubuntu10, 2.28.3-0ubuntu10.2), mysql-server-core-5.1  (5.1.41-3ubuntu12.6, 5.1.41-3ubuntu12.9), libaprutil1-ldap  (1.3.9+dfsg-3build1, 1.3.9+dfsg-3ubuntu0.10.04.1), plymouth-label  (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.2), libkcddb4 (4.4.2-0ubuntu3,  4.4.5-0ubuntu1), login (4.1.4.2-1ubuntu2, 4.1.4.2-1ubuntu2.2),  apache2-mpm-prefork (2.2.14-5ubuntu8.2, 2.2.14-5ubuntu8.4), pidgin-data  (2.6.6-1ubuntu4, 2.6.6-1ubuntu4.3), libpam-smbpass  (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), libpam-ck-connector  (0.4.1-3ubuntu1, 0.4.1-3ubuntu2), php5-gd (5.3.2-1ubuntu4.5,  5.3.2-1ubuntu4.7), libfreetype6 (2.3.11-1ubuntu2.2, 2.3.11-1ubuntu2.4),  mumble (1.2.2-1ubuntu1, 1.2.2-1ubuntu1.1), e2fsprogs (1.41.11-1ubuntu2,  1.41.11-1ubuntu2.1), plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2,  0.8.2-2ubuntu2.2), openoffice.org-math (3.2.0-7ubuntu4.1,  3.2.0-7ubuntu4.2), libmagickcore2-extra (6.5.7.8-1ubuntu1,  6.5.7.8-1ubuntu1.1), openoffice.org-writer (3.2.0-7ubuntu4.1,  3.2.0-7ubuntu4.2), libmysqlclient16 (5.1.41-3ubuntu12.6,  5.1.41-3ubuntu12.9), libisccc60 (9.7.0.dfsg.P1-1,  9.7.0.dfsg.P1-1ubuntu0.1), apache2-utils (2.2.14-5ubuntu8.2,  2.2.14-5ubuntu8.4), libc6-i386 (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.8),  libfuse2 (2.8.1-1.1ubuntu2, 2.8.1-1.1ubuntu2.2), cups-ppdc  (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3), apache2 (2.2.14-5ubuntu8.2,  2.2.14-5ubuntu8.4), update-manager (0.134.10, 0.134.11), indicator-sound  (0.2.3-0ubuntu1, 0.2.6-0ubuntu1), update-manager-core (0.134.10,  0.134.11), libsvn1 (1.6.6dfsg-2ubuntu1, 1.6.6dfsg-2ubuntu1.1),  openoffice.org-gtk (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2),  xserver-xorg-video-intel (2.9.1-3ubuntu5, 2.11.0-1ubuntu1~xup),  libck-connector0 (0.4.1-3ubuntu1, 0.4.1-3ubuntu2), linux-firmware  (1.34.1, 1.34.3), samba-common (3.4.7~dfsg-1ubuntu3.2,  3.4.7~dfsg-1ubuntu3.3), app-install-data-partner (12.10.04.3,  12.10.04.4), dbus (1.2.16-2ubuntu4, 1.2.16-2ubuntu4.1), udev (151-12.1,  151-12.3), passwd (4.1.4.2-1ubuntu2, 4.1.4.2-1ubuntu2.2), linux-image  (2.6.32.25.27, 2.6.32.28.32), apache2.2-common (2.2.14-5ubuntu8.2,  2.2.14-5ubuntu8.4), python-desktopcouch (0.6.4-0ubuntu3,  0.6.4-0ubuntu3.1), apparmor-utils (2.5-0ubuntu3,  2.5.1-0ubuntu0.10.04.3), cups-common (1.4.3-1ubuntu1.2,  1.4.3-1ubuntu1.3), uno-libs3 (1.6.0+OOo3.2.0-7ubuntu4.1,  1.6.0+OOo3.2.0-7ubuntu4.2), libhpmud0 (3.10.2-2ubuntu2.1,  3.10.2-2ubuntu2.2), liblwres60 (9.7.0.dfsg.P1-1,  9.7.0.dfsg.P1-1ubuntu0.1), nvidia-glx-185 (195.36.24-0ubuntu1~10.04,  270.18-0ubuntu1~lucid~xup1), gnome-system-tools (2.30.0-0ubuntu2,  2.30.0-0ubuntu3), linux-headers-2.6.32-25 (2.6.32-25.44, 2.6.32-25.45),  libcups2 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3), winetricks  (0.0+20100917-0ubuntu1~lucidppa1, 0.0+20110105-0ubuntu1~ppa1),  linux-image-2.6.32-25-generic (2.6.32-25.44, 2.6.32-25.45),  libkrb5support0 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.6),  python-uno (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2), ifupdown  (0.6.8ubuntu29.1, 0.6.8ubuntu29.2), openssh-client (5.3p1-3ubuntu4,  5.3p1-3ubuntu5), bsdutils (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2),  sudo (1.7.2p1-1ubuntu5.2, 1.7.2p1-1ubuntu5.3), libaprutil1-dbd-sqlite3  (1.3.9+dfsg-3build1, 1.3.9+dfsg-3ubuntu0.10.04.1), mysql-client-core-5.1  (5.1.41-3ubuntu12.6, 5.1.41-3ubuntu12.9), ttf-symbol-replacement  (1.1.42-0ubuntu4, 1.2.2-1ubuntu1~lucid1), kdepimlibs-data  (4.4.2-0ubuntu2.1, 4.4.5-0ubuntu1), apache2.2-bin (2.2.14-5ubuntu8.2,  2.2.14-5ubuntu8.4), icoutils (0.26.0-4ubuntu1, 0.29.1-0ubuntu1~lucid),  libpoppler5 (0.12.4-0ubuntu5, 0.12.4-0ubuntu5.1), linux-headers-generic  (2.6.32.25.27, 2.6.32.28.32), dpkg (1.15.5.6ubuntu4.3,  1.15.5.6ubuntu4.5), libxml2 (2.7.6.dfsg-1ubuntu1,  2.7.6.dfsg-1ubuntu1.1), libbind9-60 (9.7.0.dfsg.P1-1,  9.7.0.dfsg.P1-1ubuntu0.1), linux-image-generic (2.6.32.25.27,  2.6.32.28.32), cups (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),  libpoppler-glib4 (0.12.4-0ubuntu5, 0.12.4-0ubuntu5.1), evince  (2.30.3-0ubuntu1.1, 2.30.3-0ubuntu1.2), gir1.0-pango-1.0  (1.28.0-0ubuntu2, 1.28.0-0ubuntu2.1), flashplugin-installer  (10.1.85.3ubuntu0.10.04.1, 10.2.152.27ubuntu0.10.04.1), samba  (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3),  python-desktopcouch-records (0.6.4-0ubuntu3, 0.6.4-0ubuntu3.1),  libfreetype6-dev (2.3.11-1ubuntu2.2, 2.3.11-1ubuntu2.4), dpkg-dev  (1.15.5.6ubuntu4.3, 1.15.5.6ubuntu4.5), gwibber-service  (2.30.2-0ubuntu3, 2.30.3-0ubuntu2), ubiquity-casper (1.236, 1.236.2),  e2fslibs (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1), fglrx-modaliases  (8.723.1-0ubuntu5, 8.801-0ubuntu1~xup~lucid), nvidia-96-modaliases  (96.43.17-0ubuntu1, 96.43.18-0ubuntu1), cups-bsd (1.4.3-1ubuntu1.2,  1.4.3-1ubuntu1.3), ure (1.6.0+OOo3.2.0-7ubuntu4.1,  1.6.0+OOo3.2.0-7ubuntu4.2), desktopcouch (0.6.4-0ubuntu3,  0.6.4-0ubuntu3.1), libplasma3 (4.4.2-0ubuntu4, 4.4.5-0ubuntu1),  linux-headers-2.6.32-25-generic (2.6.32-25.44, 2.6.32-25.45),  libapparmor1 (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.3), liblircclient0  (0.8.6-0ubuntu4.1, 0.8.6-0ubuntu4.2), kdepimlibs5 (4.4.2-0ubuntu2.1,  4.4.5-0ubuntu1), libudev0 (151-12.1, 151-12.3), libplymouth2  (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.2), libwebkit-1.0-2 (1.2.0-1,  1.2.5-0ubuntu0.10.04.1), libisccfg60 (9.7.0.dfsg.P1-1,  9.7.0.dfsg.P1-1ubuntu0.1), kdelibs-bin (4.4.2-0ubuntu4, 4.4.5-0ubuntu1),  libuuid1 (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2), libc6-dev  (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.8), openoffice.org-calc  (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2), plymouth-x11 (0.8.2-2ubuntu2,  0.8.2-2ubuntu2.2), apparmor (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.3),  plymouth-theme-ubuntu-text (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.2), pidgin  (2.6.6-1ubuntu4, 2.6.6-1ubuntu4.3), libssl0.9.8 (0.9.8k-7ubuntu8.3,  0.9.8k-7ubuntu8.6), media-player-info (6-1, 12-1~lucid1), mumble-11x  (1.2.2-1ubuntu1, 1.2.2-1ubuntu1.1), man-db (2.5.7-2, 2.5.7-2ubuntu1),  python-papyon (0.4.8-0ubuntu1, 0.4.8-0ubuntu2),  ttf-mscorefonts-installer (3.2, 3.2ubuntu0.1), imagemagick  (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1), openssl (0.9.8k-7ubuntu8.3,  0.9.8k-7ubuntu8.6), rsyslog (4.2.0-2ubuntu8, 4.2.0-2ubuntu8.1),  php5-mysql (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.7), mount (2.17.2-0ubuntu1,  2.17.2-0ubuntu1.10.04.2), kdelibs5-data (4.4.2-0ubuntu4,  4.4.5-0ubuntu1), kdebase-runtime (4.4.2-0ubuntu4.1, 4.4.5-0ubuntu1),  libss2 (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1), linux-libc-dev  (2.6.32-25.44, 2.6.32-28.55), openoffice.org-common (3.2.0-7ubuntu4.1,  3.2.0-7ubuntu4.2), php5-cgi (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.7),  samba-common-bin (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), winbind  (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), fuse-utils  (2.8.1-1.1ubuntu2, 2.8.1-1.1ubuntu2.2), xserver-xorg-video-radeon  (6.13.0-1ubuntu5, 6.13.1-1ubuntu1~xup3~lucid), grub-common  (1.98-1ubuntu7, 1.98-1ubuntu10), php5-cli (5.3.2-1ubuntu4.5,  5.3.2-1ubuntu4.7), ssh-askpass-gnome (5.3p1-3ubuntu4, 5.3p1-3ubuntu5),  gwibber (2.30.2-0ubuntu3, 2.30.3-0ubuntu2), upstart (0.6.5-7, 0.6.5-8),  libisc60 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1), libgssapi-krb5-2  (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.6), libdbus-1-dev  (1.2.16-2ubuntu4, 1.2.16-2ubuntu4.1), dbus-x11 (1.2.16-2ubuntu4,  1.2.16-2ubuntu4.1), system-tools-backends (2.9.4-0ubuntu1,  2.9.4-0ubuntu1.1), libcupsmime1 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),  libc-dev-bin (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.8),  openoffice.org-style-galaxy (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2), libc6  (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.8), language-pack-en-base  (10.04+20100714, 10.04+20110204), kdebase-runtime-data  (4.4.2-0ubuntu4.1, 4.4.5-0ubuntu1), openoffice.org-gnome  (3.2.0-7ubuntu4.1, 3.2.0-7ubuntu4.2), libaprutil1 (1.3.9+dfsg-3build1,  1.3.9+dfsg-3ubuntu0.10.04.1), nvidia-173-modaliases  (173.14.22-0ubuntu11, 173.14.27-0ubuntu1), mysql-common  (5.1.41-3ubuntu12.6, 5.1.41-3ubuntu12.9), php5-common (5.3.2-1ubuntu4.5,  5.3.2-1ubuntu4.7), mysql-server-5.1 (5.1.41-3ubuntu12.6,  5.1.41-3ubuntu12.9), language-pack-en (10.04+20100714, 10.04+20110204),  nvidia-185-modaliases (195.36.24-0ubuntu1~10.04,  270.18-0ubuntu1~lucid~xup1), openoffice.org-core (3.2.0-7ubuntu4.1,  3.2.0-7ubuntu4.2), nautilus-sendto-empathy (2.30.2-0ubuntu1,  2.30.3-0ubuntu1), python-libxml2 (2.7.6.dfsg-1ubuntu1,  2.7.6.dfsg-1ubuntu1.1), plymouth (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.2),  mysql-client-5.1 (5.1.41-3ubuntu12.6, 5.1.41-3ubuntu12.9),  nvidia-settings (195.36.08-0ubuntu2, 270.18-0ubuntu1~lucid~xup1),  python-kde4 (4.4.2-0ubuntu2, 4.4.5-0ubuntu1), hplip-data  (3.10.2-2ubuntu2.1, 3.10.2-2ubuntu2.2), consolekit (0.4.1-3ubuntu1,  0.4.1-3ubuntu2)
End-Date: 2011-02-17  22:49:07
```

 
My Ubuntu is actually a x86 bit system. Presumably, it's able to support both x32 and x64 software.
I am under the assumption that my XP Pro Virtual Machine is 32 bit

I'm not sure what you mean by "the level of DirectX inside the Virtual Machine". Could I trouble you to elaborate if you can?

---

### Post by Hedgehog1 on 2011-02-25
Without getting too off topic, MS has been offering better/faster DirectX APIs - these are the way to minimize overhead and talk directly to your GPU card as much as possible.

The fact that you are not aware of the DriectX level tells me you have not futzed with any of that, so that is what I need to know.

The XP PRO is 32 bit, so Ubuntu 32 or 64 bit will handle it fine.

Basically, we are down the the Ubuntu Nvidia drivers, then.

Essentially, you need to go back to **a** previous version of just the Ubuntu Nvidia driver (I had to do this very thing for ATI Windows drivers a bit ago, newer ones barfed <technical phrase> with Photoshop's GPU acceleration - it happens).  I will assume that they didn't try your 'Unique' setup in Nvidia's testing plan.

I believe the process is to then 'blacklist' further updates once that is done, so the newer ones won't break your setup.

So - step one is we find out how to go back to earlier Nvidia drivers in Ubuntu (new experience for me - never done it) and how to blacklist the drivers once you get the correct earlier version re-loaded.

The are both questions you can ask on the regular forums (the note book folks often have to do this).

It not a direct answer - but a path to it.

I will be learning too as I follow it.

:KS

p.s. Keep the posts direct and simple.  We Hedgehogs have a reputation to uphold!

---

### Post by Flaminghedgehog on 2011-02-25
My current NVidia version is 270.18 on my host machine. I had recently downloaded a NVIDIA-Linux-x86_64-260.19.36.run file from the main NVidia website. I assume the NVidia version here is 260.19.36 based on the file name.

Simply put, would you recommend I run it in my terminal?

---

### Post by Hedgehog1 on 2011-02-25
> **Flaminghedgehog said:**
> My current NVidia version is 270.18 on my host machine. I had recently downloaded a NVIDIA-Linux-x86_64-260.19.36.run file from the main NVidia website. I assume the NVidia version here is 260.19.36 based on the file name.

Simply put, would you recommend I run it in my terminal?

To be very honest: I have not tried to downgrade a driver before in Ubuntu and I don't know if that is all there is to it.

I suspect you have all you need, and running it is all that is needed, but I cannot say for sure.:confused:

Not much help, I know; but I don't want to hurt your system.

*p.s. I just looked at my Nvidia driver and I am at 260.19.06 - I have fallen rather behind myself...*

---

