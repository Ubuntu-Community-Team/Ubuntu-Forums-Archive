---
title: "memory needed for Lubuntu tested with vbox"
date: 2013-04-14
forum: Ubuntu Development Version
---

### Post by sudodus on 2013-04-14
I want to share these results
                        
[SIZE=4]**Testing Lubuntu Raring daily in VirtualBox with different amount of RAM available and 512 MB swap.**[/SIZE] 

   
[SIZE=3][B]A. Installation

[/B][/SIZE]***1. 768 MB RAM***
It is possible to boot a live session and install 'carelessly' from it. But you should create swap at the partitioning page, otherwise there might be problems later.

[I][B]2. 512 MB RAM
[/B][/I]It is possible to boot a live session and install from it, but only if you have already created swap before starting the installer. Otherwise it will get stuck before the partitioning page. So use gparted and create partitions including swap.

***3. 384 MB RAM***
It is possible to boot a live session but not to install from it. It does not help to have already created swap before starting the installer. It is not even possible to install directly from the installer (directly at boot).  But it works well to install from the alternate iso file, which uses text mode.

***4. 256 MB RAM***
It is possible to run a live session.  I can install neither from the desktop iso nor the alternate iso with my default settings of the virtual machine: Acceleration: VT-x/AMD-V, nested paging, PAE/NX, 128 MB video memory, 3D acceleration.  When I shut off VT-x/AMD-V and nested paging, and allocate only 32 MB for video memory, the alternate iso can install Lubuntu.

[SIZE=3]**B. Running an installed system**[/SIZE]

***1. 384 MB RAM or more***
It works well to run Lubuntu with 384 MB RAM (or more) and 512 MB swap, but of course the low memory specs will limit what can be run and done.

***2. 256 MB RAM***
It works to run Lubuntu with as little as 256 MB RAM and 512 MB swap, but of course the low memory specs will limit severely what can be run and done. Firefox works but slowly due to swapping where Chromium-browser will stall (show the 'Dead Jim' screen), for example Firefox can play youtube video clips. Gimp can edit (with tools and filters) 6 Mpixel but not 12 Mpixel pictures, and Mplayer can play local video clips. Office tasks also work.

---

