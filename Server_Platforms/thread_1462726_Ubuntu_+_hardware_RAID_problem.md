---
title: "Ubuntu + hardware RAID problem"
date: 2010-04-26
forum: Server Platforms
---

### Post by any.linux12 on 2010-04-26
Hi everyone!

I am a network administrator with 1 and a half year of experience with ubuntu distros. I got an industrial PC last Friday and I am having some uncommon problems with the Grub Loading. This PC has hardware RAID capability with hot-swappable hard drives but when I do the installation ubuntu detects 2 hard disk instead of the RAID Volume. As far as I can understand ubuntu makes the installation in the first hard disk and the RAID 1 mirrors the installation to the second but when I start the system it doesn't know where the Grub configuration is, as it sees 2 hard drives with the same content. The only howto's that I have seen tell me to use a fakeraid or a HW and SW RAID at the same time but I think that it will mean that I loose the hot-swappable capability. Another point is that this PC's HW RAID works with windows, so it's not a hardware issue and I have a server from HP running with hardware RAID 5, hot-swappable and ubuntu, with no problems.

Any idea?

Thanks

---

### Post by windependence on 2010-04-26
Most likely your HW RAID controller is really software on a chip, in other words fake RAID. What kind of controller are you using? 

Many here will suggest software RAID but I am not a big fan. I can suggest some controllers that may work if yours isn't supported.

-Tim

---

### Post by any.linux12 on 2010-04-26
> **windependence said:**
> Most likely your HW RAID controller is really software on a chip, in other words fake RAID. What kind of controller are you using? 

Many here will suggest software RAID but I am not a big fan. I can suggest some controllers that may work if yours isn't supported.

-Tim

You are correct. After trying a bunch of distributions I found that I have a fake RAID. I am installing the 9.04 Alternate distro and it has found the RAID although I am not sure if I can replace the hard drive without turning the PC off and rebuilding the array. If this doesn't work we have to buy a PCI controller. I saw [this]("http://www.exsys.ch/index.php?main_page=product_info&products_id=278"). It should work right?

---

### Post by windependence on 2010-04-26
> **any.linux12 said:**
> You are correct. After trying a bunch of distributions I found that I have a fake RAID. I am installing the 9.04 Alternate distro and it has found the RAID although I am not sure if I can replace the hard drive without turning the PC off and rebuilding the array. If this doesn't work we have to buy a PCI controller. I saw [this]("http://www.exsys.ch/index.php?main_page=product_info&products_id=278"). It should work right?
Yep, that looks like it's based on a silicon image 3512 chipset. That should work.

So the alternate install CD found the RAID? I didn't even know this was possible. It's great if it is. I also find that the LTS releases seem to support more hardware. I'm sticking with 8.04 until the new one is released shortly. Once those releases are updated, they are every bit as good if not better than the interim releases.

-Tim

---

### Post by Grenage on 2010-04-26
[s]That could easily be a FakeRAID card, too; genuine RAID cards aren't particularly cheap.  [/s]While software RAID is always an option, I always recommend people don't use it.  Compared to a real hardware RAID system, it's a poor substitute (99/100 times).

---

### Post by any.linux12 on 2010-04-26
> **windependence said:**
> Yep, that looks like it's based on a silicon image 3512 chipset. That should work.

So the alternate install CD found the RAID? I didn't even know this was possible. It's great if it is. I also find that the LTS releases seem to support more hardware. I'm sticking with 8.04 until the new one is released shortly. Once those releases are updated, they are every bit as good if not better than the interim releases.

-Tim

The alternate is working perfectly which is kind of shocking because now I don't understand why they didn't include this RAID function in the Desktop and Server distro.

Thanks everyone!

---

### Post by windependence on 2010-04-26
> **any.linux12 said:**
> The alternate is working perfectly which is kind of shocking because now I don't understand why they didn't include this RAID function in the Desktop and Server distro.

Thanks everyone!
Looks like the driver is built in to the kernel on the alternate disc. That's good to know.

Thanks,

-Tim

---

