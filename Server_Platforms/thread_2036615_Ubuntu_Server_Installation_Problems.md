---
title: "Ubuntu Server Installation Problems"
date: 2012-08-02
forum: Server Platforms
---

### Post by jonesyp on 2012-08-02
Hello,

I’m trying to Ubuntu Server 12.04 on a couple of Desktop PCs with AMD X2 64Bit Processors.  As soon as it gets to the hardware identification stage, the installation hangs.

How would I make the installation more verbose so I can start looking for any error messages?

Many thanks

Peter Jones

---

### Post by LHammonds on 2012-08-02
> **jonesyp said:**
> Hello,

I’m trying to Ubuntu Server 12.04 on a couple of Desktop PCs with AMD X2 64Bit Processors.  As soon as it gets to the hardware identification stage, the installation hangs.

How would I make the installation more verbose so I can start looking for any error messages?

Many thanks

Peter JonesI assume you are trying to install the 64-bit version of Ubuntu Server 12.04 LTS?

Depending on the hardware, it might be a hardware support issue.  Try the [64-bit alternate CD]("http://releases.ubuntu.com/12.04/")

---

### Post by jonesyp on 2012-08-02
Sorry, I should have mentioned that I tried the 32Bit version as well with the same issue.

Best wishes

---

### Post by LHammonds on 2012-08-02
You should still try the alternative CD.

Starting with 12.04, they are no longer supporting old hardware methods.  I forget the details but those who have problems installing the latest versions should try the alternate CDs to see if that resolves the problem.

---

### Post by jonesyp on 2012-08-02
Thanks, I will try this tonight.

I have just tried the Desktop version of Ubuntu 12.04 and this installs fine without problems.

Peter

---

### Post by jonesyp on 2012-08-02
Hi,

I have found the issue (I could use the standard install CD, no need to the alternate one), but I do not know how to solve it.

I have a Edimax EW-7128g Wireless card in my machine, which I think uses the standard Ralink chip.

[http://www.edimax.com/en/produce_detail.php?pd_id=1&pl1_id=1&pl2_id=44](http://www.edimax.com/en/produce_detail.php?pd_id=1&pl1_id=1&pl2_id=44)

If I take the card out the install works fine and it looks for the Ethernet card which is present.

I was hoping to use the wifi card.  Is there a work around?

I can install the desktop version of Ubuntu 12.04 and it picks up the wireless fine.

Many thanks


Thanks

Peter Jones

---

### Post by jonesyp on 2012-08-02
Just to confirm having checked that my wireless card uses Ralink RT2500 chipsets

Thanks

Peter Jones

---

### Post by jonesyp on 2012-08-04
Any help on this would be much appreciated.

Best wishes

Peter Jones

---

### Post by LHammonds on 2012-08-05
So you have a working and fully installed server if you leave the wireless card out during install...does it still work (boot up) if you plug in the card after setup?

If so, it may just be a matter of finding the right drivers.

If not, you might want to take a shot with the alternate CD.

LHammonds

---

