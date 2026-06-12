---
title: "Thoughts on RAID 1+0 (10) Server Build"
date: 2009-01-23
forum: Server Platforms
---

### Post by R.Bucky on 2009-01-23
I have been hosting my web site for about 2 years now. I am ready to build a more substantial box now. I am fairly new to the hardware arena, however here is what I have come up with:

RAID 10, 4 x WD 250GB, 4 x 1GB DDR3 RAM, Biostar TA780G M2+ motherboard, AMD 64x2 5000+ 2.6GHz. 

My web traffic is insignificant (50-100 original hits/day), but I also operate a streaming media server with a half dozen users. The setup is overkill now, but I am looking for a project that would be around a $1000. 

Thoughts or sugestions?

---

### Post by windependence on 2009-01-24
Mark, 

I have several boxes that I have built from scratch for servers. They are all rack mount server class hardware and running fine. The problem is now I can buy two commercial boxes for the price it cost me to build the big server (dual quad core Opteron, 16GB RAM). Dell has some great stuff on their outlet site either scratch and dent or refurb and they are like new with warranty. We just bought a quad core box with drives and beaucoup RAM for $1200. It's a 1950 box and has 4 GB NICs, and a terabyte of storage on a Perc6i built in RAID controller.

The only thing I would change in your config would be to run RAID 5 (3 drives) and use a server class board like Tyan, Supermicro, Intel, or even Asus. RAID 5 would be better for your streaming because of the additional spindles.

-Tim

---

### Post by R.Bucky on 2009-01-24
I appreciate the input. It seems like there is much back and forth between RAID5 and 10; reliability versus use (e.g. large amounts of data being written versus not) is what it seems to come back to. 

Another feature that would be nice to have would include a hot swap. That seems like another dog all together.

Again - thank you for the input.

~Mar

---

