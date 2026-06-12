---
title: "alternate-CD, kernelmodul rtl8187"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Lebowski1 on 2012-04-02
Hi,
i'm trying to install 12.04 using the alternate-CD. Everything works fie, also my wlan-card is configured right after installation.
But during Installation I can't use the wlan-card. lsusb shows me an rtl8187. There is an kernelmodul (rtl8187) for this card, but its not included, so I can't load it. 
But I've to use wlan during installation. So how can I get them to work?

Thanks

---

### Post by plucky on 2012-04-02
> **Lebowski1 said:**
> Hi,
i'm trying to install 12.04 using the alternate-CD. Everything works fie, also my wlan-card is configured right after installation.
But during Installation I can't use the wlan-card. lsusb shows me an rtl8187. There is an kernelmodul (rtl8187) for this card, but its not included, so I can't load it. 
**But I've to use wlan during installation.** So how can I get them to work?

Thanks

You do not have to have a network connection to do the installation.

If you want a network connection,I always try to use a wired connection as it is easier for the install CDs to have the drivers for a wired connection.

Then after the installation is complete,you can use the wired connection to download the drivers for the wireless connection.

Also even when my wireless connections work out of the box,the installation CDs don't seem to like WPA2 connections even though they work after the installation.

Just my observations with installing Ubuntu.

Good Luck

---

### Post by Lebowski1 on 2012-04-02
Thanks for reply

I've 54 laptops to install ..., using mini.iso + preseed. So it's easier for me to use wlan. Wire them all is a lot of work
It is working with 10.04. Is there a chance for 12.04

---

### Post by cariboo on 2012-04-02
> **Lebowski1 said:**
> Thanks for reply

I've 54 laptops to install ..., using mini.iso + preseed. So it's easier for me to use wlan. Wire them all is a lot of work
It is working with 10.04. Is there a chance for 12.04

I'd suggest you create a bug report about the problem. Your's is a bit of a corner case, so problems like you are running into, don't show up during iso testing.

---

