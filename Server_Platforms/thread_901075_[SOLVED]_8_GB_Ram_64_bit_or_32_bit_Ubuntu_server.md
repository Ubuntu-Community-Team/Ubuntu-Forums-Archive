---
title: "[SOLVED] 8 GB Ram 64 bit or 32 bit Ubuntu server?"
date: 2008-08-26
forum: Server Platforms
---

### Post by TusharG on 2008-08-26
Hi all,
   I've purchased Dell Xeon Quad Core Server with 8 GB Ram and 12 MB Cache memory. The server will be mainly used for compiling the code. I've installed 32 bit Ubuntu server edition on the server. The server shown 8 GB ram when checked with cat /proc/meminfo however most of the posts say that 32 kernal cannot take the advantage of 4+ GB Ram. I'm also fine in installing 64 bit Ubuntu. Its basically I have to use 32 compilers to compile the code. Most of the developers are demanding 32 bit OS. 
  What I'd like to know is can i safely run Ubuntu 32 bit server edition with 8 GB Ram? Can 32 bit Ubuntu take the advantage of 8 GB Ram? Its not only processor important to me but ram is also important as this server will be shared between 8 developers who will be compiling their code in their own directories in parallel. The code compilation usually takes 1.5 hours on 2.5 GHZ machine with 2 GB Ram. I'd like to speed up the compilation as well.

---

### Post by cariboo on 2008-08-26
As far as I know a compiler doesn't care if the operating system is 32 or 64bit, it is just a matter of setting the correct flags. Also maybe start dropping hints to your developers that there a not a whole lot of 32 bit systems being sold anymore, so they should compile their software for both 64 and 32 bit systems.

Jim

---

### Post by kerry_s on 2008-08-26
if you want to use 32bit, i would go with debian  and use the bigmem kernel or you could rebuild the ubuntu kernel with large memory support.

[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

here's the net installer, at the package selection part just uncheck the desktop and check the server stuff you want.

after the install, just log in  as root and apt-get the bigmem kernel.

apt-get install linux-image-686-bigmem

---

### Post by gtdaqua on 2008-08-26
> **TusharG said:**
> Hi all,
   I've purchased Dell Xeon Quad Core Server with 8 GB Ram and 12 MB Cache memory. The server will be mainly used for compiling the code. I've installed 32 bit Ubuntu server edition on the server. The server shown 8 GB ram when checked with cat /proc/meminfo however most of the posts say that 32 kernal cannot take the advantage of 4+ GB Ram. I'm also fine in installing 64 bit Ubuntu. Its basically I have to use 32 compilers to compile the code. Most of the developers are demanding 32 bit OS. 
  What I'd like to know is can i safely run Ubuntu 32 bit server edition with 8 GB Ram? Can 32 bit Ubuntu take the advantage of 8 GB Ram? Its not only processor important to me but ram is also important as this server will be shared between 8 developers who will be compiling their code in their own directories in parallel. The code compilation usually takes 1.5 hours on 2.5 GHZ machine with 2 GB Ram. I'd like to speed up the compilation as well.

Why wont this work on 64-bit Ubuntu? It should. 32-bit will work on 4GB+ (PAE), but 64-bit will be native and the Quadcore Proc you have can better be addressed a native 64 bit OS (although, intel neither does native 64bit nor native quadcore).

Performance, especially in your 45nm Penryn, should be significant if you are running on 64 bit. You see, 64 bit has little or no advantage in a 32-bit environment (64-bit OS on <4 GB RAM). But sure does in a native environment (64bit OS on >4GB RAM).

---

### Post by TusharG on 2008-08-26
Ok Thanks a lot for your suggestions. Right now I have installed 32 bit Ubuntu and I'm gonna measure the compilation period on the same. After that I'll be installing 64 bit and compile the code again. 
  My only point was I installed 32 bit Ubuntu and it confused me as it detected the 8 GB ram without a issues, the remaining point was can it really use 4+ GB ram? under 32 bit OS?

---

### Post by gtdaqua on 2008-08-26
> **TusharG said:**
> Ok Thanks a lot for your suggestions. Right now I have installed 32 bit Ubuntu and I'm gonna measure the compilation period on the same. After that I'll be installing 64 bit and compile the code again. 
  My only point was I installed 32 bit Ubuntu and it confused me as it detected the 8 GB ram without a issues, the remaining point was can it really use 4+ GB ram? under 32 bit OS?

As you saw urself, it detects 8GB without any prob.

---

### Post by insane_alien on 2008-08-26
it uses 8GB by assigning the memory in blocks rather than the usual way. causes some inneficiencies in storage(things will take up more RAM and so on).

i'd recommend 64-bit though. it natively accesses the RAM and is generally faster at compiling. and you can compile a binary for any arcitecture on any other architecture. just a matter of setting a few flags.

also, when the devs switch to 64-bit(which will probably happen in the next couple of years as commodity computers exceed the 4GB RAM threshold) the 64-bit OS will be able to compile the 64-bit code significantly faster as it doesn't need to use multiple registers.

---

### Post by TusharG on 2008-08-27
Thanks everyone on discussing the topic. I'll install 64 Bit Ubuntu server edition.

---

