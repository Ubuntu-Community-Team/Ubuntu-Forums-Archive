---
title: "dual 2 cpu version of ubuntu?"
date: 2005-02-27
forum: Server Platforms
---

### Post by bwiese on 2005-02-27
I have a dual cpu server that I would like to install ubuntu on... the install disk started up and said it was only going to use 1 cpu though. =(  One of my main reasons for promoting people to use GNU/Linux is because 'dual cpu' is free -- no extra licensing like with NT/2K/XP stuff from micro$oft.  
Is there any work to create a 2-cpu version?  
Would it have to be a separate branch?  
Can anyone recommend a quick knoppix-like (fast hw autodetect and install) gnu/linux distro suitable for server installation? 

I thought ubuntu might be it, but this cpu thing has got me.  I love what you've done though, especially with the custom/expert installs and bare requirements of only 32mb-- thats what gnu/linux is about, especially for older hardware and reusing technology as [www.computers4africa.org](www.computers4africa.org) does. =)

Brian - brianwiese.net

---

### Post by Chris C on 2005-02-27
Just go to synaptic - base system - linux image *86 smp and pick the one that best suits your system. More than one CPU is SMP.

---

### Post by thorndike on 2006-02-04
It is my understanding though, that there are NO SMP kernels created for P3 servers.  My servers currently have 2 Xeon processors in them, but I am unable to utilize the second.

I was only able to find SMP kernels for  AMD and P4 cpus.  Did I miss the right ones?

Thanks,

Thorndike

---

### Post by venzen on 2006-02-05
Hi,

Multi-processor support is a proud linux tradition and many architectures are supported... certainly any kernel image with both '686' and 'smp' in the name will support PII, PIII and PIV multi-cpu's. This can be seen from the package description in synaptic or dselect.

For two PIII processors you want to install **linux-image-2.6.12-10-686-smp** with synaptic or by issuing:

```
sudo apt-get update
```

and then:

```
sudo apt-get install linux-image-2.6.12-10-686-smp
```

---

### Post by LordHunter317 on 2006-02-05
[QUOTE=bwiese]I have a dual cpu server that I would like to install ubuntu on... the install disk started up and said it was only going to use 1 cpu though. =(  One of my main reasons for promoting people to use GNU/Linux is because 'dual cpu' is free -- no extra licensing like with NT/2K/XP stuff from micro$oft. [/quote]Dual CPU is free for Windows XP Professional.

Dual-core is free for any version of Windows XP.  So it's not a big gain.  Actually, strictly speaking, as many cores as you can fit on a die are free for any version of Windows XP.

> [I thought ubuntu might be it, but this cpu thing has got me.You just need to install an SMP kernel.

---

