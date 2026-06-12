---
title: "Server edition on laptop."
date: 2010-04-04
forum: Server Platforms
---

### Post by NiGhtMarEs0nWax on 2010-04-04
My dad just cleared out a lot of spyware from his laptop, so i suggested he tried out linux.

I would just install the desktop edition, but it comes with a lot of bloat that is unnecessary, so since I've already installed ubuntu server before and got a desktop environment up and running, i thought why not use that instead.

a couple of questions I have first though. 

1. besides all the packages that come pre-installed on the desktop edition and the fact that there is no desktop environment out of the box, from a basic installation of karmic server edition, no extra packages installed, what are the main differences between the desktop edition and server edition? in other words is it really viable for day to day use in a home environment?

2. i doubt the server edition will support a touchpad out of the proverbial box, what packages will I need to install to get it working?

3. wireless support, I'm assuming the same as above, what packages/modules will I need to install to get wireless working?

4. are there any other packages that you would recommend that are an absolute must, that I should install?


[here]("http://hothardware.com/Articles/Compaq-Presario-V4000/") is his laptop specs.


Thank you for you time.

---

### Post by Bachstelze on 2010-04-04
> **NiGhtMarEs0nWax said:**
> 
1. besides all the packages that come pre-installed on the desktop edition and the fact that there is no desktop environment out of the box, from a basic installation of karmic server edition, no extra packages installed, what are the main differences between the desktop edition and server edition? in other words is it really viable for day to day use in a home environment?

Besides that, none.

> 2. i doubt the server edition will support a touchpad out of the proverbial box, what packages will I need to install to get it working?

Of course it will.

> 3. wireless support, I'm assuming the same as above, what packages/modules will I need to install to get wireless working?

Depends on the wireless adapter. Most will be supported. Basically, if it requires using the Restricted Driver Manager on a desktop system, it will require at least installing some paackages.

> 4. are there any other packages that you would recommend that are an absolute must, that I should install?

No. The packages you must install are the ones you need.

---

### Post by iissmart on 2010-04-04
The Desktop edition uses a different kernel optimized for day-to-day use, whereas the Server edition uses a kernel with some tweaks to it...they are fairly different but you probably won't notice a difference.

---

### Post by Bachstelze on 2010-04-04
> **iissmart said:**
> they are fairly different but you probably won't notice a difference.

If it's not noticeable, maybe it's because they're not that much different...

---

### Post by iissmart on 2010-04-04
> **Bachstelze said:**
> If it's not noticeable, maybe it's because they're not that much different...
Whatever you say...

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features](http://www.ubuntu.com/products/whatisubuntu/serveredition/features)

---

### Post by volkswagner on 2010-04-04
I suggest downloading the alternate install cd.  You can install a text only environment then add only what you want.

Search "Ubuntu Minimal Install"  for some easy how to's.

---

### Post by NiGhtMarEs0nWax on 2010-04-05
i went with the minimal install, thanks.

in the view of security, what should i be concerned about? does apparmor work out of the box? im not really concerned with building a profile for user programs such as firefox, since i am setting it up for my father and if he runs into problems it could be a headache, but is it set up for system executables by default?

Thanks again.

---

