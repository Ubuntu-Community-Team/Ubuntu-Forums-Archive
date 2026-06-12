---
title: "video ati en ubuntu"
date: 2011-07-13
forum: Software
---

### Post by zaret on 2011-07-13
la verdad es que tengo un problema con la aceleracion 3d es decir el 3d direct, tengo ubuntu 10.04 y mi targeta es una ati hd4570 , lo importante es que si tengo aceleracion 3d con el driver privativo pero solo como super user, cuando pongo $glxinfo |grep direct como usuario me dice direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

a lo cual no se me ocurre como abilitarlo para el usr y no solo para el super user....
bueno esto se debe a que quiero jugar el stepmania pero me dice  exactamente
que no tengo el opengl andando, alguna idea??

---

### Post by zaret on 2011-07-13
error excato que me da el stepmania,

zaret@zaret-laptop:~/Descargas/StepMania-3.9$ ./stepmania 
StepMania 3.9
Log starting 2011-07-13 02:21:04
Loading window: gtk
OS: Linux ver 020632
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.11.1
Threads library: NPTL 2.11.1
TLS is available
/////////////////////////////////////////
WARNING: Got file 'kcore' in 'proc/' from list, but can't stat? (Value too large for defined data type)
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Got file 'kcore' in 'proc' from list, but can't stat? (Value too large for defined data type)
/////////////////////////////////////////
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.21.
ALSA Driver: 0: HDA Intel [Intel], device 0: STAC92xx Analog [STAC92xx Analog], 1/1 subdevices avail
ALSA Driver: 1: HDA ATI HDMI [HDMI], device 3: ATI HDMI [ATI HDMI], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 44100hz
Sound driver: ALSA-sw

(stepmania:15242): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
SDL version: 1.2.14
Got 32 bpp (8888), 24 depth, 0 stencil
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: ATI Technologies Inc.
OGL Renderer: ATI Mobility Radeon HD 4500 Series
OGL Version: 1.4 (3.2.9756 Compatibility Profile Context)
OGL Extensions: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays GL_ARB_texture_float 
OGL Max texture size: 8192
GLU Version: 1.3
Display: :0.0 (screen 0)
Direct rendering: no
X server vendor: The X.Org Foundation [1.7.6.0]
Server GLX vendor: ATI [1.4]
Client GLX vendor: ATI [1.4]
Mixing 503.771727 ahead in 863 Mix() calls
Language: english
Current renderer: OpenGL
Theme: default
Error: There was an error while initializing your video card.

   PLEASE DO NOT FILE THIS ERROR AS A BUG!

Video Driver: OpenGL

Initializing OpenGL...
Your system is reporting that direct rendering is not available.  Please obtain an updated driver from your video card manufacturer.

---

### Post by zaret on 2011-07-13
ya encontré la manera en que me diga direct renderin yes tanto al user como al super user 
$unset LIBGL_ALWAYS_INDIRECT

Pero el error con el stepmania continua, alguna idea??

---

