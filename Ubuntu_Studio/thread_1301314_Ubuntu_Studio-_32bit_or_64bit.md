---
title: "Ubuntu Studio- 32bit or 64bit"
date: 2009-10-25
forum: Ubuntu Studio
---

### Post by Vigh on 2009-10-25
Hi, 
  I was just wondering, I am going to download the rc 9.10 of ubuntu and am going to manually install realtime kernel and studio repos. which version of ubuntu is best for audio production work? cheers Ant =-)

---

### Post by AutoStatic on 2009-10-26
That depends on the configuration of your system, especially the amount of RAM and type of CPU.
Also, I would advise to wait a few days and install the final release of 9.10.

---

### Post by trulan on 2009-10-26
I have a 32 bit install of 9.10 on 32 bit processor laptop, and a 64 bit install of 9.10 on my AMD64 desktop.  I honestly can't tell a difference in performance.  9.10 is performing well for me though, much better than Jaunty IMO, as far as stability on the real time kernel, especially with a decently heavy processor load.

---

### Post by darkksyde on 2009-10-27
32bit unless you have more than 4gb's of ram

---

### Post by VertexPusher on 2009-10-27
> **darkksyde said:**
> 32bit unless you have more than 4gb's of ram
Ubuntu 32bit can't use more than **3**GB.

---

### Post by AutoStatic on 2009-10-27
> **VertexPusher said:**
> Ubuntu 32bit can't use more than **3**GB.Unless you use the PAE kernel.

---

### Post by ttados on 2009-10-27
Like AutoStatic said, you can only have around 3GB unless you use PAE. I think with PAE you can get up to like 32GB or 64GB...something crazy.

I'm not sure if you would be able to tell a considerable difference in audio work. You might be to see a speed boost in something like converting file types though. Personally I would suggest getting the 64bit version if you have a 64bit cpu, you might as well use it.

---

### Post by GraysonPeddie on 2009-10-27
I'd also go with 64-bit version of Ubuntu Studio, which is great if you plan to upgrade to 8GB of RAM. This is useful if you have samples of 1GB or higher (especially grand piano sample, which can use over 2GB or more).

You can get a really nice sounding grand piano and acoustic guitar sample, which could rival those professional keyboards costing 2 or 3 grand. How about acoustic bass guitar for some nice and smooth jazz? :) Try to imagine...

The doors to very large samples will open once you have more than equal to 4GB of RAM (8GB recommended).

---

### Post by VertexPusher on 2009-10-28
> **AutoStatic said:**
> Unless you use the PAE kernel.
Are you suggesting to run audio production on the PAE-enabled server kernel, only to avoid going 64bit?

---

### Post by AutoStatic on 2009-10-28
No, I just wanted to point out that Ubuntu 32bit can use more than 3Gb of memory. I'm not suggesting anything.

---

### Post by Totalchaos on 2009-10-28
64bit gives you better performance. The only reason for using 32bit can be wineasio. I recommend 8.04. It has the most stable RT kernel to-date ;);)

---

### Post by trulan on 2009-10-28
While time will tell just how stable  9.10's RT kernel will be,  IMO it is even more stable than 8.04.  I can certainly run higher processor loads without x-runs using 9.10.  Things would start to crash on 8.04 if my CPU hit 50%.  The breaking point for 9.10 is above 70%.

Nevertheless, 8.04 is still known for its stability after being out for a year and a half, which is something that cannot be said about 9.10.

---

### Post by bluesscream on 2009-10-30
> **Totalchaos said:**
> 64bit gives you better performance. The only reason for using 32bit can be wineasio. I recommend 8.04. It has the most stable RT kernel to-date ;);)

wineasio for 64bit:
```
wget http://homerecording.de/~4damind/hr/wineasio-x_0.3.deb
sudo dpkg -i wineasio-x_0.3.deb
regsvr32 wineasio.dll
```
I prefer 9.10 64bit, kernel 2.6.31-9-rt, with good reason. Free a partition and give it a try :D.

---

