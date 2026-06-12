---
title: "Regnum"
date: 2007-10-22
forum: Ubuntu Gamers Arena
---

### Post by AnLGP on 2007-10-22
Hey,

I tried to launch Regnum and it tells me this:

Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version

-

So I checked what kind of file I am using and as I don't know what any of this means to me I'm going to post the output.

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, fast devsel, latency 0, IRQ 20
Memory at 52200000 (32-bit, non-prefetchable) [size=512K]
I/O ports at 20e0 [size=8]
Memory at 40000000 (32-bit, prefetchable) [size=256M]
Memory at 52280000 (32-bit, non-prefetchable) [size=256K]
Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: Gateway 2000 Unknown device 5049
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at 522c0000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
Memory behind bridge: 52300000-523fffff
Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
Memory behind bridge: 52400000-524fffff
Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at 2080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at 2060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at 2040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 0, IRQ 20
I/O ports at 2020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 0, IRQ 18
Memory at 522c4000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
I/O behind bridge: 00001000-00001fff
Memory behind bridge: 52000000-521fffff
Prefetchable memory behind bridge: 0000000050000000-0000000051ffffff
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at 20b0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
I/O ports at 20c8 [size=8]
I/O ports at 20ec [size=4]
I/O ports at 20c0 [size=8]
I/O ports at 20e8 [size=4]
I/O ports at 20a0 [size=16]
Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
Subsystem: Gateway 2000 Unknown device 5050
Flags: medium devsel, IRQ 11
I/O ports at 2000 [size=32]

03:00.0 Multimedia controller: ATI Technologies Inc Theater 550 PRO PCI [ATI TV Wonder 550]
Subsystem: ATI Technologies Inc Unknown device a346
Flags: bus master, medium devsel, latency 32, IRQ 11
Memory at 52000000 (32-bit, non-prefetchable) [size=1M]
Memory at 50000000 (32-bit, prefetchable) [size=32M]
Capabilities: <access denied>

03:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
Subsystem: Conexant Unknown device 2000
Flags: bus master, medium devsel, latency 32, IRQ 9
Memory at 52100000 (32-bit, non-prefetchable) [size=64K]
I/O ports at 1040 [size=8]
Capabilities: <access denied>

03:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, medium devsel, latency 32, IRQ 16
Memory at 52115000 (32-bit, non-prefetchable) [size=2K]
Memory at 52110000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
Subsystem: Gateway 2000 Unknown device 5049
Flags: bus master, medium devsel, latency 32, IRQ 21
Memory at 52114000 (32-bit, non-prefetchable) [size=4K]
I/O ports at 1000 [size=64]
Capabilities: <access denied>

--

what I want to know is -

Is it upgradeable a la option 2 or 3 above:

(2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version)

or is it the first option?

1. Your video card is too old

Thanks.

EDIT:

I have a Gateway GT5018E that was bought (guesstimate) within the last 12-18 months - could it be that my video card is too old?

I'd really like to play this game!  

Thanks for your help.

I also put this in another forum but came directly here from [http://gaming.gwos.org/doku.php]("http://gaming.gwos.org/doku.php")

so I figured I would repost it here because maybe it would get a better response.

---

### Post by compiledkernel on 2007-10-22
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
Subsystem: Gateway 2000 Unknown device 5050
Flags: bus master, fast devsel, latency 0, IRQ 20
Memory at 52200000 (32-bit, non-prefetchable) [size=512K]
I/O ports at 20e0 [size=8]
Memory at 40000000 (32-bit, prefetchable) [size=256M]
Memory at 52280000 (32-bit, non-prefetchable) [size=256K]
Capabilities: <access denied>

Thats your video card I assume. 

[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)

Intel graphics card. 

The linux drivers I hear are pretty shakey and unreliable, but I could be wrong.

---

### Post by AnLGP on 2007-10-22
Thanks for replying!

I'm not sure what to do there, though.

Failing my linux I have XP installed but it says 'error initializing Direct3D Renderer" or the equivilant and I can't get it to play there, either.

---

### Post by jaybombalous on 2007-10-23
card is not supported or its bad.

---

### Post by EdThaSlayer on 2007-10-24
> (2. You haven't installed the latest available drivers
 3. You haven't installed the latest DirectX version)
 


From what I have read above it seems that you are not using the linux version and have downloaded the setup.exe file instead of the linux. Visit this and download the linux version.
[http://www.regnumonline.com.ar/index.php?l=1&sec=6](http://www.regnumonline.com.ar/index.php?l=1&sec=6)

You also might not have 3d rendering turned on. Just open the terminal(in linux) by going to Applications->Others(the place where calculator can be found)-> Terminal.  Type "glxinfo" and tell us if direct rendering is enabled. If you are very unlucky, your graphic card might not even be able support direct3d(Windows) or openGL(Linux and Windows), meaning you can't play 3d games. Just tell me if anything confused you. :)

---

### Post by AnLGP on 2007-10-24
I'll be able to make it to linux at home tonight.  I'll be sure to remind myself to do this.

---

### Post by AnLGP on 2007-10-24
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by jascase901 on 2008-06-29
im running hardy heron with the same graphics card as you, and i got regnum working by installing driconf([http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)) and enabling  the st3c option which is on the second tab.

you can install driconf from the synaptic and you run it by typing driconf in the terminal.

---

### Post by prlewis on 2008-07-10
> **jascase901 said:**
> im running hardy heron with the same graphics card as you, and i got regnum working by installing driconf([http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)) and enabling  the st3c option which is on the second tab.

you can install driconf from the synaptic and you run it by typing driconf in the terminal.

I can confirm that this works for me with an intel 945.

Thanks!

---

### Post by aliayaz on 2008-07-29
> **prlewis said:**
> I can confirm that this works for me with an intel 945.

Thanks!

Really ?! i have the same Video Card you have and i tried before it didn't work now gonna download it again and try with DRICONFIG :D thank you for your help

---

### Post by fencer on 2008-09-27
> **jascase901 said:**
> im running hardy heron with the same graphics card as you, and i got regnum working by installing driconf([http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)) and enabling  the st3c option which is on the second tab.

you can install driconf from the synaptic and you run it by typing driconf in the terminal.

WTG pal thats what I was looking for a long time ago xD

---

### Post by joaquingo on 2008-11-14
it is works!!! and the performance is better on ubuntu. now the graphics do not are show properly, you know something to correct this? I tried different options in "3d acceleration" and nothing works. thanks
sorry for mi english

---

