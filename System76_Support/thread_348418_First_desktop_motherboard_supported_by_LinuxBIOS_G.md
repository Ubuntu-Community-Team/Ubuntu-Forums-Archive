---
title: "First desktop motherboard supported by LinuxBIOS: GIGABYTE M57SLI-S4"
date: 2007-01-28
forum: System76 Support
---

### Post by DRM_free on 2007-01-28
The state of the art [[COLOR="DarkOrange"]GIGABYTE M57SLI-S4[/COLOR]]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2287&ModelName=GA-M57SLI-S4") is the first desktop motherboard supported by [LinuxBIOS]("http://linuxbios.org"), thanks to AMD-employee Yinghai Lu who [[COLOR="DarkOrange"]released[/COLOR]]("http://www.openbios.org/pipermail/linuxbios/2007-January/018001.html") GPL-licensed code a couple of days ago. This motherboard is based on the NVIDIA® nForce 570 SLI chipset and AMD's latest Socket AM2 socket. It supports Athlon 64 X2 / Athlon 64 FX / Athlon 64 processors, and contains advanced features such as:
2X PCI Express x16 slots
3X PCI Express x1 slots
3X 1394a (FireWire) ports
SATA RAID
6X SATA 3Gb/s slots.

It would be awesome if System76 offered a desktop based on this motherboard -- the mere fact that this is the **first desktop ever to run a free BIOS** will make System76 front page news on all FOSS-friendly sites. Imagine how many LinuxBIOS computers you will sell when Slashdot comes out with the story: "*System76 first to sell desktops pre-installed with LinuxBIOS*".

**Update**: You can already [[COLOR="DarkOrange"]buy GIGABYTE M57SLI-S4 motherboards from Newegg[/COLOR]]("http://www.newegg.com/Product/Product.asp?Item=N82E16813128014").

---

### Post by becominglumberg on 2007-01-29
This is very good news, especially the news that this motherboard is from the current generation. Do you know if this would this allow for hardware raid to work out of the box?

---

### Post by crichell on 2007-01-29
This is cool news!  I'm happy to see the project pickup some manufacturing.

---

### Post by alinuxfan on 2007-01-29
DARN!
I just bought a mobo and CPU. BAH

I guess I should have waited a week or checked up again on the status of LinuxBIOS:mad:

---

### Post by DRM_free on 2007-01-29
*Do you know if this would this allow for hardware raid to work out of the box?*

I'm not sure, but you can ask on the [LinuxBIOS mailinglist]("http://www.linuxbios.org/mailman/listinfo/linuxbios"). This motherboard can certainly do software RAID, however.

The philosophy of LinuxBIOS is to give the OS (Linux) as much control over the hardware as possible. In general, this means that no LinuxBIOS code runs after the OS has booted. This is a good thing because if the BIOS is in charge of driving the hardware (as is the case in [Intel's EFI]("http://kerneltrap.org/node/6884")),  DRM restrictions can be put into the BIOS that cannot be overcome by changing the OS. It's also a good idea to keep the BIOS small and simple in order to keep bugs out. After all, it's easier to replace a buggy OS than to re-flash the BIOS.

---

### Post by eeried on 2007-02-28
And Is this Mobo Linux-compatible? 

Anyway it's a pity it's rather expensive with features not everyone needs (SLI). Lets' hope other LinuxBIOS Mobo come out.

---

### Post by DRM_free on 2007-02-28
*And Is this Mobo Linux-compatible?*

Yes, all the  [GIGABYTE GA-M57SLI]("http://www.newegg.com/Product/Product.asp?Item=N82E16813128014")'s built-in components (audio, ethernet, USB, FireWire, etc) work out of the box in Linux.

---

### Post by apoclypse on 2007-03-01
One thing I was interested in was a project they had going for Linux bios that played  animation at boot time as well as a wav file. This slowed down startup but it was interesting nonetheless. I think if they created a nice boot chime (maybe the Ubuntu drum thing they use for gdm) and and the ubuntu logo at startup along with slick boot, we can have as close to a mac experience as possible. I think that the first Linux system builder to get all of this right will be the one to watch.

---

### Post by Jerry Wolczanski on 2007-03-01
Well, we shall see.  I'm planning to build a Linux-only machine (Ubuntu) and just as I was in the process or ordering an Intel chip and motherboard, I found the thread talking about the new Gigabyte M57SLI-S4.  I changed the order and bought the Gigabyte board and an AMD dual core chip.

In 3-4 days, I'll have a pile of parts which will become a computer.  Having build ham radio gear from scratch (both tube and solid state), I have no qualms about building a computer.  Software and Hardware, now that's another matter.  Stay tuned!

Ubuntu has popularized Linux in a way no other distribution has.  I'm a believer!
Jerry

---

### Post by borris.morris on 2007-03-01
Sounds good to me. I would love to get this mobo for my desktop. Right now got an AMD Duron 1.3 Ghz overclocked to 1.5 Ghz. It runs linux excellent.

---

### Post by koshimazaki on 2007-03-04
> **DRM_free said:**
> *And Is this Mobo Linux-compatible?*

Yes, all the  [GIGABYTE GA-M57SLI]("http://www.newegg.com/Product/Product.asp?Item=N82E16813128014")'s built-in components (audio, ethernet, USB, FireWire, etc) work out of the box in Linux.

What about hardware monitoring?

---

### Post by Skerit on 2007-03-10
I want a Linux-only system, and I really need to replace my current hardware, but AMD is so .. bleh. It seems to me they're always 5 steps behind Intel, and there really aren't any other GOOD motherboards who are supported :(

---

### Post by alterego74 on 2008-03-14
Hey Jerry....

Did you get that motherboard yet???
Ok, it  maybe a bit soon, but I've been playing with mythbuntu for a while now (loving and hating it, btw)
I am considering this mobo for my backend / server and was wondering if you had any wisdom you could share.

Thanks!

---

