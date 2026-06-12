---
title: "Preferable Partition Setup for a 16GB SSD?"
date: 2010-04-27
forum: The Cafe
---

### Post by user1397 on 2010-04-27
So I think I'm about to install arch on my netbook which has a 16GB SSD, I am just wondering what people recommend for partition setup, such as should I have a /boot partition, amount of swap (if any, I have 1GB ram), whether it is pointless or not to have a /home, etc.

Opinions?

Only reason I'm posting in the cafe is because it's not something I don't know how to do, it's just that I don't know the best way to do it, hence the need for advice.

---

### Post by earthpigg on 2010-04-27
in your case, i'd just do one large partition.

1) you are using arch, meaning you won't be re-installing every 6 months.
2) your /home is pretty much guaranteed to never exceed 14gb. not that large. if you do need to re-install, it wont be a big deal to copy your entire /home to somewhere else.

---

### Post by user1397 on 2010-04-27
> **earthpigg said:**
> in your case, i'd just do one large partition.

1) you are using arch, meaning you won't be re-installing every 6 months.
2) your /home is pretty much guaranteed to never exceed 14gb. not that large. if you do need to re-install, it wont be a big deal to copy your entire /home to somewhere else.
Good points.  What about a swap partition, and if yes, how large should I make it?

---

### Post by NovaAesa on 2010-04-27
Size of swap depends on what activities you plan to do on the netbook. If you are just browsing/programming/taking notes (which is what I use my netbook for), then having no swap should be fine. As long as you don't plan on using hibernate that is.

---

### Post by earthpigg on 2010-04-28
i have 1gb of ram and a 500mb swap on my netbook. i dont think ive ever actually used any of the swap space. 

i suppose it couldnt hurt to keep a small swap partition, just in case... but i wouldnt call it 'needed', except for those installing ubuntu-desktop or it's equivalent on other distros. which you probably wont be.

i bet on arch you would probably be able to get away with full gnome and not have a swap.

---

### Post by snowpine on 2010-04-28
+1 for a single 16gb ext4 partition.

---

