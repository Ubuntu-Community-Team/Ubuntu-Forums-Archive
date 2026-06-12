---
title: "Small Complaint About UNR"
date: 2010-02-24
forum: Testimonials &amp; Experiences
---

### Post by uRock on 2010-02-24
There seems to be only one image we can use for doing an install to a Netbook, so why does the installer not offer the ability to install on an encrypted LVM? Having an encrypted disk on something this portable is very important, IMO.

I am sure that mostly every model of Netbook has the same wireless NIC, so why does it seem to have an incompatible driver? I have noticed that either Suse or Solaris (open versions) have another driver they are looking to use and I hope that the Lucid release is going to offer a better driver, too. The current driver is the Ath9k.

This is not a rant nor flame. I am hoping that by some odd chance the right dev might see this.

Those two issues aside, I love the look and feel of UNR.

---

### Post by uRock on 2010-02-24
I did find the fix for the wireless [here]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks"), but it would be nice if the next release has the fix incorporated into it.

If your are looking to fix this enter the following code in a terminal. ```
sudo apt-get install linux-backports-modules-karmic
```

---

### Post by cariboo on 2010-02-24
Why would you need **L**ogical **V**olume **M**anagement on a net book with a single hard drive? The UNR installer does give you the option to encrypt your home directory during the installation process.

My Compaq mini 110 has a Broadcom 4312 chipset. The driver was available through jockey-gtk

---

### Post by snowpine on 2010-02-24
You can use the Alternate Install CD to create an encrypted LVM, if you feel it is important to you. Just choose a CLI-only minimal install, then:

```
sudo apt-get install ubuntu-netbook-remix
```

---

### Post by uRock on 2010-02-24
> **cariboo907 said:**
> Why would you need **L**ogical **V**olume **M**anagement on a net book with a single hard drive?

That is the option given in the alternate installer. It is what I use on my desktop, too. Snowpine mentioned a away that I didn't know of. I will give that a try when Lucid comes out.

Thanx to both of you for the input.

---

