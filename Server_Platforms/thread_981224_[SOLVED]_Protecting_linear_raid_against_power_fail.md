---
title: "[SOLVED] Protecting linear raid against power failure"
date: 2008-11-13
forum: Server Platforms
---

### Post by LittleFoot on 2008-11-13
Okay I have three (3) disks set up in a software linear raid via mdadm.  I spent some time figuring it out and all was well until last night, the power flickered.

Suddenly I can no longer access my disk array.  I've set the whole thing up again but how do I protect the system from this happening again? (short of buying a ups)

---

### Post by fjgaude on 2008-11-13
I would say a UPS is your best and easiest way to go.

---

### Post by LittleFoot on 2008-11-14
Alright how about second best bets?  Say disk 2 gets unmounted while the software raid controler has it marked dirty, how do I remove the dirty flag on that one volume so that the filesystem will mount the array correctly again?

---

### Post by fjgaude on 2008-11-14
Well, I've never done what you are doing... linear. It would seem that if **mdadm** indicates a drive in an array is bad, you fault it, remove it, then all you have to do is add a new drive back in, using the normal commands.

I can't say how **md** makes a linear array... is it one big partition table or are there somekind of links drive-to-drive.

Let us know what you come up with, eh?

---

### Post by LittleFoot on 2008-11-14
> **fjgaude said:**
> Let us know what you come up with, eh?

Working on it but if I knew what I was doing I wouldn't be asking here. :)

---

### Post by fjgaude on 2008-11-14
My feelings about linear is that it is not reliable... you could have multi-drives, each with their own partition, linked with symlink to make them look like one drive, though I've never done such. That way if one failed it wouuldn't take down the rest.

And always have backups!

---

### Post by LittleFoot on 2008-11-15
> **fjgaude said:**
> My feelings about linear is that it is not reliable... you could have multi-drives, each with their own partition, linked with symlink to make them look like one drive, though I've never done such. That way if one failed it wouuldn't take down the rest.

And always have backups!

Any way to set that up where all of the drive space of each of the three combined drives is available to a single directory?  Pretty much the entire reason why I ended up using linear raid was not enough space on any single unit for my needs.  The array is used to make temporary backups of large drive volumes.  And when I say temporary I mean three or for days.  But if every time the power flickers (which happens more often than I'm comfortable with) I loose an array member it ends up being a real pain.  At least until we get those three 1 TB drives and a 3 port sata card with hardware raid sometime in the next couple of months.  Just gotta have this work for now.

---

### Post by djamu on 2008-11-15
sorry to butt in ...

but I fail to understand why you are using mdadm for a linear raid ?
LVM ( EVMS )does a better job doing just this and doesn't need to rebuild.....


2nd. a way to protect your 3 disk array without UPS ... NONE.... if lightning strikes they're a gonner just like any ordinary disk ...

if you want redundancy ... make it a RAID5 / 6 / 10, but those don't protect you either from heavy power surges ....


so get a proper UPS ( and check it has current conditioning ! )

---

### Post by cariboo on 2008-11-15
In my area you can get a ups that allows the computer to gracefully shut down when the poer goes out for less than a case of beer. :)

Jim

---

### Post by fjgaude on 2008-11-15
> **LittleFoot said:**
> Any way to set that up where all of the drive space of each of the three combined drives is available to a single directory?  Pretty much the entire reason why I ended up using linear raid was not enough space on any single unit for my needs.  The array is used to make temporary backups of large drive volumes.  And when I say temporary I mean three or for days.  But if every time the power flickers (which happens more often than I'm comfortable with) I loose an array member it ends up being a real pain.  At least until we get those three 1 TB drives and a 3 port sata card with hardware raid sometime in the next couple of months.  Just gotta have this work for now.

Please, with your situation, a UPS is the way to go.

---

### Post by djamu on 2008-11-15
> **cariboo907 said:**
> In my area you can get a ups that allows the computer to gracefully shut down when the poer goes out for less than a case of beer. :)

Jim

mm can you send me a couple of those then ?:lolflag:

---

### Post by LittleFoot on 2008-11-17
> **djamu said:**
> sorry to butt in ...

but I fail to understand why you are using mdadm for a linear raid ?
LVM ( EVMS )does a better job doing just this and doesn't need to rebuild.....

Going to take a deeper look at this but on the outset it looks like it might be better suited for my purpose.

For all those that recommended a UPS, it's noted.  Not going to happen but it's noted. 

Thank's for all the feedback, if I figure out LVM I'll post my procedure.  Still not sure how to take a disk array that's marked dirty out of a linear array and reset the dirty flag but if LVM works out the way I hope it will I'll no longer care.

---

### Post by koenn on 2008-11-17
> **djamu said:**
> mm can you send me a couple of those then ?:lolflag:
cases of beer ?

---

### Post by djamu on 2008-11-20
> **koenn said:**
> cases of beer ?

Ja lekker, West-Vleteren ofzo  ... groetjes :popcorn:

---

