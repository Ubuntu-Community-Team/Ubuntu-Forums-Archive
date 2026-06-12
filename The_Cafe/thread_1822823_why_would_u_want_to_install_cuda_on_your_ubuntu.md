---
title: "why would u want to install cuda on your ubuntu?"
date: 2011-08-11
forum: The Cafe
---

### Post by tweakmy on 2011-08-11
Hi to all,
Opening this topic for discussion. Have read and understand no much bout cuda. But why do you want to install cuda on your machine?

General curios?

---

### Post by Legendary_Bibo on 2011-08-11
1. This makes no sense
2. Please use "you" instead of "u", it's just two letters.

---

### Post by FlameReaper on 2011-08-11
CUDA? I thought its a technology that comes with the newer NVIDIA cards starting from the 8800GT or something? Which lets the GPU take over some computing tasks from the CPU, supposedly alleviating some load from it?

... That said, I really like the prospect of CPU+GPU/GPGPU computing instead of relying totally on the CPU.

I've had a few instances where GPU acceleration saved me from what seemed like an unrecoverable lag...

---

### Post by tweakmy on 2011-08-11
what kind of instances are these?
Mind  to share more. Could quote a bit specific?

---

### Post by FlameReaper on 2011-08-11
> **tweakmy said:**
> what kind of instances are these?
Mind  to share more. Could quote a bit specific?

Opening a 20,000-pixels wide painting.

In GIMP it was quite painful, and made me sleep while waiting... and it still hasn't finished by the time I awakened.

So I rebooted to Windows, used Photoshop CS3 (which has GPU acceleration enabled) to open it. I was saved. Although this is just pointing out the significance of having a GPU-assisted processing in general, not just by having CUDA.

Also for video encoders/decoders, using GPU-assisted processing (namedly, CUDA), accelerates video encoding/decoding significantly compared to when you depend on the CPU.

Actually, just so you know, CUDA isn't something like a software that can be installed. If you go and buy an NVIDIA graphics card past the 8800GT ages, CUDA is already a standard feature in NVIDIA cards.

---

### Post by NovaAesa on 2011-08-11
Eh, you don't install CUDA on anything because CUDA isn't software. CUDA allows you as a programmer to utilize certain Nvidia cards for general computations rather than just graphics. It's very handy if you want to do some serious multiprocessing but don't want to spend money on a cluster or supercomputer.

---

### Post by FlameReaper on 2011-08-11
I do think he might be talking about installing the drivers necessary for software developers to have access to CUDA processing libraries/toolkits...

... Or the CUDA Toolkit...

... argh, I can't remember.

---

### Post by ninjaaron on 2011-08-11
> **Legendary_Bibo said:**
> Please use "you" instead of "u", it's just two letters.
Don't be that guy.

---

### Post by 3Miro on 2011-08-11
GPUs are heavily optimized hardware and for some applications that can do the job much faster than any CPU. CUDA is deprecated technology allowing you to do program on the GPU. The current technology is OpenCL.

I know people that program on OpenCL or CUDA as their job, so they definitely need it.

---

### Post by tweakmy on 2011-08-11
as what i suspected. I recently went for a linux group session on chaos theory. I guess they could use it but I dont think it is for me. : )

Yeap, I avoid the 'u' thingy. Sorry about tat. Dont meant to be disrespectful.

---

### Post by Paqman on 2011-08-11
CUDA is awesome. CUDA-enabled BOINC apps crunch significantly faster than those using CPU only.

---

### Post by juancarlospaco on 2011-08-11
Because i can.

Like everything else on Linux world...

---

