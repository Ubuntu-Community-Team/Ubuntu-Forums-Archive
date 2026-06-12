---
title: "Nvidia driver trouble using 14.04 installation and virtual box of the same install"
date: 2016-04-01
forum: Virtualisation
---

### Post by jeroenvandenheuvel on 2016-04-01
I'm trying to use both a normal installation of 14.04 and virtual box (from win 8.1) that reads the same installation (via the raw feature of virtualbox). No matter what nvidia driver I use, virtualbox enters a boot loop.

Without an nvidia driver the virtualbox works, but I need the nvidia driver for CUDA.

I've tried drivers 352 (bundled with CUDA), 358 and 361 (latest). All three same issue. 358 and 361 also displayed wrong on my main monitor. A sizeable border (left and top) falls of screen in the normal boot.

There could be a conflict between the virtual box driver and the nvidia driver, since both are installed. But I don't know how to resolve this.

Can anyone help me? (PS: using a GTX 660)

---

### Post by SeijiSensei on 2016-04-01
Virtualbox presents a virtualized graphics interface to the guest operating system.  I don't know of any way to address the graphics hardware directly from the guest.  The best you can get is the driver that comes with the Extension Pack: [https://www.virtualbox.org/manual/ch04.html#guestadd-video](https://www.virtualbox.org/manual/ch04.html#guestadd-video)

---

### Post by jeroenvandenheuvel on 2016-04-02
Thanks for the response. I have guest additions installed and they work fine as long as the nvidia driver is uninstalled. But I also need this nvidia driver for CUDA.

My best option right now is switching drivers, but that kind of defeats the purpose of my virtual machine. Might as well reboot into the other OS then.

---

### Post by MAFoElffen on 2016-04-03
Plus one with SeijiSensei...

A little more detail on what he said ... and some options. 

The detail of what he said, is that Virtualbox is  type 2 hypervisor: Meaning it uses software to virtualize a simulated hardware environment. So even with guest additions or the extended pack installed, the enhanced graphics enabled with those is still simulated... so installing an NVidia Driver fails because there is no actual hardware passthrough to a real NVidia GPU. VirtualBox does not do video hardware passthrough. Not knowing if I needed to beat a dead horse, but you didn't sound like you fully understood the why. So there it is.

Options:
(1) Use a type 1 hypervisor that does do passthrough...

(2) Do a dual boot, to run Linux and Winodws

(IHMO-- Both the above are not needed because of #3 below)

(3) Use the Linux version of the NVidia CUDA toollkit... NVidia's CUDA Toolkit is available for Windows, MAC OSx, and ... **[COLOR=#ff0000]Linux[/COLOR]**. Unless, maybe you think your target app is specifically doing CUDA on a Windows platform? But that is not how CUDA works. NVidia CUDA apps are crossplatform, i.e. run on a runtime module, then address to the NVidia GPU... That is what makes them cross-platform apps. You knew that right? It's in the (singular) programming guide. There is no programming guide for what platform it is running on. The only changes are to allow for the GPU you are using, and that GPU's capabilities.

---

### Post by jeroenvandenheuvel on 2016-04-04
I think I haven't explained my problem properly (maybe because I didn't understand CUDA well enough, thanks MAFoElffen!). 

I don't want to use CUDA through the virtual box. I use CUDA by booting linux from poweroff. But I also want to be able to access the same ubuntu install from windows.
I've installed the nvidia driver when booted into ubuntu (not virtual box) to use CUDA, but this breaks the virtual box. (boot loop).

---

