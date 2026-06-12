---
title: "Nvidia Optimus coming to Linux?"
date: 2012-10-01
forum: The Cafe
---

### Post by Stonecold1995 on 2012-10-01
I ready [here]("http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY") that Nvidia has confirmed that it is working on Optimus so that it can be supported by Linux.  This is great news, but what's the realistic outlook of this?  When will the actual working drivers come out for Linux?

I was unlucky enough to buy a powerful mobile GPU, the GeForce GTX 675m, but my computer's BIOS doesn't have the option to disable discrete graphics so I've never been able to use my GPU, except for with Bumblebee but it kind of sucks (it makes most games *slower* and less stable than with the CPU).  So hearing the news that I may one day be able to switch between discrete graphics and Nvidia was really relieving.

So what do you think about this?  When's it suppose to be ready to use on Linux?

> This is really great news since up to this point NVIDIA Optimus laptops have been a pain to use properly under Linux. While there is DMA-BUF/PRIME support for the Nouveau driver, using the reverse-engineered open-source NVIDIA driver isn't ideal there since the driver lacks reliable and useful power management support (a.k.a. a very short battery life and potentially a warm lap). Let's hope this support gets stabilized soon.

---

### Post by Welly Wu on 2012-10-01
If you and I are reading the same sources of information, then Nvidia is quietly working on supporting Optimus in GNU/Linux environments now. They have not announced an official release date or time to offer Nvidia graphics drivers that support Optimus in GNU/Linux yet. At the very least, you will need to upgrade to Ubuntu 12.10 32 or 64 bit because it has the newer Linux kernel 3.5.2 and it has the new OpenGL 3.x, Mesa 9.0, RandR, and Intel SNA along with X.Org versions that support PCs with multiple GPUs. So, you should think of this as a combined community effort across GNU/Linux for cutting edge distributions to offer Optimus support. Without Nvidia supplying an official graphics driver that supports Optimus, you will have multiple system crashes when trying to invoke Optimus support. Therefore, you should be patient. I would say that it would be more realistic to expect official Nvidia support by Ubuntu 13.04 32 or 64 bit in April 2013 at the earliest possible date. Of course, I am speculating just as much as you are doing so because we don't know how far along Nvidia is making progress. They have a proof of concept working now, but it is in the inchoate stages of official Optimus support for GNU/Linux. My understanding is that you will have to remove the Bumblebee Project to get the official Nvidia Optimus in GNU/Linux support.

---

### Post by litiform on 2012-10-12
I don't think Optimus will ever come to Linux. Integrated will get so good & power efficient it won't be needed.

---

### Post by Stonecold1995 on 2012-10-12
> **litiform said:**
> I don't think Optimus will ever come to Linux. Integrated will get so good & power efficient it won't be needed.

Integrated graphics are already very power efficient, but that's the problem.  They're focused on power efficiency instead of raw power.  A dedicated GPU is always going to be far more powerful than integrated graphics.

---

### Post by Welly Wu on 2012-10-12
That may be true for now, but the future direction in which Intel is taking in particular leads me to believe that integrated graphics will be up to snuff with AMD and NVIDIA GPUs in the next two years or so. For example, Intel's next generation Haswell CPU will double the graphics performance from Intel HD Graphics 4000 with its top of the line CPUs next year. This will mean that it will offer pretty good graphics performance and an AMD or NVIDIA GPU will be optional. In the next two years, I expect Intel's integrated GPU to be close in terms of performance to that of AMD and NVIDIA's second to the top of the line GPUs, but they will be much more power efficient and the CPUs and GPUs will be much smaller so that smaller form factor desktops and notebook PCs will be able to take advantage of these next generation Intel CPUs.

Take a look at the Intel HD Graphics 4000. It will play World of Warcraft at over 30 FPS at low to medium graphics settings. Who can tell me what will happen to Intel CPUs and integrated GPUs in the next two years from today?

---

### Post by Stonecold1995 on 2012-10-12
Of course Intel's integrated graphics will improve, but Nvidia and AMD will just respond by making more powerful (and less efficient) dedicated GPUs.  It'll just be an arms-race (or rather, it'll continue as an arms-race).  For example, I have the Intel HD 3000, but an Nvidia GeForce GTX 675m, which is quite good.  By the time Intel matches the 675m while keeping low power usage, Nvidia will come out with an even better one (for gaming laptops at least).

Is the Haswell CPU's integrated graphics as efficient as the 3000/4000?

---

### Post by Welly Wu on 2012-10-12
The Intel 4th Generation "Haswell" CPU is still under development. The integrated GPU is designed to be twice and powerful as the Intel HD Graphics 4000 while the CPU itself will draw 50 percent less energy than the current 3rd Generation "Ivy Bridge" CPUs and it should reduce the size down to 14 nm. It is designed with Intel Ultrabooks in mind to provide up to 9 hours of battery life and entry level high end graphics performance with up to 25 percent faster CPU speeds and efficiencies. It will be a big deal for Intel next year. It is going to be a "tock" release in their tick-tock release schedule.

---

### Post by mips on 2012-10-13
> **Welly Wu said:**
> The integrated GPU is designed to be twice and powerful as the Intel HD Graphics 4000

Even if it's twice as powerful that's still pretty dismal in performance compared a 'real' gpu.

It would be nice to have Intel as a competitor to amd & nvidia gpus.

---

### Post by Welly Wu on 2012-10-13
It's going to take at least another two more years before Intel is roughly on par with AMD and NVIDIA's latest and highest end GPU products and graphics drivers for Ubuntu GNU/Linux. The thing to remember is that integrated GPUs offer power efficiency and they allow for smaller and lighter form factors especially for mobile applications like notebook PCs, tablets, and smart phones. If Intel can equal the performance of an AMD FX 6750M or NVIDIA GeForce GT 550M GPU with their latest CPU and integrated GPU chip at under 14 nm size or smaller, then it will be a major victory for everybody involved. As it stands right now, the Intel HD Graphics 4000 is roughly equivalent to a NVIDIA GeForce GT 330M or AMD 6620G which is quite decent. You can play a number of older PC games at decent resolutions and medium graphics settings using the Intel HD Graphics 4000 integrated GPU for Intel 3rd Generation Ivy Bridge CPUs.

Remember, all GNU/Linux distributions don't support multiple GPUs right out of the box. Until AMD and NVIDIA along with the Linux kernel, mesa, X.Org, Wayland, OpenGL, etc. support hybrid multi-GPU setups, it's easier and more reliable to resort to an integrated GPU that is built into a CPU. None of the current generation NVIDIA GeForce GT or GTX 600 series mobile GPUs work with Ubuntu on notebook PCs to the best of my knowledge. Nvidia Optimus is not officially supported on Ubuntu or other GNU/Linux distributions yet.

---

### Post by Zombie Acorn on 2012-10-13
I hope it is officially supported soon, although my alienware m14x is functional, it gets intermittent errors and sometimes the graphics card bombs when using optirun with bumblebee.

---

