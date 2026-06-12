---
title: "Changing Kernel"
date: 2009-07-07
forum: Server Platforms
---

### Post by Avuton Olrich on 2009-07-07
I've been thinking of changing from Debian to Ubuntu Server lately. My reservation is that I have tried to make a custom kernel my desktop Ubuntu machine in the past and it seems like the maintainers try to do everything to prevent end users from using make-kpkg (at least I failed the few times I tried to make-kpkg in Ubuntu). Am I mistaken? Is this the same way in the Ubuntu Server?

Thanks!

---

### Post by drave99 on 2009-07-07
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

that mentions it, but ive never tried

---

### Post by Avuton Olrich on 2009-07-07
**"Building and using a custom kernel will make it very difficult to get support for your system.  While it is a learning experience to compile your own kernel, you will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without further explanation)."**

And that's what makes it difficult to make the move, so I think I'll stick with Debian until things ease up a bit. I have found in order to have a stable realtime kernel on any distribution, it takes trial and error to figure out which kernel works for greater than 3 months without issue on any given hardware. Besides, on a server distribution in a production environment, I wouldn't be interested in debugging non-rt/vanilla kernel patches.

Hope the policy changes in the future to allow more vanilla kernel support.

---

