---
title: "Virtual Disk in RAM"
date: 2012-06-19
forum: Virtualisation
---

### Post by beloved88 on 2012-06-19
Hey all!
Anyone ever launch VM's using virtual disk images entirely in RAM?
   I'm looking at purchasing a new PC, and for everything I do I think 4 or 8 GB of RAM is sufficient, but I thought of something I'd like to try, and wondering if anyone else has done it.  
   I'd like to launch VMs to try various setups for a few of the projects I'm working on.  I figure I can define the VHD file under the /tmp directory, and it will exist entirely in RAM.  If figure for that, I might actually need the additional RAM to justify getting adding RAM (I'll probably buy my own and add it) for 12 or 16 GB.
   Just wondering if anyone else has tried it and any experiences.

---

### Post by teeks99 on 2012-06-20
I *think* I tried it a while back, but it wasn't very useful as I didn't have enough RAM to make a very practicle disk image. If you've got enough RAM to make it work, and aren't worried about losing data if you have power issues, I think it should work.

Also I don't believe that by default /tmp is hosted in ram. Try /dev/shm (or /run/shm if it exists). 

I've also done network boots to ram, but that requires setting up a server seperate from your VM infrastructure to push the image out.

---

### Post by Baulageng on 2012-06-26
A virtual disk (also known as a [virtual]("http://searchservervirtualization.techtarget.com/definition/virtual") drive or a [RAM]("http://searchmobilecomputing.techtarget.com/definition/RAM") drive) is a file that represents as a physical disk drive to a guest operating system. The file may be configured on the [host]("http://searchcio-midmarket.techtarget.com/definition/host") and also on a remote file system. The user can install a new operating system onto the virtual disk without repartitioning the physical disk or rebooting the host machine.

---

