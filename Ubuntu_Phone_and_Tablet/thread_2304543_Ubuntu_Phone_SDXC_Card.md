---
title: "Ubuntu Phone SDXC Card"
date: 2015-11-27
forum: Ubuntu Phone and Tablet
---

### Post by milind727 on 2015-11-27
Using an Aquaris 4.5, is there a way to get it to recognize a 64 or 128 gb SDXC card or is it forever limited to the 32gb limit?

---

### Post by kurt18947 on 2015-11-28
SDXC cards are by default formatted to EXfat. You probably need to install exFAT tools. A search in Synaptic or Ubuntu Software Center should find what you need.

---

### Post by milind727 on 2015-11-29
I didn't find anything in the software center...and I don't have the slightest idea how to do a package manager search on the phone...?

---

### Post by kurt18947 on 2015-11-30
> **milind727 said:**
> I didn't find anything in the software center...and I don't have the slightest idea how to do a package manager search on the phone...?

I forgot about the phone part, sorry.  The two packages that show up in Synaptic when searching for 'exfat' are exfat-fuse and exfat-utils. I don't know if those are appropriate for your purposes.

---

### Post by CybaCowboy on 2016-02-19
If I am not mistaken, the bq Aquaris E4.5 Ubuntu Edition is a re-purposed [Aquaris E4]("http://store.bq.com/en/aquaris-e4")... And the Aquaris E4 only supports up to 32GB also, which means that it's probably a *hardware* limitation and thus unlikely you will ever be able to use more than 32GB in your Aquaris E4.5 Ubuntu Edition.

---

