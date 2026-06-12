---
title: "Preventing Sleep"
date: 2012-07-27
forum: Server Platforms
---

### Post by cosmarchy on 2012-07-27
Hi,

I am running v12 LTS server with kubuntu desktop and have a online photo gallery running.  

If I leave it for a while the monitor output switches off and after waking up the wireless appears to work but the web browser and gallery are unavailble on the net. 

My guess is they have gone to sleep and not woken up again.  

How can I prevent the computer sleeping or at the very least activate a wake-on-lan function of the wireless adaptor?

Thanks

---

### Post by cariboo on 2012-07-27
If you are running a server, you don't need a desktop. I'd suggest you remove kdm, then if you need a gui to do anything, use the:

```
startx
```

command, then log out when you are finished. I'd also suggest if your server is open to the world, you revert to a wired network connection, so as not to run into wireless problems.

---

