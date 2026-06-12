---
title: "Open CL/GPGPU on Linux?"
date: 2010-01-29
forum: The Cafe
---

### Post by Ravernomina on 2010-01-29
Hey All... just wonder if Linux can run OpenCL/GPGPU... Also Is the Kernel Itself written to its aspect like the Mac OS X Kernel? Thanks!
Ravernomina

---

### Post by Ravernomina on 2010-01-29
BUMP???? Linux Doesnt have this?

---

### Post by NightwishFan on 2010-01-29
I have heard that OpenCL is supposed to be cross platform, but I do not see where you could actually make use of it yet, unless you are a developer.

Do not take my word for it though.

---

### Post by Eremit on 2010-01-31
If you have an ATI graphics card you can utilize OpenCL on it through the ATI Stream SDK. With newest catalyst drivers and "nopat" kernel parameter set it works with karmic (officially only jaunty is supporetd).

[http://developer.amd.com/gpu/ATIStreamSDK/Pages/default.aspx](http://developer.amd.com/gpu/ATIStreamSDK/Pages/default.aspx)
[http://radialmind.blogspot.com/2010/01/ati-stream-technology.html](http://radialmind.blogspot.com/2010/01/ati-stream-technology.html)

Regarding cross-platform: OpenCL is only a defined standard and not an implementation. Apple has it's implementation, nvidia has an implementation (through cuda) and now ATI has one too.

---

### Post by ssam on 2010-01-31
[http://www.phoronix.com/scan.php?page=news_item&px=Nzc4NQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzc4NQ) sums it up well.

also have a look at the llvm project

i dont think the mac os x kernel does any gpgpu stuff itself.

---

### Post by Paqman on 2010-01-31
Dunno about OpenCL, but CUDA works if you've got an Nvidia card. I use it for Seti@home, it's massively increased the speed of it even though i've got a good processor and a crummy GPU.

---

### Post by Xbehave on 2010-01-31
> **Paqman said:**
> Dunno about OpenCL, but CUDA works if you've got an Nvidia card. I use it for Seti@home, it's massively increased the speed of it even though i've got a good processor and a crummy GPU.
Does openCL/CUDA interfere with graphics performance (i.e do you only use it when not at your PC)

---

### Post by Ravernomina on 2010-01-31
> **ssam said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=Nzc4NQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzc4NQ) sums it up well.

also have a look at the llvm project

i dont think the mac os x kernel does any gpgpu stuff itself.

If u look at XNU kernel source (Mac OS X kernel) ever source has the OpenCL kernel in each source code... so the XNU kernel is fully made for gpgpu/openCL work

---

### Post by Paqman on 2010-02-03
> **Xbehave said:**
> Does openCL/CUDA interfere with graphics performance (i.e do you only use it when not at your PC)

GPGPU in general is designed to harness the massive number of cores in GPUs to vastly speed up certain types of calculations. There would be no point in slowing down your number crunching by trying to render graphics at the same time.

---

### Post by Ravernomina on 2010-02-03
> **Paqman said:**
> GPGPU in general is designed to harness the massive number of cores in GPUs to vastly speed up certain types of calculations. There would be no point in slowing down your number crunching by trying to render graphics at the same time.

During boot up....?

---

