---
title: "Upgrade Stock Ubuntu 12.04 LTS to Ubuntu CE?"
date: 2013-05-10
forum: Ubuntu Christian Edition
---

### Post by parkernathan on 2013-05-10
I'm trying to install Ubuntu CE (64 Bit) on a piece of hardware I just built, and I've been having issues loading the installer. However, stock Ubuntu 12.04 LTS (64 Bit) is installing on it OK.

My question is, after Ubuntu 12.04 LTS finishes installing, can I do an "upgrade" to Ubuntu CE (64 Bit) without booting and performing a clean install? Is there a quick and easy way to install it over 12.04 LTS or simply perform an upgrade to the rest of Ubuntu CE's software?

I know this is late posting it. I've been up tip 3 AM CST trying to get this machine built and Ubuntu CE installed on it. :-)

Thanks!

---

### Post by 2F4U on 2013-05-10
I don't think so. While you will most likely find all programs in the Ubuntu repositories, you would have to install them "by hand". Since Ubuntu CE is based on stock Ubuntu, there is no real reason why it shouldn't install on your machine when Ubuntu does. Is it possible that the download is corrupt or something bad happened when you created the CD or USB stick? What were the issues?

---

### Post by parkernathan on 2013-05-10
> **2F4U said:**
> I don't think so. While you will most likely find all programs in the Ubuntu repositories, you would have to install them "by hand". Since Ubuntu CE is based on stock Ubuntu, there is no real reason why it shouldn't install on your machine when Ubuntu does. Is it possible that the download is corrupt or something bad happened when you created the CD or USB stick? What were the issues?

I tried re-downloading it and re-creating the USB stick through the app listed on Ubuntu's website, and it was still a no go.

What happens on the 64 Bit version is I select to install Ubuntu, then my system goes to a black screen and never goes any further.

On Ubuntu CE and stock Ubuntu 32 Bit, it seems to start loading the Ubuntu boot screen (after selecting to install Ubuntu), but then it again goes to a black screen and doesn't go any further.

Ubuntu stock 64 Bit installed, but now when I boot it, it again shows the Ubuntu boot screen and goes to a black screen afterwards.

Here's my hardware setup:

VIA Artigo A1250 with Via QuadCore Isaiah and VX11H Chipset.
Samsung 500GB 840 Series SSD
Crucial 8GB RAM SODIMM.

BIOS recognizes the SSD, RAM, and was set correctly to boot from the USB stick first.

---

### Post by parkernathan on 2013-05-10
I think I figured out what's up, and I can probably install a working copy of Ubuntu CE now. Problem is I'm using HDMI without all the proper drivers. I need the HDMI video drivers before I can successfully use my monitor over HDMI.

Problem now is, my monitor only works over HDMI or DVI, and my computer only works over HDMI or VGA.

I ordered a DVI to VGA cable (had to get dual-link DVI-D since that's what my monitor supports). I hope it works. If not, I guess I'll have to borrow a VGA monitor up at my other office. :-)

---

### Post by parkernathan on 2013-05-16
Got UCE working now. It was definitely the monitor issue.

---

