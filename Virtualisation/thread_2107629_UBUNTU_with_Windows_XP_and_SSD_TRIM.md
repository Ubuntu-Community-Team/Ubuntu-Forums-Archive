---
title: "UBUNTU with Windows XP and SSD TRIM"
date: 2013-01-22
forum: Virtualisation
---

### Post by broadway on 2013-01-22
My existing PC is Windows XP and is very slow. I am thinking of replacing it with one containing SSD. Since I have a lot of data/applications that are for XP I expect some of them would not run under Windows 7/8. 

I assume I can install Windows XP in a virtual box and run it under UBUNTU without problems. The increase in memory and CPU capability should improve load times. To reduce it further I could install it on SSD. As Windows XP does not handle TRIM, but UBUNTU does will TRIM be enable with this configuration?

---

### Post by SlugSlug on 2013-01-22
Not really needed as the XP VM would be a single file on the SSD.

It would get trimmed (if trim is enabled on the host) if you decided to shrink the VM volume.

---

### Post by broadway on 2013-01-23
I have done a bit more googling and it looks lide it would be better to run it on an HDD.

---

### Post by SlugSlug on 2013-01-23
Why?

---

