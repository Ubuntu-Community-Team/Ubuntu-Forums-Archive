---
title: "Installing ubuntu on the SSD in my gazp6"
date: 2012-03-06
forum: System76 Support
---

### Post by sam271828 on 2012-03-06
So I just got my new gazp6, which is beautiful, but it appears that the OS was installed on the 500 GB hard drive instead of the 60GB SSD. I was hoping that /root would be on the SSD, to take advantage of the increased speed, and that I could put /home on the HD. Can anyone give me a few pointers on how best to set that up? do i need a swap partition? I've only ever installed Ubuntu on a normal partition, with windows on the other, so this is new to me.

---

### Post by mchauber on 2012-03-07
Being that this is a new machine, why not just reinstall?  While it may be faster to dump file systems from one drive to the other, I believe there are issues with how the SSD needs to be partitioned.  If you do a fresh install there aren't any mistakes, and you won't have to worry about filesystems getting corrupted (doing the install _should_ automatically take care of any goofs made in slicing it up).

HTH




Disclaimer: Any advice I have to offer must not confused with solid gold, or even chrome plating...  At most, it is only a product of religion, forged through many sleepless nights.  :)

---

### Post by isantop on 2012-03-07
You may want to consider keeping /home on the root partition. If the secondary drive becomes inaccessible, you will be unable to boot the system and solve the problem.

---

### Post by sam271828 on 2012-03-14
Thanks! I ended up reinstalling onto the SSD and leaving /home there (but setting symlinks to Documents, Music etc on my HDD). Seems to work perfectly.

---

### Post by isantop on 2012-03-15
Perfect!

---

