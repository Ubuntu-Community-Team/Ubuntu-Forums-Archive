---
title: "Virtualization Speed Concerns"
date: 2014-10-06
forum: Virtualisation
---

### Post by sean65 on 2014-10-06
Let me start by saying I've never posted here before so if any of these issues have been solved already please send me the link to those threads.
I know how help forums work and I'm a bit under-experienced in this so this can hopefully point me in the right direction.

I recently purchased a computer tower from a friend of mine that I'm messing around with
**Specs:** Intel Core i5 CPU 750 @ 2.67ghz x 4
8GB DDR3 Ram
1TB internal HDD
Gallium 0.4 on AMD RV770

Now here's the problem I'm having;

I'm running Ubuntu 14.04 LTS on this tower as my main OS

I'm using VirtualBox to virtualize Windows 7 Ultimate 64bit
The tower is more powerful than my previous computer (iMac Intel Core 2 Duo 2.6ghz, 4 GB DDR2 Ram, 2TB internal, and whatever graphics card Apple used in late 2008 for the $1500 model)
I expected this thing to run incredibly fast by comparison and while the main OS is fine, my virtualized OS is seriously lacking.

I've used virtual machines before and I know it's much different than a hardwired configuration, but it should still be able to run at a normal operating speed.
I have Windows 7 configured at about half my computers power (2 cores, 4gb ram) which should essentially be as efficient as my mac was
It's taking a long time to load, I've recently started noticing "trailing" i think is the word, where the mouse leaves littles ghosts all along the page.


Is there something I'm doing wrong, is there something I'm not doing?

Any input at all is appreciated, thanks for the help

---

### Post by mastablasta on 2014-10-07
depends how the virtual box is setup. it's hard to say like this from the data you provided. also windows 7 has some special effects which need hardware 3D acceleration. perhaps turning those off would solve it?!

---

### Post by ajgreeny on 2014-10-07
All I can add to that, is that my tower with similar specs to yours running Xubuntu 12.04.5,  on which I use VirtualBox VMs of the 14.04 versions of Ubuntu (with unity fully functional and fast), Xubuntu, and Lubuntu, so that I can compare the three versions in the *ubuntu family, manages all of those without any obvious slowdown compared with the host's full metal install of 12.04.

Perhaps your Windows VM settings are not quite what they need to be, but I have no experience of Win 7 to assist with what might be needed to speed it up.

---

### Post by slickymaster on 2014-10-07
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by TheFu on 2014-10-07
Settings to speed up slow virtualbox: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)
Ask if anything isn't clear.

BTW, I have that exact CPU and ran for a few years with 8G of RAM. It should be plenty fast for non-graphical things.

I don't use vbox anymore, so can't be sure what the performance should be. Switched to KVM about 2 yrs ago and don't plan to ever go back - though for desktop-on-desktop virtualization, vbox is probably the least of the evil options.

---

