---
title: "Intel Q45 or nV 9x00 as base for NAS/GP Server"
date: 2009-08-06
forum: Server Platforms
---

### Post by jalyst on 2009-08-06
Hi,

I'm trying to decide between the following motherboards from the following chip-set families... 

_nVidia MCP 730i/Geforce 9400_:

This is pretty much the only decent option in Australia (Gigabyte's not available)
[http://www.dfi.com.tw/portal/CM/cmproduct/XX_cmproddetail/XX_WbProdsWindow?itemId=581&downloadFlag=false&action=e&windowstate=normal&mode=view](http://www.dfi.com.tw/portal/CM/cmproduct/XX_cmproddetail/XX_WbProdsWindow?itemId=581&downloadFlag=false&action=e&windowstate=normal&mode=view)

_Intel GMCH82Q45/ICH10DO_:

I'm yet to decide between these two (Asus not available in Australia) but I'm erring more towards the Intel board:
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=3034](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=3034)
[http://ark.intel.com/Product.aspx?id=34687](http://ark.intel.com/Product.aspx?id=34687)
Mainly because there's no guarantee that GB will provide BIOS updates every time Intel's apps/firmware is updated...

I need to work out which chip-set is most suited for my intended application, and a big part of that will be determining which has the best support in the OSS world.
If possible I'd like to implement a _bare-metal hypervisor_ that will allow me to have multiple simultaneous specialised environments running; the 1st of those being a NAS.*

Power management/efficiency of the two chip-sets seems to be a fairly close affair... 
At idle the Intel chip-set has a _tiny_ advantage but at load they're equal, brownie points to nV because at load it's IGP wallops Intel's yet it draws no more wattage!

When it comes to IGP's Intel's G45 (superior to the Q45) gets thoroughly walloped, but this is of little interest to me.
I'm more interested in performance disparities -if any- in terms of: Memory, e/SATA, RAID, USB, Ethernet etc...

According to most reviews (Windows based), Memory & SB I/O performance is very similar between the two chip-sets, although nV seems to win _just_ in most areas.
Apparently the leads are so tiny that it's unlikely the differences would be noticeable in real world applications...

This may be a very different situation in GNU/Linux, *BSD, GNU/Solaris etc. but if not the choice becomes clearer in favour of nV! 

However...

If I choose the nV platform it seems I lose the following which are part of the Q45 chip-set (not just the CPU):
Intel VT-d, JTAG boundary scan, Intel AMT 5.x Pro, Intel TPM 1.2 

I've read-up on the aforementioned features and some of them are pretty darn cool...
Perhaps the coolest (as I understand them thus far) is VT-d...

I imagine it would be very useful if I were to implement the bare-metal hypervisor I spoke of earlier...
All four of are part of the core-logic of the chip-set and I'm not sure there's a decent substitute for any of them!

According to some adverts Intel TXT is available to the nV chip-set, I'm yet to confirm but this feature may only rely on CPU selection. 

Just interested in others thoughts on where to head to from here....
Particularly those who've had lots of experience using Intel 4 Series (preferably Q45) OR nV 730i/9x00 motherboards in "*nix-land"!

Cheers
Jed
*will prolly try FreeNAS 1st

---

### Post by windependence on 2009-08-06
If you want anything in Oz from the states, I can hook you up mate. You would have to pay shipping and taxes but I can get it there if you really want it.

-Tim

---

### Post by jalyst on 2009-08-07
Not necessary but thanks...

I'm more interested in peoples thoughts on which way i should head.
Do I need to reconsider chip-sets entirely considering I've become enamoured with the bare-metal hypervisor concept?

---

### Post by windependence on 2009-08-08
No but if you are going to use VMware ESXi, here is a link to the whitebox compatibility list maintained by the user community.

[http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php](http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php)

[http://www.vm-help.com/esx/esx3.5/Whiteboxes_SATA_Controllers_for_ESX_3.5_3i.htm](http://www.vm-help.com/esx/esx3.5/Whiteboxes_SATA_Controllers_for_ESX_3.5_3i.htm)

Chipsets are the least of your worries. You should try to get a board that supports a processor with virtualization on the chip. I use mostly AMD in mine and have no problems.

If you need help, give me a shout.

-Tim

---

### Post by jalyst on 2009-08-09
Thanks for your thoughts Tim...
I'm now considering an entirely different hardware base.

SOHO Bare-metal (native) Hypervisor; best Chipset/CPU combo?
[http://episteme.arstechnica.com/eve/forums?a=tpc&s=50009562&f=77909774&m=597000880041&r=807002980041](http://episteme.arstechnica.com/eve/forums?a=tpc&s=50009562&f=77909774&m=597000880041&r=807002980041)

Amazingly in-depth thanks mostly to one user! "Prototyped"
Very interesting read if you're curious about implementing something similar.

I will prolly try XEN/ESXi before anything else.

Thanks again,
-j.

---

