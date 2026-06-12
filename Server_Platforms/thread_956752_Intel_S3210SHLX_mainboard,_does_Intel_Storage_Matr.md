---
title: "Intel S3210SHLX mainboard, does Intel Storage Matrix work with Ubuntu?"
date: 2008-10-23
forum: Server Platforms
---

### Post by jarthurs on 2008-10-23
I'm about to build myself a new server to replace the electricity hogging old Proliant box. I've decided that the S3210SHLX looks like it ticks all the boxes, but the six onboard SATA ports are covered by an Intel Storage Matrix controller.

Can this be managed under Ubuntu? Or would it be possible to set this up in the BIOS and have it presented to the OS as a regular device?

I'm hoping to set this up with 4 x 1Tb drives and virtualize all my existing servers onto the one box.

Regards,
Jason.

---

### Post by fjgaude on 2008-10-23
I think it would be better to create an array with **mdadm**, instead of using the BIOS raid program, which then would require you to use **dmraid** to mount the array while in Ubuntu. Just my opinion.

---

### Post by cariboo on 2008-10-23
Fakeraid should work quite well for your application. THere is a howto here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It took me about ten minutes to set it up.

Jim

---

### Post by fjgaude on 2008-10-23
**dmraid** doesn't work with but raid0 and raid1... so with four drives we will have to try for raid10... I've not used dmraid for years so I can't say if it works with raid10. It doesn't with raid5 as of last month. It simply can't handle parity generation and recovery.

---

### Post by Krupski on 2008-10-23
> **fjgaude said:**
> I think it would be better to create an array with **mdadm**, instead of using the BIOS raid program, which then would require you to use **dmraid** to mount the array while in Ubuntu. Just my opinion.

Big +1 on that. My file server boxes are Intel motherboard based and they have RAID built in - but I use MDADM instead.

It works flawlessly for me.

My 2 cents...

-- Roger

---

### Post by Krupski on 2008-10-23
> **fjgaude said:**
> **dmraid** doesn't work with but raid0 and raid1... so with four drives we will have to try for raid10... I've not used dmraid for years so I can't say if it works with raid10. It doesn't with raid5 as of last month. It simply can't handle parity generation and recovery.

By the way, with RAID 1 (mirroring), normally if the "preferred minor" drive fails, the system will not boot. The solution is to use GRUB fallback to boot from the other RAID member if the preferred drive fails.

---

### Post by jarthurs on 2008-10-25
> **Krupski said:**
> Big +1 on that. My file server boxes are Intel motherboard based and they have RAID built in - but I use MDADM instead.

It works flawlessly for me.

My 2 cents...

-- Roger

I'm interested to see that people are so trusting of software based RAID. What are the overheads involved, specifically I'm looking a RAID5 redundancy. I asked a similar question a couple of years back and it came back pretty resoundingly in favour of hardware solutions.

Regards,
Jason.

---

### Post by fjgaude on 2008-10-25
Well, with modern multi-core, fast CPUs and memore, the overhead is not great... I don't notice the load with my system... others may have other views. Just remember, cards that have their own CPUs still use the mainboard system bus, PCI-X or PCI-Express to provide a path. It's one more failure path to add a complex raid card to the system.

Now I'm first admit that hardware is usually easily to use than mdadm software raid... there's lots to learn to cover all situations.

---

