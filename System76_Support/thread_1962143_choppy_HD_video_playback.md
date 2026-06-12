---
title: "choppy HD video playback"
date: 2012-04-20
forum: System76 Support
---

### Post by itcave on 2012-04-20
I Panasonic-HDC-TM90K camcorder and record home movies in 1080p.  When  playing these videos on my Panp7 they are always choppy.  

I tried running Ubuntu 11.10 with the default driver and the ATI driver.  The video play back was not much different with or without the ATI driver.

Currently I am runnning LinuxMint12.  I have found with the default driver my videos with play decent with less chop, but the computer fan is running full speed ALL the time.  When I install the ATI driver the fan slows down, but the video playback is choppy again.  Also the ATI driver in Mint seems to mess up the top bar and some buttons.  I get ranbow squigles across the bar and some buttons.

It seems like this panp7 should have plenty of power to play 1080p smoothly.  Can anyone help?

Thanks!

---

### Post by sudodus on 2012-04-20
My solution to a similar situation was

1. to optimize the software.

- Running Lubuntu with the ultra-light desktop environment LXDE plays video much better with a given video player, cpu and graphics card. Or install lubuntu-desktop or LXDE into your current flavour of Ubuntu and select what to run at the log in screen.

- Try various versions of the built-in and proprietary graphics drivers.

- Try various video players: mplayer, mplayer2, vlc may be better than the default program. And tweak these programs!

- Convert the video file to something, that is easier for the video player to manage. This is particularly important if it is limited by the cpu, or if you would be able to use hardware acceleration, use the graphics processor to do some of the work instead of the cpu.

2. to install a graphics card with better support. Nvidia and ***new*** ATI/Radeon cards have better drivers for linux than older ATI cards. That will be hard in a laptop of course (I'm not familiar with System 76, so I don't know what computer type you have).

---

### Post by isantop on 2012-04-20
> **itcave said:**
> I Panasonic-HDC-TM90K camcorder and record home movies in 1080p.  When  playing these videos on my Panp7 they are always choppy.  

I tried running Ubuntu 11.10 with the default driver and the ATI driver.  The video play back was not much different with or without the ATI driver.

Currently I am runnning LinuxMint12.  I have found with the default driver my videos with play decent with less chop, but the computer fan is running full speed ALL the time.  When I install the ATI driver the fan slows down, but the video playback is choppy again.  Also the ATI driver in Mint seems to mess up the top bar and some buttons.  I get ranbow squigles across the bar and some buttons.

It seems like this panp7 should have plenty of power to play 1080p smoothly.  Can anyone help?

Thanks!

Is HD video from other sources (say YouTube) also choppy? It could be the encoding on the camera.

---

### Post by itcave on 2012-04-20
> **sudodus said:**
> My solution to a similar situation was

1. to optimize the software.

- Running Lubuntu with the ultra-light desktop environment LXDE plays video much better with a given video player, cpu and graphics card. Or install lubuntu-desktop or LXDE into your current flavour of Ubuntu and select what to run at the log in screen.

- Try various versions of the built-in and proprietary graphics drivers.

- Try various video players: mplayer, mplayer2, vlc may be better than the default program. And tweak these programs!

- Convert the video file to something, that is easier for the video player to manage. This is particularly important if it is limited by the cpu, or if you would be able to use hardware acceleration, use the graphics processor to do some of the work instead of the cpu.

2. to install a graphics card with better support. Nvidia and ***new*** ATI/Radeon cards have better drivers for linux than older ATI cards. That will be hard in a laptop of course (I'm not familiar with System 76, so I don't know what computer type you have).

Thanks for your input.  I have noticed that VLC typicaly plays things a little better.  Not sure what you condsider an 'OLD' ATI card, but here is my system info.

System76 Pangolin Performance laptop - panp7
Intel Core i5-520M (2.40GHz) - 4GB DDR3 RAM
ATI Mobility Radeon HD 4570, 512MB GDDR2
Intel Wi-Fi Link 5100, 802.11A/B/G/N - Bluetooth
15.6" HD+ LED Display (1600 x 900)
500GB HDD @ 7200 RPM - Linux Mint 12

I may give LXDE a try, but would like to do what I can with my existing desktop first.

---

### Post by itcave on 2012-04-20
> **isantop said:**
> Is HD video from other sources (say YouTube) also choppy? It could be the encoding on the camera.

YouTube HD video plays fine.  I'm sure my files are a much higher bit rate. 

How would I know if the cause was the encoding on the camera?  The camera can play back the videos perfectly.  Even when using HDMI to my TV.

---

### Post by 0011235813 on 2012-04-20
Hmmm... What bitrate are your videos? I know my computer struggles with 1080p video (which you're not getting on that laptop unless you've hooked it up to a monitor/tv) but that's because of AMDs 1.65GHz APU (which is still better than Atom) and VESA drivers. But you're system should be more than capable, if bitrate is higher than 3500 KB/s, then it's a waste of storage. Also, what format is your camera encoding? Mp4+h.264?

---

### Post by itcave on 2012-04-20
> **0011235813 said:**
> Hmmm... What bitrate are your videos? I know my computer struggles with 1080p video (which you're not getting on that laptop unless you've hooked it up to a monitor/tv) but that's because of AMDs 1.65GHz APU (which is still better than Atom) and VESA drivers. But you're system should be more than capable, if bitrate is higher than 3500 KB/s, then it's a waste of storage. Also, what format is your camera encoding? Mp4+h.264?

After looking at the manual.....  The camera uses AVCHD (MPEG-4 AVC/H.264) and the files end with a .MTS.  For 1080/60i it offers for following bit rates: 17Mbps, 13Mbps, 9Mbps, and 5Mbps.  I have been mostly shooting at 17Mbps. It also offers a 1080/60p mode @ 28Mbps.

---

### Post by 0011235813 on 2012-04-20
> **itcave said:**
> After looking at the manual.....  The camera uses AVCHD (MPEG-4 AVC/H.264) and the files end with a .MTS.  For 1080/60i it offers for following bit rates: 17Mbps, 13Mbps, 9Mbps, and 5Mbps.  I have been mostly shooting at 17Mbps. It also offers a 1080/60p mode @ 28Mbps.
An .mts file container? Why don't you try and encode it into something else using a program like Transmageton or Avidemux and see if that runs better? It could be the file container isn't properly supported.

---

### Post by SeijiSensei on 2012-04-20
Before re-encoding, I'd recommend installing **smplayer** from the repositories and seeing how well mplayer handles your file.  Unfortunately you don't have an NVIDIA card which would offload the H.264 decoding onto the graphics adapter.  There are ways to use [VA-API]("http://en.wikipedia.org/wiki/Video_Acceleration_API") with [some ATI cards]("http://en.wikipedia.org/wiki/AMD_Catalyst"); I don't know if yours is supported.

---

### Post by QIII on 2012-04-20
That card will support full HD H.264 hardware acceleration using VAAPI with the XvBA back end. 

NVIDIA comes with VDPAU out of the box because VDPAU is proprietary.  ATi has no proprietary hardware acceleration because the open standard VAAPI is available.

VAAPI can be installed easily with the addition of four packages in the repos.

I'm on my cell phone waiting for a train right now, but when I get home I will post the four packages to install for full HD 1080p hardware accelerated H.264 playback on ATI cards.

---

### Post by QIII on 2012-04-20
Install the following (may be named slightly differently in Mint repos):

vainfo, xvba-va-driver, libva-egl1, libva-glx1

In the terminal, see if everything is working:

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```

If you get an error like this:

```
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

we can deal with a misplaced symlink.

For smplayer, use xv as the output driver.

For VLC, try one of these:  OpenGL XCB, Xvideo XCB or X11 XCB

For XBMC, disable VDPAU and enable VAAPI.

---

### Post by itcave on 2012-04-24
> **0011235813 said:**
> An .mts file container? Why don't you try and encode it into something else using a program like Transmageton or Avidemux and see if that runs better? It could be the file container isn't properly supported.

Thanks for the tip.  I would rather not have to rencode every video I shoot just to be able to play it.  So idealy I am looking for a different kind of solution. 

That said, rencoding is worth a try.  I installed Avidemux.  Which  settings/format do you recomend?

---

### Post by itcave on 2012-04-24
> **SeijiSensei said:**
> Before re-encoding, I'd recommend installing **smplayer** from the repositories and seeing how well mplayer handles your file.  Unfortunately you don't have an NVIDIA card which would offload the H.264 decoding onto the graphics adapter.  There are ways to use [VA-API]("http://en.wikipedia.org/wiki/Video_Acceleration_API") with [some ATI cards]("http://en.wikipedia.org/wiki/AMD_Catalyst"); I don't know if yours is supported.

I tried SMPLAYER.  VLC still plays it better.

---

### Post by itcave on 2012-04-24
> **QIII said:**
> Install the following (may be named slightly differently in Mint repos):

vainfo, xvba-va-driver, libva-egl1, libva-glx1

In the terminal, see if everything is working:

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```

If you get an error like this:

```
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

we can deal with a misplaced symlink.

For smplayer, use xv as the output driver.

For VLC, try one of these:  OpenGL XCB, Xvideo XCB or X11 XCB

For XBMC, disable VDPAU and enable VAAPI.


I couldn't find libva-egl1, but installed the rest.  Here was the output.
```
 $ vainfo
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

Unfortunatly I haven't noticed any improvment in playback.  :(

---

### Post by 0011235813 on 2012-04-24
> **itcave said:**
> Thanks for the tip.  I would rather not have to rencode every video I shoot just to be able to play it.  So idealy I am looking for a different kind of solution. 

That said, rencoding is worth a try.  I installed Avidemux.  Which  settings/format do you recomend?

Hmm, well set the codec to MPEG4 (x.264) the audio codec to either mp3, aac or ogg (Vorbis) and the file container to something like .mkv. Make sure you press "configure" on the video codec and enter "dual pass- average bitrate" set bitrate to something like 4 or 5 thousand KB/s. 
Or you could try Transmagedon and encode it to .webm and open it in Firefox. 
That said, it may be your video card genuinely can't handle 1080p video. I'll check into it's performance and see.

---

### Post by itcave on 2012-04-24
> **0011235813 said:**
> Hmm, well set the codec to MPEG4 (x.264) the audio codec to either mp3, aac or ogg (Vorbis) and the file container to something like .mkv. Make sure you press "configure" on the video codec and enter "dual pass- average bitrate" set bitrate to something like 4 or 5 thousand KB/s. 
Or you could try Transmagedon and encode it to .webm and open it in Firefox. 
That said, it may be your video card genuinely can't handle 1080p video. I'll check into it's performance and see.

When opening MTS file in Avidemux i get the following message:

> H.264 detected

If the file is using B-frames as reference it can lead to a crash or stuttering.
Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY.
Do you want to use that mode?

I selected Yes, and used your sugested settings.  It took 19 mins to rencode a 2min 15 sec video.  The result:  no more choppy video.  The video is much lower quality and plays super slow with audio going regular speed.

---

### Post by 0011235813 on 2012-04-25
> **itcave said:**
> When opening MTS file in Avidemux i get the following message:



I selected Yes, and used your sugested settings.  It took 19 mins to rencode a 2min 15 sec video.  The result:  no more choppy video.  The video is much lower quality and plays super slow with audio going regular speed.

The lower quality thing could be due to the bitrate and resolution settings. If you set it to "copy" instead, it should use the same video quality and only the container will be changed. I suspect it is because of the container, although it could well be due to your GPU. What GPU does the model you bought have?

EDIT: I suspect the latter. If it took you 10x the amount of time to convert the 1080 video, and on a low end machine I know can convert a 1080p video that lasts 5-6 minutes in half an hour, without thrashing the processor to unusable heights, then a machine taking that much time probably couldn't handle 1080p video in the first place. I know this one can barely handle it.

---

### Post by jbelmonte on 2012-04-25
> **0011235813 said:**
> The lower quality thing could be due to the bitrate and resolution settings. If you set it to "copy" instead, it should use the same video quality and only the container will be changed. I suspect it is because of the container, although it could well be due to your GPU. What GPU does the model you bought have?

EDIT: I suspect the latter. If it took you 10x the amount of time to convert the 1080 video, and on a low end machine I know can convert a 1080p video that lasts 5-6 minutes in half an hour, without thrashing the processor to unusable heights, then a machine taking that much time probably couldn't handle 1080p video in the first place. I know this one can barely handle it.

> **itcave said:**
> ... here is my system info.

System76 Pangolin Performance laptop - panp7
Intel Core i5-520M (2.40GHz) - 4GB DDR3 RAM
ATI Mobility Radeon HD 4570, 512MB GDDR2
Intel Wi-Fi Link 5100, 802.11A/B/G/N - Bluetooth
15.6" HD+ LED Display (1600 x 900)
500GB HDD @ 7200 RPM - Linux Mint 12


Those specs look more than adequate. I doubt it is a hardware issue.

---

### Post by itcave on 2012-04-26
Yes.  It seems like the hardware should handle it fine...

I was chatting with a fellow geek at work today about this video issue.  He suggested it may be a problem with the Linux kernel.  He brought this up because the newest version of the Linux kernel made some updates to the PCIexpress bus (so he says).  He explained that his very similar laptop is able to play HD just fine even with its on-board video.  Maybe an update to the PCIexpress bus would make a huge difference with my ATI card?

Ubuntu 12.04 comes out on 4/26...  later today...  I'm thinking I may install that since it has the new kernel.  Then I can reassess the video playback.  

I really appreciate all the replies and assistance people have given.  I'll report back in a day or 2 after testing 12.04.  Unless I get more suggestions and try something else in between. :)

---

### Post by itcave on 2012-04-27
Ubuntu 12.04 has been installed but alas, no solution.  The choppyness of the video seems to be about the same.  I tried with the opensource driver and with the ATI driver...  Still about the same.  

I am really not sure what else to try.  :confused:

Now that I am running System76's officaly supported OS maybe they can provide some assistance as well?  :)

Thanks

---

### Post by isantop on 2012-04-27
I really think it's the camera in this case. You mentioned that 1080p video from other sources plays fine? That's telling me that the file is at fault, and therefore, the camera.

---

### Post by itcave on 2012-05-01
> **isantop said:**
> I really think it's the camera in this case. You mentioned that 1080p video from other sources plays fine? That's telling me that the file is at fault, and therefore, the camera.

The camera's files play fine on my wifes mac book pro which has similar hardware.  The camera itself also plays back the videos fine to my tv (via hdmi).

---

### Post by isantop on 2012-05-02
> **itcave said:**
> The camera's files play fine on my wifes mac book pro which has similar hardware.  The camera itself also plays back the videos fine to my tv (via hdmi).

Right, but the codec or container it's using is unsupported or poorly supported in Ubuntu. You'll need to find a way to have the camera create files using a different container or codec.

---

