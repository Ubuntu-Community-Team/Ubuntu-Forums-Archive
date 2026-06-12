---
title: "Motivation to go back to 32-bit?"
date: 2012-07-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MacUntu on 2012-07-15
> Errors were encountered while processing:
 libqt4-declarative:amd64
 libqtgui4:i386
 libqt4-declarative:i386
 libqtgui4:amd64
 libqt4-designer:amd64
 libqt4-designer:i386
 libqt4-qt3support:amd64
 libqt4-qt3support:i386
 libqt4-dev-bin
 libqt4-help:amd64
 libqt4-scripttools:amd64
 libqt4-scripttools:i386
 libqt4-svg:amd64
 libqt4-svg:i386
 qt4-linguist-tools
 libqt4-dev
 libqt4-opengl:amd64
 libqt4-opengl:i386
 libqt4-opengl-dev
 qt4-designer
 libqt4-declarative-folderlistmodel:amd64
 checkbox-qt
 konsole
 libqt4-gui
 libunity-2d-private0
 qdbus
 qt4-dev-tools
 unity-2d-panel
 unity-2d-spread
 unity-2d-shell
 unity-2d
 vlc
 libqtwebkit4:i386
 ia32-libs-multiarch
 ia32-libs
 skype
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now I know why 32-bit is still the recommended version of Ubuntu. :lolflag:

---

### Post by dino99 on 2012-07-15
> **MacUntu said:**
> Now I know why 32-bit is still the recommended version of Ubuntu. :lolflag:

Its often the hard way to learn about experience  :( and pay attention to the actual kernel design: built with 64 bits pointers AND 32 bits pointers fallback

So 64 bits packages are a non sense pushed by fancy hardware marketing

---

### Post by pressureman on 2012-07-15
> **MacUntu said:**
> Now I know why 32-bit is still the recommended version of Ubuntu. :lolflag:

Well sure, if you're running hardware with less 4GB RAM, there is little reason to use 64-bit. But since that seems to the *minimum* amount of RAM that most new systems ship with, I think those days are numbered.

Also, there are many people in the scientific and media production community, who frequently work with datasets larger than 4GB, and simply could not do this on 32-bit architectures.

32-bit Skype is really the culprit in your situation, not the 64-bit OS. Skype is the *only* reason I'm running multiarch on my system. All other software I use plays perfectly OK with a pure 64-bit install.

---

### Post by irv on 2012-07-15
I have been using the 64 bit version of Ubuntu for a couple of years now on and older Dell Inspiron 1521 with a AMD 64 bit processor and have never had an issue relating to the 64 bit version. I did add 2gig of memory so I have 4gig now.

---

### Post by QIII on 2012-07-17
> **dino99 said:**
> So 64 bits packages are a non sense pushed by fancy hardware marketing

I thought the same about 16 bit years ago.

I'm sure glad I can develop software that takes advantage of the greater capability of 64 bit machine architecture.

---

### Post by QIII on 2012-07-17
> **pressureman said:**
> Well sure, if you're running hardware with less 4GB RAM

RAM may be a relatively insignificant consideration in the discussion of 64 bit architecture.

---

### Post by pressureman on 2012-07-17
> **QIII said:**
> RAM may be a relatively insignificant consideration in the discussion of 64 bit architecture.

I think I'd have to disagree with that. Other than being able to address vast amounts of memory in contiguous blocks, the 64-bit arch offers relatively little over 32-bit. OK, we also get 64-bit registers, which speeds up working with very large numbers, but that's also something that I would group with the scientific/engineering users' requirement for large RAM capacity.

Don't get me wrong, I would always run 64-bit if possible, and will never buy another box with less than 4GB. Up until last year, I even ran a 64-bit Debian server, which only had 1GB of RAM.

I think for the majority of home users however, 64-bit makes little sense on systems with less than 2 or 3GB, unless they're planning to upgrade the RAM and don't want to migrate from 32-bit to 64-bit at that stage.

64-bit on small memory footprint boxes may even have some disadvantages, due to memory pointers consuming twice as much space as their 32-bit equivalent. This is being addressed (excuse the pun) by the Linux x32 ABI, which allows the kernel to run in 64-bit mode (and thus use 64-bit registers), whilst only using 32-bit memory pointers. This is sort of a compromise between 32-bit and 64-bit, since it will limit applications to 4GB virtual memory space once again, but will allow fast 64-bit arithmetic - ideal for 64-bit systems that have less than 4GB RAM.

---

### Post by Elfy on 2012-07-17
Closed.

There are more than enough 32/64 discussion threads in the Cafe.

If the OP wants this opened they can PM and I will open and move it to Recurring Discussions.

---

