---
title: "Replacing laptop HDD with SSD"
date: 2014-10-12
forum: The Cafe
---

### Post by user1397 on 2014-10-12
So I just bought [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834314539") laptop and I was thinking of replacing the hard drive it came with for an SSD.  I was thinking of buying one like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820171740") and I am going to use [this]("http://www.myfixguide.com/manual/acer-aspire-e5-571g-disassembly/") guide to disassemble the laptop carefully.

My first question is, isn't the SSD a lot smaller than the HDD? Won't there be a lot of space for it to move around in there?  How can I secure it?  Or would it be secure in the hard drive assembly (do I take apart the hard drive assembly as well or what?)

Also, if I want to dual-boot windows and ubuntu on the new SSD, do I have to do anything special after physically installing the SSD?  My only copy of windows is the recovery backup I put onto a USB flash drive through the acer backup software.  Will that not install onto the new SSD?  

Thank you in advance.

---

### Post by Dennis N on 2014-10-12
It is the same size as a standard 2 1/2 " laptop drive. Designed to fit in the same place with the same screws and screw locations. Nothing special needs to be done on installation. It is recommended to use TRIM every now and then (google "Trim on Ubuntu").

---

### Post by mips on 2014-10-13
You can also get a caddy to go in the dvd slot to relocate your existing hdd to, this way you can have a ssd+hdd in the same laptop.

---

### Post by frank75 on 2014-10-15
Ditto, should fit right in without any issues.  Make sure you turn off cache in your browser to stop extra writes to the SSD and do a "sudo fstrim -v /" every week or so to free up space and you should be good to go.  I've installed SSD's on my two laptops(Dell D420, little 1.8" ZIF and Dell 630, standard 2.5" and on my wife's Acer Aspire ZG5 with a 1.8" ZIF, had to pull it totally apart to get to the drive) and it really speeds up boot time.  Prices have come down so that now us "normal" folk can afford one.   Just take your time doing the install and good luck.

---

### Post by WinEunuchs2Unix on 2014-10-16
Boot times are a consideration because it takes 30 seconds and a SSD will reduce it to 10 seconds.  OTOH a working laptop is never booted but is put to sleep and woken up in 1 second.

If I had your 4 GB of RAM and could expand to 16GB I would do that.  Then I would get a RAM-DISK cache setup.  The entire UBUNTU would fit into the RAM-DISK.  A HDD is 100 MB per second, a SDD is 200 MB but RAM is 1600 MB.

This is all purely idle speculation and day dreaming under the influence of 3 beers and a hard day at work.

---

### Post by user1397 on 2014-10-17
> **Dennis N said:**
> It is the same size as a standard 2 1/2 " laptop drive. Designed to fit in the same place with the same screws and screw locations. Nothing special needs to be done on installation. It is recommended to use TRIM every now and then (google "Trim on Ubuntu").Ah I see, thank you.

> **mips said:**
> You can also get a caddy to go in the dvd slot to relocate your existing hdd to, this way you can have a ssd+hdd in the same laptop.Awesome, good to know, I might do this actually.

> **frank75 said:**
> Ditto, should fit right in without any issues.  Make sure you turn off cache in your browser to stop extra writes to the SSD and do a "sudo fstrim -v /" every week or so to free up space and you should be good to go.  I've installed SSD's on my two laptops(Dell D420, little 1.8" ZIF and Dell 630, standard 2.5" and on my wife's Acer Aspire ZG5 with a 1.8" ZIF, had to pull it totally apart to get to the drive) and it really speeds up boot time.  Prices have come down so that now us "normal" folk can afford one.   Just take your time doing the install and good luck.Thank you, yes I was looking up guides on how to take my laptop apart and it definitely isn't as easy as I thought it would be, but seems doable.

> **WinEunuchs2Unix said:**
> Boot times are a consideration because it takes 30 seconds and a SSD will reduce it to 10 seconds.  OTOH a working laptop is never booted but is put to sleep and woken up in 1 second.

If I had your 4 GB of RAM and could expand to 16GB I would do that.  Then I would get a RAM-DISK cache setup.  The entire UBUNTU would fit into the RAM-DISK.  A HDD is 100 MB per second, a SDD is 200 MB but RAM is 1600 MB.

This is all purely idle speculation and day dreaming under the influence of 3 beers and a hard day at work.Haha, daydreaming is always a good thing.  I might expand the RAM to 8GB if 4 doesn't cut it, but for now it's been holding up.  A ram-disk setup would be very sweet though.

---

### Post by WinEunuchs2Unix on 2014-10-17
> **ubuntuman001 said:**
> Ah I see, thank you.

Awesome, good to know, I might do this actually.

Thank you, yes I was looking up guides on how to take my laptop apart and it definitely isn't as easy as I thought it would be, but seems doable.

Haha, daydreaming is always a good thing.  I might expand the RAM to 8GB if 4 doesn't cut it, but for now it's been holding up.  A ram-disk setup would be very sweet though.

The used Dell I bought has factory installed 8 GB which is the max.  The entire machine is maxed out in fact.  Some have said 16 GB is possible although not supported and it is on my long term to-do list.  The 32GB mSATA III SSD already inside is the current to-do.  Most have it turned off but I turned on 19 GB to accelerate the 500 GB HDD under Windows (downgraded from factory 8.0 to Win 7 ultimate like most users of 2012 did).  Tonight's project is to use the other 12 GB on the SDD to accelerate (read cache) a 240 GB partition for Ubuntu.

It's all quite technical and if it works I hope to post a 5 page write-up on how it's done because thousands of pages of misleading information is on google for the 10 million owners (best guesstimate) of this genre of modern laptop.

Oh yes your original question no problem installing a regular SSD into a HDD slot.  This latptop has two HDD bays and one optical bay that could take an HDD. The mSATA SSD plugs into a little chip port (I haven't seen it yet) that resembles more of a PCI-e Mini Wi-Fi card (I think).

Anyway have fun and don't let a few trials and tribulations set you back too much.

---

### Post by glyczak on 2014-10-18
After replacing the HDD in my laptop to a SSD my boot time dropped to 6 seconds.

---

