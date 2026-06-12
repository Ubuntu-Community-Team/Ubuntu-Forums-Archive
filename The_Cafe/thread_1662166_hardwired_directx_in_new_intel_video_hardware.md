---
title: "hardwired directx in new intel video hardware"
date: 2011-01-07
forum: The Cafe
---

### Post by sdowney717 on 2011-01-07
[http://it.tmcnet.com/topics/it/articles/132670-intels-ivy-bridge-architecture-support-directx-11-on.htm](http://it.tmcnet.com/topics/it/articles/132670-intels-ivy-bridge-architecture-support-directx-11-on.htm)

so they do this to protect streaming media then it is DRM, but they say it is not DRM.
[http://www.afterdawn.com/news/article.cfm/2011/01/07/intel_insists_insider_in_sandy_bridge_is_not_drm](http://www.afterdawn.com/news/article.cfm/2011/01/07/intel_insists_insider_in_sandy_bridge_is_not_drm)

More of MS locking out therefore obsoleting linux from new technologies. If you make the hardware so it only works with proprietary software, where does that leave linux?
this is an intel design and is supposed to calm down the media producers by making it safer to push their video on the web by using MS software. The feeling I get is MS is trying through DRM to scare people into thinking DRM must be used and it must be MS DRM or it is not safe  from theft.

> Intel has insisted that the "Insider" feature of new Sandy Bridge chips is not intended to be used as Digital Rights Management (DRM).
Instead, the microchip superpower insists that the Insider features are only intended to entice Hollywood studios to make streaming high definition content available on PCs. The technology, consisting of specialized authentication and encryption features and present in second generation Core i3, i5 and i7 processors, establishes a secure connection between streaming services and PCs.

At CES, a demonstration showed the CinemaNow movie streaming site identifying a PC with a Sandy Bridge processor, and then initiating s 1080p stream of Inception.

"Insider gives PCs the level of trust that the studio needs to make their content available. In the past they were very leery of streaming content. It's not a DRM technology at all," said Josh Newman, graphics marketing director at Intel.

The Warner Bros. Home Entertainment Group plans to start streaming movies in high-definition to PCs with the new processors. Kevin Tsujihara, president of the group, said on Wednesday that the studio would be making 300 new HD titles available for streaming and may consider streaming some titles in 3D. 

---

### Post by zekopeko on 2011-01-07
First of all DirectX isn't really hardwired. It's simply supported by the GPU. If you actually read your first link you will see that they compare it to AMD ATI's 6000 GPU series ([with just released open source support]("http://www.phoronix.com/scan.php?page=news_item&px=ODk4OQ")) which also support DirectX/3D 11. The GPUs still support OpenGL.

Second of all the Insider tech could be a boon to Linux since if it's mostly in hardware it would allow Netflix and other streaming services to provide Linux support without using Silverlight or Flash.

It appears your entire post is selective reading and FUD.

---

### Post by 3Miro on 2011-01-07
There was a thread about this not too long ago. Many people commented that they will be switching to AMD.

The thing is, there is nothing Intel can do to prevent people from recording their own Desktop sessions. Then you can record a session while watching the movie in full screen. (OK this is hacking things, so I hope I don't get banned, there are other more elegant solutions that can void such locking mechanism 100%). Basically, until they can put a computer chip in my head, at some point of time, the move image has to unencrypted and sent to my eyes. That is when it can be caught and recorded. Theoretically, they cannot stop people from "stealing" movies.

I don't think this will affect Linux at all. We are basically looking at Intel marketing office selling garbage technology to technologically illiterate CEOs of some move companies.

---

### Post by CarpKing on 2011-01-07
Is this similar to the dedicated video-decoding hardware found in graphics cards for which AMD has no intention of releasing specs for use in open-source drivers?  NVidia of course releases no specs for anything, but I think they have similar separate hardware.

---

### Post by sdowney717 on 2011-01-08
benefit designed only for windows OS, linux users are out of this loop, locked out.

perhaps some part of linux could benefit if they could or would replicate directx functionality, but then the patent infringement comes in force.
so dont expect that, and now less reason for desktop or embedded linux. The web is going all out for video and 3d.

> n a company statement, said Mooly Eden, vice president and general manager, PC Client Group, Intel, "The new 2nd Generation Intel Core processors represent the biggest advance in computing performance and capabilities over any other previous generation. **The built-in visual capabilities enabled by these new processors are stunning. This, combined with improved adaptive performance, will revolutionize the PC experience in a way that is obvious for every user to see and appreciate &#8211; visibly smarter performance**.

---

### Post by disabledaccount on 2011-01-08
> **zekopeko said:**
> First of all DirectX isn't really hardwired. It's simply supported by the GPU. If you actually read your first link you will see that they compare it to AMD ATI's 6000 GPU series ([with just released open source support]("http://www.phoronix.com/scan.php?page=news_item&px=ODk4OQ")) which also support DirectX/3D 11. The GPUs still support OpenGL.Supported = hardwired, because GPU architecture is "optimized" for computing matrixes in directx native format and opengl as well. Support for opengl is maintained because most CAD and proffessionall rendering software uses opengl, not directx.

Furthermore, people seems to not know (yet) about openCL - this is the future of stream computing and "dedicated" mpeg/h264 hardware most propably will become obsolete in future (I think about next 2-3 GPU generations). At least, linux can live without this.

Furthermore #2: have you guys heard that main DRM encryption keys leaked from Intel? Actually DRM is obsolete, as it wont stop piracy or even wont decrease its scale. Intel invested a lot of time and money to bring DRM to life - so they can't just drop the project.

---

### Post by sdowney717 on 2011-01-08
one you get first mover status bringing enhanced video content to users, this tends to keep rolling the same way. 
NETFLIX! where is the linux support for desktop users??
does not exist and likely never will.
Think MS will release silverlight for linux? dream on.
You think Warner will stream somehow to let a linux user gain this benefit? Unlikely.  
Web moving towards video and I hope that open CL has a better future. 

> The Warner Bros. Home Entertainment Group plans to start streaming movies in high-definition to PCs with the new processors. Kevin Tsujihara, president of the group, said on Wednesday that the studio would be making 300 new HD titles available for streaming and may consider streaming some titles in 3D. 

---

### Post by disabledaccount on 2011-01-08
NETFLIX works in US only - where is support for the rest of the world? :)

Right now I'm able to watch every movie that is streamed in network (flash/gstreamer) - I will start to worry when this becomes impossible :)

---

### Post by sdowney717 on 2011-01-08
unrelated but shows the mindset
ARM chip makers were very happy when MS said they would develop for that hardware. the mindset is if you want entertainment and do serious work on your device, it has to be windows based.
that does not seem to be changing, IMO

[http://blogs.wsj.com/digits/2011/01/07/arm-chip-backers-revel-in-windows-news-from-ces/?utm_source=twitterfeed&utm_medium=twitter&utm_campaign=Feed%3A+wsj%2Fbiztech%2Ffeed+%28WSJ.com%3A+Business+Technology%29](http://blogs.wsj.com/digits/2011/01/07/arm-chip-backers-revel-in-windows-news-from-ces/?utm_source=twitterfeed&utm_medium=twitter&utm_campaign=Feed%3A+wsj%2Fbiztech%2Ffeed+%28WSJ.com%3A+Business+Technology%29)
> Without Windows support, for example, many travelers who want to bring an ARM-based tablet for entertainment reasons have to think about also bringing a conventional laptop if they have work to do. Windows support for ARM &#8220;will solve that issue,&#8221; Jacobs says.

---

### Post by sdowney717 on 2011-01-08
[http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA)
so is it really this bleak? I think so.

he comes to the realization that the enhancements will never be part of linux, so the experience will never be there and then the Warners- Netflixes of the world, why bother ?

> Charlie Demerjian at SemiAccurate has written a very scathing review against Sandy Bridge for this very reason: Sandy Bridge is the biggest disappointment of the year. Charlie feels that Sandy Bridge is a broken platform since there aren't Linux drivers working "out of the box" on Ubuntu 10.10. "The down side is pretty painful. Intel offers a bunch of must have, make your life better, brings world peace, flowers, and the like level features on Sandy Bridge. The working count on Linux? Zero on launch.** The chance that they will ever work on Linux? Just slightly above zero,** think the need for extended floating point precision to see that many zeros...So, back to the 'must have or your coffee shop experience is not complete' feature set. They include **Video Processing Accelerators - never coming to Linux, Color Processing Accelerators - never coming to Linux, Skin Tone Enhancements - never coming to Linux, Adaptive Contrast Enhancement - never coming to Linux, Total Color Control - never coming to Linux, Video Decode in hardware - Q1, Video Encode in hardware - Q1, 3D acceleration - Q1 sooner rather than later and a host of software to use it - never coming to Linux."** 

---

### Post by zekopeko on 2011-01-08
> **tomazzi said:**
> Supported = hardwired, because GPU architecture is "optimized" for computing matrixes in directx native format and opengl as well. Support for opengl is maintained because most CAD and proffessionall rendering software uses opengl, not directx.

I won't claim to know specific on how modern GPUs work but my point was that the OP's post was FUD. Direct3D was already supported on previous Intel GPUs. He just read "Sandy Bridge supports DirectX11" and then went to write a rant.

Not to mention that the "Insider" feature makes no mention of Linux.

---

### Post by zekopeko on 2011-01-08
> **sdowney717 said:**
> unrelated but shows the mindset
ARM chip makers were very happy when MS said they would develop for that hardware. the mindset is if you want entertainment and do serious work on your device, it has to be windows based.
that does not seem to be changing, IMO

[http://blogs.wsj.com/digits/2011/01/07/arm-chip-backers-revel-in-windows-news-from-ces/?utm_source=twitterfeed&utm_medium=twitter&utm_campaign=Feed%3A+wsj%2Fbiztech%2Ffeed+%28WSJ.com%3A+Business+Technology%29](http://blogs.wsj.com/digits/2011/01/07/arm-chip-backers-revel-in-windows-news-from-ces/?utm_source=twitterfeed&utm_medium=twitter&utm_campaign=Feed%3A+wsj%2Fbiztech%2Ffeed+%28WSJ.com%3A+Business+Technology%29)

OMG! The ARM chip makers want to support the most widely used OS! The horror.

---

