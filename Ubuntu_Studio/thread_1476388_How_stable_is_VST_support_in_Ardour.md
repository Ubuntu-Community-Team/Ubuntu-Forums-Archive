---
title: "How stable is VST support in Ardour?"
date: 2010-05-07
forum: Ubuntu Studio
---

### Post by isaacj87 on 2010-05-07
Hello all,

I've seen many articles on how unstable VST support is for Ardour and Linux in general. One thing that I've notice, however, is these articles are dated in 2007/2008. In the open-source world, 2 year is a long time!

So, my question: How stable is VST support in Ardour 2.8.7? What VST plugins or instruments are you using and how buggy is it overall?

Thanks!

---

### Post by sgx on 2010-05-08
> **isaacj87 said:**
> Hello all,

I've seen many articles on how unstable VST support is for Ardour and Linux in general. One thing that I've notice, however, is these articles are dated in 2007/2008. In the open-source world, 2 year is a long time!

So, my question: How stable is VST support in Ardour 2.8.7? What VST plugins or instruments are you using and how buggy is it overall?

Thanks!
Hi, excellence in audio i/o is the main goal of ardour, midi and vst are
much further down on the authors list, in the meantime, hosting windows vsts using wine, wineasio, and Reaper, is very stable, just don't buy vsts with dongles, pace, or ilok copy protection. About 90% of everything else
works quite well. Install your plugins in

/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins
 
unless the installer has a special default.
Cheers

---

