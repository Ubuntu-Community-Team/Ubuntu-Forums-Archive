---
title: "WRONG xorg.conf - constantly reproduced by the system"
date: 2014-02-16
forum: Ubuntu Development Version
---

### Post by 23dornot23d on 2014-02-16
Does any one on here know where to turn off this stupid feature - it must be a BUG ..........
 
How many times do people need the WRONG xorg.conf creating while in a session !!!!

If its meant to get people to a Black Screen of Death quickly .......... it works ........

I will try writing a empty file there for now and make it so that the system cannot remove it .........



[COLOR=#ff0000][SIZE=4]xorg.conf   >>>>> recreating itself between any change of desktop or  log out or even
                              swapping out of the session to go to the console.
[/SIZE][/COLOR]


It has to be ......... as there is no way you want to see the screen flashing at you each time you

change desktop environments ......

Thought the remedy was to remove the xorg.conf - but it keeps re-creating itself ..........


Boot back in again - the system knows best - so it sets it back up for you again WRONGLY

It would not be so bad if you could at least keep with the graphics working for a full session

But what happens - switch from KDE to Gnome or any other desktop and the xorg.conf

gets recreated again in between changing - BANG FLASH FLASH FLASH ...........

to a Black Screen ......... go remove the xorg.conf ......... go back in do some work log out

and the xorg,conf is back again ........... but its WRONG.

Madness ........... thought I would mention it .......

---

### Post by kansasnoob on 2014-02-16
> **23dornot23d said:**
> Does any one on here know where to turn off this stupid feature - it must be a BUG ..........
 
How many times do people need the WRONG xorg.conf creating while in a session !!!!

If its meant to get people to a Black Screen of Death quickly .......... it works ........

I will try writing a empty file there for now and make it so that the system cannot remove it .........



[COLOR=#ff0000][SIZE=4]xorg.conf   >>>>> recreating itself between any change of desktop or  log out or even
                              swapping out of the session to go to the console.
[/SIZE][/COLOR]


It has to be ......... as there is no way you want to see the screen flashing at you each time you

change desktop environments ......

Thought the remedy was to remove the xorg.conf - but it keeps re-creating itself ..........


Boot back in again - the system knows best - so it sets it back up for you again WRONGLY

It would not be so bad if you could at least keep with the graphics working for a full session

But what happens - switch from KDE to Gnome or any other desktop and the xorg.conf

gets recreated again in between changing - BANG FLASH FLASH FLASH ...........

to a Black Screen ......... go remove the xorg.conf ......... go back in do some work log out

and the xorg,conf is back again ........... but its WRONG.

Madness ........... **[COLOR="#FF0000"]thought I would mention it[/COLOR]** .......

You did NOT "mention it"!

You ranted and raved while providing no info regarding the hardware or the exact installation you started with.

Not a good way to ask for help :(

---

### Post by 23dornot23d on 2014-02-16
Yep you are right ........... will leave it at that then ............ [ rant over ]

fixed ...........

---

### Post by 23dornot23d on 2014-02-16
Apologies to anyone that visited looking for answers ..... here is what was happening and it will only affect
certain people with Optimus ( intel / Nvidia ) there seems to be a switch that is added and if it works then
all well and good - but if it does not - then it can drive you crazy as the machine keeps creating new xorg.conf
files each time you delete them.[COLOR=#ff0000]** nvidia-prime**[/COLOR]

Mux ..... problem for some users .......

Something called nvidia-prime keeps re-creating xorg.conf

The way to get rid of this - is to remove nvidia-prime

Then to remove lightdm and replace it with kdm ( reason it embeds something somewhere in lightdm )

maybe a config file somewhere but I found the easy solution was to remove it completely and put

a new window manger in its place - this just happened to be kdm ..... as gdm came up with a blank screen.

==============================

Will only effect people with the (Nvidia and Intel cards) Optimus

as it seems to want to install itself for them - maybe

Not all the time - we will see if anyone else has a problem - or if its just me .........

==============================

Will try to refrain from posting while my heads on fire ......... in future .........

Small video here - showing some problems with dynamic windows not always

showing what is in them ...... [http://youtu.be/7PlKDCXBFsE](http://youtu.be/7PlKDCXBFsE)

---

### Post by kansasnoob on 2014-02-16
Now that makes sense :D

I use this hardware for streaming video and audio:

AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

And recently there were some nvidia updates for Precise, including the installation of 'nvidia-prime'. Major blow-up :(

But that installation of Precise had multiple problems (it was actually a copy that had been installed while that drive was attached to other hardware) so I decided it was time to try Trusty.

Now, I don't remember why but I kind of gave up and then reinstalled Precise in a dual-boot w/Trusty so I could get back to streaming since I no longer have a TV or a radio in the house.

You now have my interest peaked though so I'll try booting Trusty again soon and see what happens.

---

### Post by kansasnoob on 2014-02-16
Possibly same as or similar to this bug:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1252442](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1252442)

I'm pretty ignorant when it comes to nVidia and even more so when it comes to Radeon :redface:

---

### Post by 23dornot23d on 2014-02-17
Yep that Bug report is along a similar line ......... thing is if the correct xorg.conf
was put in place then it would probably work well ..........

The thing is knowing how to create a xorg.conf for the new system and get it to
work properly with a Nvidia GT540 setup ..........

I must admit too ......... Precise is what I can always install and it picks the graphics
up for Nvidia perfectly for my two systems.

Have got this sorted now - but would not have wanted to leave this with little or no
information in it ........ you were correct in your assessment early on and I was thinking
that there was not going to be a easy way to fix it ......... only what looked like a bodge.

The nvidia-prime was the culprit ...... but after removing it - lightdm complained it was
trying to find a file that was missing - ( even doing aptitude reinstall lightdm did not fix it )

So removed lightdm and installed kdm ....... kdm tends to be better at picking up nvidia
anyway ......... and plymouth is a pain as well gdm is the worst I have ever seen it such 
a horrible bland start to a session.

Well all is ok now .......... and hope that you can use Trusty too for your streaming - I still believe
precise runs a lot faster than any of the later versions for most things and compiz still works 100%
on it too .

---

### Post by kansasnoob on 2014-02-17
I think it's fair to say that nvidia-prime is a mess. I've had pretty good luck with gdm and lightdm if it's using the lightdm-gtk-greeter, but lightdm with the unity-greeter has been problematic.

I'd forgotten, but it appears I upgraded that borked Precise to Trusty using the live DVD (yes that's a ubiquity thing) so I think those old update files are still there somewhere. I really need to poke around and see what went wrong. I was just impatient at that moment in time :oops:

---

### Post by kansasnoob on 2014-02-17
I did get my Trusty working by blowing away the xorg.conf but 'nvidia-prime' was not even installed. The performance was horrible though until I downgraded the nvidia driver.

Now I have a super stupid question - one that should maybe be asked elsewhere - how would I revert to the nouveau driver just for testing purposes?

Right now I'm getting better performance out of this hardware in Trusty:

Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

---

### Post by 23dornot23d on 2014-02-17
My performance on here is well down - by about 30 FPS ..... on the original setup I had.

[http://ubuntuforums.org/showthread.php?t=1871226&p=11641967#post11641967](http://ubuntuforums.org/showthread.php?t=1871226&p=11641967#post11641967)

That was on Natty ...... 90 FPS before - compared to the 60 FPS I am getting now.

I thought nouveau took over if it was not blacklisted ....... maybe that is what is 

causing me not to get the Nvidia to work properly.

Mine sets everything up for the intel ok - but nothing at all for the Nvidia ........

```

grep -i intel /var/log/Xorg.0.log
[    24.085] (==) Matched intel as autoconfigured driver 0
[    24.086] (==) Matched intel as autoconfigured driver 1
[    24.086] (II) LoadModule: "intel"
[    24.108] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.160] (II) Module intel: vendor="X.Org Foundation"
[    24.181] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[    24.196] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    24.196] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    24.196] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    24.211] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    24.230] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 3000
[    24.230] (--) intel(0): CPU: x86, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    24.230] (II) intel(0): Creating default Display subsection in Screen section
[    24.230] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.230] (==) intel(0): RGB weight 888
[    24.230] (==) intel(0): Default visual is TrueColor
[    24.230] (**) intel(0): Framebuffer tiled
[    24.230] (**) intel(0): Pixmaps tiled
[    24.231] (**) intel(0): "Tear free" disabled
[    24.231] (**) intel(0): Forcing per-crtc-pixmaps? no
[    24.231] (II) intel(0): Output LVDS1 has no monitor section
[    24.231] (--) intel(0): found backlight control interface acpi_video1 (type 'firmware')
[    24.231] (II) intel(0): Output VGA1 has no monitor section
[    24.231] (II) intel(0): Output HDMI1 has no monitor section
[    24.231] (II) intel(0): Output DP1 has no monitor section
[    24.231] (II) intel(0): Output VIRTUAL1 has no monitor section
[    24.231] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    24.231] (--) intel(0): Output HDMI1 using initial mode 1280x720 on pipe 1
[    24.231] (==) intel(0): DPI set to (96, 96)
[    24.277] (II) intel(0): SNA initialized with Sandybridge (gen6, gt2) backend
[    24.277] (==) intel(0): Backing store enabled
[    24.277] (==) intel(0): Silken mouse enabled
[    24.283] (II) intel(0): HW Cursor enabled
[    24.283] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.294] (==) intel(0): DPMS enabled
[    24.294] (II) intel(0): [DRI2] Setup complete
[    24.294] (II) intel(0): [DRI2]   DRI driver: i965
[    24.294] (II) intel(0): [DRI2]   VDPAU driver: i965
[    24.294] (II) intel(0): direct rendering: DRI2 Enabled
[    24.294] (==) intel(0): hotplug detection: "enabled"
[    24.495] (II) AIGLX: enabled GLX_INTEL_swap_event
[    24.510] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    24.528] (II) intel(0): switch to mode 1280x720@50.0 on HDMI1 using pipe 1, position (0, 0), rotation normal, reflection none
[    24.552] (II) intel(0): Setting screen physical size to 361 x 203
[    24.711] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[    24.711] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    24.712] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event10)
[    48.110] (II) intel(0): EDID vendor "ORN", prod id 4612
[    48.110] (II) intel(0): Using EDID range info for horizontal sync
[    48.110] (II) intel(0): Using EDID range info for vertical refresh
[    48.110] (II) intel(0): Printing DDC gathered Modelines:
[    48.110] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz eP)
[    48.110] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    48.110] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    48.110] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    48.110] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    48.110] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    48.110] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    48.110] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    48.110] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    48.110] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    51.934] (II) intel(0): resizing framebuffer to 2646x768
[    51.934] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    51.956] (II) intel(0): switch to mode 1280x720@50.0 on HDMI1 using pipe 1, position (0, 0), rotation normal, reflection none
[    51.972] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (1280, 0), rotation normal, reflection none
[    57.147] (II) intel(0): switch to mode 1280x720@50.0 on HDMI1 using pipe 0, position (1366, 0), rotation normal, reflection none
[    57.405] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none


```

Just showing the way its set up now - may come back to see whats changed once I do get the Nvidia up and running.
But it seems not to want to go in with the nvidia-current at the moment and I have tried many options - thing is wayland
seems to run very well using intel .

```

$ grep -i glx /var/log/Xorg.0.log
[    24.529] (II) "glx" will be loaded by default.
[    24.529] (II) LoadModule: "glx"
[    24.567] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.804] (II) Module glx: vendor="X.Org Foundation"
[    24.804] (==) AIGLX enabled
[    24.804] Loading extension GLX
[    25.213] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.213] (II) AIGLX: enabled GLX_ARB_create_context
[    25.213] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    25.213] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    25.213] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.213] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.213] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    25.213] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    25.213] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.214] (II) AIGLX: Loaded and initialized i965
[    25.214] (II) GLX: Initialized DRI2 GL provider for screen 0
[    51.269] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    51.269] (II) AIGLX: enabled GLX_ARB_create_context
[    51.269] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    51.269] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    51.269] (II) AIGLX: enabled GLX_INTEL_swap_event
[    51.269] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    51.269] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    51.269] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    51.269] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    51.269] (II) AIGLX: Loaded and initialized i965
[    51.269] (II) GLX: Initialized DRI2 GL provider for screen 0

```

But I should be able to use it later - will try some more once I have finished with wayland.

$ lspci -vnnn | grep VGA 
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 540M] [10de:0df4] (rev ff) (prog-if ff)





Decided to stick at it and am glad I did here are the new results

```

$ optirun glxgears -info
GL_RENDERER   = GeForce GT 540M/PCIe/SSE2
GL_VERSION    = 4.4.0 NVIDIA 331.38
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS  = GL_AMD_multi_draw_indirect GL_ARB_arrays_of_arrays  GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_buffer_storage  GL_ARB_clear_buffer_object GL_ARB_clear_texture  GL_ARB_color_buffer_float GL_ARB_compatibility  GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth  GL_ARB_compute_shader GL_ARB_compute_variable_group_size  GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_debug_output  GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture  GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_indirect  GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced  GL_ARB_enhanced_layouts GL_ARB_ES2_compatibility  GL_ARB_ES3_compatibility GL_ARB_explicit_attrib_location  GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions  GL_ARB_fragment_layer_viewport GL_ARB_fragment_program  GL_ARB_fragment_program_shadow GL_ARB_fragment_shader  GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object  GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4  GL_ARB_get_program_binary GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64  GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging  GL_ARB_indirect_parameters GL_ARB_instanced_arrays  GL_ARB_internalformat_query GL_ARB_internalformat_query2  GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment  GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect  GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query  GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object  GL_ARB_point_parameters GL_ARB_point_sprite  GL_ARB_program_interface_query GL_ARB_provoking_vertex  GL_ARB_robust_buffer_access_behavior GL_ARB_robustness  GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map  GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counters  GL_ARB_shader_bit_encoding GL_ARB_shader_draw_parameters  GL_ARB_shader_group_vote GL_ARB_shader_image_load_store  GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision  GL_ARB_query_buffer_object GL_ARB_shader_storage_buffer_object  GL_ARB_shader_subroutine GL_ARB_shader_texture_lod  GL_ARB_shading_language_100 GL_ARB_shading_language_420pack  GL_ARB_shading_language_include GL_ARB_shading_language_packing  GL_ARB_shadow GL_ARB_stencil_texturing GL_ARB_sync  GL_ARB_tessellation_shader GL_ARB_texture_border_clamp  GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32  GL_ARB_texture_buffer_range GL_ARB_texture_compression  GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc  GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array  GL_ARB_texture_env_add GL_ARB_texture_env_combine  GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float  GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge  GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample  GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels  GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg  GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage  GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle  GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2  GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced  GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object  GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object  GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding  GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader  GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev  GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers  GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc  GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform  GL_EXT_blend_color GL_EXT_blend_equation_separate  GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract  GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test  GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced  GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit  GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats  GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object  GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4  GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4  GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float  GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters  GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color  GL_EXT_separate_shader_objects GL_EXT_separate_specular_color  GL_EXT_shader_image_load_store GL_EXT_shadow_funcs  GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D  GL_EXT_texture_array GL_EXT_texture_buffer_object  GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc  GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc  GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp  GL_EXT_texture_env_combine GL_EXT_texture_env_dot3  GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer  GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp  GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB  GL_EXT_texture_sRGB_decode GL_EXT_texture_storage  GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2  GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit  GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_IBM_rasterpos_clip  GL_IBM_texture_mirrored_repeat GL_KHR_debug GL_KTX_buffer_region  GL_NV_bindless_multi_draw_indirect GL_NV_blend_equation_advanced  GL_NV_blend_square GL_NV_compute_program5 GL_NV_conditional_render  GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float  GL_NV_depth_clamp GL_NV_draw_texture GL_NV_ES1_1_compatibility  GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer  GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option  GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage  GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_gpu_program4_1  GL_NV_gpu_program5 GL_NV_gpu_program5_mem_extended  GL_NV_gpu_program_fp64 GL_NV_gpu_shader5 GL_NV_half_float  GL_NV_light_max_exponent GL_NV_multisample_coverage  GL_NV_multisample_filter_hint GL_NV_occlusion_query  GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object  GL_NV_parameter_buffer_object2 GL_NV_path_rendering  GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart  GL_NV_register_combiners GL_NV_register_combiners2  GL_NV_shader_atomic_counters GL_NV_shader_atomic_float  GL_NV_shader_buffer_load GL_NV_shader_storage_buffer_object  GL_ARB_sparse_texture GL_NV_texgen_reflection GL_NV_texture_barrier  GL_NV_texture_compression_vtc GL_NV_texture_env_combine4  GL_NV_texture_expand_normal GL_NV_texture_multisample  GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2  GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2  GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2  GL_NV_vertex_attrib_integer_64bit GL_NV_vertex_buffer_unified_memory  GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2  GL_NV_vertex_program2_option GL_NV_vertex_program3  GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_SGIS_generate_mipmap  GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow  GL_SUN_slice_accum 
4658 frames in 5.0 seconds = 931.306 FPS
4711 frames in 5.0 seconds = 942.134 FPS
5011 frames in 5.0 seconds = 1002.157 FPS
4975 frames in 5.0 seconds = 994.893 FPS


```

Something seems wrong with those figutres ..... so ran a test and here is the video

[http://youtu.be/f2oIzsMVB7M](http://youtu.be/f2oIzsMVB7M)

---

### Post by 23dornot23d on 2014-02-17
Decided to stick at it and am glad I did here are the new results

```

$ optirun glxgears -info
GL_RENDERER   = GeForce GT 540M/PCIe/SSE2
GL_VERSION    = 4.4.0 NVIDIA 331.38
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_AMD_multi_draw_indirect GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_compute_shader GL_ARB_compute_variable_group_size GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_indirect GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_indirect_parameters GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counters GL_ARB_shader_bit_encoding GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_query_buffer_object GL_ARB_shader_storage_buffer_object GL_ARB_shader_subroutine GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shader_image_load_store GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KHR_debug GL_KTX_buffer_region GL_NV_bindless_multi_draw_indirect GL_NV_blend_equation_advanced GL_NV_blend_square GL_NV_compute_program5 GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_draw_texture GL_NV_ES1_1_compatibility GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_gpu_program4_1 GL_NV_gpu_program5 GL_NV_gpu_program5_mem_extended GL_NV_gpu_program_fp64 GL_NV_gpu_shader5 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_path_rendering GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_shader_atomic_counters GL_NV_shader_atomic_float GL_NV_shader_buffer_load GL_NV_shader_storage_buffer_object GL_ARB_sparse_texture GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_attrib_integer_64bit GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
4658 frames in 5.0 seconds = 931.306 FPS
4711 frames in 5.0 seconds = 942.134 FPS
5011 frames in 5.0 seconds = 1002.157 FPS
4975 frames in 5.0 seconds = 994.893 FPS


```

Seems like the above was giving false figures or somehow working in a virtual world ..... not quite sure how
those can be so high .........

Here are the proper ones now its set up properly ........

```

7730ZG:/opt/VirtualGL/bin$ ./glxspheres
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
51.242985 frames/sec - 44.864259 Mpixels/sec
49.980669 frames/sec - 43.759075 Mpixels/sec
50.061401 frames/sec - 43.829758 Mpixels/sec
49.977160 frames/sec - 43.756004 Mpixels/sec
keith@keith-Aspire-7730ZG:/opt/VirtualGL/bin$ optirun ./glxspheres
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCIe/SSE2
130.400142 frames/sec - 114.167933 Mpixels/sec
135.526239 frames/sec - 118.655932 Mpixels/sec
134.232610 frames/sec - 117.523335 Mpixels/sec



```

Video of Nvidia Settings running   [http://youtu.be/24dV49hS8NM](http://youtu.be/24dV49hS8NM)

To set up the optimus gt540m + intel i965 ( ubuntu 14.04 testing )

First for me - remove nvidia-prime

Also removed all versions of nvidia drivers ..... these can be purged .......

Then installed 
apt-get install nvidia-331 nvidia-opencl-icd-331-updates
apt-get install nvidia-opencl-icd-331-updates libcuda1-331-updates
apt-get install nvidia-settings

apt-get install bumblebee bumblebee-nvidia primus

After this rebooted and my system was sorted.

apt-get install mesa-utils mesa-utils-extra

---

