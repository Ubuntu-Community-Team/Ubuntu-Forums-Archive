---
title: "Need help identifying the issue"
date: 2016-04-14
forum: Windows
---

### Post by mastablasta on 2016-04-14
I was playing Hitman, when the GPU crashed. ok it happened occasionally before. Only this time for some reason I couldn't get to the restore button and I would reboot afterwards. So I crashed the hitman window, restored and rebooted the whole thing. I got what is on pictures. messed up fonts.


Is this the GPU failing? is the issue another hardware? or is it a software issue?

I've never seen anything like this. on boot the fonts are messed up. and I am not sure the windows take it over yet at that point.

after about 10 or more resets and VPU recoveries I get to the normal desktop, however it then appears to be using some kind of software accel. mode to display. playing movies give out various errors that some directx is missing etc. and then plays the movie. flash video is slow. so I guess this is CPU doing GPU's work.

[ATTACH=CONFIG]268373[/ATTACH][ATTACH=CONFIG]268372[/ATTACH][ATTACH=CONFIG]268374[/ATTACH][ATTACH=CONFIG]268375[/ATTACH][ATTACH=CONFIG]268376[/ATTACH]

---

### Post by mastablasta on 2016-04-15
i don't know who saw this post so many times and wasn't bothered to reply. maybe it's the new Google AI. :)

In any case after a long afternoon and trying to boot Linux and such I found this: [http://guide2repair.com/graphics-card-failurerepair-guide](http://guide2repair.com/graphics-card-failurerepair-guide)

The screen I am getting is apparently a result of bar VRAM or it can also be caused by RAM. so I ran a mem test and after 2 passes it didn't find anything. which means it must be VRAM. unfortunately at this point all I cound do is boot into safe mode (worked fine) or remove the device and boot into windows. so 2D works ok. but no 3D. 

BSOD says: ```
The problem seems to be caused by the following file: ati2dvag
```
Kubuntu says:
```
UVD not responding, trying to reset the VCPU
```
Until it gives up.

If I don't forget I will check the logs and give the full message here. 

with further reading I get it that if screen is messed up at POST it is very likely the GPU's fault. 

I am attaching a few pictures for reference on how this looks like as information is a bit hard to find and might be useful to someone:

---

### Post by coffeecat on 2016-04-15
> **mastablasta said:**
> i don't know who saw this post so many times and wasn't bothered to reply. maybe it's the new Google AI. :)

The view count of 181 (at the moment) includes guests who are not logged in and google indexbots and the like. Whether guests are bothered or not, they can't post, neither can googlebots. The number of logged in forum members who have so far viewed this thread is 10, including you and me.

---

