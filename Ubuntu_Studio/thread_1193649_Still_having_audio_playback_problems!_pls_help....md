---
title: "Still having audio playback problems! pls help..."
date: 2009-06-21
forum: Ubuntu Studio
---

### Post by morganpatrick on 2009-06-21
OK, I've been turning to Ubuntu, becoming exasperated, giving it up, then coming back, for three years now. I keep hoping conditions will improve and so far they have not for me, but maybe I'm doing something wrong...

I want to run FL Studio with my Presonus Audiobox in ubuntu. I'm running Jaunty. I didn't get Ubuntu Studio because I don't want the extra programs but I did get linux-rt. I've already done the memlock rtprio **** on that security/conf whatever file and I created and 'audio' group and added myself to it. I can start Jack in Realtime mode but my computer freezes after like 10 minutes when I boot with that kernel.

Here are my questions: How do I get the realtime kernel to work? Do I need to wait for the next version of Ubuntu? Should I just compile my own? Does anyone have a sure-fire thread for this?

Is there a single resource that explains the different settings in qjacktl and how they affect xruns and your ability to start jack? for years all i see is 'well I tried all these permutations and somehow this just happens to work for me personally.' There has to be *some* rhyme or reason to it.

Is there a better way to do this? I have to use FL studio.

Is there any more information you need from me to offer the right advice based on my hardware?

Thank you.

---

### Post by kayosiii on 2009-06-21
From what I can gather your soundcard is supported by alsa and therefore jack (A lot of newer USB cards are not - so this is good)... 

The realtime setup is a complete PITA as you have found out. An easier solution is being worked on (one that won't require user intervention or making your machine vulnerable to certain types of attack).

FLStudio on Ubuntu - you must really want to use Ubuntu. My advice is to first get everything working even if isn't performing optimally and then go from there - so don't worry about the realtime kernel just yet. 

So your setup should look something like FLStudio->Asio->asio2jack_bridge->jack? 

As for jack settings the main ones that effect performance is the Realtime and Priority options Priority is sort of a ranking system to tell how important a particular thread or process is so the higher number services get serviced first and the scheduler in the kernel will try and make sure nothing gets starved completely. Priorities above 70 require special privelages. (This is my understanding anyways if somebody is more knowledgeable please let me know)

Frames/Period and Periods/Buffer are the main performance tweaking settings. Basically here you are trading off stability for latency. The bigger the Number the more stable but the longer the delay between an event occuring in the outside world and the computer recognising it.
If you are having xrun problems try setting Frames/Period to 4096 and Periods/Buffer to 3. If you are getting xruns at these settings then something is pretty drastically wrong. 

Ports Maximum is tells jack the maximum number of ports that can exist... for your purposes the default will be just fine. Timeout is the maximum length of time that jack can go without communication with the hardware before it kills itself. It does this to prevent hardware lockups (AFAIK). You want to increase this value if you keep losing connection to jack my previous exprience is that values above 2 seconds requires tweaking somewhere else in the situation. So I usually leave it at that. Delay Starting is fairly self explanatory you should try increasing that only if you are having trouble connecting to jack at all.

So the third column - Interface tells you which sound card to connect to. Since you are using alsa this setting is pretty vital. Most of the other settings here are helpful when you are not getting sound at all. 

One place that a realtime kernel can really help is in a situation where usb shares system resources with other devices (manufacturers sometimes do this to save money) The other device can interfere with your audio systems performance. What the realtime kernel does is virtualize the hardware resources so that your audio can be run at a higher priority than the hardware.

You should probably check out lmms - A linux native program that works like FLStudio. It may not be able to everything you need it to but if it does - your audio setup will be considerably less complicated.

Also you should look at posts on disabling Pulse Audio - It can on the current version of Ubuntu have conflicts with jackd. Which cause performance issues.

---

