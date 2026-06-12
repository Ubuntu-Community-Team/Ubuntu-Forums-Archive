---
title: "NVidia ging Open Source? Well, not quite"
date: 2022-06-06
forum: The Cafe
---

### Post by grahammechanical on 2022-06-06
Read the link starting at the heading: NVIDIA open-sources GPU kernel modules

[https://ubuntu.com/blog/state-of-iot-may-2022](https://ubuntu.com/blog/state-of-iot-may-2022)

I am not sure what to make of it all.

Regards

---

### Post by zebra2 on 2022-06-08
I'm not sure either. in fact I have never used Nvidia.  However over the years I have used software that was part proprietary and part open source.  Their license required them to provide/release the open source code when requested but had no obligation to release the proprietary part of the code. It is possible that Nvidia wants to partner with the Nouveau development for that part of the driver and keep the rest of the driver proprietary. That idea would require agreement with the Kernel/Linus in order to get it to work because the drivers are provided by the kernel. So the kernel would have an Nvidia driver that is part open and part proprietary.  
What gets me is the writer of the article seems to want to put the blame for the lack of Nvidia support entirely on Linus and not on Nvidia.  I don't know much about that.

---

### Post by #&amp;thj^% on 2022-06-08
> **grahammechanical said:**
> Read the link starting at the heading: NVIDIA open-sources GPU kernel modules

[https://ubuntu.com/blog/state-of-iot-may-2022](https://ubuntu.com/blog/state-of-iot-may-2022)

I am not sure what to make of it all.

Regards

How funny I was just reading this: [https://developer.nvidia.com/blog/nvidia-releases-open-source-gpu-kernel-modules/](https://developer.nvidia.com/blog/nvidia-releases-open-source-gpu-kernel-modules/)
while helping another user on another forum.
FWIW I'm not sure what to make of it yet, I guess time reveals all.
I'm using something similar on another OS. works pretty good, I mean we are talking about Nvidia now. :)

---

### Post by grahammechanical on 2022-06-08
The Ubuntu post mentions something that the Nvidia post does not mention.

> Also, one can&#8217;t avoid noting that most modern graphics drivers still  reside in the closed-source firmware and userspace components. [Hector Martin from Asahi Linux criticised NVIDIA]("https://twitter.com/marcan42/status/1524615058688724992") for moving most of the kernel driver into the firmware, called into by the open-sourced components. 

> In August 2020, NVIDIA unveiled its [open-source GPU documentation GitHub page]("https://github.com/NVIDIA/open-gpu-kernel-modules"), **generating suspicions of it conceding its purely proprietary culture**.

So, let us not get carried away. The owners of Nvidia have not been converted to FOSS principles. I am not fanatical about open source. I do remember the problems users had with hybrid graphics where Nvidia drivers provided better functionality on Windows than they did on Linux. And the company did not seem to care.

Regards

---

### Post by #&amp;thj^% on 2022-06-08
> **grahammechanical said:**
> 
So, let us not get carried away. The owners of Nvidia have not been converted to FOSS principles.

Regards

True That!! I think the talk right now is just that>>Talk.
I think they are helping both in the fact>  &#8220;The new NVIDIA open-source GPU kernel modules will simplify installs and increase security for Ubuntu users,
is only part of the quote>>>full quote:
> Canonical

&#8220;The new NVIDIA open-source GPU kernel modules will simplify installs and increase security for Ubuntu users, whether they&#8217;re AI/ML developers, gamers, or cloud users,&#8221; commented Cindy Goldberg, VP of Silicon alliances at Canonical. &#8220;As the makers of Ubuntu, the most popular Linux-based operating system for developers, we can now provide even better support to developers working at the cutting edge of AI and ML by enabling even closer integration with NVIDIA GPUs on Ubuntu.&#8221;

In the coming months, the NVIDIA Open GPU kernel modules will make their way into the recently launched Canonical Ubuntu 22.04 LTS.
Now what that means for older drivers such as 340 && 390 is still an unknown.

---

### Post by zebra2 on 2022-06-09
After doing some google-ing  regarding Intel's performance in the gpu area it seems that they (Intel) have made some serious advances in the GPU area.  Since Intel appears to have captured a lot of Nvidia's user base in the Linux market mostly because of lack of Driver support It makes sense that Nvidia is open sourcing their drivers.  If this is the reason for their move it says much about the influence of Linux on the market and especially as it relates to canonical.

---

### Post by #&amp;thj^% on 2022-06-09
> **zebra2 said:**
> After doing some google-ing  regarding Intel's performance in the gpu area it seems that they (Intel) have made some serious advances in the GPU area.  Since Intel appears to have captured a lot of Nvidia's user base in the Linux market mostly because of lack of Driver support It makes sense that Nvidia is open sourcing their drivers.  If this is the reason for their move i**_t says much about the influence of Linux on the market and especially as it relates to canonical_**.
We're getting there slowly, I'm still cautious about opensource && nvidia....they have a track record of disappointments. (You'll get what they give period.)

---

