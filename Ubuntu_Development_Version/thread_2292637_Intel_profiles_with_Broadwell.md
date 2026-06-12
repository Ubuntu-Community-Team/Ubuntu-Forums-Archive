---
title: "Intel profiles with Broadwell"
date: 2015-08-29
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-08-29
I only have Haswell here but am curious if any of these 3 profiles are available with Broadwell (HD 5300 > 6000, Iris pro 6100/6200
    VAProfileHEVCMain              
    VAProfileHEVCMain10             
    VAProfileVP9Profile0

Can be seen by installing & then running vainfo

Ex. with Haswell - 
```
$ vainfo
.......
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
      VAProfileH264MultiviewHigh      :	VAEntrypointVLD
      VAProfileH264MultiviewHigh      :	VAEntrypointEncSlice
      VAProfileH264StereoHigh         :	VAEntrypointVLD
      VAProfileH264StereoHigh         :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc
      VAProfileJPEGBaseline           :	VAEntrypointVLD
      VAProfileH264MultiviewHigh      :	VAEntrypointVLD
      VAProfileH264MultiviewHigh      :	VAEntrypointEncSlice
      VAProfileH264StereoHigh         :	VAEntrypointVLD
      VAProfileH264StereoHigh         :	VAEntrypointEncSlice
```

---

### Post by ventrical on 2015-08-30
Can't get that to work here:

```

ventrical@ventrical-MS-7850:~$ vainfo
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
ventrical@ventrical-MS-7850:~$ sudo vainfo
error: XDG_RUNTIME_DIR not set in the environment.
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by mc4man on 2015-08-30
> **ventrical said:**
> Can't get that to work here:

```

ventrical@ventrical-MS-7850:~$ vainfo
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
ventrical@ventrical-MS-7850:~$ sudo vainfo
error: XDG_RUNTIME_DIR not set in the environment.
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
ventrical@ventrical-MS-7850:~$ 

```
My mistake, assumed anyone using Intel gpu would have the driver installed - 
```
sudo apt-get install i965-va-driver
```
Then vainfo will work

---

### Post by ventrical on 2015-08-30
Thanks .
Whoops.. thought I had Broadwell.

```

ventrical@ventrical-MS-7850:~$ vainfo
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_38
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.38 (libva 1.6.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Haswell Desktop - 1.6.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Simple            :    VAEntrypointEncSlice
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileH264MultiviewHigh      :    VAEntrypointVLD
      VAProfileH264MultiviewHigh      :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileH264StereoHigh         :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileH264MultiviewHigh      :    VAEntrypointVLD
      VAProfileH264MultiviewHigh      :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileH264StereoHigh         :    VAEntrypointEncSlice
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by ventrical on 2015-08-30
This:

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller

```

is formerly known as haswell. Is why I thought it was not haswell desktop.

regards..
edit:

is called 'haswell refresh' which is broadwell but I need to upgrade BIOS :)+ processor.

---

