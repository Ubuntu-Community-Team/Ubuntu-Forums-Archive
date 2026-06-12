---
title: "Can a Linux machine push Crysis in Virtual Machine??"
date: 2008-07-01
forum: Virtualisation
---

### Post by grimlock838 on 2008-07-01
Perhaps a suggestion for a review or this thread ... Someone to install Virtual Box vs VMWare on same machine (I personally was thinking Intel Core Duo or Quad/ AMD equivalent with maxed out RAM and killer GPU)  and see which can push Crysis/Call or Duty 4 on top of a lightweight Host (maybe using XFCE Ubuntu?)

Now for a really wild Idea:

Install both on a same pimped out machine but the Host OS as Windows Xp Pro/Vista trying to do the same ... Run Crysis in aforementioned virtual machine. Yes,yes I know why would one do this when Windows can run it nativity? To show Linux's superior I/O capacity. (Just a theory) 

And I believe more importantly to show how much and far hardware has come along as well as showing how much Linux has matured to the point of being ridiculously awesome.

Wild Idea 2

same as above but in Mac OS X Vs Linux. This I think would be absolutely fascinating to the nerd in me and to at least a million others out there?!

I think this would garner massive attention on the Web and maybe be picked up by Wired or Phoronix who would be able to really do this to the Nth Degree! Perhaps adding another test ... Decoding/Encoding an HD Movie.

And please anyone who has already done this or read about something similar please POST the link I am starving for more Linux Vs. Vista/XP vs Mac! 
**** it could even be done with a Psystar machine as it is the only one (to my knowledge) which would be truly OS neutral. Of Course if someone took the time to do all this on their machine it would have to be able to run Mac OS X (not an easy task to fill).

What can I say guess it is just the old reporter in me ... :popcorn:

---

### Post by ene_dene on 2008-07-01
I can hardly run Heroes of Might and Magic 3 on Virtualbox. I don't think that you can play games on virtual machines.

---

### Post by Deicist on 2008-07-01
Most Virtual machines solutions don't offer much in the way of 3D acceleration support.  I think Vmware has DirectX 8 support, but that's about it.

Without 3D acceleration, you're pretty limited in what games you can run.

---

### Post by grimlock838 on 2008-07-01
Ok, I forgot Crysis runs in Direct X9 plus higher later on.
what was a kill graphics intensive game that runs Directx 8 from a few years ago? Or for that matter Encoding/decoding An HD movie is still very CPU intensive what are other benchmarking programs that could be used?

---

### Post by acron1 on 2008-07-03
VMware has a beta out that can supposedly do DirectX9 I think. But from what I understand 3D acceleration is very poor to play most games let alone Crysis.

---

### Post by llib1234 on 2008-07-04
Wait until the final release of VMware 6.5 and then try it, but only on a really fast hardware, like a Geforce GTX 280 or similar.

---

### Post by dacorr on 2008-07-04
Virtual machine software such as VMWare install a virtual abstraction layer between the hardware and the OS, they do not actually use the physical hardware more of an emulated version.

So even with a powerful graphics card the virtual machine wont use it.

You can create a hybrid virtual machine where the guest OS knows it is a virtual machine (typically they dont) and have it directly access the graphics card, well share it.

In some instances the virtual machine will directly access the host resources without the host knowing but that is usually with HardDrive and CPU.

As far as i am aware VMware does not allow you at the moment to specify physical hardware, but the virtual machine .vmx file would be the place to look to see if you can manually configure it.

If i can help PM me

Dac

---

