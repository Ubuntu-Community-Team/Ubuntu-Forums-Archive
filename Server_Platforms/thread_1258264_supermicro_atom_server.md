---
title: "supermicro atom server"
date: 2009-09-04
forum: Server Platforms
---

### Post by jay3712 on 2009-09-04
I want to build my new ubuntu server with an atom, and I like the [supermicro server board]("http://www.supermicro.com/products/motherboard/ATOM/945/X7SLA.cfm?typ=H") because it has better upgrade possibilities and 4 sata ports. I searched a bit but haven't found much about this board and ubuntu. This is going to be a file server, print server, media server, and really something to tinker with. 

Does anyone have any experience with this board under ubuntu/linux?

Thanks,
Jason

---

### Post by windependence on 2009-09-05
This board will work perfectly with Linux. In my experience, you will probably want to run XCFE or GNOME if you run a GUI, although I would highly suggest you don't if you can help it. KDE is a dog on these.

-Tim

---

### Post by jay3712 on 2009-09-05
My current server (now with bad motherboard) is headless, and I would want a pretty similar setup. What powersupply should I get to run this board with 4 hard drives? I'm going to put this in an old tower case I have, so size isn't an issue. 

Thanks

---

### Post by castrojo on 2009-09-05
I have also been mulling a low power atom server, please keep us posted on your progress!

---

### Post by jay3712 on 2009-09-06
In reading the memory requrements, can it take 2GB in each slot or 2GB total (2x1GB)? Not that I'll need that much memory, but I already have a 2GB stick that would work, unless I need to order 2x1GB sticks.

---

### Post by jay3712 on 2009-09-06
Ok I think I'm gonna go for it. Here is what the setup is gonna be:

Supermicro X7SLA-H
Antec Earthwatts 380 power supply (will I need the 430 when I add more hard drives?)

and I already have:
(2) 512mb sticks ddr2
500Gb, 1Tb sata storage drives, 40gb ide os drive
dvd rom
case

I probably could put something together that would work for cheaper, but I like experimenting with new stuff.


Lastly, can anybody reccomend a good site to order this board from? Newegg doesn't have it. So far I have found wiredzone.com and ebunlimited.com have it in stock. 

Thanks for your replies!!

---

### Post by kerry_s on 2009-09-06
next to the raid it says "windows only", is the raid software? might want to check?

that board looks almost like mine, i'm using a bare bone system:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012)

it's fully linux compatible. i just added a hd & 2gig ram. didn't even bother to install a cd yet. i install through usb.

---

### Post by jay3712 on 2009-09-06
Thanks for pointing out the raid. The primary reason I want more expansion slot options is so that I can add a hardware raid card in the future. For now I'm just going to do an rsync every night.

---

### Post by jamesrfla on 2009-09-06
I am planing to get this [http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030](http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030) but it seems to be currently out of stock or something. Hopefully it will come back so I can buy it. It comes with a 220Watt power supply, has RAID 0 and 1 capabilities, and has dual Gigabyte LAN. I will be putting 2 hard drives in RAID 1. I hope this blade will not use much power.

---

### Post by hessiess on 2009-09-06
> 
next to the raid it says "windows only", is the raid software? might want to check?

Wouldent matter, Linux can do softwere RAID too.

---

### Post by jamesrfla on 2009-09-06
> **hessiess said:**
> Wouldent matter, Linux can do softwere RAID too.

If you use the LSI MegaRAID controller it works for both Windows and Linux. Second RAID option built into the motherboard.

---

### Post by falconindy on 2009-09-06
Software and onboard RAID controllers are about as stable as WindowsME. Above all else, remember that RAID is NOT a backup solution.

---

### Post by windependence on 2009-09-07
> **jamesrfla said:**
> I am planing to get this [http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030](http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030) but it seems to be currently out of stock or something. Hopefully it will come back so I can buy it. It comes with a 220Watt power supply, has RAID 0 and 1 capabilities, and has dual Gigabyte LAN. I will be putting 2 hard drives in RAID 1. I hope this blade will not use much power.

I have 82 of these on order. Should have some by 9/21. Let me know if you can't get one through New Egg.

-Tim

---

### Post by windependence on 2009-09-07
> **falconindy said:**
> Software and onboard RAID controllers are about as stable as WindowsME. Above all else, remember that RAID is NOT a backup solution.

HARDWARE RAID controllers built into the board are just fine. This one looks like software on a chip, so I doubt it will work with Linux.

There are many other good cheap RAID controllers that will work with Linux, so I wouldn't be too worried about that.

-Tim

---

### Post by jay3712 on 2009-09-09
I'm not going to be doing raid on this in the near future, just a cron job to rsync every 12 or 24 hours. 

I'm still looking for recommendations on where to get the board. CDW has it but it ends up being $175 after shipping and taxes. Does anyone have anything to say about wiredzone.com or ebunlimited.com? Any other reputable site to get this from? Come to think of it, I don't think I have ever ordered computer hardware from anywhere except Newegg.

Thank for all the replies!

---

### Post by bear24rw on 2009-09-09
> **windependence said:**
> i have 82 of these on order. Should have some by 9/21. Let me know if you can't get one through new egg.

-tim

82??

---

### Post by jamesrfla on 2009-09-10
> **windependence said:**
> I have 82 of these on order. Should have some by 9/21. Let me know if you can't get one through New Egg.

-Tim

I think they are sold out because I don't see a add to cart button anymore. I was going to wait maybe 4 months before I got it so hopefully they will have them back by then. Let me know how they are and if they can run VMware ESXi on them. Also any additional information you can send me when you get them would be cool.

---

### Post by jay3712 on 2009-09-12
Well I ordered the motherboard from wiredzone.com and a corsair power supply from Newegg. I will update this thread when I get it up and running.

Thanks for all your help and replies.

Jason

---

### Post by jay3712 on 2009-10-14
This board works great. I am running it as a print server, file/media server, torrenting, ftp, and I'm gonna set up a VPN soon. It's really quick too.

---

