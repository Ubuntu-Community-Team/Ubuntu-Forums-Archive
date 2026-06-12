---
title: "No Suspend, or Hibernate?"
date: 2008-09-14
forum: System76 Support
---

### Post by kevin11951 on 2008-09-14
My laptop (Gazelle Value 5 w/ Nvidia) wont hibernate or suspend. I just keep getting a kernel panic! :confused:

---

### Post by glacialfury on 2008-09-14
This is a known issue with Hardy Heron; I don't remember exactly what, but it has something to do with the kernel (which Hardy implements, thus this is where most of us first encounter it).  

Supposedly you can revert to a previous version of the kernel, where it worked fine, and it will work fine again.  I haven't tried that myself.  In the meantime, there is not a lot that can be done.

---

### Post by thomasaaron on 2008-09-15
Hey, Kevin. What's the output of...

uname -r?

If you are running one of the propsed kernels (i.e. greater than -19) on your Gazelle, that probably explains it.

NOTE: The NEW Pangolins (panp4x) need the proposed kernel to work correctly.

---

