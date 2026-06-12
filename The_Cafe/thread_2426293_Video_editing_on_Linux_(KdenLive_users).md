---
title: "Video editing on Linux (KdenLive users?)"
date: 2019-09-06
forum: The Cafe
---

### Post by adrian-dmnsn on 2019-09-06
Hi, my T400 is finally feeling the strain.  At the same time I've decided I'd finally like to be able to edit video at home.  
My question is whether people have had good experiences running video editing software on dual core processors; internet forums would lead one to believe you are insane to not have a quad core when trying to edit video.  Same goes for the various GPUs.  I am not much of a computer buff and the intake of info has been a bit overwhelming.  At the moment I can afford something modest but new (with 4 cores) like a low specs Lenovo E590, though I would prefer to get something refurbished (with only 2 cores) rather than throwing money at the problem.  How about this T460:[https://www.memoryexpress.com/Products/MX78001]("https://www.memoryexpress.com/Products/MX780")   
Thanks in advance.
Adrian

---

### Post by qyot27 on 2019-09-07
I used to edit video on a Pentium III-era Celeron with Adobe Premiere 6.5.  It's not a question of whether it's possible; it's a question of whether it's *comfortable*.  And the thing that determines that isn't actually the editing part, it's the encoding or rendering part.  Number of cores and GPU mean nothing here, as those are either not going to be used by the editor itself, or to put it another way, the editing program has to have its own logic to deal with those hardware components.  Even if you got a quad core with a nice GPU, the editing program could still be single-threaded and not use the GPU at all other than what the OS in general uses it for.

Depending on your workflow, the exported video could be encoded to output formats using the additional cores or the GPU's hardware encoder, but again, that depends on your process.  Export the video from the editor in a raw or losslessly compressed format and feed it into FFmpeg to get the final output?  Yeah, multi-threaded encoding or GPU encoding is possible.  And while Kdenlive does integrate with FFmpeg's libraries for import/export functions, I think I'd still err on the side of caution and not rely on the editing program to do encoding for distribution or consumption.

---

### Post by adrian-dmnsn on 2019-09-07
Thanks for that answer.  Yes, that each program determines how hardware is used makes sense; I think most of what I read was related to the latest versions of premiere.  The editing I'm doing is also not terribly demanding, not 4k, not making use of animation or graphics as I attempt to keep it analog all the way til upload. 
I think I'll go with a refurbished comp and try my luck, figure out the workarounds for encoding using linux.  Plus, digital editing has been happening for sometime now, as I'm not using the latest technology for filming, something older ought to suffice.

---

### Post by mastablasta on 2019-09-09
Core i5 or Ryzen 5 will be OK (if used ones, i would go with 4th gen and newer). the GPU is not that important, but if you have a desktop and you can add a descent one (e.g. somewhere in the range of nvidia 1050, or at least 1030) it will help a bit. 

the CPU is still the most important. the laptops ones seem to do quite well too. i was doing a bit of editing (cutting, moving, some effects on HD video) on laptop with Core i3 6100U with 4GB ram & intel GPU and it did ok. i was using *shotcut* editor on win10. i've been thinking of getting searching for something to use at home and after checking many sites and doind this on i3, i believe that at least for my needs i5 or ryzen 5 is more than enough and i would add at least 8 GB ram to it. this was confirmed by my brother who used his desktop i5 (6th Gen) and intel GPU 4 GB ram to do some light video editing in kdenlive as well as in blender.

if you go with used laptops, get a business grade laptop.

BTW this single threaded thing - it's the reason why i can run some newish games on my 15 year old single core Athlon. ofcourse games need mostly a good GPU. still it's kind of interesting when i see some brand new laptops and PC models struggle with games that work like a charm on my old PC. to make it funnier - farcry 2 struggled on winxp. i had to set it all on low (640x480(, add special settings in config file to reduce it even further. while on linux it works on medium, normal monitor resolution without issues. it even loads faster than on windows. maybe i should try it on highest, but that might be pushing it on this old PC.

---

