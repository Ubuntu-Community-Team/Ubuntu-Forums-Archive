---
title: "Linux-rt , nvidia, troubles"
date: 2008-11-21
forum: Ubuntu Studio
---

### Post by djauto23 on 2008-11-21
I'm having trouble installing and using the linux-rt kernel. The first time I tried, after just blindly installing the linux-rt package, xorg would fail to load properly, returning an error message: "Failed to load the NVIDIA kernel module". What's worse is that the machine now freezes sometimes (not always) during the splash screen before xorg when on linux-rt. 

I'm aware of the problems concerning the rt kernel and dual core, but for me this is ok as I have a single core cpu. I just want the nvidia-kernel to be installed along with linux-rt, and everything working fine, as it was before in 7.04->8.04. Have also tried using the restricted driver manager, but when I press "Activate" on the nvidia module nothing happens. I'm thinking about trying the nvidia module from the nvidia site, but something tells me it's just a file needing to be copied from somewhere to somewhere else.

It had been nice to get any insights on how to deal with this, or any experiences. The bit about freezing upon bootup worries me the most, since I'll be using it for a live DJ broadcast using xwax.

So please, any tips, experiences or any other kind of feedback would be appreciated.

My laptop is a Dell Inspiron 8600 with a GeForceFX5200. The rt kernel is version 2.6.27-3-rt.

---

### Post by thorgal on 2008-11-21
if you don't care about 3D acc and effects, use the open source nv driver instead of the nvidia closed source driver.

---

### Post by djauto23 on 2008-11-21
> **thorgal said:**
> if you don't care about 3D acc and effects, use the open source nv driver instead of the nvidia closed source driver.

Yupp, that's what I just did, and now I have realtime scheduling working amazingly well, in fact better than ever. On the el-crappo internal soundcard JACK works adequately on as low as 2.9ms, which is truly amazing.

As for my DJ broadcast I think this will work fine. However, it would be nice to have 3D acc working also.

Opinions on wether I should continue this struggle? Is it worth it? Will the nvidia drivers always pose a threat to realtime scheduling? Even with the generic kernel latencies are way better than before, so that makes me think wether I should ditch that nvidia **** once and for all, and buy something with the Intel card or maybe ATI instead.

---

### Post by reakin on 2009-01-24
I'd like to know if there have been any advancements in this area.  I use real-time audio software (ardour+pd) in conjunction with python/opengl graphics, so I'd like to use the closed source driver that allows for hardware acceleration.

I installed the linux-rt package the other day on a completely updated intrepid system and saw the same xorg error message on reboot.

If people have heard of any news on this issue, I'd like to know.  A quick google search only led me here.

regards,
Rich

---

### Post by Abu_Dayya on 2009-01-25
I think (and please stress the 'THINK' part, I don't know for sure) that when you changed your kernel, the nvidia kernel module is changed. Thats why the new kernel will not work with the installed nivida driver. To overcome this download the nvidia driver script from nvidia's website, then remove everything related to nvidia from your system (apt-get remove nvidia*). Then close xserver. Then run the script you downloaded from the shell. This script will compile a kernel interface for your nvidia driver

---

### Post by Stochastic on 2009-01-25
this bug report may be related to your issue (might not): [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/292270](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/292270)

---

### Post by aidave on 2009-01-26
I am wary of trying this myself, but, you could try this after booting with the realtime kernel:

```

sudo envyng -t

```

This will give you an easy way to rebuild the Nvidia driver to the RT kernel.  BUT I dont know if that will work.

---

