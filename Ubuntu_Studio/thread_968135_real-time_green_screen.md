---
title: "real-time green screen"
date: 2008-11-02
forum: Ubuntu Studio
---

### Post by ipburbank on 2008-11-02
I posted this in the video section, and was advised to post it here too:

Does anyone know of software that will do real-time green screening for me? I want to stream video, but I need to green screen it first. I am running a fast computer, so power is not really in issue, unless it wants more than a quad core OC'd to 3.6 and a 9000 series gpu.

thank you for any help, istvan.

---

### Post by skullmunky on 2008-11-03
Try Pure Data.  Use the pd-extended version, and try out the pdp_compose object.  (see [http://ydegoyon.free.fr/pidip.html](http://ydegoyon.free.fr/pidip.html)).  

There are also objects for streaming and other effects so you might be able to do everything you need all from within Pd.

---

### Post by ipburbank on 2008-11-03
Thanks! one problem tho... I can't seem to launch it. I used apt, and tried compiling from source, and with ubuntu 8.10 64 bit, the latest (nov-3) build I can't launch it.

---

### Post by skullmunky on 2008-11-09
Hm, yeah, I didn't realize they don't have official amd64 builds.  I did find this thread where it looks like people have successfully compiled it, with a little tweaking:

[http://ubuntuforums.org/archive/index.php/t-722253.html](http://ubuntuforums.org/archive/index.php/t-722253.html)

also this thread on the pd forum:

[http://puredata.hurleur.com/sujet-1947-extended-amd64](http://puredata.hurleur.com/sujet-1947-extended-amd64)

I've only used it in 32 bit.  Now that I think of, that's probably one of the reasons I've always installed the i386 ubuntu even though I have an AMD64. :P

---

