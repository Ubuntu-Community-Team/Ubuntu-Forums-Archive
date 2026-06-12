---
title: "Effects of better Video Card to improve Win7 VM video?"
date: 2012-01-22
forum: Virtualisation
---

### Post by Hedgehog1 on 2012-01-22
I have recently altered my primary PC to boot Ubuntu only.

This was practical because of 2 key factors:

  * Using an SSD allows VBox VMs to run **very** fast
  * Recent improvements with Vbox 4.1.8 and the 3D 'experimental'  driver

I have set 4 cores and 4 gigs of RAM for the Win7 VM.  It boots in about 13 seconds and runs very well.

My 'big three' programs I still use in Win7 are:

  * iTunes (only way to update software to the iPod)
  * Photoshop (there are some things that only Photoshop does)
  * Sony Vegas Video Editing Suite (Pro level Video/Audio/DVD&BluRay creation suite)

The highest demands are made by Sony Vegas. I have reached a performance level that is acceptable. Here is the performance index numbers (range is 1.0 to 7.9):

  * Processor: 7.4
  * RAM 7.5
  * Graphics: 4.2
  * Gaming Graphics: 3.0
  * Primary Hard Disk: 7.7

When editing HD video, the graphics are workable, but not ideal.

Now comes the question (Finally):

Will improving the real video card on the system make any noticeable difference on my VM graphics performance?

For the gamers out there that use Windows VMs, what has been your experience?

Right now I have a pretty basic nVidia GT 430 1 gig card (it was cheap and cheerful).  Would jumping to something like a GT 560 ti with 2 gigs make a noticeable improvement from inside the VM?

Please let me know your thoughts and/or experiences.

***The Hedge***

:KS

---

### Post by CharlesA on 2012-01-22
I haven't really tried doing 3D inside a VM, but I don't think upgrading from a 460 to a 560 would make much of a difference inside the VM since the 3D driver is still experimental and I do not know how it accesses the graphics card itself.

---

### Post by Hedgehog1 on 2012-01-22
CharlesA,

I have to say that I was surprised at the improvement by using the experimental 3D driver.  Both my graphics index scores were 1.0 before changing to it.

I have found only one issue so far when using it - I cannot boot my XP VM at the same time with the experimental 3D driver (they live happily side-by-side when both use the non-experimental driver).

The little bit of info I have on the experimental 3D driver is that it translates windows directx commands to opengl commands that are then given to the Linux video driver.  Sounds simple but we all know it is anything but simple in actual practice.

So many toys... So little money...

***[I]The Hedge*[/I]**

:KS

---

### Post by CharlesA on 2012-01-22
Haha. That's interesting, thanks.

I would leave it as is unless you want to upgrade the video card for another reason.

---

