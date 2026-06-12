---
title: "WINE having GLX issues even with OpenGL drivers installed correctly..."
date: 2010-01-04
forum: Wine
---

### Post by r2rX on 2010-01-04
Greetz everyone,

I'm using Kubuntu 9.10 x64 (but this issue also applies to Ubuntu 9.10 x64) with an ATi Radeon 4870 and the official ATi Catalyst 9.12 drivers installed. I'm also using Wine v1.1.35.

The following indicates that the display drivers are installed correctly:

```
r2rx@r2rx:~$ glxinfo
name of display: :0.0
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,     
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_NV_swap_group,      
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control,     
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,              
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group,             
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap,                
    GLX_EXT_framebuffer_sRGB, GLX_ARB_fbconfig_float                          
GLX version: 1.4                                                              
GLX extensions:                                                               
    GLX_ARB_create_context, GLX_ARB_create_context_profile,                   
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,    
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,        
    GLX_NV_swap_group, GLX_OML_swap_method, GLX_SGI_make_current_read,        
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample,           
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier,               
    GLX_SGIX_swap_group, GLX_SGIX_visual_select_group,                        
    GLX_EXT_texture_from_pixmap                                               
OpenGL vendor string: ATI Technologies Inc.                                   
OpenGL renderer string: ATI Radeon HD 4800 Series                             
OpenGL version string: 3.2.9232                                               
OpenGL shading language version string: 1.50                                  
OpenGL extensions:                                                            
    GL_AMDX_name_gen_delete, GL_AMDX_vertex_shader_tessellator,               
    GL_AMD_draw_buffers_blend, GL_AMD_performance_monitor,                    
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_texture_cube_map_array,       
    GL_AMD_texture_texture4, GL_AMD_vertex_shader_tessellator,                
    GL_ARB_color_buffer_float, GL_ARB_compatibility, GL_ARB_copy_buffer,      
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture,      
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend,                           
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced,                  
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,                  
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object,                        
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays,                         
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture,          
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,                        
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex,     
    GL_ARB_seamless_cube_map, GL_ARB_shader_objects,                           
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow,     
    GL_ARB_shadow_ambient, GL_ARB_sync, GL_ARB_texture_border_clamp,           
    GL_ARB_texture_buffer_object, GL_ARB_texture_compression,                  
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map,                  
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add,                     
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,                   
    GL_ARB_texture_env_dot3, GL_ARB_texture_float,                             
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample,                
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod,                 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_snorm,         
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object,                     
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object,                      
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,  
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap,             
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil,           
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3,               
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr,             
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color,                  
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,                
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,  
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_draw_buffers2,             
    GL_EXT_draw_instanced, GL_EXT_draw_range_elements, GL_EXT_fog_coord,       
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample,                   
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB,                        
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters,                    
    GL_EXT_gpu_shader4, GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object,     
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal,   
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,                    
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,               
    GL_EXT_texgen_reflection, GL_EXT_texture3D, GL_EXT_texture_array,          
    GL_EXT_texture_buffer_object, GL_EXT_texture_compression_latc,             
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc,          
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,                        
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,                        
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,                
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias,       
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,                        
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB,                             
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm,                      
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback,     
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra,                             
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,  
    GL_NV_conditional_render, GL_NV_copy_depth_to_color,                       
    GL_NV_explicit_multisample, GL_NV_primitive_restart,                       
    GL_NV_texgen_reflection, GL_SGIS_generate_mipmap,                          
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays, 
    GL_WIN_swap_hint, WGL_EXT_swap_control                                     

81 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x47 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x49 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x4b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x71 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x72 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x73 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x74 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0xba 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 Ncon

91 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x26  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x27  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x28  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x29  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x30  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x31  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x32  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x33  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x34  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x35  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x36  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x37  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x38  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x39  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x3a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x3b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x40  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x41  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x42  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x43  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x44  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x45  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x47  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x48  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x49  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x4a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x4b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x50  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x51  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x52  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x53  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x54  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x55  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x57  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x59  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x5a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x5b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x63  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x64  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x67  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x68  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x69  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x6a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x70  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x71  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x72  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x73  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x74  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0xba  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 Ncon
0xba  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 Ncon
0xba  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0xba  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0xba  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
0xba  0 tc  0 128  0    y  . 32 32 32 32  0 24  0  0  0  0  0  0 0 None
0xba  0 tc  0 128  0    .  . 32 32 32 32  0 24  0  0  0  0  0  0 0 None
0xba  0 tc  0 64  0    y  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0xba  0 tc  0 64  0    .  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0xba  0 tc  0 32  0    y  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None
0xba  0 tc  0 32  0    .  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None

```

But when I try run any application that requires 3D acceleration (whether double-clicking an .exe or running an app with the 'wine' command in bash) the following error occurs:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  224
  Current serial number in output stream:  224

```

Wine installed properly (with every dependency it required) and running any application, that doesn't require 3D acceleration, loads fine in Wine.

So any suggestions on how to fix this? It'll be appreciated plenty. :)

r2rX  :D

---

### Post by r2rX on 2010-01-04
A quick question....is there supposed to be a Direct3D folder under HKEY_CURRENT_USER/Software/Wine/ in wine's registry?

HKEY_CURRENT_USER/Software/Wine/Direct3D/

Cause if there is supposed to be one, it isn't present at all.

NOTE: I just tested the latest trial of Cedega (v8.0.0) and it seems the same thing is happening with it too....this is implying more and more that this issue is related to the ATi drivers....it can't be that the Cat 9.12 is the main cause....perhaps there's a configuration i'm missing?

r2rX  :)

---

### Post by Soulcage on 2010-01-05
Direct3D isn't there by default you add it if you need to.
[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

### Post by r2rX on 2010-01-05
Thanks for the info.....but would one suspect this being the cause of my issue at the moment?

It's quite frustrating....i'm not sure as to how to correct this...

r2rX  :)

---

### Post by r2rX on 2010-01-05
Thanks for the info.....but would one suspect this being the cause of my issue at the moment?

It's quite frustrating....i'm not sure as to how to correct this...

r2rX  :)

---

### Post by dperfors on 2010-01-05
I get the same error. But I suspect (I can't prove) it has something to do with 64 bit systems... a little bit of googling shows multiple distributions having the same problem...

btw: [this]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/406865") describes our issue...

And looking further it seems that wine is using a 32 bit driver for OpenGL in order to be able to run 32 bit applications.

---

### Post by r2rX on 2010-01-05
Thanks for the info, dperfors....

Interestingly enough, though, i've installed Quake 3 and Quake 4 natively in Linux.....Quake 3 works fine, but Quake 4 eventually gives me the exact same error.

I have a feeling that the drivers/libraries are not set properly for 32bit apps....is there a way of checking/finding out for sure?

During my research, I came across something called *lib32-catalyst-utils*...

[http://aur.archlinux.org/packages.php?ID=24824](http://aur.archlinux.org/packages.php?ID=24824)

When downloading the lib32-catalyst-utils, it seems to be designed for Arch Linux. But if one were to edit it and modify it to work for Ubuntu, could it take care of the 32bit lib files necessary to get WINE/Quake4 working WITHOUT resorting to the 32bit MESA drivers?

r2rX  :)

---

