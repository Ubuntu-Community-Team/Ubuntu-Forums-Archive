---
title: "-rt kernel sticks me in low-graphics mode"
date: 2008-11-08
forum: Ubuntu Studio
---

### Post by Envergure on 2008-11-08
I have both the 2.6.27-7-generic and 2.6.27-3-rt kernels installed, and the 177 nVidia driver installed.  Everything works fine with the -generic kernel, but when the -rt one boots i get stuck in Low Graphics Mode.

I want an -rt kernel to use Jack without xruns left and right.

---

### Post by Zimmer on 2008-11-08
Have you really installed the nvidia driver to the -rt kernel? Any update to that kernel will probably require uninstalling and reinstalling the Nvidia driver to that kernel.
Have a look at the xorg.log to see what is going on at boot..

Are you using EnvyNG to install/uninstall it?

---

### Post by Stochastic on 2008-11-08
Sounds like you're experiencing this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/292270](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/292270)

It's yet to be confirmed right now, so you should post there with your logs/error messages/experiences too.

---

### Post by Ng Oon-Ee on 2008-11-09
> **Envergure said:**
> I have both the 2.6.27-7-generic and 2.6.27-3-rt kernels installed, and the 177 nVidia driver installed.  Everything works fine with the -generic kernel, but when the -rt one boots i get stuck in Low Graphics Mode.

I want an -rt kernel to use Jack without xruns left and right.

I had the same thing. Needs a reinstall of your nvidia driver, because DKMS fails (if you view the dmesg output) when you've only installed in 2.6.27-7-generic and are installing 2.6.27-3-rt. If you install on your rt, DKMS works properly when you go back to 2.6.27-7-generic. I'm guessing that DKMS helps more for going forward in versions than back, but I may be wrong.

My nvidia works fine in RT right now. Can't say as much for my shutting-down or dual-core problems though :D. The price to pay for eliminating xruns....

---

### Post by mrhelpman on 2008-11-09
> **Envergure said:**
> I have both the 2.6.27-7-generic and 2.6.27-3-rt kernels installed, and the 177 nVidia driver installed.  Everything works fine with the -generic kernel, but when the -rt one boots i get stuck in Low Graphics Mode.

This was the last straw for me. When this happened I did a slash and burn on Hardy and went back to Dapper and one of my own rt kernels.

I am now back to 2.6ms latency on my Audiophine USB sound module and 1.6ms on my soundblaster. With the Hardy 8.04 - or I guess in your case the 8.10 - I could not even start jack with those latencies.

> I want an -rt kernel to use Jack without xruns left and right.

Sadly the only solution I can offer is the above.

John T.

---

### Post by Stochastic on 2008-11-09
> **mrhelpman said:**
> This was the last straw for me. When this happened I did a slash and burn on Hardy and went back to Dapper and one of my own rt kernels.

I am now back to 2.6ms latency on my Audiophine USB sound module and 1.6ms on my soundblaster. With the Hardy 8.04 - or I guess in your case the 8.10 - I could not even start jack with those latencies.



Sadly the only solution I can offer is the above.

John T.

The original poster was quoting Intrepid RT kernel numbers, not Hardy numbers, so your experiences are not from the same kernel.  Sorry to hear you had trouble with the Hardy kernel though, it worked great for me.

---

