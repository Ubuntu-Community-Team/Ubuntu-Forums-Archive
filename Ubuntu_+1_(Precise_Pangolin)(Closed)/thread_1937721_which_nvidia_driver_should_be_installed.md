---
title: "which nvidia driver should be installed?"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TDK800 on 2012-03-08
Additional drivers offers following options, which should I activate:

nvidia-current
nvidia-current-updates
nvidia-173
nvidia-173-updates

---

### Post by mc4man on 2012-03-08
Post info about your display adapter & I'm sure people could properly advise you

```
sudo lshw -C display
```

---

### Post by TDK800 on 2012-03-08
*-display UNCLAIMED     
       description: VGA compatible controller
       product: G86 [GeForce 8400M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128)

---

### Post by philinux on 2012-03-08
> **TDK800 said:**
> Additional drivers offers following options, which should I activate:

nvidia-current
nvidia-current-updates
nvidia-173
nvidia-173-updates

nvidia-current

I think you'll find that one has recommended appended to it.

[http://askubuntu.com/questions/66548/whats-the-difference-between-the-nvidia-current-and-nvidia-current-updates-pac](http://askubuntu.com/questions/66548/whats-the-difference-between-the-nvidia-current-and-nvidia-current-updates-pac)

---

### Post by mc4man on 2012-03-08
Use either nvidia-current or nvidia-current-updates (atm the same

Have the same here,  - though it suffers from this corner case bug
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383)

If you're affected there is a workaround of sorts

---

### Post by TDK800 on 2012-03-08
All options it offers have the same name:
"NVIDIA binary Xord driver, kernel module and VDPAU library"
Can only differentiate using the readme file path in the descriptions.

Giving it a try.

---

### Post by TDK800 on 2012-03-08
Unfortunately still same problem I've been having throughout using 12.04 - when unity desktop should come up the screen switches off instead. 

I can ctrl+f2 into shell screen which has flickering text, but ctrl+f7 back to desktop turns screen off again.

Is it a known bug?

---

### Post by mc4man on 2012-03-08
I think your issue can be seen here - 
> [COLOR="Red"]*-display UNCLAIMED[/COLOR]
description: VGA compatible controller
product: G86 [GeForce 8400M GS]

Does your machine also have onboard graphics or something?

I know little of such stuff, can say that with pretty much the same chipset nvidia drivers work fine with the exception of mentioned compiz performance bug

Ex. here on Dell laptop
>  *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8400M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:ef00(size=128) memory:f4000000-f401ffff



---

### Post by VinDSL on 2012-03-08
> **mc4man said:**
> Does your machine also have onboard graphics or something?
Hrm...

I don't see an IRQ assigned to his vid card, soooo...

Maybe you're right.  ;)

---

### Post by philinux on 2012-03-08
> **VinDSL said:**
> Hrm...

I don't see an IRQ assigned to his vid card, soooo...

Maybe you're right.  ;)

Yep should look like this. Or similar


```
resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:dc00(size=128) memory:fbee0000-fbefffff

```

---

### Post by TDK800 on 2012-03-08
Yes, also has onboard intel graphics. How can I switch that off or over to Nvidia?

---

### Post by inajaro on 2012-03-08
I'm sincerely sorry for jumping into this thread but I can't seem to find my way around well enough to locate a thread that was probably posted years ago, so can someone please point me in the right direction? Toshiba Satellite 5105-S607 with NVidia Gforce 440. Ubuntu 8.04. only version that contained generic graphics drivers. I would like to upgrade OS but I am command line clueless. HELP!!! :confused:

---

### Post by VinDSL on 2012-03-08
> **TDK800 said:**
> Yes, also has onboard intel graphics. How can I switch that off or over to Nvidia?
Every mobo is different, but...

There should be somewhere in BIOS to disable it.

In the old days, you had to physically move jumpers around.

---

### Post by dino99 on 2012-03-08
> **inajaro said:**
> I'm sincerely sorry for jumping into this thread but I can't seem to find my way around well enough to locate a thread that was probably posted years ago, so can someone please point me in the right direction? Toshiba Satellite 5105-S607 with NVidia Gforce 440. Ubuntu 8.04. only version that contained generic graphics drivers. I would like to upgrade OS but I am command line clueless. HELP!!! :confused:

sudo update-manager -d -c

---

### Post by mc4man on 2012-03-08
> **inajaro said:**
> I'm sincerely sorry for jumping into this thread but I can't seem to find my way around well enough to locate a thread that was probably posted years ago, so can someone please point me in the right direction? Toshiba Satellite 5105-S607 with NVidia Gforce 440. Ubuntu 8.04. only version that contained generic graphics drivers. I would like to upgrade OS but I am command line clueless. HELP!!! :confused:

You might want to explore the specs on that machine, it would appear to be a 'bit' challenged as to running 12.04 or there-abouts

This should give you an easy to read overview, look in home folder

```
sudo lshw -html > hardware.html
```

---

