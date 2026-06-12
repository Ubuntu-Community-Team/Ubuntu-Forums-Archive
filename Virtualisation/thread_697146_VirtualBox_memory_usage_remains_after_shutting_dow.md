---
title: "VirtualBox memory usage remains after shutting down VM"
date: 2008-02-14
forum: Virtualisation
---

### Post by ArtInvent on 2008-02-14
I'm running an AMD dual core with 2GB of RAM. I've got Gutsy as a host and VirtualBox running XP as a guest in 1GB of RAM. Seems like it ought to be plenty right?

If you just stick to apps in one OS or the other, it's fine. The VM seems to run quite well and fast and be stable. I often use seamless mode and that's pretty slick. Other than no 3D I'm pretty amazed with it. However, I've noticed that transitioning from a Windows program to an Ubuntu app or vice versa is very slow. Once the app finally appears, it seems okay. But then going back to an app in the other OS, quite a hesitation. If I've got 5-6 apps open (nowhere near a problem in Ubuntu only) the system can really crawl.

Further, I've noticed that after a boot, my system idling uses something less than 240MB of RAM and no swap. Start a VM, of course RAM usage climbs to the predictable 1.3GB plus any other apps and swap starts getting used. However: shut down the VM, and RAM usage indicates remaining at the same 1.3GB-plus, and swap is still up around 2GB. Weird because generally if you shut down a program RAM usages goes back down. I have to reboot to get the usage graph back to normal. I've been thinking of doubling my RAM to 4GB just to eliminate the swapping and maybe improve the speed, it's not really that expensive. However it's still stupid if you've got half your RAM sitting there unusable.

Any thoughts, suggestions?

---

### Post by kpkeerthi on 2008-02-15
How much RAM did you allocate to your guest OS? Too much to guest is actually bad for your host as you will find it swapping soon. With 2GB available from host, I prefer not more than 640 MB for the guest.

As for your question about linux not recovering RAM, see [Where did my memory go?]("http://ubuntuforums.org/showthread.php?t=624148")

---

### Post by ArtInvent on 2008-02-15
That's helpful and a quick response, thanks. Actually I was messing with it last night and decided to lower the RAM assigned to the VM. I initially had it at just over half of total about 1.2GB. I had been running an  XP app that was really RAM  hungry, but now I've got a Linux native app to replace that. Also I was not really anticipating going back and forth between the two OS's as much as I actually do. I still use the Adobe CS2 suite however, so I do need a fair bit of RAM for XP. At any rate, I've put it down to about 850MB and that seems to help quite a bit. Swap is hardly used at all.

As I read the situation on that other thread, Linux will intentionally leave closed apps in RAM until it's needed by other apps, meaning I shouldn't worry so much about what the graph looks like. And yet, when I shut down a normal Ubuntu app, the graph does drop immediately. Actually, I just shut down the VM (now using 750MB) and the graph immediately dropped as it ought to. 

I guess the lesson is to not use more than about 30-40% of your total RAM for a VM. I will still probably double my RAM but at least now I shouldn't need to triple it.

VirtualBox is impressive but it desperately needs 3D acceleration. That's about all that stops it being a true equivalent of a dedicated machine, but it's a big omission.

---

