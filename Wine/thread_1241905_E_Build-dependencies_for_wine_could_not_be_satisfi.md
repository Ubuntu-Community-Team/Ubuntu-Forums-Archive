---
title: "E: Build-dependencies for wine could not be satisfied."
date: 2009-08-16
forum: Wine
---

### Post by elitenoobboy on 2009-08-16
When trying to install the build dependencies for wine using apt-get, I get this error: E: Build-dependencies for wine could not be satisfied.
How do I install the build dependencies?

---

### Post by shae on 2009-08-17
I would suggest you make sure you have Source Code enabled in your Repositories in Synaptic.

---

### Post by elitenoobboy on 2009-08-17
> **shae said:**
> I would suggest you make sure you have Source Code enabled in your Repositories in Synaptic.

I have already made sure that it is. I still get the error.

---

### Post by shae on 2009-08-17
What command are you using to try to install the build dependencies?

---

### Post by elitenoobboy on 2009-08-21
> **shae said:**
> What command are you using to try to install the build dependencies?
I was using "apt-get build-dep wine", but then I figured out "apt-get --build source wine" actually gave me some useful information so that I could figure out where the problem was.

---

