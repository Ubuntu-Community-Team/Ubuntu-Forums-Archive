---
title: "Best filesystem to use?"
date: 2008-12-05
forum: Server Platforms
---

### Post by halfelite on 2008-12-05
Well after running ext3 for a few weeks and going to expand my array size I realized its not an easy option since you have to drop the journal turn it into ext2 then expand. Is there another option i can use. This is a filesystem running on a hardware raid controller only requermint is that speed doesnt take a huge hit, i can still access it over samba from windows, and its easily expandable. If ext3 is still my best option i will keep it but there has to be a filesystem that does it all.

---

### Post by psusi on 2008-12-05
> **halfelite said:**
> Well after running ext3 for a few weeks and going to expand my array size I realized its not an easy option since you have to drop the journal turn it into ext2 then expand.

What gave you that idea?  You can resize ext3 offline just fine with gparted, and you can even resize it while the drive is mounted with a remount command, if the volume is on an underlying system that can be resized on the fly, like an lvm volume, or raid array.

---

### Post by halfelite on 2008-12-06
> **psusi said:**
> What gave you that idea?  You can resize ext3 offline just fine with gparted, and you can even resize it while the drive is mounted with a remount command, if the volume is on an underlying system that can be resized on the fly, like an lvm volume, or raid array.


what for real. I read everywere that you cant expand a ext3 withouth removing the journal. I hate myself lol.

---

### Post by psusi on 2008-12-06
> **halfelite said:**
> what for real. I read everywere that you cant expand a ext3 withouth removing the journal. I hate myself lol.

Odd... I've never heard anyone say that before.

---

### Post by Dr Small on 2008-12-06
> **psusi said:**
> Odd... I've never heard anyone say that before.
Me neither.

---

