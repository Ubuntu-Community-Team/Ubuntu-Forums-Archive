---
title: "ATI x125 - Ubuntu 9.04 \\ Acel. 3D?"
date: 2009-08-05
forum: Software
---

### Post by baila0 on 2009-08-05
Hola a todos, 
Como muchos deben saber, no existe soporte para la ATIx1250 en Jaunty por parte de la misma compañía a pesar de que es una tarjeta que venía con mi computador de hace menos de 1 año... por lo que hay que usar los drivers libres...
 
Resulta que insta&#314;e Jaunty como único sistema operativo en mi laptop, luego instalé CompizFusion, y la verdad es que funciona.... no muy fluido por que mi tarjeta de video es no es muy buena mas encima no he instalado ningun driver (asumo que ubunto los instaló solo al insatlarse como s.o, porque SI me funcionan los efectos como Cube, Burn/Quemar, Aeroplano, etc)
 
Quiero saber si está habilitada la aceleració 3D en mi laptop..... según lo que yo sé, si no estuviera instalada no debería funcionar CompizFusion. Pero quiero la respuesta de alguien mas experimentado, ya que llevo sólo unos días experimentando con Jaunty.
 
Algo extraño es también que al ejecutar fglrxinfo obtengo esto:
 
[COLOR=#000000]matias@matias-laptop:~$ fglrxinfo[/COLOR]
[COLOR=#000000]El programa «fglrxinfo» no está instalado actualmente. Puede instalarlo escribiendo:[/COLOR]
[COLOR=#000000]sudo apt-get install xorg-driver-fglrx[/COLOR]
 
 
NOTA: Al instalar fglrxinfo mediante esta forma, al reiniciar el sistema la pantalla no funciona, sólo se ven líneas aleatorias
 
Mis valores de glxinfo son:
 
[COLOR=#000000]matias@matias-laptop:~$ glxinfo[/COLOR]
[COLOR=#000000]name of display: :0.0[/COLOR]
[COLOR=#000000]display: :0 screen: 0[/COLOR]
[COLOR=#000000]direct rendering: Yes[/COLOR]
[COLOR=#000000]server glx vendor string: SGI[/COLOR]
[COLOR=#000000]server glx version string: 1.2[/COLOR]
[COLOR=#000000]server glx extensions:[/COLOR]
[COLOR=#000000]GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, [/COLOR]
[COLOR=#000000]GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, [/COLOR]
[COLOR=#000000]GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, [/COLOR]
[COLOR=#000000]GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group[/COLOR]
[COLOR=#000000]client glx vendor string: SGI[/COLOR]
[COLOR=#000000]client glx version string: 1.4[/COLOR]
[COLOR=#000000]client glx extensions:[/COLOR]
[COLOR=#000000]GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, [/COLOR]
[COLOR=#000000]GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, [/COLOR]
[COLOR=#000000]GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, [/COLOR]
[COLOR=#000000]GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, [/COLOR]
[COLOR=#000000]GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, [/COLOR]
[COLOR=#000000]GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, [/COLOR]
[COLOR=#000000]GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap[/COLOR]
[COLOR=#000000]GLX version: 1.2[/COLOR]
[COLOR=#000000]GLX extensions:[/COLOR]
[COLOR=#000000]GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, [/COLOR]
[COLOR=#000000]GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, [/COLOR]
[COLOR=#000000]GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, [/COLOR]
[COLOR=#000000]GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, [/COLOR]
[COLOR=#000000]GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group[/COLOR]
[COLOR=#000000]OpenGL vendor string: DRI R300 Project[/COLOR]
[COLOR=#000000]OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL[/COLOR]
[COLOR=#000000]OpenGL version string: 1.3 Mesa 7.4[/COLOR]
[COLOR=#000000]OpenGL extensions:[/COLOR]
[COLOR=#000000]GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, [/COLOR]
[COLOR=#000000]GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, [/COLOR]
[COLOR=#000000]GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, [/COLOR]
[COLOR=#000000]GL_ARB_texture_compression, GL_ARB_texture_cube_map, [/COLOR]
[COLOR=#000000]GL_ARB_texture_env_add, GL_ARB_texture_env_combine, [/COLOR]
[COLOR=#000000]GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, [/COLOR]
[COLOR=#000000]GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, [/COLOR]
[COLOR=#000000]GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, [/COLOR]
[COLOR=#000000]GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, [/COLOR]
[COLOR=#000000]GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, [/COLOR]
[COLOR=#000000]GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, [/COLOR]
[COLOR=#000000]GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, [/COLOR]
[COLOR=#000000]GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, [/COLOR]
[COLOR=#000000]GL_EXT_copy_texture, GL_EXT_draw_range_elements, [/COLOR]
[COLOR=#000000]GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, [/COLOR]
[COLOR=#000000]GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, [/COLOR]
[COLOR=#000000]GL_EXT_rescale_normal, GL_EXT_secondary_color, [/COLOR]
[COLOR=#000000]GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, [/COLOR]
[COLOR=#000000]GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, [/COLOR]
[COLOR=#000000]GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, [/COLOR]
[COLOR=#000000]GL_EXT_texture_env_add, GL_EXT_texture_env_combine, [/COLOR]
[COLOR=#000000]GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, [/COLOR]
[COLOR=#000000]GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, [/COLOR]
[COLOR=#000000]GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, [/COLOR]
[COLOR=#000000]GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, [/COLOR]
[COLOR=#000000]GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, [/COLOR]
[COLOR=#000000]GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, [/COLOR]
[COLOR=#000000]GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, [/COLOR]
[COLOR=#000000]GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, [/COLOR]
[COLOR=#000000]GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, [/COLOR]
[COLOR=#000000]GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, [/COLOR]
[COLOR=#000000]GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, [/COLOR]
[COLOR=#000000]GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, [/COLOR]
[COLOR=#000000]GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays[/COLOR]
 
[COLOR=#000000]16 GLX Visuals[/COLOR]
[COLOR=#000000]visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav[/COLOR]
[COLOR=#000000]id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat[/COLOR]
[COLOR=#000000]----------------------------------------------------------------------[/COLOR]
[COLOR=#000000]0x21 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x22 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x6b 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x6c 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x6d 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x6e 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x6f 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x70 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x71 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x72 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x73 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x74 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x75 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x76 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x77 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x5a 32 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
 
[COLOR=#000000]16 GLXFBConfigs:[/COLOR]
[COLOR=#000000]visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav[/COLOR]
[COLOR=#000000]id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat[/COLOR]
[COLOR=#000000]----------------------------------------------------------------------[/COLOR]
[COLOR=#000000]0x5b 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x5c 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x5d 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x5e 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x5f 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x60 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x61 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x62 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x63 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x64 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x65 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x66 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x67 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x68 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
[COLOR=#000000]0x69 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None[/COLOR]
[COLOR=#000000]0x6a 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow[/COLOR]
 
 
Entonces, la gran pregunta es.... TENGO ACELERACION 3D ??? y si estan instalados los drivers...
 
Muchas gracias....

---

### Post by Carlos C on 2009-08-05
Hola. Por favor ten cuidado con el lenguaje que usas y la manera en que escribes. Te pido que leas las normas del foro al respecto, así como el código de conducta:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Saludos.

---

### Post by baila0 on 2009-08-14
ALguien me puede responder por favor?

---

### Post by CdK1 on 2009-08-14
Nunca es malo buscar en google... 

[http://losmundosdeyupi.wordpress.com/2008/03/08/instalar-ubuntu-con-una-ati-x1250/](http://losmundosdeyupi.wordpress.com/2008/03/08/instalar-ubuntu-con-una-ati-x1250/)

---

### Post by robertor on 2009-08-14
> **baila0 said:**
> ALguien me puede responder por favor?
Tengo un problema similar. Estas corriendo el driver mesa. Por eso tienes soporte 3d, pero no es muy bueno que digamos... pero funciona con compiz, con lo básico al menos (a mi no me gusta, así que lo desactivo).

Saludos!
Roberto

---

### Post by gh05t2k on 2009-09-06
> **baila0 said:**
> H
 

[COLOR=#000000]direct rendering: Yes[/COLOR]


Según esto si tenes aceleración 3D. Probá glxinfo | grep rendering

---

