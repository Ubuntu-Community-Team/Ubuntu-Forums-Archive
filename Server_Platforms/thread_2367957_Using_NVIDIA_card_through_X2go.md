---
title: "Using NVIDIA card through X2go"
date: 2017-08-05
forum: Server Platforms
---

### Post by rackover on 2017-08-05
Hi,
I'm using as a server some old PC I've got, running Intel Pentium with 4GB of RAM. It has a NVIDIA GS210 Card connected through PCIe. 
Most of the time I use this server with kitty/putty, through ssh, but sometimes a graphical interface is needed : so I use x2go for that.
x2go is a simple program that allows to open a graphical session (in this case, xfce, as it is the one I installed : but any of them can do) via SSH and do bidirectional copypaste. It does even support pulseaudio! Is'nt that nice ?
But this graphical interface is very slow...even tho the SSH runs on LAN Network. The problem is not the retransmission of images : it's generating the images itself. I feel like the server is not using its PCIe NVIDIA Card (moving windows are stuttering, no transparency on anything, every d3d or ogl application lags af). However the drivers have been installed properly and the card seems to work through a classic VGA screen : but not with x2go.
As this program is not very well known it's pretty hard to get support : and I didn't find anyone with the same problem.
Here is some info :
```
rackover@rackover-CHADNET:~$ glxgears -info

GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.4.1)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow 



```

```
rackover@rackover-CHADNET:~$ nvidia-smi -a

==============NVSMI LOG==============


Timestamp                           : Sat Aug  5 11:05:40 2017
Driver Version                      : 340.102


Attached GPUs                       : 1
GPU 0000:01:00.0
    Product Name                    : GeForce G210
    Product Brand                   : GeForce
    Display Mode                    : N/A
    Display Active                  : N/A
    Persistence Mode                : Disabled
    Accounting Mode                 : N/A
    Accounting Mode Buffer Size     : N/A
    Driver Model
        Current                     : N/A
        Pending                     : N/A
    Serial Number                   : N/A
    GPU UUID                        : GPU-e0d53162-0a30-69a4-043e-db22dcf0f9d5
    Minor Number                    : 0
    VBIOS Version                   : 70.18.08.00.06
    MultiGPU Board                  : N/A
    Board ID                        : N/A
    Inforom Version
        Image Version               : N/A
        OEM Object                  : N/A
        ECC Object                  : N/A
        Power Management Object     : N/A
    GPU Operation Mode
        Current                     : N/A
        Pending                     : N/A
    PCI
        Bus                         : 0x01
        Device                      : 0x00
        Domain                      : 0x0000
        Device Id                   : 0x0A6010DE
        Bus Id                      : 0000:01:00.0
        Sub System Id               : 0x2180174B
        GPU Link Info
            PCIe Generation
                Max                 : N/A
                Current             : N/A
            Link Width
                Max                 : N/A
                Current             : N/A
        Bridge Chip
            Type                    : N/A
            Firmware                : N/A
    Fan Speed                       : N/A
    Performance State               : P0
    Clocks Throttle Reasons         : N/A
    FB Memory Usage
        Total                       : 511 MiB
        Used                        : 2 MiB
        Free                        : 509 MiB
    BAR1 Memory Usage
        Total                       : N/A
        Used                        : N/A
        Free                        : N/A
    Compute Mode                    : Default
    Utilization
        Gpu                         : N/A
        Memory                      : N/A
        Encoder                     : N/A
        Decoder                     : N/A
    Ecc Mode
        Current                     : N/A
        Pending                     : N/A
    ECC Errors
        Volatile
            Single Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
            Double Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
        Aggregate
            Single Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
            Double Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
    Retired Pages
        Single Bit ECC              : N/A
        Double Bit ECC              : N/A
        Pending                     : N/A
    Temperature
        GPU Current Temp            : 62 C
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
    Power Readings
        Power Management            : N/A
        Power Draw                  : N/A
        Power Limit                 : N/A
        Default Power Limit         : N/A
        Enforced Power Limit        : N/A
        Min Power Limit             : N/A
        Max Power Limit             : N/A
    Clocks
        Graphics                    : N/A
        SM                          : N/A
        Memory                      : N/A
    Applications Clocks
        Graphics                    : N/A
        Memory                      : N/A
    Default Applications Clocks
        Graphics                    : N/A
        Memory                      : N/A
    Max Clocks
        Graphics                    : N/A
        SM                          : N/A
        Memory                      : N/A
    Clock Policy
        Auto Boost                  : N/A
        Auto Boost Default          : N/A
    Compute Processes               : N/A



```

```
rackover@rackover-CHADNET:~$ egrep -i " connected|card detect|primary dev" /var/log/Xorg.0.log

[    47.241] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0. 



```

```
rackover@rackover-CHADNET:~$ glxinfo|egrep "OpenGL vendor|OpenGL renderer"

OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect



```

---

### Post by TheFu on 2017-08-05
x2go doesn't use any GPU HW.  

In fact, it works on systems without a GPU installed.  If you think about the architecture, it is clear why this is.

If you are unhappy with the performance, turn down the size of the screens transmitted (I find the 4k-jpeg excellent) and tell x2go the amount of bandwidth you have - try 1 less than the truth to get more bandwidth optimized or if using wifi.

I run at 1920x1080 all day on my chromebook and 1920x1200 on my desktop. Wonderful.

Remote audio only works if ssh is available in both directions, IME.  That is seldom the situation over the internet.  Also, don't expect video streaming to work well at all. The protocol isn't designed for that.  For productivity applications, with proper tuning of the compression and available bandwidth, x2go performs very nicely.

---

