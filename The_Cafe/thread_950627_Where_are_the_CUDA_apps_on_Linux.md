---
title: "Where are the CUDA apps on Linux"
date: 2008-10-17
forum: The Cafe
---

### Post by regomodo on 2008-10-17
#

---

### Post by ssam on 2008-10-17
[http://www.hep.manchester.ac.uk/gpmad/](http://www.hep.manchester.ac.uk/gpmad/)

(I share an office with one of the devs :-) )

---

### Post by regomodo on 2008-10-17
#

---

### Post by regomodo on 2008-10-18
#

---

### Post by MTTR on 2008-12-09
NV should fund some good programmers to get support into some of the biggest number crunchers (ffmpeg, IDS, databasing, etc). I can't imagine they would have to spend a fortune before more of the SOHO/DIY groups started jumping onto the sub-$200 products.

In retrospect I always imagined a flash/CPU/RAM/FPGA PCI package that would allow rapid programming and offloading at consumer prices. Looks like dreams are coming true, but ffmpeg is the dealbreaker IMO. :p

Regards

---

### Post by Polygon on 2008-12-09
> **regomodo said:**
> Ah, so somebody has done something with CUDA on Linux then. I've just installed the CUDA SDKand toolkit on windows xp. Damn, that is some seriously impressive stuff. The computing capabilities are crazy.

its not that we dont care, its just the fact that, hey! windows has 90% of the marketshare! of course they have all the cuda apps at the moment, because those developers most likely use windows. 

don't worry, in time we will get some, although i don't really want seperate applications, but rather integration with current applications. Ripping a dvd with handbrake + cuda, or transcoding a video with avidemux + cuda would be awesome. Hell, even distributed computing programs like folding@home and all teh BOINC projects could greatly benefit from this. Be patient =)

---

### Post by Eclipse. on 2008-12-09
> **regomodo said:**
> So nobody cares for the lack of CUDA apps in Linux. Windows gets all the good apps.

Feel free to code some yourself.:p

I'm pretty sure there will be some CUDA related projects out there.

---

### Post by Swagman on 2008-12-09
Only thing I want it for is crunching Rosetta

---

### Post by MTTR on 2008-12-10
FWIW I am no expert at these things but here are a couple cool ideas (no idea on the viability):

ARCH module to extend CPU capabilities (similar to math coprocessor?) Perhaps ASMP (asymmetrical multiprocessing).

A debugger to CUDA compiler for attaching to running sections of existing code and build portions of offload machine code. Maybe realtime with some serious -fu, more probable would be either threshhold detection or user initiated.

All of this would probably require a lot of co-op between the CPU and GPU, but maybe some of this has already been accomplished elsewhere?

---

### Post by peterhoeg on 2009-02-19
> **Polygon said:**
> its not that we dont care, its just the fact that, hey! windows has 90% of the marketshare! of course they have all the cuda apps at the moment, because those developers most likely use windows. 

don't worry, in time we will get some, although i don't really want seperate applications, but rather integration with current applications. Ripping a dvd with handbrake + cuda, or transcoding a video with avidemux + cuda would be awesome. Hell, even distributed computing programs like folding@home and all teh BOINC projects could greatly benefit from this. Be patient =)
BOINC is already using CUDA: [http://boinc.berkeley.edu/cuda.php](http://boinc.berkeley.edu/cuda.php) and claiming "These applications run from 2X to 10X faster than the CPU-only version.".

So we're getting there.

---

### Post by Polygon on 2009-02-20
also, i heard that if you use like distributed computing apps with CUDA, it SEVERELY lags your computer.Since your gpu is spending all of its power doing stuff for whatever program, it doesnt have enough time to actually render whats going on in the screen

the only way i see that working is if you leave your computer on 24/7 and that wastes electricity and defeats the purpose of the whole thing (using spare cpu cycles while your actually using the computer)

---

### Post by ladasky on 2009-09-06
> **Polygon said:**
> also, i heard that if you use like distributed computing apps with CUDA, it SEVERELY lags your computer.Since your gpu is spending all of its power doing stuff for whatever program, it doesnt have enough time to actually render whats going on in the screen

the only way i see that working is if you leave your computer on 24/7 and that wastes electricity and defeats the purpose of the whole thing (using spare cpu cycles while your actually using the computer)

There's no way to tell a CUDA-enabled graphics card to reserve a fraction of its GPU's for video under all circumstances?
 
Speaking for myself, leaving a computer on overnight to crunch numbers would be a practical option.  And with enough GPU's working on an "embarrassingly parallel" computation problem, I can't see how you would not expect significant performance gains over a single CPU.

---

### Post by gletob on 2009-09-06
> **Polygon said:**
> also, i heard that if you use like distributed computing apps with CUDA, it SEVERELY lags your computer.Since your gpu is spending all of its power doing stuff for whatever program, it doesnt have enough time to actually render whats going on in the screen

the only way i see that working is if you leave your computer on 24/7 and that wastes electricity and defeats the purpose of the whole thing (using spare cpu cycles while your actually using the computer)

I know that wasting electricity creates more pollution and stuff.  But frankly, It's my personal preference to leave my systems on 24/7, why I don't know but it's my choice.  I pay for the electricity, and I'm sorry that it causes pollution but oh well.  And why would that defeat the purpose?  Your still doing something for a good cause, I leave F@H running all night.  The F@H project is geared at cures to cancer, AIDS, parkinsons, huntingtons, etc.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-06
I  hope that more BOINC projects add CUDA compatibility

---

### Post by bear24rw on 2009-09-06
I too are eaglerly awaiting mass cuda adoption in programs, there already are some linux programs that use it. BackTrack-4 has built in cuda support with some password crackers that use it

---

### Post by Paqman on 2009-09-12
> **Polygon said:**
> also, i heard that if you use like distributed computing apps with CUDA, it SEVERELY lags your computer.

BOINC can be told to only crunch while your machine is idle. So whenever you're away from the keyboard for a few minutes, it does it's thing. Works really well for me.

> 
the only way i see that working is if you leave your computer on 24/7 and that wastes electricity and defeats the purpose of the whole thing (using spare cpu cycles while your actually using the computer)

Personally i'd recommend switching your electricity supply to a renewable source if you're going to get into 24/7 distributed computing.

---

### Post by andy16666 on 2009-10-14
I actually know of one CUDA app for Linux. It's a 3D modelling program called k3d. 

[http://www.k-3d.org/wiki/Main_Page](http://www.k-3d.org/wiki/Main_Page)

---

### Post by 3rdalbum on 2009-10-14
I think a lot of developers are holding off writing CUDA code that's Nvidia-only, when they could soon write OpenCL code that will work on ATI and possibly Intel as well.

---

### Post by Jekshadow on 2009-10-16
Aircrack-ng is out for CUDA, so is a nice hash bruteforcer called CUDA-Multiforcer. The dev says he's going to release Multiforcer under an Open Source License soon.

---

### Post by andy16666 on 2009-10-18
I agree that OpenCL will eventually supplant the vendor specific APIs like CUDA. Mainly apps written now in CUDA are ones that will benefit a lot from it (scientific, professional graphics) and don't want to wait for OpenCL to become standard.

---

### Post by regomodo on 2009-10-21
#

---

### Post by avilella on 2009-12-11
There is also CUDA-enabled VDPAU apps like mplayer or xine-lib here:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by toupeiro on 2009-12-11
Simply put, CUDA is impressive but proprietary. :)  Some people simply prefer not to lock themselves into something which may merge with something else or go away alltogether.  OpenCL is vendor neutral.

---

### Post by GatoLoko on 2009-12-16
> **avilella said:**
> There is also CUDA-enabled VDPAU apps like mplayer or xine-lib here:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

VDPAU has nothing to do with CUDA.

CUDA uses the GPU Shader processor for general purposes.
VDPAU uses the GPU PureVideo processor for video decoding.

---

### Post by Keyper7 on 2009-12-16
> **toupeiro said:**
> Simply put, CUDA is impressive but proprietary. :)  Some people simply prefer not to lock themselves into something which may merge with something else or go away alltogether.  OpenCL is vendor neutral.

Exactly.

For a lot of people, requiring NVIDIA is quite a dealbreaker.

---

### Post by ordinareez on 2009-12-23
Ocelot, an open source CUDA compiler, just released [http://developers.slashdot.org/story/09/12/23/191207/An-Open-Source-Compiler-From-CUDA-To-X86-Multicore](http://developers.slashdot.org/story/09/12/23/191207/An-Open-Source-Compiler-From-CUDA-To-X86-Multicore)

hmm what do you think about it?

---

### Post by linuxyogi on 2011-06-02
The last post on this thread was on December 24th, 2009.

I am really trying to find out if CUDA is available for Linux.

If anyone has any info please share.

PureVideo = VDPAU
CUDA =   :(

---

### Post by CharlesA on 2011-06-02
Major necro. It would be better to start a new thread.

Closed.

---

