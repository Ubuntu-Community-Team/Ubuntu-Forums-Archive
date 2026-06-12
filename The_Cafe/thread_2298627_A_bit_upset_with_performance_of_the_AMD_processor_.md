---
title: "A bit upset with performance of the AMD processor I purchased"
date: 2015-10-12
forum: The Cafe
---

### Post by michael-piziak on 2015-10-12
My HP desktop has the Intel® Core&#8482;2 Duo CPU E7400 @ 2.80GHz × 2, and it runs Ubuntu 12.04 LTS great.

I bought an HP Notebook 2000, that is a newer computer by year, that has an AMD 64 bit processor.  I installed 2 system monitor programs on this Xubuntu HP notebook but I couldn't get either to show me the exact processor it has - perhaps someone can suggest a terminal command that will help me share this exact processor.


I was not pleased with the speed of Ubuntu 12.04 LTS on the notebook; furthermore, I now have Xubuntu on it, and while a little faster, still not very satisfying.

---

### Post by v3.xx on 2015-10-12
> can suggest a terminal command that will help me share this exact processor

Install inxi

[http://manpages.ubuntu.com/manpages/trusty/man1/inxi.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/inxi.1.html)

---

### Post by michael-piziak on 2015-10-12
i see inxi in software center

if i install it, do i run it from terminal or is it an executable app

---

### Post by deadflowr on 2015-10-12
```
cat /proc/cpuinfo
```
will show all about the processor.
Look at *model name* for what it is.

---

### Post by QDR06VV9 on 2015-10-12
> **deadflowr said:**
> ```
cat /proc/cpuinfo
```
will show all about the processor.
Look at *model name* for what it is.
+1 
With inxi
```
inxi -C
```
Regards

---

### Post by pqwoerituytrueiwoq on 2015-10-12
What is the video chipset that could be the reason it feels sluggish? sometimes the AMD GPU linux drivers are so bad they make low end Intel GPUs look good
[FONT=courier new]lspci | grep -i vga[/FONT]
CPU model:
[FONT=courier new]cat /proc/cpuinfo |grep -i 'model name'[/FONT]
honestly id would just go for any current/recent intel CPU for a laptop (Sandy Bridge or better)
preferably with 2.0Ghz on the low end with at least 2 cores
i would not want a current AMD CPU in a mobile device, unless it have over 3Ghz (which is just not going to happen)

---

### Post by michael-piziak on 2015-10-12
```
michael@michael-HP-2000-Notebook-PC:~$ 
michael@michael-HP-2000-Notebook-PC:~$ 
michael@michael-HP-2000-Notebook-PC:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 2
model name    : AMD E-300 APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x500010d
cpu MHz        : 1114.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter vmmcall
bugs        : fxsave_leak
bogomips    : 2595.42
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 2
model name    : AMD E-300 APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x500010d
cpu MHz        : 780.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter vmmcall
bugs        : fxsave_leak
bogomips    : 2595.42
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

michael@michael-HP-2000-Notebook-PC:~$
```

---

### Post by MartyBuntu on 2015-10-12
> **michael-piziak said:**
> AMD E-300 APU with Radeon(tm) HD Graphics



It's the most budget of all low budget mobile CPU's.

Assuming you didn't spend too much to begin with, I'm not sure what you were expecting.

---

### Post by michael-piziak on 2015-10-12
Since it is like a 3 year old notebook, I was hoping it would be as fast as an Intel Core 2 Duo Desktop that is twice as old.

Only spent like $165 for it.  It is in great shape and the battery last a very long time.

I only do facebook and email on it, so it is ok.  I guess I just thought it would be as snappy as my HP Desktop Intel box.

---

### Post by QIII on 2015-10-12
> **pqwoerituytrueiwoq said:**
> What is the video chipset that could be the reason it feels sluggish? sometimes the AMD GPU linux drivers are so bad they make low end Intel GPUs look good
[FONT=courier new]lspci | grep -i vga[/FONT]
CPU model:
[FONT=courier new]cat /proc/cpuinfo |grep -i 'model name'[/FONT]
honestly id would just go for any current/recent intel CPU for a laptop (Sandy Bridge or better)
preferably with 2.0Ghz on the low end with at least 2 cores
i would not want a current AMD CPU in a mobile device, unless it have over 3Ghz (which is just not going to happen)

Throwing money at the problem is not the first thing I would suggest we advise, since we don't want to spend the OP's money.  Also, this is a mobile device, which means that the motherboard and CPU are likely fixed.  Thus the change would have to be accomplished by buying a new machine.  Let's try to work with what the OP already has.

@michael-piziak:  As stated, the AMD E-series APUs are very, very low power (and therefore cost) units.  I am not at all surprised that it performs more slowly than the Core 2 Duo.  But there is something that might improve performance.  Although APUs (that is a CPU and GPU on the same die) are designed to tolerate running at higher temperatures than CPUs, even with low power consumption you can still get them very hot when both the CPU and GPU are being exercised.  That means throttling is always a possibility.

The open source Radeon driver is not as good at power management as the proprietary AMD driver, which would reduce overall heat and might help improve performance under load.

It might be worth your while to see if you can get better performance by installing the proprietary fglrx driver (see section 3.1 in the ATI driver wiki in my signature.)  You can certainly install the driver from the Additional Drivers GUI (just remember to initialize the driver before you reboot!), but I prefer to recommend the terminal method because it produces messages that you can easily cut and paste back here.  If you run into problems with that, we can help you uninstall it and get back to where you are now.

---

### Post by michael-piziak on 2015-10-12
I see the fglrx driver in your signature.
Should I do the 9 steps in 3.1 to try this?

Michael

thanks so much in advance!

---

### Post by QIII on 2015-10-12
Yes.  I won't guarantee it will make a '68 Beetle into a fighter jet, but you may get some improvement.

---

### Post by michael-piziak on 2015-10-12
Thanks, I will try it later when I'm downstairs on the laptop.

---

### Post by CharlesA on 2015-10-12
Good luck.

I doubt you'll see much of a difference since the AMD CPU is 1.3GHz and the Intel one is 2.8Ghz, which is over twice as fast as the AMD one.

---

### Post by mastablasta on 2015-10-13
> **michael-piziak said:**
> Since it is like a 3 year old notebook, I was hoping it would be as fast as an Intel Core 2 Duo Desktop that is twice as old.

Only spent like $165 for it.  It is in great shape and the battery last a very long time.

I only do facebook and email on it, so it is ok.  I guess I just thought it would be as snappy as my HP Desktop Intel box.

it doesn't work that way. as you've found out. too bad you didn't ask for advice (here) before buying it. my colleague is selling a first gen i5 for 140 EUR. now that one would compare to some Core 2 duo. AMD E 300 and E350 were a bit problematic in terms of overheating. they play video nicely but are not really good at gaming. E-450 improved that a bit. why these CPU's are good is their power consumption. it is very low even under full load. but on the other hand e-450 has power comparable to old 2003 single core AMD Athlon 64 3200. similar story with Atom CPU's. they consume very little power but are not as strong. in short age won't give you much information.

E (from AMD) and Atom (Intel) series are therefore used in Tablets, Subnotebooks, Netbooks and similar cheap devices.  They are also often used in home cinema or small NAS servers - as they use little power they can be on constantly.

To get a major improvement over your old PC you would need to look for  a 2nd gen Intel Core i or  AMD A6 (better with A8).

it is remarkable how many of new GPU cards and CPU's are actually better but not that much from the 10 year old components. so you would have brand new low end card that are still weaker or similar to my 10 year old GPU - they have more RAM, are more power efficient but are not that much stronger or deliver 2x the performance you would expect.

Major advantage of newer CPUs is mostly multiple cores. problem is many applications still work on single core.

---

### Post by night_sky2 on 2015-10-13
I bought a Asus budget laptop in 2012 with  [_AMD Radeon HD 6250 Graphics _and_ AMD C-50 Processor 1.00 GHz (4GB RAM DDR3)_] and this was the worst computer I ever had, really.

Video playback was choppy, the computer was *slow *both on Windows and Linux (including Lubuntu 32 bit!) even with latest proprietary graphic driver.

My [ _Intel Pentium 4 - 2.80GhZ _and_ NVidia GeForce 8400 GS Rev 2 (2GB RAM DDR1)_] desktop computer which is 6 years older is *much* better than that. Go figure.

Fortunately for me, I was able to sell that laptop for 100 bucks but since then I am avoiding budget AMD hardware. I will stick with Intel instead.

---

### Post by mastablasta on 2015-10-13
oh the C series.... I was looking at those as well in 2012. here again the C50 is bad, but C60 was reasonably OK. nothing fancy though. I checked the reviews at the time. but still in the end I decided to go with E-450, which wasn't a bad choice. it still has enough power for some older games and works well for webwork and office progs.

C series had an even smaller energy footprint than E series (TDP is twice as low at 9W). again it depends what the CPU is used for and how. but both are nothing special as people find out. but oyu could add 14" monitor to C notebook and 3cell battery and it would probably last for quite a while :)

like I said I would now avoid anything below A6 and most E's from what I read. Well unless I was using it for home theatre. but then again Rpi is cheaper for that. maybe C series and E's would be good for home made NAS. still they have their limits.

I think C's and E's were aimed to compete with Atoms and Atom Z (?) at the time. And E450 for example did have slightly lower PCU power but a lot better graphics compared to slightly more expencive Atom at the time. i know this because I must have used a couple of days of my vacation in SE Asia trying to figure out what to get.

---

### Post by kurt18947 on 2015-10-13
A family friend has a Toshiba laptop with (I think) an E1 something running Win8. I can confirm that it's .... leisurely;-). Wife has a desktop with AMD A6, 4 GB. RAM using an Nvidia PCIe graphics card. It performs quite nicely for the tasks she uses it for - nothing too demanding. We were able to get a Asrock MoBo, A6 processor and 4 GB. DDR3 RAM for <$150 U.S. We reused other components. Another friend has an HP D5 with an AMD processor running Windows 7. The hardware seemed fine but I was having to reinstall Windows far more often than I cared for so the last time made it dual boot with Xubuntu 14.04 and suggested that when Windows takes a dump next, try booting into the other thing. I haven't heard anything since. He was actually a prime candidate for a tablet; just used his device for web surfing, no office stuff, no printing.

---

### Post by night_sky2 on 2015-10-13
> **mastablasta said:**
> oh the C series.... I was looking at those as well in 2012. here again the C50 is bad, but C60 was reasonably OK. nothing fancy though. I checked the reviews at the time. but still in the end I decided to go with E-450, which wasn't a bad choice. it still has enough power for some older games and works well for webwork and office progs.

C series had an even smaller energy footprint than E series (TDP is twice as low at 9W). again it depends what the CPU is used for and how. but both are nothing special as people find out. but oyu could add 14" monitor to C notebook and 3cell battery and it would probably last for quite a while :)

like I said I would now avoid anything below A6 and most E's from what I read. Well unless I was using it for home theatre. but then again Rpi is cheaper for that. maybe C series and E's would be good for home made NAS. still they have their limits.

I think C's and E's were aimed to compete with Atoms and Atom Z (?) at the time. And E450 for example did have slightly lower PCU power but a lot better graphics compared to slightly more expencive Atom at the time. i know this because I must have used a couple of days of my vacation in SE Asia trying to figure out what to get.
Somehow I think Intel's low-end processors are *much* better than AMD's. Those Dual-Core Celerons with the haswell technology and intergrated Intel HD graphics makes for some speedy little notebooks. That's what powering most of the Chromebooks and Microsoft's latest HP Streams.

---

### Post by pqwoerituytrueiwoq on 2015-10-13
> **QIII said:**
> Throwing money at the problem is not the first thing I would suggest we advise, since we don't want to spend the OP's money.  Also, this is a mobile device, which means that the motherboard and CPU are likely fixed.  Thus the change would have to be accomplished by buying a new machine.  Let's try to work with what the OP already has.
most retailer accept returns within 30 days and OP said it was new...

i try switching to lubuntu or you know it lets just use puppy linux on it and be done with it, it is gonna suck no matter what (1.3Ghz of anything is going to suck)
given what OP spent i would have suggested a ~2Ghz chromebook (celeron CPU)
> **CharlesA said:**
> I doubt you'll see much of a difference since the AMD CPU is 1.3GHz and  the Intel one is 2.8Ghz, which is over twice as fast as the AMD  one.
you cant compare CPUs by the clock seed unless they are the same architecture
[https://en.wikipedia.org/wiki/Megahertz_myth](https://en.wikipedia.org/wiki/Megahertz_myth)

---

### Post by CharlesA on 2015-10-13
> **pqwoerituytrueiwoq said:**
> 
you cant compare CPUs by the clock seed unless they are the same architecture
[https://en.wikipedia.org/wiki/Megahertz_myth](https://en.wikipedia.org/wiki/Megahertz_myth)

Wouldn't the desktop CPU win out over the laptop one even at the same clock speed?

---

### Post by pqwoerituytrueiwoq on 2015-10-13
> **CharlesA said:**
> Wouldn't the desktop CPU win out over the laptop one even at the same clock speed?
i don't know, but i don't want op thinking you can compare cpus like that

---

### Post by v3.xx on 2015-10-13
What about number of threads per core?  Or is that just an intel thing?

---

### Post by pqwoerituytrueiwoq on 2015-10-13
amd's 8 coeres like intel's i7s only have 4 true cores
*i don't have a sources it is just what i have read on other forums

---

### Post by michael-piziak on 2015-10-13
In step 8, I think it is not correct, there is an errorr in what i got.  see below

michael@michael-HP-2000-Notebook-PC:~$ fglrxinfo
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  17
  Current serial number in output stream:  18
michael@michael-HP-2000-Notebook-PC:~$

---

### Post by michael-piziak on 2015-10-13
another question:  can i go through all the steps in 3.1 again to try to get it to work?

---

### Post by michael-piziak on 2015-10-13
if i had to do over, i would have got the same   2000 with the intel core 2 processor - it's available in that too

i did not know amd was at a disadvantage on Linux systems

---

### Post by QDR06VV9 on 2015-10-13
The AMD FX-8350 has 4 modules with 2 cores in each module. Each 2 cores in the module will share resources. Yes, there are 8 cores in total, but they are not separate, and are not hyper-threading. This is a good cost saver for AMD.
Intel quad-core CPUs will have 4 modules with a core in each module.


Good read: [http://www.reddit.com/r/buildapc/comments/1e8226/discus](http://www.reddit.com/r/buildapc/comments/1e8226/discus)...


The problem with the FX CPUs is that it is a modular design. Every two physical CPUs shares a single FPU (Floating Point Unit). If both CPUs must use the FPU in each module, then one core basically needs to wait and do nothing until the other core is done using the FPU. Therefore, the FPU itself is a performance bottleneck.

---

### Post by kurt18947 on 2015-10-13
> **pqwoerituytrueiwoq said:**
> most retailer accept returns within 30 days and OP said it was new...



I think here in Yankeestan we generally get two weeks to return electronic doodads like PCs, phones, cameras and such. 30 days on things that people are less likely to buy with no intention of actually keeping them.

---

### Post by QIII on 2015-10-13
Would you please post the results of 

```
glxinfo
```

---

### Post by michael-piziak on 2015-10-13
I wasn't comparing it to an Intel quad-core, I was comparing it to the Intel Core-2 duo.

But thanks for your reply

---

### Post by michael-piziak on 2015-10-13
> **QIII said:**
> Would you please post the results of 

```
glxinfo
```

michael@michael-HP-2000-Notebook-PC:~$ glxinfo
The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils
michael@michael-HP-2000-Notebook-PC:~$ 



I typed this into terminal, is that correct?
 sudo apt-get install mesa-utils   ?

---

### Post by QIII on 2015-10-13
Yes, and then post the results of glxinfo.

---

### Post by michael-piziak on 2015-10-13
> **QIII said:**
> Yes, and then post the results of glxinfo.

```

michael@michael-HP-2000-Notebook-PC:~$ glxinfo
The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils
michael@michael-HP-2000-Notebook-PC:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_AMD_gpu_association, GLX_ARB_context_flush_control, 
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_allocate_memory, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_NV_swap_group, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_context_flush_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_get_proc_address, 
    GLX_ARB_multisample, GLX_EXT_buffer_age, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_swap_control, GLX_NV_swap_group, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6310 Graphics
OpenGL core profile version string: 4.3.13374 Core Profile Context 15.20.1013
OpenGL core profile shading language version string: 4.40
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMDX_debug_output, GL_AMDX_vertex_shader_tessellator, 
    GL_AMD_conservative_depth, GL_AMD_debug_output, 
    GL_AMD_depth_clamp_separate, GL_AMD_draw_buffers_blend, 
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_AMD_performance_monitor, GL_AMD_pinned_memory, 
    GL_AMD_query_buffer_object, GL_AMD_sample_positions, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trace, GL_AMD_texture_cube_map_array, 
    GL_AMD_texture_texture4, GL_AMD_transform_feedback3_lines_triangles, 
    GL_AMD_vertex_shader_layer, GL_AMD_vertex_shader_tessellator, 
    GL_AMD_vertex_shader_viewport_index, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_arrays_of_arrays, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, GL_ARB_clip_control, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_compute_shader, GL_ARB_conditional_render_inverted, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_cull_distance, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_derivative_control, 
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_no_attachments, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, 
    GL_ARB_get_texture_sub_image, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_internalformat_query2, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pipeline_statistics_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_query_buffer_object, GL_ARB_robust_buffer_access_behavior, 
    GL_ARB_sample_shading, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_image_size, 
    GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_stencil_export, GL_ARB_shader_storage_buffer_object, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_image_samples, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_packing, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_stencil_texturing, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_barrier, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_buffer_range, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_snorm, GL_ARB_texture_stencil8, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transform_feedback_overflow_query, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_viewport_array, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_meminfo, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset_clamp, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shader_integer_mix, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_bptc, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_IBM_texture_mirrored_repeat, 
    GL_KHR_context_flush_control, GL_KHR_debug, 
    GL_KHR_robust_buffer_access_behavior, GL_KHR_robustness, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_explicit_multisample, GL_NV_float_buffer, GL_NV_half_float, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_SUN_multi_draw_arrays, GL_WIN_swap_hint

OpenGL version string: 4.4.13374 Compatibility Profile Context 15.20.1013
OpenGL shading language version string: 4.40
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
    GL_AMDX_debug_output, GL_AMDX_vertex_shader_tessellator, 
    GL_AMD_conservative_depth, GL_AMD_debug_output, 
    GL_AMD_depth_clamp_separate, GL_AMD_draw_buffers_blend, 
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_AMD_performance_monitor, GL_AMD_pinned_memory, 
    GL_AMD_query_buffer_object, GL_AMD_sample_positions, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trace, GL_AMD_texture_cube_map_array, 
    GL_AMD_texture_texture4, GL_AMD_transform_feedback3_lines_triangles, 
    GL_AMD_vertex_shader_layer, GL_AMD_vertex_shader_tessellator, 
    GL_AMD_vertex_shader_viewport_index, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_arrays_of_arrays, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, GL_ARB_clip_control, 
    GL_ARB_color_buffer_float, GL_ARB_compatibility, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_compute_shader, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_copy_image, GL_ARB_cull_distance, 
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_derivative_control, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_no_attachments, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, 
    GL_ARB_get_texture_sub_image, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_internalformat_query2, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pipeline_statistics_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_query_buffer_object, GL_ARB_robust_buffer_access_behavior, 
    GL_ARB_sample_shading, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_image_size, 
    GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_stencil_export, GL_ARB_shader_storage_buffer_object, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_image_samples, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_packing, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_stencil_texturing, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_barrier, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_buffer_range, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_snorm, GL_ARB_texture_stencil8, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transform_feedback_overflow_query, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_viewport_array, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_meminfo, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset_clamp, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shader_integer_mix, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_bptc, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_IBM_texture_mirrored_repeat, 
    GL_KHR_context_flush_control, GL_KHR_debug, 
    GL_KHR_robust_buffer_access_behavior, GL_KHR_robustness, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_explicit_multisample, GL_NV_float_buffer, GL_NV_half_float, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_SUN_multi_draw_arrays, GL_WIN_swap_hint

33 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x040 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x041 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x042 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x043 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x044 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x045 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x046 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x047 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x048 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x049 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x04a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x08f 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon

43 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x040 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x041 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x042 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x043 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x044 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x045 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x046 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x047 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x048 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x049 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x04a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x08f 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon
0x08f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 Ncon
0x08f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x08f 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x08f 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 Ncon
0x08f  0 tc  0 128  0    y .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x08f  0 tc  0 128  0    . .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x08f  0 tc  0  64  0    y .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x08f  0 tc  0  64  0    . .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x08f  0 tc  0  32  0    y .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08f  0 tc  0  32  0    . .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None

michael@michael-HP-2000-Notebook-PC:~$
```

---

### Post by QIII on 2015-10-13
IF the machine is currently operating, hold what you got.  I'm going to have to do some research.

---

### Post by pqwoerituytrueiwoq on 2015-10-14
> **michael-piziak said:**
> i did not know amd was at a disadvantage on Linux systems
only on the GPU side, CPU wise it is just as bad as windows
sadly AMD's CPU performance has made little progress, to the point they have a hard time competing with a i3
unless you are doing something like budget (~130 vs ~300 for the cpu) video rendering (heavily multi threaded process) it is normally better to go with a Intel cpu
the only reason (well it was also on sale) i upgraded from my phenom II 965 @ 3.7Ghz (still a good CPU IMO) to my current i5-4690k was i knew if i waited for better i would have to replace my ram (and DDR4 did not impress me) with would cost more than ddr3

---

### Post by michael-piziak on 2015-10-14
> **QIII said:**
> IF the machine is currently operating, hold what you got.  I'm going to have to do some research.

ok, I am holding

take your time

---

### Post by d-cosner on 2015-10-15
I have a pretty low end laptop that I picked up real cheap from a pawn shop when it was only a few months old. It's an HP 655 with an AMD E1 processor that runs at 1.4 GHz and also has the on chip graphics. I mention this because I also was not happy with performance and this processor is similar to the original posters.

I currently have Windows 10 installed on the laptop for classes I am wanting to take but I did have Ubuntu 14.04 installed previously. Any OS is going to seem slow on this hardware unfortunately but I was able to get Ubuntu running pretty nice despite the low end processor.

First I installed the latest 3.19 kernel, then installed the proprietary drivers.This combination gave me the best performance as far as the OS itself. Firefox was the biggest problem after that, it was slow and sluggish. Installing AdGuard in Firefox greatly improved things. It's reasonably light and without all the ads scrolling pages worked much better. I did use the swappiness tweak and set the value to 10, it does provide a slight improvement.

I tried lighter desktop environments but honestly they all ran about the same as far as performance. Sure I could get slightly better memory use but that really was not the problem. The problem was the processor and graphics. For some reason Ubuntu 14.04 using compiz actually made the laptop seem faster using the 3.19 kernel and the proprietary drivers. Google Chrome ran slightly better than Firefox after turning off hardware acceleration. You really need to turn it off in Firefox too and in flash itself.

After doing the things I mentioned the laptop is about as quick as my desktop with a Core 2 Duo. Sadly these processors were designed more for battery life than performance.

Edit: You do have to run the sytem for a while before it speeds up. Ubuntu uses something similar to prefetch and after some use and a few reboots it will run a little faster.

---

### Post by QIII on 2015-10-15
While I was hoping to provide better news to the. OP, what I have found thus far also points to using a newer kernel.  However, it does not work universally.  Also, the use of the fglrx driver is not always successful at improving performance.

@michael-piziak:  it might be worthwhile to uninstall and reinstall the driver to see if something went wrong.  But at this point, I'm afraid, I'm not very hopeful.

---

### Post by pqwoerituytrueiwoq on 2015-10-15
well if you want a new kernel, this will make that easy
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by night_sky2 on 2015-10-15
> **d-cosner said:**
> First I installed the latest 3.19 kernel, then installed the proprietary drivers.This combination gave me the best performance as far as the OS itself. Firefox was the biggest problem after that, it was slow and sluggish. Installing AdGuard in Firefox greatly improved things. It's reasonably light and without all the ads scrolling pages worked much better. I did use the swappiness tweak and set the value to 10, it does provide a slight improvement.
Try BluHell Firewall on Firefox, it is *much* lighter than AdGuard.

[https://addons.mozilla.org/en-US/firefox/addon/bluhell-firewall/](https://addons.mozilla.org/en-US/firefox/addon/bluhell-firewall/)

I used to have a full blown Adblock Plus installed on Firefox but since I discovered this addon 2 years ago, the browser has been flying again.

---

### Post by pqwoerituytrueiwoq on 2015-10-17
in addition to what night_sky2 mentioned i use keep a launcher on my panel for terminating flash content (which frees up precious system resources that flash likes to consume)
i have the launcher run this command: [FONT=courier new]pkill -f flashplayer[/FONT]
really convenient when flash locks firefox up
sadly i have not found a way to keep that command from killing chromium also

---

