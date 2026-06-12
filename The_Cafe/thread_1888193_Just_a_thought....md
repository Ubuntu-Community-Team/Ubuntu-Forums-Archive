---
title: "Just a thought..."
date: 2011-11-28
forum: The Cafe
---

### Post by *^kyfds( on 2011-11-28
What would happen if you ran the wubi ubuntu installer with wine on Ubuntu?

it's just a thought :3

---

### Post by cgroza on 2011-11-28
I don't think something like wine provides the environment for something like Wubi to work properly.

---

### Post by Dry Lips on 2011-11-28
> **cgroza said:**
> I don't think something like wine provides the environment for something like Wubi to work properly.

What about Wubi running within a virtualbox instance of windows then?

---

### Post by Basher101 on 2011-11-28
what you try to do is a OS inside a OS inside a OS. OSception o.O

---

### Post by *^kyfds( on 2011-11-28
> **Basher101 said:**
> what you try to do is a OS inside a OS inside a OS. OSception o.O

[http://www.omgsoysauce.com/wp-content/uploads/2011/02/winception1.jpg](http://www.omgsoysauce.com/wp-content/uploads/2011/02/winception1.jpg)

---

### Post by jjex22 on 2011-11-28
When I got my new ram earlier in the year, I had nothing to really push it up anywhere near 16gb (I bought it primarily for the extra speed, and there was a £35 difference between 8GB and 16GB so, no brainer) Anyhoo.. I decided to try installing windows vista inside my windows 7 vhd - no go; VMWare had a fit,so I gave Virtualbox a go, sort of worked but I found windows wouldn't have it - the installer just never found a hard drive, So I copied one of my linux vdi's into the guest windows 7 and it ran - though guest additions was boned! I suppose it wasn't too slow really for what was going on, but the complete inability to connect to the host internet, or to share any information short of copying it as an .iso into the windows 7 guest, mount and run inside the second guest meant my dream of a guest inside a guest inside a guest was just infeasible!

Anyway, this leads me to assume that wubi inside a virtual machine would work - if I could get a virtual machine to run inside a virtual machine (admittedly not the same type of virtual machine) then I can't see why wubi, which isn't a virtual machine, should work! ... might even give it a try at the weekend, having never even used wubi!

---

### Post by nerdopolis on 2011-11-28
My guess is that it will probably create the file system files it  creates in ~/.wine/drive_c and then try to configure the Windows  bootloader configuration files (which will still be in ~/.wine/drive_c  if they are even provided by WINE) It won't configure GRUB, and I don't  know if WUBI touches the MBR. (It won't even work anyway unless you run  WINE as root)... ...probably nothing special or cool...

---

### Post by Paqman on 2011-11-29
> **Dry Lips said:**
> What about Wubi running within a virtualbox instance of windows then?

Wubi would work exactly as advertised, although I'm not sure how well Ubuntu would run if you booted it on a VM that was set up for a Windows host.

---

### Post by typhoon_tip on 2011-11-29
> **Thehumorouscheese said:**
> [http://www.omgsoysauce.com/wp-content/uploads/2011/02/winception1.jpg](http://www.omgsoysauce.com/wp-content/uploads/2011/02/winception1.jpg)

ROFL !!! :D:D:D

Saved this pic.

---

### Post by Erik1984 on 2011-11-29
> **typhoon_tip said:**
> ROFL !!! :D:D:D

Saved this pic.

Me too. Yes those BSOD jokes are getting old but this adds a new dimension ;)

---

