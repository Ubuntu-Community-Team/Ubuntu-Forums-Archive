---
title: "[SOLVED] Setup Server to sleep when inactive?"
date: 2008-09-11
forum: Server Platforms
---

### Post by Krupski on 2008-09-11
Hi,

I'm running a Network Attached Storage (NAS) box built with Ubuntu Server 64 bit. It's got modern hardware (Intel DG33BU board, 8GB ram, Intel E6700 Core 2 Duo CPU, 4GB CF card for the OS and four 1TB hard drives in a RAID 0+1 configuration).

What I would like to do is have the whole computer go into some kind of a "sleep mode" after a timeout period, but wake up and run if there's any network access attempted.

Having to wait a few seconds for hard drives to spin up is NOT a problem.

The box has no keyboard or monitor... only a power cord and a network cable.

Is there a simple way to set this up?

Lastly, the solution needs to be CLI only... I have no GUI installed and I administer the box remotely via SSH anyway.

Thanks in advance!

-- Roger

---

### Post by Vivaldi Gloria on 2008-09-11
You can try to use hdparm and /etc/hdparm.conf to spin down your disks. For example put something like

```
/dev/sda {
spindown_time = 240
}  
```

in your hdparm.conf. See

```
man hdparm
man hdparm.conf
```

Also search "hdparm" or "disk spindown" in this forum. I never used this with raid so I'm not sure how it'd work. With non-raid disks it works very well.

---

### Post by Krupski on 2008-09-11
> **Vivaldi Gloria said:**
> You can try to use hdparm and /etc/hdparm.conf to spin down your disks. For example put something like

```
/dev/sda {
spindown_time = 240
}  
```

in your hdparm.conf. See

```
man hdparm
man hdparm.conf
```

Also search "hdparm" or "disk spindown" in this forum. I never used this with raid so I'm not sure how it'd work. With non-raid disks it works very well.

Interesting. Spinning down the hard drives after a period of inactivity would be nice. I kinda also wanted to power down the whole motherboard a little if that was possible.

My main concern is, however, to save wear and tear on the hard drives. No need to have them spin tens of hours a day and not be accessed.

I'll look into the 'hdparm' stuff. Thanks!

-- Roger

---

### Post by windependence on 2008-09-11
WHY does everyone want to do this? You are actually putting MORE wear and tear on your drives by shutting them down and spinning them up again. This is the worst thing you can do to your drives. 

If you wanna make your drives last like the manuacturer says (300,000 hrs MTBF) keep them COOL above all else. Heat is the destroyer of all things electronic. Do you know how long your drives should REALLY last? In actuallity, they should be obsolete before they fry. I have some working drives here that are 10 years old.

-Tim

---

### Post by Krupski on 2008-09-11
> **windependence said:**
> WHY does everyone want to do this? You are actually putting MORE wear and tear on your drives by shutting them down and spinning them up again. This is the worst thing you can do to your drives. 

If you wanna make your drives last like the manuacturer says (300,000 hrs MTBF) keep them COOL above all else. Heat is the destroyer of all things electronic. Do you know how long your drives should REALLY last? In actuallity, they should be obsolete before they fry. I have some working drives here that are 10 years old.

-Tim

I've read that several other places too (i.e. don't spin down the drives).

I do keep them cool... I actually have a fan positioned to draw air in and over the drive bodies... they are barely warmer than ambient.

From all I've read... plus your post... I think I'll abandon the idea of spinning down the drives.

It SEEMED like a good idea at the time... :lolflag:

---

