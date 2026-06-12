---
title: "Could Plymouth be a bad thing?"
date: 2008-11-30
forum: The Cafe
---

### Post by Game_boy on 2008-11-30
It's possible I haven't understood the purpose or implementation of Plymouth, but I can see one flaw in its approach:

- Plymouth requires kernel modesetting of graphics drivers in order to be graphical. If not, text boot must be used.
- Kernel modesetting requires a part of the graphics driver to be in the kernel itself
- Open-source graphics drivers can never approach the 3D performance of closed drivers; any serious 3D gamer on Linux will use the closed drivers. AMD's bridgman on Phoronix Forums has some quite long posts proving this
- Linus will never allow closed modules in the Linux kernel

Therefore, all Linux gamers who aren't willing to sacrifice half of their framerate for the sake of using open drivers will be forced to have text bootup if Plymouth is adopted by all distros.

---

### Post by PilotJLR on 2008-11-30
You don't necessarily have to use the same driver for both Plymouth and your X session... but that does cause resolution changing and some flicker, which really isn't meant to happen with Plymouth.

When I tried Fedora 10 on my workstation, Plymouth didn't work right away; this was due to my nvidia 9800 card. By adding a kernel argument to grub, you can tell Plymouth to use a VESA driver, which works fine in lower resolutions.
After Plymouth switches to GDM, there is a brief flicker when the nividia driver takes over and gets up to a high resolution.

Plymouth does, though, look very nice.

---

### Post by Vadi on 2008-11-30
Thanks for pointing this out. It's rather useless to me now, just like PackageKit.

---

### Post by ssam on 2008-11-30
> **Game_boy said:**
> 
- Open-source graphics drivers can never approach the 3D performance of closed drivers; any serious 3D gamer on Linux will use the closed drivers. AMD's bridgman on Phoronix Forums has some quite long posts proving this


that surely depends if the the open source developers have access to the specs they need to right a fast driver.

Intel and ATI are being very open with specs.

---

### Post by loell on 2008-11-30
any technology that emanates from fedora will always be bad for ubuntu if incorporated early.. :lolflag:

look at pusleaudio = borked sound ;)
look at libv4l = borked webcam support ;)
look at network manager = unseemless net connection ;)

and plymouth!? you'll have a pretty good idea on what will be borked.. ;)

**just kidding!!! :D**

we are seeing regressions toning down, and hopefully it will be gone soon :)

seriously, all of those are for better desktop experience and that includes plymouth, so it should be a good thing, granted we hit a good timing. :KS

---

### Post by Game_boy on 2008-11-30
> **ssam said:**
> that surely depends if the the open source developers have access to the specs they need to right a fast driver.

Intel and ATI are being very open with specs.

Intel - Their IGPs suck anyway; you can't play most 3D games with them. If we got 110% of Windows performance they'd still suck.

ATI/Nvidia - I've addressed this. bridgman, an AMD employee assigned to Linux graphics driver development and documentation releases (i.e. most qualified to know what he's talking about) says that open drivers, for reasons of money, resources, IP and lack of accessibility, cannot ever get close to closed drivers.

---

### Post by Mr. Picklesworth on 2008-11-30
Plymouth doesn't need kernel mode setting, actually. The ascii art boot splash (which actually looks quite decent...) is still Plymouth, and I can get it to display a graphical theme like Solar by passing the appropriate vga parameter via kernel boot options. It just isn't *awesome* since with kernel mode setting there can be crossfades galore. (Fedora is really good at crossfading).
With that in mind, kernel mode setting's advantages far outweigh the disadvantages. First of all, it is an option. Drivers which support it happily coexist with those that do not. It means that there is NO display mode changing at runtime. This makes switching ttys instant, it means that ttys run at the right resolution, it makes logging in / out instant, and it means that there need be no black screen in that transition from boot splash to GDM. Part of it is prettiness, but another part is saving that time the system currently wastes with mode changing.

> ATI/Nvidia - I've addressed this. bridgman, an AMD employee assigned to Linux graphics driver development and documentation releases (i.e. most qualified to know what he's talking about) says that open drivers, for reasons of money, resources, IP and lack of accessibility, cannot ever get close to closed drivers.Playing with Linux's Synaptic Touchpad driver (with circular scrolling, two finger scrolling and multi-finger clicks) then comparing it to Windows' should quell that belief.
Intel's drivers are open source and work quite well. I don't think a third party would do as well as Intel themselves, closed source or not.

I don't really understand why the little chunk of driver that handles kernel mode setting can't be open source. I think it's more a matter of laziness and the fact that NVidia prefers writing the same underlying driver for every platform then making tiny changes to make it run. They don't integrate. They won't last.

I'm not a driver person, but I wonder if another group entirely could develop the kernel mode-setting driver for the proprietary nvidia drivers? For example, using the nouveau driver's mode-setting code then loading nvidia in xorg?

Here is a nice little article:
[http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1](http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1)

---

### Post by SunnyRabbiera on 2008-11-30
> **Game_boy said:**
> 
ATI/Nvidia - I've addressed this. bridgman, an AMD employee assigned to Linux graphics driver development and documentation releases (i.e. most qualified to know what he's talking about) says that open drivers, for reasons of money, resources, IP and lack of accessibility, cannot ever get close to closed drivers.

yeh but thats because he is probably a closed source suckup, open source drivers can be better then closed source ones if given the chance.
Though with hardware drivers I can understand the pro closed source apprach, its applications I can see where open source is needed.

---

### Post by Game_boy on 2008-11-30
> **Mr. Picklesworth said:**
> Plymouth doesn't need kernel mode setting, actually. The ascii art boot splash (which actually looks quite decent...) is still Plymouth, and I can get it to display a graphical theme like Solar by passing the appropriate vga parameter via kernel boot options. It just isn't *awesome* since with kernel mode setting there can be crossfades galore.

Playing with Linux's Synaptic Touchpad driver (with circular scrolling, two finger scrolling and multi-finger clicks) then comparing it to Windows' should quell that belief.
Intel's drivers are open source and work quite well. I don't think a third party would do as well as Intel themselves, closed source or not.



To your first point, I'm glad to hear that, but if that is the case why didn't they enable that by default?

To your second, I was talking about graphics only. For almost all other hardware, open works great. Graphics requires specialist coders: the open ATI driver has almost zero commits from people who aren't employed to work on it. Getting the last 50% performance out of a driver requires a huge team of specialists (we only have a few and they will always be tied up getting features to work over optimising performance) and IP which, no matter what AMD wants, cannot release due to contracts that would cost them their Windows market to break.

---

