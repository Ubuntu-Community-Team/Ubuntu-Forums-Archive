---
title: "Using your Meerkat as a TV media center? Care to talk about how well it works?"
date: 2017-06-18
forum: System76 Support
---

### Post by sikhandin on 2017-06-18
I'm thinking about buying a Meerkat with the idea that it will do double duty as my desktop and in place of a Roku or similar for my HD plasma tv. However, S76's description is two sentences long and I'm hoping someone who uses one this way would be willing to tell me how they use theirs.
And, yes, I have asked S76 sales about this and all my questions have been answered with the exception of the Media Center question. I'm really hoping for owner feedback here. This will help me choose between the Meerkat and Wild Dog Pro.

From the S76 Meerkat page:
"**Media center.** Complete with fast WiFi and gigabit  Ethernet, Meerkat is the ideal platform to build your personal media  center. Up to 2.5TB of storage provides space for all of your  entertainment content."

My questions:
-Is it meant for use with HD tvs, or just computer monitors? Does the brand or age of the tv matter? Mine's almost 5 years old.
-Is there special software pre-installed or is S76 referring to just accessing streaming content like Netflix, Amazon, and Hulu through a browser?
-Will Kodi work with Meerkat?
-Will an air mouse work with Meerkat? How easy is it to set up if so? Will it require a hardware add-on?

Thanks to any Meerkat owners willing to share experiences!! :)

---

### Post by TheFu on 2017-06-18
How much is small size worth?

There is a huge premium cost for tiny PCs. Because of the form factor, there are almost always cooling issues and upgrades are next to impossible. It is hard to add a better GPU or more disks.  You'll be stuck with external disks and USB connectivity.  I only saw an estimated $500 price. For about $300, you can get a mid-tower computer that is about 2x faster and can be expanded as all other PCs can.  Normal, popular, upgrades won't cost nearly as much either.

Don't expect DRM streaming services to work without significant effort, if it is even possible. This is a Linux thing.  Until both HW and the Linux kernel completely support DRM working together, it isn't likely.  I know they've been adding more and more DRM features to the kernel, but don't think they have it solve completely yet. Maybe another year will be needed, if not 2.

If you want to watch paid streaming services, get a Roku and be happy. It has the widest support for those compared to any other device.
 
As for working with a TV or not.  It really comes down to the video inputs on the TV and the video outputs on the computer.  Usually HDMI will be supported by both, so it won't be an issue. Just use **lxrandr** to enable the external monitor and the audio control application to send audio over the HDMI cable. Some TVs support VGA and DVI video inputs. Those don't carry audio, so an audio connection from the headphones would be needed if you don't use HDMI.  I have no understanding of DisplayPort, but suspect it does audio and video at least as well as HDMI.  It really comes down to the ports on the computer and the TV.

I don't know anything about what software is pre-installed. You have the entire Linux ecosystem available, so pre-installed doesn't matter. I doubt System76 has any specialized software they provide related to this.

Media center means different things to different people.  Some are playback devices only. That is what this appears to be. Just install kodi, setup your sources and local media content locations, be happy. It isn't hard. There's a GUI for pretty much everything. I can't see any reason why Kodi wouldn't work. It runs nicely on lessor CPUs.

I don't know anything about this specific model, but have had other tiny PCs and been very disappointed with the results. They were all loud, impossible to upgrade and had cooling issues.

Sorry if my views aren't helpful.

---

### Post by sikhandin on 2017-06-18
[I]"There is a huge premium cost for tiny PCs. Because of the form factor,  there are almost always cooling issues and upgrades are next to  impossible. It is hard to add a better GPU or more disks.  You'll be  stuck with external disks and USB connectivity.  I only saw an estimated  $500 price. For about $300, you can get a mid-tower computer that is  about 2x faster and can be expanded as all other PCs can.  Normal,  popular, upgrades won't cost nearly as much either."
[/I] 
You sound like my inner monologue as I try to decide on something before this laptop dies. There is always a reason not to buy anything! ;)
This is really why I was hoping for Meerkat owners to respond. 
There is a review floating around online showing how it can be opened up for upgrades, though you're right, it's no tower. Obviously the form factor is an important plus for me here, or I would just get the future-proofed tower. To me, the Meerkat seems like a malleable all-in-one pc. That would probably be a horror show for you, but for me a entertainment desktop that can also be used to connect to my stereo and tv seems cool to me. 
Of course, you raise potential reality points here, but I won't know unless someone can post some verified experience. 
It's just weird, because most people I know have all-in-ones that run 24/7 and don't have any of the issues you talk about. I just really don't want to buy an HP Envy with a touchscreen though.

[I]"Don't expect DRM streaming services to work without significant effort,  if it is even possible. This is a Linux thing.  Until both HW and the  Linux kernel completely support DRM working together, it isn't likely.  I  know they've been adding more and more DRM features to the kernel, but  don't think they have it solve completely yet. Maybe another year will  be needed, if not 2."
[/I]
Interesting. I thought Roku was linux-based? I guess they aren't sharing.

[I]"As for working with a TV or not.  It really comes down to the video  inputs on the TV and the video outputs on the computer.  Usually HDMI  will be supported by both, so it won't be an issue. Just use **lxrandr**  to enable the external monitor and the audio control application to  send audio over the HDMI cable. Some TVs support VGA and DVI video  inputs. Those don't carry audio, so an audio connection from the  headphones would be needed if you don't use HDMI.  I have no  understanding of DisplayPort, but suspect it does audio and video at  least as well as HDMI.  It really comes down to the ports on the  computer and the TV."
[/I]
My tv does have HDMI, so I guess I'm good here? I haven't heard of **lxrandr**, thanks!

[I]"Media center means different things to different people."
[/I]
Again, someone with direct Meerkat experience would be helpful here. But you're right, what does S76 mean? To me, it seems standard that an advertised media center would refer to movie and tv streaming at least, in addition to a stereo. Especially as they talk about games separately by touting it as a Steam client. 

  [I]"Some are  playback devices only. That is what this appears to be."
[/I] 
**What?** The Meerkat is a pc isn't it? Now I'm confused. What is a "playback device"?



*"I don't know anything about this specific model, but have had other tiny  PCs and been very disappointed with the results. They were all loud,  impossible to upgrade and had cooling issues.*
[I]Sorry if my views aren't helpful."
[/I]
You're fine. Mostly I do know that a NUC isn't a tower. However, all-in-ones aren't either and they seem pretty cool. You know, if they ran linux without driver issues out of the box and I could find one at Best Buy without W10 and a touchscreen.
I'm not hoping for this to be my 5-7 year tower pal, just a stop gap until I find a tower I like. I intend to spend more $ on my monitor and my keyboard honestly. My eyes and hands are tired.

---

### Post by jweber53 on 2017-06-19
I've been using my meerkat for over a year and it's performed well. The model I got was pretty much an Intel NUC6i3SYB. I use it for watching and recording digital broadcast TV with a USB tuner adapter hooked to a rooftop antenna. I also use it to watch web based content. Seems to have plenty of power for all this. I have the Intel(R) Core(TM) i3-6100U CPU @ 2.30GHz processor with 8GB ram. I'm using a 27" Samsung 1080p computer monitor. I like  the small size and the power consumption is less than 20W giving great UPS run time for an always-up server (I also use it as a remote logging host for other devices). It wasn't using the factory installed System76 drivers, so I haven't added them after reinstalling the OS.

---

### Post by sikhandin on 2017-06-19
JWeber53, thanks for the response! 
When clamped to the back of a monitor, can you really discern a performance difference between your meerkat and any similar i3 all-in-one you might see at Best Buy?
TheFu really has me re-thinking NUCs. I just assumed they were like the systems on the back of an imac or HP Envy,etc.

It's interesting you're giving it some server duties also. I'm just getting to the point where I'm beginning to feel a need for my owner server, but I don't yet have a real sense of what that means as far as power usage, etc.

---

### Post by TheFu on 2017-06-19
If you want more details about servers, it would probably be worth posting a specific question to the "Servers" subforum. I'm active over there. Plus there are lots of others there with server experience. In general, people throw way too much hardware at home servers than is needed.   It is only when you want to run Geospatial databases or 15 virtual machines that normal $500 in computing hardware doesn't cut it ... or if you get a NUC.

---

