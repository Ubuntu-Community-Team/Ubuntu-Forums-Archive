---
title: "Galago Pro OpenCL support"
date: 2015-06-25
forum: System76 Support
---

### Post by notbitmonk on 2015-06-25
Received my Galago Pro last week. I ordered it with 14.04. I use darktable to develop my RAW photographs. The software has the option to use OpenCL if the graphic cards supports it. In this case the Intel Iris 5200 supports it. In my previous computer I had a Radeon card and support for OpenCL was only available when I used the closed source AMD drivers. When I used the Restricted Drivers application I did not find any Intel drivers or any drivers for that matter. Using ```
clinfo
``` I got the following results:
```
clinfo: /usr/lib/x86_64-linux-gnu/libOpenCL.so.1: no version information available (required by clinfo)
I: ICD loader reports no usable platforms

```
Further search got me to Intel Graphic Installer that is not available to 14.04. I searched for Intel OpenCL and ended up at [https://software.intel.com/en-us/articles/opencl-drivers](https://software.intel.com/en-us/articles/opencl-drivers). In section 3 of the installation instructions it says that OpenCL support is provided by using the Intel Graphic Drivers. Back to the Graphic Installer I went. If I understood things right, the Graphics Installer will install the Intel Graphics Stack for Linux, the latest being 2015Q1. So I went to the latest Graphics Stack ([https://01.org/linuxgraphics/downloads/2015/2015q1-intel-graphics-stack-release](https://01.org/linuxgraphics/downloads/2015/2015q1-intel-graphics-stack-release)) to look at the components of it. Searching in the Ubuntu Software Center I observed that libva and vaapi are not installed in my computer. These appear to be the graphic drivers supporting hardware acceleration. I ran ```
vainfo
``` and received the following message:
```
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```
Am I right to think that hardware acceleration is not enabled without these drivers? Bak to OpenCL, the Intel entry for OpenCL in the Ubuntu Software Center is beignet, which is quite old. Do you think that I can install libva1, i965-va-driver, gstreamer1.0-vaapi and beignet for hardware acceleration and OpenCL support without messing my computer?

---

### Post by notbitmonk on 2015-06-25
I installed libva1, i965-va-driver, gstreamer1.0-vaapi and beignet. Beignet didn't make darktable use OpenCL so I removed it. I did not see any noticeable (by this I mean changes my eyes could see) after installing libva1, i965-va-driver and gstreamer1.0-vaapi.
I downloaded Intel OpenCL drivers at [https://software.intel.com/en-us/articles/opencl-drivers#ubuntu64](https://software.intel.com/en-us/articles/opencl-drivers#ubuntu64). Afterwards I ran clinfo and got these results:
```

Number of platforms:				 1
  Platform Profile:				 FULL_PROFILE
  Platform Version:				 OpenCL 1.2 LINUX
  Platform Name:				 Intel(R) OpenCL
  Platform Vendor:				 Intel(R) Corporation
  Platform Extensions:				 cl_khr_icd cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics cl_khr_byte_addressable_store cl_khr_depth_images cl_khr_3d_image_writes cl_intel_exec_by_local_thread cl_khr_spir cl_khr_fp64 


  Platform Name:				 Intel(R) OpenCL
Number of devices:				 1
  Device Type:					 CL_DEVICE_TYPE_CPU
  Device ID:					 32902
  Max compute units:				 8
  Max work items dimensions:			 3
    Max work items[0]:				 8192
    Max work items[1]:				 8192
    Max work items[2]:				 8192
  Max work group size:				 8192
  Preferred vector width char:			 1
  Preferred vector width short:			 1
  Preferred vector width int:			 1
  Preferred vector width long:			 1
  Preferred vector width float:			 1
  Preferred vector width double:		 1
  Native vector width char:			 32
  Native vector width short:			 16
  Native vector width int:			 8
  Native vector width long:			 4
  Native vector width float:			 8
  Native vector width double:			 4
  Max clock frequency:				 2200Mhz
  Address bits:					 64
  Max memory allocation:			 2073026560
  Image support:				 Yes
  Max number of images read arguments:		 480
  Max number of images write arguments:		 480
  Max image 2D width:				 16384
  Max image 2D height:				 16384
  Max image 3D width:				 2048
  Max image 3D height:				 2048
  Max image 3D depth:				 2048
  Max samplers within kernel:			 480
  Max size of kernel argument:			 3840
  Alignment (bits) of base address:		 1024
  Minimum alignment (bytes) for any datatype:	 128
  Single precision floating point capability
    Denorms:					 Yes
    Quiet NaNs:					 Yes
    Round to nearest even:			 Yes
    Round to zero:				 No
    Round to +ve and infinity:			 No
    IEEE754-2008 fused multiply-add:		 No
  Cache type:					 Read/Write
  Cache line size:				 64
  Cache size:					 262144
  Global memory size:				 8292106240
  Constant buffer size:				 131072
  Max number of constant args:			 480
  Local memory type:				 Global
  Local memory size:				 32768
  Error correction support:			 0
  Unified memory for Host and Device:		 1
  Profiling timer resolution:			 1
  Device endianess:				 Little
  Available:					 Yes
  Compiler available:				 Yes
  Execution capabilities:				 
    Execute OpenCL kernels:			 Yes
    Execute native function:			 Yes
  Queue properties:				 
    Out-of-Order:				 Yes
    Profiling :					 Yes
  Platform ID:					 0x1576a70
  Name:						 Intel(R) Core(TM) i7-4770HQ CPU @ 2.20GHz
  Vendor:					 Intel(R) Corporation
  Device OpenCL C version:			 OpenCL C 1.2 
  Driver version:				 1.2.0.43
  Profile:					 FULL_PROFILE
  Version:					 OpenCL 1.2 (Build 43)
  Extensions:					 cl_khr_icd cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics cl_khr_byte_addressable_store cl_khr_depth_images cl_khr_3d_image_writes cl_intel_exec_by_local_thread cl_khr_spir cl_khr_fp64 

```
It seems I have OpenCL support, darktable just doesn't see it.
Just in case somebody is wondering about the vainfo after I installed the drivers, this is what I got:
```

libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_35
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.35 (libva 1.3.0)
vainfo: Driver version: Intel i965 driver - 1.3.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Simple            :	VAEntrypointEncSlice
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc
      VAProfileJPEGBaseline           :	VAEntrypointVLD

```

---

