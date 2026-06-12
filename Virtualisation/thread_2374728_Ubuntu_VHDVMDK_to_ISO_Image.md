---
title: "Ubuntu VHD/VMDK to ISO Image"
date: 2017-10-18
forum: Virtualisation
---

### Post by shrry8 on 2017-10-18
Hi,

I have installed Ubuntu Image 14.04 and customized it as per my requirement. Is there any possible way to convert that VHD/VMDK disk to ISO Image for Bootable Disk in order to have bare metal installation.

Is it do able ??

---

### Post by DuckHook on 2017-10-18
Welcome to the forums, shrry8,

An unusual request, to be sure. Your approach has two big issues that I can see:

[LIST=1]
[*]A proper installation is expecting both read and write (dynamic) access to the HDD whereas ISOs are static. That's how the ISO protocol works. Even if you could somehow get the image transferred, your image would likely result in a kernel panic as soon as you try to run it. A LiveUSB/DVD is a completely different animal and is built to load and run entirely in RAM. That's why it doesn't crash, but that's not what your approach would yield.
[*]You can achieve a customized bootable USB stick/drive simply by installing onto such a stick/drive. You can clone such a customized stick/drive as many times as you like. Your roundabout way of customizing a VM just seems superfluous to me, unless there's something you're trying to finesse that you haven't told us.
[/LIST]
To answer your question: I'm not sure it's doable, mainly because of point #1 above.

---

