---
title: "Running a gaming server"
date: 2006-08-29
forum: Server Platforms
---

### Post by ColinS on 2006-08-29
Hi there,

I've been setting up a server to host games servers. I installed Ubuntu 6.06

I've been reading up and to achieve the best performance the kernel needs to be compiled with the -HZ 1000 option. Can anyone tell me what setting the precompiled version is compiled with? Is there any way to change this setting once a server is installed, or is it necessary to recompile (which I really don't want to do, since the servers are hosted remotely and I'm scared I'll fluff it up and they wont come back up!)?

Look forward to your replies!

---

### Post by Woei on 2006-08-29
> **ColinS said:**
> 
I've been setting up a server to host games servers. I installed Ubuntu 6.06

I've been reading up and to achieve the best performance the kernel needs to be compiled with the -HZ 1000 option. Can anyone tell me what setting the precompiled version is compiled with?


The default on a 2.6 kernel used to be 1000Hz up until 2.6.13 IIRC. It's changed since then to 250Hz. The kernel that ships with Ubuntu does not deviate from this default, and also has its tickrate set at 250Hz.

> Is there any way to change this setting once a server is installed, or is it necessary to recompile (which I really don't want to do, since the servers are hosted remotely and I'm scared I'll fluff it up and they wont come back up!)?

No, that simply isn't possible. It's a change that can only be done at compile time, as a lot of other code in the kernel is dependent on the value of the CONFIG_HZ variable in the source.

BTW, what software will you be running and what guide said you needed 1000Hz for optimum performance ? It's usually the other way around: if you want low latencies, then a kernel with a higher tickrate is usually a bit smoother, but if you want higher throughput, then a kernel with a low tickrate 100-250Hz is better. Really, I'd be surprised if you were to see *any* difference at all when hosting a game. There are so many other variables, most importantly network latency and overal systems configuration, that messing with the tickrate becomes a waterdrop in the ocean. That being said, if you really want to, configuring the kernel for 1000Hz isn't hard, as it's an option in the menu driven kernel configuration, or a one-line change in the config file (CONFIG_HZ_1000). There are numerous guides on tweaking the default Ubuntu kernel, for example, on Ubuntu's own [Wiki](https://wiki.ubuntu.com/KernelCustomBuild).

---

### Post by Kurt` on 2006-08-29
He's probably trying to run Counterstrike servers.

No offense, but newbies to hosting game servers seem to think that having "1000 FPS" servers makes their server a better place to play.

Asking this question in any linux-related IRC channel would get you kicked/banned, because it's flat out stupid.

The guide you are reading is probably written by someone who doesn't understand what they're doing.

---

### Post by tribaal on 2006-08-29
I believe there is no such thing as a stupid question, only stupid... answers.

- trib'

---

### Post by ColinS on 2006-08-30
Yes I'm going to be running Counter-Strike servers to start with, I don't intend running the servers at 1000fps, but I would like the option to have them run at higher than 250. 

Yes it will probably make a difference of about 5ms in the ping to the server, which may seem like a drop in the ocean, but as an ISP with gigabits of bandwidth available we're interested in getting our pings as low as possible to attract more business from those gamers you mention who only care about server fps and ping!

Thanks for the informative answer Woei. :)

---

