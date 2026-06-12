---
title: "World of Warcraft graphic issues"
date: 2009-05-30
forum: Wine
---

### Post by deboare on 2009-05-30
Hi
I'm not a long time Ubuntu user, so I don't really know much about running windows applications under wine. However, I've tried to run WoW from a guide on WoWwiki here: [http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)
This worked fine, except for my framerate (FPS) is 20 or sometimes lower. Because this very much sucks I searched a bit further and came across this guide: [http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)
This guide had me change a registry value and put some values in the config.wtf file in the WoW folder (including changing the rendering from directx to opengl). After I did that I started up WoW and I got a black screen where the opening should normally be, I could still enter my info though (I can post screens if required). After I logged in I could only see the terrain, not my character or any other NPCs, mobs, etc.
The good thing though, was that my FPS went from 20 to 110. I would like to keep that FPS, and keep my character :)

Any suggestions or help will be very well appreciated
I will leave a snippet of my terminal when running WoW under opengl here:

brecht@brecht-ubuntu:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
fixme:powrprof:DllMain (0x7c3a0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c3a0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3554
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x37404324) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0xe0032, 0x139cb0): stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x32d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0xe0032, (nil), 16): stub


NOTE: the shadows still work in opengl mode, don't ask me why.

---

### Post by deboare on 2009-05-30
Maybe it will help too if I include the output of my glxinfo, here it is:
brecht@brecht-ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.8087 Release
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

It's not the full output but, after this it's just all numbers coming.

---

### Post by deboare on 2009-05-30
bump

---

### Post by deboare on 2009-05-30
I have fixed the model issue by using this line of code:
SET M2UseShaders "0"

put it in the config.wtf file
Source is: [http://www.wowwiki.com/Wine_troubleshooting](http://www.wowwiki.com/Wine_troubleshooting)

However, I'm now experiencing some heavy FPS "trouble". When I am in a building my FPS goes from 100 to 150. When I go outside it's mostly around 45. As you can see my FPS varies a lot, I'd like to know if there's anything I can do about it.

Thanks

---

### Post by nolliecrooked on 2009-05-31
whats your graphics card/chip?
 
EDIT; actually nevermind I just read your Terminal output, you have an ATi x1950, which basically means you gonna have to hack like a bitch to get everything working properly. 
 
if you have ATi graphics, stick with Windows, however much you may hate it, it isnt as bad as having to suffer ATi crappy Linux drivers.

---

### Post by Hairy_Palms on 2009-05-31
to stop the jumpy FPS i remember someone who had to tick Vertical Sync and Triple Buffering in the ingame Video Options

---

### Post by deboare on 2009-05-31
> **Hairy_Palms said:**
> to stop the jumpy FPS i remember someone who had to tick Vertical Sync and Triple Buffering in the ingame Video Options

Vsync doesn't seem to change anything to my FPS and when I run OpenGL I don't have Triple Buffering, it's gone. Don't ask me why :)

---

### Post by Hairy_Palms on 2009-05-31
:confused::confused::confused: i run with opengl and if i triple buffering can be activated here, the only thing that cant is the shadow quality, you know triple buffering is grey till vsync is enabled right?

---

### Post by deboare on 2009-06-01
> **Hairy_Palms said:**
> :confused::confused::confused: i run with opengl and if i triple buffering can be activated here, the only thing that cant is the shadow quality, you know triple buffering is grey till vsync is enabled right?

I run in OpenGL too and even if I enable VSync, there is no trible buffering option beneath it. In Direct3D however, there is, but that means playing with 5 FPS again :)

---

### Post by deboare on 2009-06-05
bump, I need some help with this. I'd also like to note that my FPS drops mostly outside (probably when more objects need to be loaded), and inside a building it's around 100 or more.

---

### Post by deboare on 2009-06-08
Does anyone know what I can do to resolve this?
I've tried just about every FPS boost I can find googling:

RegEdit change with the DisabledExtensions key
Console input like: /console maxfpsbk 3
Running WoW in a separate X server just leaves the mouse cursor with an X and nothing happens.

My graphics card is ATI Radeon x1950 Pro.

deboare

---

### Post by ajackson on 2009-06-08
> **deboare said:**
> Does anyone know what I can do to resolve this?

Well what problem are you having, you've said

> When I am in a building my FPS goes from 100 to 150. When I go outside it's mostly around 45.
45 FPS is perfectly fine, it will be higher in enclosed spaces as there is less graphical processing to do.

---

### Post by deboare on 2009-06-10
> **ajackson said:**
> Well what problem are you having, you've said


45 FPS is perfectly fine, it will be higher in enclosed spaces as there is less graphical processing to do.

My mouse seems sloppy though sometimes :/ This must be the hardware cursor then... So I just leave the FPS jumps?

---

