---
title: "Running Ubuntu 10.04 AMD64 server edition on I686 Machine"
date: 2010-12-29
forum: Virtualisation
---

### Post by DaGeek247 on 2010-12-29
I have a 32-Bit Ubuntu 10.04 desktop installation. I also have on it, Oracle VM VirtualBox 4.0.0. I downloaded Ubuntu 10.04 Server edition 64-Bit. I read somwhere that VirtualBox needed 64-bit to run, which is why i did that. The problem is that when i boot the downloaded iso, it says i need a 64-Bit machine to run. (Not VirtualBox, Ubuntu Server says it needs and AMD64 processor to run.)

My question:
How do i Virtualize an AMD64 Processor on and I686 PC with VirtualBox? or, do i need some other software to do this?

It took forever to just download the iso I already have and, i would like to have it work.

Thanks for the help.

---

### Post by supershin on 2010-12-29
I believe this is want you're looking for.

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests]("http://www.virtualbox.org/manual/ch03.html#intro-64bitguests")

> If you want to use 64-bit guest support on a 32-bit host operating system, you must also select a 64-bit operating system for the particular VM. Since supporting 64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this support upon explicit request.

On your virtual machine, ensure it is setup to have a 64bit OS then try to install.

EDIT: If you did above and Ubuntu server says you need an AMD64 processor then the only thing i can think of is going to settings->processor and look at the options there.

---

### Post by DaGeek247 on 2010-12-29
> You need a 64-bit processor with hardware virtualization support

I have a 32-Bit processor with a 32-Bit OS. do i just need to download the 32-Bit version?

---

### Post by supershin on 2010-12-30
Yes. Download the 32-bit version of Ubuntu server. You should have no problems with that.

If you had a 64-bit processor then you could have had 32-bit/64-bit host and guest OSes.

---

### Post by DaGeek247 on 2010-12-30
thanks. its being downloaded.

---

