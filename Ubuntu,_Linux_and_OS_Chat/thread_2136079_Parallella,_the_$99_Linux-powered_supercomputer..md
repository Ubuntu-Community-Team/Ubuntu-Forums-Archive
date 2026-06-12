---
title: "Parallella, the $99 Linux-powered supercomputer."
date: 2013-04-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Linuxratty on 2013-04-16
Here is something to brighten your day.
> 
What Adapteva has done is create a credit-card sized parallel-processing board. This comes with a dual-core ARM A9 processor and a 64-core Epiphany Multicore Accelerator chip, along with 1GB of RAM, a microSD card, two USB 2.0 ports, 10/100/1000 Ethernet, and an HDMI connection. If all goes well, by itself, this board should deliver about 90 GFLOPS of performance, or — in terms PC users understand — about the same horse-power as a 45GHz CPU.
[B]
This board will use Ubuntu Linux 12.04 for its operating system.[/B] To put all this to work, the platform reference design and drivers are now available.
[http://www.zdnet.com/parallella-the-99-linux-supercomputer-7000014036/](http://www.zdnet.com/parallella-the-99-linux-supercomputer-7000014036/)

---

### Post by ssam on 2013-04-16
I ordered one when it was on kickstarter :-)

---

### Post by ibjsb4 on 2013-04-16
Gut an old laptop and turn it into a supercomputer me wonders

---

### Post by Linuxratty on 2013-04-16
> **ssam said:**
> I ordered one when it was on kickstarter :-)
Have you got it yet?

---

### Post by ssam on 2013-04-16
> **Linuxratty said:**
> Have you got it yet?

the makers have just got the first 10 prototype boards [http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/456048?ref=email&show_token=89caf0c07627d711](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/456048?ref=email&show_token=89caf0c07627d711) so it will still be a while before they reach the kickstart backers

---

### Post by Dragonbite on 2013-04-17
I think this is going to be similar to the Raspberry Pi for parallel computing, but on a smaller scale.  Looks interesting and is another place where Linux will excel while Windows likely won't even get in the doors (for a while at least).

---

### Post by montag dp on 2013-04-19
This would be awesome for the MPI computational fluid dynamics code I'm working on.  :)

---

### Post by 3Miro on 2013-04-20
Am I reading it wrong or does it come with only 1GB of RAM. This makes it pretty useless, doesn't it?

---

### Post by slooksterpsv on 2013-04-20
Not really, 1GB of RAM is pretty good depending on what you need it to do. Granted PC min spec now-a-days is 4GB about to transition to 6GB, but 1GB is pretty dang good for that size. You figure most android devices come with 512MB for low end, 1GB for Med and 2GB for High End. Android 4.2 devices are generally running 2GB, but it depends on if you really need the RAM. Pi only comes with 512MB IIRC; so yeah 1GB is awesome for an ARM board. =D

---

### Post by slooksterpsv on 2013-04-21
I just read how the Epiphany Multi-Core accelerators work, oh my gosh, that thing is going to change computing experience as we know it. This thing is amazing, I need to get one =D

---

### Post by 3Miro on 2013-04-22
> **slooksterpsv said:**
> Not really, 1GB of RAM is pretty good depending on what you need it to do. Granted PC min spec now-a-days is 4GB about to transition to 6GB, but 1GB is pretty dang good for that size. You figure most android devices come with 512MB for low end, 1GB for Med and 2GB for High End. Android 4.2 devices are generally running 2GB, but it depends on if you really need the RAM. Pi only comes with 512MB IIRC; so yeah 1GB is awesome for an ARM board. =D

They are not selling a phone device where 1GB of RAM is indeed plenty. They are selling a device with a high number of FLOPS, i.e. floating point operations. For any serious math, 1GB of RAM is not enough. Also, ARM cannot be paired with a regular CPU the same way GPUs can be used to accelerate computations.

This thing may have a future, but it is pretty useless right now.

---

