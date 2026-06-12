---
title: "VP9 hardware acceleration vanished after upgrade from 17.10 to 18.04 beta"
date: 2018-03-16
forum: Ubuntu Development Version
---

### Post by cran2 on 2018-03-16
Hardware is Dell XPS13 9365 with i7-7Y75 (Kaby Lake) CPU. With 17.10 I used to have hardware accelerated video decoding for VP9, as reported by vainfo:

```

# vainfo
error: XDG_RUNTIME_DIR not set in the environment.
libva info: VA-API version 0.40.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_40
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.40 (libva )
vainfo: Driver version: Intel i965 driver for Intel(R) Kabylake - 1.8.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Simple            :    VAEntrypointEncSlice
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSliceLP
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointEncSliceLP
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointEncSliceLP
      VAProfileH264MultiviewHigh      :    VAEntrypointVLD
      VAProfileH264MultiviewHigh      :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileH264StereoHigh         :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointEncPicture
      VAProfileVP8Version0_3          :    VAEntrypointVLD
      VAProfileVP8Version0_3          :    VAEntrypointEncSlice
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointEncSlice
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileHEVCMain10             :    VAEntrypointEncSlice
      VAProfileVP9Profile0            :    VAEntrypointVLD
      VAProfileVP9Profile0            :    VAEntrypointEncSlice
      VAProfileVP9Profile2            :    VAEntrypointVLD

```

After upgrade to bionic beta, the output of vainfo on the same hardware is this:

```

# vainfo 
error: can't connect to X server!
libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_0
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Kaby Lake - 2.0.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Simple            :    VAEntrypointEncSlice
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSliceLP
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointEncSliceLP
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointEncSliceLP
      VAProfileH264MultiviewHigh      :    VAEntrypointVLD
      VAProfileH264MultiviewHigh      :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileH264StereoHigh         :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointEncPicture
      VAProfileVP8Version0_3          :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointEncSlice
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileHEVCMain10             :    VAEntrypointEncSlice

```

Kernel version is 4.15.0-12-generic. To me it looks like it has to do with the libva API change that happened with the switch of the VA-API version. In any case it's certainly a regression, as I could watch 4k VP9 before (although buggy, but for another reason), now I can't at all.

H.264 hardware decoding still works fine, though youtube high resolution content is usually only available with VP9.

Can somebody with the same chipset perhaps confirm this? Also, if it's a bug, should I report this to libva upstream? Or i965-va-driver upstream? Or to launchpad?

Thanks!

---

### Post by cran2 on 2018-03-16
It works if I download and compile libva-2.1.0 and intel-vaapi-driver-2.1.0 myself. So something is messed up with the packages in bionic.

[https://bugs.launchpad.net/ubuntu/+source/intel-vaapi-driver/+bug/1756380](https://bugs.launchpad.net/ubuntu/+source/intel-vaapi-driver/+bug/1756380)

---

### Post by mc4man on 2018-03-16
You should try the repo libva as it was already at 2.1.0 & the compiled 2.1.0 intel-vaapi-driver  as the Debian/Ubuntu version is still at 2.0.0
Then you'd know if it was the driver version or driver version mismatch..

---

### Post by cran2 on 2018-03-16
Yes, it works with current libva/intel-vaapi-driver from github. See also the linked bug report in my second post. As I understand it the fix is simply to update the driver package to the current upstream release.

---

### Post by cran2 on 2018-03-16
after reading your post again it seems I did not fully understand it on first read. will try

---

### Post by mc4man on 2018-03-16
I use the new driver here for different reasons as my iGPU is too old for vp9, (there are some new functions in libva that need the 2.1.x driver), it's a little surprising Debian hasn't added it yet, I've checked every couple of days for last several weeks & nothing.
Ubuntu generally just syncs from Debian so that's why they're still on the 2.0.0 one. At this point there is a feature freeze so not as simple to add, though can be done.
I'd expect them to add at some point, in any event it'll show up in a ppa or two before too long.

---

### Post by cran2 on 2018-03-17
I can confirm that updating the driver is enough to bring VP9 back:

  LIBVA_DRIVERS_PATH=$HOME/tmp/intel/dri vainfo

list the corresponding profiles.

---

### Post by jbicha on 2018-03-17
Please file an Ubuntu bug for this issue.

---

### Post by mc4man on 2018-03-17
> **jbicha said:**
> Please file an Ubuntu bug for this issue.
Do you mean file to upgrade  i965-va-driver or bug on issue against  i965-va-driver (the later was already done..

---

### Post by jbicha on 2018-03-17
Ok, never mind. I see the bug now. :D

---

