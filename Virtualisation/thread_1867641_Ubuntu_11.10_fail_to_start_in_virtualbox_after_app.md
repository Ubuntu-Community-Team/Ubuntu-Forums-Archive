---
title: "Ubuntu 11.10 fail to start in virtualbox after applying guest OS add-ons."
date: 2011-10-23
forum: Virtualisation
---

### Post by georgelappies on 2011-10-23
Hi, I am currently using ubuntu 11.04 64bit version with only software installed from the official repositories and due to IT policies that is the way it must stay.

The version of virtualbox available in the 11.04 repo's is "4.0.4_OSE r70112".

11.10 install fine. As soon as I install the guest add-ons and reboot the system cannot boot anymore and freezes when showing the last dots.

I would like to test 11.10 thoroughly before installing it and would prefer running it in virtualbox. Is there a workaround?

---

### Post by haqking on 2011-10-23
> **georgelappies said:**
> Hi, I am currently using ubuntu 11.04 64bit version with only software installed from the official repositories and due to IT policies that is the way it must stay.

The version of virtualbox available in the 11.04 repo's is "4.0.4_OSE r70112".

11.10 install fine. As soon as I install the guest add-ons and reboot the system cannot boot anymore and freezes when showing the last dots.

I would like to test 11.10 thoroughly before installing it and would prefer running it in virtualbox. Is there a workaround?

could be many things, but the fact you are using old Vbox then that is the first thing i would fix, it is currently 4.1.4

if you can download the latest then you are left with checking the logs and playing with graphics settings.

For 11.10 i use 1 GB ram, 32 MB memory, 3D enabled and everything works fine including compiz (ccsm)

---

### Post by jurck on 2011-10-24
> **haqking said:**
> could be many things, but the fact you are using old Vbox then that is the first thing i would fix, it is currently 4.1.4

if you can download the latest then you are left with checking the logs and playing with graphics settings.

For 11.10 i use 1 GB ram, 32 MB memory, 3D enabled and everything works fine including compiz (ccsm)
I'm having the sane problem. I just upgraded the VirtulBox to the latest version, but  Kubuntu freezes when showing the last dots.

---

### Post by haqking on 2011-10-24
> **jurck said:**
> I'm having the sane problem. I just upgraded the VirtulBox to the latest version, but  Kubuntu freezes when showing the last dots.

so back to my post, have you checked the logs ?

what graphics settings are you using ?

---

### Post by nothingspecial on 2011-10-24
Thread moved to Vitualization.

---

### Post by jurck on 2011-10-24
> **haqking said:**
> so back to my post, have you checked the logs ?

what graphics settings are you using ?
Grafic settings are: 32 MB memory, 3D enabled 
Here is the log from Vbox

```
VirtualBox 4.1.4 r74291 win.amd64 (Oct  3 2011 16:38:50) release log
00:00:02.665 Log opened 2011-10-24T10:03:41.804171600Z
00:00:02.665 OS Product: Windows 7
00:00:02.665 OS Release: 6.1.7601
00:00:02.665 OS Service Pack: 1
00:00:02.668 Host RAM: 4046MB RAM, available: 2214MB
00:00:02.668 Executable: C:\Program Files\Oracle\VirtualBox\VirtualBox.exe
00:00:02.668 Process ID: 3396
00:00:02.668 Package type: WINDOWS_64BITS_GENERIC
00:00:02.668 Installed Extension Packs:
00:00:02.668   None installed!
00:00:02.692 SUP: Loaded VMMR0.r0 (C:\Program Files\Oracle\VirtualBox\VMMR0.r0) at 0xfffff8800970d000 - ModuleInit at fffff88009723a90 and ModuleTerm at fffff88009723b20 using the native ring-0 loader
00:00:02.692 SUP: VMMR0EntryEx located at fffff88009724ac0, VMMR0EntryFast at fffff88009723d10 and VMMR0EntryInt at fffff88009723d00
00:00:02.692 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VMMR0.r0=0xfffff8800970d000
00:00:02.713 File system of 'C:\Users\jurck\VirtualBox VMs\ubuntu\Snapshots' (snapshots) is unknown
00:00:02.713 File system of 'C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd' is ntfs
00:00:02.743 VBoxSharedClipboard mode: Bidirectional
00:00:02.960 OpenGL Info: Render SPU: GL_VENDOR:   ATI Technologies Inc.
00:00:02.960 OpenGL Info: Render SPU: GL_RENDERER: Radeon HD 6470M
00:00:02.960 OpenGL Info: Render SPU: GL_VERSION:  4.1.10531 Compatibility Profile Context
00:00:02.960 OpenGL Info: Render SPU: GL_EXTENSIONS: GL_AMDX_debug_output GL_AMDX_vertex_shader_tessellator GL_AMD_conservative_depth GL_AMD_debug_output GL_AMD_depth_clamp_separate GL_AMD_draw_buffers_blend GL_AMD_name_gen_delete GL_AMD_performance_monitor GL_AMD_sample_positions GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_shader_trace GL_AMD_texture_cube_map_array GL_AMD_texture_texture4 GL_AMD_transform_feedback3_lines_triangles GL_AMD_vertex_shader_tessellator GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_indirect GL_ARB_draw_instanced GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_stencil_export GL_ARB_shader_subroutine GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_compression GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_snorm GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_buffer GL_EXT_copy_texture GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shader_image_load_store GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_bptc GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_explicit_multisample GL_NV_float_buffer GL_NV_half_float GL_NV_primitive_restart GL_NV_texgen_reflection GL_NV_texture_barrier GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_WIN_swap_hint WGL_EXT_swap_control
00:00:02.962 Shared crOpenGL service loaded.
00:00:02.965 ************************* CFGM dump *************************
00:00:02.965 [/] (level 0)
00:00:02.965   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:02.965   CpuExecutionCap <integer> = 0x0000000000000064 (100)
00:00:02.965   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:02.965   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:02.965   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:02.965   Name            <string>  = "ubuntu" (cb=7)
00:00:02.965   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:02.965   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:02.965   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:02.965   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
00:00:02.965   RamSize         <integer> = 0x0000000040000000 (1073741824)
00:00:02.965   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:02.965   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:02.965   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:02.965   UUID            <bytes>   = "e5 fb c9 ed b6 d4 a0 4d 92 5d 86 ce 42 d6 f6 79" (cb=16)
00:00:02.965 
00:00:02.965 [/CPUM/] (level 1)
00:00:02.965   SyntheticCpu <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/] (level 1)
00:00:02.965 
00:00:02.965 [/Devices/8237A/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/8237A/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/] (level 3)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:02.965   Object <integer> = 0x0000000002574ed0 (39276240)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/Config/] (level 4)
00:00:02.965   GuestCoreDumpDir <string>  = "C:\Users\jurck\VirtualBox VMs\ubuntu\Snapshots" (cb=47)
00:00:02.965   RamSize          <integer> = 0x0000000040000000 (1073741824)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "HGCM" (cb=5)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:02.965   Object <integer> = 0x0000000003aef480 (61797504)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:02.965   Driver <string>  = "MainStatus" (cb=11)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:02.965   First   <integer> = 0x0000000000000000 (0)
00:00:02.965   Last    <integer> = 0x0000000000000000 (0)
00:00:02.965   papLeds <integer> = 0x00000000024f3e18 (38747672)
00:00:02.965 
00:00:02.965 [/Devices/acpi/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/Config/] (level 4)
00:00:02.965   CpuHotPlug        <integer> = 0x0000000000000000 (0)
00:00:02.965   FdcEnabled        <integer> = 0x0000000000000000 (0)
00:00:02.965   HostBusPciAddress <integer> = 0x0000000000000000 (0)
00:00:02.965   HpetEnabled       <integer> = 0x0000000000000000 (0)
00:00:02.965   IOAPIC            <integer> = 0x0000000000000000 (0)
00:00:02.965   IocPciAddress     <integer> = 0x0000000000010000 (65536)
00:00:02.965   NumCPUs           <integer> = 0x0000000000000001 (1)
00:00:02.965   RamHoleSize       <integer> = 0x0000000020000000 (536870912)
00:00:02.965   RamSize           <integer> = 0x0000000040000000 (1073741824)
00:00:02.965   Serial0IoPortBase <integer> = 0x0000000000000000 (0)
00:00:02.965   Serial0Irq        <integer> = 0x0000000000000000 (0)
00:00:02.965   Serial1IoPortBase <integer> = 0x0000000000000000 (0)
00:00:02.965   Serial1Irq        <integer> = 0x0000000000000000 (0)
00:00:02.965   ShowCpu           <integer> = 0x0000000000000000 (0)
00:00:02.965   ShowRtc           <integer> = 0x0000000000000000 (0)
00:00:02.965   SmcEnabled        <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "ACPIHost" (cb=9)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:02.965 
00:00:02.965 [/Devices/ahci/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x000000000000000d (13)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/Config/] (level 4)
00:00:02.965   Bootable        <integer> = 0x0000000000000001 (1)
00:00:02.965   PortCount       <integer> = 0x0000000000000001 (1)
00:00:02.965   PrimaryMaster   <integer> = 0x0000000000000000 (0)
00:00:02.965   PrimarySlave    <integer> = 0x0000000000000001 (1)
00:00:02.965   SecondaryMaster <integer> = 0x0000000000000002 (2)
00:00:02.965   SecondarySlave  <integer> = 0x0000000000000003 (3)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/Config/Port0/] (level 5)
00:00:02.965   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "Block" (cb=6)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.965   Driver <string>  = "VD" (cb=3)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.965   BlockCache <integer> = 0x0000000000000001 (1)
00:00:02.965   Format     <string>  = "VHD" (cb=4)
00:00:02.965   Path       <string>  = "C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd" (cb=48)
00:00:02.965   Type       <string>  = "HardDisk" (cb=9)
00:00:02.965   UseNewIo   <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/Config/] (level 5)
00:00:02.965   Mountable <integer> = 0x0000000000000000 (0)
00:00:02.965   Type      <string>  = "HardDisk" (cb=9)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#999/] (level 4)
00:00:02.965   Driver <string>  = "MainStatus" (cb=11)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#999/Config/] (level 5)
00:00:02.965   DeviceInstance        <string>  = "ahci/0" (cb=7)
00:00:02.965   First                 <integer> = 0x0000000000000000 (0)
00:00:02.965   Last                  <integer> = 0x0000000000000000 (0)
00:00:02.965   pConsole              <integer> = 0x00000000024f3920 (38746400)
00:00:02.965   papLeds               <integer> = 0x00000000024f3c28 (38747176)
00:00:02.965   pmapMediumAttachments <integer> = 0x00000000024f3e30 (38747696)
00:00:02.965 
00:00:02.965 [/Devices/apic/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/apic/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/apic/0/Config/] (level 4)
00:00:02.965   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:02.965   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/e1000/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/Config/] (level 4)
00:00:02.965   AdapterType    <integer> = 0x0000000000000000 (0)
00:00:02.965   CableConnected <integer> = 0x0000000000000001 (1)
00:00:02.965   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:02.965   MAC            <bytes>   = "08 00 27 d6 d3 06" (cb=6)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "NAT" (cb=4)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#0/Config/] (level 5)
00:00:02.965   AliasMode       <integer> = 0x0000000000000000 (0)
00:00:02.965   BootFile        <string>  = "ubuntu.pxe" (cb=11)
00:00:02.965   DNSProxy        <integer> = 0x0000000000000000 (0)
00:00:02.965   Network         <string>  = "10.0.2.0/24" (cb=12)
00:00:02.965   PassDomain      <integer> = 0x0000000000000001 (1)
00:00:02.965   TFTPPrefix      <string>  = "C:\Users\jurck/.VirtualBox\TFTP" (cb=32)
00:00:02.965   UseHostResolver <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#999/] (level 4)
00:00:02.965   Driver <string>  = "MainStatus" (cb=11)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#999/Config/] (level 5)
00:00:02.965   First   <integer> = 0x0000000000000000 (0)
00:00:02.965   Last    <integer> = 0x0000000000000000 (0)
00:00:02.965   papLeds <integer> = 0x00000000024f3dd8 (38747608)
00:00:02.965 
00:00:02.965 [/Devices/i8254/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/i8254/0/] (level 3)
00:00:02.965 
00:00:02.965 [/Devices/i8254/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/i8259/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/i8259/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/i8259/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "AUDIO" (cb=6)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:02.965   AudioDriver <string>  = "dsound" (cb=7)
00:00:02.965   StreamName  <string>  = "ubuntu" (cb=7)
00:00:02.965 
00:00:02.965 [/Devices/mc146818/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/mc146818/0/] (level 3)
00:00:02.965 
00:00:02.965 [/Devices/mc146818/0/Config/] (level 4)
00:00:02.965   UseUTC <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/parallel/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/pcarch/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/pcarch/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/pcarch/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/0/Config/] (level 4)
00:00:02.965   BootDevice0            <string>  = "FLOPPY" (cb=7)
00:00:02.965   BootDevice1            <string>  = "DVD" (cb=4)
00:00:02.965   BootDevice2            <string>  = "IDE" (cb=4)
00:00:02.965   BootDevice3            <string>  = "NONE" (cb=5)
00:00:02.965   FloppyDevice           <string>  = "i82078" (cb=7)
00:00:02.965   HardDiskDevice         <string>  = "piix3ide" (cb=9)
00:00:02.965   IOAPIC                 <integer> = 0x0000000000000000 (0)
00:00:02.965   McfgBase               <integer> = 0x0000000000000000 (0)
00:00:02.965   McfgLength             <integer> = 0x0000000000000000 (0)
00:00:02.965   NumCPUs                <integer> = 0x0000000000000001 (1)
00:00:02.965   PXEDebug               <integer> = 0x0000000000000000 (0)
00:00:02.965   RamHoleSize            <integer> = 0x0000000020000000 (536870912)
00:00:02.965   RamSize                <integer> = 0x0000000040000000 (1073741824)
00:00:02.965   SataHardDiskDevice     <string>  = "ahci" (cb=5)
00:00:02.965   SataPrimaryMasterLUN   <integer> = 0x0000000000000000 (0)
00:00:02.965   SataPrimarySlaveLUN    <integer> = 0x0000000000000001 (1)
00:00:02.965   SataSecondaryMasterLUN <integer> = 0x0000000000000002 (2)
00:00:02.965   SataSecondarySlaveLUN  <integer> = 0x0000000000000003 (3)
00:00:02.965   UUID                   <bytes>   = "e5 fb c9 ed b6 d4 a0 4d 92 5d 86 ce 42 d6 f6 79" (cb=16)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:02.966 
00:00:02.966 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
00:00:02.966   NIC           <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/pci/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/pci/0/] (level 3)
00:00:02.966   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/pci/0/Config/] (level 4)
00:00:02.966   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/] (level 3)
00:00:02.966   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/Config/] (level 4)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.966   Driver <string>  = "MainKeyboard" (cb=13)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.966   Object <integer> = 0x00000000024d9b80 (38640512)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:02.966   QueueSize <integer> = 0x0000000000000040 (64)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:02.966   Driver <string>  = "MouseQueue" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:02.966   Driver <string>  = "MainMouse" (cb=10)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:02.966   Object <integer> = 0x0000000002513730 (38876976)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:02.966   QueueSize <integer> = 0x0000000000000080 (128)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000008 (8)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/Config/] (level 4)
00:00:02.966   Am79C973       <integer> = 0x0000000000000000 (0)
00:00:02.966   CableConnected <integer> = 0x0000000000000000 (0)
00:00:02.966   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:02.966   MAC            <bytes>   = "08 00 27 eb f5 63" (cb=6)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "NAT" (cb=4)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#0/Config/] (level 5)
00:00:02.966   AliasMode       <integer> = 0x0000000000000000 (0)
00:00:02.966   BootFile        <string>  = "ubuntu.pxe" (cb=11)
00:00:02.966   DNSProxy        <integer> = 0x0000000000000000 (0)
00:00:02.966   Network         <string>  = "10.0.3.0/24" (cb=12)
00:00:02.966   PassDomain      <integer> = 0x0000000000000001 (1)
00:00:02.966   TFTPPrefix      <string>  = "C:\Users\jurck/.VirtualBox\TFTP" (cb=32)
00:00:02.966   UseHostResolver <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#999/] (level 4)
00:00:02.966   Driver <string>  = "MainStatus" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#999/Config/] (level 5)
00:00:02.966   First   <integer> = 0x0000000000000000 (0)
00:00:02.966   Last    <integer> = 0x0000000000000000 (0)
00:00:02.966   papLeds <integer> = 0x00000000024f3de0 (38747616)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/Config/] (level 4)
00:00:02.966   Type <string>  = "PIIX4" (cb=6)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/Config/SecondaryMaster/] (level 5)
00:00:02.966   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:02.966   Driver <string>  = "Block" (cb=6)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:02.966   Mountable <integer> = 0x0000000000000001 (1)
00:00:02.966   Type      <string>  = "DVD" (cb=4)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:02.966   Driver <string>  = "MainStatus" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:02.966   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
00:00:02.966   First                 <integer> = 0x0000000000000000 (0)
00:00:02.966   Last                  <integer> = 0x0000000000000003 (3)
00:00:02.966   pConsole              <integer> = 0x00000000024f3920 (38746400)
00:00:02.966   papLeds               <integer> = 0x00000000024f3c08 (38747144)
00:00:02.966   pmapMediumAttachments <integer> = 0x00000000024f3e30 (38747696)
00:00:02.966 
00:00:02.966 [/Devices/serial/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:02.966   Driver <string>  = "MainStatus" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:02.966   First   <integer> = 0x0000000000000000 (0)
00:00:02.966   Last    <integer> = 0x0000000000000000 (0)
00:00:02.966   papLeds <integer> = 0x00000000024f3e20 (38747680)
00:00:02.966 
00:00:02.966 [/Devices/vga/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/Config/] (level 4)
00:00:02.966   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:02.966   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:02.966   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:02.966   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:02.966   LogoFile         <string>  = "" (cb=1)
00:00:02.966   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:02.966   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:02.966   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:02.966   VRamSize         <integer> = 0x0000000002000000 (33554432)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "MainDisplay" (cb=12)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:02.966   Object <integer> = 0x0000000002574670 (39274096)
00:00:02.966 
00:00:02.966 [/Devices/virtio-net/] (level 2)
00:00:02.966 
00:00:02.966 [/HWVirtExt/] (level 1)
00:00:02.966   EnableLargePages   <integer> = 0x0000000000000001 (1)
00:00:02.966   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:02.966   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:02.966   Enabled            <integer> = 0x0000000000000001 (1)
00:00:02.966   Exclusive          <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/MM/] (level 1)
00:00:02.966   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/PDM/] (level 1)
00:00:02.966 
00:00:02.966 [/PDM/AsyncCompletion/] (level 2)
00:00:02.966 
00:00:02.966 [/PDM/AsyncCompletion/File/] (level 3)
00:00:02.966 
00:00:02.966 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:02.966 
00:00:02.966 [/PDM/BlkCache/] (level 2)
00:00:02.966   CacheSize <integer> = 0x0000000000500000 (5242880)
00:00:02.966 
00:00:02.966 [/PDM/Devices/] (level 2)
00:00:02.966 
00:00:02.966 [/PDM/Drivers/] (level 2)
00:00:02.966 
00:00:02.966 [/PDM/Drivers/VBoxC/] (level 3)
00:00:02.966   Path <string>  = "VBoxC" (cb=6)
00:00:02.966 
00:00:02.966 [/TM/] (level 1)
00:00:02.966   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/USB/] (level 1)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/] (level 2)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/] (level 3)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/Config/] (level 4)
00:00:02.966   Absolute <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "MouseQueue" (cb=11)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.966   Driver <string>  = "MainMouse" (cb=10)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.966   Object <integer> = 0x0000000002513730 (38876976)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/Config/] (level 5)
00:00:02.966   QueueSize <integer> = 0x0000000000000080 (128)
00:00:02.966 
00:00:02.966 [/USB/USBProxy/] (level 2)
00:00:02.966 
00:00:02.966 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:02.966 
00:00:02.966 ********************* End of CFGM dump **********************
00:00:02.966 MM: cbHyperHeap=0x140000 (1310720)
00:00:02.967 Logical host processors: 4 present, 4 max, 4 online, online mask: 000000000000000f
00:00:02.967 ************************* CPUID dump ************************
00:00:02.967          RAW Standard CPUIDs
00:00:02.967      Function  eax      ebx      ecx      edx
00:00:02.967 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:02.967 Hst:           0000000d 756e6547 6c65746e 49656e69
00:00:02.967 Gst: 00000001  000206a7 00000800 00000209 078bf1bf
00:00:02.967 Hst:           000206a7 01100800 1fbae3ff bfebfbff
00:00:02.967 Gst: 00000002  76035a01 00f0b2ff 00000000 00ca0000
00:00:02.967 Hst:           76035a01 00f0b2ff 00000000 00ca0000
00:00:02.967 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:02.967 Hst:           00000040 00000040 00000003 00021120
00:00:02.967 Name:                            GenuineIntel
00:00:02.967 Supports:                        0-5
00:00:02.967 Family:                          6      Extended: 0     Effective: 6
00:00:02.967 Model:                           10      Extended: 2     Effective: 42
00:00:02.967 Stepping:                        7
00:00:02.967 Type:                            0 (primary)
00:00:02.967 APIC ID:                         0x00
00:00:02.967 Logical CPUs:                    0
00:00:02.967 CLFLUSH Size:                    8
00:00:02.967 Brand ID:                        0x00
00:00:02.967 Mnemonic - Description                 = guest (host)
00:00:02.967 FPU - x87 FPU on Chip                  = 1 (1)
00:00:02.967 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:02.967 DE - Debugging extensions              = 1 (1)
00:00:02.967 PSE - Page Size Extension              = 1 (1)
00:00:02.967 TSC - Time Stamp Counter               = 1 (1)
00:00:02.967 MSR - Model Specific Registers         = 1 (1)
00:00:02.967 PAE - Physical Address Extension       = 0 (1)
00:00:02.967 MCE - Machine Check Exception          = 1 (1)
00:00:02.967 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:02.967 APIC - APIC On-Chip                    = 0 (1)
00:00:02.967 10 - Reserved                          = 0 (0)
00:00:02.967 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:02.967 MTRR - Memory Type Range Registers     = 1 (1)
00:00:02.967 PGE - PTE Global Bit                   = 1 (1)
00:00:02.967 MCA - Machine Check Architecture       = 1 (1)
00:00:02.967 CMOV - Conditional Move Instructions   = 1 (1)
00:00:02.967 PAT - Page Attribute Table             = 1 (1)
00:00:02.967 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:02.967 PSN - Processor Serial Number          = 0 (0)
00:00:02.967 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:02.967 20 - Reserved                          = 0 (0)
00:00:02.967 DS - Debug Store                       = 0 (1)
00:00:02.967 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:02.967 MMX - Intel MMX Technology             = 1 (1)
00:00:02.967 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:02.967 SSE - SSE Support                      = 1 (1)
00:00:02.967 SSE2 - SSE2 Support                    = 1 (1)
00:00:02.967 SS - Self Snoop                        = 0 (1)
00:00:02.967 HTT - Hyper-Threading Technology       = 0 (1)
00:00:02.967 TM - Thermal Monitor                   = 0 (1)
00:00:02.967 30 - Reserved                          = 0 (0)
00:00:02.967 PBE - Pending Break Enable             = 0 (1)
00:00:02.967 Supports SSE3                          = 1 (1)
00:00:02.967 PCLMULQDQ                              = 0 (1)
00:00:02.967 DS Area 64-bit layout                  = 0 (1)
00:00:02.967 Supports MONITOR/MWAIT                 = 1 (1)
00:00:02.967 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:02.967 VMX - Virtual Machine Technology       = 0 (1)
00:00:02.967 SMX - Safer Mode Extensions            = 0 (1)
00:00:02.967 Enhanced SpeedStep Technology          = 0 (1)
00:00:02.967 Terminal Monitor 2                     = 0 (1)
00:00:02.967 Supplemental SSE3 instructions         = 1 (1)
00:00:02.967 L1 Context ID                          = 0 (0)
00:00:02.967 11 - Reserved                          = 0 (0)
00:00:02.967 FMA extensions using YMM state         = 0 (0)
00:00:02.967 CMPXCHG16B instruction                 = 0 (1)
00:00:02.967 xTPR Update Control                    = 0 (1)
00:00:02.967 Perf/Debug Capability MSR              = 0 (1)
00:00:02.967 16 - Reserved                          = 0 (0)
00:00:02.967 PCID - Process-context identifiers     = 0 (1)
00:00:02.967 DCA - Direct Cache Access              = 0 (0)
00:00:02.967 SSE4.1 instruction extensions          = 0 (1)
00:00:02.967 SSE4.2 instruction extensions          = 0 (1)
00:00:02.967 Supports the x2APIC extensions         = 0 (1)
00:00:02.967 MOVBE instruction                      = 0 (0)
00:00:02.967 POPCNT instruction                     = 0 (1)
00:00:02.967 TSC-Deadline LAPIC timer mode          = 0 (1)
00:00:02.967 AESNI instruction extensions           = 0 (1)
00:00:02.967 XSAVE/XRSTOR extended state feature    = 0 (1)
00:00:02.967 Supports OSXSAVE                       = 0 (1)
00:00:02.967 AVX instruction extensions             = 0 (1)
00:00:02.967 29/30 - Reserved                       = 0x0 (0x0)
00:00:02.967 Hypervisor Present (we're a guest)     = 0 (0)
00:00:02.967 
00:00:02.967          RAW Extended CPUIDs
00:00:02.967      Function  eax      ebx      ecx      edx
00:00:02.967 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:02.967 Hst:           80000008 00000000 00000000 00000000
00:00:02.967 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000001 28100800
00:00:02.967 Gst: 80000002  20202020 49202020 6c65746e 20295228
00:00:02.967 Hst:           20202020 49202020 6c65746e 20295228
00:00:02.967 Gst: 80000003  65726f43 294d5428 2d356920 30343532
00:00:02.967 Hst:           65726f43 294d5428 2d356920 30343532
00:00:02.967 Gst: 80000004  5043204d 20402055 30362e32 007a4847
00:00:02.967 Hst:           5043204d 20402055 30362e32 007a4847
00:00:02.967 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: 80000006  00000000 00000000 01006040 00000000
00:00:02.967 Hst:           00000000 00000000 01006040 00000000
00:00:02.967 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000100
00:00:02.967 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:02.967 Hst:           00003024 00000000 00000000 00000000
00:00:02.967 Gst: 80000009  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Ext Name:                        
00:00:02.967 Ext Supports:                    0x80000000-0x80000008
00:00:02.967 Family:                          0      Extended: 0     Effective: 0
00:00:02.967 Model:                           0      Extended: 0     Effective: 0
00:00:02.967 Stepping:                        0
00:00:02.967 Brand ID:                        0x000
00:00:02.967 Mnemonic - Description                 = guest (host)
00:00:02.967 FPU - x87 FPU on Chip                  = 0 (0)
00:00:02.967 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:02.967 DE - Debugging extensions              = 0 (0)
00:00:02.967 PSE - Page Size Extension              = 0 (0)
00:00:02.967 TSC - Time Stamp Counter               = 0 (0)
00:00:02.967 MSR - K86 Model Specific Registers     = 0 (0)
00:00:02.967 PAE - Physical Address Extension       = 0 (0)
00:00:02.967 MCE - Machine Check Exception          = 0 (0)
00:00:02.967 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:02.967 APIC - APIC On-Chip                    = 0 (0)
00:00:02.967 10 - Reserved                          = 0 (0)
00:00:02.967 SEP - SYSCALL and SYSRET               = 0 (1)
00:00:02.967 MTRR - Memory Type Range Registers     = 0 (0)
00:00:02.967 PGE - PTE Global Bit                   = 0 (0)
00:00:02.967 MCA - Machine Check Architecture       = 0 (0)
00:00:02.967 CMOV - Conditional Move Instructions   = 0 (0)
00:00:02.967 PAT - Page Attribute Table             = 0 (0)
00:00:02.967 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:02.967 18 - Reserved                          = 0 (0)
00:00:02.967 19 - Reserved                          = 0 (0)
00:00:02.967 NX - No-Execute Page Protection        = 0 (1)
00:00:02.967 DS - Debug Store                       = 0 (0)
00:00:02.967 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:02.967 MMX - Intel MMX Technology             = 0 (0)
00:00:02.967 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:02.967 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:02.967 26 - 1 GB large page support           = 0 (0)
00:00:02.967 27 - RDTSCP instruction                = 0 (1)
00:00:02.967 28 - Reserved                          = 0 (0)
00:00:02.967 29 - AMD Long Mode                     = 0 (1)
00:00:02.967 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:02.967 31 - AMD 3DNow                         = 0 (0)
00:00:02.967 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:02.967 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:02.967 SVM - AMD VM Extensions                = 0 (0)
00:00:02.967 APIC registers starting at 0x400       = 0 (0)
00:00:02.967 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:02.967 Advanced bit manipulation              = 0 (0)
00:00:02.967 SSE4A instruction support              = 0 (0)
00:00:02.967 Misaligned SSE mode                    = 0 (0)
00:00:02.967 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:02.967 OS visible workaround                  = 0 (0)
00:00:02.967 Instruction based sampling             = 0 (0)
00:00:02.967 SSE5 support                           = 0 (0)
00:00:02.967 SKINIT, STGI, and DEV support          = 0 (0)
00:00:02.967 Watchdog timer support.                = 0 (0)
00:00:02.967 31:14 - Reserved                       = 0x0 (0x0)
00:00:02.967 Full Name:                              Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz
00:00:02.967 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:02.967 TLB 2/4M Data:                   res0     0 entries
00:00:02.967 TLB 4K Instr/Uni:                res0     0 entries
00:00:02.967 TLB 4K Data:                     res0     0 entries
00:00:02.967 L1 Instr Cache Line Size:        0 bytes
00:00:02.967 L1 Instr Cache Lines Per Tag:    0
00:00:02.967 L1 Instr Cache Associativity:    res0  
00:00:02.967 L1 Instr Cache Size:             0 KB
00:00:02.967 L1 Data Cache Line Size:         0 bytes
00:00:02.967 L1 Data Cache Lines Per Tag:     0
00:00:02.967 L1 Data Cache Associativity:     res0  
00:00:02.967 L1 Data Cache Size:              0 KB
00:00:02.967 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:02.967 L2 TLB 2/4M Data:                off       0 entries
00:00:02.967 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:02.967 L2 TLB 4K Data:                  off       0 entries
00:00:02.967 L2 Cache Line Size:              0 bytes
00:00:02.967 L2 Cache Lines Per Tag:          0
00:00:02.967 L2 Cache Associativity:          off   
00:00:02.967 L2 Cache Size:                   0 KB
00:00:02.967 APM Features:                   
00:00:02.967 Physical Address Width:          36 bits
00:00:02.967 Virtual Address Width:           48 bits
00:00:02.967 Guest Physical Address Width:    0 bits
00:00:02.967 Physical Core Count:             0
00:00:02.967 
00:00:02.967          RAW Centaur CPUIDs
00:00:02.967      Function  eax      ebx      ecx      edx
00:00:02.967 Gst: c0000000  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: c0000001  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: c0000002  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: c0000003  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Centaur Supports:                0xc0000000-0x00000000
00:00:02.967 
00:00:02.967 ******************** End of CPUID dump **********************
00:00:02.968 Debug: HCPhysInterPD=00000000bee99000 HCPhysInterPaePDPT=00000000bee96000 HCPhysInterPaePML4=00000000bee94000
00:00:02.968 Debug: apInterPTs={00000000bee98000,00000000bee97000} apInterPaePTs={000000003a9ad000,00000000352ae000} apInterPaePDs={00000000363ef000,000000011b830000,0000000037431000,0000000034032000} pInterPaePDPT64=00000000bee95000
00:00:02.968 Host paging mode: AMD64+PGE+NX
00:00:02.968 PGMPool: cMaxPages=560 (u64MaxPages=545)
00:00:02.968 pgmR3PoolInit: cMaxPages=0x230 cMaxUsers=0x460 cMaxPhysExts=0x460 fCacheEnable=true 
00:00:02.969 REM: Loading C:/Program Files/Oracle/VirtualBox/VBoxREM2.rel at 0x0000000008220040 (1178064 bytes)
00:00:02.969 REM: (gdb) add-symbol-file C:/Program Files/Oracle/VirtualBox/VBoxREM2.rel 0x0000000008220040
00:00:02.979 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=66
00:00:03.011 TM: cTSCTicksPerSecond=0x98fa7bf0 (2 566 552 560) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:03.011 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:03.012 CoreCode: R3=0000000006120000 R0=fffff880093cb000 RC=a0594000 Phys=00000000bedee000 cb=0x1000
00:00:03.013 AIOMgr: Default manager type is "Async"
00:00:03.013 AIOMgr: Default file backend is "NonBuffered"
00:00:03.013 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
00:00:03.013 BlkCache: Cache commit interval is 10000 ms
00:00:03.013 BlkCache: Cache commit threshold is 2621440 bytes
00:00:03.015 [SMP] BIOS with 1 CPUs
00:00:03.023 SUP: Loaded VBoxDDR0.r0 (C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0) at 0xfffff880097a9000 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000 using the native ring-0 loader
00:00:03.023 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0=0xfffff880097a9000
00:00:03.026 SUP: Loaded VBoxDD2R0.r0 (C:\Program Files\Oracle\VirtualBox\VBoxDD2R0.r0) at 0xfffff880097ce000 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000 using the native ring-0 loader
00:00:03.026 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VBoxDD2R0.r0=0xfffff880097ce000
00:00:03.026 Activating Local APIC
00:00:03.026 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:03.026 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:03.027 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.032 Shared Folders service loaded.
00:00:03.047 Chipset cannot do MSI: VERR_NOT_IMPLEMENTED
00:00:03.048 DrvBlock: Flushes will be ignored
00:00:03.048 DrvBlock: Async flushes will be passed to the disk
00:00:03.048 VDInit finished
00:00:03.076 AIOMgr: Endpoint for file 'C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd' (flags 000c0723) created successfully
00:00:03.085 AHCI: LUN#0: disk, PCHS=16383/16/63, total number of sectors 16777216
00:00:03.085 AHCI: LUN#0: using async I/O
00:00:03.086 AHCI ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 16777216
00:00:03.086 AHCI ATA: LUN#1: no unit
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.086 AHCI ATA: LUN#2: no unit
00:00:03.086 AHCI ATA: LUN#3: no unit
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.087 PIIX3 ATA: LUN#0: no unit
00:00:03.087 PIIX3 ATA: LUN#1: no unit
00:00:03.087 DrvBlock: Flushes will be ignored
00:00:03.087 DrvBlock: Async flushes will be passed to the disk
00:00:03.087 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:03.087 PIIX3 ATA: LUN#3: no unit
00:00:03.087 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:03.087 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:03.105 New value of somaxconn: 1
00:00:03.105 NAT: value of BindIP has been ignored
00:00:03.115 New value of somaxconn: 1
00:00:03.115 NAT: value of BindIP has been ignored
00:00:03.116 Audio: Trying driver 'dsound'.
00:00:03.142 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:03.153 VUSB: attached 'HidMouse' to port 1
00:00:03.169 DevPcBios: SATA LUN#0 LCHS=1024/255/63
00:00:03.169 PGM: The CPU physical address width is 36 bits
00:00:03.169 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:03.172 VMM: fUsePeriodicPreemptionTimers=false
00:00:03.172 HWACCM: Host CR4=000406F8
00:00:03.172 HWACCM: MSR_IA32_FEATURE_CONTROL      = 5
00:00:03.172 HWACCM: MSR_IA32_VMX_BASIC_INFO       = da040000000010
00:00:03.172 HWACCM: VMCS id                       = 10
00:00:03.172 HWACCM: VMCS size                     = 400
00:00:03.172 HWACCM: VMCS physical address limit   = None
00:00:03.172 HWACCM: VMCS memory type              = 6
00:00:03.172 HWACCM: Dual monitor treatment        = 1
00:00:03.172 HWACCM: MSR_IA32_VMX_PINBASED_CTLS    = 7f00000016
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_EXT_INT_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_NMI_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_VIRTUAL_NMI
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_PREEMPT_TIMER
00:00:03.172 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS   = fff9fffe0401e172
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_IRQ_WINDOW_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_TSC_OFFSET
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_HLT_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_INVLPG_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MWAIT_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDPMC_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDTSC_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_LOAD_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_STORE_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_TPR_SHADOW
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_NMI_WINDOW_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MOV_DR_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_UNCOND_IO_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_IO_BITMAPS
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_TRAP_FLAG
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_MSR_BITMAPS
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_PAUSE_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_USE_SECONDARY_EXEC_CTRL
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT *must* be set
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT *must* be set
00:00:03.172 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS2  = ff00000000
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VIRT_APIC
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_EPT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_DESCRIPTOR_INSTR_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_RDTSCP_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_X2APIC
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VPID
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_WBINVD_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_REAL_MODE
00:00:03.172 HWACCM: MSR_IA32_VMX_ENTRY_CTLS       = ffff000011ff
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_IA64_MODE
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_ENTRY_SMM
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_DEACTIVATE_DUALMON
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PERF_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PAT_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_EFER_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG *must* be set
00:00:03.172 HWACCM: MSR_IA32_VMX_EXIT_CTLS        = 7fffff00036dff
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_HOST_AMD64
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_ACK_EXTERNAL_IRQ
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_PAT_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_PAT_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_EFER_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_EFER_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_VMX_PREEMPT_TIMER
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG *must* be set
00:00:03.172 HWACCM: MSR_IA32_VMX_EPT_VPID_CAPS    = f0106114141
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_RWX_X_ONLY
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_GAW_48_BITS
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_UC
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_WB
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_SP_21_BITS
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_CONTEXT
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_ALL
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_INDIV
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_CONTEXT
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_ALL
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_CONTEXT_GLOBAL
00:00:03.172 HWACCM: MSR_IA32_VMX_MISC             = 100401e5
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_PREEMPT_TSC_BIT 5
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_ACTIVITY_STATES 7
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_CR3_TARGET      4
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_MAX_MSR         200
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_MSEG_ID         0
00:00:03.172 HWACCM: MSR_IA32_VMX_CR0_FIXED0       = 80000021
00:00:03.172 HWACCM: MSR_IA32_VMX_CR0_FIXED1       = ffffffff
00:00:03.172 HWACCM: MSR_IA32_VMX_CR4_FIXED0       = 2000
00:00:03.172 HWACCM: MSR_IA32_VMX_CR4_FIXED1       = 667ff
00:00:03.172 HWACCM: MSR_IA32_VMX_VMCS_ENUM        = 2a
00:00:03.172 HWACCM: TPR shadow physaddr           = 00000000beded000
00:00:03.172 HWACCM: VCPU0: MSR bitmap physaddr      = 00000000bedda000
00:00:03.172 HWACCM: VCPU0: VMCS physaddr            = 00000000bedec000
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled PAE
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled LONG MODE
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled syscall/ret
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled LAHF/SAHF
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled NXE
00:00:03.172 HWACCM: 32-bit and 64-bit guests supported.
00:00:03.172 HWACCM: VMX enabled!
00:00:03.172 HWACCM: Enabled nested paging
00:00:03.172 HWACCM: EPT root page                 = 00000000bee10000
00:00:03.172 HWACCM: Unrestricted guest execution enabled!
00:00:03.172 HWACCM: Large page support enabled!
00:00:03.172 HWACCM: enmFlushPage    1
00:00:03.172 HWACCM: enmFlushContext 1
00:00:03.172 HWACCM: TPR Patching disabled.
00:00:03.172 HWACCM: Using the VMX-preemption timer (cPreemptTimerShift=5)
00:00:03.172 HWACCM:    VT-x/AMD-V init method: LOCAL
00:00:03.175 VM: Halt method global1 (5)
00:00:03.175 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=125000
00:00:03.175 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:03.175 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:03.175 AIOMgr: Endpoints without assigned bandwidth groups:
00:00:03.175 AIOMgr:     C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd
00:00:03.175 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:03.178 Guest Log: BIOS: VirtualBox 4.1.4
00:00:03.178 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.182 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:03.182 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:03.182 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:03.182 AHCI ATA: Ctl: finished processing RESET
00:00:03.182 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:03.182 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:03.196 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=000000000ae60000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:03.394 2D video acceleration is disabled.
00:00:05.656 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=000000000ae60000 w=640 h=480 bpp=0 cbLine=0x280, flags=0x1
00:00:05.674 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:05.675 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:05.677 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:05.677 Guest Log: BIOS: Boot from CD-ROM failed
00:00:05.680 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:05.736 Guest Log: BIOS: Booting from Hard Disk...
00:00:05.736 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0xc4 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:05.736 AHCI ATA: Ctl: finished processing RESET
00:00:06.791 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=000000000ae60000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:09.678 PIT: mode=2 count=0x12a5 (4773) - 249.98 Hz (ch=0)
00:00:09.999 PIT: mode=4 count=0xb76 (2934) - 406.67 Hz (ch=0)
00:00:09.999 PIT: mode=4 count=0xb06 (2822) - 422.81 Hz (ch=0)
00:00:10.004 PIT: mode=4 count=0xbf1 (3057) - 390.31 Hz (ch=0)
00:00:10.004 PIT: mode=4 count=0x938 (2360) - 505.58 Hz (ch=0)
00:00:10.009 PIT: mode=4 count=0x7b8 (1976) - 603.83 Hz (ch=0)
00:00:10.009 PIT: mode=4 count=0x450 (1104) - 1080.78 Hz (ch=0)
00:00:10.013 PIT: mode=4 count=0x878 (2168) - 550.36 Hz (ch=0)
00:00:10.013 PIT: mode=4 count=0x566 (1382) - 863.37 Hz (ch=0)
00:00:10.016 PIT: mode=4 count=0x9fd (2557) - 466.63 Hz (ch=0)
00:00:10.016 PIT: mode=4 count=0x6fd (1789) - 666.95 Hz (ch=0)
00:00:10.020 PIT: mode=4 count=0x9e7 (2535) - 470.68 Hz (ch=0)
00:00:10.020 PIT: mode=4 count=0x724 (1828) - 652.72 Hz (ch=0)
00:00:10.024 PIT: mode=4 count=0x9dc (2524) - 472.73 Hz (ch=0)
00:00:10.024 PIT: mode=4 count=0x747 (1863) - 640.46 Hz (ch=0)
00:00:10.028 PIT: mode=4 count=0x94b (2379) - 501.54 Hz (ch=0)
00:00:10.028 PIT: mode=4 count=0x660 (1632) - 731.11 Hz (ch=0)
00:00:10.032 PIT: mode=4 count=0xa42 (2626) - 454.37 Hz (ch=0)
00:00:10.032 PIT: mode=4 count=0x7b8 (1976) - 603.83 Hz (ch=0)
00:00:10.036 PIT: mode=4 count=0xa2c (2604) - 458.21 Hz (ch=0)
00:00:10.036 PIT: mode=4 count=0x786 (1926) - 619.51 Hz (ch=0)
00:00:10.040 PIT: mode=4 count=0xa43 (2627) - 454.19 Hz (ch=0)
00:00:10.040 PIT: mode=4 count=0x7b6 (1974) - 604.44 Hz (ch=0)
00:00:10.044 PIT: mode=4 count=0xa35 (2613) - 456.63 Hz (ch=0)
00:00:10.044 PIT: mode=4 count=0x799 (1945) - 613.46 Hz (ch=0)
00:00:10.048 PIT: mode=4 count=0xa35 (2613) - 456.63 Hz (ch=0)
00:00:10.048 PIT: mode=4 count=0x793 (1939) - 615.35 Hz (ch=0)
00:00:10.052 PIT: mode=4 count=0x9f7 (2551) - 467.73 Hz (ch=0)
00:00:10.184 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:10.184 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:10.184 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:10.184 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:10.240 OHCI: Software reset
00:00:10.240 OHCI: USB Operational
00:00:24.487 NAT: IPv6 not supported
00:00:24.643 PCNet#1: Init: ss32=1 GCRDRA=0x39a3b000[32] GCTDRA=0x36e1c000[16]
00:00:25.082 NAT: DHCP offered IP address 10.0.2.15
00:00:25.083 NAT: DHCP offered IP address 10.0.2.15
00:00:27.414 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:27.415 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:27.455 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:39.704 PCNet#1: Init: ss32=1 GCRDRA=0x39a3b000[32] GCTDRA=0x36e1c000[16]
00:02:49.727 PCNet#1: Init: ss32=1 GCRDRA=0x39a3b000[32] GCTDRA=0x36e1c000[16]
02:01:09.991 NAT: DHCP offered IP address 10.0.2.15
02:01:20.738 OHCI: USB Reset
02:01:20.757 Entering S5 power state (power down)
02:01:20.757 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.
02:01:20.757 ****************** Guest state at power off ******************
02:01:20.757 Guest CPUM (VCPU 0) state: se
02:01:20.757 rax=0000000000001401 rbx=0000000000004004 rcx=0000000000004004 rdx=0000000000004004
02:01:20.757 rsi=0000000000001401 rdi=0000000000004004 r8 =0000000000000002 r9 =ffff880036c99cf8
02:01:20.757 r10=0000000000004020 r11=0000000000000000 r12=0000000000000010 r13=0000000000001401
02:01:20.757 r14=0000000000001401 r15=0000000000000000
02:01:20.757 rip=ffffffff81349cf3 rsp=ffff880036c99d08 rbp=ffff880036c99d08 iopl=0         nv up di pl nz na po nc
02:01:20.757 cs={0010 base=0000000000000000 limit=ffffffff flags=0000a09b}
02:01:20.757 ds={0000 base=0000000000000000 limit=000fffff flags=00010000}
02:01:20.757 es={0000 base=0000000000000000 limit=000fffff flags=00010000}
02:01:20.757 fs={0000 base=00007f4b7eb30720 limit=000fffff flags=00010000}
02:01:20.757 gs={0000 base=ffff88003fc00000 limit=000fffff flags=00010000}
02:01:20.757 ss={0018 base=0000000000000000 limit=ffffffff flags=0000c093}
02:01:20.757 cr0=000000008005003b cr2=00007f4b7e71fdf0 cr3=000000003bc75000 cr4=00000000000006f0
02:01:20.757 dr0=0000000000000000 dr1=0000000000000000 dr2=0000000000000000 dr3=0000000000000000
02:01:20.757 dr4=0000000000000000 dr5=0000000000000000 dr6=00000000ffff0ff0 dr7=0000000000000400
02:01:20.757 gdtr=ffff88003fc04000:007f  idtr=ffffffff81bbd000:0fff  eflags=00000046
02:01:20.757 ldtr={0000 base=00000000 limit=00000000 flags=00000082}
02:01:20.757 tr  ={0040 base=ffff88003fc10600 limit=00002087 flags=0000008b}
02:01:20.757 SysEnter={cs=0010 eip=ffffffff815f3630 esp=0000000000000000}
02:01:20.757 FCW=037f FSW=0000 FTW=0000 FOP=0000 MXCSR=00001fa1 MXCSR_MASK=0000ffff
02:01:20.757 FPUIP=5b145fa7 CS=0000 Rsrvd1=0000  FPUDP=d9d721f8 DS=0000 Rsvrd2=0000
02:01:20.757 ST(0)=FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(1)=FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(2)=FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(3)=FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(4)=FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(5)=FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(6)=FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(7)=FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 XMM0 =00000000'00000000'40bc65cb'4dc21dd0  XMM1 =00000000'00000000'40260ca4'14917000
02:01:20.757 XMM2 =00000000'00000000'41c7aaec'77800000  XMM3 =00000000'00000000'00000000'00000000
02:01:20.757 XMM4 =00000000'00000000'3ff00000'00000000  XMM5 =00000000'00000000'3ffc965b'0bc7e000
02:01:20.757 XMM6 =00000000'00000000'3fcec61b'fb5b5334  XMM7 =00000000'00000000'3ffc965b'0bc7e000
02:01:20.757 XMM8 =00000000'00000000'3fe84e79'01292b33  XMM9 =00ff0097'00850091'00ff0097'00850091
02:01:20.757 XMM10=00ff00ff'00ff00ff'00ff00ff'00ff00ff  XMM11=00ff00ff'00ff00ff'00ff00ff'00ff00ff
02:01:20.757 XMM12=00000000'00000000'00000000'00000000  XMM13=ff978591'ff978591'ff978591'ff978591
02:01:20.757 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
02:01:20.757 EFER         =0000000000000d01
02:01:20.757 PAT          =0007010600070106
02:01:20.757 STAR         =0023001000000000
02:01:20.757 CSTAR        =ffffffff815f3860
02:01:20.757 LSTAR        =ffffffff815f2230
02:01:20.757 SFMASK       =0000000000003700
02:01:20.757 KERNELGSBASE =0000000000000000
02:01:20.757 ***
02:01:20.757 Guest paging mode:  AMD64+NX, changed 14538 times, A20 enabled
02:01:20.757 Shadow paging mode: EPT
02:01:20.757 Host paging mode:   AMD64+G+NX
02:01:20.757 ***
02:01:20.757 Active Timers (pVM=0000000002640000)
02:01:20.757 pTimerR3         offNext  offPrev  offSched Clock               Time             Expire HzHint State                     Description
02:01:20.757 00000000080facc0 00017000 00000000 00000000 Real             8248332            8248339      0 2-ACTIVE                  VGA Refresh Timer
02:01:20.757 0000000008111cc0 ffffff80 fffe9000 00000000 Real             8248332            8248351      0 2-ACTIVE                  EMT Yielder
02:01:20.757 0000000008111c40 00000000 00000080 00000000 Real             8248332            8248741      0 2-ACTIVE                  CPU Load Timer
02:01:20.757 000000000810d230 ffffc8c0 00000000 00000000 Virt       7277581408074      7277585439253      0 2-ACTIVE                  Audio timer
02:01:20.757 0000000008109af0 00000000 00003740 00000000 Virt       7277581412205      7279149653560      0 2-ACTIVE                  E1000 Link Up Timer
02:01:20.757 00000000080f2b30 00000670 00000000 00000000 VrSy       7277581415905      7277582608442    434 2-ACTIVE                  i8254 Programmable Interval Timer
02:01:20.757 00000000080f31a0 0001d4b0 fffff990 00000000 VrSy       7277581420521      7277990000000      0 2-ACTIVE                  MC146818 RTC/CMOS - Second
02:01:20.757 0000000008110650 00000000 fffe2b50 00000000 VrSy       7277581424270      8399048221207      0 2-ACTIVE                  ACPI PM Timer
02:01:20.757 ***
02:01:20.757 Shadow GDT (GCAddr=ff596000):
02:01:20.757 ffd8 - 81180087 ff008900 - base=ff008118 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
02:01:20.757 ffe0 - 80900087 ff008900 - base=ff008090 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSS
02:01:20.757 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
02:01:20.757 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
02:01:20.757 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
02:01:20.757 ***
02:01:20.757 ************** End of Guest state at power off ***************
02:01:20.757 Changing the VM state from 'POWERING_OFF' to 'OFF'.
02:01:20.760 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
02:01:20.775 Changing the VM state from 'OFF' to 'DESTROYING'.
02:01:20.775 ************************* Statistics *************************
02:01:20.775 /Devices/E1k0/ReceiveBytes           3546 bytes
02:01:20.775 /Devices/E1k0/TransmitBytes         15030 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit0/AtapiDMA        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/AtapiPIO        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit0/WrittenBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit1/AtapiDMA        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/AtapiPIO        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit1/WrittenBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit0/AtapiDMA        1 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/AtapiPIO       20 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit0/WrittenBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit1/AtapiDMA        0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/AtapiPIO        0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit1/WrittenBytes        0 bytes
02:01:20.775 /Devices/PCNet1/ReceiveBytes            0 bytes
02:01:20.775 /Devices/PCNet1/TransmitBytes           0 bytes
02:01:20.775 /Devices/SATA0/Port0/DMA             3900 times
02:01:20.775 /Devices/SATA0/Port0/ReadBytes   149957632 bytes
02:01:20.775 /Devices/SATA0/Port0/WrittenBytes  5723136 bytes
02:01:20.775 /Devices/VMMDev/BalloonChunks           0 count
02:01:20.775 /FT/Checkpoint/Network                  0 times
02:01:20.775 /FT/Checkpoint/Storage                  0 times
02:01:20.775 /FT/Received/Mem                        0 bytes
02:01:20.775 /FT/Received/State                      0 bytes
02:01:20.775 /FT/Sent/Mem                            0 bytes
02:01:20.775 /FT/Sent/State                          0 bytes
02:01:20.775 /FT/Sync/DeltaMem                       0 times
02:01:20.775 /FT/Sync/DeltaVM                        0 times
02:01:20.775 /FT/Sync/Full                           0 times
02:01:20.775 /GVMM/EMTs                              1 calls
02:01:20.775 /GVMM/HostCPUs                          4 calls
02:01:20.775 /GVMM/HostCpus/0                        0 
02:01:20.775 /GVMM/HostCpus/0/CurTimerHz             0 Hz
02:01:20.775 /GVMM/HostCpus/0/DesiredHz              0 Hz
02:01:20.775 /GVMM/HostCpus/0/PPTChanges             0 times
02:01:20.775 /GVMM/HostCpus/0/PPTStarts              0 times
02:01:20.775 /GVMM/HostCpus/0/idxCpuSet              0 
02:01:20.775 /GVMM/HostCpus/1                        1 
02:01:20.775 /GVMM/HostCpus/1/CurTimerHz             0 Hz
02:01:20.775 /GVMM/HostCpus/1/DesiredHz              0 Hz
02:01:20.775 /GVMM/HostCpus/1/PPTChanges             0 times
02:01:20.775 /GVMM/HostCpus/1/PPTStarts              0 times
02:01:20.775 /GVMM/HostCpus/1/idxCpuSet              1 
02:01:20.776 /GVMM/HostCpus/2                        2 
02:01:20.776 /GVMM/HostCpus/2/CurTimerHz             0 Hz
02:01:20.776 /GVMM/HostCpus/2/DesiredHz              0 Hz
02:01:20.776 /GVMM/HostCpus/2/PPTChanges             0 times
02:01:20.776 /GVMM/HostCpus/2/PPTStarts              0 times
02:01:20.776 /GVMM/HostCpus/2/idxCpuSet              2 
02:01:20.776 /GVMM/HostCpus/3                        3 
02:01:20.776 /GVMM/HostCpus/3/CurTimerHz             0 Hz
02:01:20.776 /GVMM/HostCpus/3/DesiredHz              0 Hz
02:01:20.776 /GVMM/HostCpus/3/PPTChanges             0 times
02:01:20.776 /GVMM/HostCpus/3/PPTStarts              0 times
02:01:20.776 /GVMM/HostCpus/3/idxCpuSet              3 
02:01:20.776 /GVMM/Sum/HaltBlocking            3004462 calls
02:01:20.776 /GVMM/Sum/HaltCalls              105815187 calls
02:01:20.776 /GVMM/Sum/HaltNotBlocking        102810725 calls
02:01:20.776 /GVMM/Sum/HaltTimeouts            2703061 calls
02:01:20.776 /GVMM/Sum/HaltWakeUps                   0 calls
02:01:20.776 /GVMM/Sum/PokeCalls                   336 calls
02:01:20.776 /GVMM/Sum/PokeNotBusy                  30 calls
02:01:20.776 /GVMM/Sum/PollCalls                 38597 calls
02:01:20.776 /GVMM/Sum/PollHalts                     0 calls
02:01:20.776 /GVMM/Sum/PollWakeUps                   0 calls
02:01:20.776 /GVMM/Sum/WakeUpCalls              403445 calls
02:01:20.776 /GVMM/Sum/WakeUpNotHalted          224018 calls
02:01:20.776 /GVMM/Sum/WakeUpWakeUps                 0 calls
02:01:20.776 /GVMM/VM/HaltBlocking             3004462 calls
02:01:20.776 /GVMM/VM/HaltCalls               105815187 calls
02:01:20.776 /GVMM/VM/HaltNotBlocking         102810725 calls
02:01:20.776 /GVMM/VM/HaltTimeouts             2703061 calls
02:01:20.776 /GVMM/VM/HaltWakeUps                    0 calls
02:01:20.776 /GVMM/VM/PokeCalls                    336 calls
02:01:20.776 /GVMM/VM/PokeNotBusy                   30 calls
02:01:20.776 /GVMM/VM/PollCalls                  38597 calls
02:01:20.776 /GVMM/VM/PollHalts                      0 calls
02:01:20.776 /GVMM/VM/PollWakeUps                    0 calls
02:01:20.776 /GVMM/VM/WakeUpCalls               403445 calls
02:01:20.776 /GVMM/VM/WakeUpNotHalted           224018 calls
02:01:20.776 /GVMM/VM/WakeUpWakeUps                  0 calls
02:01:20.776 /GVMM/VMs                               1 calls
02:01:20.776 /MM/HyperHeap/cbFree              1049536 bytes
02:01:20.776 /MM/HyperHeap/cbHeap              1310400 bytes
02:01:20.776 /PDM/BlkCache/cbCached            4251648 bytes
02:01:20.776 /PDM/BlkCache/cbCachedFru               0 bytes
02:01:20.776 /PDM/BlkCache/cbCachedMruIn       4251648 bytes
02:01:20.776 /PDM/BlkCache/cbCachedMruOut            0 bytes
02:01:20.776 /PDM/BlkCache/cbMax               5242880 bytes
02:01:20.776 /PDM/CritSects/8237A#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/8237A#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/8237A#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/AHCI#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/AHCI#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/AHCI#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ATA#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ATA#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/ATA#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ATA#1/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ATA#1/ContentionRZLock       10 times
02:01:20.776 /PDM/CritSects/ATA#1/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/AudioSniffer#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/E1000#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/E1000#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/E1000#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/E1000#0RX/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/E1000#0RX/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/E1000#0RX/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/EM-REM/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA0/ContentionRZLock       18 times
02:01:20.776 /PDM/CritSects/EmulatedATA0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA1/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA1/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA1/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/FTM/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/FTM/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/FTM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/IOM Lock/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/IOM Lock/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/IOM Lock/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/NOP/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/NOP/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/NOP/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PCNet#1/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/PCNet#1/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/PCNet#1/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PDM/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/PDM/ContentionRZLock       45 times
02:01:20.776 /PDM/CritSects/PDM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PGM/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/PGM/ContentionRZLock        7 times
02:01:20.776 /PDM/CritSects/PGM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/REM-Register/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/VGA#u/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/VGA#u/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/VGA#u/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/VMMDev#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#u/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/VMMDev#u/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#u/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/acpi0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/acpi0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/acpi0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ahci#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ahci#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/ahci#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/e1000#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/e1000#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/e1000#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/i8259#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/i8259#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/i8259#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ichac97#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ichac97#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/ichac97#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/mc146818#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/mc146818#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/mc146818#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pcarch#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pcarch#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pcarch#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pcbios#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pcbios#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pcbios#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pci#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pci#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pci#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pckbd#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pckbd#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pckbd#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pcnet#1 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pcnet#1 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pcnet#1 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/piix3ide#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/piix3ide#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/piix3ide#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pit/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/pit/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pit/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/usb-ohci#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/vga#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/vga#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/vga#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/Queue/AHCI-Xmit/AllocFailures        0 times
02:01:20.776 /PDM/Queue/AHCI-Xmit/Flush              0 calls
02:01:20.776 /PDM/Queue/AHCI-Xmit/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/AHCI-Xmit/Insert          4079 calls
02:01:20.776 /PDM/Queue/AHCI-Xmit/cItems            60 count
02:01:20.776 /PDM/Queue/AHCI-Xmit/cbItem            32 bytes
02:01:20.776 /PDM/Queue/DevHlp/AllocFailures         0 times
02:01:20.776 /PDM/Queue/DevHlp/Flush                 0 calls
02:01:20.776 /PDM/Queue/DevHlp/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/DevHlp/Insert                0 calls
02:01:20.776 /PDM/Queue/DevHlp/cItems                8 count
02:01:20.776 /PDM/Queue/DevHlp/cbItem               48 bytes
02:01:20.776 /PDM/Queue/E1000-Rcv/AllocFailures        0 times
02:01:20.776 /PDM/Queue/E1000-Rcv/Flush              0 calls
02:01:20.776 /PDM/Queue/E1000-Rcv/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/E1000-Rcv/Insert            22 calls
02:01:20.776 /PDM/Queue/E1000-Rcv/cItems             1 count
02:01:20.776 /PDM/Queue/E1000-Rcv/cbItem            24 bytes
02:01:20.776 /PDM/Queue/E1000-Xmit/AllocFailures        0 times
02:01:20.776 /PDM/Queue/E1000-Xmit/Flush             0 calls
02:01:20.776 /PDM/Queue/E1000-Xmit/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/E1000-Xmit/Insert           74 calls
02:01:20.776 /PDM/Queue/E1000-Xmit/cItems            1 count
02:01:20.776 /PDM/Queue/E1000-Xmit/cbItem           24 bytes
02:01:20.776 /PDM/Queue/Keyboard/AllocFailures        0 times
02:01:20.776 /PDM/Queue/Keyboard/Flush               0 calls
02:01:20.776 /PDM/Queue/Keyboard/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/Keyboard/Insert              0 calls
02:01:20.776 /PDM/Queue/Keyboard/cItems             64 count
02:01:20.776 /PDM/Queue/Keyboard/cbItem             32 bytes
02:01:20.776 /PDM/Queue/Mouse/AllocFailures          0 times
02:01:20.776 /PDM/Queue/Mouse/Flush                  0 calls
02:01:20.776 /PDM/Queue/Mouse/FlushLeftovers         0 times
02:01:20.776 /PDM/Queue/Mouse/Insert                 0 calls
02:01:20.776 /PDM/Queue/Mouse/cItems               128 count
02:01:20.776 /PDM/Queue/Mouse/cbItem                56 bytes
02:01:20.776 /PDM/Queue/Mouse_1/AllocFailures        0 times
02:01:20.776 /PDM/Queue/Mouse_1/Flush                0 calls
02:01:20.776 /PDM/Queue/Mouse_1/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/Mouse_1/Insert             148 calls
02:01:20.776 /PDM/Queue/Mouse_1/cItems             128 count
02:01:20.776 /PDM/Queue/Mouse_1/cbItem              56 bytes
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/AllocFailures        0 times
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/Flush            0 calls
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/Insert           0 calls
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/cItems           1 count
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/cbItem          24 bytes
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/AllocFailures       36 times
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/Flush           0 calls
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/Insert         93 calls
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/cItems          1 count
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/cbItem         24 bytes
02:01:20.776 /PGM/CPU0/cGuestModeChanges         14538 times
02:01:20.776 /PGM/ChunkR3Map/Mapped                122 count
02:01:20.776 /PGM/ChunkR3Map/Unmapped                0 count
02:01:20.776 /PGM/ChunkR3Map/c                     122 count
02:01:20.776 /PGM/ChunkR3Map/cMax             4294967295 count
02:01:20.776 /PGM/LargePage/Recheck                  0 times
02:01:20.776 /PGM/LargePage/Refused                  2 times
02:01:20.776 /PGM/LargePage/Reused                 321 times
02:01:20.776 /PGM/Page/cAllPages                271559 count
02:01:20.776 /PGM/Page/cBalloonedPages               0 count
02:01:20.776 /PGM/Page/cHandyPages                  88 count
02:01:20.776 /PGM/Page/cLargePages                  31 count
02:01:20.776 /PGM/Page/cLargePagesDisabled           0 count
02:01:20.776 /PGM/Page/cMonitoredPages               0 count
02:01:20.776 /PGM/Page/cPrivatePages             71289 count
02:01:20.776 /PGM/Page/cPureMmioPages               37 count
02:01:20.776 /PGM/Page/cReadLockedPages              0 count
02:01:20.776 /PGM/Page/cReusedSharedPages            0 count
02:01:20.776 /PGM/Page/cSharedPages                  0 count
02:01:20.776 /PGM/Page/cWriteLockedPages             0 count
02:01:20.776 /PGM/Page/cWrittenToPages               0 count
02:01:20.776 /PGM/Page/cZeroPages               200233 count
02:01:20.776 /PGM/cRelocations                       0 times
02:01:20.776 /PROF/CPU0/EM/Capped                    0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/CPU0/EM/ForcedActions      250400514 times
02:01:20.776 /PROF/CPU0/EM/Halted               944948 times
02:01:20.776 /PROF/CPU0/EM/RAWTotal                  0 times
02:01:20.776 /PROF/CPU0/EM/REMTotal                  0 times
02:01:20.776 /PROF/CPU0/EM/Total              18878834523046 ticks/call (18878834523046 ticks,       1 times, max 18878834523046, min 18878834523046)
02:01:20.776 /PROF/VM/CPU0/Halt/Block            52249 ns/call (5528810557523 ticks, 105815183 times, max  15710184, min       1)
02:01:20.776 /PROF/VM/CPU0/Halt/BlockInsomnia        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/VM/CPU0/Halt/BlockOnTime          0 ns/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/VM/CPU0/Halt/BlockOverslept        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/VM/CPU0/Halt/Timers             925 ns/call (234053189378 ticks, 252839382 times, max   7136870, min       2)
02:01:20.776 /PROF/VM/CPU0/Halt/Yield             4681 ns/call (   180698106 ticks,   38597 times, max   2051907, min    1016)
02:01:20.776 /REM/TbFlushCount                       0 times
02:01:20.776 /REM/TbPhysInvldCount               14129 times
02:01:20.776 /REM/TlbFlushCount                  13922 times
02:01:20.776 /TM/CPU/00/cNsExecuting          54620921986 ns
02:01:20.776 /TM/CPU/00/cNsHalted             5856407961469 ns
02:01:20.776 /TM/CPU/00/cNsOther              1366555213940 ns
02:01:20.776 /TM/CPU/00/cNsTotal              7277584097395 ns
02:01:20.776 /TM/CPU/00/cPeriodsExecuting     13850274 count
02:01:20.776 /TM/CPU/00/cPeriodsHalted          944921 count
02:01:20.776 /TM/CPU/00/pctExecuting                30 %
02:01:20.776 /TM/CPU/00/pctHalted                    0 %
02:01:20.776 /TM/CPU/00/pctOther                    69 %
02:01:20.776 /TM/CPU/pctExecuting                   30 %
02:01:20.776 /TM/CPU/pctHalted                       0 %
02:01:20.776 /TM/CPU/pctOther                       69 %
02:01:20.776 /TM/MaxHzHint                           0 Hz
02:01:20.776 /TM/R0/1nsSteps                     34674 times
02:01:20.776 /TM/R3/1nsSteps                    193724 times
02:01:20.776 /TM/TSC/offCPU0                         0 ticks
02:01:20.776 /TM/VirtualSync/CurrentOffset           0 ns
02:01:20.776 /VUSB/0/cUrbsInPool                     1 count
02:01:20.776 ********************* End of statistics **********************
02:01:20.885 NAT: zone(nm:mbuf, used:1)
02:01:20.885 NAT: zone(nm:mbuf_cluster, used:0)
02:01:20.885 NAT: zone(nm:mbuf_packet, used:0)
02:01:20.885 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
02:01:20.885 NAT: zone(nm:mbuf_jumbo_9k, used:0)
02:01:20.885 NAT: zone(nm:mbuf_jumbo_16k, used:0)
02:01:20.886 NAT: zone(nm:mbuf, used:0)
02:01:20.886 NAT: zone(nm:mbuf_cluster, used:0)
02:01:20.886 NAT: zone(nm:mbuf_packet, used:0)
02:01:20.886 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
02:01:20.886 NAT: zone(nm:mbuf_jumbo_9k, used:0)
02:01:20.886 NAT: zone(nm:mbuf_jumbo_16k, used:0)
02:01:21.062 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
```

---

### Post by haqking on 2011-10-24
> **jurck said:**
> Grafic settings are: 32 MB memory, 3D enabled 
Here is the log from Vbox

```
VirtualBox 4.1.4 r74291 win.amd64 (Oct  3 2011 16:38:50) release log
00:00:02.665 Log opened 2011-10-24T10:03:41.804171600Z
00:00:02.665 OS Product: Windows 7
00:00:02.665 OS Release: 6.1.7601
00:00:02.665 OS Service Pack: 1
00:00:02.668 Host RAM: 4046MB RAM, available: 2214MB
00:00:02.668 Executable: C:\Program Files\Oracle\VirtualBox\VirtualBox.exe
00:00:02.668 Process ID: 3396
00:00:02.668 Package type: WINDOWS_64BITS_GENERIC
00:00:02.668 Installed Extension Packs:
00:00:02.668   None installed!
00:00:02.692 SUP: Loaded VMMR0.r0 (C:\Program Files\Oracle\VirtualBox\VMMR0.r0) at 0xfffff8800970d000 - ModuleInit at fffff88009723a90 and ModuleTerm at fffff88009723b20 using the native ring-0 loader
00:00:02.692 SUP: VMMR0EntryEx located at fffff88009724ac0, VMMR0EntryFast at fffff88009723d10 and VMMR0EntryInt at fffff88009723d00
00:00:02.692 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VMMR0.r0=0xfffff8800970d000
00:00:02.713 File system of 'C:\Users\jurck\VirtualBox VMs\ubuntu\Snapshots' (snapshots) is unknown
00:00:02.713 File system of 'C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd' is ntfs
00:00:02.743 VBoxSharedClipboard mode: Bidirectional
00:00:02.960 OpenGL Info: Render SPU: GL_VENDOR:   ATI Technologies Inc.
00:00:02.960 OpenGL Info: Render SPU: GL_RENDERER: Radeon HD 6470M
00:00:02.960 OpenGL Info: Render SPU: GL_VERSION:  4.1.10531 Compatibility Profile Context
00:00:02.960 OpenGL Info: Render SPU: GL_EXTENSIONS: GL_AMDX_debug_output GL_AMDX_vertex_shader_tessellator GL_AMD_conservative_depth GL_AMD_debug_output GL_AMD_depth_clamp_separate GL_AMD_draw_buffers_blend GL_AMD_name_gen_delete GL_AMD_performance_monitor GL_AMD_sample_positions GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_shader_trace GL_AMD_texture_cube_map_array GL_AMD_texture_texture4 GL_AMD_transform_feedback3_lines_triangles GL_AMD_vertex_shader_tessellator GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_indirect GL_ARB_draw_instanced GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_stencil_export GL_ARB_shader_subroutine GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_compression GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_snorm GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_buffer GL_EXT_copy_texture GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shader_image_load_store GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_bptc GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_explicit_multisample GL_NV_float_buffer GL_NV_half_float GL_NV_primitive_restart GL_NV_texgen_reflection GL_NV_texture_barrier GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_WIN_swap_hint WGL_EXT_swap_control
00:00:02.962 Shared crOpenGL service loaded.
00:00:02.965 ************************* CFGM dump *************************
00:00:02.965 [/] (level 0)
00:00:02.965   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:02.965   CpuExecutionCap <integer> = 0x0000000000000064 (100)
00:00:02.965   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:02.965   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:02.965   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:02.965   Name            <string>  = "ubuntu" (cb=7)
00:00:02.965   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:02.965   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:02.965   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:02.965   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
00:00:02.965   RamSize         <integer> = 0x0000000040000000 (1073741824)
00:00:02.965   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:02.965   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:02.965   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:02.965   UUID            <bytes>   = "e5 fb c9 ed b6 d4 a0 4d 92 5d 86 ce 42 d6 f6 79" (cb=16)
00:00:02.965 
00:00:02.965 [/CPUM/] (level 1)
00:00:02.965   SyntheticCpu <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/] (level 1)
00:00:02.965 
00:00:02.965 [/Devices/8237A/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/8237A/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/] (level 3)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:02.965 
00:00:02.965 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:02.965   Object <integer> = 0x0000000002574ed0 (39276240)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/Config/] (level 4)
00:00:02.965   GuestCoreDumpDir <string>  = "C:\Users\jurck\VirtualBox VMs\ubuntu\Snapshots" (cb=47)
00:00:02.965   RamSize          <integer> = 0x0000000040000000 (1073741824)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "HGCM" (cb=5)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:02.965   Object <integer> = 0x0000000003aef480 (61797504)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:02.965   Driver <string>  = "MainStatus" (cb=11)
00:00:02.965 
00:00:02.965 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:02.965   First   <integer> = 0x0000000000000000 (0)
00:00:02.965   Last    <integer> = 0x0000000000000000 (0)
00:00:02.965   papLeds <integer> = 0x00000000024f3e18 (38747672)
00:00:02.965 
00:00:02.965 [/Devices/acpi/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/Config/] (level 4)
00:00:02.965   CpuHotPlug        <integer> = 0x0000000000000000 (0)
00:00:02.965   FdcEnabled        <integer> = 0x0000000000000000 (0)
00:00:02.965   HostBusPciAddress <integer> = 0x0000000000000000 (0)
00:00:02.965   HpetEnabled       <integer> = 0x0000000000000000 (0)
00:00:02.965   IOAPIC            <integer> = 0x0000000000000000 (0)
00:00:02.965   IocPciAddress     <integer> = 0x0000000000010000 (65536)
00:00:02.965   NumCPUs           <integer> = 0x0000000000000001 (1)
00:00:02.965   RamHoleSize       <integer> = 0x0000000020000000 (536870912)
00:00:02.965   RamSize           <integer> = 0x0000000040000000 (1073741824)
00:00:02.965   Serial0IoPortBase <integer> = 0x0000000000000000 (0)
00:00:02.965   Serial0Irq        <integer> = 0x0000000000000000 (0)
00:00:02.965   Serial1IoPortBase <integer> = 0x0000000000000000 (0)
00:00:02.965   Serial1Irq        <integer> = 0x0000000000000000 (0)
00:00:02.965   ShowCpu           <integer> = 0x0000000000000000 (0)
00:00:02.965   ShowRtc           <integer> = 0x0000000000000000 (0)
00:00:02.965   SmcEnabled        <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "ACPIHost" (cb=9)
00:00:02.965 
00:00:02.965 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:02.965 
00:00:02.965 [/Devices/ahci/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x000000000000000d (13)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/Config/] (level 4)
00:00:02.965   Bootable        <integer> = 0x0000000000000001 (1)
00:00:02.965   PortCount       <integer> = 0x0000000000000001 (1)
00:00:02.965   PrimaryMaster   <integer> = 0x0000000000000000 (0)
00:00:02.965   PrimarySlave    <integer> = 0x0000000000000001 (1)
00:00:02.965   SecondaryMaster <integer> = 0x0000000000000002 (2)
00:00:02.965   SecondarySlave  <integer> = 0x0000000000000003 (3)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/Config/Port0/] (level 5)
00:00:02.965   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "Block" (cb=6)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.965   Driver <string>  = "VD" (cb=3)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.965   BlockCache <integer> = 0x0000000000000001 (1)
00:00:02.965   Format     <string>  = "VHD" (cb=4)
00:00:02.965   Path       <string>  = "C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd" (cb=48)
00:00:02.965   Type       <string>  = "HardDisk" (cb=9)
00:00:02.965   UseNewIo   <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#0/Config/] (level 5)
00:00:02.965   Mountable <integer> = 0x0000000000000000 (0)
00:00:02.965   Type      <string>  = "HardDisk" (cb=9)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#999/] (level 4)
00:00:02.965   Driver <string>  = "MainStatus" (cb=11)
00:00:02.965 
00:00:02.965 [/Devices/ahci/0/LUN#999/Config/] (level 5)
00:00:02.965   DeviceInstance        <string>  = "ahci/0" (cb=7)
00:00:02.965   First                 <integer> = 0x0000000000000000 (0)
00:00:02.965   Last                  <integer> = 0x0000000000000000 (0)
00:00:02.965   pConsole              <integer> = 0x00000000024f3920 (38746400)
00:00:02.965   papLeds               <integer> = 0x00000000024f3c28 (38747176)
00:00:02.965   pmapMediumAttachments <integer> = 0x00000000024f3e30 (38747696)
00:00:02.965 
00:00:02.965 [/Devices/apic/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/apic/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/apic/0/Config/] (level 4)
00:00:02.965   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:02.965   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/e1000/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/Config/] (level 4)
00:00:02.965   AdapterType    <integer> = 0x0000000000000000 (0)
00:00:02.965   CableConnected <integer> = 0x0000000000000001 (1)
00:00:02.965   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:02.965   MAC            <bytes>   = "08 00 27 d6 d3 06" (cb=6)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "NAT" (cb=4)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#0/Config/] (level 5)
00:00:02.965   AliasMode       <integer> = 0x0000000000000000 (0)
00:00:02.965   BootFile        <string>  = "ubuntu.pxe" (cb=11)
00:00:02.965   DNSProxy        <integer> = 0x0000000000000000 (0)
00:00:02.965   Network         <string>  = "10.0.2.0/24" (cb=12)
00:00:02.965   PassDomain      <integer> = 0x0000000000000001 (1)
00:00:02.965   TFTPPrefix      <string>  = "C:\Users\jurck/.VirtualBox\TFTP" (cb=32)
00:00:02.965   UseHostResolver <integer> = 0x0000000000000000 (0)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#999/] (level 4)
00:00:02.965   Driver <string>  = "MainStatus" (cb=11)
00:00:02.965 
00:00:02.965 [/Devices/e1000/0/LUN#999/Config/] (level 5)
00:00:02.965   First   <integer> = 0x0000000000000000 (0)
00:00:02.965   Last    <integer> = 0x0000000000000000 (0)
00:00:02.965   papLeds <integer> = 0x00000000024f3dd8 (38747608)
00:00:02.965 
00:00:02.965 [/Devices/i8254/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/i8254/0/] (level 3)
00:00:02.965 
00:00:02.965 [/Devices/i8254/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/i8259/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/i8259/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/i8259/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/] (level 3)
00:00:02.965   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.965   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:02.965   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.965   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:02.965   Driver <string>  = "AUDIO" (cb=6)
00:00:02.965 
00:00:02.965 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:02.965   AudioDriver <string>  = "dsound" (cb=7)
00:00:02.965   StreamName  <string>  = "ubuntu" (cb=7)
00:00:02.965 
00:00:02.965 [/Devices/mc146818/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/mc146818/0/] (level 3)
00:00:02.965 
00:00:02.965 [/Devices/mc146818/0/Config/] (level 4)
00:00:02.965   UseUTC <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/parallel/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/pcarch/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/pcarch/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/pcarch/0/Config/] (level 4)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/] (level 2)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/0/] (level 3)
00:00:02.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/0/Config/] (level 4)
00:00:02.965   BootDevice0            <string>  = "FLOPPY" (cb=7)
00:00:02.965   BootDevice1            <string>  = "DVD" (cb=4)
00:00:02.965   BootDevice2            <string>  = "IDE" (cb=4)
00:00:02.965   BootDevice3            <string>  = "NONE" (cb=5)
00:00:02.965   FloppyDevice           <string>  = "i82078" (cb=7)
00:00:02.965   HardDiskDevice         <string>  = "piix3ide" (cb=9)
00:00:02.965   IOAPIC                 <integer> = 0x0000000000000000 (0)
00:00:02.965   McfgBase               <integer> = 0x0000000000000000 (0)
00:00:02.965   McfgLength             <integer> = 0x0000000000000000 (0)
00:00:02.965   NumCPUs                <integer> = 0x0000000000000001 (1)
00:00:02.965   PXEDebug               <integer> = 0x0000000000000000 (0)
00:00:02.965   RamHoleSize            <integer> = 0x0000000020000000 (536870912)
00:00:02.965   RamSize                <integer> = 0x0000000040000000 (1073741824)
00:00:02.965   SataHardDiskDevice     <string>  = "ahci" (cb=5)
00:00:02.965   SataPrimaryMasterLUN   <integer> = 0x0000000000000000 (0)
00:00:02.965   SataPrimarySlaveLUN    <integer> = 0x0000000000000001 (1)
00:00:02.965   SataSecondaryMasterLUN <integer> = 0x0000000000000002 (2)
00:00:02.965   SataSecondarySlaveLUN  <integer> = 0x0000000000000003 (3)
00:00:02.965   UUID                   <bytes>   = "e5 fb c9 ed b6 d4 a0 4d 92 5d 86 ce 42 d6 f6 79" (cb=16)
00:00:02.965 
00:00:02.965 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:02.966 
00:00:02.966 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
00:00:02.966   NIC           <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/pci/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/pci/0/] (level 3)
00:00:02.966   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/pci/0/Config/] (level 4)
00:00:02.966   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/] (level 3)
00:00:02.966   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/Config/] (level 4)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.966   Driver <string>  = "MainKeyboard" (cb=13)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.966   Object <integer> = 0x00000000024d9b80 (38640512)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:02.966   QueueSize <integer> = 0x0000000000000040 (64)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:02.966   Driver <string>  = "MouseQueue" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:02.966   Driver <string>  = "MainMouse" (cb=10)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:02.966   Object <integer> = 0x0000000002513730 (38876976)
00:00:02.966 
00:00:02.966 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:02.966   QueueSize <integer> = 0x0000000000000080 (128)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000008 (8)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/Config/] (level 4)
00:00:02.966   Am79C973       <integer> = 0x0000000000000000 (0)
00:00:02.966   CableConnected <integer> = 0x0000000000000000 (0)
00:00:02.966   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:02.966   MAC            <bytes>   = "08 00 27 eb f5 63" (cb=6)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "NAT" (cb=4)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#0/Config/] (level 5)
00:00:02.966   AliasMode       <integer> = 0x0000000000000000 (0)
00:00:02.966   BootFile        <string>  = "ubuntu.pxe" (cb=11)
00:00:02.966   DNSProxy        <integer> = 0x0000000000000000 (0)
00:00:02.966   Network         <string>  = "10.0.3.0/24" (cb=12)
00:00:02.966   PassDomain      <integer> = 0x0000000000000001 (1)
00:00:02.966   TFTPPrefix      <string>  = "C:\Users\jurck/.VirtualBox\TFTP" (cb=32)
00:00:02.966   UseHostResolver <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#999/] (level 4)
00:00:02.966   Driver <string>  = "MainStatus" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/pcnet/1/LUN#999/Config/] (level 5)
00:00:02.966   First   <integer> = 0x0000000000000000 (0)
00:00:02.966   Last    <integer> = 0x0000000000000000 (0)
00:00:02.966   papLeds <integer> = 0x00000000024f3de0 (38747616)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/Config/] (level 4)
00:00:02.966   Type <string>  = "PIIX4" (cb=6)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/Config/SecondaryMaster/] (level 5)
00:00:02.966   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:02.966   Driver <string>  = "Block" (cb=6)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:02.966   Mountable <integer> = 0x0000000000000001 (1)
00:00:02.966   Type      <string>  = "DVD" (cb=4)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:02.966   Driver <string>  = "MainStatus" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:02.966   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
00:00:02.966   First                 <integer> = 0x0000000000000000 (0)
00:00:02.966   Last                  <integer> = 0x0000000000000003 (3)
00:00:02.966   pConsole              <integer> = 0x00000000024f3920 (38746400)
00:00:02.966   papLeds               <integer> = 0x00000000024f3c08 (38747144)
00:00:02.966   pmapMediumAttachments <integer> = 0x00000000024f3e30 (38747696)
00:00:02.966 
00:00:02.966 [/Devices/serial/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:02.966   Driver <string>  = "MainStatus" (cb=11)
00:00:02.966 
00:00:02.966 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:02.966   First   <integer> = 0x0000000000000000 (0)
00:00:02.966   Last    <integer> = 0x0000000000000000 (0)
00:00:02.966   papLeds <integer> = 0x00000000024f3e20 (38747680)
00:00:02.966 
00:00:02.966 [/Devices/vga/] (level 2)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/] (level 3)
00:00:02.966   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.966   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:02.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/Config/] (level 4)
00:00:02.966   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:02.966   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:02.966   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:02.966   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:02.966   LogoFile         <string>  = "" (cb=1)
00:00:02.966   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:02.966   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:02.966   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:02.966   VRamSize         <integer> = 0x0000000002000000 (33554432)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "MainDisplay" (cb=12)
00:00:02.966 
00:00:02.966 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:02.966   Object <integer> = 0x0000000002574670 (39274096)
00:00:02.966 
00:00:02.966 [/Devices/virtio-net/] (level 2)
00:00:02.966 
00:00:02.966 [/HWVirtExt/] (level 1)
00:00:02.966   EnableLargePages   <integer> = 0x0000000000000001 (1)
00:00:02.966   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:02.966   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:02.966   Enabled            <integer> = 0x0000000000000001 (1)
00:00:02.966   Exclusive          <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/MM/] (level 1)
00:00:02.966   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/PDM/] (level 1)
00:00:02.966 
00:00:02.966 [/PDM/AsyncCompletion/] (level 2)
00:00:02.966 
00:00:02.966 [/PDM/AsyncCompletion/File/] (level 3)
00:00:02.966 
00:00:02.966 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:02.966 
00:00:02.966 [/PDM/BlkCache/] (level 2)
00:00:02.966   CacheSize <integer> = 0x0000000000500000 (5242880)
00:00:02.966 
00:00:02.966 [/PDM/Devices/] (level 2)
00:00:02.966 
00:00:02.966 [/PDM/Drivers/] (level 2)
00:00:02.966 
00:00:02.966 [/PDM/Drivers/VBoxC/] (level 3)
00:00:02.966   Path <string>  = "VBoxC" (cb=6)
00:00:02.966 
00:00:02.966 [/TM/] (level 1)
00:00:02.966   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:02.966 
00:00:02.966 [/USB/] (level 1)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/] (level 2)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/] (level 3)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/Config/] (level 4)
00:00:02.966   Absolute <integer> = 0x0000000000000001 (1)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/] (level 4)
00:00:02.966   Driver <string>  = "MouseQueue" (cb=11)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.966   Driver <string>  = "MainMouse" (cb=10)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.966   Object <integer> = 0x0000000002513730 (38876976)
00:00:02.966 
00:00:02.966 [/USB/HidMouse/0/LUN#0/Config/] (level 5)
00:00:02.966   QueueSize <integer> = 0x0000000000000080 (128)
00:00:02.966 
00:00:02.966 [/USB/USBProxy/] (level 2)
00:00:02.966 
00:00:02.966 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:02.966 
00:00:02.966 ********************* End of CFGM dump **********************
00:00:02.966 MM: cbHyperHeap=0x140000 (1310720)
00:00:02.967 Logical host processors: 4 present, 4 max, 4 online, online mask: 000000000000000f
00:00:02.967 ************************* CPUID dump ************************
00:00:02.967          RAW Standard CPUIDs
00:00:02.967      Function  eax      ebx      ecx      edx
00:00:02.967 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:02.967 Hst:           0000000d 756e6547 6c65746e 49656e69
00:00:02.967 Gst: 00000001  000206a7 00000800 00000209 078bf1bf
00:00:02.967 Hst:           000206a7 01100800 1fbae3ff bfebfbff
00:00:02.967 Gst: 00000002  76035a01 00f0b2ff 00000000 00ca0000
00:00:02.967 Hst:           76035a01 00f0b2ff 00000000 00ca0000
00:00:02.967 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:02.967 Hst:           00000040 00000040 00000003 00021120
00:00:02.967 Name:                            GenuineIntel
00:00:02.967 Supports:                        0-5
00:00:02.967 Family:                          6      Extended: 0     Effective: 6
00:00:02.967 Model:                           10      Extended: 2     Effective: 42
00:00:02.967 Stepping:                        7
00:00:02.967 Type:                            0 (primary)
00:00:02.967 APIC ID:                         0x00
00:00:02.967 Logical CPUs:                    0
00:00:02.967 CLFLUSH Size:                    8
00:00:02.967 Brand ID:                        0x00
00:00:02.967 Mnemonic - Description                 = guest (host)
00:00:02.967 FPU - x87 FPU on Chip                  = 1 (1)
00:00:02.967 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:02.967 DE - Debugging extensions              = 1 (1)
00:00:02.967 PSE - Page Size Extension              = 1 (1)
00:00:02.967 TSC - Time Stamp Counter               = 1 (1)
00:00:02.967 MSR - Model Specific Registers         = 1 (1)
00:00:02.967 PAE - Physical Address Extension       = 0 (1)
00:00:02.967 MCE - Machine Check Exception          = 1 (1)
00:00:02.967 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:02.967 APIC - APIC On-Chip                    = 0 (1)
00:00:02.967 10 - Reserved                          = 0 (0)
00:00:02.967 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:02.967 MTRR - Memory Type Range Registers     = 1 (1)
00:00:02.967 PGE - PTE Global Bit                   = 1 (1)
00:00:02.967 MCA - Machine Check Architecture       = 1 (1)
00:00:02.967 CMOV - Conditional Move Instructions   = 1 (1)
00:00:02.967 PAT - Page Attribute Table             = 1 (1)
00:00:02.967 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:02.967 PSN - Processor Serial Number          = 0 (0)
00:00:02.967 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:02.967 20 - Reserved                          = 0 (0)
00:00:02.967 DS - Debug Store                       = 0 (1)
00:00:02.967 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:02.967 MMX - Intel MMX Technology             = 1 (1)
00:00:02.967 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:02.967 SSE - SSE Support                      = 1 (1)
00:00:02.967 SSE2 - SSE2 Support                    = 1 (1)
00:00:02.967 SS - Self Snoop                        = 0 (1)
00:00:02.967 HTT - Hyper-Threading Technology       = 0 (1)
00:00:02.967 TM - Thermal Monitor                   = 0 (1)
00:00:02.967 30 - Reserved                          = 0 (0)
00:00:02.967 PBE - Pending Break Enable             = 0 (1)
00:00:02.967 Supports SSE3                          = 1 (1)
00:00:02.967 PCLMULQDQ                              = 0 (1)
00:00:02.967 DS Area 64-bit layout                  = 0 (1)
00:00:02.967 Supports MONITOR/MWAIT                 = 1 (1)
00:00:02.967 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:02.967 VMX - Virtual Machine Technology       = 0 (1)
00:00:02.967 SMX - Safer Mode Extensions            = 0 (1)
00:00:02.967 Enhanced SpeedStep Technology          = 0 (1)
00:00:02.967 Terminal Monitor 2                     = 0 (1)
00:00:02.967 Supplemental SSE3 instructions         = 1 (1)
00:00:02.967 L1 Context ID                          = 0 (0)
00:00:02.967 11 - Reserved                          = 0 (0)
00:00:02.967 FMA extensions using YMM state         = 0 (0)
00:00:02.967 CMPXCHG16B instruction                 = 0 (1)
00:00:02.967 xTPR Update Control                    = 0 (1)
00:00:02.967 Perf/Debug Capability MSR              = 0 (1)
00:00:02.967 16 - Reserved                          = 0 (0)
00:00:02.967 PCID - Process-context identifiers     = 0 (1)
00:00:02.967 DCA - Direct Cache Access              = 0 (0)
00:00:02.967 SSE4.1 instruction extensions          = 0 (1)
00:00:02.967 SSE4.2 instruction extensions          = 0 (1)
00:00:02.967 Supports the x2APIC extensions         = 0 (1)
00:00:02.967 MOVBE instruction                      = 0 (0)
00:00:02.967 POPCNT instruction                     = 0 (1)
00:00:02.967 TSC-Deadline LAPIC timer mode          = 0 (1)
00:00:02.967 AESNI instruction extensions           = 0 (1)
00:00:02.967 XSAVE/XRSTOR extended state feature    = 0 (1)
00:00:02.967 Supports OSXSAVE                       = 0 (1)
00:00:02.967 AVX instruction extensions             = 0 (1)
00:00:02.967 29/30 - Reserved                       = 0x0 (0x0)
00:00:02.967 Hypervisor Present (we're a guest)     = 0 (0)
00:00:02.967 
00:00:02.967          RAW Extended CPUIDs
00:00:02.967      Function  eax      ebx      ecx      edx
00:00:02.967 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:02.967 Hst:           80000008 00000000 00000000 00000000
00:00:02.967 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000001 28100800
00:00:02.967 Gst: 80000002  20202020 49202020 6c65746e 20295228
00:00:02.967 Hst:           20202020 49202020 6c65746e 20295228
00:00:02.967 Gst: 80000003  65726f43 294d5428 2d356920 30343532
00:00:02.967 Hst:           65726f43 294d5428 2d356920 30343532
00:00:02.967 Gst: 80000004  5043204d 20402055 30362e32 007a4847
00:00:02.967 Hst:           5043204d 20402055 30362e32 007a4847
00:00:02.967 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: 80000006  00000000 00000000 01006040 00000000
00:00:02.967 Hst:           00000000 00000000 01006040 00000000
00:00:02.967 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000100
00:00:02.967 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:02.967 Hst:           00003024 00000000 00000000 00000000
00:00:02.967 Gst: 80000009  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Ext Name:                        
00:00:02.967 Ext Supports:                    0x80000000-0x80000008
00:00:02.967 Family:                          0      Extended: 0     Effective: 0
00:00:02.967 Model:                           0      Extended: 0     Effective: 0
00:00:02.967 Stepping:                        0
00:00:02.967 Brand ID:                        0x000
00:00:02.967 Mnemonic - Description                 = guest (host)
00:00:02.967 FPU - x87 FPU on Chip                  = 0 (0)
00:00:02.967 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:02.967 DE - Debugging extensions              = 0 (0)
00:00:02.967 PSE - Page Size Extension              = 0 (0)
00:00:02.967 TSC - Time Stamp Counter               = 0 (0)
00:00:02.967 MSR - K86 Model Specific Registers     = 0 (0)
00:00:02.967 PAE - Physical Address Extension       = 0 (0)
00:00:02.967 MCE - Machine Check Exception          = 0 (0)
00:00:02.967 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:02.967 APIC - APIC On-Chip                    = 0 (0)
00:00:02.967 10 - Reserved                          = 0 (0)
00:00:02.967 SEP - SYSCALL and SYSRET               = 0 (1)
00:00:02.967 MTRR - Memory Type Range Registers     = 0 (0)
00:00:02.967 PGE - PTE Global Bit                   = 0 (0)
00:00:02.967 MCA - Machine Check Architecture       = 0 (0)
00:00:02.967 CMOV - Conditional Move Instructions   = 0 (0)
00:00:02.967 PAT - Page Attribute Table             = 0 (0)
00:00:02.967 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:02.967 18 - Reserved                          = 0 (0)
00:00:02.967 19 - Reserved                          = 0 (0)
00:00:02.967 NX - No-Execute Page Protection        = 0 (1)
00:00:02.967 DS - Debug Store                       = 0 (0)
00:00:02.967 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:02.967 MMX - Intel MMX Technology             = 0 (0)
00:00:02.967 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:02.967 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:02.967 26 - 1 GB large page support           = 0 (0)
00:00:02.967 27 - RDTSCP instruction                = 0 (1)
00:00:02.967 28 - Reserved                          = 0 (0)
00:00:02.967 29 - AMD Long Mode                     = 0 (1)
00:00:02.967 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:02.967 31 - AMD 3DNow                         = 0 (0)
00:00:02.967 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:02.967 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:02.967 SVM - AMD VM Extensions                = 0 (0)
00:00:02.967 APIC registers starting at 0x400       = 0 (0)
00:00:02.967 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:02.967 Advanced bit manipulation              = 0 (0)
00:00:02.967 SSE4A instruction support              = 0 (0)
00:00:02.967 Misaligned SSE mode                    = 0 (0)
00:00:02.967 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:02.967 OS visible workaround                  = 0 (0)
00:00:02.967 Instruction based sampling             = 0 (0)
00:00:02.967 SSE5 support                           = 0 (0)
00:00:02.967 SKINIT, STGI, and DEV support          = 0 (0)
00:00:02.967 Watchdog timer support.                = 0 (0)
00:00:02.967 31:14 - Reserved                       = 0x0 (0x0)
00:00:02.967 Full Name:                              Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz
00:00:02.967 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:02.967 TLB 2/4M Data:                   res0     0 entries
00:00:02.967 TLB 4K Instr/Uni:                res0     0 entries
00:00:02.967 TLB 4K Data:                     res0     0 entries
00:00:02.967 L1 Instr Cache Line Size:        0 bytes
00:00:02.967 L1 Instr Cache Lines Per Tag:    0
00:00:02.967 L1 Instr Cache Associativity:    res0  
00:00:02.967 L1 Instr Cache Size:             0 KB
00:00:02.967 L1 Data Cache Line Size:         0 bytes
00:00:02.967 L1 Data Cache Lines Per Tag:     0
00:00:02.967 L1 Data Cache Associativity:     res0  
00:00:02.967 L1 Data Cache Size:              0 KB
00:00:02.967 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:02.967 L2 TLB 2/4M Data:                off       0 entries
00:00:02.967 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:02.967 L2 TLB 4K Data:                  off       0 entries
00:00:02.967 L2 Cache Line Size:              0 bytes
00:00:02.967 L2 Cache Lines Per Tag:          0
00:00:02.967 L2 Cache Associativity:          off   
00:00:02.967 L2 Cache Size:                   0 KB
00:00:02.967 APM Features:                   
00:00:02.967 Physical Address Width:          36 bits
00:00:02.967 Virtual Address Width:           48 bits
00:00:02.967 Guest Physical Address Width:    0 bits
00:00:02.967 Physical Core Count:             0
00:00:02.967 
00:00:02.967          RAW Centaur CPUIDs
00:00:02.967      Function  eax      ebx      ecx      edx
00:00:02.967 Gst: c0000000  00000000 00000000 00000000 00000000
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: c0000001  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: c0000002  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Gst: c0000003  00000000 00000000 00000000 00000000*
00:00:02.967 Hst:           00000000 00000000 00000000 00000000
00:00:02.967 Centaur Supports:                0xc0000000-0x00000000
00:00:02.967 
00:00:02.967 ******************** End of CPUID dump **********************
00:00:02.968 Debug: HCPhysInterPD=00000000bee99000 HCPhysInterPaePDPT=00000000bee96000 HCPhysInterPaePML4=00000000bee94000
00:00:02.968 Debug: apInterPTs={00000000bee98000,00000000bee97000} apInterPaePTs={000000003a9ad000,00000000352ae000} apInterPaePDs={00000000363ef000,000000011b830000,0000000037431000,0000000034032000} pInterPaePDPT64=00000000bee95000
00:00:02.968 Host paging mode: AMD64+PGE+NX
00:00:02.968 PGMPool: cMaxPages=560 (u64MaxPages=545)
00:00:02.968 pgmR3PoolInit: cMaxPages=0x230 cMaxUsers=0x460 cMaxPhysExts=0x460 fCacheEnable=true 
00:00:02.969 REM: Loading C:/Program Files/Oracle/VirtualBox/VBoxREM2.rel at 0x0000000008220040 (1178064 bytes)
00:00:02.969 REM: (gdb) add-symbol-file C:/Program Files/Oracle/VirtualBox/VBoxREM2.rel 0x0000000008220040
00:00:02.979 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=66
00:00:03.011 TM: cTSCTicksPerSecond=0x98fa7bf0 (2 566 552 560) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:03.011 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:03.012 CoreCode: R3=0000000006120000 R0=fffff880093cb000 RC=a0594000 Phys=00000000bedee000 cb=0x1000
00:00:03.013 AIOMgr: Default manager type is "Async"
00:00:03.013 AIOMgr: Default file backend is "NonBuffered"
00:00:03.013 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
00:00:03.013 BlkCache: Cache commit interval is 10000 ms
00:00:03.013 BlkCache: Cache commit threshold is 2621440 bytes
00:00:03.015 [SMP] BIOS with 1 CPUs
00:00:03.023 SUP: Loaded VBoxDDR0.r0 (C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0) at 0xfffff880097a9000 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000 using the native ring-0 loader
00:00:03.023 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0=0xfffff880097a9000
00:00:03.026 SUP: Loaded VBoxDD2R0.r0 (C:\Program Files\Oracle\VirtualBox\VBoxDD2R0.r0) at 0xfffff880097ce000 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000 using the native ring-0 loader
00:00:03.026 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VBoxDD2R0.r0=0xfffff880097ce000
00:00:03.026 Activating Local APIC
00:00:03.026 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:03.026 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:03.027 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.032 Shared Folders service loaded.
00:00:03.047 Chipset cannot do MSI: VERR_NOT_IMPLEMENTED
00:00:03.048 DrvBlock: Flushes will be ignored
00:00:03.048 DrvBlock: Async flushes will be passed to the disk
00:00:03.048 VDInit finished
00:00:03.076 AIOMgr: Endpoint for file 'C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd' (flags 000c0723) created successfully
00:00:03.085 AHCI: LUN#0: disk, PCHS=16383/16/63, total number of sectors 16777216
00:00:03.085 AHCI: LUN#0: using async I/O
00:00:03.086 AHCI ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 16777216
00:00:03.086 AHCI ATA: LUN#1: no unit
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.086 AHCI ATA: LUN#2: no unit
00:00:03.086 AHCI ATA: LUN#3: no unit
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.086 AHCI ATA: Ctl: finished processing RESET
00:00:03.087 PIIX3 ATA: LUN#0: no unit
00:00:03.087 PIIX3 ATA: LUN#1: no unit
00:00:03.087 DrvBlock: Flushes will be ignored
00:00:03.087 DrvBlock: Async flushes will be passed to the disk
00:00:03.087 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:03.087 PIIX3 ATA: LUN#3: no unit
00:00:03.087 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:03.087 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:03.105 New value of somaxconn: 1
00:00:03.105 NAT: value of BindIP has been ignored
00:00:03.115 New value of somaxconn: 1
00:00:03.115 NAT: value of BindIP has been ignored
00:00:03.116 Audio: Trying driver 'dsound'.
00:00:03.142 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:03.153 VUSB: attached 'HidMouse' to port 1
00:00:03.169 DevPcBios: SATA LUN#0 LCHS=1024/255/63
00:00:03.169 PGM: The CPU physical address width is 36 bits
00:00:03.169 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:03.172 VMM: fUsePeriodicPreemptionTimers=false
00:00:03.172 HWACCM: Host CR4=000406F8
00:00:03.172 HWACCM: MSR_IA32_FEATURE_CONTROL      = 5
00:00:03.172 HWACCM: MSR_IA32_VMX_BASIC_INFO       = da040000000010
00:00:03.172 HWACCM: VMCS id                       = 10
00:00:03.172 HWACCM: VMCS size                     = 400
00:00:03.172 HWACCM: VMCS physical address limit   = None
00:00:03.172 HWACCM: VMCS memory type              = 6
00:00:03.172 HWACCM: Dual monitor treatment        = 1
00:00:03.172 HWACCM: MSR_IA32_VMX_PINBASED_CTLS    = 7f00000016
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_EXT_INT_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_NMI_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_VIRTUAL_NMI
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_PREEMPT_TIMER
00:00:03.172 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS   = fff9fffe0401e172
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_IRQ_WINDOW_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_TSC_OFFSET
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_HLT_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_INVLPG_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MWAIT_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDPMC_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDTSC_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_LOAD_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_STORE_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_TPR_SHADOW
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_NMI_WINDOW_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MOV_DR_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_UNCOND_IO_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_IO_BITMAPS
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_TRAP_FLAG
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_MSR_BITMAPS
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_PAUSE_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_USE_SECONDARY_EXEC_CTRL
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT *must* be set
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT *must* be set
00:00:03.172 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS2  = ff00000000
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VIRT_APIC
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_EPT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_DESCRIPTOR_INSTR_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_RDTSCP_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_X2APIC
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VPID
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_WBINVD_EXIT
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_REAL_MODE
00:00:03.172 HWACCM: MSR_IA32_VMX_ENTRY_CTLS       = ffff000011ff
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_IA64_MODE
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_ENTRY_SMM
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_DEACTIVATE_DUALMON
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PERF_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PAT_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_EFER_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG *must* be set
00:00:03.172 HWACCM: MSR_IA32_VMX_EXIT_CTLS        = 7fffff00036dff
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_HOST_AMD64
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_ACK_EXTERNAL_IRQ
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_PAT_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_PAT_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_EFER_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_EFER_MSR
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_VMX_PREEMPT_TIMER
00:00:03.172 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG *must* be set
00:00:03.172 HWACCM: MSR_IA32_VMX_EPT_VPID_CAPS    = f0106114141
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_RWX_X_ONLY
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_GAW_48_BITS
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_UC
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_WB
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_SP_21_BITS
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_CONTEXT
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_ALL
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_INDIV
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_CONTEXT
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_ALL
00:00:03.172 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_CONTEXT_GLOBAL
00:00:03.172 HWACCM: MSR_IA32_VMX_MISC             = 100401e5
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_PREEMPT_TSC_BIT 5
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_ACTIVITY_STATES 7
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_CR3_TARGET      4
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_MAX_MSR         200
00:00:03.172 HWACCM:    MSR_IA32_VMX_MISC_MSEG_ID         0
00:00:03.172 HWACCM: MSR_IA32_VMX_CR0_FIXED0       = 80000021
00:00:03.172 HWACCM: MSR_IA32_VMX_CR0_FIXED1       = ffffffff
00:00:03.172 HWACCM: MSR_IA32_VMX_CR4_FIXED0       = 2000
00:00:03.172 HWACCM: MSR_IA32_VMX_CR4_FIXED1       = 667ff
00:00:03.172 HWACCM: MSR_IA32_VMX_VMCS_ENUM        = 2a
00:00:03.172 HWACCM: TPR shadow physaddr           = 00000000beded000
00:00:03.172 HWACCM: VCPU0: MSR bitmap physaddr      = 00000000bedda000
00:00:03.172 HWACCM: VCPU0: VMCS physaddr            = 00000000bedec000
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled PAE
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled LONG MODE
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled syscall/ret
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled LAHF/SAHF
00:00:03.172 CPUMSetGuestCpuIdFeature: Enabled NXE
00:00:03.172 HWACCM: 32-bit and 64-bit guests supported.
00:00:03.172 HWACCM: VMX enabled!
00:00:03.172 HWACCM: Enabled nested paging
00:00:03.172 HWACCM: EPT root page                 = 00000000bee10000
00:00:03.172 HWACCM: Unrestricted guest execution enabled!
00:00:03.172 HWACCM: Large page support enabled!
00:00:03.172 HWACCM: enmFlushPage    1
00:00:03.172 HWACCM: enmFlushContext 1
00:00:03.172 HWACCM: TPR Patching disabled.
00:00:03.172 HWACCM: Using the VMX-preemption timer (cPreemptTimerShift=5)
00:00:03.172 HWACCM:    VT-x/AMD-V init method: LOCAL
00:00:03.175 VM: Halt method global1 (5)
00:00:03.175 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=125000
00:00:03.175 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:03.175 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:03.175 AIOMgr: Endpoints without assigned bandwidth groups:
00:00:03.175 AIOMgr:     C:\Users\jurck\VirtualBox VMs\ubuntu\ubuntu.vhd
00:00:03.175 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:03.178 Guest Log: BIOS: VirtualBox 4.1.4
00:00:03.178 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.182 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:03.182 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:03.182 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:03.182 AHCI ATA: Ctl: finished processing RESET
00:00:03.182 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:03.182 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:03.196 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=000000000ae60000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:03.394 2D video acceleration is disabled.
00:00:05.656 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=000000000ae60000 w=640 h=480 bpp=0 cbLine=0x280, flags=0x1
00:00:05.674 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:05.675 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:05.677 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:05.677 Guest Log: BIOS: Boot from CD-ROM failed
00:00:05.680 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:05.736 Guest Log: BIOS: Booting from Hard Disk...
00:00:05.736 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0xc4 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:05.736 AHCI ATA: Ctl: finished processing RESET
00:00:06.791 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=000000000ae60000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:09.678 PIT: mode=2 count=0x12a5 (4773) - 249.98 Hz (ch=0)
00:00:09.999 PIT: mode=4 count=0xb76 (2934) - 406.67 Hz (ch=0)
00:00:09.999 PIT: mode=4 count=0xb06 (2822) - 422.81 Hz (ch=0)
00:00:10.004 PIT: mode=4 count=0xbf1 (3057) - 390.31 Hz (ch=0)
00:00:10.004 PIT: mode=4 count=0x938 (2360) - 505.58 Hz (ch=0)
00:00:10.009 PIT: mode=4 count=0x7b8 (1976) - 603.83 Hz (ch=0)
00:00:10.009 PIT: mode=4 count=0x450 (1104) - 1080.78 Hz (ch=0)
00:00:10.013 PIT: mode=4 count=0x878 (2168) - 550.36 Hz (ch=0)
00:00:10.013 PIT: mode=4 count=0x566 (1382) - 863.37 Hz (ch=0)
00:00:10.016 PIT: mode=4 count=0x9fd (2557) - 466.63 Hz (ch=0)
00:00:10.016 PIT: mode=4 count=0x6fd (1789) - 666.95 Hz (ch=0)
00:00:10.020 PIT: mode=4 count=0x9e7 (2535) - 470.68 Hz (ch=0)
00:00:10.020 PIT: mode=4 count=0x724 (1828) - 652.72 Hz (ch=0)
00:00:10.024 PIT: mode=4 count=0x9dc (2524) - 472.73 Hz (ch=0)
00:00:10.024 PIT: mode=4 count=0x747 (1863) - 640.46 Hz (ch=0)
00:00:10.028 PIT: mode=4 count=0x94b (2379) - 501.54 Hz (ch=0)
00:00:10.028 PIT: mode=4 count=0x660 (1632) - 731.11 Hz (ch=0)
00:00:10.032 PIT: mode=4 count=0xa42 (2626) - 454.37 Hz (ch=0)
00:00:10.032 PIT: mode=4 count=0x7b8 (1976) - 603.83 Hz (ch=0)
00:00:10.036 PIT: mode=4 count=0xa2c (2604) - 458.21 Hz (ch=0)
00:00:10.036 PIT: mode=4 count=0x786 (1926) - 619.51 Hz (ch=0)
00:00:10.040 PIT: mode=4 count=0xa43 (2627) - 454.19 Hz (ch=0)
00:00:10.040 PIT: mode=4 count=0x7b6 (1974) - 604.44 Hz (ch=0)
00:00:10.044 PIT: mode=4 count=0xa35 (2613) - 456.63 Hz (ch=0)
00:00:10.044 PIT: mode=4 count=0x799 (1945) - 613.46 Hz (ch=0)
00:00:10.048 PIT: mode=4 count=0xa35 (2613) - 456.63 Hz (ch=0)
00:00:10.048 PIT: mode=4 count=0x793 (1939) - 615.35 Hz (ch=0)
00:00:10.052 PIT: mode=4 count=0x9f7 (2551) - 467.73 Hz (ch=0)
00:00:10.184 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:10.184 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:10.184 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:10.184 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:10.240 OHCI: Software reset
00:00:10.240 OHCI: USB Operational
00:00:24.487 NAT: IPv6 not supported
00:00:24.643 PCNet#1: Init: ss32=1 GCRDRA=0x39a3b000[32] GCTDRA=0x36e1c000[16]
00:00:25.082 NAT: DHCP offered IP address 10.0.2.15
00:00:25.083 NAT: DHCP offered IP address 10.0.2.15
00:00:27.414 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:27.415 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:27.455 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:39.704 PCNet#1: Init: ss32=1 GCRDRA=0x39a3b000[32] GCTDRA=0x36e1c000[16]
00:02:49.727 PCNet#1: Init: ss32=1 GCRDRA=0x39a3b000[32] GCTDRA=0x36e1c000[16]
02:01:09.991 NAT: DHCP offered IP address 10.0.2.15
02:01:20.738 OHCI: USB Reset
02:01:20.757 Entering S5 power state (power down)
02:01:20.757 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.
02:01:20.757 ****************** Guest state at power off ******************
02:01:20.757 Guest CPUM (VCPU 0) state: se
02:01:20.757 rax=0000000000001401 rbx=0000000000004004 rcx=0000000000004004 rdx=0000000000004004
02:01:20.757 rsi=0000000000001401 rdi=0000000000004004 r8 =0000000000000002 r9 =ffff880036c99cf8
02:01:20.757 r10=0000000000004020 r11=0000000000000000 r12=0000000000000010 r13=0000000000001401
02:01:20.757 r14=0000000000001401 r15=0000000000000000
02:01:20.757 rip=ffffffff81349cf3 rsp=ffff880036c99d08 rbp=ffff880036c99d08 iopl=0         nv up di pl nz na po nc
02:01:20.757 cs={0010 base=0000000000000000 limit=ffffffff flags=0000a09b}
02:01:20.757 ds={0000 base=0000000000000000 limit=000fffff flags=00010000}
02:01:20.757 es={0000 base=0000000000000000 limit=000fffff flags=00010000}
02:01:20.757 fs={0000 base=00007f4b7eb30720 limit=000fffff flags=00010000}
02:01:20.757 gs={0000 base=ffff88003fc00000 limit=000fffff flags=00010000}
02:01:20.757 ss={0018 base=0000000000000000 limit=ffffffff flags=0000c093}
02:01:20.757 cr0=000000008005003b cr2=00007f4b7e71fdf0 cr3=000000003bc75000 cr4=00000000000006f0
02:01:20.757 dr0=0000000000000000 dr1=0000000000000000 dr2=0000000000000000 dr3=0000000000000000
02:01:20.757 dr4=0000000000000000 dr5=0000000000000000 dr6=00000000ffff0ff0 dr7=0000000000000400
02:01:20.757 gdtr=ffff88003fc04000:007f  idtr=ffffffff81bbd000:0fff  eflags=00000046
02:01:20.757 ldtr={0000 base=00000000 limit=00000000 flags=00000082}
02:01:20.757 tr  ={0040 base=ffff88003fc10600 limit=00002087 flags=0000008b}
02:01:20.757 SysEnter={cs=0010 eip=ffffffff815f3630 esp=0000000000000000}
02:01:20.757 FCW=037f FSW=0000 FTW=0000 FOP=0000 MXCSR=00001fa1 MXCSR_MASK=0000ffff
02:01:20.757 FPUIP=5b145fa7 CS=0000 Rsrvd1=0000  FPUDP=d9d721f8 DS=0000 Rsvrd2=0000
02:01:20.757 ST(0)=FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(1)=FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(2)=FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(3)=FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(4)=FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(5)=FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(6)=FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 ST(7)=FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
02:01:20.757 XMM0 =00000000'00000000'40bc65cb'4dc21dd0  XMM1 =00000000'00000000'40260ca4'14917000
02:01:20.757 XMM2 =00000000'00000000'41c7aaec'77800000  XMM3 =00000000'00000000'00000000'00000000
02:01:20.757 XMM4 =00000000'00000000'3ff00000'00000000  XMM5 =00000000'00000000'3ffc965b'0bc7e000
02:01:20.757 XMM6 =00000000'00000000'3fcec61b'fb5b5334  XMM7 =00000000'00000000'3ffc965b'0bc7e000
02:01:20.757 XMM8 =00000000'00000000'3fe84e79'01292b33  XMM9 =00ff0097'00850091'00ff0097'00850091
02:01:20.757 XMM10=00ff00ff'00ff00ff'00ff00ff'00ff00ff  XMM11=00ff00ff'00ff00ff'00ff00ff'00ff00ff
02:01:20.757 XMM12=00000000'00000000'00000000'00000000  XMM13=ff978591'ff978591'ff978591'ff978591
02:01:20.757 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
02:01:20.757 EFER         =0000000000000d01
02:01:20.757 PAT          =0007010600070106
02:01:20.757 STAR         =0023001000000000
02:01:20.757 CSTAR        =ffffffff815f3860
02:01:20.757 LSTAR        =ffffffff815f2230
02:01:20.757 SFMASK       =0000000000003700
02:01:20.757 KERNELGSBASE =0000000000000000
02:01:20.757 ***
02:01:20.757 Guest paging mode:  AMD64+NX, changed 14538 times, A20 enabled
02:01:20.757 Shadow paging mode: EPT
02:01:20.757 Host paging mode:   AMD64+G+NX
02:01:20.757 ***
02:01:20.757 Active Timers (pVM=0000000002640000)
02:01:20.757 pTimerR3         offNext  offPrev  offSched Clock               Time             Expire HzHint State                     Description
02:01:20.757 00000000080facc0 00017000 00000000 00000000 Real             8248332            8248339      0 2-ACTIVE                  VGA Refresh Timer
02:01:20.757 0000000008111cc0 ffffff80 fffe9000 00000000 Real             8248332            8248351      0 2-ACTIVE                  EMT Yielder
02:01:20.757 0000000008111c40 00000000 00000080 00000000 Real             8248332            8248741      0 2-ACTIVE                  CPU Load Timer
02:01:20.757 000000000810d230 ffffc8c0 00000000 00000000 Virt       7277581408074      7277585439253      0 2-ACTIVE                  Audio timer
02:01:20.757 0000000008109af0 00000000 00003740 00000000 Virt       7277581412205      7279149653560      0 2-ACTIVE                  E1000 Link Up Timer
02:01:20.757 00000000080f2b30 00000670 00000000 00000000 VrSy       7277581415905      7277582608442    434 2-ACTIVE                  i8254 Programmable Interval Timer
02:01:20.757 00000000080f31a0 0001d4b0 fffff990 00000000 VrSy       7277581420521      7277990000000      0 2-ACTIVE                  MC146818 RTC/CMOS - Second
02:01:20.757 0000000008110650 00000000 fffe2b50 00000000 VrSy       7277581424270      8399048221207      0 2-ACTIVE                  ACPI PM Timer
02:01:20.757 ***
02:01:20.757 Shadow GDT (GCAddr=ff596000):
02:01:20.757 ffd8 - 81180087 ff008900 - base=ff008118 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
02:01:20.757 ffe0 - 80900087 ff008900 - base=ff008090 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSS
02:01:20.757 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
02:01:20.757 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
02:01:20.757 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
02:01:20.757 ***
02:01:20.757 ************** End of Guest state at power off ***************
02:01:20.757 Changing the VM state from 'POWERING_OFF' to 'OFF'.
02:01:20.760 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
02:01:20.775 Changing the VM state from 'OFF' to 'DESTROYING'.
02:01:20.775 ************************* Statistics *************************
02:01:20.775 /Devices/E1k0/ReceiveBytes           3546 bytes
02:01:20.775 /Devices/E1k0/TransmitBytes         15030 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit0/AtapiDMA        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/AtapiPIO        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit0/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit0/WrittenBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit1/AtapiDMA        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/AtapiPIO        0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA0/Unit1/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA0/Unit1/WrittenBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit0/AtapiDMA        1 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/AtapiPIO       20 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit0/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit0/WrittenBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit1/AtapiDMA        0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/AtapiPIO        0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/DMA            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/PIO            0 times
02:01:20.775 /Devices/IDE0/ATA1/Unit1/ReadBytes        0 bytes
02:01:20.775 /Devices/IDE0/ATA1/Unit1/WrittenBytes        0 bytes
02:01:20.775 /Devices/PCNet1/ReceiveBytes            0 bytes
02:01:20.775 /Devices/PCNet1/TransmitBytes           0 bytes
02:01:20.775 /Devices/SATA0/Port0/DMA             3900 times
02:01:20.775 /Devices/SATA0/Port0/ReadBytes   149957632 bytes
02:01:20.775 /Devices/SATA0/Port0/WrittenBytes  5723136 bytes
02:01:20.775 /Devices/VMMDev/BalloonChunks           0 count
02:01:20.775 /FT/Checkpoint/Network                  0 times
02:01:20.775 /FT/Checkpoint/Storage                  0 times
02:01:20.775 /FT/Received/Mem                        0 bytes
02:01:20.775 /FT/Received/State                      0 bytes
02:01:20.775 /FT/Sent/Mem                            0 bytes
02:01:20.775 /FT/Sent/State                          0 bytes
02:01:20.775 /FT/Sync/DeltaMem                       0 times
02:01:20.775 /FT/Sync/DeltaVM                        0 times
02:01:20.775 /FT/Sync/Full                           0 times
02:01:20.775 /GVMM/EMTs                              1 calls
02:01:20.775 /GVMM/HostCPUs                          4 calls
02:01:20.775 /GVMM/HostCpus/0                        0 
02:01:20.775 /GVMM/HostCpus/0/CurTimerHz             0 Hz
02:01:20.775 /GVMM/HostCpus/0/DesiredHz              0 Hz
02:01:20.775 /GVMM/HostCpus/0/PPTChanges             0 times
02:01:20.775 /GVMM/HostCpus/0/PPTStarts              0 times
02:01:20.775 /GVMM/HostCpus/0/idxCpuSet              0 
02:01:20.775 /GVMM/HostCpus/1                        1 
02:01:20.775 /GVMM/HostCpus/1/CurTimerHz             0 Hz
02:01:20.775 /GVMM/HostCpus/1/DesiredHz              0 Hz
02:01:20.775 /GVMM/HostCpus/1/PPTChanges             0 times
02:01:20.775 /GVMM/HostCpus/1/PPTStarts              0 times
02:01:20.775 /GVMM/HostCpus/1/idxCpuSet              1 
02:01:20.776 /GVMM/HostCpus/2                        2 
02:01:20.776 /GVMM/HostCpus/2/CurTimerHz             0 Hz
02:01:20.776 /GVMM/HostCpus/2/DesiredHz              0 Hz
02:01:20.776 /GVMM/HostCpus/2/PPTChanges             0 times
02:01:20.776 /GVMM/HostCpus/2/PPTStarts              0 times
02:01:20.776 /GVMM/HostCpus/2/idxCpuSet              2 
02:01:20.776 /GVMM/HostCpus/3                        3 
02:01:20.776 /GVMM/HostCpus/3/CurTimerHz             0 Hz
02:01:20.776 /GVMM/HostCpus/3/DesiredHz              0 Hz
02:01:20.776 /GVMM/HostCpus/3/PPTChanges             0 times
02:01:20.776 /GVMM/HostCpus/3/PPTStarts              0 times
02:01:20.776 /GVMM/HostCpus/3/idxCpuSet              3 
02:01:20.776 /GVMM/Sum/HaltBlocking            3004462 calls
02:01:20.776 /GVMM/Sum/HaltCalls              105815187 calls
02:01:20.776 /GVMM/Sum/HaltNotBlocking        102810725 calls
02:01:20.776 /GVMM/Sum/HaltTimeouts            2703061 calls
02:01:20.776 /GVMM/Sum/HaltWakeUps                   0 calls
02:01:20.776 /GVMM/Sum/PokeCalls                   336 calls
02:01:20.776 /GVMM/Sum/PokeNotBusy                  30 calls
02:01:20.776 /GVMM/Sum/PollCalls                 38597 calls
02:01:20.776 /GVMM/Sum/PollHalts                     0 calls
02:01:20.776 /GVMM/Sum/PollWakeUps                   0 calls
02:01:20.776 /GVMM/Sum/WakeUpCalls              403445 calls
02:01:20.776 /GVMM/Sum/WakeUpNotHalted          224018 calls
02:01:20.776 /GVMM/Sum/WakeUpWakeUps                 0 calls
02:01:20.776 /GVMM/VM/HaltBlocking             3004462 calls
02:01:20.776 /GVMM/VM/HaltCalls               105815187 calls
02:01:20.776 /GVMM/VM/HaltNotBlocking         102810725 calls
02:01:20.776 /GVMM/VM/HaltTimeouts             2703061 calls
02:01:20.776 /GVMM/VM/HaltWakeUps                    0 calls
02:01:20.776 /GVMM/VM/PokeCalls                    336 calls
02:01:20.776 /GVMM/VM/PokeNotBusy                   30 calls
02:01:20.776 /GVMM/VM/PollCalls                  38597 calls
02:01:20.776 /GVMM/VM/PollHalts                      0 calls
02:01:20.776 /GVMM/VM/PollWakeUps                    0 calls
02:01:20.776 /GVMM/VM/WakeUpCalls               403445 calls
02:01:20.776 /GVMM/VM/WakeUpNotHalted           224018 calls
02:01:20.776 /GVMM/VM/WakeUpWakeUps                  0 calls
02:01:20.776 /GVMM/VMs                               1 calls
02:01:20.776 /MM/HyperHeap/cbFree              1049536 bytes
02:01:20.776 /MM/HyperHeap/cbHeap              1310400 bytes
02:01:20.776 /PDM/BlkCache/cbCached            4251648 bytes
02:01:20.776 /PDM/BlkCache/cbCachedFru               0 bytes
02:01:20.776 /PDM/BlkCache/cbCachedMruIn       4251648 bytes
02:01:20.776 /PDM/BlkCache/cbCachedMruOut            0 bytes
02:01:20.776 /PDM/BlkCache/cbMax               5242880 bytes
02:01:20.776 /PDM/CritSects/8237A#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/8237A#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/8237A#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/AHCI#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/AHCI#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/AHCI#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ATA#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ATA#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/ATA#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ATA#1/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ATA#1/ContentionRZLock       10 times
02:01:20.776 /PDM/CritSects/ATA#1/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/AudioSniffer#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/E1000#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/E1000#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/E1000#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/E1000#0RX/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/E1000#0RX/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/E1000#0RX/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/EM-REM/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA0/ContentionRZLock       18 times
02:01:20.776 /PDM/CritSects/EmulatedATA0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA1/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA1/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/EmulatedATA1/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/FTM/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/FTM/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/FTM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/IOM Lock/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/IOM Lock/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/IOM Lock/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/NOP/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/NOP/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/NOP/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PCNet#1/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/PCNet#1/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/PCNet#1/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PDM/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/PDM/ContentionRZLock       45 times
02:01:20.776 /PDM/CritSects/PDM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PGM/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/PGM/ContentionRZLock        7 times
02:01:20.776 /PDM/CritSects/PGM/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/REM-Register/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/VGA#u/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/VGA#u/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/VGA#u/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/VMMDev#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#u/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/VMMDev#u/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/VMMDev#u/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/acpi0/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/acpi0/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/acpi0/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ahci#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ahci#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/ahci#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/e1000#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/e1000#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/e1000#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/i8259#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/i8259#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/i8259#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/ichac97#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/ichac97#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/ichac97#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/mc146818#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/mc146818#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/mc146818#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pcarch#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pcarch#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pcarch#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pcbios#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pcbios#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pcbios#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pci#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pci#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pci#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pckbd#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pckbd#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pckbd#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pcnet#1 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/pcnet#1 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pcnet#1 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/piix3ide#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/piix3ide#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/piix3ide#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/pit/ContentionR3         0 times
02:01:20.776 /PDM/CritSects/pit/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/pit/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/usb-ohci#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/CritSects/vga#0 Auto/ContentionR3        0 times
02:01:20.776 /PDM/CritSects/vga#0 Auto/ContentionRZLock        0 times
02:01:20.776 /PDM/CritSects/vga#0 Auto/ContentionRZUnlock        0 times
02:01:20.776 /PDM/Queue/AHCI-Xmit/AllocFailures        0 times
02:01:20.776 /PDM/Queue/AHCI-Xmit/Flush              0 calls
02:01:20.776 /PDM/Queue/AHCI-Xmit/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/AHCI-Xmit/Insert          4079 calls
02:01:20.776 /PDM/Queue/AHCI-Xmit/cItems            60 count
02:01:20.776 /PDM/Queue/AHCI-Xmit/cbItem            32 bytes
02:01:20.776 /PDM/Queue/DevHlp/AllocFailures         0 times
02:01:20.776 /PDM/Queue/DevHlp/Flush                 0 calls
02:01:20.776 /PDM/Queue/DevHlp/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/DevHlp/Insert                0 calls
02:01:20.776 /PDM/Queue/DevHlp/cItems                8 count
02:01:20.776 /PDM/Queue/DevHlp/cbItem               48 bytes
02:01:20.776 /PDM/Queue/E1000-Rcv/AllocFailures        0 times
02:01:20.776 /PDM/Queue/E1000-Rcv/Flush              0 calls
02:01:20.776 /PDM/Queue/E1000-Rcv/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/E1000-Rcv/Insert            22 calls
02:01:20.776 /PDM/Queue/E1000-Rcv/cItems             1 count
02:01:20.776 /PDM/Queue/E1000-Rcv/cbItem            24 bytes
02:01:20.776 /PDM/Queue/E1000-Xmit/AllocFailures        0 times
02:01:20.776 /PDM/Queue/E1000-Xmit/Flush             0 calls
02:01:20.776 /PDM/Queue/E1000-Xmit/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/E1000-Xmit/Insert           74 calls
02:01:20.776 /PDM/Queue/E1000-Xmit/cItems            1 count
02:01:20.776 /PDM/Queue/E1000-Xmit/cbItem           24 bytes
02:01:20.776 /PDM/Queue/Keyboard/AllocFailures        0 times
02:01:20.776 /PDM/Queue/Keyboard/Flush               0 calls
02:01:20.776 /PDM/Queue/Keyboard/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/Keyboard/Insert              0 calls
02:01:20.776 /PDM/Queue/Keyboard/cItems             64 count
02:01:20.776 /PDM/Queue/Keyboard/cbItem             32 bytes
02:01:20.776 /PDM/Queue/Mouse/AllocFailures          0 times
02:01:20.776 /PDM/Queue/Mouse/Flush                  0 calls
02:01:20.776 /PDM/Queue/Mouse/FlushLeftovers         0 times
02:01:20.776 /PDM/Queue/Mouse/Insert                 0 calls
02:01:20.776 /PDM/Queue/Mouse/cItems               128 count
02:01:20.776 /PDM/Queue/Mouse/cbItem                56 bytes
02:01:20.776 /PDM/Queue/Mouse_1/AllocFailures        0 times
02:01:20.776 /PDM/Queue/Mouse_1/Flush                0 calls
02:01:20.776 /PDM/Queue/Mouse_1/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/Mouse_1/Insert             148 calls
02:01:20.776 /PDM/Queue/Mouse_1/cItems             128 count
02:01:20.776 /PDM/Queue/Mouse_1/cbItem              56 bytes
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/AllocFailures        0 times
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/Flush            0 calls
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/Insert           0 calls
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/cItems           1 count
02:01:20.776 /PDM/Queue/PCNet-Rcv_1/cbItem          24 bytes
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/AllocFailures       36 times
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/Flush           0 calls
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/FlushLeftovers        0 times
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/Insert         93 calls
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/cItems          1 count
02:01:20.776 /PDM/Queue/PCNet-Xmit_1/cbItem         24 bytes
02:01:20.776 /PGM/CPU0/cGuestModeChanges         14538 times
02:01:20.776 /PGM/ChunkR3Map/Mapped                122 count
02:01:20.776 /PGM/ChunkR3Map/Unmapped                0 count
02:01:20.776 /PGM/ChunkR3Map/c                     122 count
02:01:20.776 /PGM/ChunkR3Map/cMax             4294967295 count
02:01:20.776 /PGM/LargePage/Recheck                  0 times
02:01:20.776 /PGM/LargePage/Refused                  2 times
02:01:20.776 /PGM/LargePage/Reused                 321 times
02:01:20.776 /PGM/Page/cAllPages                271559 count
02:01:20.776 /PGM/Page/cBalloonedPages               0 count
02:01:20.776 /PGM/Page/cHandyPages                  88 count
02:01:20.776 /PGM/Page/cLargePages                  31 count
02:01:20.776 /PGM/Page/cLargePagesDisabled           0 count
02:01:20.776 /PGM/Page/cMonitoredPages               0 count
02:01:20.776 /PGM/Page/cPrivatePages             71289 count
02:01:20.776 /PGM/Page/cPureMmioPages               37 count
02:01:20.776 /PGM/Page/cReadLockedPages              0 count
02:01:20.776 /PGM/Page/cReusedSharedPages            0 count
02:01:20.776 /PGM/Page/cSharedPages                  0 count
02:01:20.776 /PGM/Page/cWriteLockedPages             0 count
02:01:20.776 /PGM/Page/cWrittenToPages               0 count
02:01:20.776 /PGM/Page/cZeroPages               200233 count
02:01:20.776 /PGM/cRelocations                       0 times
02:01:20.776 /PROF/CPU0/EM/Capped                    0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/CPU0/EM/ForcedActions      250400514 times
02:01:20.776 /PROF/CPU0/EM/Halted               944948 times
02:01:20.776 /PROF/CPU0/EM/RAWTotal                  0 times
02:01:20.776 /PROF/CPU0/EM/REMTotal                  0 times
02:01:20.776 /PROF/CPU0/EM/Total              18878834523046 ticks/call (18878834523046 ticks,       1 times, max 18878834523046, min 18878834523046)
02:01:20.776 /PROF/VM/CPU0/Halt/Block            52249 ns/call (5528810557523 ticks, 105815183 times, max  15710184, min       1)
02:01:20.776 /PROF/VM/CPU0/Halt/BlockInsomnia        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/VM/CPU0/Halt/BlockOnTime          0 ns/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/VM/CPU0/Halt/BlockOverslept        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
02:01:20.776 /PROF/VM/CPU0/Halt/Timers             925 ns/call (234053189378 ticks, 252839382 times, max   7136870, min       2)
02:01:20.776 /PROF/VM/CPU0/Halt/Yield             4681 ns/call (   180698106 ticks,   38597 times, max   2051907, min    1016)
02:01:20.776 /REM/TbFlushCount                       0 times
02:01:20.776 /REM/TbPhysInvldCount               14129 times
02:01:20.776 /REM/TlbFlushCount                  13922 times
02:01:20.776 /TM/CPU/00/cNsExecuting          54620921986 ns
02:01:20.776 /TM/CPU/00/cNsHalted             5856407961469 ns
02:01:20.776 /TM/CPU/00/cNsOther              1366555213940 ns
02:01:20.776 /TM/CPU/00/cNsTotal              7277584097395 ns
02:01:20.776 /TM/CPU/00/cPeriodsExecuting     13850274 count
02:01:20.776 /TM/CPU/00/cPeriodsHalted          944921 count
02:01:20.776 /TM/CPU/00/pctExecuting                30 %
02:01:20.776 /TM/CPU/00/pctHalted                    0 %
02:01:20.776 /TM/CPU/00/pctOther                    69 %
02:01:20.776 /TM/CPU/pctExecuting                   30 %
02:01:20.776 /TM/CPU/pctHalted                       0 %
02:01:20.776 /TM/CPU/pctOther                       69 %
02:01:20.776 /TM/MaxHzHint                           0 Hz
02:01:20.776 /TM/R0/1nsSteps                     34674 times
02:01:20.776 /TM/R3/1nsSteps                    193724 times
02:01:20.776 /TM/TSC/offCPU0                         0 ticks
02:01:20.776 /TM/VirtualSync/CurrentOffset           0 ns
02:01:20.776 /VUSB/0/cUrbsInPool                     1 count
02:01:20.776 ********************* End of statistics **********************
02:01:20.885 NAT: zone(nm:mbuf, used:1)
02:01:20.885 NAT: zone(nm:mbuf_cluster, used:0)
02:01:20.885 NAT: zone(nm:mbuf_packet, used:0)
02:01:20.885 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
02:01:20.885 NAT: zone(nm:mbuf_jumbo_9k, used:0)
02:01:20.885 NAT: zone(nm:mbuf_jumbo_16k, used:0)
02:01:20.886 NAT: zone(nm:mbuf, used:0)
02:01:20.886 NAT: zone(nm:mbuf_cluster, used:0)
02:01:20.886 NAT: zone(nm:mbuf_packet, used:0)
02:01:20.886 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
02:01:20.886 NAT: zone(nm:mbuf_jumbo_9k, used:0)
02:01:20.886 NAT: zone(nm:mbuf_jumbo_16k, used:0)
02:01:21.062 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
```

OK well your virtualisation is setup in Windows, unless it is a specific Ubuntu related question i cant really help.

If it is Kubuntu related you will need to view its logs to see what is happening or not.

I do see you dont have the extensions pack installed which might be an issue i dont know, either way you should have it installed anyways.

Also the vhd is listed as NTFS, i am not sure if that means it is on a ntfs drive which is correct as you are using windows or it means the vhd itself is using ntfs.

Anyways install the extensions pack and go from there

---

