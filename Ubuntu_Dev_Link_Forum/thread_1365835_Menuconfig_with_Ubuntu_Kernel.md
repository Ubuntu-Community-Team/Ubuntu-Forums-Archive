---
title: "Menuconfig with Ubuntu Kernel"
date: 2009-12-27
forum: Ubuntu Dev Link Forum
---

### Post by ghostknife on 2009-12-27
I am busy porting a driver for a network device to the new kernel in Karmic (there were some API changes from 2.6.28).

For this I need to rebuild the kernel, and have done so configuring it via the files in debian.master/config.

I followed the steps at:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

With this I got the sources for the same build as with an updated karmic (ie. 2.6.31-16-generic).

I was then able to build with the same kernel options, adding debugging information (gcc -g).

If I were to run make menuconfig, will I be working from the same configuration, or do I have to import this configuration somehow. 

I'm not familiar with the configuration layout, being quite different than the standard layout (.config only), though I would like to get the menu to make managing the options easier and less error prone.

Thanks.

---

