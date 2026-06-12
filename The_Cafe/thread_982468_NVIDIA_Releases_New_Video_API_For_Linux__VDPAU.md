---
title: "NVIDIA Releases New Video API For Linux : VDPAU"
date: 2008-11-14
forum: The Cafe
---

### Post by Jags_FL on 2008-11-14
from the Slashdot article:

"Phoronix is reporting on a new Linux driver nVidia is about to release that [**brings PureVideo features to Linux**]("http://www.phoronix.com/vr.php?view=13102"). 

This new API is named VDPAU, and is described as: 'The Video Decode and Presentation API for Unix (VDPAU) provides a complete solution for decoding, post-processing, compositing, and displaying compressed or uncompressed video streams. 

These video streams may be combined (composited) with bitmap content, to implement OSDs and other application user interfaces."

Nvidia Link : [HTML]ftp://download.nvidia.com/XFree86/vdpau/doxygen/html/index.html[/HTML]

---

### Post by tbroderick on 2008-11-15
Nice to see the Linux drivers catching up with Windows ones.

---

### Post by MaxIBoy on 2008-11-15
The thread title scared me for a moment. I was thinking that there would soon be "nVidia only" video formats.


As long as the specifications are open, this is a fantastic development.

---

### Post by eternalnewbee on 2008-11-15
How does this release affect me?
I have a 7300GT card.

---

### Post by Jags_FL on 2008-11-15
@ eternalnewbee

excerpts from the Phoronix article:

"This driver adds a new VDPAU API, which provides [**PureVideo**]("http://www.nvidia.com/page/purevideo.html")-like features on Linux, adds in CUDA 2.1 support, new workstation performance optimizations, X Render improvements, and other improvements.

VDPAU provides PureVideo-like features, which is a technology NVIDIA has embedded into their graphics cards for several generations now with the latest iteration being known as [**PureVideo HD**]("http://www.nvidia.com/page/purevideo_hd.html"). PureVideo is described by NVIDIA as providing ultra-smooth video, superb picture clarity, and precise, vivid colors on any display. The necessary header files, wrapper library, and library / driver files ship with this just-released 180.06 driver."

Related article, aslo from Phoronix : [**NVIDIA VDPAU Benchmarks**]("http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1")

---

### Post by eternalnewbee on 2008-11-15
Thanks for the info Jags_FL. Have you installed it? If yes, could you tell me how you did it?

---

### Post by FuturePilot on 2008-11-15
A list of supported GPUs is at the bottom of this post
[http://www.nvnews.net/vbulletin/showthread.php?t=123091]("http://www.nvnews.net/vbulletin/showthread.php?t=123091")

Also it's worth noting that as of right now no video players can take advantage of this...yet :)

---

### Post by 3rdalbum on 2008-11-15
Oh good. It's not like Nvidia's drivers don't already cause problems with video playback already without them taking on the decoding load too!

---

### Post by handy on 2008-11-15
No problem for me, my 7950gt isn't supported anyway. :-)

---

### Post by ssam on 2008-11-15
a shame they could not help out with galium GPU Video Decoding.
[http://en.wikipedia.org/wiki/Gallium3D](http://en.wikipedia.org/wiki/Gallium3D)
[http://tech.slashdot.org/tech/08/07/11/1210224.shtml](http://tech.slashdot.org/tech/08/07/11/1210224.shtml)

---

### Post by Sealbhach on 2008-11-15
So will this make it into Ubuntu repos at some stage? Maybe in Jaunty?


.

---

### Post by Martje_001 on 2008-11-15
> **Sealbhach said:**
> So will this make it into Ubuntu repos at some stage? Maybe in Jaunty?


.
Depends on when Nvidia releases the final (not beta) driver.

In a short while we'll have decoding acceleration [AMD/ATi](http://www.phoronix.com/scan.php?page=article&item=amd_xvmc_xvba&num=1) and Nvidia =)

---

### Post by EdThaSlayer on 2008-11-15
Can't wait till this comes out. At the moment I'm stuck to the SGI driver(the one that everyone gets out of the box) with my Kubuntu 8.10. Hopefully in 9.04 I will be able to have the Nvidia drivers installed and have a great experience when it comes to the 2d, and video rendering. Glad I got a 9500m. :)

---

### Post by Jags_FL on 2008-11-15
@ eternalnewbee

No I haven't installed the new Nvidia driver 180.06 as my GPU is not supported.

From [**the  link**]("http://www.nvnews.net/vbulletin/showthread.php?t=123091") 'FuturePilot' provided, here's the current list of VDPAU supported Nvidia GPUs :

Desktop GPUs:
GeForce 200 Series
GeForce 9 Series
GeForce 86xx Series
GeForce 85xx Series
GeForce 84xx Series
GeForce 8300 GS
GeForce 8800 GTS 512
GeForce 8800 GT
GeForce 8800 GS

Mobile GPUs:
GeForce 98xxM
GeForce 9700M
GeForce 96xxM
GeForce 9500M
GeForce 9300M
GeForce 9200M
GeForce 8800M
GeForce 8800M GTS
GeForce 8800M GTX
GeForce 8600M
GeForce 8400M

Motherboard GPUs:
GeForce 9400
GeForce 9300
GeForce 9100
GeForce 8300
GeForce 8200

---

### Post by eternalnewbee on 2008-11-15
So mine isn't supported either...

---

### Post by Jags_FL on 2008-11-16
@ eternalnewbee

sorry pal same here... it would be great if someone who have tried this new 180.06 drivers can report if its playing video any better

On my desktop (Intel 2.8 GHZ HT, 2.5 GB RAM, GeForce FX 5200 128 MB) VLC freezes alott playing .mkv files and eventually gives up after 10 min or so...

---

### Post by eragon100 on 2008-11-16
> **Jags_FL said:**
> @ eternalnewbee

sorry pal same here... it would be great if someone who have tried this new 180.06 drivers can report if its playing video any better

On my desktop (Intel 2.8 GHZ HT, 2.5 GB RAM, GeForce FX 5200 128 MB) VLC freezes alott playing .mkv files and eventually gives up after 10 min or so...

If you have an fx5200, you can forget it. It doesn't and won't support anything older than a GeForce 8.

---

### Post by mips on 2008-11-16
> **Jags_FL said:**
> 
sorry pal same here... it would be great if someone who have tried this new 180.06 drivers can report if its playing video any better


How would one test to see if video runs better? Are there any benchmarking tools or is the eye good enough?

I have a 9600GT and access to the 180.06-1 beta driver in the Arch linux repo so I could test it but I would not know what to look for.

EDIT: If you have a good file to test with maybe pm with a link to it, as long it is not to big.

---

### Post by Jags_FL on 2008-11-16
@ eragon100

thanks for the reply and yes, I already know and also mentioned (along with the list of supported GPUs) the same in my earlier posts that the new Nvidia driver with VDPAU not gonna be supported on FX 5200.

@ mips

usually those .mkv are 4.5 GB in size  :(

---

### Post by mips on 2008-11-16
> **Jags_FL said:**
> 
@ mips

usually those .mkv are 4.5 GB in size  :(

I have not checked the sizes on all files but will these be ok, [http://www.matroska.org/samples/](http://www.matroska.org/samples/)

---

### Post by eragon100 on 2008-11-16
> **mips said:**
> How would one test to see if video runs better? Are there any benchmarking tools or is the eye good enough?

I have a 9600GT and access to the 180.06-1 beta driver in the Arch linux repo so I could test it but I would not know what to look for.

EDIT: If you have a good file to test with maybe pm with a link to it, as long it is not to big.

You can get 50 mb .mkv files for free from [www.bleachportal.net](www.bleachportal.net) :wink:

You can download the entire bleach anime there, just make a free account (I haven't had any spam mail from them, and I have been registered for a couple of weeks now)

You can directly download all episoded from their archive at hight speedd, and the first 160 episoded are all .mkv.

50 mb isn't too big, right?

---

### Post by Jags_FL on 2008-11-16
@ mips

> I have not checked the sizes on all files but will these be ok, [http://www.matroska.org/samples/](http://www.matroska.org/samples/)

the MKVs I was referring to were all 720p and usually they start freezing/legging after 5+ minutes while the link you mentioned have lesser than 720p. 

You can compare playback, before and after installing 180.06, for any HD content like this one:

Full HD _1080p_ trailer of new Bond movie Quantum of Solace :

```
http://ve3d.ign.com/videos/play/31520/PC/Quantum-of-Solace
```

---

### Post by mips on 2008-11-16
> **eragon100 said:**
> You can get 50 mb .mkv files for free from [www.bleachportal.net]("http://www.bleachportal.net") :wink:

You can download the entire bleach anime there, just make a free account (I haven't had any spam mail from them, and I have been registered for a couple of weeks now)

You can directly download all episoded from their archive at hight speedd, and the first 160 episoded are all .mkv.

50 mb isn't too big, right?

50MB is fine. 

I'm busy downloading episode one of bleach as well as about 50MB of sample files from the Matroska site.

---

### Post by mips on 2008-11-16
> **Jags_FL said:**
> 
Full HD _1080p_ trailer of new Bond movie Quantum of Solace :

```
http://ve3d.ign.com/videos/play/31520/PC/Quantum-of-Solace
```

Thanks, I just realised I already have the 1080p QoS movie trailer as well as Happy feet one.

---

### Post by mips on 2008-11-16
Feedback

Just installing the 180.06 driver provides no noticeable performance difference in the video quality or cpu usage. Tested in Dragon Player, SMPlayer & VLC

The application obviously does not know about VDPAU

I'm going to 'try' and patch mplayer to support VDPAU to see what gives.

EDIT: I cannot get the patched mplayer to build, will have to figure it out somehow.

---

### Post by mips on 2008-11-16
[http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1)

Above are benchmarks and they look good from a cpu usage perspective.

---

### Post by Jags_FL on 2008-11-16
Thanks mips.

OK, so we need apps to support/utilize VDPAU. If there's noticeable difference and as per Phoronix benchmarks, there is, then app developers will soon start supporting VDPAU.

---

### Post by TomtheWombat on 2008-11-16
Why aren't they supporting older chipsets like the one on my nforce 630a motherboard.  I believe its a geforce 7050, and it does support PureVideo.

Why no driver support in linux?

---

### Post by cprofitt on 2008-11-16
That is odd that they do not support the 8800GTS 320

---

### Post by tbroderick on 2008-11-16
> **TomtheWombat said:**
> 
Why no driver support in linux?

Because VDPAU only supports the second generation of PureVideo. Maybe they will add the first generation in the future. Maybe not.

---

### Post by TomtheWombat on 2008-11-16
> **tbroderick said:**
> Because VDPAU only supports the second generation of PureVideo. Maybe they will add the first generation in the future. Maybe not.

VDPAU better work well enough for my girlfriend to notice.  It's going to be hard to explain a new video card, the htpc guts sprawled all over, and me swearing as I try to cram them all back into the case.

---

### Post by sensimilla on 2008-11-16
Cards earlier than the 8*** series can use XvMC acceleration with the NVIDIA driver, so they already have some GPU video acceleration. Later cards currently have no acceleration at all. 

For me this is a big issue as I have an 8800GT and my CPU (Athlon X2 3800) is not quite fast enough to properly play 720p h264, So I have to boot into windows to watch 720p video on my HDTV. :( 
I was seriously considering upgrading my MB/CPU just for this reason. Now I won't need to.

I have compiled the mplayer with the patches and the performance difference is amazing, mplayer uses just 4% of cpu playing the 1080 sample. At the moment it won't play much apart from the samples suggested in the readme but I'm sure this will be fixed in future releases and it will be supported by other video playback software.

I do wonder if this is in response to ATI providing gpu acceleration with it's latest drivers as NVIDIA have never said that they were planning to support video acceleration under linux with these newer cards.

here is a quick guide if you want to try it yourself.

First download and **install** the appropriate 180.06 Beta display driver.

[http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html)
[http://www.nvidia.com/object/linux_display_amd64_180.06.html](http://www.nvidia.com/object/linux_display_amd64_180.06.html)

then get the script which will download and build the patched version of mplayer.
```
wget ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3076399.tar.bz2
tar -xvf mplayer-vdpau-3076399.tar.bz2
cd mplayer-vdpau-3076399
```
install the dependencies for building mplayer
```
sudo apt-get install build-essential subversion
sudo apt-get build-dep mplayer
```
run the  download and build script, this will take a while.
```
sh checkout-patch-build.sh
```
Then checkout the README.txt for instructions on how to use it, and where to get the working sample clips.

if you get errors like video codec not found after compiling succesfully you may need delete the ~/.mplayer folder.

---

### Post by Jags_FL on 2008-11-17
> **sensimilla said:**
> the performance difference is amazing, mplayer uses just 4% of cpu playing the 1080 sample

that's awesome... so now VDPAU supported Nvidia GPUs will play 1080p / 720p x264 videos without burning CPU horsepower  :) 

(my lappy was getting so hott playing those 720p/x264 .MKVs, it'd shutoff in 20 some minutes)

---

### Post by sensimilla on 2008-11-17
> **Jags_FL said:**
> that's awesome... so now VDPAU supported Nvidia GPUs will play 1080p / 720p x264 videos without burning CPU horsepower  :) 

(my lappy was getting so hott playing those 720p/x264 .MKVs, it'd shutoff in 20 some minutes)

It could still be a problem for you as the GPU will be getting hot instead of CPU. However the GPU should be more effecient at decoding than the CPU, According to some benchmarks [here at Anandtech]("http://www.anandtech.com/printarticle.aspx?i=2977"). It looks like an 8600 uses about 65% of the power that a Core 2 Duo uses decoding H.264 (above idle that is, not total power) so it should help you some.

---

### Post by Jags_FL on 2008-11-17
@ sensimilla

my GPU (GeForce FX 5200) is not supported by new Nvidia 180.06 anyway :(

What I meant, for those VDPAU supported GPUs will use less CPU while playin video and hence probably (especially)laptops wouldn't get that hot... but 'Nvidia 84xx & 86xx GPUs getting too hot' issues are completely different from this CPU getting too hot because of 720p/x264 video playback.

All in all newer 8xxx series onward GPUs will see (major?) improvements.

---

### Post by Duranxl on 2008-11-17
I have a problem:
$ ./mplayer -vc ffh264vdpau -vo vdpau '/media/drv0/Documents and Settings/W/My Documents/My Videos/Dexter/Season 3/8.mkv'

[I]Forced video codec: ffh264vdpau
Cannot find codec matching selected -vo and video format 0x3[/I]1637661.

Then later:
*Video: no video*

I've downloaded the correct mplayer build and it patched succesfully, as far as i can tell
[http://ubuntuforums.org/showthread.php?t=984198](http://ubuntuforums.org/showthread.php?t=984198)

8600M GT @ 180.06 @ 64bit intrepid

i have 
$ sudo apt-get install build-essential subversion
$ sudo apt-get build-dep mplayer
as well

Thanks

---

### Post by sensimilla on 2008-11-17
> **Duranxl said:**
> 
[I]Forced video codec: ffh264vdpau
Cannot find codec matching selected -vo and video format 0x3[/I]1637661.
*Video: no video*


You need to delete the hidden **.mplayer** folder from your home directory. Possibly just deleteing the file **codecs.conf** from that folder should be enough.

---

### Post by Trail on 2008-11-18
Pretty exciting. I'm just waiting for the MPplayer patches to go mainstream. (Or I might just compile it myself if I get the time).

---

### Post by Duranxl on 2008-11-18
> **sensimilla said:**
> You need to delete the hidden **.mplayer** folder from your home directory. Possibly just deleteing the file **codecs.conf** from that folder should be enough.

Thanks, that fixed it.
However, when playing .wmv3 i get:
```
$ ./mplayer -vc ffwmv3vdpau -vo vdpau '/media/drv0/Documents and Settings/W/My Documents/My Videos/Amazing_Caves_1080.wmv'

Forced video codec: ffwmv3vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VDPAU accelerated codec.
Selected video codec: [ffwmv3vdpau] vfm: ffmpeg (FFmpeg WMV3/WMV9 (VDPAU))

Error at libvo/vo_vdpau.c:637
```

With .mkv i get
> $./mplayer -vc ffh264vdpau -vo vdpau '/media/drv0/Documents and Settings/W/My Documents/My Videos/Dexter/Season 3/8.mkv' 

Error at libvo/vo_vdpau.c:826

:(

---

### Post by noisymime on 2008-11-18
> **Duranxl said:**
> However, when playing .wmv3 i get:
```
$ ./mplayer -vc ffwmv3vdpau -vo vdpau '/media/drv0/Documents and Settings/W/My Documents/My Videos/Amazing_Caves_1080.wmv'

Forced video codec: ffwmv3vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VDPAU accelerated codec.
Selected video codec: [ffwmv3vdpau] vfm: ffmpeg (FFmpeg WMV3/WMV9 (VDPAU))

Error at libvo/vo_vdpau.c:637
```
There's the following note in the VDPAU readme docs:
"VC-1 support in NVIDIA's VDPAU implementation currently requires GeForce
9300 GS, GeForce 9200M GS, GeForce 9300M GS, or GeForce 9300M GS."
Given that those particular cards are pretty uncommon, chances are that you won't yet have WMV support

Driver 180.06 has a lot of problems playing anything but the samples, particularly mkv files. I highly recommend moving to 180.08 ([ftp://download.nvidia.com/XFree86/Linux-x86/180.08/](ftp://download.nvidia.com/XFree86/Linux-x86/180.08/)) which seems to have fixed some of the issues

---

### Post by Duranxl on 2008-11-18
> **noisymime said:**
> There's the following note in the VDPAU readme docs:
"VC-1 support in NVIDIA's VDPAU implementation currently requires GeForce
9300 GS, GeForce 9200M GS, GeForce 9300M GS, or GeForce 9300M GS."
Given that those particular cards are pretty uncommon, chances are that you won't yet have WMV support

Driver 180.06 has a lot of problems playing anything but the samples, particularly mkv files. I highly recommend moving to 180.08 ([ftp://download.nvidia.com/XFree86/Linux-x86/180.08/](ftp://download.nvidia.com/XFree86/Linux-x86/180.08/)) which seems to have fixed some of the issues
1) What does VC-1 have to do with .mkv & wmv3? I'm not using the VC-1 codec.
2) I'm on 180.08 right now and i still can't play 720p .mkv

---

### Post by noisymime on 2008-11-18
> **Duranxl said:**
> 1) What does VC-1 have to do with .mkv & wmv3? I'm not using the VC-1 codec.
2) I'm on 180.08 right now and i still can't play 720p .mkv

1) Correct me if I'm wrong, but I thought wmv3 used VC-1? [http://en.wikipedia.org/wiki/VC-1#WMV3](http://en.wikipedia.org/wiki/VC-1#WMV3)

2) Well it is still beta after all. 180.08 certainly improved things for me, although its far from perfect.

---

