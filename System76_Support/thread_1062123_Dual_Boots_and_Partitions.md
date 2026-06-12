---
title: "Dual Boots and Partitions"
date: 2009-02-06
forum: System76 Support
---

### Post by chez17 on 2009-02-06
I am installing XP because I need to dual boot it for work. (And I just miss Civ 4, sorry. Wine doesn't support the Direct2Drive version)

Anywho, XP doesn't like the SATA drive(I think that's the right terminology) so I changed it to IDE in the BIOS. I was wondering a couple things.

What hardware vendor do you guys use so I can try to get the SATA drivers for XP?

Also, what is the best way to partition the remaining space for Ubuntu. I ahve about 180 GB for Ubuntu and people often talk about having a seperate partition for the /home. Do you recommend a separate partition for boot as well? Any recommendations are most appreciated.

Thanks,
Dave

---

### Post by thomasaaron on 2009-02-06
Windows' sata drivers are generic. There are some tutorials out there that explain how to acquire and install them.Here's one that I've given out a couple of times...

[http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C0](http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C0)

Here's how we recommend dual-booting (and it includes info on partitioning as well)...
[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

### Post by chez17 on 2009-02-06
Tom,

I don't know if you know anything about this, but I installed XP and it doesn't recognize a lot of the hardware. It doesn't have any networking, it doesn't recognize that the laptop is plugged in, just that the battery is 100%. Stuff like that. As I said, the only thing in the BIOS I changed was I switched the SATA to IDE and the OS version from Vista to XP. Any thoughts?

---

### Post by chez17 on 2009-02-06
OK, I may be in over my head here. But does a 250 GB SATA II HD mean tha tI have 2 250 GB drives? I am trying to partition my comp laptop and it seems it has 2 drives. I have a pangolin model: panp4n installing 64 bit Ibex.

---

### Post by thomasaaron on 2009-02-06
Hi, Dave.

If memory serves, you have a PanP4n, right?

You can download all of the necessary windows drivers for the PanP4i and the PanP4n here...

[http://knowledge76.com/index.php/Panp4](http://knowledge76.com/index.php/Panp4)

So, you'll need the nVidia driver, not the Intel driver.

---

### Post by MorphWVUtuba on 2009-02-06
No, that's just the spec for the type of drive.  SATA II means it supports 3.0Gbs, where version 1 only supported 1.5Gbs.

Here's where you can get your drivers:
[http://knowledge76.com/index.php/Panp4]("http://knowledge76.com/index.php/Panp4")

You may need to download them to a flash drive from another machine, as I did, but as long as Windows boots you're golden.

---

### Post by thomasaaron on 2009-02-06
> I am trying to partition my comp laptop and it seems it has 2 drives

I *think* you are seeing different partitions on the same drive.

---

