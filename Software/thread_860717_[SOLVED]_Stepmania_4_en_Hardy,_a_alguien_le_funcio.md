---
title: "[SOLVED] Stepmania 4 en Hardy, a alguien le funciona?"
date: 2008-07-15
forum: Software
---

### Post by atari130xe on 2008-07-15
Stepmania me persigue jejeje, resulta que instalé desde getdeb la versión 4 que en gutsy funcionaba bién, pero... en hardy no se que pasa, o sea se instala perfecto pero cuando inicio el juego, al segundo "ok" no avanza más como si se congelara, pero no es asi, el programa sigue funcionando pero queda ahí. a alguien le pasó o pasa lo mismo? gracias :)

---

### Post by Mauro22 on 2008-07-15
La consola que dice?

:popcorn:

---

### Post by atari130xe on 2008-07-15
> **Mauro22 said:**
> La consola que dice?

:popcorn:

al ejecutar stepmania4 desde consola obtengo esto:

lo del sonido es lo "habitual" en mi compu (escucho lastfm y "sonaron" otras aplicaciones (mi karma el de las múltiples fuentes de sonidos a la vez)

```
$ stepmania4
StepMania CVS 4.0 CVS
Log starting 2008-07-15 23:02:48
Loading window: gtk
OS: Linux ver 020624
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.7
Threads library: NPTL 2.7
libavcodec: 0x332600 (3352064)
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.16.
ALSA Driver: 0: C-Media CMI8738 [CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC], 0/1 subdevices avail
ALSA Driver: 0: C-Media CMI8738 [CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC], 1/1 subdevices avail
ALSA Driver: 0: C-Media CMI8738 [CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958], 1/1 subdevices avail
Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
Couldn't load driver OSS: RageSoundDriver_OSS: Couldn't open /dev/dsp: Device or resource busy
Sound driver: Null
Lights driver: SystemMessage
Lights driver: Export
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../idVendor": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../idProduct": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../serial": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../product": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../manufacturer": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../idVendor": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../idProduct": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../serial": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../product": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../manufacturer": No such file or directory
/////////////////////////////////////////

(stepmania4:28074): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../idVendor": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../idProduct": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../serial": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../product": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/fd0/device/../manufacturer": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../idVendor": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../idProduct": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../serial": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../product": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../manufacturer": No such file or directory
/////////////////////////////////////////
mount: /dev/fd0 no es un dispositivo de bloques válido
/////////////////////////////////////////
WARNING: failed to execute 'mount /dev/fd0' with error 8192.
/////////////////////////////////////////
Display: :20.0 (screen 0)
Direct rendering: no
X server vendor: The X.Org Foundation [1.4.0.90]
Server GLX vendor: NVIDIA Corporation [1.4]
Client GLX vendor: NVIDIA Corporation [1.4]
OpenGL shading language: 1.20 NVIDIA via Cg compiler
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: NVIDIA Corporation
OGL Renderer: GeForce 8400 GS/PCI/SSE2/3DNOW!
OGL Version: 2.1.2 NVIDIA 173.14.09
OGL Max texture size: 8192
OGL Texture units: 4
GLU Version: 1.3
OGL Extensions:
  GL_ARB: color_buffer_float, depth_texture, draw_buffers, fragment_program, fragment_program_shadow, 
    fragment_shader, half_float_pixel, imaging, multisample, multitexture, occlusion_query, pixel_buffer_object, 
    point_parameters, point_sprite, shader_objects, shading_language_100, shadow, texture_border_clamp, 
    texture_compression, texture_cube_map, texture_env_add, texture_env_combine, texture_env_dot3, texture_float, 
    texture_mirrored_repeat, texture_non_power_of_two, texture_rectangle, transpose_matrix, vertex_buffer_object, 
    vertex_program, vertex_shader, window_pos
  GL_ATI: draw_buffers, texture_float, texture_mirror_once
  GL_EXTX_framebuffer_mixed_formats
  GL_EXT: Cg_shader, abgr, bgra, bindable_uniform, blend_color, blend_equation_separate, blend_func_separate, 
    blend_minmax, blend_subtract, compiled_vertex_array, depth_bounds_test, draw_buffers2, draw_instanced, 
    draw_range_elements, fog_coord, framebuffer_blit, framebuffer_multisample, framebuffer_object, 
    framebuffer_sRGB, geometry_shader4, gpu_program_parameters, gpu_shader4, multi_draw_arrays, 
    packed_depth_stencil, packed_float, packed_pixels, pixel_buffer_object, point_parameters, rescale_normal, 
    secondary_color, separate_specular_color, shadow_funcs, stencil_two_side, stencil_wrap, texture3D, 
    texture_array, texture_buffer_object, texture_compression_latc, texture_compression_rgtc, 
    texture_compression_s3tc, texture_cube_map, texture_edge_clamp, texture_env_add, texture_env_combine, 
    texture_env_dot3, texture_filter_anisotropic, texture_integer, texture_lod, texture_lod_bias, 
    texture_mirror_clamp, texture_object, texture_sRGB, texture_shared_exponent, timer_query, vertex_array
  GL_IBM: rasterpos_clip, texture_mirrored_repeat
  GL_KTX_buffer_region
  GL_NVX_conditional_render
  GL_NV: blend_square, conditional_render, copy_depth_to_color, depth_buffer_float, depth_clamp, fence, 
    float_buffer, fog_distance, fragment_program, fragment_program2, fragment_program_option, 
    framebuffer_multisample_coverage, geometry_shader4, gpu_program4, half_float, light_max_exponent, 
    multisample_coverage, multisample_filter_hint, occlusion_query, packed_depth_stencil, parameter_buffer_object, 
    pixel_data_range, point_sprite, primitive_restart, register_combiners, register_combiners2, texgen_reflection, 
    texture_compression_vtc, texture_env_combine4, texture_expand_normal, texture_rectangle, texture_shader, 
    texture_shader2, texture_shader3, transform_feedback, vertex_array_range, vertex_array_range2, vertex_program, 
    vertex_program1_1, vertex_program2, vertex_program2_option, vertex_program3
  GL_S3_s3tc
  GL_SGIS: generate_mipmap, texture_lod
  GL_SGIX: depth_texture, shadow
  GL_SUN_slice_accum
OpenGL Fullscreen 640x480 16 color 16 texture 58Hz Vsync SmoothLines
Mixing 4196.767144 ahead in 1327 Mix() calls
Mixing underruns: 2
Players joined: P1
Language: en
Current renderer: OpenGL
Theme: default

```

---

### Post by faktorqm on 2008-07-17
y te debe tirar error por varias cosas, la primera, que no puede abrir ningun servidor de sonido (probó con alsa y oss y falló), despues no encuentra un directorio que se llama /sys/algo... y despues me llama poderosamente la atencion que tira un glxinfo y dice "direct rendering: no", esto significa que no tenes aceleracion 3d. este juego la necesita? Salu2!

---

### Post by atari130xe on 2008-07-17
> **faktorqm said:**
> y te debe tirar error por varias cosas, la primera, que no puede abrir ningun servidor de sonido (probó con alsa y oss y falló), despues no encuentra un directorio que se llama /sys/algo... y despues me llama poderosamente la atencion que tira un glxinfo y dice "direct rendering: no", esto significa que no tenes aceleracion 3d. este juego la necesita? Salu2!

jejeje mirá:

```

jose@jose-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
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
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 173.14.09
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
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

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
jose@jose-desktop:~$ 


```
tengo aceleración gráfica :)

el tema es que el juego no se cuelga sino que deja de responder el teclado por alguna razón en ese 2do "ok" que hay que darle para avanzar "muere" ahí, pero no se cuelga.

Anduve mirando en aca mismo en gaming & leisure y no soy el único, el tema es que no comprendo bién los que dicen que solucionaron el tema, instalando los driver de la gráfica con Envy, todo bién pero asi lo tengo instalado yo :confused:

[URL="http://ubuntuforums.org/showthread.php?t=730340&
highlight=stepmania"]http://ubuntuforums.org/showthread.php?t=730340&highlight=stepmania[/URL]

Según el flaco que posteó ese thread dice: "after endless rebooting, uninstalling and resintalling of Nvidia drivers.. I decided to give Envy a go, and that seemed to have done it, now when the resolution matches that of the desktop the input won't die... " 
Luego de reinicios interminables, desinstalando y reinstalando los driver Nvidia, decidí probar con Envy y parece que él lo hizo, ahora la resolución concuerda la del escritorio el teclado no "muere"...  
ahh? :confused: es como raro, no voy a reinstalar algo que funciona bien en casi todo, será un bug? en gutsy no me pasaba, claro era otra gráfica (Nvidia Gforce 6400)

---

### Post by faktorqm on 2008-07-17
Claro, y proba de ejecutarlo asi a ver que pasa:

```
export DISPLAY=:0 && stepmania4
```

y con el tema del sonido, bueno, si ya lo estas arrastrando de antes, fijate si podes cerrar todas las aplicaciones que tenes que usen audio y corre el juego solo. Tambien podes probar de deshabilitar compiz para jugar.
Salu2!

---

### Post by atari130xe on 2008-07-17
> **faktorqm said:**
> Claro, y proba de ejecutarlo asi a ver que pasa:

```
export DISPLAY=:0 && stepmania4
```

y con el tema del sonido, bueno, si ya lo estas arrastrando de antes, fijate si podes cerrar todas las aplicaciones que tenes que usen audio y corre el juego solo. Tambien podes probar de deshabilitar compiz para jugar.
Salu2!

resultado:
```
jose@jose-desktop:~$ export DISPLAY=:0 && stepmania4
StepMania CVS 4.0 CVS
Log starting 2008-07-17 12:27:23
No protocol specified
Couldn't load driver gtk: Couldn't initialize gtk (cannot open display)

(stepmania4:6823): Gtk-CRITICAL **: gtk_widget_hide_all: assertion `GTK_IS_WIDGET (widget)' failed

(stepmania4:6823): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(stepmania4:6823): GLib-GObject-CRITICAL **: g_signal_emit_by_name: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Error: Couldn't open any loading windows.
jose@jose-desktop:~$ 

``` :confused:

*Lo del sonido asi es, lo vengo arrastrando desde Gutsy pero ahi seteando todo a ALSA o ESD lo pude solucionar, acá con PulseAudio no tuve suerte, se bloquean las aplicaciones unas a otras, posteé en Launchpad el bug, pero hasta ahora no hubo respuesta, el post es del 2007 cuando todavia estaban con las betas de Feisty creo. Esperaré no queda otra.

---

### Post by atari130xe on 2008-07-17
Bueno ingre&#347;e en foro de Stepmania y me dieron una solución "temporal" pero que zafa y permite usar el programa de manera casi "normal"

1) iniciar el juego normalmente (sugirieron hacerlo en una ventana no en pantalla completa, lo probé en ambos y funciona igual)
2) elegir las opciones (único jugador o Múltiple jugadores)
3) la 2da vez que hay que dar "ok" (ANTES de hacerlo) presionar "Alt + Enter" y darle de nuevo a esa combinacion de teclas, y el juego sigue su curso normal.
Porqué pasa eso... mmm la menor idea, pero al menos así funciona. Espero les sirva a los que tengan el mismo problema.

PD: a los que les pasa eso en otra parte del juego sencillamente aplican esa combinación de teclas ANTES del punto donde les pase el problema.:popcorn:

---

