---
title: "nvidia drivers wont load"
date: 2018-03-30
forum: Ubuntu Development Version
---

### Post by f76 on 2018-03-30
Hi!
 Trying Bionic and i need to get graphics and 3d running eventually for some applications that are accelerated with GPU

I have installed nvidia-390 (It should support my GPU).
I did get a display prompting me to disable some kind of encryption so I could run proprietary software, but --- Im not sure If it worked --

When I run:
>>> sudo lshw -C video

I get
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GM107GL [Quadro K1200]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

Nvidia-settings does not show my gfx-card.

---

### Post by #&amp;thj^% on 2018-03-30
Have a look at all the post's down from #45: [https://ubuntuforums.org/showthread.php?t=2385770&p=13752525#post13752525](https://ubuntuforums.org/showthread.php?t=2385770&p=13752525#post13752525)

---

### Post by dino99 on 2018-03-30
nvidia propose 346 for that card (to be installed from ubuntu archive; purge the previous one(s) if needed first)
[http://www.nvidia.com/download/driverResults.aspx/83304/en-us](http://www.nvidia.com/download/driverResults.aspx/83304/en-us)

sudo apt purge *nvidia*
sudo apt-get install nvidia-346

---

### Post by f76 on 2018-03-30
> **dino99 said:**
> nvidia propose 346 for that card (to be installed from ubuntu archive; purge the previous one(s) if needed first)
[http://www.nvidia.com/download/driverResults.aspx/83304/en-us](http://www.nvidia.com/download/driverResults.aspx/83304/en-us)

sudo apt purge *nvidia*
sudo apt-get install nvidia-346

Thanks a lot! It worked

---

