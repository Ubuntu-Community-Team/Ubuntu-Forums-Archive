---
title: "(Disco) Chromium hight rate cpu"
date: 2019-03-31
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-03-31
Get randomly  a full cpu rate lock, and that error is logged:

 [HTML]chromium-browser.desktop[1608]: [2668:2668:0331/062808.264552:ERROR:sandbox_linux.cc(364)] InitializeSandbox() called with multiple threads in process gpu-process.[/HTML]

Need to kill the process and reload the browser till the next lock.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=918433](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=918433)

Should be sandboxed, but it is not , as listed below: "Sandboxed	false"


```
Graphics Feature Status
Canvas: Hardware accelerated
Flash: Hardware accelerated
Flash Stage3D: Hardware accelerated
Flash Stage3D Baseline profile: Hardware accelerated
Compositing: Hardware accelerated
Multiple Raster Threads: Enabled
Native GpuMemoryBuffers: Software only. Hardware acceleration disabled
Out-of-process Rasterization: Disabled
Hardware Protected Video Decode: Unavailable
Rasterization: Software only. Hardware acceleration disabled
Skia Renderer: Disabled
Surface Control: Disabled
Surface Synchronization: Enabled
Video Decode: Unavailable
Viz Service Display Compositor: Enabled
WebGL: Hardware accelerated
WebGL2: Hardware accelerated
Driver Bug Workarounds
adjust_src_dst_region_for_blitframebuffer
clear_uniforms_before_first_program_use
count_all_in_varyings_packing
disable_framebuffer_cmaa
disable_post_sub_buffers_for_onscreen_surfaces
exit_on_context_lost
msaa_is_slow
scalarize_vec_and_mat_constructor_args
disabled_extension_GL_KHR_blend_equation_advanced
disabled_extension_GL_KHR_blend_equation_advanced_coherent
Problems Detected
Accelerated video decode is unavailable on Linux: 137247
Disabled Features: accelerated_video_decode
Protected video decoding with swap chain is for Windows and Intel only
Disabled Features: protected_video_decode
Clear uniforms before first program use on all platforms: 124764, 349137
Applied Workarounds: clear_uniforms_before_first_program_use
Mesa drivers in Linux handle varyings without static use incorrectly: 333885
Applied Workarounds: count_all_in_varyings_packing
Disable partial swaps on Mesa drivers (detected with GL_RENDERER): 339493
Applied Workarounds: disable_post_sub_buffers_for_onscreen_surfaces
Always rewrite vec/mat constructors to be consistent: 398694
Applied Workarounds: scalarize_vec_and_mat_constructor_args
On Intel GPUs MSAA performance is not acceptable for GPU rasterization: 527565
Applied Workarounds: msaa_is_slow
Use GL_INTEL_framebuffer_CMAA on ChromeOS: 535198
Applied Workarounds: disable_framebuffer_cmaa
Disable partial swaps on Mesa drivers (detected with GL_VERSION): 339493
Applied Workarounds: disable_post_sub_buffers_for_onscreen_surfaces
adjust src/dst region if blitting pixels outside read framebuffer on Linux Intel: 664740
Applied Workarounds: adjust_src_dst_region_for_blitframebuffer
Disable KHR_blend_equation_advanced until cc shaders are updated: 661715
Applied Workarounds: disable(GL_KHR_blend_equation_advanced), disable(GL_KHR_blend_equation_advanced_coherent)
Some drivers can't recover after OUT_OF_MEM and context lost: 893177
Applied Workarounds: exit_on_context_lost
Native GpuMemoryBuffers have been disabled, either via about:flags or command line.
Disabled Features: native_gpu_memory_buffers
Skia renderer is not used by default.
Disabled Features: skia_renderer
Version Information
Data exported	2019-04-01T14:32:11.378Z
Chrome version	Chrome/73.0.3683.86
Operating system	Linux 5.0.0-8-generic
Software rendering list URL	[https://chromium.googlesource.com/chromium/src/+/f9b0bec6063ea50ce2b71f5b9abbae7beee319a6/gpu/config/software_rendering_list.json](https://chromium.googlesource.com/chromium/src/+/f9b0bec6063ea50ce2b71f5b9abbae7beee319a6/gpu/config/software_rendering_list.json)
Driver bug list URL	[https://chromium.googlesource.com/chromium/src/+/f9b0bec6063ea50ce2b71f5b9abbae7beee319a6/gpu/config/gpu_driver_bug_list.json](https://chromium.googlesource.com/chromium/src/+/f9b0bec6063ea50ce2b71f5b9abbae7beee319a6/gpu/config/gpu_driver_bug_list.json)
ANGLE commit id	unknown hash
2D graphics backend	Skia/73 636ee33902ddc27fd9683d250ceb23f65467488b-
Command Line	/usr/lib/chromium-browser/chromium-browser --ppapi-flash-path=/usr/lib/adobe-flashplugin/libpepflashplayer.so --ppapi-flash-version=32.0.0.156 --enable-pinch --flag-switches-begin --flag-switches-end
Driver Information
Initialization time	56
In-process GPU	false
Passthrough Command Decoder	false
Sandboxed	false
GPU0	VENDOR = 0x8086 [Intel Open Source Technology Center], DEVICE= 0x1912 [Mesa DRI Intel(R) HD Graphics 530 (Skylake GT2) ] *ACTIVE*
Optimus	false
AMD switchable	false
Driver vendor	Mesa
Driver version	19.0.1
Driver date	
GPU CUDA compute capability major version	0
Pixel shader version	4.50
Vertex shader version	4.50
Max. MSAA samples	16
Machine model name	
Machine model version	
GL_VENDOR	Intel Open Source Technology Center
GL_RENDERER	Mesa DRI Intel(R) HD Graphics 530 (Skylake GT2)
GL_VERSION	4.5 (Core Profile) Mesa 19.0.1
GL_EXTENSIONS	GL_3DFX_texture_compression_FXT1 GL_AMD_conservative_depth GL_AMD_depth_clamp_separate GL_AMD_draw_buffers_blend GL_AMD_gpu_shader_int64 GL_AMD_multi_draw_indirect GL_AMD_query_buffer_object GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_shader_trinary_minmax GL_AMD_texture_texture4 GL_AMD_vertex_shader_layer GL_AMD_vertex_shader_viewport_index GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_APPLE_object_purgeable GL_ARB_ES2_compatibility GL_ARB_ES3_1_compatibility GL_ARB_ES3_2_compatibility GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_compressed_texture_pixel_storage GL_ARB_compute_shader GL_ARB_conditional_render_inverted GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_indirect GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_shader GL_ARB_fragment_shader_interlock GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_gpu_shader_int64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_indirect_parameters GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect GL_ARB_occlusion_query2 GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_sprite GL_ARB_polygon_offset_clamp GL_ARB_post_depth_coverage GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_query_buffer_object GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counter_ops GL_ARB_shader_atomic_counters GL_ARB_shader_ballot GL_ARB_shader_bit_encoding GL_ARB_shader_clock GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_stencil_export GL_ARB_shader_storage_buffer_object GL_ARB_shader_subroutine GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shader_viewport_layer_array GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_barrier GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map_array GL_ARB_texture_filter_anisotropic GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transform_feedback_overflow_query GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ATI_blend_equation_separate GL_ATI_texture_float GL_EXT_abgr GL_EXT_blend_equation_separate GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_polygon_offset_clamp GL_EXT_provoking_vertex GL_EXT_shader_framebuffer_fetch GL_EXT_shader_framebuffer_fetch_non_coherent GL_EXT_shader_integer_mix GL_EXT_shader_samples_identical GL_EXT_texture_array GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_IBM_multimode_draw_arrays GL_INTEL_conservative_rasterization GL_INTEL_performance_query GL_INTEL_shader_atomic_float_minmax GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_robust_buffer_access_behavior GL_KHR_robustness GL_KHR_texture_compression_astc_ldr GL_KHR_texture_compression_astc_sliced_3d GL_MESA_pack_invert GL_MESA_shader_integer_functions GL_MESA_texture_signed_rgba GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fragment_shader_interlock GL_NV_packed_depth_stencil GL_NV_texture_barrier GL_OES_EGL_image GL_S3_s3tc
Disabled Extensions	GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent
Disabled WebGL Extensions	
Window system binding vendor	SGI
Window system binding version	1.4
Window system binding extensions	GLX_ARB_create_context GLX_ARB_create_context_no_error GLX_ARB_create_context_profile GLX_ARB_create_context_robustness GLX_ARB_fbconfig_float GLX_ARB_framebuffer_sRGB GLX_ARB_multisample GLX_EXT_create_context_es_profile GLX_EXT_create_context_es2_profile GLX_EXT_fbconfig_packed_float GLX_EXT_framebuffer_sRGB GLX_EXT_import_context GLX_EXT_libglvnd GLX_EXT_no_config_context GLX_EXT_texture_from_pixmap GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_INTEL_swap_event
Window manager	GNOME Shell
XDG_CURRENT_DESKTOP	GNOME
GDMSESSION	gnome-xorg
Compositing manager	Yes
Direct rendering	Yes
Reset notification strategy	0x8252
GPU process crash count	0
System visual ID	33
RGBA visual ID	318
Compositor Information
Tile Update Mode	One-copy
Partial Raster	Enabled
GpuMemoryBuffers Status
R_8	Software only
R_16	Software only
RG_88	Software only
BGR_565	Software only
RGBA_4444	Software only
RGBX_8888	Software only
RGBA_8888	Software only
BGRX_8888	Software only
BGRX_1010102	Software only
RGBX_1010102	Software only
BGRA_8888	Software only
RGBA_F16	Software only
YVU_420	Software only
YUV_420_BIPLANAR	Software only
UYVY_422	Software only
Display(s) Information
Info	Display[15343722355051076] bounds=[0,0 1920x1080], workarea=[0,27 1920x1053], scale=1, external.
Color space information	{primaries_d50_referred: [[0.6457, 0.3326], [0.3168, 0.5977], [0.1496, 0.0672]], transfer:GAMMA22, matrix:RGB, range:FULL}
Bits per color component	8
Bits per pixel	24
Video Acceleration Information
Log Messages
[3938:3938:0401/065940.851922:ERROR:sandbox_linux.cc(364)] : InitializeSandbox() called with multiple threads in process gpu-process.
[3938:3938:0401/070421.312254:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/071843.393547:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/071843.395821:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/072735.665524:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/073024.048752:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/073024.049010:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/085621.640329:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/090427.842592:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[3938:3938:0401/092947.917495:WARNING:x11_util.cc(1426)] : X error received: serial 2364018, error_code 170 (GLXBadWindow), request_code 152, minor_code 32 (X_GLXDestroyWindow)
[3938:3938:0401/092947.917666:WARNING:x11_util.cc(1426)] : X error received: serial 2364022, error_code 3 (BadWindow (invalid Window parameter)), request_code 4, minor_code 0 (X_DestroyWindow)
[3938:3938:0401/135410.652507:WARNING:ipc_message_attachment_set.cc(49)] : MessageAttachmentSet destroyed with unconsumed attachments: 0/1
```

---

