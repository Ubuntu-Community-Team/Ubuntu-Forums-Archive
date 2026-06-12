---
title: "Drive Cloning"
date: 2008-08-05
forum: Windows
---

### Post by 16777216 on 2008-08-05
I have a friend that has XP on a 20 gig drive and wants to clone it to a larger drive.

I am thinking about giving him a live CD with printed instructions on how to clone it with dd.

The thing I want to know is will dd copy the MBR as well or will he have to use the win repair console off the win install CD?

I can't go over and do this as I just Broke 3 bones in my shoulder dodging a deer on a scooter. ( I missed it but not the ditch. )

I was thinking of using the gParted live CD but not using their copy disk procedure because it looks like it doesn't copy the MBR.

Instead have him open a terminal fdisk the drive info ( or use what gParted gives him ) use dd to clone then Gparted to grow the new empty space so that is now useable.

Is this good or is their a better/easyer way?

---

### Post by logos34 on 2008-08-05
yes, if you dd the whole disk (as opposed to just a partition) it will copy the MBR as well

---

### Post by fiddledd on 2008-08-05
Just burn him a CD of [Clonezilla](http://www.clonezilla.org/)

---

### Post by logos34 on 2008-08-05
> **fiddledd said:**
> Just burn him a CD of [Clonezilla]("http://www.clonezilla.org/")

why?  dd is easier--one command.

---

### Post by prshah on 2008-08-05
> **16777216 said:**
> has XP on a 20 gig drive and wants to clone it to a larger drive. thinking about giving him a live CD with printed instructions on how to clone it with dd. The thing I want to know is will dd copy the MBR as well or will he have to use the win repair console off the win install CD?

You're on the right track; dd will also clone and write back the mbr as well. Then he can use gparted to resize the partitions to his hearts content.

Please be very careful with the dd commands; if he/you reverses if/of, it's goodbye XP. (I wouldn't call that necessarily a bad thing! :) )

---

### Post by fiddledd on 2008-08-05
> **logos34 said:**
> why?  dd is easier--one command.

Why not? The OP said his friend is using XP and wants to clone a Hard Drive, why not give him Open Source software on a CD that he can use or share later.

---

### Post by 16777216 on 2008-08-05
Thanks for the info everybody.
This has helped me a lot.

---

