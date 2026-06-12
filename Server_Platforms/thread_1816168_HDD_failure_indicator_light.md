---
title: "HDD failure indicator light?"
date: 2011-08-01
forum: Server Platforms
---

### Post by joeinbend on 2011-08-01
Hey guys,
I'm wondering if there's a way to trigger the "failed" light/LED for a hard disk, in a RAID array, on standard whitebox hardware? I know in the enterprise world, NAS's and SAN's have this capability, I'm wondering if there's a way either smartmontools or mdadm have the ability to trigger this. 

In my setup, I'm using a pair of hot-swap chassis ([link here]("http://www.amazon.com/Thermaltake-Backplane-Removable-3-5-Inches-RC3400101A/dp/tech-data/B004G8QES4/ref=de_a_smtd")) Each drive bay has a red and green LED; green is normal, red is activity. It would be awesome if I could trigger it to red on a disk failure condition (either determined by mdadm, or 'eminent falure' via smartmontools)

thanks!

---

