---
title: "Server kernel vs i686 kernel"
date: 2006-04-22
forum: Server Platforms
---

### Post by kozimodo on 2006-04-22
What are thoughts on the new Dapper server kernel? If I understand what I'm reading correctly, the generic server kernel is for all i386 architectures and there is no specialized one for i686 (recent CPUs). Is it better to use the server kernel or the i686 kernel for a box whose only remaining function is as a server.

---

### Post by rocktorrentz on 2006-06-16
I am also interested in the answer to this question. Does anyone know it?

---

### Post by gimpologist on 2006-06-22
Yup, make that three that would love to know.

---

### Post by gimpologist on 2006-06-22
From doing a little searching on the forums and on the net, I've found a little information to hopefully kickstart this thread again...

1) The Ubuntu Server ISO uses the 386 kernel to begin the boot process since this is the most compatible kernel for most machines.

2) However, although the kernel that is used on the server install is 2.6.15-23-server, it is based off the 686 kernel (totally do not know if this is the case, but from this [thread]("http://ubuntuforums.org/showthread.php?t=197884&highlight=dapper+server+kernel") it seems that this is what's going on.

3) When you apt-get dist-upgrade, the following kernel is used after reboot (2.6.15-25-server).

So the question is:

What's better to use the linux-image-686 kernel that's optimized for Intel Processors > Pentium Pro or the 2.6.15-25-server kernel that's being used now? (I have a PII-366mhz)

Any explanation between the kernels would also be great!

Thanks

---

### Post by mem on 2006-07-06
... well from my test, using the -686-server kernel removed support for more than 4GB of memory.... so i had to go back to the default 2.6.15-23-server. It's a shame because i have 4 P4's in this box...

---

### Post by mandrakethepenguin on 2006-07-06
I found an entry on Ubuntu Wiki that explains the kernels.  [Here]("https://wiki.ubuntu.com/KernelServerRoadmap") is the explanation of the server kernel.

---

### Post by moopere on 2006-07-09
> **mem said:**
> ... well from my test, using the -686-server kernel removed support for more than 4GB of memory.... so i had to go back to the default 2.6.15-23-server. It's a shame because i have 4 P4's in this box...

Really?  How does this work/what motherboard?  I had the impression (obviously wrong) that P4's were not SMP capable and that you had to spring for Xeons if you wish for SMP.

Cheers,
Craig

---

### Post by TonioRoffo on 2006-07-12
So if I understand correctly, as long as I keep using dapper server, memory over 4GB will be detected out of the box?

Thanks

---

### Post by Kadin2048 on 2008-03-13
> **TonioRoffo said:**
> So if I understand correctly, as long as I keep using dapper server, memory over 4GB will be detected out of the box?

Thanks

My understanding (which is limited!) is that the -server kernels support PAE for 32-bit architectures, which is essentially a hardware hack allowing you to have more than 4GB of RAM in a 32-bit address space.  It also uses a different scheduling model (deadline instead of fair?) which is apparently preferred for servers.

I've never done, and I've never seen, any really good metrics as to what kind of performance you can get by changing from 686 to server.  I think the memory would be the really big reason for most users.

Personally right now I have an old dual-proc PIII and I'm running the 686 kernel just fine. Apt-get keeps trying to move me to the -server kernel though, so sometime I'll probably let it go and see if everything still works okay.

At least when I installed originally, I got stuck with the 386 kernel (!) which doesn't support SMP.  So if you're doing a fresh install from the Dapper server disc, make sure to run apt-get update / apt-get upgrade right away and let it move you to a real kernel.

---

