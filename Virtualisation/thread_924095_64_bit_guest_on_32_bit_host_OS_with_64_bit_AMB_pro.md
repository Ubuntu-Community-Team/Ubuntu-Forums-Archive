---
title: "64 bit guest on 32 bit host OS with 64 bit AMB processor?"
date: 2008-09-19
forum: Virtualisation
---

### Post by shjoity on 2008-09-19
is it possible, host is windows vista which despite not being supported by vmware server works fine. does the host 32 bit kernel make 64 bit not work? do i have to upgrade both to 64 bit?

ps i hate vista but its not my computer

---

### Post by lazyart on 2008-09-19
try it and find out.  vmware seems to support 64 bit guests on 32 bit host, but i would imagine that performance would be poor.

---

### Post by dark_phantom on 2008-09-20
That's an odd situation, but like the previous poster said you can try.  The main reason for a 64-bit OS is to access a have access to more memory then a 32-bit OS.  Of course there are other benefits to a 64-bit OS, but not most regular desktops.  JMHO.

---

### Post by bradmkjr on 2008-09-20
> **lazyart said:**
> try it and find out.  vmware seems to support 64 bit guests on 32 bit host, but i would imagine that performance would be poor.

It wouldn't be virtualization, it would be emulation. VMware products are virtualization products, they are unable to operate at a different cpu then that which is present in the host system.

Programs, such as the old virtual pc, for MAC, was an emulator which emulated the x86 chipset on a Macintosh power pc. They where able to do so, but at a very high cost in the way of performance. There are products out there, which can run a 64bit guest os on a 32bit host, but they are using emulation, not virtualization. Virtualization requires the native hardware to be present to "share", compared to emulation which allows the software to generate any needed hardware, from a atari gaming system emulator to an iphone emulator. 

Hope this makes it a little more clear,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

### Post by shjoity on 2008-09-30
The real question is weather vmware virtualization is done at the hardware or software level (kernel vs user). It isnt neccicarily emulation if there is 64 bit hardware bradmkjr.

some of it certainly is done at the kernel level and therefore could use 64 bit even if the host did not, but does the host kernel make this 64 bit *virtualization* impossible?

---

### Post by EchoBeach on 2008-10-02
My Vista laptop is using AMD Turon64 x2.
I have VMWare Server 1.0.7 installed with a 8.04 64bit VM.
It's 'working' except that I can't make a connection with the laptop's wireless card - so no internet. :-(
Having to use Firefox on Vista in the meantime!
Echo

---

### Post by originalsurfmex on 2008-11-10
i am in a similar situation.  at work i can't install another os, however maybe i can do vmware and ubuntu 64.

i want to use blender, kerkythea, indigo, voodoo - all those programs that work better in linux and even better in 64 bit...

...will i see a performance advantage on the vmware?

we have:
xp professional
amd 64bit athlon x2

---

