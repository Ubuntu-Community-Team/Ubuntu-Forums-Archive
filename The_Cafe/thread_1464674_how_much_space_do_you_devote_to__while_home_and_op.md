---
title: "how much space do you devote to / while /home and /opt are seperate from it."
date: 2010-04-28
forum: The Cafe
---

### Post by legolas_w on 2010-04-28
Hi

I want to repartition my hard disk and I am wondering how much space I should allocate for the / while my /opt and /home has their own paritions.

PS: is it better to use EXT4 for / or EXT3 considering the number and size of the files living on the / mountpoint.


Thanks.

---

### Post by Bachstelze on 2010-04-28
4G is enough for everyday desktop use. Make it bigger (6, 8, 10) if you install a lot of packages. More than 10 is most probably overkill.

---

### Post by undecim on 2010-04-28
My / is 10 GB with a separate /home/ and I'm only using 3.7 GB so far with a fresh install of Lucid.

I had been using about 8GB before the fresh install, because I was testing out various DEs. I would recommend 5 GB, unless you want to install a lot of packages.

Also, use ext4, not ext3

---

### Post by Penguin Guy on 2010-04-28
Use ext4, it's pretty stable now. I use 3.9GB/9.7GB on my root partition. However, unless you have a specific plan, I would advise against partitioning.

---

### Post by ajgreeny on 2010-04-28
> **Penguin Guy said:**
> Use ext4, it's pretty stable now. I use 3.9GB/9.7GB on my root partition. [COLOR=Red]However, unless you have a specific plan, I would advise against partitioning.[/COLOR]
What do you mean by that comment?  I use a separate /home and I would suggest that it is definitely worth doing; it makes any re-installation or upgrade of distro version so much easier.

---

### Post by NCLI on 2010-04-28
I give it 20 GB, but I do install A LOT of stuff :D

---

### Post by cariboo on 2010-04-28
For desktops 10Gb for / and the rest for /home, no Windows partitions. For servers 20Gb for / 10Gb for /home and the rest for shareable storage.

---

### Post by PhoHammer on 2010-04-28
> **ajgreeny said:**
> What do you mean by that comment?  I use a separate /home and I would suggest that it is definitely worth doing; it makes any re-installation or upgrade of distro version so much easier.

+1

I'm using 2.99GiB/18.7GiB of my / partition. My install is pretty fresh and I haven't even added all the packages I want, so i would go with at least 6 GB or so.

---

### Post by swoll1980 on 2010-04-28
I do 10GB / to be on the safe side.

---

### Post by eriktheblu on 2010-04-28
I'm a bit on the excessive side. I've got 25GB in the / partition. I hardly use any of it (maybe 8 GB), but I have plenty of space (250 and 500 GB HDDs) and don't want to mess with it down the road.

All my partitions (excluding swap) are EXT4.

It's often considered a wise practice to leave unformatted space between partitions to allow for expansion.

---

### Post by K.Mandla on 2010-04-28
64Mb for /boot, 128Mb for swap, 2-4Gb for /, the rest is /home.

---

### Post by Xbehave on 2010-04-28
5-6 GB for /

or

3-5  for /usr
1-1½ for /var
½ for /
¼ for /boot

---

### Post by legolas_w on 2010-04-29
Thank you all for sharing comments here.

I have 37 GB / partition right now and 14 GB is full. I will repartition the hard disk and give it 20 GB.

I will give all 17 GB to home parition to extend it.

Thanks.

---

