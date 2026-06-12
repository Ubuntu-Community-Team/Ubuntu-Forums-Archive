---
title: "VLC - GPU Video Decoding (Intel HD 4000)"
date: 2013-04-13
forum: Ubuntu Development Version
---

### Post by ubu-for on 2013-04-13
I would like to use VLC to play high res videos but it looks like the CPU does all the decoding, despite the fact that overlay is marked by default.

Every hint to keep the fan speed low would be appreciated!

---

### Post by ajgreeny on 2013-04-13
The Intel HD 4000 gpu is on the cpu, so that may be why you think the cpu does all the decoding.  Where are you getting that info, anyway?

Are you using the sandybridge acceleration (sna) which is available with the later versions of the xserver-xorg-video-intel-2:2.2.21-6 that can even be installed on precise with the appropriate ppa repository.  If you're not sure about that run command ```
grep "SNA init" /var/log/Xorg.0.log
``` and you will soon see if you are.  If there is no output make a new /etc/X11/xorg.conf file with ```
gksudo gedit /etc/X11/xorg.conf
``` and add the following text to it
 ```
# New xorg.conf file manually added after update of xserver-xorg-video-intel from:-
# ppa:glasen/intel-driver
#
Section "Device"
 Identifier "Card0"
 Driver "intel"
 Option "AccelMethod" "sna"
EndSection

``` and restart the x session.

---

### Post by ubu-for on 2013-04-13
I thought the CPU is not as powerful as the GPU to decode videos, so the CPU workload produces lots of heat and the fan speeds up.

Yesterday I've tried to enable SNA with [this HowTo]('http://askubuntu.com/questions/225356/how-can-i-enable-the-sna-acceleration-method-for-intel-cards-under-ubuntu-12-04') but after reboot I could only start Ubuntu with low res once to undo everything.

Currently Ubuntu runs with xserver-xorg-video-intel 2:2.2.21-**5** and if I enter ...

```
grep "SNA init" /var/log/Xorg.0.log
```
I get the following output ...

```
[     5.388] (II) intel(0): SNA initialized with IvyBridge backend
```

So it looks like SNA is enabled.

---

### Post by Gyokuro on 2013-04-13
> **ubu-for said:**
> I would like to use VLC to play high res videos but it looks like the CPU does all the decoding, despite the fact that overlay is marked by default.Every hint to keep the fan speed low would be appreciated!Could you check following settings in VLC??Video Settings => Display mark: Accelerated video output (Overlay) and Output use OpenGL GLX video output (XCB)Input & Codecs: Codecs mark: Use GPU accelerated decoding

---

### Post by mc4man on 2013-04-13
I've a newer laptop that has intel hd4000 (nvidia gtx 660m) but atm have no interest in installing Ubuntu on it.
I can however test from a live session where vlc will use hardware decoding if enabled & supported.

You may want to install vainfo to check  - 


```
ubuntu@ubuntu:~$ vainfo
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.17
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```
And  then follow previous post (Gyokuro) , Ex.
```

vlc  -vv /path/to/vid
clipped...
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
[0x7f18640069c8] pulse audio output debug: using stereo channel map
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
[0x7f186cc02cc8] avcodec decoder: Using VA API version 0.32 for hardware decoding.
```

---

### Post by ubu-for on 2013-04-14
> **Gyokuro said:**
> Could you check following settings in VLC??Video Settings => Display mark: Accelerated video output (Overlay) and Output use OpenGL GLX video output (XCB)Input & Codecs: Codecs mark: Use GPU accelerated decoding
Ok, overlay was marked by default, output was set to default and now to OpenGL GLX video output (XCB).

Input/Codecs / Videocodes / FFmpeg / "hardware decoding" wasn't marked, now marked, if I got you right.

---

### Post by Gyokuro on 2013-04-14
> **ubu-for said:**
> Ok, overlay was marked by default, output was set to default and now to OpenGL GLX video output (XCB).

Input/Codecs / Videocodes / FFmpeg / "hardware decoding" wasn't marked, now marked, if I got you right.

Yes and how is now the CPU utilization - should be lower but not so low as in Mac OS X as the Mac GPU drivers are more advanced but should get much better with Mesa 9.2. It will take some time to get on par with Mac OS X drivers and the Intel's developers are doing a great job within the Mesa project.

---

### Post by ubu-for on 2013-04-14
> **Gyokuro said:**
> Yes and how is now the CPU utilization - should be lower but not so low as in Mac OS X as the Mac GPU drivers are more advanced but should get much better with Mesa 9.2. It will take some time to get on par with Mac OS X drivers and the Intel's developers are doing a great job within the Mesa project.

You're right! After some testing with my downloaded [reference video]('http://www.youtube.com/watch?v=06G4e15a46Y') (1080p), the fan does no longer speed up during playback and afterwards it turns higher and higher but not as high as before and not for a long time.

Thank you very much for your help! That's why I love Ubuntu ... it's not perfect, but the community :)

Are you part of the Mesa dev team and is there a time frame for Mesa 9.2?

---

