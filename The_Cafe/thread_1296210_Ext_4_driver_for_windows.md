---
title: "Ext 4 driver for windows"
date: 2009-10-20
forum: The Cafe
---

### Post by praveesh on 2009-10-20
My friend wish to view the linux partition in windows . I could find ext 2 driver for windows in the internet . But he is planning to move to karmic . And I couldn't find any ext 4 drivers for windows in the net . Is there any ext4 drivers for windows available ? Thanks


Is this question in the right place ? Should I ask in the main support categories ?

---

### Post by openfly on 2009-10-20
I know ext3 was backwards compatible to ext2 so windows ext2 drivers would work.  I am not familiar with ext4s compatability with ext2.

---

### Post by Nozze on 2009-10-20
I only know that I had trouble with the ext2driver at my ext4 partition so I would like a new driver if some one have one.

---

### Post by Jesus_Valdez on 2009-10-20
I installed the afore mention driver for EXT2 and I'm unable to see my Jaunty partition (EXT4) from windows Vista.

So, I hope You could find a solution and share it with us.

---

### Post by Dragonbite on 2009-10-20
This would be extremely helpful.

---

### Post by sanderj on 2009-10-20
See info here [http://ubuntuforums.org/showthread.php?t=1181698](http://ubuntuforums.org/showthread.php?t=1181698)

Short answer: No, you can't.

---

### Post by Dragonbite on 2009-10-20
> **sanderj said:**
> See info here [http://ubuntuforums.org/showthread.php?t=1181698](http://ubuntuforums.org/showthread.php?t=1181698)

Short answer: No, you can't.

Yet.

---

### Post by Excedio on 2009-10-20
Where there's a will...there's a way ;-)

---

### Post by Nerd King on 2009-10-20
Personally I wouldn't want windows accessing my linux partition thank you very much. It's a nice little security barrier keeping them seperate! My simple rule is Don't Give Windows Access To Anything Important.

---

### Post by oldfred on 2009-10-20
+1 for Nerd King

If you have to share something create a separate NTFS partition.

---

### Post by JoshuaRL on 2009-10-20
> **Nerd King said:**
> Personally I wouldn't want windows accessing my linux partition thank you very much. It's a nice little security barrier keeping them seperate! My simple rule is Don't Give Windows Access To Anything Important.

Fair enough, I once had my brother install a game to my root folder accidentally through XP.  But ext3 and especially ext4 are vastly better filesystems than NTFS.  So if I want to store all my media and important documents on my Ubuntu partition (where I'm at usually anyway) and read them on Windows, that isn't a ridiculous request.  I'm of the opinion now that a dual-boot system is necessary.  Nothing is better for fixing dumb user-born problems than a second bootable OS.  After all, LiveCDs are REALLY slow.

---

### Post by Giant Speck on 2009-10-20
I would love to be able to access my Linux partitions from my Windows partition.  I mean, I can access my Windows partition from my Linux partition; why shouldn't I be able to do the opposite?

---

### Post by Nerd King on 2009-10-21
> **JoshuaRL said:**
> Fair enough, I once had my brother install a game to my root folder accidentally through XP.  But ext3 and especially ext4 are vastly better filesystems than NTFS.  So if I want to store all my media and important documents on my Ubuntu partition (where I'm at usually anyway) and read them on Windows, that isn't a ridiculous request.  I'm of the opinion now that a dual-boot system is necessary.  Nothing is better for fixing dumb user-born problems than a second bootable OS.  After all, LiveCDs are REALLY slow.
I agree about dual-boot, it's very handy for fixing broken stuff, though a usb with a suitable linux is just as good.

Personally I would recommend putting media on the windows partition (and backing up to an external drive using ext4) and that way you can access it from Windows AND linux without a problem, or as oldfred suggested make a separate ntfs partition for the job. That way, no linux components are exposed to risk.

---

### Post by Frak on 2009-10-21
> **Giant Speck said:**
> I would love to be able to access my Linux partitions from my Windows partition.  I mean, I can access my Windows partition from my Linux partition; why shouldn't I be able to do the opposite?
The irony is staggering.

---

### Post by AllRadioisDead on 2009-10-21
> **Frak said:**
> The irony is staggering.
Haha, yes it is.:)

---

