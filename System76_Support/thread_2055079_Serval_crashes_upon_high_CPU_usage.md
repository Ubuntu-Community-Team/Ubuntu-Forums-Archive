---
title: "Serval crashes upon high CPU usage"
date: 2012-09-08
forum: System76 Support
---

### Post by 130s on 2012-09-08
My Serval laptop has suddenly started immediate turn-off power recently. It's happened at  least twice in last 2 days. Any idea is appreciated and please tell me  which log files you need to investigate so that I'm happy to provide  those.

I can only describe the situation non-numerically b/c I didn't record anything when it occurred but:

- CPU usage is high (roughly, the usage of all 4 cores is more than 75% less than 100% on Gnome System Monitor)
- Noise of the fan was the one of the busiest
- Memory usage was about 50%
- Application program running was a simulator for robotics (called  Gazebo), which after a few minutes of running the phenomenon occurs.  I've used the same tool before on this machine so shouldn't be the matter.

Not sure if it's related but after I've upgraded to Precise, the fan has been making more noise even when the CPU usage is very low.

Environment:
- Ubuntu 12.04 (originally 11.04 upon purchase, then 11.10)
- Kernel 3.2.0-30-generic
- Core i7 2GHz x 8
- 11.7GB RAM

Thanks.

---

### Post by isantop on 2012-09-10
> **130s said:**
> My Serval laptop has suddenly started immediate turn-off power recently. It's happened at  least twice in last 2 days. Any idea is appreciated and please tell me  which log files you need to investigate so that I'm happy to provide  those.

I can only describe the situation non-numerically b/c I didn't record anything when it occurred but:

- CPU usage is high (roughly, the usage of all 4 cores is more than 75% less than 100% on Gnome System Monitor)
- Noise of the fan was the one of the busiest
- Memory usage was about 50%
- Application program running was a simulator for robotics (called  Gazebo), which after a few minutes of running the phenomenon occurs.  I've used the same tool before on this machine so shouldn't be the matter.

Not sure if it's related but after I've upgraded to Precise, the fan has been making more noise even when the CPU usage is very low.

Environment:
- Ubuntu 12.04 (originally 11.04 upon purchase, then 11.10)
- Kernel 3.2.0-30-generic
- Core i7 2GHz x 8
- 11.7GB RAM

Thanks.

Try blowing compressed air through the vents on the back of the computer. I'm guessing they're cloged up, and blowing the dust free will resolve your issue.

---

### Post by 130s on 2012-09-11
Thanks isantop. So you suspect that this could be unusual high temperature issue right? 
I've done these:


[LIST]
[*]I blew the fan at the back/bottom (I saw some dust at the exterior of air outlet, but not that terribly much I believe. And I don't see much either at the fan inside though it's darker and not clear)
[*]I moved the machine on flat, hard surface (before, it was placed on magazines) just to make it clear the surface underneath is what's intended (so that the air outlet won't get clogged)
[/LIST]
Now, after testing the same simulator a few times, I haven't seen shutdowns so far.

I also started checking CPU temp (by psensor) and observed (all are observation after blowing fan):

[LIST]
[*]When CPU usage is around 20%, Core 0 thru 3 are around 52C(elsius), GPU0 is 58C
[*]When running the same simulation that makes CPU usage 70% or higher, temps of CPUs are 85 - 95C (this particular simulation doesn't use GPU).
[/LIST]
Assuming again temperature is related, are these values abnormal? Unfortunately I have no idea how hot they were upon the shutdowns.

Thanks again.

---

### Post by isantop on 2012-09-11
> **130s said:**
> Thanks isantop. So you suspect that this could be unusual high temperature issue right? 
I've done these:


[LIST]
[*]I blew the fan at the back/bottom (I saw some dust at the exterior of air outlet, but not that terribly much I believe. And I don't see much either at the fan inside though it's darker and not clear)
[*]I moved the machine on flat, hard surface (before, it was placed on magazines) just to make it clear the surface underneath is what's intended (so that the air outlet won't get clogged)
[/LIST]
Now, after testing the same simulator a few times, I haven't seen shutdowns so far.

I also started checking CPU temp (by psensor) and observed (all are observation after blowing fan):

[LIST]
[*]When CPU usage is around 20%, Core 0 thru 3 are around 52C(elsius), GPU0 is 58C
[*]When running the same simulation that makes CPU usage 70% or higher, temps of CPUs are 85 - 95C (this particular simulation doesn't use GPU).
[/LIST]
Assuming again temperature is related, are these values abnormal? Unfortunately I have no idea how hot they were upon the shutdowns.

Thanks again.

Those sound right. Keep an eye on it and let us know if you see anything else unusual.

---

### Post by 130s on 2013-06-20
Turned out after nearly 10 months later that I had to clean the fan itself. I opened not only the back lid of the laptop, but also the covers of the 2 fan components; inside the fans I see the parts that connect to the dust ducts where were clogged terribly. I thank the fans are open-able by screws. Not the processors temperature become 20F lower than it was during high usage.
[IMG]https://lh6.googleusercontent.com/-38ifjYHqIvQ/UcRu-nwX-bI/AAAAAAAActM/z_Sak9_MFTk/s912/2013-06-20%252014.59.28.jpg[/IMG]
[IMG]https://lh4.googleusercontent.com/-OIyvHcUiXmI/UcRu_FQHbRI/AAAAAAAActU/Jy2CRYq5DWE/s912/2013-06-20%252015.01.36.jpg[/IMG]

---

