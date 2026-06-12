---
title: "Unigine Heaven Benchmark thread"
date: 2011-07-18
forum: The Cafe
---

### Post by inobe on 2011-07-18
[http://unigine.com/](http://unigine.com/)

my tested system.





```
xxxxx@linux-beast:~$ cd ~/Downloads/Unigine_Heaven-2.5
xxxxx@linux-beast:~/Downloads/Unigine_Heaven-2.5$ sh x64_1920x1080_fullscreen_tess_normal.sh
Loading "/home/xxxxx/Downloads/Unigine_Heaven-2.5/bin/../data/heaven_2.5.cfg"...
Loading "libGL.so.1"...
Loading "libopenal.so.1"...
Set 1920x1080 fullscreen video mode
Set 1.00 gamma value
Unigine engine http://unigine.com/
Binary: Linux 64bit GCC 4.4.5 Release Mar  1 2011
App path:  /home/xxxxx/Downloads/Unigine_Heaven-2.5/bin/
Data path: /home/xxxxx/Downloads/Unigine_Heaven-2.5/data/
Save path: /home/xxxxx/Downloads/Unigine_Heaven-2.5/bin/

---- System ----
System: Linux 2.6.38-10-generic x86_64
CPU: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz 2999MHz MMX SSE SSE2 SSE3 SSSE3 HTT
GPU: GeForce GTX 460 PCI Express 270.41.06
System memory: 5912 Mb
Video memory:  2048 Mb

---- MathLib ----
Set SSE simd processor

---- Sound ----
Renderer: PulseAudio Software
OpenAL vendor:   OpenAL Community
OpenAL renderer: OpenAL Soft
OpenAL version:  1.1 ALSOFT 1.12.854
Found AL_EXT_LINEAR_DISTANCE
Found AL_EXT_OFFSET
Found ALC_EXT_EFX
Found EFX Filter
Found EFX Reverb
Found EAX Reverb
Found QUAD16 format
Found 51CHN16 format
Found 61CHN16 format
Found 71CHN16 format
Maximum sources:         256
Maximum effect slots:    4
Maximum auxiliary sends: 2

---- Render ----
Renderer: NVIDIA NV60 2048Mb
OpenGL vendor:   NVIDIA Corporation
OpenGL renderer: GeForce GTX 460/PCI/SSE2
OpenGL version:  4.1.0 NVIDIA 270.41.06
Found required GL_ARB_map_buffer_range
Found required GL_ARB_vertex_array_object
Found required GL_ARB_vertex_buffer_object
Found required GL_ARB_half_float_vertex
Found required GL_ARB_half_float_pixel
Found required GL_ARB_occlusion_query
Found required GL_EXT_texture3D
Found required GL_EXT_texture_cube_map
Found required GL_EXT_texture_sRGB
Found required GL_EXT_texture_swizzle
Found required GL_ARB_shader_object
Found required GL_ARB_vertex_shader
Found required GL_ARB_fragment_shader
Found required GL_ARB_draw_buffers
Found required GL_ARB_framebuffer_object
Found required GL_EXT_framebuffer_blit
Found required GL_EXT_framebuffer_multisample
Found optional GL_ARB_draw_instanced
Found optional GL_ARB_transform_feedback
Found optional GL_ARB_draw_elements_base_vertex
Found optional GL_EXT_draw_buffers2
Found optional GL_ARB_blend_func_extended
Found optional GL_ARB_uniform_buffer_object
Found optional GL_ARB_tessellation_shader
Found optional GL_ARB_geometry_shader4
Found optional GL_ARB_sample_shading
Found optional GL_ARB_gpu_shader4
Found optional GL_ARB_gpu_shader5
Found optional GL_EXT_Cg_shader
Found optional GL_ARB_texture_rg
Found optional GL_ARB_texture_array
Found optional GL_ARB_texture_snorm
Found optional GL_ARB_texture_multisample
Found optional GL_ARB_texture_compression
Found optional GL_ARB_texture_compression_rgtc
Found optional GL_ARB_seamless_cube_map
Found optional RGB10A2 render texture format
Shading language:      4.10 NVIDIA via Cg compiler
Maximum texture size:  16384
Maximum texture units: 160
Maximum draw buffers:  8

---- Physics ----
Physics: Multi-threaded

---- PathFind ----
PathFind: Multi-threaded

Unigine~# gl_render_use_arb_tessellation_shader 1 && render_restart
---- Interpreter ----
Version: 2.39

Loading "heaven/unigine.cpp" 112ms
Loading "demos/heaven/locale/unigine.en" dictionary
Loading "core/materials/unigine_post.mat" 11 materials 11 shaders 5ms
Loading "core/materials/unigine_render.mat" 38 materials 306 shaders 3ms
Loading "core/materials/unigine_meshes.mat" 17 materials 10924 shaders 55ms
Loading "core/materials/unigine_terrains.mat" 1 material 144 shaders 0ms
Loading "core/materials/unigine_grass.mat" 1 material 69 shaders 2ms
Loading "core/materials/unigine_particles.mat" 1 material 45 shaders 1ms
Loading "core/materials/unigine_billboards.mat" 1 material 51 shaders 0ms
Loading "core/materials/unigine_volumes.mat" 6 materials 45 shaders 4ms
Loading "core/materials/unigine_guis.mat" 1 material 82 shaders 0ms
Loading "core/materials/unigine_water.mat" 1 material 101 shaders 30ms
Loading "core/materials/unigine_skies.mat" 1 material 13 shaders 24ms
Loading "core/materials/unigine_decals.mat" 1 material 55 shaders 0ms
Loading "core/properties/unigine.prop" 2 properties 0ms
Unigine~# world_load heaven
Loading "heaven.cpp" 219ms
Loading "demos/heaven/materials/heaven_base.mat" 7 materials 1ms
Loading "demos/heaven/materials/heaven_environment.mat" 12 materials 1553ms
Loading "demos/heaven/materials/heaven_ruins.mat" 27 materials 4030ms
Loading "demos/heaven/materials/heaven_buildings.mat" 51 materials 4082ms
Loading "demos/heaven/materials/heaven_props.mat" 10 materials 791ms
Loading "demos/heaven/materials/heaven_sfx.mat" 11 materials 23ms
Loading "demos/heaven/materials/heaven_fort.mat" 15 materials 1088ms
Loading "demos/heaven/materials/heaven_airship.mat" 26 materials 6197ms
Object::loadWorld(): different surface names "mill_wings" "mill_wings_1"
Loading "heaven.world" 28838ms
Unigine~# render_hdr 2 && render_restart
Unigine~# render_restart
Benchmark running
Unigine~# render_dof 2 && render_restart
Unigine~# render_dof 0 && render_restart
Unigine~# render_dof 2 && render_restart
Unigine~# render_dof 0 && render_restart
Unigine~# render_dof 2 && render_restart
Unigine~# render_dof 0 && render_restart
Unigine~# render_restart
Benchmark finished
Time:   259.753
Frames: 7275
FPS:    28.0074
Min FPS:        9.93427
Max FPS:        57.3318
Scores: 705.505
Unigine~# quit
Close "libopenal.so.1"
Close "libGL.so.1"
Memory usage: 72b
Allocations:  2
Shutdown

```

enjoy folks:D

edit, had wrong image and edited out my name :P

---

### Post by Snowboi on 2011-07-18
Id join but i manage to average 1 fps. :KS

---

### Post by 3Miro on 2011-07-18
Here is what I have. I don't have a large enough monitor so I can only run the windowed mode.

---

### Post by inobe on 2011-07-18
kick *** phenom, looks great:)


my results are mainly gpu, the cpu can be oc'ed, it's all stock at the moment.

---

### Post by 3Miro on 2011-07-18
> **inobe said:**
> kick *** phenom, looks great:)


my results are mainly gpu, the cpu can be oc'ed, it's all stock at the moment.

6 cores, well worth the $250 I gave for it.

Your GPU should be better though and it seems you have support for things I don't (or maybe I have an older version of the benchmark.

One thing that isn't listed is the memory. I have DDR3 1333 8GB. I expect this would give significant difference compared to DDR2.  What do you have?

---

### Post by inobe on 2011-07-18
> **3Miro said:**
> 6 cores, well worth the $250 I gave for it.

Your GPU should be better though and it seems you have support for things I don't (or maybe I have an older version of the benchmark.

One thing that isn't listed is the memory. I have DDR3 1333 8GB. I expect this would give significant difference compared to DDR2.  What do you have?

6 gig ddr2 800, the difference is huge :)

---

### Post by 3Miro on 2011-07-18
Another thing to consider is whether or not you have compiz and/or unity running. I am using xfwm4, which is pretty light. You should get better results if you disable the desktop effects.

---

### Post by inobe on 2011-07-18
check back later, i will do that and use the same res you've used in window mode:)

---

### Post by Lucradia on 2011-07-18
[Here are mine](http://i.imgur.com/Zzaeh.png) on Windows.

A note, my CPU's cooling is just a tiny 80mm fan, it cannot perform well with this stock cooler. At stage 12, the CPU fan went over 4500 RPM, and the nvidia fan went overlimit.

---

### Post by inobe on 2011-07-18
okay heres an interesting comparison 3Miro, using the same resolution.

that's about right considering the differences in memory and cpu cores:)

---

### Post by 3Miro on 2011-07-19
> **inobe said:**
> okay heres an interesting comparison 3Miro, using the same resolution.

that's about right considering the differences in memory and cpu cores:)

Yes, this is more reasonable. Phenom X6 is better than Core 2 Duo, but on a single threaded app, the difference shouldn't be that much. You basically get extra cache and the AMD Turbo mode.

I think the main difference is the DDR3 vs DDR2, especially since you should get the advantage of the better GPU.

---

### Post by 3Miro on 2011-07-19
> **Lucradia said:**
> [Here are mine](http://i.imgur.com/Zzaeh.png) on Windows.

A note, my CPU's cooling is just a tiny 80mm fan, it cannot perform well with this stock cooler. At stage 12, the CPU fan went over 4500 RPM, and the nvidia fan went overlimit.

You can try smaller resolution and windowed mode, but something isn't right here. With your hardware, you should be getting much better results. I am using stock cooling on my Phenom and I have no issues with the heat (idle 25C full load on the six cores goes to the low 50s).

---

### Post by 3Miro on 2011-07-19
Here is my work computer. Phenom II X4, Nvidia GTX250 and 4GB DDR2 (800).

Lucradia: I got absolutely no heat issues with the benchmark, even with the Phenom X4 that emits quite a bit of extra heat (compared to X6). There is something definitely broken in your machine (I mean other than the OS that you are using). You should see what the problem is and get it fixed, your system would work much better.

---

### Post by Lucradia on 2011-07-19
Other than the Harddrive having an issue with Reallocation: 

```
smartctl 5.41 2011-06-09 r3365 [i686-w64-mingw32-win7(64)-sp1] (sf-win32-5.41-1)

Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    5VP52VG8
LU WWN Device Id: 5 000c50 0248fc892
Firmware Version: CC44
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Jul 19 10:02:24 2011 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed

                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (  609) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off supp
ort.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 194) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_
FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   112   099   006    Pre-fail  Always       -
       48233046
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -
       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -
       673
  5 Reallocated_Sector_Ct   0x0033   002   002   036    Pre-fail  Always   FAILI
NG_NOW 4015
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -
       80537896
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -
       5222
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -
       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -
       673
183 Runtime_Bad_Block       0x0000   100   100   000    Old_age   Offline      -
       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -
       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -
       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -
       168
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -
       0
190 Airflow_Temperature_Cel 0x0022   071   051   045    Old_age   Always       -
       29 (Min/Max 26/29)
194 Temperature_Celsius     0x0022   029   049   000    Old_age   Always       -
       29 (0 14 0 0)
195 Hardware_ECC_Recovered  0x001a   043   024   000    Old_age   Always       -
       48233046
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -
       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -
       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -
       1
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -
       15096810052460
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -
       3079895444
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -
       2309696153
```

My RAM in my signature is limited to 4GB, Dual Channel. Also, my PNY Nvidia card is taxed way too easily for a GTX 470, I believe it's because it's made from PNY, known for cheap parts. The drive has been "FAILING NOW" for the past week. I cannot buy a [new drive](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136801) or [cooling device](http://www.newegg.com/Product/Product.aspx?Item=N82E16835106150) until next month, which I plan to do. The drive will be from Best Buy, as I still have a 15 USD Gift Card with them.

---

### Post by 3Miro on 2011-07-19
> **Lucradia said:**
> 
My RAM in my signature is limited to 4GB, Dual Channel. Also, my PNY Nvidia card is taxed way too easily for a GTX 470, I believe it's because it's made from PNY, known for cheap parts. The drive has been "FAILING NOW" for the past week. I cannot buy a new drive or cooling device until next month, which I plan to do.

Cheap parts or not, 470 should not be better than 260. The HDD is probably the main problem, the benchmark data is being read on the fly and hence slowing things down. Hope you get it fixed soon.

---

### Post by Lucradia on 2011-07-19
> **3Miro said:**
> Cheap parts or not, 470 should not be better than 260. The HDD is probably the main problem, the benchmark data is being read on the fly and hence slowing things down. Hope you get it fixed soon.

A week and 3-4 days left ;)

---

### Post by Bandit on 2011-07-19
Here is my results from mine. System specs are on the screenshots.

First one is at native 1920x1080 resolution and other is at 1024x768.
My system is using 4x 1GB DDR2-800 chips in Dual Channel mode..

---

### Post by Bandit on 2011-07-19
> **Lucradia said:**
> ...................
In regards to your video card. I would get a MSI Cyclone 460GTX. Less then 200 bucks and its a smaller new series core compaired to the 470. My GPU never went above 34C the whole benchmark 5x times none stop.

---

### Post by 3Miro on 2011-07-19
I had an older version of the Benchmark. Here is the correct one. 

The test is mostly about the GPU (CPU and DDR seem to make little difference).

---

### Post by inobe on 2011-07-19
a little better fellas.

i will update the kernel module and give it another go.

---

### Post by inobe on 2011-07-19
kernel module helped :)

---

### Post by inobe on 2011-07-23
curious to see how others do with the benchmark:)

---

### Post by Bandit on 2011-07-24
Me too..

---

### Post by inobe on 2011-07-29
> **Bandit said:**
> Me too..


maybe their should be a browser load up benchmark for faceplant sites.

my browser opens instantly:p

---

### Post by Bandit on 2011-07-29
> **inobe said:**
> maybe their should be a browser load up benchmark for faceplant sites.

my browser opens instantly:p

LOL mine never closes.. hehe :popcorn:

---

### Post by Pdavid on 2011-07-30
Lucradia's results seem ok to me. He's using 8x AA, while the other posts don't have any AA. I've attached benchmarks with and without AA for comparison. 

In fact, my GPU (560Ti) is supposed to be very similar in performance to a 470, but clearly it's not performing anywhere near Lucradia's given the resolution difference (1024 x 768 against 1920 x 1080), although it seems to be in line with other benchmark in this thread.

These was no notable difference in results between unity2d and unity3d (1-2 average fps)

---

### Post by Bandit on 2011-07-30
8xAA at 1920x1080 max settings is to much for my system to show reasonably..
If I had dual video cards and a 6 core.. then maybe.. Its still tuff tho.

---

### Post by Lucradia on 2011-08-06
Brand new harddrive, Thermaltake Frio CPU Cooler, and new 8 GB of Mushkin RAM:

[http://i.imgur.com/IKidg.png](http://i.imgur.com/IKidg.png)

Not much difference from the old results, save for it running better. (Just not all that faster.)

gained about 200 score over the old one. Not the same settings either (4x instead of 16x.)

So a non-failing harddrive isn't any better it seems.

Even though it does run at about 20 FPS most of the time, the engine actually "Looks" like it's running 30+ FPS, so I don't know why they're showing horrible results.

When I did my previous results, 20 FPS looked super horrid, very laggy and everything. I think unigine is being biased, and actually limiting the FPS on AMD / nvidia.

---

### Post by Lucradia on 2011-08-07
It seems I *may* have found the culprit, sort of. Tessellation seems to bog down the engine quite a lot on my nvidia card. Removing tessellation and maxing everything else seems to make it play smoothly (even though the engine says it's about 25~30 fps average.)

Now, on 1280 x 720, the FPS Skyrockets, doubling the max FPS all the way to 118.

My card performs best in the night scenes, or any scene that doesn't focus on textures. Rather, it performs better with dynamics (flag waiving, etc.) and lighting.

Also may have taken a load off the CPU by notching down its voltage into the normal range (0.8 to 1.36) and upping the RAM from 1333 to 1600 MHz, and putting its voltage to stock (which, ASUS Probe II doesn't like, because stock is 1.35 Volts, and that's in below normal range according to it.)

RAM doesn't need OC CPU nor overvoltage to get 1600 (The motherboard can handle 1600 without OC'ing, as said in the manuals, and on newegg.)

---

### Post by Bandit on 2011-08-07
> **Lucradia said:**
> Brand new harddrive, Thermaltake Frio CPU Cooler, and new 8 GB of Mushkin RAM:

[http://i.imgur.com/IKidg.png](http://i.imgur.com/IKidg.png)

Not much difference from the old results, save for it running better. (Just not all that faster.)

gained about 200 score over the old one. Not the same settings either (4x instead of 16x.)

So a non-failing harddrive isn't any better it seems.

Even though it does run at about 20 FPS most of the time, the engine actually "Looks" like it's running 30+ FPS, so I don't know why they're showing horrible results.

When I did my previous results, 20 FPS looked super horrid, very laggy and everything. I think unigine is being biased, and actually limiting the FPS on AMD / nvidia.

Yea fast hard drives do nothing for you when your in the game. But they will help you get into the game faster. I am running 4x 320GB WD Blue Caviar HDDs. I get 380R/370W-Max and 280R/270W-average MB/s running them stripped (RAID0).

---

### Post by Lucradia on 2011-08-11
> **Bandit said:**
> Yea fast hard drives do nothing for you when your in the game. But they will help you get into the game faster. I am running 4x 320GB WD Blue Caviar HDDs. I get 380R/370W-Max and 280R/270W-average MB/s running them stripped (RAID0).

That's all? Wow, no use for RAID then with a handful of SSDs getting up to 550 MB/s alone.

---

### Post by mmsmc on 2011-08-11
[http://unigine.com/](http://unigine.com/)

  i saw the programs on that site, i must ask, what are they??

---

### Post by Bandit on 2011-08-12
> **mmsmc said:**
> [http://unigine.com/](http://unigine.com/)

  i saw the programs on that site, i must ask, what are they??

Gaming Benchmarks.. They work on Windows and Linux. So it can be a good comparison to over all system performance.

---

### Post by Bandit on 2011-08-12
> **Lucradia said:**
> That's all? Wow, no use for RAID then with a handful of SSDs getting up to 550 MB/s alone.

I am running SATA3, Even a OCZ Agility 3 want hit 550+ unless its on a SATA 6GBps compatible motherboard.

---

### Post by Lucradia on 2011-08-12
> **Bandit said:**
> I am running SATA3, Even a OCZ Agility 3 want hit 550+ unless its on a SATA 6GBps compatible motherboard.

My motherboard is 6 GBps compat: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131735](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131735)

```

SATA 6Gb/s
    7 x SATA 6Gb/s

SATA RAID
    6 x SATA 6Gb/s port(s), red support Raid 0, 1, 5, 10 by AMD SB950
```

---

### Post by Bandit on 2011-08-13
> **Lucradia said:**
> My motherboard is 6 GBps compat: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131735](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131735)

...

Thats a very nice mobo there. That would be good upgrade then. :-)

I been wanting to get a OCZ Revo drive, but I am broke and they are salty.. :(

---

### Post by Lucradia on 2011-08-13
> **Bandit said:**
> Thats a very nice mobo there. That would be good upgrade then. :-)

I been wanting to get a OCZ Revo drive, but I am broke and they are salty.. :(

It is a nice motherboard, but the normal voltage for CPU is not accepted as "normal" on the board. You may have to undervolt it to 1.36 or so for the CPU/NB light to turn green. I know I had to, and it makes the system much more stable. (Rarely, it will spit out an "Overclocking Failed" Error on POST, but it's rare enough to not matter.)

My RAM's stock voltage of 1.35 (Which still allows for 1600 Speed) is "normal" according to the onboard LED Light, but I had to turn off ASUS Probe II for the RAM Voltage monitor, as anything below 1.400 is too low voltage.

---

### Post by Perfect Storm on 2011-08-14
Mine:


Heaven Benchmark v2.5 Basic
System: elementary OS (Gnome with compiz enable).

[SIZE="3"]**FPS:**[/SIZE]	
60.3
[SIZE="3"]**Scores:**[/SIZE]	
1518
[SIZE="3"]**Min FPS:**[/SIZE]	
27.0
[SIZE="3"]**Max FPS:**	[/SIZE]
124.5


[SIZE="3"]**Hardware**[/SIZE]

**Binary:**	Linux 64bit GCC 4.4.5 Release Mar 1 2011
**Operating system:** Linux 2.6.35-30-generic x86_64
**CPU model:** AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
**CPU flags:** 3013MHz MMX+ 3DNow!+ SSE SSE2 SSE3 HTT
**GPU model:** GeForce GTX 285 PCI Express 280.13 1024Mb


**[SIZE="3"]Settings[/SIZE]**

**Render:** opengl
**Mode:** 1024x768 windowed
**Shaders:** high
**Textures:** high
**Filter:** trilinear
**Anisotropy:** 16x
**Occlusion:** enabled
**Refraction:** enabled
**Volumetric:** enabled
**Tessellation:** disabled

---

