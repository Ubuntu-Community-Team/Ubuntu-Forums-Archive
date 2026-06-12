---
title: "Xserver problems"
date: 2008-07-29
forum: Testimonials &amp; Experiences
---

### Post by MrShurr on 2008-07-29
I seriously need a professional's help!

Okay, so here's my story. I've had trouble with the nVIDIA drivers in the past (I have a GeForce 6800 GTS or something, but it's not important). So I went and downloaded an older driver, the first one I ever used with ubuntu, which worked great before. Once I put it on and restarted, my xserver failed. It gave me a message saying it wasn't configured correctly or something and to make it right.

I reinstalled the driver, telling it to NOT do whatever it does involving the kernel. (sorry.. not sure, just something about a kernel and I said no). then I ran:
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

and it worked! except, every time i reboot, i have to do this. Can anybody help me?
Thanks,
Dave

P.S. is this in the right section of the forums?

---

