---
title: "May have to upgrade the computer do to video editting I'm doing"
date: 2011-07-04
forum: The Cafe
---

### Post by nec207 on 2011-07-04
I'm thinking of getting the i5 or i7 as that is intel top of the line CPU but not sure if intel or AMD is better as AMD has the phenom 2 the Quad-core or the 6 core and it looks really good.
 
And 4 GB of RAM or 6 GB of RAM.There is some debate at ubuntuforums if one should get a good motherboard and good video card.Some members at ubuntuforums say good CPU and lots of RAM is better.
 
And a 20 minute video clip and size is 1.6 GB how long should it take.After using the video editing software it applies the effects and save the resoults on the hard-drive.If the computer is turn off all the video editing work will be lost and you will have to do it all over again.It is a 20 minute video clip and size is 1.6 GB after trimming the 20 minute to 18 minute it took well over a hour.That seems too long.

---

### Post by nec207 on 2011-07-05
Why did this thread get moved? I thought I posted in the section with hardware and desktop computers?

---

### Post by Elfy on 2011-07-05
Nope - just checked the Edit history - no move details. I can move it now if you want - where to?

---

### Post by wizard10000 on 2011-07-05
Best bang for the buck if you're doing video editing right now is a Core i5-2500k.  I have a slightly overclocked Core i7-920 that makes pretty short work of rendering video and the i5 might even be a little quicker than my i7.

---

### Post by Swagman on 2011-07-05
lol

I started NLE on a P2 @ 300mhz with just 512mb Ram and a 4gb scsi 2 fast & wide hard drive (on Win95)

---

### Post by forrestcupp on 2011-07-05
These are my _opinions_ from my current research on this. The raw processing power of an AMD Phenom II true quad core outperforms a first generation Core i processor (i5 and below). But a 2nd gen Core i probably outperforms the AMD Phenom II, and it definitely does if you're using the built in graphics compared to entry level AMD graphics. The new Intel HD Graphics 3000 built in to the new Core i processors is much, much better than their previous integrated graphics.

Also, don't let them fool you. The only difference at all between an i3 and an i5 is that the i5 has the turbo boost feature, which automatically overclocks your processor a small amount when needed. Other than that, the i3 is exactly the same. When using integrated graphics, I would rather have a 2nd gen i3 than a first gen i5, and I'm not totally convinced the it's worth the price difference, anyway. An i3 is not like a new Celeron. The i3 is a pretty decent proc, especially the new ones.

The i7 is definitely worth it if you can afford it. It's a true quad core, and it will blow away the Phenom II whether you're using integrated graphics or a discrete video card.

---

### Post by wizard10000 on 2011-07-05
> **forrestcupp said:**
> Also, don't let them fool you. The only difference at all between an i3 and an i5 is that the i5 has the turbo boost feature, which automatically overclocks your processor a small amount when needed. Other than that, the i3 is exactly the same.

I'm afraid this is no longer true.  Speaking 2nd gen only, all i5 processors except the 2390T are quad core while all i3 processors are dual core.

edit:  [http://ark.intel.com](http://ark.intel.com) is a catchall site to find and compare Intel processor specs.

---

### Post by akand074 on 2011-07-05
> **wizard10000 said:**
> I'm afraid this is no longer true.  Speaking 2nd gen only, all i5 processors except the 2390T are quad core while all i3 processors are dual core.

edit:  [http://ark.intel.com](http://ark.intel.com) is a catchall site to find and compare Intel processor specs.

Both of you are correct actually. The first generation i3s are all dual cores hyperthreaded to 4, same with all the i5s for notebooks (if I'm not mistaken). For desktops on the other hand, the i5-6xx series is dual core hyperthreaded while the i5-7xx is a true quad core (no hyperthreading). The second gen i5s have both quad cores and dual cores hyper threaded. So basically, the i5s that are just dual cores are the same as the i3s just with turbo boost (as far as most people are concerned), while obviously the quad core i5s are different.

That said, I'd go with an i7 and you won't have to update your computer again in a long time. First gen i7 with the x58 chipset **might** actually be better if you want dedicated graphics, otherwise second gen would be much better with integrated (well first gen i7 doesn't even support integrated). Though, overall performance would be better with the second gen i7 (not for gaming and other intensive tasks though).

AMD is better value. i.e it can beat Intel in terms of performance per dollar, but current AMD processors won't match Intels high performance processors (which are more expensive).

---

### Post by marin123 on 2011-07-05
i happen to have intel i5-430M and lscpu gives this:

```
marin@marincelo:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               1199.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K

```

and virtualbox shows 8 processors.
so this means i5 IS quad core with 2 threads per core.
if you want to test it, let me know what to do and i will measure times :)

---

### Post by akand074 on 2011-07-05
> **marin123 said:**
> i happen to have intel i5-430M and lscpu gives this:

```
marin@marincelo:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               1199.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K

```and virtualbox shows 8 processors.
so this means i5 IS quad core with 2 threads per core.
if you want to test it, let me know what to do and i will measure times :)

The i5-430 is a dual core with 2 threads per core. It says right there, 2 cores per socket, 2 threads per core, and thus 4 CPUs. [If I must.]("http://ark.intel.com/Product.aspx?id=43537")

---

### Post by mips on 2011-07-05
> **marin123 said:**
> 
and virtualbox shows 8 processors.


It does the same here even though I have 4 cores with 1 thread per core. VB is wrong.

---

### Post by wizard10000 on 2011-07-05
> **marin123 said:**
> i happen to have intel i5-430M and lscpu gives this:

```
marin@marincelo:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               1199.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K

```

and virtualbox shows 8 processors.
so this means i5 IS quad core with 2 threads per core.
if you want to test it, let me know what to do and i will measure times :)

Intel says your processor is a hyperthreading dual core.  I guess I'd believe them  ;)

[http://ark.intel.com/Product.aspx?id=49023&processor=i5-430UM&spec-codes=SLBVS](http://ark.intel.com/Product.aspx?id=49023&processor=i5-430UM&spec-codes=SLBVS)

---

### Post by forrestcupp on 2011-07-05
> **wizard10000 said:**
> I'm afraid this is no longer true.  Speaking 2nd gen only, all i5 processors except the 2390T are quad core while all i3 processors are dual core.

edit:  [http://ark.intel.com](http://ark.intel.com) is a catchall site to find and compare Intel processor specs.

Yeah, sorry for the mix up. My research was for laptops, not desktops. Notebook i5s are all still dual core with 4 threads. It appears that the new desktops *are* quad core. In that case, I stand by what I said earlier if you're buying a laptop. But if you're buying a desktop, the i5 really does have an advantage.

But the hyperthreaded i3s still do a pretty good job. They're much better than the old Core2Duos.

---

### Post by wizard10000 on 2011-07-05
> **forrestcupp said:**
> Yeah, sorry for the mix up. My research was for laptops, not desktops. Notebook i5s are all still dual core with 4 threads. It appears that the new desktops *are* quad core. In that case, I stand by what I said earlier if you're buying a laptop. But if you're buying a desktop, the i5 really does have an advantage.

But the hyperthreaded i3s still do a pretty good job. They're much better than the old Core2Duos.

Let's call it even.  I didn't check mobile processors  :D

---

### Post by forrestcupp on 2011-07-05
> **wizard10000 said:**
> Let's call it even.  I didn't check mobile processors  :D

Ok, we're even. :)

FYI, I just bought a Gateway laptop with an i3-2310M and its integrated Intel HD Graphics 3000. Everything worked out of the box with the latest Ubuntu, Kubuntu, Xubuntu, and Mint. I was pretty pleased. I didn't have to do any tweaking at all to get things to work.

---

### Post by wizard10000 on 2011-07-05
> **forrestcupp said:**
> Ok, we're even. :)

FYI, I just bought a Gateway laptop with an i3-2310M and its integrated Intel HD Graphics 3000. Everything worked out of the box with the latest Ubuntu, Kubuntu, Xubuntu, and Mint. I was pretty pleased. I didn't have to do any tweaking at all to get things to work.

Nice  :)

My latest technical accomplishment is putting an Intel 6200 a/b/g/n card in my HP netbook in place of the Broadcom 4312 that was in there.

I found out the hard way after purchasing the card that HP whitelists internal WLAN and WWAN devices in BIOS - at least on netbooks.  When I fired up the netbook I was greeted with a 

[COLOR="Green"]**104 unsupported WLAN device detected - system halted.  please remove the device and reboot.**[/COLOR]

I got lucky and found a hacked BIOS with the whitelist removed, flashed the machine, installed the card and everything took off.

Since Intel WLAN drivers are open source I'm looking forward to doing my next install over wireless  ;)

---

### Post by nec207 on 2011-07-05
So you are saying the i7 is 2 times faster than the AMD phenom 2 the Quad-core or the 6 core ?

---

### Post by wizard10000 on 2011-07-05
> **nec207 said:**
> So you are saying the i7 is 2 times faster than the AMD phenom 2 the Quad-core or the 6 core ?

I don't think anybody said that.  If I was buying a processor for video editing and price was an object for me it'd be either a low-end i7, a six-core AMD or an i5-2500k.  The i7 and the i5 will outperform the six-core chip but maybe not by enough to justify the cost.

Top of the heap CPU cycles per dollar?  Probably the i5-2500k.  Look here -

[http://www.anandtech.com/bench/CPU/2](http://www.anandtech.com/bench/CPU/2)

A top-end Phenom II X6 is gonna cost you $190, the i5 will be about $219 and an i7 will run you from about $260 on up.

Video rendering is processor intensive - you want a fair bit of CPU horsepower if you're gonna do it regularly.

My i7-920 will render a one hour, 550mb avi to DVD format in about six minutes. With my old 2.8GHz P4 it took as long to render a video as it took to watch it  ;)

---

### Post by Dustin2128 on 2011-07-05
Based on what I've heard, either wait for AMD to come out with bulldozer, or get a sandy bridge line i7.

---

### Post by marin123 on 2011-07-06
> **akand074 said:**
> The i5-430 is a dual core with 2 threads per core. It says right there, 2 cores per socket, 2 threads per core, and thus 4 CPUs. [If I must.]("http://ark.intel.com/Product.aspx?id=43537")

silly me, i just saw 4 cpu and 2 threads per core. also, my system monitor shows 4 cpus. now i'm dissapointed in my processor :D

---

### Post by akand074 on 2011-07-06
> **marin123 said:**
> silly me, i just saw 4 cpu and 2 threads per core. also, my system monitor shows 4 cpus. now i'm dissapointed in my processor :D

Haha yeah software reads each thread as a processor, it doesn't know the difference. System monitor should show that. Mine too XD

---

### Post by marin123 on 2011-07-06
> **akand074 said:**
> Haha yeah software reads each thread as a processor, it doesn't know the difference. System monitor should show that. Mine too XD

omg, you've got a processor farm there :D

---

### Post by nec207 on 2011-07-06
> **wizard10000 said:**
> I don't think anybody said that. If I was buying a processor for video editing and price was an object for me it'd be either a low-end i7, a six-core AMD or an i5-2500k. The i7 and the i5 will outperform the six-core chip but maybe not by enough to justify the cost.
 
Top of the heap CPU cycles per dollar? Probably the i5-2500k. Look here -
 
[http://www.anandtech.com/bench/CPU/2](http://www.anandtech.com/bench/CPU/2)
 
A top-end Phenom II X6 is gonna cost you $190, the i5 will be about $219 and an i7 will run you from about $260 on up.
 
Video rendering is processor intensive - you want a fair bit of CPU horsepower if you're gonna do it regularly.
 
My i7-920 will render a one hour, 550mb avi to DVD format in about six minutes. With my old 2.8GHz P4 it took as long to render a video as it took to watch it ;)
 
hu ? the i5 is a Quad core? So you say I should get a Quad core  a i5 or i7?
 
Too do 6 minutes it takes over 30 minutes that is very long like a snail.No effects just removing unwanted scenes.
 
The file size was 294 MB. But yes to do 5 or 6 minutes it takes over 30 minutes .

---

### Post by wizard10000 on 2011-07-07
> **nec207 said:**
> hu ? the i5 is a Quad core? So you say I should get a Quad core  a i5 or i7?
 
Too do 6 minutes it takes over 30 minutes that is very long like a snail.No effects just removing unwanted scenes.
 
The file size was 294 MB. But yes to do 5 or 6 minutes it takes over 30 minutes .

The only current *desktop* i5 that isn't a quad-core is the 2390T.

Video rendering is processor-intensive as opposed to RAM-, video-  or disk-intensive.  You want as much processor horsepower as your budget will allow if you spend a lot of time working with video.

---

### Post by nec207 on 2011-07-08
> **wizard10000 said:**
>  
Video rendering is processor-intensive as opposed to RAM-, video- or disk-intensive. You want as much processor horsepower as your budget will allow if you spend a lot of time working with video.
 
Can you elaborate here.

---

### Post by mips on 2011-07-08
> **nec207 said:**
> Can you elaborate here.

The more cores & threads you have the better.

Maybe look for Blender CPU benchmarks to get an idea as to which cpu would perform best.

Your best performer I suspect would be this [http://en.wikipedia.org/wiki/Gulftown_(microprocessor)](http://en.wikipedia.org/wiki/Gulftown_(microprocessor)) followed by the Sandy Bridge processors.

---

### Post by nec207 on 2011-07-08
> **mips said:**
> The more cores & threads you have the better.
 
Maybe look for Blender CPU benchmarks to get an idea as to which cpu would perform best.
 
Your best performer I suspect would be this [http://en.wikipedia.org/wiki/Gulftown_(microprocessor](http://en.wikipedia.org/wiki/Gulftown_(microprocessor)) followed by the Sandy Bridge processors.
 
 
So the i5 Quad core or i7 Quad core is the best ? What about lots of RAM and good video card?
 
Also anyone had any luck with Mac computers ? I hear they the best for this stuff like the new 2011 macbook pro or the new 2011 iMac.
 
I hear they use i5 and have lots of RAM.

---

### Post by mips on 2011-07-08
> **nec207 said:**
> So the i5 Quad core or i7 Quad core is the best ?

Did you even bother reading the link I provided?

---

### Post by wizard10000 on 2011-07-08
> **mips said:**
> Did you even bother reading the link I provided?

I don't think he could.  In your link above the closing parenthesis is outside the URL tag - this happened to me this morning in another post.  Might be a vBulletin "feature".

---

### Post by nec207 on 2011-07-08
> **mips said:**
> Did you even bother reading the link I provided?
 
The link is broken.

---

### Post by forrestcupp on 2011-07-08
A good video card won't make a bit of difference for video editing. there may be other things you want to do that would use the gpu, but not video editing. In the past, it made a difference, but now even most entry level gpus can do hardware video overlay and hd playback.

I'd probably go with the best current gen i5 or i7 that you can get and get as much ram as you can but put the emphasis on the proc. also, you're just going to have to suck it up and understand that video rendering takes a long time, especially if you're doing hd.

---

### Post by mips on 2011-07-09
> **wizard10000 said:**
> I don't think he could.  In your link above the closing parenthesis is outside the URL tag - this happened to me this morning in another post.  **Might be a vBulletin "feature".**

Yip, this has happened to me before, very annoying.

> **nec207 said:**
> The link is broken.

Fixed.

---

### Post by nec207 on 2011-07-09
> A good video card won't make a bit of difference for video editing. there may be other things you want to do that would use the gpu, but not video editing. In the past, it made a difference, but now even most entry level gpus can do hardware video overlay and hd playback
 
This is the part I do not understand. Are you saying in the past video editing use the video card but not any more and if so why?
 
Is this going to change in the future?
 
So a good video card would not be used for video editing?

---

### Post by Swagman on 2011-07-09
NLE is 2D not 3D so just about any modern video card will have enough grunt & RAM to cover your needs unless you have a program that utilises CUDA.

I started on a Matrox 4mb G200 upgraded to a 8mb G550 and quit video editing when I was using a nVidia GT8800 (512mb). All of them sufficed.

---

### Post by forrestcupp on 2011-07-09
> **nec207 said:**
> This is the part I do not understand. Are you saying in the past video editing use the video card but not any more and if so why?
No, I'm saying that in the early days of computer video editing, GPUs were pretty crappy and they couldn't handle simple hardware accelerated 2D overlays. I'm talking about like the mid 90's when people were first trying to edit videos digitally. But now, even the lowest level, cheap video cards and GPUs can easily handle that, so it's not going to ever be anything you have to worry about for editing videos. You'll probably want to make sure you at least have a new enough card that it can handle HD playback. Entry level video cards have been able to do that for quite some  time, though.

The only reason you would need an upscale video card is if you're planning on creating your own 3D animations to include in your videos using Blender or something. Or if you're going to be doing other types of things that require 3D, of course.

---

### Post by koleoptero on 2011-07-09
[Buy one of these.]("http://www.nvidia.com/object/personal-supercomputing.html")

---

### Post by nec207 on 2011-07-09
sorry what does 2D or 3D have do with it? 
 
 
A good video card will have fast GPU that can render each frame very fast .So I do not understand why a video card GPU would not be used.
 
Any video editing has to go through and render each frame.And this takes long time.

---

### Post by forrestcupp on 2011-07-10
> **nec207 said:**
> sorry what does 2D or 3D have do with it? 
 
 
A good video card will have fast GPU that can render each frame very fast .So I do not understand why a video card GPU would not be used.
 
Any video editing has to go through and render each frame.And this takes long time.

Let me try this one more time. The biggest point of higher end GPUs is for 3D, and 3D has absolutely nothing to do with video editing, unless you're doing CGI stuff. Since video overlay uses hardware accelerated _2D_, that is what is important. _Video editors do not use your GPU to render the video; they use the CPU._ The only thing your GPU is used for in most cases is for previewing your video in real time, and some video effects may use the GPU for previewing it in real time. But the GPU is not used at all during the rendering process.

With that in mind, what I was trying to say is that about all modern GPUs can handle the 2D overlay that takes place while you are previewing your work. Since your main concern is with the time it takes to *render*, you need to invest more in the CPU and not be as concerned with the GPU, since the CPU is what is used for rendering.

In the mid-90's, the type of video card you had mattered, because low end ones weren't powerful enough to let you preview in real time without it looking really crappy. Those times are long gone, and you don't have to worry about that anymore. I've been digitally editing videos since the mid-90's, so I've experienced all of these things.


Edit: If you have the money, by all means buy a good video card. I'm just saying that if you are on a budget, I would try to allocate more money to the CPU rather than trying to get an expensive video card. But that's also based on the assumption that video editing is the primary purpose for your computer.

---

### Post by mips on 2011-07-10
> **nec207 said:**
> sorry what does 2D or 3D have do with it? 
 
 
A good video card will have fast GPU that can render each frame very fast .So I do not understand why a video card GPU would not be used.
 
Any video editing has to go through and render each frame.And this takes long time.

Are you talking about video editing or 2/D3D rendering as in building 2D/3D models in Blender etc?

[http://www.3dmd.net/forum/3d-discussion-5688.html](http://www.3dmd.net/forum/3d-discussion-5688.html)
[http://forums.blendernewbies.com/viewtopic.php?f=17&t=4110](http://forums.blendernewbies.com/viewtopic.php?f=17&t=4110)
[http://www.blendernation.com/2010/08/23/smallluxgpu-interactive-demo-with-blender-2-5-videos-tutorials/](http://www.blendernation.com/2010/08/23/smallluxgpu-interactive-demo-with-blender-2-5-videos-tutorials/)

---

### Post by nec207 on 2011-07-10
> **forrestcupp said:**
> Let me try this one more time. The biggest point of higher end GPUs is for 3D, and 3D has absolutely nothing to do with video editing, unless you're doing CGI stuff. Since video overlay uses hardware accelerated _2D_, that is what is important. _Video editors do not use your GPU to render the video; they use the CPU._ The only thing your GPU is used for in most cases is for previewing your video in real time, and some video effects may use the GPU for previewing it in real time. But the GPU is not used at all during the rendering process.
 
With that in mind, what I was trying to say is that about all modern GPUs can handle the 2D overlay that takes place while you are previewing your work. Since your main concern is with the time it takes to *render*, you need to invest more in the CPU and not be as concerned with the GPU, since the CPU is what is used for rendering.
 
In the mid-90's, the type of video card you had mattered, because low end ones weren't powerful enough to let you preview in real time without it looking really crappy. Those times are long gone, and you don't have to worry about that anymore. I've been digitally editing videos since the mid-90's, so I've experienced all of these things.
 
 
Edit: If you have the money, by all means buy a good video card. I'm just saying that if you are on a budget, I would try to allocate more money to the CPU rather than trying to get an expensive video card. But that's also based on the assumption that video editing is the primary purpose for your computer.
 
Okay I understand you post now but why can't they make video card do every thing?
 
Why does vidoe editing take so long.
 
Also would Linux or windows be better for this stuff? What about Mac computers those new 2011 macbook pros or those new 2011 iMac ? I haer they are very powerful and have i5 CPU and some high end once have i7.
 
[http://www.apple.com/mac/](http://www.apple.com/mac/)
 
The spects look good.
 
I hear windows have alot of bloatware and slow and bloated where Linux and Mac OS X is like driving a race car.

---

### Post by mips on 2011-07-10
I think you should just buy yourself a Mac Pro, the 12 Core one.
[http://store.apple.com/us/configure/Z0M4?mco=MTg2OTQ5OTk](http://store.apple.com/us/configure/Z0M4?mco=MTg2OTQ5OTk)


.

---

### Post by forrestcupp on 2011-07-10
> **nec207 said:**
> Okay I understand you post now but why can't they make video card do every thing?
 
Why does vidoe editing take so long.Video cards are made to be specialized to perform the computations necessary to display graphics. A big part of a high end card's specialty is having pipelines, hardware shaders, etc., to be able to display 3D graphics. If you're talking about the raw processing power of a GPU, GPUs have a *way* slower clock speed than a CPU. They're not made for performing general calculations, but just for *displaying* graphics. That's why the CPU is way more powerful for doing the rendering than a GPU would be. But GPUs are good for helping with watching a preview while you're working.

As for why does it take so long? Just think about what it's doing. A video stream is going to be something like 24 frames per second for film quality and 29.97 frames per second for video. You can think of that as being like at least 24 jpg images for every second of video that it has to process, not including the audio stream. Then you go splicing together any number of video tracks, adding transitions, effects, overlays, transparencies, and then you mix in all of your music and sound tracks, adjusting volumes, pans, etc. When you finally get everything looking and sounding exactly how you want it, the video editor has to perform all of the computations to mix all of those things together for each frame of the video all while converting it to whatever format and standard you want the end solution to be. Considering that it has to perform all of that 24-30 times for each second of video, that's *a lot* of work. It's very processor intensive, and it's never going to be really quick unless you're just wanting to do something as basic as joining two clips together with no transitions or anything.

Basically, the more things you do to the video, the longer it will take to process.
 
> **nec207 said:**
> Also would Linux or windows be better for this stuff? What about Mac computers those new 2011 macbook pros or those new 2011 iMac ? I haer they are very powerful and have i5 CPU and some high end once have i7.
Linux doesn't have any really great options for video editing.  A lot of people swear by Final Cut Pro in Mac. I personally use and love Sony Vegas Pro in Windows, and I don't really see how spending all the extra money on a Mac and Final Cut Pro would be any better.


Edit: just be glad you're not getting into CGI. Pixar has two rendering farms, each containing hundreds of servers. For Toy Story 3, it took them an average of 7 hours to render each frame of the movie. There were 24 frames per second of movie. Some frames took up to 39 hours to render.

---

### Post by marin123 on 2011-07-10
> Edit: just be glad you're not getting into CGI. Pixar has two rendering farms, each containing hundreds of servers. For Toy Story 3, it took them an average of 7 hours to render each frame of the movie. There were 24 frames per second of movie. Some frames took up to 39 hours to render.

that means it would take 140 years for 2 hour movie to render. are you sure about that?

and as for video editors in linux, my favorite is open shot. it does the job very well.

---

### Post by wizard10000 on 2011-07-10
> **forrestcupp said:**
> ...Linux doesn't have any really great options for video editing.

cinelerra is about as good as it gets but it's not particularly user-friendly.

---

### Post by forrestcupp on 2011-07-10
> **marin123 said:**
> that means it would take 140 years for 2 hour movie to render. are you sure about that?Yeah. Their render farms were rendering several frames in parallel. It took 7 hours average per frame, but they weren't using all of their resources on each frame; they were rendering many frames at once. It supposedly took them 1084 days to make the movie.

> **wizard10000 said:**
> cinelerra is about as good as it gets but it's not particularly user-friendly.Cinelerra is pretty great. I've used it on a fairly large project (large by my standards). I used the CV version, and I actually thought it was more user friendly than what people complain about. It definitely has a lot of functionality. My main complaints with Cinelerra were that it was a little buggy, and it didn't support a very good variety of file formats. For simpler projects, I was pretty impressed with Kdenlive, if you can get around the bugginess. I'm pretty spoiled with Sony Vegas, though.

---

