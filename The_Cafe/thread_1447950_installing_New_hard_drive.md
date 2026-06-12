---
title: "installing New hard drive?"
date: 2010-04-06
forum: The Cafe
---

### Post by soryu on 2010-04-06
any tips on installing a new hard drive?
i've had this one for 10yrs.time for an upgrade.
it's a IDE interface.

---

### Post by haddog on 2010-04-06
> **soryu said:**
> any tips on installing a new hard drive?
i've had this one for 10yrs.time for an upgrade.
it's a IDE interface.

Clone the old drive to the new one with clonezilla. Has always worked for me without fail.

---

### Post by haddog on 2010-04-06
CClone old drive to new one with clonezilla.

---

### Post by handy on 2010-04-06
What the other two posters said.

Clonezilla is great, download it & burn the bootable CD.

---

### Post by Grenage on 2010-04-06
*Clonezilla* or *dd* via a liveCD.  I tend to use *dd* myself, but *Clonezilla* is a lot simpler.

---

### Post by Paqman on 2010-04-06
> **soryu said:**
> time for an upgrade.

Time for an SSD then (assuming you've got a SATA port on the board)

---

### Post by Khakilang on 2010-04-06
I think the IDE interface hard disk is still available but its more costly due to low demand. But if you can get a PCI SATA interface adapter to plug into your computer PCI slot than you can get a SATA hard disk. The performance is much better that IDE.

---

### Post by handy on 2010-04-06
> **Grenage said:**
> *Clonezilla* or *dd* via a liveCD.  I tend to use *dd* myself, but *Clonezilla* is a lot simpler.

Clonezilla uses dd for certain file systems, & as you say, it is much simpler which makes it a lot harder to make a potentially costly mistake.

---

### Post by Paqman on 2010-04-06
> **Koh Kook Loon said:**
> The performance is much better that IDE.

Actually, for traditional magnetic hard drives performance is the same between IDE and SATA. You need a seriously fast drive to exceed the speed of the IDE interface. SSDs will do it, which is why they're all SATA.

---

### Post by The Real Dave on 2010-04-06
If your mobo doesn't have a SATA interface, which it probably doesn't, get yourself a SATA PCI card, a cheap one will do fine, rather then buying a large IDE drive. 

IDE drives are more expensive per GB than SATA, and SATA drives come in much larger capacities. :) 

And clone the old one just in case. Clonezilla is the best thing out there :)

---

### Post by haddog on 2010-04-06
Agreed on just getting a SATA PCI card if your computer doesn't have a SATA interface. I have an old Dell Dimension 2350 that I put a SATA PCI card in. Put Ubuntu Server 10.04 on it. 

Now has a 300 Gig SATA hard drive and an 80 gig IDE. Works great. Backed up the Server to a 1TB usb drive using Clonezilla LiveCD.

Tutorial on using clonezilla:

[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by handy on 2010-04-06
> **The Real Dave said:**
> If your mobo doesn't have a SATA interface, which it probably doesn't, get yourself a SATA PCI card, a cheap one will do fine, rather then buying a large IDE drive. 

IDE drives are more expensive per GB than SATA, and SATA drives come in much larger capacities. :) 

And clone the old one just in case. Clonezilla is the best thing out there :)

You don't need a SATA card, you can buy a cheap adapter that plugs in between the SATA drive & the IDE cable, I use these myself, & they work fine.

---

### Post by thekanuk on 2010-04-06
WoW!

This thread just helped me with my next question... ...no need to ask or search now, lol.

You guys are a ton of help!  :)

---

### Post by haddog on 2010-04-07
> **handy said:**
> You don't need a SATA card, you can buy a cheap adapter that plugs in between the SATA drive & the IDE cable, I use these myself, & they work fine.

Haven't seen one of those cheap adapters. Where do you purchase from?

---

### Post by CharlesA on 2010-04-07
> **haddog said:**
> Haven't seen one of those cheap adapters. Where do you purchase from?

[Generic crap ftw!]("http://www.amazon.com/gp/product/B002Y2NI4M/ref=pd_lpo_k2_dp_sr_1?pf_rd_p=486539851&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=B000ZLM9IA&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=03VGAK7M812T7BHSEKNQ")

---

### Post by sandyd on 2010-04-08
grab a raid card and setup raid0 or raid1. oh yeah!!

---

### Post by Roasted on 2010-04-08
> **haddog said:**
> Clone the old drive to the new one with clonezilla. Has always worked for me without fail.

I have a question regarding this that I assume the original poster might benefit from knowing...

Whenever I've used Clonezilla, it's always saved the image as a package, which indicated to me I need to upload the image from drive A to an external, then re-deploy it to drive B from my external.

In his case, no external is in the mix. It's just old drive (A) and new drive (B). Is there a straight up DD function clonezilla has, which can take away from the need of saving/re-deploying the "package" (image) and do it all in 1 solid shot? 

If so, would the user need to use GParted afterwards to expand the partition to utilize the new space on the new drive?

---

### Post by CharlesA on 2010-04-08
I don't know if that's possible. I usually just image a machine to a network share or local device and then go from there.

---

