---
title: "What do you think of OpenCL?"
date: 2009-08-28
forum: The Cafe
---

### Post by billdotson on 2009-08-28
What do you think of Apple's OpenCL? From what I understand it is a way to utilize the power of a GPU in addition to the normal CPU for any application coded to do so. This is a change from the normal way of doing things where the graphics cards only did "graphics stuff".

I may be wrong but I seem to see somewhere that this had something to do with OpenGL and OpenAL. Do you think OpenGL, OpenAL (and all the other sound, input, etc. stuff) in addition to OpenCL will be able to overtake MS DirectX and allow more applications (I guess specifically games and multimedia applications) to be cross-platform?

 Do you think this will catch on and will be widely used (as in more than OS X)? Do you think it is going to be a very useful technology or will it flop? From what I heard it sounded pretty cool to me. I just wish that someone other than Apple had developed it (they did develop it right?). Don't mean to offend any Apple fans out there but Apple developing it is almost as bad (in my opinion) as Microsoft making it. At least Apple is (appearing to) make it an open, cross-platform thing, I just wish a company I liked a bit more (like what previously used to be Sun Microsystems) had created this technology.

DISCUSS!

---

### Post by kernelhaxor on 2009-08-28
I don't know in detail .. From what I've heard and know, I think comparing OpenCL and DirectX is like comparing Apples and Oranges ..
DirectX has such a long history and has goals different than that of OpenCL I think ..  It's mainly aimed at providing APIs for multimedia and games related tasks while OpenCL like you said wants to utilize the power of GPU in addition to the normal CPU for any app coded to do so ..  I think in recent times even DirectX is moving in this direction too ..

Given the richness and such industry wide adoption of DirectX, I highly doubt even the combination you mentioned would overtake DirectX in adoption by games and multimedia application devs

---

### Post by Methuselah on 2009-08-28
OpenCL is a GPGPU framework, IIRC.
That's is, an API to allow general purpose computing tasks to be performed on the GPU across different architectures.

NVidia has their CUDA and ATI had their own framework (whose name now escapes me).
But as both are set to (or have provided) OpenCL drivers it would be possible to write software for GPUs without using platform specific APIs.

DirectX and OpenGL are pretty much strictly 3D APIs thogh they have been steadily allowing more programmability through shader scripts etc. as GPUs become more advanced.
I think we are going full circle (Doom etc. were written for fully programmable CPUs and now GPUs are steadily becoming more general purpose) but as of now, OpenGL and DirectX still have their niche, I think.
Eventually, it's is quite possible that more general APIs might become the standard way to write for GPUs to fully tap into their programmability.

Modern GPUs are immensely powerful, massively multi-core stream processors.
At peak throughput they usually dominate the CPUs at brute force computing tasks.
So there has been ongoing work to tap into their power for more than just graphics processing.
In the future they'll probably become more of a general purpose coprocessor, subsuming CPU SIMD units.

Check out AMD fusion:
[http://en.wikipedia.org/wiki/AMD_Fusion](http://en.wikipedia.org/wiki/AMD_Fusion)

And intel Larrabee
[http://en.wikipedia.org/wiki/Larrabee_(GPU](http://en.wikipedia.org/wiki/Larrabee_(GPU))

As you can see, I'm rather interested in these developments. :D

---

### Post by orlox on 2009-08-28
I'm enormously interested in openCL. I have seen some of the real time simulations they do in machines that aren't impressive, and I'm hoping to use this in some fluids simulations somewhere in the future. Hopefully, I will be able to do interesting stuff in a machine of my own.

(Just for the record...I haven't actually worked on serious fluid simulations, but I expect to do it in a not so far future)

---

### Post by MikeTheC on 2009-08-28
I seem to remember reading someplace that Nero has already adopted OpenCL, and that when you use it to do a video transcode for a typical movie, the process goes from several hours (which is what we're all used to, more-or-less) to like 30 minutes.

For tasks which are suited to GPU processing, the performance is supposed to be substantial.

---

### Post by MaxIBoy on 2009-08-28
This is what I know of openCL:

[LIST]
[*]It is a C-like language which is uniquely suited to massively parallel tasks.
[*]It is specified by the Khronos group, a consortium of companies including Apple, ATI, nVidia, and more. The Khronos group is the same organization behind openGL, openGL-ES, openVG, and more.
[*]The specification is released by Khronos, but this is just a description of the language and how it should behave. The actual implementation (code) is not released by the Khronos group, but each implementation needs to be approved by them.
[*]An advantage of this language is that it can be compiled to run on GPUs, however it could also run on CPUs, similar to OpenGL (although openGL is almost never run in software these days.)
[*]For "embarrassingly parallel" tasks, the language is superior because it unlocks the massively parallel computation abilities of GPUs. Especially for huge amounts of simultaneous floating-point operations.
[*]A beta-test nVidia Linux driver with openCL support has been leaked.
[*]openCL has been demonstrated on a Radeon HD 4000 series graphics card under Windows.
[*]Software (non-accelerated) implementations of openCL are already available, so openCL programs will at least be made to run on your computer, but they won't benefit from hardware acceleration.
[/LIST]

I hope this will receive more popularity than DirectX Compute (which comes out with DirectX 11.) [DirectCompute is technologically inferior to openCL]("http://www.xbitlabs.com/news/video/display/20090804231719_DirectX_Compute_Shaders_Less_Advanced_than_OpenCL_Head_of_Khronos_Group.html") according to some experts.

---

### Post by madjr on 2009-08-28
1 of the few things good from apple

---

### Post by billdotson on 2009-08-29
So do you think it is going to get wide-spread support (as in not only OS X and if it is on other platforms not having gimped functionality because the platform isn't OS X)? It sounds like a really big step forward in processing intensive tasks. I guess it won't really affect games too much as they already use the GPU.

---

### Post by madjr on 2009-08-29
> **billdotson said:**
> So do you think it is going to get wide-spread support (as in not only OS X and if it is on other platforms not having gimped functionality because the platform isn't OS X)? It sounds like a really big step forward in processing intensive tasks. I guess it won't really affect games too much as they already use the GPU.

yea already adopted by khronos

so it might even become part of openGL

---

### Post by sydbat on 2009-08-29
> **kernelhaxor said:**
> I don't know in detail .. From what I've heard and know, I think comparing OpenCL and DirectX is like **comparing Apples and Oranges** ..<snip>+1000 for the superb pun!!

---

### Post by MaxIBoy on 2009-08-29
> **madjr said:**
> so it might even become part of openGLThis I doubt. OpenGL is for graphics only, whereas DirectX has all kinds of other stuff besides Direct3D (for example, DirectSound.) OpenCL is completely unrelated to OpenGL and has very little to do with it, whereas DirectCompute has everything to do with DirectX.

---

### Post by Quentusrex on 2009-09-01
I'm really looking forward to testing this. I have 2 dev boxes just waiting to crash with the beta versions of opencl implementations.

---

### Post by madjr on 2009-09-01
when is this coming to linux?

i want my kde/firefox/openoffice to use my gpu and work a lot faster

---

### Post by billdotson on 2009-09-01
So OpenCL could be used with OpenGL games? I would love to see DirectX dethroned. Then Microsoft would have to release a giant update to unbork OpenGL on Vista or else everyone wouldn't be able the play their brand new OpenGL and OpenCL games. I can dream can't I?

---

### Post by ssam on 2009-09-01
> **madjr said:**
> when is this coming to linux?

soon
[http://www.phoronix.com/scan.php?page=news_item&px=NzQ5Mw](http://www.phoronix.com/scan.php?page=news_item&px=NzQ5Mw)

> **madjr said:**
> 
i want my kde/firefox/openoffice to use my gpu and work a lot faster
it probably wont make much difference.

parallel processing works well when a task can be broken into little pieces. for image processing you can split an image into tiles/pixels, and apply the same algorithm to each. for video/audio encoding/decoding, you can split the file up into short sections, and deal with each independently.

---

