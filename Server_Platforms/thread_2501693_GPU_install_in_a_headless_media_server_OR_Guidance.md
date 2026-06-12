---
title: "GPU install in a headless media server OR Guidance"
date: 2024-10-17
forum: Server Platforms
---

### Post by sgt-mike on 2024-10-17
Currently I have two GTX 550Ti's installed in my media server (headless).
 
My _objective for having a or multiple GPU's in is to transcode_. I know that these are not as good as other versions / models  of GPU's for this purpose. But I had the idea to attempt these until such a time as I could select better Hardware for this purpose. << That part may be a fool's folly on my part.  
As such I have scoured multiple sites including here to no avail in order to load drivers for these cards. Every time the installation fails due to dependencies. I have attempted to purge any Nvida drivers via the CLI before any attempt to load any drivers, which I can't even recall how many different drivers I have tried. I have attempted headless drivers and drivers that are not headless. 

I have seen in past post's that many go Ohhhh NOOOO or NOT AGAIN when the GTX 550Ti is mentioned and now fully understand why LOL

My understanding is that version 390 I think was the LAST version before Nvida abandoned driver support for that card. I maybe wrong. 

```
mike@deepblue:~$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.1 LTS
Release:        24.04
Codename:       noble 
```

```
mike@deepblue:~$ sudo lshw -C display  *-display
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 resolution=1280,1024
       resources: irq:56 memory:f4000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:e000(size=128) memory:c0000-dffff
  *-display
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:57 memory:f0000000-f1ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:d000(size=128) memory:f2000000-f207ffff 
```

I have noticed that from the lshw out put that nouveau is listed as a driver. I have attempted to uninstall it several times before install attempts of a nvida driver. 

This part will sound like thread drift but in reality it isn't when I got the system which was used I guess for gaming it actually had three GTX 550Ti in it 2 bridged via SLI 1 separate for video ? Anyway the actual important part is I don't have these bridged as my understanding is that it wont work for my intended purpose. The only reason I mention this is so it's clear that_ they are not bridged for clarity's sake_. Why did I stick two in ? simple not a good card from my understanding and two might work better than 1 as a interim. (as I keep going over this and editing the thought goes through my mind this might be why I keep failing, maybe pull one and reattempt? so I can save / waste more time on this )

While I would like to get these working as a interim, it is not required for my sanity.
 I KNOW _EVERYONE here is a VOLUNTEER  and is NOT REQUIRED to assist._ 
I would Like to thank each of you for your efforts upfront. 

[B]This post is actually requesting answers / solutions / guidance by or in two parts
1. gain assistance in installing drivers 

OR 

2. Recommendations for a GPU for this purpose. [/B]

While I like Nvida somewhat, I'm not opposed to any recommendation as long as it works. Bear in mind that I do intend on using a more capable GPU in the future SO even input vs assistance is highly welcomed. The best course of action may very well be to shelve the idea and seek a better card I don't know. And Honestly I don't just Have to have this card work. 

I have considered the GTX 1070 as one solution based on used price point vs cuda cores and score. Still on the fence on that card. I have that one in my windows box and it works great there but may not be the best choice for the media server, that is one reason I considered it.

---

### Post by sgt-mike on 2024-10-17
Just to show what is going on with my end

```
 mike@deepblue:~$ sudo apt-get purge xserver-xorg-video-nouveau && sudo apt-get install nvidia-driver-390Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'xserver-xorg-video-nouveau' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libfontenc1 libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390 libnvidia-decode-390 libnvidia-encode-390
  libnvidia-fbc1-390 libnvidia-gl-390 libnvidia-ifr1-390 libxcvt0 libxfont2 libxnvctrl0 nvidia-compute-utils-390
  nvidia-dkms-390 nvidia-kernel-common-390 nvidia-kernel-source-390 nvidia-prime nvidia-settings nvidia-utils-390
  screen-resolution-extra x11-xkb-utils xcvt xfonts-base xfonts-encodings xfonts-utils xserver-common
  xserver-xorg-core xserver-xorg-video-nvidia-390
Suggested packages:
  xfs | xserver xfonts-100dpi | xfonts-75dpi xfonts-scalable
Recommended packages:
  libnvidia-compute-390:i386 libnvidia-decode-390:i386 libnvidia-encode-390:i386 libnvidia-ifr1-390:i386
  libnvidia-fbc1-390:i386 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libfontenc1 libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390 libnvidia-decode-390 libnvidia-encode-390
  libnvidia-fbc1-390 libnvidia-gl-390 libnvidia-ifr1-390 libxcvt0 libxfont2 libxnvctrl0 nvidia-compute-utils-390
  nvidia-dkms-390 nvidia-driver-390 nvidia-kernel-common-390 nvidia-kernel-source-390 nvidia-prime nvidia-settings
  nvidia-utils-390 screen-resolution-extra x11-xkb-utils xcvt xfonts-base xfonts-encodings xfonts-utils xserver-common
  xserver-xorg-core xserver-xorg-video-nvidia-390
0 upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/60.4 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package libfontenc1:amd64.
(Reading database ... 135043 files and directories currently installed.)
Preparing to unpack .../00-libfontenc1_1%3a1.1.8-1build1_amd64.deb ...
Unpacking libfontenc1:amd64 (1:1.1.8-1build1) ...
Selecting previously unselected package libnvidia-cfg1-390.
Preparing to unpack .../01-libnvidia-cfg1-390_390.157-0ubuntu7_amd64.deb ...
Unpacking libnvidia-cfg1-390 (390.157-0ubuntu7) ...
Selecting previously unselected package libnvidia-common-390.
Preparing to unpack .../02-libnvidia-common-390_390.157-0ubuntu7_all.deb ...
Unpacking libnvidia-common-390 (390.157-0ubuntu7) ...
Selecting previously unselected package libnvidia-compute-390:amd64.
Preparing to unpack .../03-libnvidia-compute-390_390.157-0ubuntu7_amd64.deb ...
Unpacking libnvidia-compute-390:amd64 (390.157-0ubuntu7) ...
Selecting previously unselected package libnvidia-decode-390:amd64.
Preparing to unpack .../04-libnvidia-decode-390_390.157-0ubuntu7_amd64.deb ...
Unpacking libnvidia-decode-390:amd64 (390.157-0ubuntu7) ...
Selecting previously unselected package libnvidia-encode-390:amd64.
Preparing to unpack .../05-libnvidia-encode-390_390.157-0ubuntu7_amd64.deb ...
Unpacking libnvidia-encode-390:amd64 (390.157-0ubuntu7) ...
Selecting previously unselected package libnvidia-fbc1-390:amd64.
Preparing to unpack .../06-libnvidia-fbc1-390_390.157-0ubuntu7_amd64.deb ...
Unpacking libnvidia-fbc1-390:amd64 (390.157-0ubuntu7) ...
Selecting previously unselected package libnvidia-gl-390:amd64.
Preparing to unpack .../07-libnvidia-gl-390_390.157-0ubuntu7_amd64.deb ...
Unpacking libnvidia-gl-390:amd64 (390.157-0ubuntu7) ...
Selecting previously unselected package libnvidia-ifr1-390:amd64.
Preparing to unpack .../08-libnvidia-ifr1-390_390.157-0ubuntu7_amd64.deb ...
Unpacking libnvidia-ifr1-390:amd64 (390.157-0ubuntu7) ...
Selecting previously unselected package libxcvt0:amd64.
Preparing to unpack .../09-libxcvt0_0.1.2-1build1_amd64.deb ...
Unpacking libxcvt0:amd64 (0.1.2-1build1) ...
Selecting previously unselected package libxfont2:amd64.
Preparing to unpack .../10-libxfont2_1%3a2.0.6-1build1_amd64.deb ...
Unpacking libxfont2:amd64 (1:2.0.6-1build1) ...
Selecting previously unselected package libxnvctrl0:amd64.
Preparing to unpack .../11-libxnvctrl0_510.47.03-0ubuntu4_amd64.deb ...
Unpacking libxnvctrl0:amd64 (510.47.03-0ubuntu4) ...
Selecting previously unselected package nvidia-compute-utils-390.
Preparing to unpack .../12-nvidia-compute-utils-390_390.157-0ubuntu7_amd64.deb ...
Unpacking nvidia-compute-utils-390 (390.157-0ubuntu7) ...
Selecting previously unselected package nvidia-kernel-source-390.
Preparing to unpack .../13-nvidia-kernel-source-390_390.157-0ubuntu7_amd64.deb ...
Unpacking nvidia-kernel-source-390 (390.157-0ubuntu7) ...
Selecting previously unselected package nvidia-kernel-common-390.
Preparing to unpack .../14-nvidia-kernel-common-390_390.157-0ubuntu7_amd64.deb ...
Unpacking nvidia-kernel-common-390 (390.157-0ubuntu7) ...
Selecting previously unselected package nvidia-dkms-390.
Preparing to unpack .../15-nvidia-dkms-390_390.157-0ubuntu7_amd64.deb ...
Unpacking nvidia-dkms-390 (390.157-0ubuntu7) ...
Selecting previously unselected package nvidia-utils-390.
Preparing to unpack .../16-nvidia-utils-390_390.157-0ubuntu7_amd64.deb ...
Unpacking nvidia-utils-390 (390.157-0ubuntu7) ...
Selecting previously unselected package x11-xkb-utils.
Preparing to unpack .../17-x11-xkb-utils_7.7+8build2_amd64.deb ...
Unpacking x11-xkb-utils (7.7+8build2) ...
Selecting previously unselected package xserver-common.
Preparing to unpack .../18-xserver-common_2%3a21.1.12-1ubuntu1_all.deb ...
Unpacking xserver-common (2:21.1.12-1ubuntu1) ...
Selecting previously unselected package xserver-xorg-core.
Preparing to unpack .../19-xserver-xorg-core_2%3a21.1.12-1ubuntu1_amd64.deb ...
Unpacking xserver-xorg-core (2:21.1.12-1ubuntu1) ...
Selecting previously unselected package xserver-xorg-video-nvidia-390.
Preparing to unpack .../20-xserver-xorg-video-nvidia-390_390.157-0ubuntu7_amd64.deb ...
Unpacking xserver-xorg-video-nvidia-390 (390.157-0ubuntu7) ...
Selecting previously unselected package nvidia-driver-390.
Preparing to unpack .../21-nvidia-driver-390_390.157-0ubuntu7_amd64.deb ...
Unpacking nvidia-driver-390 (390.157-0ubuntu7) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../22-nvidia-prime_0.8.17.2_all.deb ...
Unpacking nvidia-prime (0.8.17.2) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../23-screen-resolution-extra_0.18.3_all.deb ...
Unpacking screen-resolution-extra (0.18.3) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../24-nvidia-settings_510.47.03-0ubuntu4_amd64.deb ...
Unpacking nvidia-settings (510.47.03-0ubuntu4) ...
Selecting previously unselected package xcvt.
Preparing to unpack .../25-xcvt_0.1.2-1build1_amd64.deb ...
Unpacking xcvt (0.1.2-1build1) ...
Selecting previously unselected package xfonts-encodings.
Preparing to unpack .../26-xfonts-encodings_1%3a1.0.5-0ubuntu2_all.deb ...
Unpacking xfonts-encodings (1:1.0.5-0ubuntu2) ...
Selecting previously unselected package xfonts-utils.
Preparing to unpack .../27-xfonts-utils_1%3a7.7+6build3_amd64.deb ...
Unpacking xfonts-utils (1:7.7+6build3) ...
Selecting previously unselected package xfonts-base.
Preparing to unpack .../28-xfonts-base_1%3a1.0.5+nmu1_all.deb ...
Unpacking xfonts-base (1:1.0.5+nmu1) ...
Setting up nvidia-prime (0.8.17.2) ...
Setting up nvidia-kernel-common-390 (390.157-0ubuntu7) ...
update-initramfs: deferring update (trigger activated)
Setting up x11-xkb-utils (7.7+8build2) ...
Setting up libxnvctrl0:amd64 (510.47.03-0ubuntu4) ...
Setting up libfontenc1:amd64 (1:1.1.8-1build1) ...
Setting up nvidia-kernel-source-390 (390.157-0ubuntu7) ...
Setting up xfonts-encodings (1:1.0.5-0ubuntu2) ...
Setting up libnvidia-compute-390:amd64 (390.157-0ubuntu7) ...
Setting up screen-resolution-extra (0.18.3) ...
Setting up libnvidia-common-390 (390.157-0ubuntu7) ...
Setting up libxcvt0:amd64 (0.1.2-1build1) ...
Setting up nvidia-settings (510.47.03-0ubuntu4) ...
Setting up nvidia-utils-390 (390.157-0ubuntu7) ...
Setting up xserver-common (2:21.1.12-1ubuntu1) ...
Setting up libnvidia-fbc1-390:amd64 (390.157-0ubuntu7) ...
Setting up nvidia-compute-utils-390 (390.157-0ubuntu7) ...
info: The home dir /nonexistent you specified can't be accessed: No such file or directory


info: Selecting UID from range 100 to 999 ...


info: Selecting GID from range 100 to 999 ...
info: Adding system user `nvidia-persistenced' (UID 113) ...
info: Adding new group `nvidia-persistenced' (GID 112) ...
info: Adding new user `nvidia-persistenced' (UID 113) with group `nvidia-persistenced' ...
info: Not creating `/nonexistent'.
Setting up libxfont2:amd64 (1:2.0.6-1build1) ...
Setting up libnvidia-cfg1-390 (390.157-0ubuntu7) ...
Setting up nvidia-dkms-390 (390.157-0ubuntu7) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-390.157 DKMS files...
Building for 6.8.0-47-generic
Building for architecture x86_64
Building initial module for 6.8.0-47-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-390.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-47-generic (x86_64)
Consult /var/lib/dkms/nvidia/390.157/build/make.log for more information.
dpkg: error processing package nvidia-dkms-390 (--configure):
 installed nvidia-dkms-390 package post-installation script subprocess returned error exit status 10
Setting up libnvidia-decode-390:amd64 (390.157-0ubuntu7) ...
Setting up libnvidia-gl-390:amd64 (390.157-0ubuntu7) ...
Setting up xserver-xorg-core (2:21.1.12-1ubuntu1) ...
Setting up xfonts-utils (1:7.7+6build3) ...
Setting up libnvidia-encode-390:amd64 (390.157-0ubuntu7) ...
Setting up xcvt (0.1.2-1build1) ...
Setting up xfonts-base (1:1.0.5+nmu1) ...
dpkg: dependency problems prevent configuration of nvidia-driver-390:
 nvidia-driver-390 depends on nvidia-dkms-390 (<= 390.157-1); however:
  Package nvidia-dkms-390 is not configured yet.
 nvidia-driver-390 depends on nvidia-dkms-390 (>= 390.157); however:
  Package nvidia-dkms-390 is not configured yet.


dpkg: error processing package nvidia-driver-390 (--configure):
 dependency problems - leaving unconfigured
Setting up libnvidia-ifr1-390:amd64 (390.157-0ubuntu7) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up xserver-xorg-video-nvidia-390 (390.157-0ubuntu7) ...
Processing triggers for fontconfig (2.15.0-1.1ubuntu2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.3) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for initramfs-tools (0.142ubuntu25.4) ...
update-initramfs: Generating /boot/initrd.img-6.8.0-47-generic
Errors were encountered while processing:
 nvidia-dkms-390
 nvidia-driver-390
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@deepblue:~$ 
```

---

### Post by 1fallen on 2024-10-17
You should get better results with the [COLOR=#FFFFFF] GeForce GTX 1070 Ti with a newer driver.
Man those 550's fell off support quickly. That 390 Driver is utter crap now currently.
[/COLOR]https://www.amazon.com/s?k=gtx+1070&language=en_US&crid=QZG8C6B1P5FW&linkCode=sl2&linkId=65476b67dcc10f00d25b320a1efa1b81&sprefix=gtx+1070%2Caps%2C191&tag=gpuspecs03-20&ref=as_li_ss_tl

I'm trying to keep up with all the changes Mike but it is hard to stay on my tiptoes....LOL

---

### Post by sgt-mike on 2024-10-17
LOL yes Rick it is.... but that is boredom from waiting on parts.... ONWARD to next project. (actually not yet I'm doing this while I wait on the NFS parts) 

OK a update on the GTX 550ti status I found success well kind of. Without boring folks I did get the drivers on However crashed. so I've come to the conclusion that it's a fools folly to pursue the GTX 550's for that purpose. just too old and no driver support. 


I pulled your link up nice ok so your thinking the GTX 1070 as well huh? 
The only question is are you running that card and transcoding? if so how was the driver /cuda install for you?

Honestly from what I seen from Nvida driver site it didnt have the most cuda cores, but it did keep up with the top of the list. The plus side of that is it's probably best for just one to sit in there. I suspect that two would be pointless and a waste not sure if I could saturate the cores of just one. 

(just sharing a thought on that, I could swap the GPU's with the windows box..... Nah nix that would / could have to many issues, I only need to break one system at a time )

---

### Post by 1fallen on 2024-10-17
> **sgt-mike said:**
> 
I pulled your link up nice ok so your thinking the GTX 1070 as well huh? 
The only question is are you running that card and transcoding? if so how was the driver /cuda install for you?
No but I know some Devs that do, they have no reason to upgrade yet.
> **sgt-mike said:**
> 
Honestly from what I seen from Nvida driver site it didnt have the most cuda cores, but it did keep up with the top of the list. The plus side of that is it's probably best for just one to sit in there. I suspect that two would be pointless and a waste not sure if I could saturate the cores of just one. 


It will handle the 560 driver, and install should be painless, and Two would be pointless is an agreement with me. :)
EDIT: after thought, two would be nice if you wanted some KVM's with GPU passthrough 

The only thing I can think of on GPU end is a Newer card, but they are Gold now days.(an arm and both legs cost wise)

---

### Post by sgt-mike on 2024-10-17
> **1fallen2 said:**
> 
EDIT: after thought, two would be nice if you wanted some KVM's with GPU passthrough
That is a point I had not thought of

---

### Post by TheFu on 2024-10-17
I have not been impressed with the quality from HW-based transcoding from my Ryzen 5600G, which is much newer than your 550Ti.  Yes, it is faster. There isn't near enough control over the options, like a SW based encode provides and even exploding the files to be 2x leaves terrible artifacts in the resulting video files.  I tested using both h.264 and h.265 video encoding.  BTW, the speed that both run is about the same.

Still, I stopped using any HW-based transcoding except for live broadcasts.  The quality is just so bad.  I'm happy to use ffmpeg to transcode mpeg2 1080i video to h.264/h.265 1080i instead.  And for archival uses, I'll use handbrake to deal with the transcoding to h.265. The software transcodes generate output without any visual artifacts and usually with smaller files, often 75% smaller for the handbrake transcodes.  Of course, the SW based transcodes do take longer, but the h.264 codec is still fast at less than 20 minutes per hour of video.  The h.265 is between 1.2x and 2x the playback time, but but creates beautiful, small, files with a constant qualify of 20-21.  For h.264, I use a QC of 19.

Just to be very clear, the Ryzen integrated GPU transcoding never showed up in the CPU "top" and didn't appear to impact normal CPU workloads at all.  I didn't modify the BIOS to give the iGPU more RAM when I was testing.  Just followed the Jellyfin HW-Encoding guide and it worked with their modified ffmpeg binary. 

I haven't tried nVidia transcoding, so YMMV.  I heard years ago that Intel's iGPUs did a good job of transcoding, but never tested it.

Why do I bother with h.264 transcoding at all?  I use raspberry pi systems to watch videos.  They have built-in hardware decoding for h.264 and it works really well.  MPEG2 decoding is all done in software and while one of my Pis does transcoding of h.265 in hardware, the other one doesn't - and h.265 playback (or VP9) will end up with SW-based decoding, which usually fails and locks up the playback.  The Pi connected to our projection system does handle h.265 decoding in hardware, so any I'm willing to having movies archived in that vcodec knowing that playback using other devices will require on-the-fly h.265 to h.264 transcoding which Jellyfin will do in hardware ... with not-so-great results.

I've probably blabbed too much.

---

### Post by sgt-mike on 2024-10-18
nope you didn't blab too much for my information. I was hoping you would weigh in here. Good information you bring to the table. 

On handbrake I'm using the GTX 1070 founders edition and it greatly reduces the load on that 4th Gen i7 (4770K) processer, of course I maxed the ram out because of Win 10. With handbrake on that GTX 1070 never saturates the GPU and takes a lot off the CPU. 

In some of my research others have echoed what you stated about the quality of playback. I was hoping that you might have located a Radeon that actually works well in the decode area. 

The Server (i7 3rd gen 3770K) that I'm sticking this in is running Jellyfin as well , so your input is greatly in line with what I'm doing. Right now because of the drivers the 550Ti's are not engaged into HW decoding. Although the i7 has a iGPU which does work to a small degree it's not fully capable of h256. 

Intel GPU's heard the same even the low end they claim to work well.

---

### Post by TheFu on 2024-10-18
Decoding for playback isn't any issue.  It is the encoding using the hardware that has poor quality.  I'm running a test right now for you.
Recorded a TV show recently.
```

A. 6.9G    The_Summit-Snakes_and_Ladd-huge-mpg.mkv  <--- Commercials included 135:59 mpeg2/ac3 1080@29.97 fps 
B. **3.2G**    The_Summit-Snakes_and_Ladd-h.mkv   <--- Commercials removed 61:20 mpeg2/ac3 1080@29.97 fps
C. **3.1G**    The_Summit-Snakes_and_Ladd.mkv  <--- Commercials removed 61:20  h.264/vorbis 1080@29.97 fps 
D. **3.7G**    The_Summit-Snakes_and_Ladd-h.mkv-hevc-longhw.mkv  <--- Commercials removed 61:20 hevc/vorbis 1080@29.97 fps 
E. **3.2G**    The_Summit-Snakes_and_Ladd-h.mkv-longhw.mkv <--- Commercials removed 61:20 h.264/vorbis 1080@29.97 fps

```
_A_ is the original recording put into an mkv container. It was actually a .ts file. For the show, an extra 45 min is recorded due to live sports sometimes shifting all shows later. 
_B_ is the original recording with all commercials removed and the extra 45 min from the following show cut.  Typically, commercials add 50% to the file size and about 30% more time.  A 1 hour show is 20 minutes of commercials, so removing commercials saves 20 minutes/hour.
_C_ is the Handbrake transcode to h.264/vorbis/mkv container. Transcode time about 22 min. File size for 1080 videos is never great. The resulting video is beautiful. No artifacts at all.  According to mediainfo, the overall bitrate is 7,055 kb/s
_D_ is the HW encoding to hevc/vorbis/mkv using the Ryzen 5600G iGPU.  Transcode time is 4.2x real time. About 15 min. 
```
frame=109704 fps=124 q=-0.0 Lsize= 3809198kB time=01:01:20.81 bitrate=8477.7kbits/s dup=0 drop=490 **speed=4.16x**    
video:3575544kB audio:228968kB subtitle:95kB other streams:0kB global headers:13kB muxing overhead: 0.120711%

real    **14m45.889s**
user    2m32.698s
sys     0m18.171s
```
The file is actually larger than the source to avoid video artifacts and yet it is still a little jumpy, unlike the smooth playback from the source.  I spent about a week looking for the best settings to be used with the HW encoder. Mostly the video profile and Mbps control quality.
```
    nice /usr/lib/jellyfin-ffmpeg/ffmpeg \
          -hwaccel vaapi \
          -hwaccel_device /dev/dri/renderD128 \
          -hwaccel_output_format vaapi \
          -i  "${file}" \
          -map 0 \
          -vf 'scale_vaapi=format=p010' \
          -c:v **hevc_vaapi** -profile:v 2 -b:v 8M \
          -c:a libvorbis -q:a 6 \
        "${new}-hevc-longhw.mkv"
```
According to mediainfo, the overall bitrate is 8,478 kb/s

_E_ is the HW encoding to h.264/vorbis/mkv using the Ryzen 5600G iGPU. It is currently running a 4.15x, so basically the same as the hevc HW encode. In general, since the h.264 and h.265 encodes take the same runtime, there's little reason to use the less efficient h.264 mode.  
```
frame=109704 fps=123 q=-0.0 Lsize= 3343968kB time=01:01:20.81 bitrate=7442.3kbits/s dup=0 drop=490 **speed=4.14x**    
video:3110317kB audio:228968kB subtitle:95kB other streams:0kB global headers:13kB muxing overhead: 0.137431%

real    **14m49.422s**
user    2m31.874s
sys     0m17.059s

```

The command used:
```
    nice /usr/lib/jellyfin-ffmpeg/ffmpeg \
          -hwaccel vaapi \
          -hwaccel_device /dev/dri/renderD128 \
          -hwaccel_output_format vaapi \
          -i  "${file}" \
          -map 0 \
          -vf 'scale_vaapi=-2:1080' \
          -c:v **h264_vaapi**  -b:v 7M  -maxrate 8M \
          -c:a libvorbis -q:a 6 \
        "${new}-longhw.mkv"
```
According to mediainfo, the overall bitrate is 7,442 kb/s

To be fair, this type of show with vast landscapes of sky, mountains, water, and subtle shades of green is really tough on encoders, so more bits are always required to maintain quality.  Think _Lord of the Rings_ mountains as what most of the show has.   As I said before, the iGPU utilization doesn't impact regular CPU use that I can see.  ffmpeg with HW encoding uses less than 20% of 1 core.  Handbrake pegs all cores at 100%.

Remember, there are different goals for each type of encoding.  The HW encodes place speed and qualify over file size.  I don't intend to save those files forever, so I'm much less sensitive to file size and just want something that plays back on my player devices without any artifacts as the primary goal.  
Handbrake encodes are for files I plan to keep forever.  Typically, I'll encode using hevc, not h.264 with handbrake, since those file sizes for the same quality will be 50% smaller, but in my example above, I used h.264 because this is a TV show that won't be archived.  It is a watch-once show.

---

