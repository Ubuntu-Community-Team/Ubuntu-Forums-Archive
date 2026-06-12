---
title: "Slow Nvidia Graphics"
date: 2009-11-08
forum: Virtualisation
---

### Post by mooreted on 2009-11-08
AMD Phenom Quad Core
3GB RAM
Nvidia 8800GT 512

Running Windows 7 Ultimate 32bit as host and Ubuntu 9.10 Guest in Virtualbox 3.08. Everything is running great except graphics. I turned of compositing on the Ubuntu guest. Set performance to High Performance on the Windows host, tried VT/x on and off; nothing helps so far.

Screen redraws and dragging windows is very, very slow.

I should mention that on my Debian VM, everything works perfectly; you really can't even tell it's running as a VM.

---

### Post by dzon65 on 2009-11-08
In 8.10 they suggested the 180 driver,but graphics worked far better for me using the 177 version.In 9.10 I'm using the 185 version which works very nice.Perhaps you should try one of the other drivers?

---

### Post by mooreted on 2009-11-08
I'm currently using Nvidia driver version 191.07 in Windows. Ubuntu is the guest OS. Are you saying to try to downgrade the Windows driver?

---

### Post by mooreted on 2009-11-08
Checking glxinfo and glxgears, 3D acceleration is working. Also, streaming video works fine. It seems to be a 2D acceleration problem.

---

### Post by catco_designs on 2009-11-08
> AMD Phenom Quad Core
3GB RAM
Nvidia 8800GT 512

The issue may lie with the system running 32 bit instead of the capabilities at 64 bit.
although 32 bit will work fine for a 64bit system you are already downgrading by running 32bit

---

### Post by mooreted on 2009-11-08
That's an idea. However, debian runs perfectly. That seems to point to an Ubuntu problem.

I've had nothing but problems with 64bit OS's so I'm leery of using them.

---

### Post by mooreted on 2009-11-08
Well, it would have been nice to see what the difference is. I'm beginning to think Windows 7 is causing issues. It is starting to slow down.

I think I've learned all I need about Windows 7. I'm going to install 9.10 and be done with it. I really just don't like running Windows.

Thanks for all the replies.

---

### Post by catco_designs on 2009-11-08
FYI the 64 bit version of Ubuntu9.10 seems to run just fine

---

### Post by mooreted on 2009-11-08
Until you try to run Wow or Second Life and a host of other software from developers that aren't coding for 64-bit.

---

### Post by catco_designs on 2009-11-09
It is my understanding that 32 bit programs can work in a 64 bit system. It is your option though you could go install Windows 95 in it and it won't affect me either.
In 32bit emulation Wine can work with many games...

---

### Post by mooreted on 2009-11-09
Just speaking from my own personal experience with both Windows and Linux 64 bit systems. I had more problems with them than 32 bit systems.

---

