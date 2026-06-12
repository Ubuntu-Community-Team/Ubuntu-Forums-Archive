---
title: "Ubuntu Freezes when loading in VM VirtualBox"
date: 2018-06-14
forum: Virtualisation
---

### Post by ed-ucation on 2018-06-14
Hey guys,

I am fairly new to Linux (and this forum, so if I'm doing something wrong in the way I'm asking just say!), but have used Ubuntu 18.04 64-bit for the past couple of months via VBox 5.2.12 to run several python machine-learning based projects, and haven't had any issue until recently. 

However today, after installing Docker and after, the latest version of OpenFace (following these instructions: [http://cmusatyalab.github.io/openface/setup/](http://cmusatyalab.github.io/openface/setup/)), I shut it down safely, yet when I'm trying to load it up again it's stuck on the screen in the attached picture.
[ATTACH=CONFIG]280099[/ATTACH]

I've tried to let it run, but it seems constantly stuck in this position. The details of my machine are in the following picture below:

[ATTACH=CONFIG]280100[/ATTACH]

Is there something I've done wrong? OpenFace has had no issues with the Mac I tested it on, and seems to have been built for Linux operating systems. I want to avoid doing a full reinstall because that's what I've done when I had this issue with the last VM (didn't install OpenFace on the last one however).

Any help is appreciated!

---

### Post by deadflowr on 2018-06-14
What are the overall machine specs for the host?
(The image is neither fully-readable nor complete)

What is the host operating system, as well.

---

### Post by MikeCyber on 2018-06-15
boot recovery mode and fix it from there

---

### Post by ed-ucation on 2018-06-15
> **deadflowr said:**
> What are the overall machine specs for the host?
(The image is neither fully-readable nor complete)

What is the host operating system, as well.

I'm sorry didn't get the overall specs in the original post. It has been solved now, thanks to MikeCyber's comment, and adding an extra CPU and a tad more RAM to my machine. But, for the benefit of others who have my problem, here are my specs:

Host...
OS: Windows 10 Pro (Version 10.0.16299, Build 16299)
System Type: x64
Processor: Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz, 2904 Mhz, 2 Cores, 4 Logical Processors
RAM: 8 GB
Total Memory: 2TB
BIOS Version/Date: American Megatrends Inc. UX310UAK.306, 09/08/2017

Machine (At time of error)...
OS: Ubuntu 18.04 (All guest additions installed)
System Type: x64
Available Memory: 4096MB (Was changed to 4880MB)
Processor Number: 1 (Was changed to 2) with 100% execution cap and PAE/NX enabled
Total Memory Size: 100.00GB (Fixed)

If there's anything else you need as a standard for the forum, let me know!

---

### Post by LHammonds on 2018-06-15
> **ed-ucation said:**
> 
Total Memory: 2TB
Total Memory Size: 100.00GB (Fixed)


I think you meant to say "storage" (as in hard drive storage) instead of "memory."  Memory is typically refers to RAM (Random Access Memory)
```

Total Storage: 2TB
Total Storage Size: 100.00GB (Fixed)

```

---

